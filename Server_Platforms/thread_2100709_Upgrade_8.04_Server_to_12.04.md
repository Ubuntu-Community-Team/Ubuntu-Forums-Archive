---
title: "Upgrade 8.04 Server to 12.04 ?"
date: 2013-01-02
forum: Server Platforms
---

### Post by sentinelace on 2013-01-02
I have a 8.04 running qmail.  Is there a way to upgrade this to 12.04?

---

### Post by CharlesA on 2013-01-02
If you are going to upgrade, you would have to bump to 10.04, then 12.04.

I have no experience running qmail, so I do not know if you will run into any problems or not, but whenever you do an update make a full system backup beforehand.

---

### Post by sentinelace on 2013-01-02
Okay. I'll give that a shot

---

### Post by CharlesA on 2013-01-02
You can find upgrade notes here:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

It looks you cannot bump directly from 10.04 to 12.04 until 12.04.1 is released.

---

### Post by CharlesA on 2013-01-02
You can find upgrade notes here:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

It looks you cannot bump directly from 10.04 to 12.04 until 12.04.1 is released.

---

### Post by sentinelace on 2013-01-04
is my best option to do a dist-upgrade?  Are there any issues going to 10.04 and then 12.04?  I am running Qmail 1.03

---

### Post by CharlesA on 2013-01-04
Follow the instructions here to update to 10.04:
[https://help.ubuntu.com/community/LucidUpgrades#Network_Upgrade_for_Ubuntu_Servers_.28Recommended.29-1](https://help.ubuntu.com/community/LucidUpgrades#Network_Upgrade_for_Ubuntu_Servers_.28Recommended.29-1)

The same procedure should let you upgrade to 12.04 because 12.04.1 was released back in august.

---

### Post by sentinelace on 2013-01-04
I upgraded to 10.04 and everything was fine but when I reboot now something with grub has changed.  /dev/disk/modules cannot be found.  I tried even booting to a different kernel with no luck.

---

### Post by cariboo on 2013-01-04
I'm running 12.04 here, this is the output of:

```
cariboo@willy:/dev/disk$ ls -l
total 0
drwxr-xr-x 2 root root 720 Dec  7 11:24 by-id
drwxr-xr-x 2 root root 320 Dec  7 11:24 by-path
drwxr-xr-x 2 root root 200 Dec  7 11:24 by-uuid
```

no modules directory to be seen.

I did a fresh install btw, as I seem to be upgrading every time a new version comes out. I've vowed to stay with 12.04 until it eol's this time. :-D

---

