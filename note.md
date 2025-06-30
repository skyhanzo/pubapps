GAMBARON GitHub Pages ホスティング設定
=============================================================================

GitHub Pages 設定手順
=============================================================================
1. GitHub Pages に登録するリポジトリ作成
	1. トップページを index.html で作成
	2. アプリ毎フォルダに必要な公開ページを作成 (利用規約、プライバシーポリシー、特定商取引法に基づく表示、必要なデータ 等)
	3. コミット & プッシュ

2. GitHubリポジトリの設定 > Pages > Custom domain にドメインを登録
	- 登録確認完了したら ✅ Enforce HTTPS にチェック

3. ドメインプロバイダに Aレコードを設定 (最大72h程かかる)
	| TYPE | ホスト名     | 値(IPAddr)      | TTL  |
	| ---- | ------------ | --------------- | ---- |
	| A    | 取得ドメイン | 185.199.108.153 | 3600 |
	| A    | 取得ドメイン | 185.199.109.153 | 3600 |
	| A    | 取得ドメイン | 185.199.110.153 | 3600 |
	| A    | 取得ドメイン | 185.199.111.153 | 3600 |

4. Google Search Console でドメインのTXTレコード登録を行う

5. ドメインプロバイダにTXTレコードを設定 [Googleサーチコンソール導入・設定手順と使い方](https://www.onamae.com/column/howto/2/)

6. Google Search Console でGoogle検索表示させる設定 [GitHub PagesでGoogle検索に表示させたい](https://qiita.com/r_saiki/items/9ab3be34fa255724c9dd)
	1. ルートに _config.yml を追加
		```yml
		plugins:
		- jekyll-sitemap
		```
	2. GitHub Pages を設定完了するとリモートのルートに CNAME ファイルが自動で追加されているので $ git pull でマージしてから push
	3. リポジトリには _config.yml が追加されるのみだが、実サイトには自動生成された sitemap.xml が追加されている
		- 確認方法: https://{ユーザー名}.github.io/{リポジトリ名}/sitemap.xml
		- カスタムドメインの場合は: https://{取得ドメイン}/sitemap.xml
	4. sitemap.xml をGoogle検索にヒットさせるため送信する
		- Google Search Console > サイトマップ: https://{ユーザー名}.github.io/{リポジトリ名}/sitemap.xml を設定する
		- カスタムドメインの場合は: https://{取得ドメイン}/sitemap.xml

- 更新してから反映まで1-2時間程かかるので注意
- favicon.ico (32x32のみ): 全てのhtmlに <link rel="icon" href="favicon.ico" type="image/x-icon"> タグを設定
- 5日程経過すると Google から以下のメールが来たので /robots.txt を書いて設置
	```
	ページ がインデックスに登録されない新しい要因
	Search Console で、貴サイトのいくつかの ページ がインデックスに登録されていないことが検出されました。以下がその要因となっています。
	robots.txt によりブロックされました
	```
	- Search Consoleで再クロール依頼が必要
	- TODO: プライバシーポリシー等はHITさせる必要は無いので robots.txt に "Disallow: /許可しないディレクトリ/" 等と指定する予定
		- 2025/6 現状 ルート直下が個別アプリディレクトリの階層構成なので /policies/アプリ名 等という構成にしたいが、アプリ内のリンクが固定なので次回アプデで変更する


-----------------------------------------------------------------------------
[GAMBARONトップページ](https://gambaron.com) / [オリジナル](https://skyhanzo.github.io/pubapps/index.html)
=============================================================================
- アプリサムネ


-----------------------------------------------------------------------------
IQ Knight
=============================================================================

### iOS/Android
- [プライバシーポリシー](https://gambaron.com/IQKnight/privacy-policy.html) / [オリジナル](https://skyhanzo.github.io/pubapps/IQKnight/privacy-policy.html)
- [利用規約]()
- [特定商取引法に基づく表示]()
