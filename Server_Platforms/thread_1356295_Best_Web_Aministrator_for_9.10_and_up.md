---
title: "Best Web Aministrator for 9.10 and up?"
date: 2009-12-15
forum: Server Platforms
---

### Post by Vegan on 2009-12-15
So I have finally make progress after a headache or 5 that Excedrin could not tough.

So one idea was a remote desktop, how about a browser to administer the machine?

---

### Post by windependence on 2009-12-15
SSH? Screen? Terminal? All have the widest set of admin tools available.

-Tim

---

### Post by erict43 on 2009-12-15
Webmin is pretty nice for web-based administration.  I use it on a production server at work.

---

### Post by BkkBonanza on 2009-12-16
Webmin is likely a good choice for a free one. The really popular admin panels like CPanel and DirectAdmin etc. cost a lot to install.

---

### Post by Vegan on 2009-12-16
> **erict43 said:**
> Webmin is pretty nice for web-based administration.  I use it on a production server at work.

I take it that its easy to use and stable?

---

### Post by i.r.id10t on 2009-12-16
What are you trying to admin? If it is websites, DNS, email then check out ISPConfig

---

### Post by Vegan on 2009-12-16
I checked to see if that isp tool was in the repository, did not find it. If there another name for it I missed?

---

### Post by CharlesA on 2009-12-16
> **BkkBonaza said:**
> Webmin is likely a good choice for a free one. The really popular admin panels like CPanel and DirectAdmin etc. cost a lot to install.

I second webmin. I use it to configure samba, ssh and iptables. (cuz I am lazy :P)

> **Vegan said:**
> I take it that its easy to use and stable?

It's easy to install since it comes in a .deb package.

> **Vegan said:**
> I checked to see if that isp tool was in the repository, did not find it. If there another name for it I missed?

Check here maybe? [http://www.ispconfig.org/](http://www.ispconfig.org/)

---

### Post by MikeyPooh on 2009-12-16
ebox is a nice web interface server admin tool, I Have used it several timnes, It makes life alot simpiler :KS


Mike

---

### Post by cj13579 on 2009-12-16
> **erict43 said:**
> Webmin is pretty nice for web-based administration.  I use it on a production server at work.

+1 for Webmin here. I have been using it for a while and have nothing but good things to say about it. 

This is a really good tut for installation/setup: 

[http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html](http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html)

---

### Post by penguin_patrick on 2009-12-16
+1 for webmin.  very nice.

---

### Post by Iowan on 2009-12-16
[eBox]("https://help.ubuntu.com/9.04/serverguide/C/ebox.html")?

---

### Post by mchecca on 2009-12-16
Haven't got around to using eBox, but I do use Webmin and it works amazingly for Apache, ProFTPD, and even has a file manager which is pretty cool. Also has a .deb package so it's simple to install.

---

### Post by Vegan on 2009-12-16
That ISPconfig tool looks attractive but version 3 looks like its still in beta. Curious why its not in the repository either. Looks like Ubuntu only likes ebox so far.

Seems Ubuntu is not really helping admins as much as they could with helpful software. :(

So from I stand ebox looks like the only choice for my server with automatic updates.

---

### Post by HighCommander540 on 2009-12-17
> **Vegan said:**
> That ISPconfig tool looks attractive but version 3 looks like its still in beta. Curious why its not in the repository either. Looks like Ubuntu only likes ebox so far.

Seems Ubuntu is not really helping admins as much as they could with helpful software. :(

So from I stand ebox looks like the only choice for my server with automatic updates.

Yeah, webmin isn't in the repository either, but if you want something. Its part of being an admin. You need to do **** yourself. Once you know what to do then you can be lazy. From what I hear eBox isn't as good as webmin...

---

### Post by Jethro_uk on 2009-12-18
+1 for Webmin here

my (Linux geek) brother installed it yesterday, and already it has changed my life !!!!! I was struggling to administer ProFTPd, and within a few minutes of using Webmin I fixed it all. Looking at it's other features it is a brilliant piece of code ... It even lets you edit GRUB ...

It's already transformed my view of Ubuntu .... I reckon if a bit of polish was rubbed over Webmin, you'd have the basis for a very, very real contender to the *dows stable of offerings.

And I've been using Linux for 2 years !

---

### Post by kadeous on 2009-12-18
+1 for Webmin, it's gotten me up and running with little knowledge and some google searching. :)

---

