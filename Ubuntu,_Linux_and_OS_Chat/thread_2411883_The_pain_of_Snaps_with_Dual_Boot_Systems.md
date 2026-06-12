---
title: "The pain of Snaps with Dual Boot Systems"
date: 2019-02-05
forum: Ubuntu, Linux and OS Chat
---

### Post by leed-f on 2019-02-05
Hi, I'm looking for some advice on how to cope better with future Ubuntu Releases. I've been using Ubuntu sind approx. 2007 in a dual boot manner with Windows, avoiding booting windows as much as possible. 

The recent releases (17.04, 18.04) started causing larger problems with my setup. I had to struggle with new permission issues on my shared NTFS drives, as for some reason the newer Ubuntu systems only allowed root to write to these. I managed to fix this with some fstab configs. 

But I'm still getting such issues with Software that was installed as Snap. These Snaps do not only lack write permissions to the drives, they do not even have read access. The same goes for Optical drives. 
I recently wanted to use handbrake with a DVD, but could not even read the disc. Needless to say, this programm is pretty useless without access to optical drives. 
Another common problem is, that when my chromium browser wants to save a file, it can only save to my ubuntu home folder, not the other NTFS Harddrives. 

Unfortunately google searches seem to prefer delivering me advice related to old Ubuntu versions, such as 14.04. I have not yet found an easy solution to tacke the access problems of Snaps. I understand they should be sandboxes, but having absolutely no access to my drives isn't helpful. 

How do you handle these issues?

---

### Post by TheFu on 2019-02-05
**+1 - TESTIFY!**

Remove all the snaps and purge the snap daemon from your system, then install the packages using the standard APT package manager.

Today, snaps are packaged with confinement settings that you and I cannot change.  I suppose that is good for great-great-non-technical grandma. It follows the Google-Android idea that file managers shouldn't be allowed to ... er .... manage files.  I agree with you in thinking this is an ignorant setup.

If you still want some constraints what specific programs can do, check out **firejail**.  Local admins have access to the config files for each program under firejail.  You can block all networking, block most access to the OS file system, allow specific access to part of the file system, as you need.  Configs are in /etc/firejail/.   Lots of examples there.

I still wonder why is a calculator in a snap at all?   Why?

Be happy.

---

### Post by oldfred on 2019-02-05
I also remove snaps:

       boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb)

---

### Post by maglin2 on 2019-02-05
Does this help?
[https://docs.snapcraft.io/interface-management/6154](https://docs.snapcraft.io/interface-management/6154)
From what has been said I'm guessing not, but it appears that an interface between removable media and chromium may be feasible
```
[FONT=monospace][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ snap interface removable-media[/COLOR]
name:    removable-media
summary: allows access to mounted removable storage
plugs:
  - chromium
slots:
  - core
[/FONT]
```

---

