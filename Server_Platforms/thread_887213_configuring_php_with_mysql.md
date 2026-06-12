---
title: "configuring php with mysql"
date: 2008-08-11
forum: Server Platforms
---

### Post by sawatdee on 2008-08-11
I'm trying to install php so that is works with MySQL.

I installed the following ubuntu packages
[LIST]
[*]mysql-server
[*]mysql-client
[*]mysql-common
[*]mysql-client-5.0
[*]libmysqlclient15off
[*]libdbd-mysql-perl
[/LIST]
MySQL seems to work fine.

I downloaded php 5.2.6. I like to build php from source so that I can configure it the way I want. I ran

```
$ ./configure --with-apxs2=/usr/local/apache2/bin/apxs --with-gd --with-mysql --with-mysqli --with-pdo-mysql --enable-soap --with-libxml-dir

```


But I keep getting this error
```
configure: error: Cannot find MySQL header files under yes.
Note that the MySQL client library is not bundled anymore!

```

I downloaded the ubuntu source package mysql-dfsg-5.0_5.0.51a.orig.tar.gz, hoping that it would contain the header files I need. Then I set the --with-mysql option to the include directory in that source package, but I get the same error.

Any ideas as to how I can get php to configure?

---

