---
title: "help please - broke my network"
date: 2011-02-05
forum: Server Platforms
---

### Post by sjhupp on 2011-02-05
Ok, so running 64bit ubuntu sever 10.04LTS. Had everything working beautifully, then turned it off and unplugged it (to clean my study).
Then I:
- added another 2GB ram (was 4BG in the box before, just took out 2G to test another box)
- changed cabling of LAN (still eth0 on server though)
- plugged in few more ethernet cables to other server nic ports (those devices off though)
Now:
Boots up, but SSH fails: 
"ssh simon@starbug
Received disconnect from 192.168.1.250: 2: Packet corrupt" ??
Hooking up a monitor and kb, I can't apt-get update, so something with the network is wrong.  
If I try to ping my gateway, it responds ok, but has "wrong data byte #54 was ... should be ...". Is slow also, ~700ms direct cable.
BUT, can still remote into transmission and tvheadend web gui.
But no samba or vnc, no webmin. 

Any clues please?  :confused:
Happened once before (after plugging in other cables again) but I reinstalled that time. Don't want to this time though, as had everything configured perfectly :(
Cheers.

---

### Post by sjhupp on 2011-02-05
False alarm. Seems after 3 hours (no reboot or anything) it now works.
WTF ?? :confused:

---

### Post by sjhupp on 2011-02-05
Nope, now fubar again.
No samba or webmin, but I can add torrents to transmission, and just removed a completed one, but get the SSH error again.
That makes no sense to me - just proves the nic works I guess.
Any ideas please??

---

