---
title: "SCSI (Scuzzi) Drives sceaching!"
date: 2008-10-30
forum: Server Platforms
---

### Post by gazz1982 on 2008-10-30
Dear all I have just picked up an old server (2002) and I am hoping to turn it into a Kbuntu powered mapserver, it still has windows on it and everytime I boot it up it sceaches very high pitch - a friend says its the SCSI alignment - does anyone have any idea how to fix this?

---

### Post by Wayne_V on 2008-10-30
If you are sure it is coming from the scsi disk I would say get rid of it .... not worth fixing.

Install smartmontools and see what they have to say about the drive:

$ sudo apt-get install smartmontools
$ sudo smartctl -a /dev/sda   (assuming this is the only drive)

---

### Post by 080829k on 2008-10-30
[**world of warcraft gold**](http://www.oofay.com/)Bornakk does point out that at least, with the level 55 creation level, you can start the Death Knight on a seperate server and get a feel for it before deciding if you want to delete or transfer a character on your main server. cheap [**wow gold**](http://www.oofay.com/)Still, I know that half the fun for me is getting a good name reserved for my character, [**wow gold**](http://www.oofay.com/)so I've personally already deleted a lowbie Draenei Paladin from my main server in order to create a placeholder character with my chosen name

---

