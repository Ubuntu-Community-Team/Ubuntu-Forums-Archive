---
title: "Lock PC with flash drive"
date: 2010-11-06
forum: Security
---

### Post by largent2005 on 2010-11-06
Is there a program like BlueProximity but works with a file on a flash drive which will lock up the computer if it does not detect a file on a flash drive.  What I am wanting to do is make certain features inaccessible if the flash drive is removed so if anyone uses my computer they can't hurt anything.

---

### Post by thegodfaza on 2010-11-07
You (or someone good with bash) could probably write a script that could look for a file (and it's hash / contents) on a device and if it's not present, log you off / lock the computer. A problem could arise if the device storing the file is destroyed / damaged as the computer would be unusable if you really go crazy with the script (disable tty logins, etc).

---

