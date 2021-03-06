.. _files_expand_cluster:

-----------------------
ファイル：EXPAND CLUSTER
-----------------------

概要
++++

ファイルは、デプロイメントをスケールアップおよびスケールアウトする機能を提供します。 Files VMのCPUとメモリをスケールアップすると、環境でより高いストレージスループットと同時セッション数をサポートできます。現在、
Files VMは最大で12個のvCPUとそれぞれ96GBのRAMにスケールアップできます

Filesのスケーラビリティの真の力は、単純にファイルVMを追加する機能であり、基盤となるNutanix分散ストレージファブリックのようにスケールアウトします。個々のFilesクラスターは、Nutanixクラスター内の物理ノードの数までスケールアウトできるため、
通常の操作中に単一のノードで実行されるファイルVMは1つだけです

Filesクラスターの拡張
+++++++++++++++++++

#. **Prism** で　> **File Server 「ファイルサーバー」** に戻り、**BootcampFS** を選択します

#. Click **Update 「更新」> Number of File Server VMs「ファイルサーバーVMの数」**　をクリックします

   .. figure:: images/25.png

#. Files VMの数を3から4に増やし、[次へ]をクリックします

   .. figure:: images/26.png

   追加されたFiles VMをサポートするために、クライアントとストレージネットワークの両方で追加のIPが消費されることに注意してください

#. **Next「次へ」> Save「保存」**　をクリックします
　　
   これでクラスターに対して4番目のFiles VMがデプロイされ、電源がオンになります。ステータスは、**Prism> Tasks** で監視できます

   .. 注意::

     Filesクラスターの拡張が完了するまでに約10分かかります

   拡張に続いて、クライアント接続が新しいVMに負荷分散できることを確認します

#. RDPまたはコンソールを介して *Initials*\ **-ToolsVM** に接続します

#. **Control Panel「コントロールパネル」 > Administrative Tools 「管理ツール」> DNS** を開きます。

#. 以下のフィールドに入力して、**OK** をクリックします:

   - **次のコンピュータ** を選択します
   - **dc.ntnxlab.local** を指定します
   - **指定したコンピューターに今すぐ接続を選択します**

   .. figure:: images/28.png

#. **DC.ntnxlab.local > Forward Lookup Zones「前方参照ゾーン」> ntnxlab.local** を開き、**BootcampFS**　の4つのエントリがあることを確認します. FilesはラウンドロビンDNSを利用して、FilesVM間で接続の負荷を分散します

   .. figure:: images/29.png

   .. 注意::

     エントリが3つしかない場合は、Filesクラスターを選択して[DNS]をクリックすることにより、**Prism** > ファイルサーバーから　**DNS** エントリを自動的に更新できます

持ち帰り
+++++++

**Nutanix Files** について知っておくべき重要なことは何ですか？

- ワンクリックのパフォーマンス最適化により、Filesをスケールアップおよびスケールアウトできます
