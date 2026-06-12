---
title: "Can't connect to MS Sql Server from PHP - What do I have to install / configure?"
date: 2018-11-07
forum: Server Platforms
---

### Post by aaaa42 on 2018-11-07
- Ubuntu Server 16.04

-PHP: PHP 7.0.32-0ubuntu0.16.04.1

-Apache: Server version: Apache/2.4.18 (Ubuntu)
Server built:   2018-04-18T14:53:04



Hello, I have a Ubuntu Server 16.04, with PHP and Apache .....

I am trying to connect a small app to a Ms Sql Server from PHP, and I am trying to configure the frame.... mssqltools.... sqlcmp..... drivers... extensions.... openssl.... but I can't get and even I don't have clear what I really need....

I can't connect... differents kinds of errors.... and so....

I am trying to start from zero... and first of trying anything else I would like to resolve some doubts (in fact I am rather new in Ubuntu and Linux in general).... 


- Would be enough installing the extesion php7-sybase or I need mssqltools and more.... in my Ubuntu Server ??????

- Is it necesary openssl ?????

- I am trying to install just sqlcmd to try to connect to the server.... without results.  Is it necesary (sqlcmd) ????  To get installing and working sqlcmd is necesary install MsSql Server??? 

I have read one hundred tutorials without results.... trying this... that.... downgrading versions....

Please, what steps might I go on?? What do I really need in my Ubuntu Server? What about my doubs???

Regards.

---

### Post by howefield on 2018-11-07
Thread moved to the "*Server Platforms*" forum.

---

### Post by chipmand on 2018-11-21
Try installing php-odbc? MS SQL Server uses ODBC allow connections to it. I'm on 18.10 here, but you could try "apt-cache search odbc" to find the ODBC-related packages. There are lots, for different software that can connect using ODBC. Good luck!

---

### Post by SeijiSensei on 2018-11-21
First, try php-odbc.

Then if you can, replace MS SQL server with an open-source alternative. I prefer PostgreSQL over MySQL myself.  Both of them are much better supported than MS SQL in open environments like Linux.

---

