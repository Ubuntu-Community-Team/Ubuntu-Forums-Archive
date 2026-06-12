---
title: "Building a Server for backups (NAS)"
date: 2009-06-13
forum: Server Platforms
---

### Post by RvA944 on 2009-06-13
Hello All,
 
Well I'm new to Linux so be gentle. I've been a long time Window$ user and recently had to move up to being a system admin. I have a Window$ SBS 2003 server up and running with 5 client machines. I back up my server and my clients to a 320gb drive on my server right now. But I'm running out of room in a hurry. 
 
So I started looking for a second server to handle all my backups. First I started looking into the MS solutions and relized fast it was going to cost as much as my SBS server and the comercial NAS where just as bad and I knew that's wasn't going to fly with my bean counter. So a friend of mine told me to look into Linux, and am I impressed! You guys have some great stuff here. As of right now this looks like it will be my first Linux server and but it won't be my last either.
 
OK here's what I have so far. I took some spare parts i had and built a nice little server machine. Celeron Dual Core 2ghz E1400, 4gb ram, 160gb IDE boot drive and two 1tb WD SATA green drives.
 
I have the 160gb drive up and running with Ubunta Server 9.04 using Samba for my shares. What I'd like to do now is take my two 1tb drive set them up as a Raid1 mirror and share that with my system to take all the backup files from my Window$ machines. but I can't figure out how to build the raid and share it. Everything I've seen so far is for raiding the boot drive. And I don't want to do that. I'm sure it's going to be something really simple and I'll feel like an idiot once I figure it out. But any help would be greatly appreciated.
 
Best,
 
Roger

---

### Post by ian dobson on 2009-06-13
Hi,

For raid have a look at mdadm. Here's a link as a start:-
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

And then samba for sharing it with windows PC's.

Regards
Ian Dobson

---

### Post by TwiceOver on 2009-06-13
Also check out BackupPC.  It takes a little tweaking to get working right, but it runs on top of the server edition (administered by web interface) and goes out at night and backs up all your network machines.  

Handy little program and you won't have to deal with individual backup settings on each pc.

---

### Post by RvA944 on 2009-06-13
Wow that was fun! LOL But I have to working now. Doing a test backup on one of my machines now  Kewl! Thanks for the pointer to that mdadm thread, there was a link 
 
[[COLOR=#800080]http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID[/COLOR]]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID") 
 
at the bottom of it that I missed the first time I looked at that thread that really made it "easy" to set this up.  Getting the second share in samba took some looking around but once I figured out I just had to add a second configuration for it in the smb.conf file it was a snap.
 
Thanks again guys and I'll take a look into that BackupPC app next.
 
Roger

---

