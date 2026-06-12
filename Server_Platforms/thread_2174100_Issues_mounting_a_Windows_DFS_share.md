---
title: "Issues mounting a Windows DFS share"
date: 2013-09-12
forum: Server Platforms
---

### Post by cesarb714 on 2013-09-12
We're trying to mount DFS shares on our Linux servers (ubuntu and centos). I can mount it fine using cifs-utils. The problem occurs when we shut off our local DFS server. None of the linux boxes are able to hit the remote DFS shares. With DFS it should matter what server we are pulling files from, if it goes down it is supposed to pick up the next one in line. 

Ubuntu doesn't really give much of an error, just says no such device or address

CentOS gave me a little bit more but I dont have it in front of me to look.

---

### Post by Vegan on 2013-09-12
I use Hyper-V and I run Ubuntu in a VM fine.

What version of storage server are you using? These days MSFT is using storage groups which can contain virtual machine images etc

---

