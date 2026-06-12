---
title: "NFS performance problems"
date: 2018-05-18
forum: Server Platforms
---

### Post by modomobo on 2018-05-18
I'm new to Ubuntu, having a lot of trouble setting up a media server.

I am starting to wonder if this is something that Ubuntu can do, or if I should be trying something different (Earlier version? Different distro? Windows 10? Ugh. Dunno).

Brand new hardware. Installed 18.04 for the desktop, which was easy. Set up samba, which ended up being a pain and performance is horrible.

As an alternative, I set up NFS, but that has turned into its own nightmare. I want to mount the NFS share from OS X 10.12.6 (Sierra). There were all kinds of arcane complications with permissions (finally sorted), but now it is very slow, even worse than samba it seems (over two hours to copy a DVD ISO file) or else unreliable (the mount disconnects).

My machine is set up like this:

(1) I have a directory /media/me

**$ ls -l /media**

drwxrwxrwx+ 3 root smbgroup 4096 May 18 10:20 me

(2) Inside that, I have a mounted HDD:

**$ ls -l /media/me**

drwxrwxrwx 5 root smbgroup 4096 May 18 12:09 hdd-2018-01

(3) According to **df -h**, the drive is mounted like this:

/dev/sdb       1.8T  8.4G  1.7T   1% /media/me/hdd-2018-01

(4) I have **/etc/exports** set up like this:

/media/me    my-macbook-pro.local(rw,crossmnt,async,root_squash,no_subtree_check,anonuid=502,anongid=20)

I have hard-wired the UID and GID from my OS X machine.

(5) I can mount the NFS share, like this:

**$ sudo mount -t nfs -o resvport,rw 10.0.1.22:/media/me /Users/me/nfs**

It works, but seems glacially slow.

At this point I am wondering what I should do to mount a file system with decent performance.

Suggestions?

---

### Post by wildmanne39 on 2018-05-18
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by kerry_s on 2018-05-18
[https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html)

---

### Post by modomobo on 2018-05-18
Thanks for this. It doesn't really address performance issues, though.

---

### Post by modomobo on 2018-05-20
Following up: I found that by connecting my NFS client to an Ethernet cable instead of WiFi, performance improved dramatically.

This may be obvious to those more expert than I, but for anybody else getting started with NFS, give it a try and compare the difference.

---

### Post by jbamford92 on 2018-05-20
> **modomobo said:**
> Following up: I found that by connecting my NFS client to an Ethernet cable instead of WiFi, performance improved dramatically.

This may be obvious to those more expert than I, but for anybody else getting started with NFS, give it a try and compare the difference.

NFS works better over Ethernet. NFS will work over WIFI but requires to manually mount via terminal. If you have a AC AP & a AC Wireless card you will get good speeds also. I use NFS on a daily basis over both Ethernet in LACP with HP NC360T in servers and Workstation in Bond0. A Intel 7260 AC Card with Speeds up to 867 mbps. 

What Software are you using? Ubuntu Desktop with NFS Server or Ubuntu Server?

What Ethernet Hardware are you using? & WIFI Hardware?

---

### Post by TheFu on 2018-05-24
> **modomobo said:**
> Following up: I found that by connecting my NFS client to an Ethernet cable instead of WiFi, performance improved dramatically.

This may be obvious to those more expert than I, but for anybody else getting started with NFS, give it a try and compare the difference.

A simple rule of thumb - servers should be on GigE wired ethernet connections.

WiFi networks seem stable to a human, but most of the time they wildly change throughput constantly. That isn't good for any protocols that don't buffer largely.  From second to second a wifi connection can go from 70 Mbps to 15 Mbps to 30 to 2 to 80 ... those wild changes are bad.  
It is worse based on obstructions, distance and the channels used, but even 2-4 ft away from the WAP, wild throughput changes happen due to atmospheric conditions and outside interference.   

Lots of things are on 2.4Ghz. Lots.   And the more devices there are, the less bandwidth there is for any single device.   Have a tablet, smartphone, streaming box all on wifi? They are eating bandwidth just by being connected to the AP.  802.11N and later protocols have gotten a little better about this, but it isn't until multi-phase-channels with 802.11ac  where it finally got noticeably better. A single 802.11g device can bring an entire network performance down.

IME.

---

