---
title: "Free FTP Storage"
date: 2009-05-18
forum: The Cafe
---

### Post by abhiroopb on 2009-05-18
I have 70gb of music which I would like to upload to a ftp server and be able to stream to my mobile phone.

I would like to do this for. I know that is probably an unreasonable request, but doesn't hard to ask. Are there any services which offer FTP service and come close?

---

### Post by abhiroopb on 2009-05-19
bump!

---

### Post by mr.propre on 2009-05-19
There is no free "good" solution. But you can setup a small home server and connect to the internetz.

---

### Post by gnomeuser on 2009-05-19
You somehow expect that someone will offer a service that will allow you to take up 70gb of data plus your bandwidth usage.. for free.

I believe it's time to examine your assumptions about reality. 

What would possibly be the revenue stream for such a service to cover the costs?

---

### Post by abhiroopb on 2009-05-19
Comments like this give me a headache. What was the point of that? Firstly, [adrive]("http://www.adrive.com/") offers 50gb of storage BUT does not support ftp. So, yes there are companies that offer so much free space.

I started this thread to get feelers, perhaps there are some services that offer it. I'm not SO keen on it that I am willing to spend money on it, but if it exists then I would like to use it.

Please examine your assumptions about the motivation of others before you post unnecessary comments.

---

### Post by abhiroopb on 2009-05-19
> **mr.propre said:**
> There is no free "good" solution. But you can setup a small home server and connect to the internetz.

Are there any "bad" solutions? :P! Can you suggest any links where I can see how to set-up a home server?

---

### Post by ad_267 on 2009-05-19
[https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html)

You can use a dynamic dns service like dyndns ([https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS), [http://www.dyndns.com/](http://www.dyndns.com/)) to get a domain name to point to your home ip address (don't need this if you have a static IP), and use port forwarding on your router to forward the ports required by FTP to your computer.

---

### Post by MikeTheC on 2009-05-19
> **ad_267 said:**
> [https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html)

You can use a dynamic dns service like dyndns ([https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS), [http://www.dyndns.com/](http://www.dyndns.com/)) to get a domain name to point to your home ip address (don't need this if you have a static IP), and use port forwarding on your router to forward the ports required by FTP to your computer.

That's what I've done before. You'll have to check into whether your ISP will tolerate such behavior. I was with TimeWarner up until Comcast bought out the local account, and they never complained. Of course, the traffic to my server was relatively minimal. Heck, both hard drives put together only gave me 70GB of space, with obviously some amount of that taken up by the OS and apps.

Personally, I would suggest using SFTP and not FTP because it's more secure, but that's just me.

---

### Post by monsterstack on 2009-05-19
Setting up your own server is the best option for you, I'm afraid. At least that way you're only limited by the size of your hard-disk. Get a battered old computer, stick Ubuntu Server on it, and then put it in a closet someplace and forget about it. That's what I did. You can get domain names cheaply these days, too.

---

### Post by gn2 on 2009-05-19
Sounds like you need an NSLU2.
I have one and it's excellent.

---

