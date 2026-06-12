---
title: "which is best UBUNTU VERSION"
date: 2009-04-28
forum: Server Platforms
---

### Post by salim.madni on 2009-04-28
hello gurus

how are you

i do have one old laptop IBM A21 THINKPAK with 128MB ram, and aprox 1GHZ machine, 20gb ide hard disk with dvd

so i try using ubuntu 9.04,8.10 but not loaded...

advise shell i use as server or desktop, and which version suitable for low configurtion machine with graphics and without graphics

advise highly apprecited

kind regards
salim

---

### Post by lisati on 2009-04-28
The "desktop" version is good for every-day use, and can be setup as a server if you choose to do so later.
The "server" version is good for setting up a server, but doesn't come with a GUI (you can add one later if you choose)

---

### Post by salim.madni on 2009-04-28
> **lisati said:**
> The "desktop" version is good for every-day use, and can be setup as a server if you choose to do so later.
The "server" version is good for setting up a server, but doesn't come with a GUI (you can add one later if you choose)

hello sir, this is suprise to hear the desktop can work as server also? surprise can you give some guideline on this. 

But problem sir none version loading,

in fact there was redhat server was there i use bootini cd to remove MBR,all partition of redhat create.now complete harddisk is wipeout.

but when i boot it start loading loading... and partialy success

then last nothing comes out

advise according to spec of machine can work anything? which version please

regards
salim

---

### Post by DracoJesi on 2009-04-28
the great secret is, they're all the same...

the only difference is whats installed from the get go

---

### Post by DracoJesi on 2009-04-28
> **salim.madni said:**
> hello sir, this is suprise to hear the desktop can work as server also? surprise can you give some guideline on this. 

But problem sir none version loading,

in fact there was redhat server was there i use bootini cd to remove MBR,all partition of redhat create.now complete harddisk is wipeout.

but when i boot it start loading loading... and partialy success

then last nothing comes out

advise according to spec of machine can work anything? which version please

regards
salim

well Ubuntu doesn't require much Ram, but it does require 256MB (that may be conservative though, and you may be able to get by with less I dunno, but I did read of a problem with the Live CD, where it might not load with less than 256MB  ) you have 128MB, I'm I'm pretty sure thats probably the issue...

there's bad news and good news, 

bad news, since they don't make make 128MB sticks anymore (or 256MB).... you can't go out and by another stick, and if you could you need to make sure you have a slot open, you have a 1Ghz CPU, so I doubt you have two 64MB sticks or four 32mb sticks lol

good news, if you can find the stick type you need, it shouldn't be very expensive at all... :)

 
[http://www-307.ibm.com/pc/support/site.wss/MIGR-4PCRRF.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-4PCRRF.html)

looks like you have 2 64Mb sticks, maybe 1 128MB,  if 128MB, you need at least another 128MB, but I'd go for the dull 512MB from two 256MB sticks...

---

### Post by Chainz on 2009-04-28
Indeed, Your 128MB RAM is the bottle neck here.

If you can manage to expand it would be great improvement for that machine and usability.

However if you still want to give it a try, please use Xubuntu alternate install CD.
This will install (using text mode - quite simply though) Ubuntu with lightweight window manager that uses less RAM (your 128MB should be just enough with this option).

> **Minimum system requirements**
You need 192 MB RAM to run the Live CD or 128 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time. To install Xubuntu, you need 1.5 GB of free space on your hard disk. Once installed, Xubuntu can run with starting from 192 (or even just 128 ) MB RAM, but it is strongly recommended to have at least 256 MB RAM. 


Let us know how it went.

---

### Post by Iowan on 2009-04-28
If I'm reading the POST screen correctly, I have 128M on my Hardy LAMP server. It's only a development machine for teaching myself webserver, but seems to run OK. It doesn't take a lot - IF you run CLI only (no GUI).

---

### Post by quietas on 2009-04-28
Take a look at Xubuntu 9.04. Same core as Ubuntu, but rather than the more resource intensive Gnome, it uses XFCE for the GUI. I've used Xubuntu many times on older equipment and recently installed 9.04 beta on a Celeron 800 laptop with 128mg ram and crappy onboard video. It works great as a web surfing coffee table pc.

---

### Post by salim.madni on 2009-04-29
thanks, can you advise me further where to download from xbuntu 9.04

i found it is available for playstation3,mac machines etc

can you suggest i have intel processor and i386 based machine 32bits...
can you send me link which one to download exactly

on the site i found 
[http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/)

regards

---

### Post by quietas on 2009-04-29
[http://www.xubuntu.com ]("http://www.xubuntu.com") Click [Get Xubuntu]("http://xubuntu.com/get")

Find your local mirror and follow the directions below for install.

---

### Post by Chainz on 2009-04-29
Here you go:
On: [http://cdimage.ubuntu.com/xubuntu/releases/9.04/release/]("http://cdimage.ubuntu.com/xubuntu/releases/9.04/release/")
You have all you need.


And direct link to version that you should use is:
[http://cdimage.ubuntu.com/xubuntu/releases/9.04/release/xubuntu-9.04-alternate-i386.iso]("http://cdimage.ubuntu.com/xubuntu/releases/9.04/release/xubuntu-9.04-alternate-i386.iso")


Good luck!

---

