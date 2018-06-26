# Riak-kv-docker

Riakを試せるdocker環境

![Riak_Explorer](src/imgs/Riak_Explorer.png)

[basho/riak-kv](https://hub.docker.com/r/basho/riak-kv/)を参考に作成している

## 起動

コンテナを起動する
```
% docker-compose up -d coordinator 
```

web UIを開く

http://localhost:8098/admin/

## 簡単な動作確認

以下の手順でデータを登録する

![Riak_Explorer2](src/imgs/Riak_Explorer2.png)

![Riak_Explorer3](src/imgs/Riak_Explorer3.png)

![Riak_Explorer4](src/imgs/Riak_Explorer4.png)

その後curlを叩くを値が取得できる事が確認できる

```shell
% curl http://localhost:8098/admin/riak/clusters/default/types/default/buckets/sample/keys/key
{"sample-Key":"sample-value"}
```

### web UIを使わずにcurlから直接PUTしてみる

以下を実行する

```shell
% curl -v -X PUT http://localhost:8098/riak/favs/db -H "Content-Type: text/html" -d "<html><body><h1>My new favorite DB is RIAK</h1></body></html>"
```

ブラウザから http://localhost:8098/riak/favs/db にアクセスする

![Riak_Explorer5](src/imgs/Riak_Explorer5.png)
