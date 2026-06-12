---
title: "How to setup multiple server"
date: 2013-11-28
forum: Server Platforms
---

### Post by zylmak on 2013-11-28
Hi I have 3 servers behind a router all port on the router are set to point to the server 1

On the web I have a name server for server1.mydomain.com  server2.mydomain.com  server3.mydomain.com who point to the same IP address
witch is the router 

What I would like to do is if I do ftp.server1.mydomain.com it connect to server1 and I do ftp.server3.mydomain.com it connect to server3
same thing for ssh and http

For http I found the way in http config so if I enter [http://server3.mydomain.com](http://server3.mydomain.com) it show the page on server3 and if I do [http://server2.mydomain.com](http://server2.mydomain.com) it goes to server2

the problem is if I ftp to server2 or server3 it always connect to server1

Same has for ssh

How Do I configure ftp and ssh so it goes to the right machine ?

---

