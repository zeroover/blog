---
title: Docker入门
date: 2020-06-01
tags:
 - docker 
 - vm
categories:
 - 笔记
---


## 安装docker
1. 卸载旧版本


```sh
$ sudo yum remove docker \
            docker-client \
            docker-client-latest \
            docker-common \
            docker-latest \
            docker-latest-logrotate \
            docker-logrotate \
            docker-engine
```

2. 安装依赖
   
```sh
$ sudo yum install -y yum-utils \
         device-mapper-persistent-data \
         lvm2
```

3. 设置稳定的仓库
   
```sh
$ sudo yum-config-manager \
      --add-repo \
      https://download.docker.com/linux/centos/docker-ce.repo
```

4. 安装最新版docker
   
```sh
$ sudo yum install docker-ce docker-ce-cli containerd.io
```

## 设置阿里云镜像

[https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors)

```sh
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://xxx.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```


## 安装docker-compose

```sh
$ sudo curl -L "https://github.com/docker/compose/releases/download/1.25.5/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
//如果速度太慢可以换成下面的地址执行
$ curl -L https://get.daocloud.io/docker/compose/releases/download/1.25.5/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose

$ sudo chmod +x /usr/local/bin/docker-compose

$ sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```