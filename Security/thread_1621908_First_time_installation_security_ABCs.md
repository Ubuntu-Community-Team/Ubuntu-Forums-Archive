---
title: "First time installation security ABCs"
date: 2010-11-14
forum: Security
---

### Post by zhaotianwu on 2010-11-14
Hi there. I'm going to install Ubuntu 10.10 system onto my netbook. Other than full-disk encryption with LUKS, I also want to ensure that the freshly installed system free of web-based threats. Can you provides some basic yet easy-to-follow security practices during the installation? Highly appreciated. Thanks.

---

### Post by The Thunder Chimp on 2010-11-14
My dad has a partition on which he doesn't even connect on the internet to be safe. He does his web surfing on the other partition.

That can be a 99% secure option.

---

### Post by Dex73 on 2010-11-14
use ufw (uncomplicated fire wall) no install required! Check this site for all the details.


[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by cariboo on 2010-11-14
There really isn't anything you need to do. Like I said in your other thread, in a default installation there are no ports open to the outside world., so you really don't even need a firewall, especially if you are behind a router.

Don't install any services like a web server or an ssh server. Go into System-Preferences->Startup Applications and remove the remote desktop server. Make sure you have a strong password.

---

### Post by zhaotianwu on 2010-11-14
> **cariboo907 said:**
> There really isn't anything you need to do. Like I said in your other thread, in a default installation there are no ports open to the outside world., so you really don't even need a firewall, especially if you are behind a router.

Don't install any services like a web server or an ssh server. Go into System-Preferences->Startup Applications and remove the remote desktop server. Make sure you have a strong password.

Thanks, but what are web server or an ssh server? And what is remote desktop server?

---

### Post by CharlesA on 2010-11-14
They are services that aren't installed/enabled by default.

---

### Post by zhaotianwu on 2010-11-14
> **The Thunder Chimp said:**
> My dad has a partition on which he doesn't even connect on the internet to be safe. He does his web surfing on the other partition.

That can be a 99% secure option.


This sounds like a very ingenious solution indeed! Can any expert throw in some thoughts on this? Is it advisable and safe to have two functioning partition(username), one is conneted to the internet, one is cut out, despite the fact that they share the same harddrive and BIOS?

---

### Post by CharlesA on 2010-11-14
> **zhaotianwu said:**
> This sounds like a very ingenious solution indeed! Can any expert throw in some thoughts on this? Is it advisable and safe to have two functioning partition(username), one is conneted to the internet, one is cut out, despite the fact that they share the same harddrive and BIOS?
It's overkill tbh.

---

### Post by zhaotianwu on 2010-11-15
> **CharlesA said:**
> It's overkill tbh.

Really? But the partition username A that is connected to the web and the partition user B that is insulated from the web still share the same physical harddrive and BIOS. Can any insidious malware take advantage of this?

---

### Post by CharlesA on 2010-11-15
> **zhaotianwu said:**
> Really? But the partition username A that is connected to the web and the partition user B that is insulated from the web still share the same physical harddrive and BIOS. Can any insidious malware take advantage of this?

What you are discribling is using two different user accounts, which doesn't use two separate partitions, only separate home directories.

The way Linux permissions work is that you don't have full read/write access to most of the file system unless you use sudo. You only have access to yer home directory.

That gives you a bit of protection, I suppose.

I can speak only for myself but if I had to switch user accounts or boot into a different OS just to access the internet, I would get tired of it quite quickly, but then again, I usually have a browser window open at all times.

If you really want to be safe, just use something like NoScript and AppArmor in firefox instead of going totally overboard.

Linux is not Windows, and using the Windows security mindset doesn't work.

---

### Post by zhaotianwu on 2010-11-15
> **CharlesA said:**
> What you are discribling is using two different user accounts, which doesn't use two separate partitions, only separate home directories.

The way Linux permissions work is that you don't have full read/write access to most of the file system unless you use sudo. You only have access to yer home directory.

That gives you a bit of protection, I suppose.

I can speak only for myself but if I had to switch user accounts or boot into a different OS just to access the internet, I would get tired of it quite quickly, but then again, I usually have a browser window open at all times.

If you really want to be safe, just use something like NoScript and AppArmor in firefox instead of going totally overboard.

Linux is not Windows, and using the Windows security mindset doesn't work.

Thank you CharlesA, especially for sharing your personal feeling about switching accounts, that makes me think it twice now. 

However I would still like to give it a try, how can I implement this: 
I encrypt a partition using LUKS, and store personal data on this partition. Then create a user account that solely deals with this partition and insulated from the Internet. Normally for each boot I do not even need to mount the LUKS encrypted partition, and when I mount that partition under that special user account, I can make sure that the Internet is cut off.

I'm going to do the alternate installation these days, could you provide a brief sketch regarding what steps I should go through to implement the above result? Thank you.

---

### Post by CharlesA on 2010-11-15
Never done that before tbh, but it shouldn't be that hard, since you can encrypt yer home directory during a normal install of Ubuntu.

---

### Post by cariboo on 2010-11-15
> **zhaotianwu said:**
> Thanks, but what are web server or an ssh server? And what is remote desktop server?

A web server is a service that serves web pages, like this forum. An ssh server allows to to connect securely to another computer via the command line, all communications between the two systems are encrypted. It is useful for maintaining servers that don't run a gui. Remote desktop allows you to take over the desktop on another computer, and operate it as though you were sitting in from of it. For more info:

[LIST]
[*][Web server]("http://en.wikipedia.org/wiki/Web_server")
[*] [SSH Server]("http://www.openssh.com/")
[*][Remote Desktop Protocol]("http://en.wikipedia.org/wiki/Remote _Desktop_Protocol")
[/LIST]

---

### Post by zhaotianwu on 2010-11-16
> **cariboo907 said:**
> There really isn't anything you need to do. Like I said in your other thread, in a default installation there are no ports open to the outside world., so you really don't even need a firewall, especially if you are behind a router.

Don't install any services like a web server or an ssh server. Go into System-Preferences->Startup Applications and remove the remote desktop server. Make sure you have a strong password.


Hi cariboo907, if there is no port open to the outside world, does it mean that by default your Ubuntu system cannot logon to the Internet, until you open some of those ports?

Also, should I login as root to remove the remote desktop server you mentioned above? Or I can do it as any user account? Thanks.

---

### Post by Johncena230 on 2010-11-16
I am first time installation security then installed problem on my system.

---

### Post by CharlesA on 2010-11-16
> **zhaotianwu said:**
> Hi cariboo907, if there is no port open to the outside world, does it mean that by default your Ubuntu system cannot logon to the Internet, until you open some of those ports?

Also, should I login as root to remove the remote desktop server you mentioned above? Or I can do it as any user account? Thanks.

There are no listening services installed by default, so that means you can access the internet just fine.

You should never login to a GUI as root. You can just remove that entry as your normal user.

---

### Post by zhaotianwu on 2010-11-17
> **CharlesA said:**
> There are no listening services installed by default, so that means you can access the internet just fine.

You should never login to a GUI as root. You can just remove that entry as your normal user.


So does it mean as an unprofessional user, I don't even know about root, and it won't do me any harm?

---

### Post by CharlesA on 2010-11-17
The root account is locked by default, meaning you can't login as root. You'd use sudo to do administrative stuff like installing programs and whatnot.

The password required is your user's password, not root's.

It doesn't mean it's foolproof, but nothing is 100% foolproof.

---

