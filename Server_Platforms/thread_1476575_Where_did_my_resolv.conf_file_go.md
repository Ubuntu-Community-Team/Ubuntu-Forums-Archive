---
title: "Where did my resolv.conf file go?"
date: 2010-05-08
forum: Server Platforms
---

### Post by 1serveyou on 2010-05-08
I tried to setup a dyndns, and ever since I tried to get that setup, I can't access my webmin, or access /etc/hosts/resolv.conf. But I can still access my samba shares I had created before this happened. Thanks in advance on any help!

---

### Post by volkswagner on 2010-05-08
What version are you running.  My systems, 8.04 and 9.04 both are located at /etc/resolv.conf not /etc/hosts/resolv.conf.

You should be more informative with your post so we can help.

How are you currently connecting to the machine, ssh, putty, etc.?

---

### Post by 1serveyou on 2010-05-08
> **volkswagner said:**
> What version are you running.  My systems, 8.04 and 9.04 both are located at /etc/resolv.conf not /etc/hosts/resolv.conf.

You should be more informative with your post so we can help.

How are you currently connecting to the machine, ssh, putty, etc.?

I could of sworn last night I tried that (/etc/resolv.conf) and it didn't work, but now I just did and it worked. I'm using putty to connect to my server. I thought I might have changed something in my resolv.conf file but I don't see anything different. 

I'm using 9.10, with Samba4(I wasn't able to download a previous version of Samba as I'm a new to Ubuntu and just downloaded the newest version. I apologize for the lack of information, I'm usually a little more thorough.

Any ideas on why I can't connect with webin?

I forgot to mention, I have another physical server on the network and I can connect to webmin with that one though.

---

### Post by CharlesA on 2010-05-08
resolv.conf is in /etc/resolv.conf in 10.04 as well.

How are you trying to set up dyndns?

---

### Post by 1serveyou on 2010-05-08
Fixed it, not sure when it changed back, because the past week or two I haven't had much time to play with it, but found the problem. I'm on comcast, and for some reason for their DNS address always has a period at the end of it and when I checked my resolv file the period was back at the end of it. Next I restarted the network(ing) which gave me an error, and I apologize I can't remember the error, but after I restarted putty, I did the network restart and it went though. Tried webmin and worked!

How do I change this to solved?

I still haven't been able to get dyndns to work, but from talking to my brother I need to setup apache and stuff to get it to work.

---

### Post by Iowan on 2010-05-08
> **1serveyou said:**
> How do I change this to solved?[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

