---
title: "How can deployed my application on ubuntu server 9.04 ?"
date: 2009-05-01
forum: Server Platforms
---

### Post by hoboy on 2009-05-01
I am very new to ubuntu server.
I have made some jsf/java/ application witch is packed as WAR file.
As I want to learn ubuntu server I have installed ubuntu in Sun VirtualBox.
so, Sun virtualbox is the guest runing ubuntu server 9.04.
and Vista as host,this is where the virtualBox is installed with ubuntu server.
My problem is now how can I put the war file ander the tomcat engine that is runing on ubuntu server on the virtualbox ?
because I have programmed the application using NetBeans on vista,so i have the WAR file that should come to ubuntu server.
I had anticipate to to use ftp, but I can't connect to the virtualBox.

---

### Post by i.r.id10t on 2009-05-01
apt-get install openssh-server on the ubuntu side.  Then use winscp to copy from the windows to ubuntu

---

### Post by hoboy on 2009-05-02
> **i.r.id10t said:**
> apt-get install openssh-server on the ubuntu side.  Then use winscp to copy from the windows to ubuntu
When I login to virtualBox I come here:Test-test@kr-PC:~$

openssh-server. Is installed.
when I ifconfig, I get inet addr:10.0.2.15;Bcast:10.0.2.255
Then I try to connect using winscp
host name:10.0.2.15,
port:3389
user name:Test-test,
and the correct password.
when I click on winscp login I get: Network error :Connection refused.

---

