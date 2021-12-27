# OneNav
使用PHP + SQLite 3开发的简约导航/书签管理器，xiaoz新作，欢迎体验。

![](https://i.bmp.ovh/imgs/2020/12/40f222b7da7a89c9.png)

![](https://i.bmp.ovh/imgs/2021/04/5c46f84f158d8d3a.png)

![](https://i.bmp.ovh/imgs/2020/12/7a1eee25c16d2d81.png)

![](https://i.bmp.ovh/imgs/2020/12/abba0af566f3c16a.png)

## 功能特色

* 支持后台管理
* 支持私有链接
* 支持书签批量导入
* 支持多种主题风格
* 支持链接信息自动识别
* 支持API
* 支持Docker部署
* 支持uTools插件

## 安装

**常规安装：**

1. 需安装PHP环境，并确保支持SQLite3
2. 下载源码解压到站点根目录
3. 将`config.simple.php`复制为`data/config.php`并填写自己的站点信息
5. 访问后台：`http://IP/index.php?c=login`

**Docker部署：**

```bash
docker run -itd --name="onenav" -p 80:80 \
    -e USER='xiaoz' -e PASSWORD='xiaoz.me' \
    -v /data/onenav:/data/wwwroot/default/data \
    helloz/onenav
```

* `USER`：设置用户名，上述设置为`xiaoz`
* `PASSWORD`：设置密码，上述设置为`xiaoz.me`
* `/data/onenav`：本机挂载目录，用于持久存储Onenav数据

更多说明，请参考帮助文档：https://www.yuque.com/helloz/onenav

## 安全设置

如果您使用得Nginx，请务必将以下规则添加到站点配置中，否则数据库可能被下载（非常危险）：
```#安全设置
location ~* ^/(class|controller|db|data|functions|templates)/.*.(db3|php|php5)$ {
    return 403;
}
location /db {
        deny all;
}

#伪静态
rewrite ^/click/(.*) /index.php?c=click&id=$1 break;
rewrite ^/api/(.*)?(.*) /index.php?c=api&method=$1&$2 break;
rewrite /login /index.php?c=login break;
```

如果使用得Apache则无需设置，已内置.htaccess进行屏蔽。

## Demo

以下是OneNav部分用户演示站，排名不分先后。

* OneNav：[https://nav.rss.ink/](https://nav.rss.ink/)
* 千行书签：[http://www.52qx.club/](http://www.52qx.club/)
* 纽及书签：[http://www.1006788.com/](http://www.1006788.com/)

## 联系我

* Blog:https://www.xiaoz.me/
* QQ:337003006
* QQ群：147687134
* 社区支持：[https://dwz.ovh/vd0bw](https://dwz.ovh/vd0bw)

## 鸣谢

OneNav诞生离不开以下项目，在此表示感谢（排名不分先后）。

* [WebStackPage](https://github.com/WebStackPage/WebStackPage.github.io)
* [LayUI](https://github.com/sentsin/layui)
* [Medoo](https://github.com/catfan/Medoo)
* [MDUI](https://github.com/zdhxiong/mdui)
