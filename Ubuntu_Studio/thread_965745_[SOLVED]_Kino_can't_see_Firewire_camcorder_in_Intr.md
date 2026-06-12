---
title: "[SOLVED] Kino can't see Firewire camcorder in Intrepid"
date: 2008-10-31
forum: Ubuntu Studio
---

### Post by Envergure on 2008-10-31
Never worked in Hardy either.

When i switch to the "capture" tab in Kino i get "WARNING:  raw1394 kernel module not loaded or failure to read/write to /dev/raw1384!" and the buttons are all greyed out.

I tried both the normal kernel and the -rt one (which is older and stuck me in low-graphics mode) and reinstalling libraw1394.

Camcorder model is JVC something

---

### Post by Envergure on 2008-11-02
No problem - just went "sudo kino" and that was that :)  took me long enough.

---

### Post by Erlander on 2008-11-04
The problem with using sudo is that the video  files generated are owned by root and not you the user.

I found the following helpful:  [https://help.ubuntu.com/community/Firewire]("https://help.ubuntu.com/community/Firewire")
and in particular Method 5 at the bottom.

Rob

---

### Post by zeroge on 2008-11-04
Good sharing!There is a dining-room for the prisoners and another for the officers. The room [WarCraft 3 CD Key](http://www.mmovp.com/buy-cd-key-warcraft-3-cd-key-c-1268_1272.html) where the prisoners dine is a large hall capable of seating fully twelve hundred men.Each table is long enough to accommodate [Diablo 2 CD Key](http://www.mmovp.com/buy-cd-key-diablo-2-cd-key-c-1268_1270.html) to twenty men, and resembles an ordinary [StarCraft CD Key](http://www.mmovp.com/buy-cd-key-starcraft-cd-key-c-1268_1271.html) school-desk. There are no table-cloths or napkins; [Age of Conan cdkey](http://www.mmovp.com/buy-cd-key-age-of-conan-cdkey-time-card-c-1268_1351.html) nothing but a plain, clean board. The table furniture consists of a tin quart cup, a small piece of [Age of Conan time card](http://www.mmovp.com/buy-cd-key-age-of-conan-cdkey-time-card-c-1268_1351.html) pan of the same precious metal, which holds the hash, an iron knife, fork and spoon.

---

### Post by darco on 2008-11-21
I had to boot into Vista to capture a video!!!....not now...thanks man!

darco

---

### Post by Dai777 on 2008-11-22
> **Envergure said:**
> Never worked in Hardy either.

When i switch to the "capture" tab in Kino i get "WARNING:  raw1394 kernel module not loaded or failure to read/write to /dev/raw1384!" and the buttons are all greyed out.

I tried both the normal kernel and the -rt one (which is older and stuck me in low-graphics mode) and reinstalling libraw1394.

Camcorder model is JVC something

To set up kino to use raw1394 on Ubuntu do the following:
type in the following in to the terminal:

sudo gedit /etc/udev/rules.d/40-permissions.rules
type in your password

copy the line 
KERNEL=="raw1394",			GROUP="disk"
and paste it so the are are two of them.

now change the second line so it reads.
KERNEL=="raw1394",			GROUP="video"

and comment out the first line

reboot your system and Kino should be set up to capturte video.

here is an example:
# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
#KERNEL=="raw1394",			GROUP="disk"
KERNEL=="raw1394",			GROUP="video"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"

---

