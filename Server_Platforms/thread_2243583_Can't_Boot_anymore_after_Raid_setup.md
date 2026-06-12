---
title: "Can't Boot anymore after Raid setup"
date: 2014-09-09
forum: Server Platforms
---

### Post by Darin_Mosier on 2014-09-09
I have server 12.04 (using for samba server)  and it's was running with two 500 gb drives at  raid1 in three partitions. 1. swap,  2. sys files, and 3. /home dir in it's own partition.  It was running fine until I tried to add two 1tb drives in another raid config.

Now System will not boot from HD.  I can boot to xubuntu I have on thumb drive but that's it.  In xubuntu I can manage the partitions but I need help mounting drives and editing the config to go back to before.

Suggestions?

---

### Post by Darin_Mosier on 2014-09-10
UPDATE1:  It's not the raid. I was able to run mdadm on the raid and they all checked out.  

It was booting to a blank screen when I'm using a DVI cable.
If I use a VGA cable I can see that it tries to boot then hangs on something but I can't read it because it's showing squares and characters that are not readable.

UPDATE2:
3:18pm MST - Still can't view the screen message.  I tried different video cards but same result.  I think it's something to do with my Flat screen.  Going to go try a VGA monitor. if I can find one.


Is there a way to boot with no server packages running??  (kinda like safe mode for windows?)

---

