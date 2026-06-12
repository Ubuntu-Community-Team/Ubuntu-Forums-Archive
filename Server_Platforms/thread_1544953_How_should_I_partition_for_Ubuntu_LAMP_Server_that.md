---
title: "How should I partition for Ubuntu LAMP Server that will also run xbmc?"
date: 2010-08-03
forum: Server Platforms
---

### Post by nateuni on 2010-08-03
Hi Guys,

I am new to the board... I have been reading posts here, but never posted myself. So hi to everyone!

I am a first year Uni student and we use Linux at Uni. I am only new to Linux, but I have been messing around with different distros, even with Linux Routers. To help my ability to learn Linux I have made a Ubuntu Server. But recently I received some more HDDs so, I was going to start a fresh.  

I am setting up an Ubuntu home server that I will run SSH, FTP, PHP, MySQL, XBMC and this time I will also install a desktop so I can browse the net from my couch, when the time calls for it. I was looking at the manual partitioning options and I thought that on this setup I might explore partitioning this myself.

But I am unsure about best practices? I am still getting used to Linux and the manner is which the file systems is setup, so I don't want to waist my time by doing something impractical.

I have 2 HDs.

#1 160GB
#2 320GB

I want to use the FTP so I can store and backup files from my laptop. 
XBMC will be the main purpose of the box. 
The SQL, PHP, SSH is so I can get more linux experience and practice.

Regards,
Nathan

---

### Post by gobbledigook on 2010-08-03
hi there!

there are many different options for partitioning, you could split your disks into different partitions for each user, and run your programs as seperate users etc... but this is a little complex for your needs. 

I run xbmc and an ubuntu server - the main problem i had with the server install was that i had multiple x sessions running and found it a headache to get the right program to start in the right session on boot! So now i have the 10.04 desktop, which although uses a lot more memory... is easier to configure for the less cli savvy of us ;) i have xbmc set to go full-screen at start, so it is effectively a media centre, then to administer i ssh into the box, i run a couple of websites and some recording scripts etc... have a torrent client set up and a sabnzbd for newsgroups. a samba share for the rest of the house and i can ftp or use samba for moving files about.

if you want to mess about with partitioning, then check out [**_LVM_**]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)") as it is great for addding and removing partitions/disks and literally managing your volumes!

---

### Post by nateuni on 2010-08-03
Hey gobbledigook, 

Your setup is exactly what I was thinking of doing!

Q. What hardware setup do you have? And how well does XBMC run on your system?

Thanks again!

Regards,
Nate

---

### Post by gobbledigook on 2010-08-03
ok, 

i have a 3.5ghz single core amd 64, Nvidia something or other with vga, s-vid and dvi output,2gb ram, and 2x1tb drive 1x320gb 1x100gb - i have my main system on a 40gb partition of the 100gb drive and all the others are kinda "stitched" together using [**_mhddfs_**]("http://romanrm.ru/en/mhddfs") although i am looking at moving to LVM when i purchase an extra 2tb drive ("any day now!" - been saying that all this year!!) 

i installed ubuntu 10.04 desktop - then from cli installed apache mysql and php, there are plenty of tutorials for installing LAMP just remember you won't need the "linux" part ;)

as for speed - i must admit that after switching to the desktop install it is slow! takes about 3 mins to do a full reboot! xbmc is a little sluggish on entering some directories, but i think thats more to do with the volume of data i have. initial ssh connection can pause for a few seconds but thats about it. you see running a website and doing basic file operations is not resource intensive... but if i had the money? 

a quad core with at least 4 gb ram :p

---

