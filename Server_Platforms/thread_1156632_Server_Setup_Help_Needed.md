---
title: "Server Setup Help Needed?"
date: 2009-05-11
forum: Server Platforms
---

### Post by totaltechnologyllc on 2009-05-11
I have already installed ubuntu server on an old hp, added a sata raid card, a port multiplier, 5 1.5TB HDD, new case and power supply. Need some help with the setup of the system, just still very new at this, and need some pointers.

I need to setup a software raid5 with my 5 drives and then get samba working to share them for the windows network. I had the raid up and working once, but must have missed a step because once I reboot, the raid didn't exist anymore! Installed ebox, which is pretty cool, but until i get the raid working right that is not really going to help.

I am total new to server, and reasonable new at linux in general.

I am sure this is pretty simple, just need some pointers and advice, Thanks,

Pat

---

### Post by tommynz1975 on 2009-05-11
have a look in the server section... are a few howto's

---

### Post by kevmev12 on 2009-05-12
I'm a total n00b at Linux as well as server and RAID installations (only 3 weeks into my own Linux/Ubuntu self-education!) but the official Ubuntu documentation really helped get my head around the whole concept; and now my server is running perfectly. Read this to help with setting up RAID:
 
[https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html)
 
My home file/media server has a 80GB HDD with / on it and 4.96GB swap space, and 2 x 1TB HDD running in RAID1 configuration with /home on it - all 3 HDDs are connected to the motherboard, no extra SATA or RAID controller cards installed.
 
As for samba, there are many how-to guides in this forum and outside on how to setup samba shares. I personally used an amalgamation of different tutorials to help me setup what I want but this guide would be a good start:
 
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)
 
Good luck!!

---

