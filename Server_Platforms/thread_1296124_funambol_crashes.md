---
title: "funambol crashes"
date: 2009-10-20
forum: Server Platforms
---

### Post by mutrax on 2009-10-20
Hello all,

I'm trying to get a vanilla funambol 8.0.1 server running. There are great tutorials on how to do the trick by using mod_jk, or a custom java, etc.., but I just want the standard bundle up and running on hardy 8.04.3 and work my way up from there.

I tried the installation on a 9.04 desktop version and it starts and runs without any glitches. But on a 8.04.3 server it starts for a few seconds (i can browse to port 8080 within a few secs) but then crashes eventually.

Can someone point me toward a way to troubleshoot this problem, or did anyone had the same problems....

Anyway thanks! I couldn't google my way out of this (even tried french and italian howto's)

Regards, 
Ed

---

### Post by smaffulli on 2009-10-21
What processor do you run on? is your ubuntu 32 or 64 bit? do you have enough ram? these are the things that come to my mind. HTH
stef

---

### Post by mutrax on 2009-10-24
The server runs on a Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz.
Memory available;
MemTotal:      1025640 kB
MemFree:        639796 kB
Buffers:         22188 kB
Cached:         205040 kB
SwapCached:          0 kB
Active:         202288 kB
Inactive:       156584 kB
HighTotal:      121408 kB
HighFree:          240 kB
LowTotal:       904232 kB
LowFree:        639556 kB
SwapTotal:     3004024 kB
SwapFree:      3004024 kB
Dirty:              64 kB
Writeback:           0 kB
AnonPages:      131656 kB
Mapped:          54480 kB
Slab:            13040 kB
SReclaimable:     4780 kB
SUnreclaim:       8260 kB
PageTables:       2296 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   3516844 kB
Committed_AS:   340320 kB
VmallocTotal:   118776 kB
VmallocUsed:      5628 kB
VmallocChunk:   112652 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB


Thanks for taking the time to help me out. is funambol such a resource hog?

---

### Post by mutrax on 2009-10-26
What I did try out...

Replace the embedded java 1.5.0 with the 1.6.0 from the server environment (java_home)


Run it on the systems tomcat server (5.5) instead of the embedded one (6.0)

Us a mysql server instead of the embedded DB used.

Could someone point me in the right direction in how to diagnose the problem (were's funambol/tomcat/java error output?, checked /var/log/messages allready):confused:

---

### Post by mutrax on 2009-11-07
I'm still at it.... just some good advice on how to troubleshoot this problem would be much appreciated...

---

### Post by mutrax on 2009-11-22
So I installed it on a fresh 8.04.3 server install and it works.... So how do I figure out why it isn't working on production server?

Can anyone give me some advice?

---

### Post by mutrax on 2010-06-14
Well the problems where caused by another daemon instance (vmware) running another version of java.
See [http://ubuntuforums.org/showpost.php?p=9458768&postcount=11](http://ubuntuforums.org/showpost.php?p=9458768&postcount=11)

---

