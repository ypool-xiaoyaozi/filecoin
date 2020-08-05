官方博客：https://filecoin.io/zh-cn/

源码仓库：https://github.com/filecoin-project

lotus开发文档：https://docs.lotu.sh/

go-filecoin开发文档：https://go.filecoin.io/go-filecoin-tutorial/Home.html

英文版白皮书：https://filecoin.io/filecoin.pdf

区块浏览器:https://stats.testnet.filecoin.io/   https://filscout.io/zh   https://filscan.io/#/   https://filfox.io/zh

spces设计文档: https://filecoin-project.github.io/specs/

filecoin文档：https://docs.filecoin.io/

测试网第二阶段相关下载链接：
filecoin挖矿需要下载proof证明文件，才能顺利接入测试网：
https://proofs.filecoin.io/
或者使用环境变量：export IPFS_GATEWAY="https://proof-parameters.s3.cn-south-1.jdcloud-oss.com/ipfs/"
运行环境变量后运行此命令：./lotus fetch-params 32G

经济模型：https://filecoin.io/blog/filecoin-cryptoeconomic-constructions/

甘特图：https://app.instagantt.com/shared/s/1152992274307505/latest

rust的安装环境配置（Cargo）： 官方文档：https://www.rust-lang.org/tools/install  社区文档：https://learnku.com/docs/rust-lang/2018/ch01-01-installation/4494

Filecoin Discover： 官方中文博客https://filecoin.io/zh-cn/blog/intro-filecoin-discover/

奖励网初始化命令lotus-miner init --actor=t04464 --owner=t3wpbw6ew4bgrufsndzboutey4xyy23qjjc4cgmbiworvssslgkjh7k645eqv3i42xdud333urtge2zcjj4dca
如果竞赛网有智障还是疯狂的刷ID：./lotus-miner init --owner=t3.... --sector-size 32GiB

简单叙述如何将自己的矿工暴露出去。接到存储订单

相关查看命令：lotus-miner net listen lotus-miner net peers

开始步入正轨

  vi .lotusminer/config.toml
  
  修改地方为
  
        ListenAddress = "/ip4/0.0.0.0/tcp/2345/http"
        
        RemoteListenAddress = "0.0.0.0:2345"
        
        ListenAddresses = ["/ip4/0.0.0.0/tcp/5472"]
        
        AnnounceAddresses = ["/ip4/1.2.3.4/tcp/26164"]
        
        修改后重启lotus-miner
        
  lotus-miner netid
  
  lotus-miner actor set-addrs /ip4/1.2.3.4/tcp/26164/p2p/id
  
  cat /lotus/build/bootstrap/bootstrappers.pi 查看之后可执行一下内容可修改
  
  lotus-miner net connect /dns4/bootstrap-3.calibration.fildev.network/tcp/1347/p2p/12D3KooWJt4zgPL8B2cMoCLDQ6MPpMKH62ZjgvvPmrfDBLWpggKG（此内容可变动）
  
  相关排查命令
  
  lotus client query-ask t0xxx
  
  lotus state miner-info t0XXX
  
  lotus-miner storage-deals list
  
  lotus client deal 
