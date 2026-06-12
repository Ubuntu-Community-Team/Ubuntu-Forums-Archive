---
title: "boot error, failed command: READ FPDMA QUEUD, mounting /dev/sda2 on /root failed"
date: 2020-03-09
forum: Server Platforms
---

### Post by 8ER on 2020-03-09
Hello,

I am aware that there are similar posts regarding boot issues but, none of them fits my case. Since I cannot find any similar posts here I decided to make a new thread about the issue. 

In short: I am facing an boot problem with my ubuntu 18.08 server. 

I am running ubuntu inside a vm with virtualbox and initially it worked fine. Yesterday though it crashed for some reason and crashed the host machine with it. 

Prior to crash I had install nginx server with wordpress inside. Before the error I manage to print a few screenshots with the error output

[ATTACH=CONFIG]285176[/ATTACH][ATTACH=CONFIG]285177[/ATTACH][ATTACH=CONFIG]285178[/ATTACH][ATTACH=CONFIG]285179[/ATTACH]


I tried logging in with recovery mode and fixing the disks with fsck but, the fsck command does not exist.

I tried using a liverecovery cd and it says that there is nothing wrong with the disk.

Any ideas?

Thanks in advance

---

### Post by TheFu on 2020-03-09
> **8ER said:**
>  I tried using a liverecovery cd and it says that there is nothing wrong with the disk.


Exactly how does it say nothing is wrong?  Commands, options, and output, please.  In short, prove it.

But if only the VM is complaining, then I'd look at the hostOS and the physical disks where that storage is setup.  Are you using IOMMU passthrough of the controller?  Providing LVs for each guestOS?  Is there some way that you can trace a specific partition to the guestVM?  What does fsck and SMART say about the physical storage and the physical file system?

BTW, if a "Try Ubuntu" flash boot/install drive is used, you can just install whatever programs are needed into the "Try Ubuntu" environment, just like normal. They will go away at reboot, so you'd need to reinstall them every time. Usually, that is just a few seconds these days.

---

### Post by 8ER on 2020-03-10
Hello, 

First of all thank you for the quick reply.

> Exactly how does it say nothing is wrong?  Commands, options, and output, please.  In short, prove it.

When I run the "check disk for defects option" with ubuntu live cd. 
[ATTACH=CONFIG]285182[/ATTACH]

  > Are you using IOMMU passthrough of the controller?

I am going to be honest here, I don't know what that is or how to set it up...

> Providing LVs for each guestOS?

I use the bridged adapter option for the Linux guest. If that's what you mean. 

> What does fsck and SMART say about the physical storage and the physical file system?

when I try running the server in recovery mode, fsck does not seem to be present. I can't run the fsck command.

> BTW, if a "Try Ubuntu" flash boot/install drive is used, you can just  install whatever programs are needed into the "Try Ubuntu" environment,  just like normal.

I tried running the "try ubuntu" but then *everything* crashes. Including my host computer which is ubuntu 18.04 by the way. Below you can see the error. I could not capture it with any other way.
[ATTACH=CONFIG]285184[/ATTACH]

_additional information_:
virtual box 6
ubuntu server (host) 18.04
nginx  1.17

hopefully that clarifies things a bit.

---

