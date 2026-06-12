---
title: "Proftpd behind router/firewall"
date: 2008-07-07
forum: Server Platforms
---

### Post by MarioFromBelgium on 2008-07-07
Hi,

I have a working Ubuntu Server with a working proftpd. That is from within my LAN I can make a connection to my ftp-server.

The ftp-server is listening to port 7003.
Now I configured my router-firwall that he NATs requests on port 7003to port 7003 on the server.

The result is that from the internet I reach my server, I authenticate but than...nothing.
(PS. the NAT-translating works fine for http and putty, on other ports ofcourse. This just to show that the router works)

I think it has somthing to do with what is mentioned in
[http://www.proftpd.org/localsite/Userguide/linked/x862.html](http://www.proftpd.org/localsite/Userguide/linked/x862.html)
and below in
[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

If it has nothing to do with that, than what I'm I doing wrong?
If it has something to do with that, could anybody explain me so it is dummy-proof.

Thx

---

### Post by MarioFromBelgium on 2008-07-07
Oh yes,
I forgot to say that when proftpd listened at port 21 and the router NATted 21 to 21 to the server everything worked.

But since port 21 is blocked at where I work, I want it to listen to another port between 7000 and 7100

---

### Post by jorge.maravi on 2008-07-07
Are you using FTPES?

---

### Post by MarioFromBelgium on 2008-07-08
What is FTPES?
What I dit is install proftp with apt-get and change the config-file so that it listens to port 7003

Thats all.

---

### Post by horeon on 2008-07-08
Hi,

When you install a ftp server you have two distinct port :
21 to authentification
and if you have in passive mode, the server negociate a random port to send datas.
or if you're not in a passive mode it's a port 20.

Verify you router manage "ftp passive mode".

Hope that help you.

---

### Post by MarioFromBelgium on 2008-07-09
Let me see if I get this right:

1°
if I leave the port to 21 in proftpd.conf (the way it is by default) the authentication is done through port 21 but datatransfer through 20

2° if I change the port to something else like 7003 than authentication is through 7003 but datatransfer is through a randomport.

---

### Post by jorge.maravi on 2008-07-12
I just got my ftp server working
Why don't you take all the default ports by default make sure it works and then customize your server?

---

