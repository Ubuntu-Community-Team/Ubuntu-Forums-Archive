---
title: "Error message when booting = security breach?"
date: 2011-06-15
forum: Security
---

### Post by Camilia on 2011-06-15
When I boot up I get message:
Inode (9) corrupt input/output error. 

Tried booting with previous upgrades and still have the message.

Tried booting with CD but is corrupted, why don't know.

---

### Post by cariboo on 2011-06-15
It looks like there may be a hard drive error, You need to run fsck to fix the problem. If your Live CD doesn't work, you can tell the system to run fsck on reboot. Open a terminal and type:

```
sudo -i
```

next cd into the root directory:

```
cd /
```

Now create a file called forcefsck:

```
touch /forcefsck
```

Now reboot:

```
reboot
```

Your system should run the disk check utility on reboot.

---

### Post by Camilia on 2011-06-17
Well, I found an old Ubuntu CD and it worked. I shall save the info for next time. Now unfortunately can't get Windows OS to work and need to for Netflix.

I am still wondering if it was a virus. For Windows os also became unexcessable.

---

### Post by cariboo on 2011-06-17
Probably not a virus, as the chances of getting a virus on Ubuntu are pretty small. I would suggest a hardware problem, before a virus..

---

