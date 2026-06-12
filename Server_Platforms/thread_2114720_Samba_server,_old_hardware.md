---
title: "Samba server, old hardware"
date: 2013-02-10
forum: Server Platforms
---

### Post by VishmanX on 2013-02-10
So I recently was given a VERY VERY old HP Omnibook 2100. It had Windows 98 but I formated it, to put Ubuntu. Now, hear is the part I don't want to people to start groaning about and say it is extremely outdated. Because of the poor specs I had to put Ubunu 5.10 Breezy server on it. My goal is to create a file server between my two Win 7 pcs and my Win Vista pc. I already installed 5.10's version of Samba and need directions to set it up. Also if it is available, I'll take suggestions for newer systems to build my server on. 

The PC specs:
---------------------
CPU: 700 MHz Pentium II
RAM: 128 MB
HDD: 4.1 GB
OS: Ubuntu 5.10 Server

---

### Post by tgalati4 on 2013-02-10
I've had a Dapper Drake (6.06) desktop/server running continuously since June 2006.  I would upgrade to that.  It's stable.

---

### Post by Doug S on 2013-02-10
I am running Ubuntu server 13.04 (dev) on a 200Mhz Pentium Pro, with 128 Megabytes of memory. It has also run Server 12.10, 12.04, 11.10, 10.10, and for many years ran 6.06.
However, I have never seriously run Samba on it. I could try it, not sure when I would get to it though.

---

### Post by tgalati4 on 2013-02-10
Max out the RAM if you can find it, and make a swap disk partition.  That will make it run faster.

[http://nas4free](http://nas4free) will run OK on that hardware as well.

---

### Post by spynappels on 2013-02-11
Do you intend running this as a file server or as a domain controller? If as a file server, will you be connecting a USB HDD for the actual storage?

---

### Post by Doug S on 2013-02-11
I added samba to my pathetic old server mentioned in post #3 above:
 
I am getting 6.5 Megabytes per second file transfer rate from the server to my windows vista LapTop. The processor is max'd out, with smbd taking about 91%, and other stuff taking the rest, including "top" using 2% while I try to see what is going on.
 
For the other direction: File transfer from windows vista box to the server: I get 1.00 megabytes per second. The processor has idle time. smbd is taking about 15%. I'm not sure what the bottle neck is for this direction.
 
Edit: See posting #11.  File transfer from windows to server is now much faster.

---

### Post by koenn on 2013-02-11
> **Doug S said:**
>  
For the other direction: File transfer from windows vista box to the server: I get 1.00 megabytes per second. The processor has idle time. smbd is taking about 15%. I'm not sure what the bottle neck is for this direction.

educated guess : disk I/O.

---

### Post by lykwydchykyn on 2013-02-11
Old laptops usually have dismally slow hard drives.  You'll probably just have to accept some slow performance from it.

I would recommend using the latest Debian stable or else tinycore linux.  Really depends on your level of expertise, and if Samba is really all you want on this thing.

When you take X11 out of the equation, there's not much reason to run an old version of Linux.  The CLI will fly even on that old hardware.

---

### Post by koenn on 2013-02-11
> **VishmanX said:**
> 

The PC specs:
---------------------
CPU: 700 MHz Pentium II
RAM: 128 MB
HDD: 4.1 GB
OS: Ubuntu 5.10 Server

Until 2 weeks ago I ran a samba server on similar hardware - last century desktop. Don't remember all the numbers, but 4 GB disk, PII, 128 MB RAM - sounds about right. I did add a couple of extra disks salvaged from other PCs for extra space).
It ran Debian 5, iirc. With Samba, mysql, Apache, and some misc other software. 
I'm sure you can get 12.04 LTS to run on those specs - unless you're talking a  fullblown desktop + samba. But then Samba isn't your problem.

---

### Post by VishmanX on 2013-02-11
Installing Lubuntu CLI crossing fingers. And as for the earlier question, file server, I intend to buy a old usb 1.0 hdd off ebay. Also checking BIOS I realized I put the wrong MHz it's 300 MHz so I think it won't run

---

### Post by Doug S on 2013-02-11
> **koenn said:**
> educated guess : disk I/O.Ya, I thought so also, and even wrote so at first, but later I edited it to what is there now.
 
Disk write limit seems to be about 9.0 megabytes per second (I used a simple program to write a big file, and checked that the program itself was mostly waiting for the disk).
Network limit seems to be just less than about the theoretical limit for 100 megabit ethernet, or 9 megabytes per second in either direction (I used iperf).
 
Anyway, it doesn't matter as the OP is going to try lubuntu, which myself I would not do.
Edit: Opps... I missed the "CLI" part when the OP mentioned lubuntu. O.K.
 
Edit 2: Seems to be RX packets errors on server during large file transfer, perhaps explaining low transfer rate.
 
Edit 3: Changed NIC: Now, file to server rate = 5.2 megabytes per second. Processor 0% idle. smbd = about 80%.

---

