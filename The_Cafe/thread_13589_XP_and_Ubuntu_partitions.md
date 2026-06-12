---
title: "XP and Ubuntu partitions"
date: 2005-02-01
forum: The Cafe
---

### Post by ctt1wbw on 2005-02-01
I have XP and Ubuntu on my laptop right now, but I want to take space away and give it Ubuntu.  I have Partition Magic on my XP side.  If I resize the XP partition and then reformat the saved area for Linux, can I merge the new space with my Ubuntu partition?

Am I doing this the hard way or what?  I've not used fdisk yet.

---

### Post by crane on 2005-02-01
Why are you trying to do this? Are you running out of space with ubuntu?
The best thing I could think of would be to reformat the new partition, then mount through fstab.
Possible you home directory id getting to big? then mount the new drive as /home.
Before doing this I would mount it to a temp file first and copy all your files over.

---

### Post by ctt1wbw on 2005-02-01
I'm not running out of room yet, I just wanted to learn how to do it.  But that's not a bad idea of creating a mounted /home disk.

---

### Post by crane on 2005-02-01
[QUOTE=ctt1wbw]I'm not running out of room yet, I just wanted to learn how to do it.  But that's not a bad idea of creating a mounted /home disk.[/QUOTE]
 
I personally do not have /home mounted on different partition. I do have /usr/local/games mounted on a different partition for my games. Right now I have Quake3,UT2004, Enemy Teritory, wolfenstein, and Doom3 installed. this keeps me from reinstalling the games every time I reinstall the OS. I just tell the install partitioner if it asks to mount the partition on usr/local/games and boom I have all my games again!

 I also have a backup file on that partition that I save config files I tweaked in. (samba,X11, etc)

---

