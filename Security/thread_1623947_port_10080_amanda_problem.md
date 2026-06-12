---
title: "port 10080 amanda problem"
date: 2010-11-17
forum: Security
---

### Post by pepsifx357 on 2010-11-17
I did a port scan on my server from outside my network and saw that port 10080 AMANDA is open.

Amanda isn't installed on any of my computers or my server and the port is not forwarded by my modem or router.  So why is this port open and how can I close it?

---

### Post by brian_p on 2010-11-17
> **pepsifx357 said:**
> 

So why is this port open and how can I close it?

It won't be AMANDA.

```
sudo lsof -i:10080 

```

---

### Post by pepsifx357 on 2010-11-17
> **brian_p said:**
> It won't be AMANDA.


That sounds serious...

Edit:  Now port 8080 is open along with 10080.

I tried the ```
sudo lsof -i:10080
``` and got no response.  The port is still open.

---

### Post by brian_p on 2010-11-17
> **pepsifx357 said:**
> That sounds serious...

Why?

> I tried the ```
sudo lsof -i:10080
``` and got no response.  The port is still open.

No response means nothing is on port 10080 of your server. Try 8080.

Your scan didn't scan your server - it scanned your router. 10058 isn't forwarded to your server so it doesn't go anywhere.

---

### Post by pepsifx357 on 2010-11-17
Nothing on the server other than 22, 80, and 10000.  Which are supposed to be there.  So I guess I'm good?

---

### Post by FuturePilot on 2010-11-17
> **pepsifx357 said:**
> So I guess I'm good?

No, I would investigate your router. There's most likely some remote admin enabled which could lead to trouble.

---

### Post by pepsifx357 on 2010-11-18
Thanks for the help guys.  I'll be paying close attention to my router and modem for this problem.

---

### Post by progone on 2012-01-07
Out of curiosity, are you using ddns or any other dns type of service or perhaps openstack?  

I have the same issue. My router is a Linksys

---

### Post by progone on 2012-01-07
This might be our AMANDA 

[http://www.amanda.org/](http://www.amanda.org/)

> AMANDA, the Advanced Maryland Automatic Network Disk Archiver, is a backup solution that allows the IT administrator to set up a single master backup server to back up multiple hosts over network to tape drives/changers or disks or optical media. Amanda uses native utilities and formats (e.g. dump and/or GNU tar) and can back up a large number of servers and workstations running multiple versions of Linux or Unix. Amanda uses a native Windows client to back up Microsoft Windows desktops and servers.


checkout this link in their forums

[http://forums.zmanda.com/showthread.php?t=3424&highlight=port+10080](http://forums.zmanda.com/showthread.php?t=3424&highlight=port+10080)

If you didn't put AMANDA or download any other type of BACKUP app/service from Synaptic you just might be hacked.  As for me, I have a backup service going, however I am still going to investigate my backup service a little further to see if it is AMANDA related.

---

### Post by pepsifx357 on 2012-01-20
> **progone said:**
> Out of curiosity, are you using ddns or any other dns type of service or perhaps openstack?  

I have the same issue. My router is a Linksys

I just saw your post.  Yes, at the time I was using ddns for my webserver.  And Yes, I also had a linksys.

---

