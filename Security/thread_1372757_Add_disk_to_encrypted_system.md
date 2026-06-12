---
title: "Add disk to encrypted system"
date: 2010-01-04
forum: Security
---

### Post by baltazar3 on 2010-01-04
Im running ubuntu server 9.04 and I encrypted the whole system disk on installation. There was an option on the livecd to do this. Anyway, I would like to add a new disk to this system. The best thing would be to use the same encryption and same keyword for this new disk. I realize that its probably not that simple, but if I could get info on what underlying program the livecd used for encryption then I got find more info on my own.

---

### Post by FuturePilot on 2010-01-04
The live CD cannot set up full disk encryption. It only has the option to set up an encrypted /home using ecryptfs.

As for adding another disk I would assume you could add another disk to the LVM volume and it would do what you want it to do. Though I'm no expert on LVM.

---

### Post by bodhi.zazen on 2010-01-05
You can do this with a live CD:

[How to: Resize an Encrypted Partition (LUKS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=4530641")

---

### Post by baltazar3 on 2010-01-05
Nice tutorial! Exactly what is was looking for.

---

