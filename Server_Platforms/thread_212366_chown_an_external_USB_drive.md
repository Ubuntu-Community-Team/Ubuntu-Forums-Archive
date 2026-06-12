---
title: "chown an external USB drive?"
date: 2006-07-09
forum: Server Platforms
---

### Post by tgoose on 2006-07-09
I'm using a 200 GB USB HDD to store music to be streamed onto other computers on the network, but unfortunately it seems stuck on root ownership, which means I can't use it for many things unless I run them all as root. Running sudo chown {non root username} says "Changing ownership of '{some directory}/': Operation not permitted. This applies to the drive itself and all directories contained within it. The drive is automatically mounted on /media/sda1 at startup and (I think) whenever it's connected. Is there any way I can do this? Thank you.

---

### Post by simonn on 2006-07-10
The fat specifications do not allow for file permissions, so this is handled for the whole drive at mount time.

Have a look at the "Mount options for fat" section in man mount.

---

### Post by ExMachina on 2006-07-10
I have a 350gb external NTFS hdd. 
How do I set it so my linux box will rwx and i can use it as a netwrok storage unit?

---

### Post by lamego on 2006-07-10
You can't use NTFS for read-write on Linux. You would need to convert it to FAT32.

---

