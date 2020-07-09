## Alertmanager告警对接第三方接口

1. 因统计数据格式差异较大，对于云平台promeheus监控体系，技术上统一监控中心的zabbix体系无法适配。

2. 云平台内部监控使用Prometheus， Grafana等组件，以operator形式部署。由alertmanager 发送OCP平台产生的告警信息，通过webhook形式转发给定制插件，把消息转发统一监控中心。

3. 告警对接:由统一监控中心提供告警接口(http post)文档与测试环境， 协助云平台在测试环境测试验证通 过后，接入正式环境。


## 项目构建方法

1. 安装Docker Daemon, 注意版本高于v19.3

~~~
    # docker version
    Client: Docker Engine - Community
     Version:           19.03.4
     API version:       1.40
     Go version:        go1.12.10
     Git commit:        9013bf583a
     Built:             Fri Oct 18 15:52:22 2019
     OS/Arch:           linux/amd64
     Experimental:      false
~~~

2. git clone 项目

~~~
    git clone https://github.com/yekaifeng/alertmanager-zabbix-webhook.git
~~~

3. 构建镜像

~~~
    cd alertmanager-zabbix-webhook
    docker build -t alertmanager-zabbix-webhook-cmic:1.0 .
~~~
