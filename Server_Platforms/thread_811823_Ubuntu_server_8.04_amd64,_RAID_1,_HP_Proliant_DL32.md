---
title: "Ubuntu server 8.04 amd64, RAID 1, HP Proliant DL320"
date: 2008-05-29
forum: Server Platforms
---

### Post by badc0de on 2008-05-29
Hello all, i have a problem. HP ProLiant DL320 G5, 2x250GB SATA. 
In RAID controller menu generating RAID 1 array. 
Launching install - installer shows me TWO harddisk's. 
How i install server on my raid array?

---

### Post by artesvida on 2008-05-29
This is hardware RAID?  And you're sure that the mirror wasn't already partitioned?

That's weird indeed.

---

### Post by TheGameAh on 2008-05-29
I have a VERY similar, only mine has smaller drives, and is a G4.

I ran into the exact problem a few months ago in installing Ubuntu.  Turns out, the G4 doesn't use hardware RAID, but FakeRAID (I'm guessing you might have the same problem).  Basically, not a true hardware RAID, so Ubuntu will see two separate drives instead of a RAID array.

2 options.  Either install a true hardware RAID controller.  Or, use Software RAID (this is what I did).

Although, just FYI.  I ended up switching to Debian, at least for my server installs.  It turns out that Ubuntu will not boot if one member of a RAID array is missing (pretty much defeating the purpose of a RAID array).

---

### Post by carbm1 on 2008-05-29
Similar situation here too with a Compaq Proliant DL310.  The IDE Raid is really fake-raid and only works on Windows.  Oh well... Software RAID is just as good in my opinion.  As far as Software RAID only booting off of one hard drive thats just because GRUB isn't installed on both hard drives.  There are some tutorials around about using Software RAID that is reduntant where you can boot from either drive.  Here is one I like: [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server)

---

### Post by TheGameAh on 2008-05-29
That's what I thought at first (GRUB not being on both drives).

As it turns out, not the case.  I DID install Grub on both drives.  And pulling one, meant the system wouldn't boot.

I dug high and low (there's a long post here on it too, I'll dig it up).  Turns out that Ubuntu does have a bug (it is classified as a bug) where a RAID will not boot while missing an array member.

---

### Post by badc0de on 2008-05-29
I'd not understand. So my raid that i setup after post, before os loaing (on hardware level) is fake raid?

if so, why some other linux os'es is detecting my raid as one single drive? (no brands than ubuntu, no ask).

---

### Post by badc0de on 2008-05-29
> **artesvida said:**
> This is hardware RAID?  And you're sure that the mirror wasn't already partitioned?

That's weird indeed.

Server is at the ends of my fingers. Yep, i'v made array in hardware menu before any system installing. i'v label it, some linux distros founded my RAID 1 name, but not Ubuntu. 

If really, i want ubuntu on my server, but i can't.. coz i see 2 hard drivers, if need i cant drop out here dmesg output.

---

### Post by lptr on 2008-12-22
Hi all,

would like to know if it is possible to switch an Proliant DL320G5p (with Intel Xeon 3075) into plain SATA mode, so faikRAID is just not working? 

Anybody?

rob*

---

