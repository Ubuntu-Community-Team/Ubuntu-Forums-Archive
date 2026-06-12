---
title: "Server 9.10 sda error ?"
date: 2009-12-10
forum: Server Platforms
---

### Post by jleaman on 2009-12-10
Ok, so i LOVE ubuntu dekstop, have it working 100% on a p4 1.7 with 1.5 gigs ram and a 80gig hard drive i love it alot. So i decided to think that my osx g4 400mhz bos is about to die ( maybe ) so i'm thinking i want to use ubuntu server.

Downloaded it and tried to install it, however i get through the install and come to a error can't rear write to /sda i get the continue  retry or cancel option.

I know all the hard ware works because i had windows 2003 server on it, ( DIDNT LIKE IT ) so now i want to install ubuntu for my home server for ftp http & file storage for all my files, plus allow my self to remote desktop into it and use it to download my torrents and other user files. 

Help ?

---

### Post by munky99999 on 2009-12-10
Did you get a power pc image?

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

[http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-server-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-server-powerpc.iso)


sounds like you did. Just making sure.

---

### Post by jleaman on 2009-12-10
> **munky99999 said:**
> Did you get a power pc image?

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

[http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-server-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/9.10/release/ubuntu-9.10-server-powerpc.iso)


sounds like you did. Just making sure.



nope, Ubuntu-Server 9.10 i386  :(

#define DISKNAME  Ubuntu-Server 9.10 "Karmic Koala" - Release i386
#define TYPE  binary
#define TYPEbinary  1
#define ARCH  i386
#define ARCHi386  1
#define DISKNUM  1
#define DISKNUM1  1
#define TOTALNUM  0
#define TOTALNUM0  1


Any thing else it could be ?

---

### Post by munky99999 on 2009-12-10
No that'd be the issue.

Your mac G4 CPU architecture is Power pc. So you need to get the powerpc version of ubuntu.

Get one from the links I gave. The 2nd link is server 9.1 powerpc which is what you want afaik.

---

### Post by jleaman on 2009-12-10
> **munky99999 said:**
> No that'd be the issue.

Your mac G4 CPU architecture is Power pc. So you need to get the powerpc version of ubuntu.

Get one from the links I gave. The 2nd link is server 9.1 powerpc which is what you want afaik.

NO, you miss understood / i gave wrong impression.

I'm trying to REPLACE my osx server :) and run ubuntu on my free 1.5gig intel tower :) not run ubuntu on my g4 server :)

:0

Jase

---

### Post by munky99999 on 2009-12-10
oohhh. lol

Well then. In the bios is the hard drive detected? Can you get to the partitioner where you choose to partition the whole drive or only part or manual?

---

### Post by jleaman on 2009-12-10
> **munky99999 said:**
> oohhh. lol

Well then. In the bios is the hard drive detected? Can you get to the partitioner where you choose to partition the whole drive or only part or manual?

Hard drive is found, in the bios. I can try this install again then ill post a photo of what i'm talking about, and also try what you are asking :)

Brb :)

---

### Post by jleaman on 2009-12-10
ok, put new drive in machine  :P all installed now need help setting up graphical user interface :)

---

### Post by jleaman on 2009-12-10
ttt

---

