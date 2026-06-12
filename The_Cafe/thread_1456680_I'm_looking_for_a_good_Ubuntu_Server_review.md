---
title: "I'm looking for a good Ubuntu Server review"
date: 2010-04-17
forum: The Cafe
---

### Post by metalf8801 on 2010-04-17
I keep finding reviews of Ubuntu desktop but I would really like to find a good detailed review of Ubuntu Server.  It would be best if it was a review of Ubuntu 8.04 server and it needs to be a review of more than just the installer and setting up the server.  It would be great if there was a review that was written by someone who had been using Ubuntu server for a year of longer.  

Thank you

---

### Post by cariboo on 2010-04-17
Wouldn't it just be easier to ask what you want to know about it, or better yet install it and use it.

The Ubuntu server is one of the most basic you can get. There is no gui, and very few graphical tools to set things up. The server can be anything you want.

My server is just sitting on a shelf in my garage/shop/office, the only connections on it are power, network and ups, I do all administration remotely. It serves media files to my media center pc, stores ISO's of almost every program CD I've bought and/or downloaded. My desktop systems get backed up to it daily.

I have samaba setup to share files to Windows systems, and nfs for sharing amongst Linux powered systems.

I overbuilt this server, so that it would last for quite a while. It uses an Intel E5400 CPU and 2Gb ram, and currently just under 2Tb of storage.

---

### Post by metalf8801 on 2010-04-24
> **cariboo907 said:**
> Wouldn't it just be easier to ask what you want to know about it, or better yet install it and use it.

The Ubuntu server is one of the most basic you can get. There is no gui, and very few graphical tools to set things up. The server can be anything you want.

My server is just sitting on a shelf in my garage/shop/office, the only connections on it are power, network and ups, I do all administration remotely. It serves media files to my media center pc, stores ISO's of almost every program CD I've bought and/or downloaded. My desktop systems get backed up to it daily.

I have samaba setup to share files to Windows systems, and nfs for sharing amongst Linux powered systems.

I overbuilt this server, so that it would last for quite a while. It uses an Intel E5400 CPU and 2Gb ram, and currently just under 2Tb of storage.

I already did that.  I'm hoping to find out about unexpected down time and some comparisons to other Server OS like RHEL, SLES, Debian, or Solaris.   

What release of Ubuntu are you using on your server and have you run into any problems with it? 

Thanks 
Dan

---

### Post by Queue29 on 2010-04-24
I've been running 8.04 server for a while now. There isn't much to say about it really. The packages are almost all out of date, and back when it was receiving updates, almost _every_ update would break something. But now it has passed its last major update, so it's really just about as reliable as can be. The only problem is if you need up-to-date packages, because you aren't going to get them with 8.04

---

### Post by cariboo on 2010-04-24
> **metalf8801 said:**
> I already did that.  I'm hoping to find out about unexpected down time and some comparisons to other Server OS like RHEL, SLES, Debian, or Solaris.   

What release of Ubuntu are you using on your server and have you run into any problems with it? 

Thanks 
Dan

I'm currently running 9.10 (Karmic), the only downtime is something I do myself. I recently had to replace the motherboard on the server, so I took the opportunity to upgrade to a newer version, I was also running out of disk space, so I shut it down to add another hdd, otherwise it just runs, check out this:

```
 uprecords
     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1    21 days, 20:31:23 | Linux 2.6.31-20-server    Tue Mar 30 13:01:40 2010
->   2     3 days, 01:49:12 | Linux 2.6.31-20-server    Wed Apr 21 10:49:31 2010
     3     0 days, 00:45:17 | Linux 2.6.31-20-server    Wed Apr 21 09:55:25 2010
     4     0 days, 00:05:39 | Linux 2.6.31-20-server    Wed Apr 21 10:40:08 2010
----------------------------+---------------------------------------------------
no1 in    18 days, 18:42:12 | at                        Thu May 13 07:20:54 2010
    up    24 days, 23:11:31 | since                     Tue Mar 30 13:01:40 2010
  down     0 days, 00:25:32 | since                     Tue Mar 30 13:01:40 2010
   %up               99.929 | since                     Tue Mar 30 13:01:40 2010

```

The only other server I've used is Debian, so I can't compare it to RHEL or SLES. 

After learning to use Linux on RedHat and Mandrake, I swore never to use an rpm based distro again.

---

### Post by tica vun on 2010-04-24
Here's a review: Don't bother. After using server 9.10 for a couple months and being an unpaid betatester for 10.04 for almost the same length of time, I still can't get it to reliably reboot and start up networking (fsck faliures, boot process stops for no reason, networking service doesn't start, etc). My server is back to running Arch. Ubuntu is a decent desktop distribution, but it has no place in a serious server environment.

---

### Post by CharlesA on 2010-04-24
> **cariboo907 said:**
> I'm currently running 9.10 (Karmic), the only downtime is something I do myself. I recently had to replace the motherboard on the server, so I took the opportunity to upgrade to a newer version, I was also running out of disk space, so I shut it down to add another hdd, otherwise it just runs, check out this:

```
 uprecords
```

I have a similar experience, I have my server sitting in the corner on my dining room with only a power cord, UPS, ethernet cable and some external drives for backup hooked up. The only time it has gone down is when I need to reboot after a kernel update or when I need to take it down to clean out the dust or whatnot. I haven't had any problems with it at all, but maybe I am just lucky.

It's running an E6500 Dual Core Pentium on a gigabyte mobo with 4GB of RAM. I use it as a media server and VM host (as well as a DHCP server). It's got around 4TB of disk space (RAID-5 array) and is set to backup daily. Works great for my needs.

> **tica vun said:**
> Here's a review: Don't bother. After using server 9.10 for a couple months and being an unpaid betatester for 10.04 for almost the same length of time, I still can't get it to reliably reboot and start up networking (fsck faliures, boot process stops for no reason, networking service doesn't start, etc). My server is back to running Arch. Ubuntu is a decent desktop distribution, but it has no place in a serious server environment.

Use what works for you. I know RHEL works great for enterprise use (CentOS too). Ubuntu or even Debian could work, but I wouldn't use them in an enterprise environment.

---

### Post by cariboo on 2010-04-24
You may want to check out this list of what companies run Ubuntu servers.

[http://www.workswithu.com/the-works-with-u-1000/](http://www.workswithu.com/the-works-with-u-1000/)

@tica vun

Just because you had a problem with the server version, doesn't mean it won't work for others.

---

### Post by perlluver on 2010-04-24
Running it on an old computer in my basement, serving files and a local web page.  I never shut it down or reboot it unless I get a kernel update.  It is running 9.10 until 10.04 is stable, then I plan on upgrading to a newer motherboard and case.  I haven't had any problems with it, and it has been running since 8.04, so it has been awhile.

---

### Post by CharlesA on 2010-04-24
> **cariboo907 said:**
> You may want to check out this list of what companies run Ubuntu servers.

[http://www.workswithu.com/the-works-with-u-1000/](http://www.workswithu.com/the-works-with-u-1000/)


Thanks for the link there. Pretty cool to see all sorts of companies running Ubuntu servers.

Also thanks for the info about the uprecords command, quite neat. :)

---

### Post by tgalati4 on 2010-04-24
Here's my review of Dapper Drake Desktop 6.06 LTS used as a server:

It works.

tgalati4@tubuntu2:~$ uprecords
     #               Uptime | System                                    Boot up 
----------------------------+-------------------------------------------------
     1   216 days, 06:49:56 | Linux 2.6.15-28-386      Tue May 22 22:36:24 2007
     2   163 days, 23:49:22 | Linux 2.6.15-26-386      Tue Oct 24 12:19:49 2006
     3   153 days, 01:33:24 | Linux 2.6.15-29-386      Wed Dec 26 13:22:27 2007
     4   117 days, 23:40:07 | Linux 2.6.15-51-386      Thu Jun  7 10:18:37 2007
     5    94 days, 02:31:54 | Linux 2.6.15-52-386      Mon Oct 20 10:55:37 2008
     6    64 days, 20:48:44 | Linux 2.6.15-54-386      Sun Aug  2 12:56:44 2009
     7    59 days, 15:24:32 | Linux 2.6.15-53-386      Sun Feb  8 16:44:19 2009
     8    44 days, 22:39:39 | Linux 2.6.15-55-386      Sat Oct 24 10:56:14 2009
     9    44 days, 05:43:51 | Linux 2.6.15-54-386      Thu Apr 30 10:32:09 2009
    10    42 days, 22:30:09 | Linux 2.6.15-55-386      Mon Feb  8 12:17:12 2010
----------------------------+-------------------------------------------------
->  12    31 days, 23:21:57 | Linux 2.6.15-55-386      Tue Mar 23 15:47:41 2010
----------------------------+-------------------------------------------------
1up in     9 days, 22:21:05 | at                       Tue May  4 13:30:41 2010
no1 in   184 days, 07:28:00 | at                       Mon Oct 25 22:37:36 2010

---

### Post by The Real Dave on 2010-04-24
Ya, I'm loving Ubuntu server also :) Mine runs on an older PIV, running Samba, NFS, rTorrent, and also Squid and Apt-Cacher-NG proxies, along with monitoring software, and a LAMP stack. All on a 1.7Ghz PIV with 384Mb of RAM :)

It's run extremely reliably, the only problem I've ever had was an errant program swallowing all the memory. I changed the program, and adding 2Gb of swap for safety :)

It's been up for

```
 23:20:13 up 60 days, 23:29,  4 users,  load average: 0.38, 0.17, 0.05

```

Pics, exact specs, and videos can be found on my [blog, Linux Expresso.]("http://linuxexpresso.wordpress.com/hardware")

---

