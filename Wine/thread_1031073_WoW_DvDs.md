---
title: "WoW DvDs?"
date: 2009-01-05
forum: Wine
---

### Post by jbaerbock on 2009-01-05
So I've been messing with Linux off and on for awhile. Am back and trying to install WoW. Have gotten World of Warcraft installed fine before but I ran into a snag this time. I have WoW Original installed but for some reason I can't get Wine to install from DvDs. I followed the usual instructions from the ubuntu community guide but nothing seems to work. I have Linux Mint (Intrepid Ibex basicaly). Any clues?

---

### Post by donkyhotay on 2009-01-05
Installing from CD/DVD can be a little odd using wine. There are two main ways of working around it, the first (and my recommendation) is to just download the installer and install from that rather then the discs. If for some reason you absolutely can't do that then copy all of the files from the DVD onto your hard drive and then run setup from there.

---

### Post by jbaerbock on 2009-01-05
I already have WoW installed just need to install both expansions. When I try to run the installer from the DvD or after copying files it gives me the error in the following image:

---

### Post by jbaerbock on 2009-04-18
UPDATE:
I figured out how to always work with installing WoW DvDs. You must unmount it and then remount it as follows:

sudo mount -t udf -o ro,unhide,uid=username /dev/scd0 /media/cdrom0/

Where it says uid=username you must replace the username with the username you created for Ubuntu.

---

