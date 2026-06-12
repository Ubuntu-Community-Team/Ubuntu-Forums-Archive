---
title: "Network Interfaces Moved"
date: 2007-04-25
forum: Server Platforms
---

### Post by shimmyt on 2007-04-25
Well here's the story: I am in the process of creating a snort farm on 5 actual IDS boxes feeding their data to one mysql database on a 6th box. These are all HP Proliant DL360 G4 setup with RAID-1 (mirroring), with 4 network ports (2 built in and 2 cards). I setup the first IDS box no problem, then I did what I normally do to create an image. I took one of the hard drives out and booted it up on another box with no problems. Now when I look at the interfaces they are no loner eth0, eth1, eth2, eth3, but are now eth4, eth5, eth6, and eth7. I know how to fix this in Windows, but I can't seem to figure out how to remove the instances of the old interfaces so the new ones show up as eth0 - eth3. Any help is appreciated!

---

### Post by spd106 on 2007-04-26
Check the /etc/iftab for MAC addresses, if there are any in there clean them out and re-image.

---

### Post by shimmyt on 2007-05-04
That's exactly what I was looking for! Thanks :)

---

