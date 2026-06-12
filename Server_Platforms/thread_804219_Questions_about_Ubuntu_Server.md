---
title: "Questions about Ubuntu Server"
date: 2008-05-22
forum: Server Platforms
---

### Post by sebz2005 on 2008-05-22
My Father and I are looking at getting a new server for a company and we're thinking of getting Ubuntu Server.


Before I start asking the questions, I'll give a few details so you can understand.

Windows SMB is running on this network.
We plan to have the server contain up to 250 Gb worth of .dwg files (up to a few hundred megs each)
35 computers are already connected to the network.


Now for the questions.

How many concurrent connections can I have at a given time?
Can Ubuntu Server have a RAID-1 setup with 4 hard drives? (OS on one pair and data on the second)

Thanks in advance.

---

### Post by freebeer on 2008-05-22
To my understanding, there's no limit to the number of concurrent connections.  We're not talking Microsoft and their CLAs here. :D

I've never played with RAID1 in Linux, but many folks have posted on these forums about similar setups, so I would not expect that to be an issue.

---

### Post by sebz2005 on 2008-05-22
Cool!

Thank you so much!

---

### Post by freebeer on 2008-05-22
Feel free to post back when you want help/advice in planning and setting it up.  I still consider myself a neophyte (a tick above a noob) but I've managed to set up Ubuntu as a server for my little company (7 windows clients) without much difficulty.  It's been my experience, for what it's worth, that the Linux box is more stable and requires less hand-holding than does the Win2003 Server that I have.

---

### Post by jonabyte on 2008-05-23
one of the main file servers I have setup just has two 500gb hd's one has the os/programs, the second has all the data.
They did not want raid for some reason and are happy with this setup.
There are over 25 users who access it, I am assuming you will be getting new hardware for this server, if so 35 users shouldn't be a problem.

---

### Post by NateMan on 2008-05-23
I know linux software raid can easily handle a raid1 setup, and 2 port true hardware raid cards for ide are less than $20. I'd buy two of those and use hardware. Check out weirdstuff.com, they normally have some nice deals on older ide raid cards, which are plenty fast for a server environment.

---

### Post by artesvida on 2008-05-23
Yes, if you're going to do RAID, I suggest hardware RAID.  I have successfully run Ubuntu server on older HP Proliant hardware (both somewhat old and really old).

---

### Post by andguent on 2008-05-23
Of the two dozen raid setups I've been involved with, hardware raid has been more likely to cause issues then software raid. Especially when dealing with cheap hardware raid. Reassembling a failed mirror can be a pain if the firmware doesn't feel like using your new drive. Some of those partitions aren't very readable for recovery purposes.

Software raid is very flexible, and only needs useable drives with the same geometry. You can monitor progress without any special software (mdadm is in the main apt-get pool). The only time it is more complicated is when trying to do a knoppix boot and reassemble. Even then, it is only 3-4 commands and you are into your data.

Resources I use:
[http://really.slacking.net/~modat7/howto/RAID-mdadm-Setup.txt](http://really.slacking.net/~modat7/howto/RAID-mdadm-Setup.txt)
[http://www.linuxsa.org.au/mailing-list/2003-07/1270.html](http://www.linuxsa.org.au/mailing-list/2003-07/1270.html)
[https://alioth.debian.org/projects/rootraiddoc/](https://alioth.debian.org/projects/rootraiddoc/)

In the end, it comes down to what you are comfortable with. If you have more experience with hardware raid and are aware of its limitations, use that. If you love command line and are familiar with modprobe & rsync, use software raid.

As for concurrent connections, that will only be limited by hardware speeds. If you are dealing with 35 AutoCAD users, 15 of which are concurrently screwing with .5G dwg files, your bandwidth will most likely be your bottleneck. It won't matter what OS you run, a $10 nic will pull you to your knees. 

Test network functionality with a handful of 'ping -f server' commands, aka ping floods, running over the course of an entire weekend. If your switch or nic melts from that type of activity, you don't want to run AutoCAD over it either. Some minor packet loss is to be expected.

---

### Post by quad3d@work on 2008-05-23
Yea.... I agree with above.

Software RAID is quite good in respect compares to HW RAID, IMHO.

If drive falls, you gotta reboot the server, go into RAID controller BIOS, and rebuild the drive. With mdadm just set fail on the drive, track down which one, replace on spot, and rebuild the array. No reboots.

Solaris admins in-house loves ZFS. :)

---

### Post by carbm1 on 2008-05-23
Doesn't your motherboard/controller has to support hot swap in order to rebuild your data without rebooting???

This is the best tutorial I have seen on software raid:
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

---

