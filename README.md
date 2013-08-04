
	//	使えるかもしれない非公式Twitter API & Consumer Key
	/*
		API 1.1から全エンドポイント認証必須になってしまい、クソザコサービスになりさがりやがったので、
		なるべく認証不要 + 隠しAPIを探し、集めてみました。中には偶然見つけたヤツもあったので、
		探せばもっと出てくるんじゃなかろうか
	*/

	<==============================================================================================>
	//	cdn.api.twitter.com系は、埋め込みツイートから拾ってきてるので、実質規制無いようなものです。
	UserID -> ScreenName ( 認証不要 ) by 某凍結氏
	https://twitter.com/users/[user_id].json

	ツイート取得 ( 認証不要 )
	https://cdn.api.twitter.com/1/statuses/show.json?id=[user_id]&include_entities=true

	/*	API 1.1の移行とともに利用できなくなりました。
	aとbの関係。単にフォローしてるかどうかのチェックならば、下のAPI使ったほうが楽。 ( 認証不要 )
	by 某凍結氏
	https://twitter.com/friendships/show?format=json&target_id=[user_id]&source_id=[user_id]
	*/

	aがbをフォローしてるかどうかどうか ( 認証不要 )
	https://cdn.api.twitter.com/1/friendships/exists.json?screen_name_a=[user_a]&screen_name_b=[user_b]

	ユーザー情報の取得 ( 認証不要 )
	https://cdn.api.twitter.com/1/users/show.json?screen_name=[screen_name]

	ユーザー情報の取得の一括 ( 一度に100人まで )( 認証不要 )
	https://cdn.api.twitter.com/1/users/lookup.json?user_id=[user_id, user_id...]

	ガジェットIDからタイムラインを取得できる。ただ整形処理が必要でめんどくせー
	http://cdn.syndication.twimg.com/widgets/timelines/324713397071527936

	指定スクリーンネームがとられているかどうかをチェックする(認証不要。RateLimited有り)
	by フォロワーさん
	https://api.twitter.com/i/users/username_available.json?username=[screen_name]

	メールアドレスが使えるかどうか(認証不要。RateLimited有り)
	by フォロワーさん
	https://api.twitter.com/i/users/email_available.json?email=[mail_address]

	//	こっから認証必要
	Status Activity ( ふぁぼ、RTの詳細を得られる )
	https://api.twitter.com/i/statuses/[tweet_id]/activity/summary.json

	<==============================================================================================>
	//	公式クライアントで使われてるアクティビティAPI
	By friends Activity
	http://api.twitter.com/i/activity/by_friends.json

	About me Activity
	http://api.twitter.com/i/activity/about_me.json

	//	未確認。
	Following Followers of
	http://api.twitter.com/users/following_followers_of.json

	以下、公式クライアントのキーでないと動かない
	古いツイート(7日以上前)を探せるAPI by 某凍結氏
	https://api.twitter.com/1.1/search/universal.json?q=[q]

	??不明。
	https://api.twitter.com/1.1/search/typeahead.json

	おすすめツイ―ト？みたいな。
	https://api.twitter.com/1.1/discover/universal.json

	ハイライト？
	https://api.twitter.com/1.1/discover/highlight.json

	各ユーザーへのおすすめユーザを取得するAPI
	https://api.twitter.com/1.1/users/recommendations.json?screen_name=[target_user_screen_name]

	ツイートを各言語に変換するAPI
	https://api.twitter.com/1.1/translations/show.json?dest=["en", "jp"..etc]&id=[tweet_id]

	・・・？トレンドっぽい
	https://api.twitter.com/1.1/trends/personalized.json

	会話API by 某凍結氏
	https://api.twitter.com/1.1/conversation/show/[tweet_id].json

	メディア系のタイムライン取得 by 某凍結氏
	https://api.twitter.com/1.1/statuses/media_timeline.json

	<==============================================================================================>
	//	UserStreamの非公式引数

	フォローユーザーの活動状況をリアルタイムに手に入れる。ふぁぼ、あんふぁぼ、ブロック、フォローなどなど。
	FavStarとか特定ユーザーの監視向け
	by 某凍結氏
	include_followings_activity : Boolean

	<==============================================================================================>
	-- Consumer Key & Consumer Secret --

	Twitter for Windows
		consumer_key: TgHNMa7WZE7Cxi1JbkAMQ
		consumer_secret : SHy9mBMBPNj3Y17et9BF4g5XeqS4y3vkeW24PttDcY

	<==============================================================================================>