---
title: "Building a NAS server (Raid 5)"
date: 2011-07-06
forum: Server Platforms
---

### Post by Dean Ironwood on 2011-07-06
Hi all, new to the forum here. I'm looking at building a small NAS setup for my home to hold all my media (DVD's, pictures, music etc..). I'm not too concerned with backups of it at this point as I have all the data elsewhere as it is, but would like one central spot to access it.

A friend of mine turned me on to Ubuntu to do this with but he's never tried it, so I'm looking to see if anyone else has done this or if there issues with it. I've used linux off and on for several years, but this would be my first Ubuntu install.

I'm looking at either using some older hardware I have sitting around, or something cheap like a small dell server (T310 or something). I'd get 4 2TB drives and just use them in a software raid 5 array. It would be accessed with a few different samba shares I'm thinking.

Is this feasible? Got any better ideas?

Thanks

---

### Post by rubylaser on 2011-07-06
If you're not really familiar with Linux, and you only need a NAS device, I'd probably just suggest installing [FreeNAS]("http://www.freenas.org/") on some older hardware. It's dead simple to install and setup.

If you need to extend beyond a simple NAS, then Ubuntu with mdadm may fit the bill.

---

### Post by linuxnizer on 2011-07-06
for personal use [check this]("http://www.amazon.com/Western-Digital-ShareSpace-Ethernet-Attached/dp/B001FAE64K/ref=sr_1_3?ie=UTF8&qid=1309970675&sr=8-3")

---

### Post by rubylaser on 2011-07-06
Those WD Sharespace's are okay, but VERY slow.  It takes forever to transfer files onto them.   If you already have hardware, just snap up a few 2 TB drives, install FreeNAS / Ubuntu + mdadm and your good to go.

---

### Post by Dean Ironwood on 2011-07-06
> **rubylaser said:**
> Those WD Sharespace's are okay, but VERY slow.  It takes forever to transfer files onto them.   If you already have hardware, just snap up a few 2 TB drives, install FreeNAS / Ubuntu + mdadm and your good to go.

From what I've seen/read, nearly all those "NAS in a box" solutions are notoriously slow, and cost about as much as just building something. Plus with building something you have expandability. Why I started exploring this route.

I was mainly looking for caveats with installing Linux (Ubuntu) on a pretty large raid volume (~6TB usable space). I don't recall the last time I installed any version of linux in a non VM environment where I didn't have some sort of hardware issue.:(

---

### Post by kgatan on 2011-07-07
Id recommend FreeNAS as well for a simple NAS. 
You can run it on a toaster and you get alot of goodies as ZFS filesystem, web-gui etc.
Check [www.freenas.org](www.freenas.org)

As Rubylaser wrote, if you feel you need more future applications Uubntu might be a better option. The community is also awesome so there's a lot of help to get if any problems.

---

### Post by Groodles on 2011-07-07
I am running exactly that which you are asking about.

Ubuntu Server with mdadm controlling 4x2TB drives in RAID6.  It's also hosting FTP/Samba/VPN and other bits and bobs.  Old hardware will be fine for running a RAID6 array.  All you need is enough ports for the drives you want to add to the array.

---

### Post by rubylaser on 2011-07-07
I love mdadm and have used it for years on many different platforms for many different purposes (my current home fileserver has 10 disks in a RAID6 array), but for someone with limited Linux experience and no Ubuntu experience who only needs a simple NAS like the OP is, there is no better way to go than a purpose built distro like FreeNAS or Openfiler for most users.

---

### Post by brighty22 on 2011-07-07
I actually just moved to ubuntu server *from* freenas earlier today. So far my experience with ubuntu has been... absolutely impeccable. Ubuntu server takes 5 seconds to boot, vs over 3 minutes with freenas. I built my own freenas machine with 4 1.5TB drives, and configured them in raid 5 (it has a Celeron with 1GB ram). With freenas, unless youre willing to spend ages partitioning, you really need a pen drive to store the OS on. Freenas raid does work, as one of my four drives did fai. No data was lost, however I only found out because the entire system slowed to a crawl.. transfers of 20KB/s etc. I could literally see the machine walk through the php rendering the webguiI.. it was honestly that slow. Scared the hell out of me.. which isn't great when 4.5TB of data is at stake. Mdadm is streaks ahead in both data transfer speed and initial sync time when first creating the array.

I ultimately shifted because I had installed MySQL and php on my freenas system (with a lot of effort), and couldn't upgrade them as freenas is an *extremely* watered down version of bsd. It really is worth emphasising that freenas is a NAS operating system rather than a server operating system, like ubuntu. Freenas is very much set it and forget it. When it's working, there's no maintenance at all, however when something breaks, or transmission suddenly throws a permission error claiming it can't access its download directory (and you are disappointed in the morning when you find everything has stopped), it can be a major headache. The freenas forums are of very little help, compared to the, as previously said, millions of people with seemingly limitless knowledge on, for example, this forum.

If you want simplicity, and don't like tweaking, go for freenas. Compared to ubuntu server, freenas is like using a mac - in terms of both boundaries and simplicity. For a bit more effort, I think ubuntu server is a much better choice in the long run.

---

### Post by ivank2139 on 2011-07-15
I just wrote up an article on another forum about using ZFS to do this.  I built a new machine and with a 64Gb SSD and added 4 2Tb drives.  ZFS manages all of them in a raidz1-0 configuration giving me 5.4Tb of storage.  It was really easy and seems to work just fine.  ZFS is great and I used it for many years on Solaris, OpenSolaris, and OpenIndiana.  Now it is available on  Linux, see ZFS on Linux project.

---

### Post by ythe1300 on 2011-07-15
Link pls :)

> **ivank2139 said:**
> I just wrote up an article on another forum about using ZFS to do this.  I built a new machine and with a 64Gb SSD and added 4 2Tb drives.  ZFS manages all of them in a raidz1-0 configuration giving me 5.4Tb of storage.  It was really easy and seems to work just fine.  ZFS is great and I used it for many years on Solaris, OpenSolaris, and OpenIndiana.  Now it is available on  Linux, see ZFS on Linux project.

---

