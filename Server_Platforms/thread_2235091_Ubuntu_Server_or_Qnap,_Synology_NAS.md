---
title: "Ubuntu Server or Qnap, Synology NAS?"
date: 2014-07-18
forum: Server Platforms
---

### Post by alex228 on 2014-07-18
Hello everyone!  I have never used linux before but i have heard that it can be a pretty powerful tool.  Any way I am in need of a NAS, cloud, torrent, media server machine and i am wondering as to what route i should take.  The other thing is i would need to be able to access it from my android phone and a surface pro tablet.  I also need to be able to send a link to friends and family so that they can download something stored on the NAS.   If i were to go ubuntu and build a new small machine is it hard to get all of those functions setup and working or are then even all available?  Another concern of mine would be security/antivirus.  

The system that i would probably build would be:
case:  [http://www.newegg.com/Product/Product.aspx?Item=N82E16811147218](http://www.newegg.com/Product/Product.aspx?Item=N82E16811147218)
MB: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813157491](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157491)
CPU:  [http://www.newegg.com/Product/Product.aspx?Item=N82E16819113364](http://www.newegg.com/Product/Product.aspx?Item=N82E16819113364)
RAM: 4 or 8 gb not sure which yet

If i were to go with a NAS the one that seems to be the best bang for buck would be the qnap ts-269L or a similar synology nas, but qnap has better hardware compared to the synology ones.   Software wise they seem pretty similar and i think both would serve the purpose.

So what are your thoughts?

---

### Post by TheFu on 2014-07-19
Do you like having complete control over your systems or do you just want to plug it in and forget it?  Linux servers don't have a GUI and you need to know what to type for controls.  It can be extremely frustrating for the first few years as the learning curve is steep - like learning a new language.  

Plus Linux has a different design philosophy which can be a struggle for non-programmers. I write a few scripts weekly to get things done. If that isn't you, buy the pre-paid NAS for 3x more money. It will save you time - hundreds of hours.  Every time I look at storage solutions and compare the flexibility, features, and costs - I run back to a home built solution.  BTW, I've worked with and designed computer systems from 1-pc for Mom to a $20M set of systems used in telecom, including $M in SAN storage from EMC, Dell, HP, IBM, and others.  I've seen the capabilities and have been trained on them by the higher-end vendors.

OTOH, if you have interest, time and aptitude, there is nothing like running your own linux servers. Eventually, they will do almost anything you ask. You'll become a scripting wizard - perl, python, bash, ruby and others - to get things accomplished. You'll wonder why all those people waste their time with GUIs for non-interactive tasks and you may even grow a beard.  I started learning Linux in 1993 and I'm still learning.  It has created career opportunities and allowed me to retire in my 40s that I can't imagine happening from any other career choice (at least for me).

Halfway between "pay-your-money" and "build-your-own" solutions is FreeNAS (or the fork).  If you follow their advice and have the budget for a good system ($1200 min) it is a great solution and is a little more flexible.

---

### Post by tgalati4 on 2014-07-19
Neckbeards for Freedom!  Search the forums and the web in general for experiences with both qnap and synology.  You will find some similar themes:  They work, but when you try to do something fancy--you can't because the operating systems (proprietary linux) are limited and you wonder why a simple feature is not implemented.  Of course you won't appreciate the limitations until you have built your own freenas box or just set up a linux server with extra drives.

TheFu summarizes the build-your-own approach nicely.  If you have the money and don't care (or understand) the limitations then buy an off-the-shelf NAS and be happy.  If it fails, recovery can be difficult, but that is another discussion.

---

### Post by TheFu on 2014-07-19
> **tgalati4 said:**
> Neckbeards for Freedom!  

Good points!  I was afraid that I'd overstated the build-your-own difficulty. It is hard for me to remember back when I was learning anymore.

Shaved my neckbeard last month during YAPC:NA conference.  Guess I'm out of the club now. ;(

---

### Post by alex228 on 2014-07-19
Thanks for your input.  I think for now I am going to go with a pre built NAS then.  I am a little worried that I just wouldn't be able to config a Ubuntu server to do what I want at least not right away, as you said it has a steep learning curve.  I will most likely still build that other system and load Ubuntu server on it but not right away maybe a few months down the road.

---

### Post by TheFu on 2014-07-19
If you are buying, look for a solution that supports NFS, not just CIFS.  NFS works great with UNIX-like OSes and provides native file/directory permissions that CIFS cannot.

---

### Post by tgalati4 on 2014-07-19
It takes 10 years to really learn linux, but only a couple to get a really good neckbeard going.  So after using your off-the-shelf nas for a couple of years, you will be pulling your hair out because you can't do this or that.  By then, you will be able to build your own server and have a stylish [neckbeard]("http://blogs.westword.com/latestword/2013/10/best_neckbeards_in_history_andrew_luck.php").

---

