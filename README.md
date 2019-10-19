# OL-DLMOVER
Detect newer CSV File by its name and copy to specific folder
![fig1](https://user-images.githubusercontent.com/25300684/67138419-b6031580-f27d-11e9-8a9e-ae4f572ff464.png)
一定時間毎にデータロガーにより生成されるフォルダ、ファイルの名前から最新のファイルを特定し、指定のフォルダにコピーします。また、コピーしたファイルの日時情報を記憶しておき、これより新しいファイルである場合にのみコピーします。
![fig2](https://user-images.githubusercontent.com/25300684/67138433-f498d000-f27d-11e9-8d28-241495b364ac.png)
フォルダの命名には何の手も加えられていないことを想定しています。例えば、上の階層から順に新しいモノを決定しているので、古い日付のフォルダに新しいファイルが入っているというような状態ではうまく動作しません。

## 想定環境
Python 3.x系です。動作を確認しているのはPython 3.7.4です。
OS問わず動作するはずですが、今のところmacOSでしか動作を確認していません。

## 利用ライブラリ
ありません。

##　使い方
以下のコマンドライン引数を与えて下さい。
|引数|内容|制約|
|---|---|---|
|監視対象フォルダ|データロガーにより生成されるフォルダが入るパスを指定して下さい。||
|出力フォルダ|最新のファイルをコピーするフォルダのパスを指定して下さい。|実行時に存在している必要があります。|
|ファイル名|コピーした最新のファイルのファイル名を指定して下さい。||
```bash
$ python app.py [監視対象フォルダ] [出力フォルダ] [ファイル名]
```
![fig3](https://user-images.githubusercontent.com/25300684/67138479-9ddfc600-f27e-11e9-8e8b-9b7697e4e20a.png)

また、以下のオプションが使えます。
|引数|内容|
|---|---|
|-h, --help|ヘルプ画面を表示します|
|-i INTERVAL, --interval INTERVAL|ファイル探索間隔を変更します。（デフォルト：3秒）|
|-d, --debug|デバッグメッセージを有効にします。|
ヘルプ画面を表示：
```bash
$ python app.py [監視対象フォルダ] [出力フォルダ] [ファイル名] -h
```
ファイル探索間隔を5秒に変更：
```bash
$ python app.py [監視対象フォルダ] [出力フォルダ] [ファイル名] -i 5
```