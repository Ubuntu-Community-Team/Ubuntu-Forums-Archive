---
title: "Server won't boot after fresh install"
date: 2006-06-06
forum: Server Platforms
---

### Post by mkong on 2006-06-06
Converting my home server from Windows to Dapper.  I've got an Intel P4 2.4Ghz, 1GB or RAM, with a 3Ware 7500-4 RAID controller configured in hardware for RAID5 with 3 drives.

I went through the installer, and everthing seemed to work fantastic.  The system reboots and then hangs at 

[FONT="Courier New"]*Running local boot scripts (/etc/rc.local)[/FONT]

Anyone have any ideas?

---

### Post by nokiahackman on 2006-06-26
Same prob for me.

I had two cd drives - well one internal and one external via USB - it is actually a dvd rewriter.

After I had detached the usb device and did a re-install - it seemed to work fine.  

Have you got two drives?

ps..I am a linux virgin

nh

---

### Post by Original Syn on 2006-06-30
I am also experiencing this.

Celeron 900mhz
256mb ram 
10gb ide hdd
36x CD-ROM

There's nothing special about the machine, no USB devices attached just vga monitor, ps2 kb/mouse, and 10/100 NIC.

I ran the base install to harddrive no settings really out of the ordinary.

**Edit:** Apperantly it was just taking it's sweet a** time, I let it sit for 30 minutes and it finally gave me a login.
**Edit2:** I was wrong again, ubuntu doesn't like my monitor and text is extending passed the bottom, every time I switch back from my other desktop I have to readjust the vertical.

---

### Post by MJN on 2006-07-01
It might be worth you all booting from a live CD and checking the logfiles on your HDDs - e.g. /var/log/syslog and /var/log/boot just to see if the last line(s) give any indication as to what was happening prior to the hangs.

Mathew

---

