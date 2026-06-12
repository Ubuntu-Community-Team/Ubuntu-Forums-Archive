---
title: "Bot intrusion while running latest Ubuntu beta"
date: 2008-10-25
forum: Security
---

### Post by knoopx on 2008-10-25
Past week i got home and somehow a bot managed to open the terminal and execute random commands. Exactly it the made my computer to download an archive from internet ([http://freesms.xail.net/pascee/cmd.tgz](http://freesms.xail.net/pascee/cmd.tgz)), unpack it under /tmp/ and execute a binary file called "stealth". The archive was full of DOS utilities but none of them was "apparently" executed.

Output of the "stealth" command executed was "Stealth> 80.67.5.22 : port 80". Immediately I disconnected the machine from internet and tried to sniff the traffic. I was unable to log anything so i tried to ensure there was no rootkit installed. I'm currently not using the computer, i'm just waiting until the final release of the new ubuntu to reinstall the whole system but I'm a scared about if some personal information was stolen.
 
Is there any known vulnerability on latest Ubuntu beta? Does somebody know anything about the "stealth" tool or anything related to this intrusion? I found almost no information but this guy seems is having the same problem:
[http://xceedspeed.com/forums/showthread.php?p=2122058](http://xceedspeed.com/forums/showthread.php?p=2122058)

---

### Post by dburnett77 on 2008-10-25
Could be executes from your temp dir.
I often execute:
sudo rm -r *
from the /tmp dir.

I've seen guys compile random error bits in that directory.  Good maintenance.  And, as a funny thing I've noticed, my OS became inoperable after this procedure, once so far.

---

### Post by Kinstonian on 2008-10-25
Deleting files in /tmp knowing it is going to delete potentially valuable evidence that can help answer a lot of questions you have during an incident doesn't make any sense to me.

---

### Post by koenn on 2008-10-25
> **knoopx said:**
>  
Is there any known vulnerability on latest Ubuntu beta? Does somebody know anything about the "stealth" tool or anything related to this intrusion? I found almost no information but this guy seems is having the same problem:
[http://xceedspeed.com/forums/showthread.php?p=2122058](http://xceedspeed.com/forums/showthread.php?p=2122058)

maybe the vulnarability is you ?
the other guy you point to left vnc accessible to the internet. which services do you expose to the internet ?

---

### Post by tgalati4 on 2008-10-25
VNC is not secure when its ports are left open to the interweb.  That applies to any version of Linux/Ubuntu/etc.  The intrusion was probably incidental.  If this was a windows machine, then the code would probably have executed.

You can tunnel VNC through SSH but there are better ways for secure remote access to your machine.  It depends on what you need to do.  Sometimes running web-based administration/services is easier and more secure.

---

### Post by The Cog on 2008-10-25
> If this was a windows machine, then the code would probably have executed.
Don't be so sure. Windows doesn't use .tgz files, or have a /tmp folder. This intrusion almost certainly knew it was on a Linux box.

---

### Post by koenn on 2008-10-25
> **The Cog said:**
> Don't be so sure. Windows doesn't use .tgz files, or have a /tmp folder. This intrusion almost certainly knew it was on a Linux box.
and linux doesn't use "DOS utilities" (re OP)  :)

---

### Post by Kinstonian on 2008-10-25
> **koenn said:**
> and linux doesn't use "DOS utilities" (re OP)  :)

I think he meant DoS utilities. :)

---

### Post by koenn on 2008-10-25
oh.

---

### Post by cariboo on 2008-10-25
I just snooped a bit and all those files are linux binaries, so they should work on your computer :)

Of course I'm not saying that you should, but if you make the .pl scripts executable they will run. They are missing a perl module, so they won't do much good.

The other executables need to be run as root. They are fairly old programs so most  of the exploits have been repaired.

Jim

---

