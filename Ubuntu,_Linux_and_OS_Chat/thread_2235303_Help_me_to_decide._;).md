---
title: "Help me to decide. ;)"
date: 2014-07-20
forum: Ubuntu, Linux and OS Chat
---

### Post by mj_oralde on 2014-07-20
Hi there! I am one of those people who can't decide which distribution of linux to use, can someone please help me? I have a few questions.

I'm currently using a windows 8 os on my Dell Inspiron 3421 with an I3 processor and 4gb of ram. I want to install a linux distro alongside with my windows 8. I am planning to use linux as my os for programming cause some people say that its faster than a windows os.

 I have tried installing linux mint but it has that UEFI problem thing so I searched for other distros.

right now, I can't decide if I should go with Ubuntu or elementary os. :)

---

### Post by kc1di on 2014-07-20
Hie Mj_oralde and welcome to Ubutnu,

Of course this being a ubuntu forum you more likely to get advice to install ubuntu of some flavor, But since mint is derived from Ubuntu you will most likely have the same UEFI problem with it. and So is Elementary - though I think they may lag behind the ubuntu version a bit.  

IT's best to try each one with the Live media first - Remember they will be slower than an installed version and see which one fits your needs best.
[Then read this page]("http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported") and to install with dual boot window 8. 
good luck :)

With that said there is another way you may want to explore also you can run either windows or Ubuntu in Virtual Machine  (Virtual Box is available free in the repository)  You can read up on V.B.[ here. ]("http://www.n00bsonubuntu.net/content/install-virtualbox-ubuntu-14-04/")

---

### Post by coffeecat on 2014-07-20
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by Erik1984 on 2014-07-20
Just try both and see which one you prefer.

---

### Post by alias2234 on 2014-07-20
Thats the ting with Linux. 

You can try all distributions you want and choose one that works best for your hardware. 

Linux is fantastic in that regard.

Look on distrowatch.

---

### Post by Rob Sayer on 2014-07-20
There is no linux distro other than ubuntu that I'd recommend for newbies.  None of the others has nearly as good tech support as what is here and on askubuntu.

I've tried Mint and I consider their support pretty bad.  I actually had to use ubuntu support sites in mint because there didn't seem to be anyone there who knew anything about the subject I wanted.  From a quick look elementary OS is as bad or worse.

Besides, they're both based on ubuntu, but an older version.  Why not just use ubuntu unless you really have to have cinnamon?

That said, while I'm all for using linux, I wouldn't necessarily consider speed a good reason to use it.  It isn't necessarily faster.  Depends on the desktop flavor, and even then I wouldn't say it'd be faster without knowing what hardware you're talking about. 

I used the unity desktop for a little while and would not call it fast.  At all.  KDE (kubuntu) is big and not that fast as set up by default but you can configure it like crazy and get quite good speed.  Some don't like to do that much configuring though.

Xubuntu and lubuntu are much faster, especially the latter.  But lubuntu is harder to configure and I found lubuntu 14.04 too buggy.  I run kubuntu 12.04 on my i3 laptop and xubuntu 14.04 on my netbook.

I'll say one thing, though ... xubuntu is way faster on my netbook than the Windows 7 Starter it came with.  Now *that* was slow.  Good Lord.

What I'd suggest is getting all 4 ubuntu flavor live CDs and try them on a USB stick in live mode to get a feel for them before installing.  Unfortunately many linux newbies aren't aware there is more than one ubuntu.  Doubly unfortunate for the ones lately who are XP refugees using old computers that are too slow to run Unity properly.

---

### Post by stalkingwolf on 2014-07-20
I would suggest looking at distrowatch.  from there you can browse many of the distros, read about them then select 4-5 that interest you to download and try as live disks.

Generally speaking you will find people here that use almost all of the ubuntu flavors. I prefer the mint mate release, but have used about all of them at one time or another.

Again generally speaking any package available in synaptic package manager is available on all flavors.  If you find you like one distro and a different desktop environment you can install that DE.  One of the greatest things about Ubuntu/linux is choice.  As you go along if you find that you cant find exactly what you like you can build your own from scratch or use a release like mini to build what you want.

---

### Post by mj_oralde on 2014-07-20
thank you all for your replies. I have tried linux mint and lubuntu last night without installing it, but I got a problem for they are not detecting my usb wifi adapter so im about to try ubuntu now. thanks again :D

---

### Post by craig10x on 2014-07-20
Hope Ubuntu with unity will work for you...it's great ;)

---

### Post by mj_oralde on 2014-07-21
> **craig10x said:**
> Hope Ubuntu with unity will work for you...it's great ;)


i have installed it, but I cant get may alfa 036h wireless adapter to work. :(

---

### Post by deadflowr on 2014-07-21
Perhaps start a thread here
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

If anyone can help with the wifi adapter, it's the folks who frequent this area.

---

### Post by stalkingwolf on 2014-07-21
have you tried the linux driver from here?[http://www.alfa.com.tw/download_show.php?combo_0=11&combo_1=AWUS036H&combo_2=Driver&keyword=&verify=PTWT8J&x=29&y=10]("http://www.alfa.com.tw/download_show.php?combo_0=11&combo_1=AWUS036H&combo_2=Driver&keyword=&verify=PTWT8J&x=29&y=10")

---

### Post by Bucky Ball on 2014-07-21
Don't worry about it. Most wifi cards DON'T work from a Live boot. Easy enough to get the majority of them going once you have an install. This is not a support thread, but if you open a terminal and give us the output of this command:

```
sudo lshw -C network
```

... we'll be able to tell you if your card will be easy enough to get working with a full install, then up to you whether you go ahead with a full install (post a new thread if you do and have issues with wireless then).

 Enjoy your Linux explorations. ;)

PS: Be aware that if stalkingwolf's link does work to get your wireless up all changes will be lost on reboot. You can't actually install a driver permanently into a Live boot. Just mentioning it ...

---

### Post by chili555 on 2014-07-23
> **mj_oralde said:**
> i have installed it, but I cant get may alfa 036h wireless adapter to work. :(Hop over to Networking and Wireless and we'll be very glad to help.

---

