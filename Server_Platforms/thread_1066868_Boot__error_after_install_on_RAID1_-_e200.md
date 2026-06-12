---
title: "Boot  error after install on RAID1 - e200"
date: 2009-02-11
forum: Server Platforms
---

### Post by gavrochelegnou on 2009-02-11
Hi, 

I just installed an ubuntu-server (tried 8.10 and 8.04, x86 and amd64) on a HP proliant ml110-g5 with the onboard raid controller (e200)
Install works like a charm it detects the raid(1) array and installs everything but on first boot it show the following :

"
Gave up waiting for root device. 
...common problmes...
-Missing modules (cat /proc/modules, ls /dev)
ALERT! /dev/mapper/ddf1_ARRAYNAME1 does not exist; Dropping to a shell!
"

I tried waiting and typing "exit" but still doesn't work.
Tried rootdelay=90 without any luck too ....

Any idea ?

---

### Post by gavrochelegnou on 2009-02-12
Up anybody ?

could it be something about module not loaded ? a specific module to load ? anything ?

---

### Post by gavrochelegnou on 2009-02-12
Ok found it !
For further reference , 
To make it work :

Once dropped into busybox type :
# dmraid -ay
# exit

Then ubuntu will boot

Once it's fully booted, upgrade your system
# apt-get update
# apt-get upgrade
# apt-get dist-upgrade

AND the magic one ! 

# dpkg-reconfigure dmraid

---

### Post by fjgaude on 2009-02-12
Interesting... you actually booted from a raid1 hardward card that **dmraid** knows about? And from there you fixed the issue yourself. Wonderful!

Thanks for letting us know just what was going on.

---

