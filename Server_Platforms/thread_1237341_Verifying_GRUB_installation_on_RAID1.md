---
title: "Verifying GRUB installation on RAID1"
date: 2009-08-11
forum: Server Platforms
---

### Post by rocknrollmouse on 2009-08-11
Running ubuntu server 8.1 on a 2 drives using a RAID1 disk array (mdadm).  How do I verify Grub is installed on both drives?

---

### Post by R.Bucky on 2009-08-11
This should tell you all that you need to know
```
sudo mdadm --query --detail /dev/md0
```

---

### Post by rocknrollmouse on 2009-08-12
Sorry if I'm being slow, but which line tells me if grub is installed on the physical drive?

---

### Post by R.Bucky on 2009-08-12
Below is the return from one of my RAID1 boxes. The response from the previously mentioned command tells you your Raid Level (RAID1), total Devices (number of active hard drives), and the "State", which informs you whether it is "active" or not. I am not sure what hardware configuration you have (i.e. RAID level, # of hot spares if any, etc...).

```
/dev/md0:
        Version : 00.90
  Creation Time : Fri Aug  7 06:52:35 2009
     Raid Level : raid1
     Array Size : 38435392 (36.65 GiB 39.36 GB)
  Used Dev Size : 38435392 (36.65 GiB 39.36 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Aug 12 14:06:26 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : ae78c7bc:a1a68591:a186c41c:c789acde
         Events : 0.11

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
```

---

### Post by alastair on 2009-08-12
I would try booting from each disk with the cable removed from the other. It's the best way to be sure really - and what I do. On Ubuntu Hardy 8.04.2, you might have to say "bootdegraded=1" at the grub line to get it to boot :

[https://wiki.edubuntu.org/BootDegradedRaid](https://wiki.edubuntu.org/BootDegradedRaid)

It does work though - but you need to make sure you install Grub on each disk i.e. (this example is only an example)

# grub
grub> find /grub/stage1
(hd0,0)
(hd1,0)
grub> root (hd0,0)
grub> setup (hd0)
grub> root (hd1,0)
grub> setup (hd1)

Hope that helps.

Alastair

---

### Post by rocknrollmouse on 2009-08-13
Hi R.Bucky,

Thanks for your reply.  I see something very similar (RAID1, no hot spare).  But which line here tells me if GRUB is installed on each hard drive?
(ie should one of the drives fail, the other will need GRUB for the server to re-start.  My understanding is this is a manual installation, not default, but as I didn't build this server I want to check what it has before starting and risk getting into a mess!)


Hi Alastair,

Thanks for your reply.  
Unfortunately this is an active server, and the last thing I want to do have it start in a degraded state, and then have to re-build one of the drives(!)  So I'm looking for a non-destructive command that can tell me what is installed.

As a last resort, I also though I could just re-install GRUB on both drives (although I really don't want to make *any* changes on this system until its officially under my control).

Can I just check the sequence of GRUB commands
> 
(hd0,0)
(hd1,0)
grub> root (hd0,0)
grub> setup (hd0)
grub> root (hd1,0)
grub> setup (hd1)

my understanding of the command was I had to select the drive (partition) then run the setup
> 
(hd0,0)
grub> root (hd0,0)
grub> setup (hd0)
(hd1,0)
grub> root (hd1,0)
grub> setup (hd1)

or am I misunderstanding the commands?

Also
> 
grub> find /grub/stage1

ran this on my test server (which does have GRUB on both drives) and got
> 
Error 15: File not found


---

### Post by fjgaude on 2009-08-13
Well, grub may be on both drives but is stage1?

---

### Post by alastair on 2009-08-13
> **rocknrollmouse said:**
> 
grub> find /grub/stage1

---> Error 15: File not found 


Maybe try :

grub> find /boot/grub/stage1

Because Grub's installed in /boot which is in / (and not a separate partition).

I generally do all of this stuff before the system's in production though :-)

---

### Post by rocknrollmouse on 2009-08-13
Hi Alistair,

Yes, I wih I'd had the option to do this before the server was live as well ;-)
with this I now get:
> 
grub> find /boot/grub/stage1
 (hd0,0)
 (hd1,0)

hopefully this is telling me GRUB is loaded in both hd0,1 and hd1,0 - which is exactly what I want (need) to see?

---

