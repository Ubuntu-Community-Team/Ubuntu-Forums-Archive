---
title: "Local software update"
date: 2007-07-05
forum: Repositories &amp; Backports
---

### Post by SaitoSan on 2007-07-05
I hope I explain this well :D

Say I have a network of computers running Ubuntu on a rather slow internet connection where I can't afford for each computer to download the software update. Would it be possible for one of the computers to download the update and then the rest of the computers will get the update from the updated computer?

Thanks

Saito

---

### Post by solar george on 2007-07-05
I use apt-proxy,
you install it on your main machine (lets call this machine A) and point all of the /etc/apt/sources.list files to machine A on port 9999 (providing you haven't changed this), then all .debs (package files) that you download will be cached by this machine so that all other (local) machines will receive the local copy instead of downloading it.

Below is a sources.list line for the restricted and main sections of the feisty archive loading off 192.168.0.11 (change this to the ip of machine A)
```
deb http://192.168.0.11:9999/ubuntu/ feisty main restricted
```
the :9999 tell apt to connect to port 9999 of machine A which is the default proxy port.

---

### Post by SaitoSan on 2007-07-05
How do I then install the software update on the other computers? Do I do that by running apt-get update on the other computers?

Thanks for the reply bty.

---

### Post by SaitoSan on 2007-07-05
Do I need to comment the following line from the source list:
```
deb http://archive.ubuntu.com/ubuntu/ feisty main restricted

```
if I do your suggestion?

Do I have to set the IP address of machine A to be static then?

---

### Post by solar george on 2007-07-05
Machine A needs to have a static ip.

> Do I need to comment the following line from the source list:
Code:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted



You need to replace all mentions of archive.ubuntu.com or security.ubuntu.com with machine A's ip:9999

In my case machine A is on 192.168.0.11 so I put 192.168.0.11:9999 instead of archive.ubuntu.com.

You then just install software in the usual way.

---

