ref: https://docs.docker.com/engine/reference/commandline/docker/

#### DOCKER 物件資訊
`docker inspect [OPTIONS] [ID/NAME]`
#####  [OPTIONS]
```
-f, --format 將結果format
-s, --size 完整file size
--type
```

## Image

#### 確認目前 images
`docker images`
##### [OPTIONS]
```
-a 完整資訊
-q 只列出ID  
```

#### 從 ducker hub下載 image
`docker pull [OPTIONS] [REPOSITORY[:TAG]]`
#####  [OPTIONS]
```
-a 所有tag的映像檔
REPOSITORY 需要的image
TAG 指定image的tag
```

#### 將 IMAGES 存入本機
`docker save -o [FILE.tar] [REPOSITORY[:TAG]]` 適合多平台
`docker save [REPOSITORY[:TAG]] > [FILE.tar]` STDOUT，接收方可能會無法load
##### [OPTIONS]
```
-o, --output 寫成檔案
```

#### 讀取 LOCAL IMAGES 進入 container
`docker load -i [FILE.tar]` 適合多平台
`docker load < [FILE.tar]` STDIN，接收方可能會無法load

##### [OPTIONS]:
```
-i, --input 讀取檔案
```

#### 刪除 image
`docker rmi [IMAGE ID/NAME]`
******
## Container

#### 透過 iamge 執行並產生一個新的 container
`docker run [NAME] [OPTIONS] [REPOSITORY[:TAG]] [COMMEND]`
ex.`docker run --name test -it -p 5000:5000 python:3.7 /bin/bash`
##### [NAME]
```
--name  給定啟動的container名字
```

##### [OPTIONS]
```
-i, --interactive 互動模式，鍵盤輸入會被Container接手
-t, --tty         配置一個終端機，Container的螢幕會接到原來的螢幕上。
-d, --detach      在背景執行
-p, --port        使用指定通訊埠進行網路通訊，指定本機port 對應 container port
```
##### [COMMEND]
```
開啟後執行的指令如 bash, /bin/bash
```
#### 查看執行中的 container
`docker ps`
##### [OPTIONS]
```
-a 所有的 container
```

#### 啟動 container
`docker start [Container ID/NAME]`

#### 執行 container 從外部向執行中的Container下指令
`docker exec -it [NAME] [COMMEND]`
##### [COMMEND]
```
開啟後執行的指令如 bash, /bin/bash
```

#### 從外部/Container 複製檔案到 container/外部
`docker cp [OPTIONS] CONTAINER:SRC_PATH DEST_PATH`
`docker cp [OPTIONS] SRC_PATH CONTAINER:DEST_PATH`

#### 將修改後的 container 提交存成 image
`docker commit [OPTIONS] [Container ID/NAME] [REPOSITORY[:TAG]]`
##### [OPTIONS]
```
-a, --author  e.g. "Brad Pitt"
-c, --change  Apply Dockerfile instruction to the created image
-m, --message Commit message
-p, --pause   Pause container during commit
```

#### 給定 tag
`docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]`

#### 停止 container 不佔記憶體，服務中斷
`docker stop [Container ID/NAME]`

#### 強制停止 container
`docker kill [Container ID/NAME]`

#### 重新啟動 container
`docker restart [Container ID/NAME]`

#### 暫停 container
`docker pause [Container ID/NAME]`

#### 解除暫停 container
`docker unpause [Container ID/NAME]`

#### 刪除 container
`docker rm [Container ID/NAME]`
