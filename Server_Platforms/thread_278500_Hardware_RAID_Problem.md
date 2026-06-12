---
title: "Hardware RAID Problem"
date: 2006-10-16
forum: Server Platforms
---

### Post by slacker9876 on 2006-10-16
Good Day All, 
I had planned to dual-boot our Dell PowerEdge 2300 server this week to see how it handled versus Windows 2003 Server as Intranet server. I shut down our services after transitioning to our replicated server and began the installation. Everything was just like a normal desktop install until it got to partitioning where it seems to have permanently paused. I say paused because I can still launch other processes without issue, but the server has not allowed me into the partition setup screen.

This server is a dual processor P2/400 with 1GB RAM and 25GB free on the RAID 1 drive where I would like to install Ubuntu. I have the current 6.06 CD from Conical. I did select install or run live because we will in fact need *want* the GUI on this server since I will not be the only administrator.

If anybody has a tip on how to get past this, I would love to hear it. I will continue additional parameters and see what I can find, but this is an oddity that I have never seen. If not, I'll try the LAMP CD and add GNOME later.

Thank you.

---

### Post by slacker9876 on 2006-10-16
OK, so my previous mirror did not have the server nor alternate ISO's ... and I had no idea those existed. Mods, feel free to kill the thread.

---

### Post by slacker9876 on 2006-10-16
OK, perhaps I was too quick on closure. I have downloaded and burned BOTH the server CD-ROM and the ALTERNATE CD-ROM. Neither one boots ...

On the "factory" CD-ROM I tried earlier, it was as easy as selecting "0" when the SCSI bus recognized the bootable disc. Now it still recognizes it but will not boot the darn thing. I tried both in my laptop and they booted just fine. Is there something special I need to do, in order to have a Dell PowerEdge 2300 with SCSI only CD-ROM boot one of these disks?](*,)

---

### Post by Charles Hand on 2006-10-16
When you say "hardware raid", are you talking about "fake raid"? Fake raid (often called hardware raid) is software raid which is partially implemented in the bios. But it's still software raid, the CPU is still doing the raid-ing. There are a number of threads on these forums on this subject (try searching for "fake raid"). I tried to get it working and finally gave up.

The only reason for using bios fake raid that I can think of is if you want to dual-boot and you want to access your Windows filesystem from Linux.

I ended up turning off the fake raid in order to have the windows filesystem available on Linux. But now that I'm ready to dump the Windows part all together, I'll configure Linux software raid.

---

### Post by slacker9876 on 2006-10-16
I appreciate the quick response. No it is not fake RAID. This particluar system has a PERC 2/dc RAID card with 16MB of RAM onboard. I do need to keep the Windows file system in tact and access could be nice because then I can copy the webs from the local disk instead of over the LAN.

My RAID is the real McCoy with a hardware driven mirror and span off the same controller. It is old, but it is real.

---

### Post by slacker9876 on 2006-10-16
OK, Never mind again ... mods delete again.

Apparently in what they thought to be infinite wisdom (I think it is finite myself), Ubuntu removed the support for all Dell PERC, 2, 3 cards.

Guess perhaps FC5 may be the next route.

---

### Post by ebozzz on 2006-10-21
I'm just curious. Did you have any success getting Ubuntu installed on your 2300? I am trying to complete the same task.

---

