---
title: "Is there a guide for absolute beginners"
date: 2015-03-12
forum: Server Platforms
---

### Post by mandarpowale on 2015-03-12
... to do an install of UBUNTU Server Edition 14.04.2. I have never used UBUNTU Server in my life, I so have the ISO on CD though and would like to use the SERVER for learning purpose.
(currently running UBUNTU Desktop on one of my partition), I was a  Windows User.

Thanks in advance,

Mandar Powale

---

### Post by Elfy on 2015-03-12
[https://help.ubuntu.com/lts/serverguide/](https://help.ubuntu.com/lts/serverguide/)

and moved

---

### Post by nerdtron on 2015-03-12
If you are new, don't start just copy pasting tutorials found on the Internet. The first lesson are to familiarize your self with how the linux filesystem is structured and how the command line works.

1. Install OS, [www.youtube.com](www.youtube.com) videos are a great help here.
2. Familiarized yourself with the command line. An easy to read book is [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) you can download the free pdf version.
3. Become familiar with Ubuntu Server. A book I read is [http://www.amazon.com/Official-Ubuntu-Server-Book-Edition/dp/0133017532](http://www.amazon.com/Official-Ubuntu-Server-Book-Edition/dp/0133017532)
4. Do what you want and start installing the applications you like, nfs, samba, web server, email.


Remember the first task is to familiarize. Don't rush and enjoy reading. BTW, it would help if you open yourself how linux does things. It's different from windows.

---

### Post by Elfy on 2015-03-12
Never run a server, so couldn't help but

> don't start just copy pasting tutorials found on the Internet.

sums up much of what I could say.

There are a huge amount of *buntu* based tutorials out there, with search ranking working the way it does - many are years old.

---

### Post by mandarpowale on 2015-03-12
Thanks , the both of you.

---

### Post by deadflowr on 2015-03-12
I would say if you wanted to learn and try stuff out, I would recommend doing it in a virtual machine, like qemu-kvm, or virtualbox.
Probably easier from the get-go in virtualbox.
That way you can run the server install in a vm and keep your regular system open for quick help if needed.
On top of if you go with a vm you won't have to muck with re-partitioning and all the muck that goes along with a normal install.
My two cents.

---

### Post by mandarpowale on 2015-03-12
> **deadflowr said:**
> I would say if you wanted to learn and try stuff out, I would recommend doing it in a virtual machine, like qemu-kvm, or virtualbox.
Probably easier from the get-go in virtualbox.
That way you can run the server install in a vm and keep your regular system open for quick help if needed.
On top of if you go with a vm you won't have to muck with re-partitioning and all the muck that goes along with a normal install.
My two cents.

I have just 4 GB RAM and an AMD Athlon II x2 260, i don't know how to use virtual box or whether it will run on my system?

Thanks for the advice.

---

### Post by Drone4four on 2015-03-13
I'd recommend you try paying for the basic $5/mo service on DigitalOcean.  Its a web host for new and veteran sysadmins alike  They have detailed documentation dedicated to instructing new users on how to set up a Linux-Apache-MySQL-and-PHP server.  That's what I am using.  It's lots of fun and I'm learning a lot.

---

### Post by Habitual on 2015-03-13
> **Drone4four said:**
> They have detailed documentation...is putting it mildly. I use their Documentation all the time and I don't even host with them. 
The articles are short and annotated professionally. Good Stuff.

---

### Post by mastablasta on 2015-03-16
> **mandarpowale said:**
> I have just 4 GB RAM and an AMD Athlon II x2 260, i don't know how to use virtual box or whether it will run on my system?

Thanks for the advice.

server will run well on much less than that. It needs 256 Mb ram dedicated to it but more is better. I ran it on 2 GB single core Athlon, so I couldn't even dedicate a CPU core to it. then I upgraded the ram so now I can dedicate 1 Gb to it. we used it for testing various server distros. runs preety nicely.

here is a nice guide for virtualbox install. just replace the desktop image with server image: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

you can also get ready server virtualbox images on Bitnami stack (ubuntu based) or Turnkey Linux (debian based). so no need to install them you just add them to virtualbox and select you password and you are good to go.

if you want a GUI server (web or desktop GUI) have a look at Zentyal which has official canonical support. there are many other good ones out there to explore (OMV, ClearOS...).

also server install is pretty much same as desktop it will only pop up some additional options.

---

### Post by mandarpowale on 2015-03-16
ty again

---

### Post by LHammonds on 2015-03-17
I have a few tutorials.  I'm updating the old tutorials for 12 to 14 as I update my servers.

[How to Install and Configure an Ubuntu Server 14.04.1 LTS]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=210")
[My Notes for Installing MariaDB on Ubuntu Server 14.04.1 LTS]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=211")

I don't yet have updated versions for Craftbukkit (now dead), WordPress, Nagios and FTPS/SFTP.

LHammonds

---

### Post by mandarpowale on 2015-03-20
For some reason I have to use the 32 bit version of Ubuntu, it won't let me use 64 bit version. DO I need to have ram > 4GB?


Add: Does Ubuntu have any logical sequence to its commands ?

---

### Post by CharlesA on 2015-03-20
> **mandarpowale said:**
> For some reason I have to use the 32 bit version of Ubuntu, it won't let me use 64 bit version. DO I need to have ram > 4GB?


Add: Does Ubuntu have any logical sequence to its commands ?

I usually use the 64-bit version even on small VPSes (128MB memory), but it shouldn't really matter if you have less than 4GB RAM.

If your CPU won't support 64-bit, you'll be stuck with 32-bit but I don't think that'll be a big problem.

The different commands are similar for all Debian-based distros.

I would recommend starting here:
[http://www.tecmint.com/useful-linux-commands-for-newbies/](http://www.tecmint.com/useful-linux-commands-for-newbies/)

I learned a bunch of things by googling "man tar" or "man apt-get" or whatever, but there are also man pages installed when you install the packages.

---

### Post by deadflowr on 2015-03-20
> **mandarpowale said:**
> For some reason I have to use the 32 bit version of Ubuntu, it won't let me use 64 bit version. DO I need to have ram > 4GB?


RAM really has little to do with it.
Whether or not you can run 64-bit or 32-bit depends upon whether or not the CPU can.
You can run 64-bit with 1Gb or less if you wanted to.
(Less than 1GB, though, is less than ideal)

And: ninja'd by post above.

---

### Post by mandarpowale on 2015-03-21
> **CharlesA said:**
> I usually use the 64-bit version even on small VPSes (128MB memory), but it shouldn't really matter if you have less than 4GB RAM.

If your CPU won't support 64-bit, you'll be stuck with 32-bit but I don't think that'll be a big problem.

The different commands are similar for all Debian-based distros.

I would recommend starting here:
[http://www.tecmint.com/useful-linux-commands-for-newbies/](http://www.tecmint.com/useful-linux-commands-for-newbies/)

I learned a bunch of things by googling "man tar" or "man apt-get" or whatever, but there are also man pages installed when you install the packages.

> **deadflowr said:**
> RAM really has little to do with it.
Whether or not you can run 64-bit or 32-bit depends upon whether or not the CPU can.
You can run 64-bit with 1Gb or less if you wanted to.
(Less than 1GB, though, is less than ideal)

And: ninja'd by post above.


ummm, I forgot to add that I am using Oracle Virtualbox to Run UBUNTU  14.04.02 Server. My CPU is AMD ATHLON II X2 260 which is an 64 bit CPU and I have 4 GB of RAM.

---

### Post by mandarpowale on 2015-03-21
I also see that there is no consensus on what I shd learn first.

---

### Post by CharlesA on 2015-03-21
> **mandarpowale said:**
> ummm, I forgot to add that I am using Oracle Virtualbox to Run UBUNTU  14.04.02 Server. My CPU is AMD ATHLON II X2 260 which is an 64 bit CPU and I have 4 GB of RAM.

Are you running a 64-bit or 32-bit OS for the host? It looks like that CPU supports hardware virtualization and is 64-bit capable.
[http://www.cpu-world.com/CPUs/K10/AMD-Athlon%20II%20X2%20260%20-%20ADX260OCK23GM%20%28ADX260OCGMBOX%29.html](http://www.cpu-world.com/CPUs/K10/AMD-Athlon%20II%20X2%20260%20-%20ADX260OCK23GM%20%28ADX260OCGMBOX%29.html)

Start slow imo and learn as you go. If you have questions, you can create a thread and they should be answered relatively quickly.

---

### Post by mandarpowale on 2015-03-21
> 
Are you running a 64-bit or 32-bit OS for the host? It looks like that  CPU supports hardware virtualization and is 64-bit capable.

I was running a Windows 7 64 bit ult. Now I have switched to UBUNTU 14.04.02 Server with GUI

---

