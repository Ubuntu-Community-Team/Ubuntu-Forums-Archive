---
title: "Segmentation fault running a php script from crontab"
date: 2009-01-05
forum: Server Platforms
---

### Post by chrislynch8 on 2009-01-05
Hi I am getting the following mailed to www-data when I try and run a php script in the crontab

[HTML]
From www-data@server01.our.org  Mon Jan  5 17:26:01 2009
Return-Path: <www-data@server01.our.org>
X-Original-To: www-data
Delivered-To: www-data@server01.our.org
Received: by server01.our.org (Postfix, from userid 33)
        id 8947346048C; Mon,  5 Jan 2009 17:26:01 +0000 (GMT)
From: root@server01.our.org (Cron Daemon)
To: www-data@server01.our.org
Subject: Cron <www-data@server01> cd /var/www/crm/test/fdc; php -f cron.php > /dev/null2>&1
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/usr/mjk>
X-Cron-Env: <HOME=/var/www>
X-Cron-Env: <LOGNAME=www-data>
Message-Id: <20090105172601.8947346048C@server01.our.org>
Date: Mon,  5 Jan 2009 17:26:01 +0000 (GMT)

/bin/sh: line 1: 10434 Segmentation fault      php -f cron.php > /dev/null 2>&1
[/HTML]

The odd thing is that i can run the script in command line and via the URL and I get no errors and the script runs just fine. 

My PHP version is 5.1.2 (cli) (built: Jul 23 2008 17:01:17
OS Dapper 6.10 kernel 2.6.15-53-amd64-server

---

