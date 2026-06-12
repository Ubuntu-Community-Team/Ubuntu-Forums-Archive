---
title: "Reconfiguring RAID - disaster needing help"
date: 2011-07-08
forum: Server Platforms
---

### Post by kyral210 on 2011-07-08
[LEFT]OH MY GOD!
 
I tried setting up the raid files on my server for RAID1. Well, I did that ok, but some problem with GRUB (server 11.04) meant that the server didnt boot.
 
So I tried to install the more stable and tested Server 10.04, I tried to reconfigure the disks to be RAID5 (as it should have been in the start) and BOOM! Now I have bugger raid that can be configured, wiped or deleted. One of the MD's cant be deleted and is blocking further progress.
 
How can I install a clean Ubuntu server onto my machine with freshly configured RADI5 drives. In short, turn a buggered setup into a nice one that runs well?
 
Please help, I am very very new to this server business and dont want to have to go to IT and tell them I have destroyed one of their servers (even though it is an old one).
 
:([/LEFT]

---

### Post by rubylaser on 2011-07-08
If your system still boots, I'd just stop all running mdadm devices. Otherwise boot the live cd and apt-get install mdadm, then proceed.

```
mdadm --stop /dev/md<your_device_here>
```

Then zero the superblock on all of the disks that you had in the array.
```
mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdc1
etc
```

Finally, delete your /etc/mdadm/mdadm.conf file.  Now, you're back at a point where there's no mdadm metadata hanging around and you can setup a new array.  Just as an FYI, I'm not sure if you're trying to boot from the RAID5 array, but that will not work.

---

### Post by kyral210 on 2011-07-08
REALLY basic question, how do I *boot the live CD*? I have the installation CD, but what do I do with it? I rebooted the server with the installation CD in and told it to boot from hard drive, but I just got back a FD) fatel error and 'no hard drive'. What do I do? Sorry I am such a noob.

---

### Post by ASchweitzer on 2011-07-08
A live CD is different from a server installation CD. You'll want to download and burn a desktop installation CD, which will let you boot into a desktop environment.

---

### Post by rubylaser on 2011-07-08
Just download the [desktop version]("http://releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-i386.iso") and enter the option to **Try Ubuntu**.  Once is booted, just
```
sudo -i
apt-get update && apt-get install mdadm -y
```

Then use fdisk -l to identify your mdadm disks, and zero the superblocks as I showed before.

---

### Post by kyral210 on 2011-07-08
Ah, I cant do that either. I have tried to 'try Ubuntu' from a desktop PC but it just sends the server into a whole load of orange coloured errors...

---

### Post by rubylaser on 2011-07-08
It sounds like it's having a problem with your graphics card.  You could use [Finnix]("http://www.finnix.org/releases/101/finnix-101.iso")  and boot from the 32 bit text mode (it's Debian based, so it will play very nicely with your Ubuntu install). 

It already comes with mdadm installed, so you'll just need to run fdisk -l, get your device paths, and zero the superblocks.

---

### Post by kyral210 on 2011-07-08
Ok, I have sort of fixed the problem, sort of.
 
I did a fresh installation with Ubuntu 10.10 Server and when it came to partitioning I told it to do guided first hard drive (or whatver it said). That worked and I am now logged in and running! Well, I am not on RAID1, but I will do a reinstall later when I am more confident.
 
Trying to work around the server, I tried running:
 
sudp apt-get update and this is what I got:
 
W:failed to fetch http://<address> Temporary failure resolving 'security.ubuntu.com'
 
(and lots of those)
 
When i was installing I did select 'do not configure network now', but I do have an thernet cable into the back of the server which is flashing green.
 
Does this mean that my server is not on the internet yet? How do i solve this?

---

### Post by rubylaser on 2011-07-08
It sounds like at a minimum DNS isn't working, but probably you don't have an ip.  Does the server have 2 NICS?  What's the output of these commands?

```
ifconfig
```
```
cat /etc/resolv.conf
```
```
ping www.google.com
```

---

### Post by kyral210 on 2011-07-08
Thanks, will give it a bash tomorrow when I go back to the office to see if I can get this server up and running!!!

---

### Post by kyral210 on 2011-07-11
> **rubylaser said:**
> It sounds like at a minimum DNS isn't working, but probably you don't have an ip. Does the server have 2 NICS? What's the output of these commands?
 
```
ifconfig
```
```
cat /etc/resolv.conf
```
```
ping [www.google.com]("http://www.google.com")
```
 
I ran the codes and this is what I got back:
 
[IMG]http://farm7.static.flickr.com/6004/5926461665_ef899bb1c9_z.jpg[/IMG]

---

### Post by kyral210 on 2011-07-23
I solved this buy creating a Server 10.10 disk and running a clean installation. The problem was that the server had a hardware RAID already configured, so I was trying to add a software RAID on top of hardware RAID!!!!!!

I might rebuild the server in the future and will know to unformat
the hardware raid first.

Thanks guys for your help.

:KS

---

