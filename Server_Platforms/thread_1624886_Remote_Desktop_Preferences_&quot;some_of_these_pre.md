---
title: "Remote Desktop Preferences &quot;some of these preferences are locked down&quot;"
date: 2010-11-18
forum: Server Platforms
---

### Post by M1GEO on 2010-11-18
Dear all,

I have a computer running Ubuntu 10.04.1 LTS.  I am trying to get remote desktop sharing on this machine.  I have several other computers that I have successfully got Desktop Sharing (VNC) working on, but I cannot, for some reason, make this one work.

Going System > Preferences > Remote Desktop tells me "some of these preferences are locked down."  Actually, everything is.

Any advice that may help me figure it out?  I've tried googling and a lot of pages about development come up, and most in languages I cannot read.

Any help or pointers would be great, Cheers.

---

### Post by M1GEO on 2010-11-18
Solved. I had x11vnc running in tbe backround, which started via a script. I stopped this. I also restarted the computer to load an updated kernel.  Not sure what caused it work, but after the restart it now does :)  Just for the record.

---

