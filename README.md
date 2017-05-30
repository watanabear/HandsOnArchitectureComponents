# HandsOnArchitectureComponents
https://developer.android.com/topic/libraries/architecture/index.html
https://riggaroo.co.za/android-architecture-components-looking-room-livedata-part-1/

## Roomとは何か？

ルームはAndroidアプリでデータベースを作成する新しい方法です。 `Room`には、アプリケーションにデータを保存するために事前に書かなければならない定型コードがたくさんあります。 `Room`はJavaクラスとSQLiteの間のORMです。 `Room`では、もはやカーソルとローダーを使用する必要はありません。 `Room`は本格的なORMではありません。たとえば、他のORMソリューションが提供するような複雑なオブジェクトのネストを行うことはできません。

`Room`では、データを照会できるいくつかの方法があります。

- LiveDataは、更新を受け取るために登録できるイベントのストリームを公開するクラスです。 これは非同期であるため、メインスレッドで使用できます。
- RxJava2 Flowable抽象クラスを使用します。
- AsyncTaskなどのバックグラウンドスレッドに同期呼び出しを配置します。 （`Room`では、メインスレッドでデータベースクエリを発行することはできません（ANRsを生成できるため）。

## LiveDataとは何か？

`LiveData`を使用すると、明示的で堅固な依存関係のパスを作成せずに、アプリケーションの複数のコンポーネントにわたるデータの変更を監視できます。 `LiveData`は、アクティビティとフラグメントのさまざまなライフサイクルを尊重します。 `LiveData`と`Room`を組み合わせると、標準のSQLiteDatabaseを使用するだけでは達成できない自動データベース更新を受け取ることができます。

## In Summary

`Room`はAndroid上でSQLiteの実装をラップする使いやすいライブラリです。 また、カーソルやコンテンツプロバイダの代わりにオブジェクトを扱うための直観的なインターフェイスも提供します。 `LiveData`で`Room`を使用することは、革命です。 これは、標準のSQLiteDatabaseで達成するのが難しい可能性があるデータ変更についてのビューを通知することを許可します。

アクティビティやフラグメントに直接データをロードすることにはいくつかの落とし穴があります。 主な問題は、あなたのアクティビティやフラグメントがデータベースに緊密に結合していることです。 これは、`テストを追加したり、別の場所でロジックを再利用したりする場合には適していません`。 データベースロジックをビューロジックから分離する方がはるかに良い方法です。 ViewModelアーキテクチャコンポーネントは、この問題を解決することを目的としています。 
