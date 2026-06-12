---
title: "IMB x3650 Server issues with Ubuntu"
date: 2008-12-11
forum: Server Platforms
---

### Post by bishopvle on 2008-12-11
We have just purchased a IBM x3650 model 7979KWG 4 gig ram
5 x 146 gigbyte SAS drives in a RAID 5 config im sure its an adaptec RAID Controller. 

Previously I have installed ubuntu server edition 8.10 on a test server and everything has been fine though this was a 5 year old server with only 1 SATA hard disk.

Yesterday we installed ubuntu server 8.10 on this new server, the install looked to go through ok, get to the end screen where it says that it needs to be restarted, and to take out the disk. Doing this the server reboots but not properly, we get past the bios screen, but theres no prompts or anything that looks like linux starting up. we get a flashing - cursor then a tottaly black screen for a second then the flashing - cursor. Pressing any key does nothing. And its definatly not the promt in linux.

We have reinstalled it again and same problem, and even installing the 64 we end up with the same problem. 

Any one else had this problem

---

### Post by Golfonauta on 2009-01-28
I'm installing the same server and I have the same problem, after reboot I can only see _ on screen. It's a new x3650 with the serverraid 8k, 4 discs on a Raid 5. The setup detected the raid and made everything well (it loocked well) but after reboot there is nothing to see. I'm gona try to find if it's externally accesible by ssh or com port if I have enougth time.

---

