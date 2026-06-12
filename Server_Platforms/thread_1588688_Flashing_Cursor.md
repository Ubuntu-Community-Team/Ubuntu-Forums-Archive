---
title: "Flashing Cursor"
date: 2010-10-05
forum: Server Platforms
---

### Post by tacobelldog52 on 2010-10-05
I have tried to search the net before posting here, and haven't found something exactly the same as mine. ( Though I know that is often mis-proven quickly )


Trying to install 10.04 (64) on my server. It has an nvidia on board raid setup in a mirror (0.0) and (0.1). Ubuntu installs fine, asks you to take out the disk and restart. The server restarts, the raid controller loads, and then it goes to a screen that has a flashing cursor in the top left corner. I have tried opening a new console with a keyboard shortcut ( but it didn't work ). Ubuntu does work fine, and boots if I take the one of the hard drives out and install it on a single disk. 

Any help would be great

---

### Post by arrrghhh on 2010-10-05
So are you doing RAID0?  RAID1?  It seems your array isn't properly configured... You setup the RAID before you install right?  Hardware RAID has to be in place before you boot that install disc...

---

### Post by tacobelldog52 on 2010-10-05
Yes the raid is setup in a RAID1, and it is setup as the bootable disk both in BIOS, and the RAID management.

---

### Post by tacobelldog52 on 2010-10-05
I found a post on another forum 

[Here]("http://www.linuxquestions.org/questions/linux-newbie-8/fc6-grub-with-flashing-cursor-496516/")


The problem is very similar to mine, but I am doing  a clean install with no XP.


Anyone have any guess, kinda desperate at this point.:)

---

### Post by arrrghhh on 2010-10-05
Hrm, not sure TBH.  Curious, can you boot the Desktop LiveCD?  Can you mount the RAID array after the install?  I'm curious if everything is correct in there.

Admittedly, I've never setup a hardware RAID array so I may not be the best troubleshooter in this case ;)

---

