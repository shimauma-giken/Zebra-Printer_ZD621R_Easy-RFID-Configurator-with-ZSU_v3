# RFIDプリンタの調整・設定ガイド(ZD621R)

</br>

<!--
_backgroundColor: black
_color: white
-->
![bg brightness:0.3](https://www.devprojournal.com/wp-content/uploads/2017/09/Zebra-Logo.jpg)

UPDATE: 2025/11/23


## 0. 目次


1. 準備
2. 設定ファイルの取得
3. 印字圧力の調整　　
4. サプライの装填
5. ラベルセンサーの調整
6. 基本設定（印刷）
7. 基本設定（RFID）
8. テスト印刷・エンコード
9. 印刷品質の調整
10. その他の設定（通信、用紙オプション）
11. 推奨設定（Syslog、RFID Log）

</br>

## 1. 準備

本手順で必要なマテリアルは下記の通り。

|マテリアル|詳細|備考|
|-|-|-|
| Zebra RFIDプリンタ| 最新ファームウェア推奨
| RFIDラベル   |ID:　0.5-1.0" (オプション利用時:1.5, 2.0, 3.0")</br> OD: 5.0"
| インクリボン | ID:　1.0" (300m), 0.5"(74m) </br>**巻き取り用の紙芯**|[ZD621R スペック](https://www.zebra.com/jp/ja/products/spec-sheets/printers/desktop/zd600-series.html)</br>[ZD621R 技術仕様](https://partnerportal.zebra.com/content/dam/zebra_dam/en/tech-specs/zd621-tech-specs-en-us.pdf)
| USB ケーブル | PC<-->Printer 接続用
| Windows PC   |下記ソフトウェアがインストール済みであること。</br>- [Zebra Setup Utilities for Windows](https://www.zebra.com/us/en/support-downloads/software/printer-software/printer-setup-utilities.html)</br>- [Zebra Designer 3 Professional](https://www.zebra.com/jp/ja/support-downloads/software/printer-software/zebra-designer-3-downloads.html)
| 清掃キット | 不織布+ IPA 90%以上

</br>

#### 推奨マテリアル

|マテリアル|詳細|備考|
|-|-|-|
|シリアル接続ケーブル| PC環境に応じて準備| トラブルシューティング、複数台導入で重宝
|USBメモリ | Fat32でフォーマット | 様々なシーンで利用

</br>


## 2. 設定ファイルの取得


1. 設定用ファイルをダウンロードする。
   [<>Code] > [Local] > [Download ZIP]
   
   https://github.com/shimauma-giken/Zebra-Printer-ZT-Series-Easy-Pinter-Configurator-with-USB
   <br>

3. ZIPを解凍する。
</br>

### 「参考」 設定ファイルの構成

   | ファイル名    | 用途 |
   |-|-|
   | DEL_STAMP.ZPL	| USBメモリタイムスタンプ削除用	| 
   | PRT_TEST.ZPL	| 印刷テスト用（印刷のみ）	| 
   | RFID_RO1.zpl	| 印刷テスト用（RFID Read）	| 
   | RFID_RW1.ZPL	| 印刷テスト用（RFID Write）	| 
   | SET_CALB.ZPL	| 設定用（用紙キャリブレーション）	| 
   | SET_DTBR.ZPL	| 設定用（感熱、黒マーク）	| 
   | SET_DTGP.ZPL	| 設定用（感熱、ギャップ）	| 
   | SET_TTBR.ZPL	| 設定用（熱転写、黒マーク）	| 
   | SET_TTGP.ZPL	| 設定用（熱転写、ギャップ）	| 

</br>

</br>

### 「参考」ラベルとセンサー

##### 連続紙・レシート
  <img width=400 src="https://docs.zebra.com/content/dam/techpubs/media/printers/industrial/zt411-421/g-media-continuous.svg/_jcr_content/renditions/original">
  </br>

  ##### ギャップ・ノッチ
  <img width=400 src="https://docs.zebra.com/content/dam/techpubs/media/printers/industrial/zt230/g-zt230-media-noncont-gaps.png/_jcr_content/renditions/original">
  </br>

  ##### 黒マーク
  <img width=400 src="https://docs.zebra.com/content/dam/techpubs/media/printers/industrial/zt230/g-zt230-media-noncont-blk-mrk.png/_jcr_content/renditions/original">
  </br>
    </br>



## 3. 印字圧力の調整　　

ZD621Rは実施不要。

</br>
</br>

## 4. サプライの装填（リボン）

<img height=400 src="https://docs.zebra.com/content/dam/techpubs/media/printers/desktop/zd620-zd420/g-zd620-zd420-ribbon-transfer-roll-loading-place-on-spindle.png/_jcr_content/renditions/original"><img height=400 src="https://docs.zebra.com/content/dam/techpubs/media/printers/desktop/zd620-zd420/g-zd620-zd420-ribbon-transfer-roll-loading-align-ribbon-to-core.png/_jcr_content/renditions/original">

</br>

下記点に注意しながら、リボンを装填する。
- リボンは外巻きを推奨
- リボンの取り付け方向
- リボンの通り道（PHDの下を通るように）
  
詳細な手順は下記リンクを参考にすること。  
[熱転写ロール リボンの装着](https://docs.zebra.com/jp/ja/printers/desktop/zd421-and-zd621-desktop-printers-user-guide/c-zd620-420-setup/c-zd200t-ug-loading-thermal-transfer-roll-ribbon.html)


</br>

## 4. サプライの装填（ラベル）


下記点に注意しながら、ラベルを装填する。
- ラベルは外巻きを推奨
- ラベルの通り道（リボン・PHDの下を通るように）

</br>


<img height=300 src="https://docs.zebra.com/content/dam/techpubs/media/printers/desktop/zd620-zd420/g-zd420d-media-roll-loading.png/_jcr_content/renditions/original">
<img height=300 src="https://docs.zebra.com/content/dam/techpubs/media/printers/desktop/zd620-zd420/g-zd620-zd420-pull-the-media.png/_jcr_content/renditions/original">
<img height=300 src="https://docs.zebra.com/content/dam/techpubs/media/printers/desktop/zd620-zd420/g-zd420dsg-push-the-media.png/_jcr_content/renditions/original">
</br>

※ 詳細は下記リンクを参照  
[用紙のセット](https://docs.zebra.com/jp/ja/printers/desktop/zd421-and-zd621-desktop-printers-user-guide/c-zd620-420-setup/guid-293b74c5-3de0-4bc1-8ae9-8118915c5e31-ja/t-zd620-420-loading-media.html)

</br>



## 5. ラベルセンサーの調整

ラベルセンサーをラベル形状、タイプに合わせて、ポジショニングすること。
<br>

<img src="https://docs.zebra.com/content/dam/techpubs/media/printers/desktop/zd620-zd420/g-zd620-zd420-media-roll-sensor-alignment.png/_jcr_content/renditions/original">

</br>

|図| ラベルタイプ| センサ位置|
|-|-|-|
|A| ギャップ   |・センサー位置をギャップ位置に合わせる。</br>・受光センサー範囲内に設定すること。</br> <img width=300 src="https://docs.zebra.com/content/dam/techpubs/media/printers/desktop/zd620-zd420/g-zd620-zd420-movable-sensor-adjusting-for-web-gap-sensing-2.png/_jcr_content/renditions/original">
|B| 黒マーク   |・センサー位置をブラックマーク位置に合わせる。

<br>

#### 図：ギャップセンサー設定例
   ![bg](./picture/Label-Sensor-01.png)


<br>



</br>

## 6. 基本設定（印刷）

<img src="./picture/ZSU-Send-File-01.png" width="50%">


1. プリンタとPCをUSBケーブルで接続。
1. Zebra Setup Utilities for Windows（以降ZSU） を使用して適切な設定ファイルを送付する。
   ```
   ZSU > [プリンタツールを開く] > [設定] > [ファイルを送る] > "任意のファイルを選択" > [送信]
   ```


   | ファイル名    | 用途 |
   |-|-|
   | SET_DTBR.ZPL	| 設定用（感熱、黒マーク）	| 
   | SET_DTGP.ZPL	| 設定用（感熱、ギャップ）	| 
   | SET_TTBR.ZPL	| 設定用（熱転写、黒マーク）	| 
   | SET_TTGP.ZPL	| 設定用（熱転写、ギャップ）	| 

   <br>

1. 用紙キャリブレーションが完了するまで待つ。
1. キャリブレーションの正常性を確認する。

<br>

**※ 用紙キャリブレーションができない場合はマニュアルキャリブレーションを実施すること。**

[参考：Youtube: ZT411 Printer: Ribbon and Media Calibration /Zebra](https://www.youtube.com/watch?v=-80-NPebwGA)



</br>

## 7. 基本設定（RFID）

<img src="https://docs.zebra.com/content/dam/techpubs/media/printers/desktop/zd421-zd621/g-mlk-ug-menu-rfid-cal-1.png/_jcr_content/renditions/cq5dam.web.1280.1280.jpeg" width="80%">

1. 用紙キャリブレーションが完了していることを確認。
2. プリンタ液晶 > [RFID] > [RFID Calibrate] を選択。
3. RFID キャリブレーションが完了するまで待つ。
4. エラーが発生していないことを確認する。

### RFID キャリブレーションが失敗するときは。。。。
1. 用紙キャリブレーションが適切か
1. 用紙設定が適切か
1. RFIDキャリブレーション中に用紙詰まりが発生していないか


</br>

## 10. テスト印刷・エンコード


1. Zebra Setup Utilities for Windows（以降ZSU） を使用して適切な設定ファイルを送付する。
   ZSU > [プリンタツールを開く] > [設定] > [ファイルを送る] > "下記表のファイルを選択" > [送信]
1. Void やエラーが発生しないことを確認する。
<br>



## テスト用ファイル
| ファイル名    | 用途 |
|-|-|
| PRT_TEST.ZPL	| 印刷テスト用（印刷のみ）	| 
| RFID_RO1.zpl	| 印刷テスト用（RFID Read）	| 
| RFID_RW1.ZPL	| 印刷テスト用（RFID Write）	| 

※ テストファイルはZebra Designer 3 Pro/Developerで作成してもOK。



</br>

## VOID発生原因 TOP5

1. 不適切なRFIDラベルの利用
   - サポート対象外のインレイ
   - ラベル選定
1. 不適切な用紙調整、用紙ジャム
   - ラベルセンサーの位置
   - 用紙設定
2. 用紙・RFIDキャリブレーションの未実施
3. 不適切なSKU
   - 電波出力不足
1. Win ドライバによる設定上書き
</br>

## VOID発生時の確認ポイント

1. **ラベル・プリンタ選定**
1. Firmware
1. **用紙センサー位置**
1. ラベルジャム、ラベル詰まり
1. 印字ヘッド周囲の汚れ
1. **用紙設定・調整** 
1. RFID設定・調整

</br>

## VOID発生時の切り分け時に便利なコマンド

1. RFID キャリブレーション
   ```zpl
    ^XA^HR^XZ
    ```
    - 用紙調整、ラベルジャム、詰まり
    - 電波強度
  

2. RFID ログ
   ```shell
   ! U1 setvar "rfid.log.enabled" "yes"
   ! U1 getvar "rfid.log.entries"
   ```
   - VOIDのエラーコード

3. RFID 設定一覧
   ```
   ! U1 getvar "rfid"
   ```


</br>

## 8. 印刷品質の調整
<img src="./picture/ZSU-Wizard-Print-Quality-01.png" width="50%">


印刷対象のラベルに応じて、適切な設定をする。

- ラベルサイズ
- 印字濃度
- 印字速度
- ラベル用紙の種類

</br>

## 9. その他の設定（通信、用紙オプション）

その他、付属オプションに応じて、適切な設定をすること。

1. 用紙オプション設定
   - カッター
   - ピーラー
   - リワインダー
2. 通信オプション設定
   - Ethernet
   - Bluetooth 
   - Wi-Fi
3. フォントファイルのインストール
   - 日本語フォントなど


</br>

<br>
<br>
<br>

# プリンタは工業製品です。適切な手順を踏むことで、適切な動作をする仕様です。
#### 大半のVOIDエラーは適切に設定・調整をしていないことによって発生しています。
#### 行き詰ったら、立ち止まって、ガイドを見直して、未対応項目がないか確認しましょう。

<img src="https://i.pinimg.com/originals/86/84/43/86844362e4f4f5bb08ccad7db2296e8f.gif" width="50%">
