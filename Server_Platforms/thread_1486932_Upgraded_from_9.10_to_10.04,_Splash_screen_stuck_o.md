---
title: "Upgraded from 9.10 to 10.04, Splash screen stuck on &quot;Press S to Skip or M to manually"
date: 2010-05-18
forum: Server Platforms
---

### Post by elias832 on 2010-05-18
I recently upgraded from 9.10 server to 10.04 server, Splash screen stuck on "Press S to Skip or M to manually mount" every time i reboot server. I run a headless server Acer AH340. It worked perfect before the upgrade.
Any idea what can i do to fix it.

Every time i reboot, i have to manually press S for Ubuntu to load thru, otherwise it says on the loading screen and gives me that option at the top left hand corner.

any help is greatly appreciated. I have tried researching for a solution but couldn't find any.

32bit Ubuntu server.
3 TB harddrives (1 TB - OS installed on, 2TB disk for extra storage)

---

### Post by creamers on 2010-05-18
Once you press edit type in.

sudo gedit /etc/fstab

Something in your fstab is mounting that partition wrong. Look at the top there is format on how to correct it. Also here in a great article on the fstab file. [http://wiki.archlinux.org/index.php/Fstab](http://wiki.archlinux.org/index.php/Fstab)

---

### Post by Deadite81 on 2010-05-18
Hi elias832.

I have the same issue.  I know what's causing it, although I have not fixed it yet because I don't know how off the top of my head and I'm extremely lazy.

First when you get to the splash screen lockup, if you hit ESC instead of S it *should* show you where the hangup is.  Once you hit ESC and see the boot loading info go ahead and hit S and it should show you what it is actually skipping.

Mine is skipping mounting a partition.  You see, it was a FAT32 volume on my internal hdd, but to get the permissions correct I had to manually edit my fstab file.
Well, then I decided to change said partition to ext3.  Then, even though the fstab was reset correctly, Ubuntu wouldn't recognize it.  So I changed it back to FAT32 and made sure that the fstab file read as it did before the whole mess started.  But regardless of what the fstab says the permissions are still altered (i.e. I own the drive, even though the fstab, acording to what I've read, should be auto-mounting the partition as owned by root).

So now Ubuntu refuses to mount the FAT32 partition at boot automatically and makes the system hang until I press "S".  Once I'm in the system the partition mounts (manually) and functions properly.  Go figure.

Hope that maybe points you in the right direction, if it's even understandable :)

---

### Post by elias832 on 2010-05-18
BIG THANKS for both of you.... That was it, I had saved an external hard drive to mount, but never had a problem with it until i upgraded i guess.

I just modified webmin to not automatically mount it. :)

---

### Post by creamers on 2010-05-18
@Deadite81

try this

find your uuid by running ls -l /dev/disk/by-uuid



UUID=******************************* /media/myfat32device fat32 defaults 0 2

---

### Post by Deadite81 on 2010-05-19
Thanks creamers.  The uuid was, of course, wrong.  However, "fat32", in Lucid anyway, needs to be "vfat" or else it won't load (still with the "S" junk).  Otherwise your fstab entry suggestion does revert it the partition back to it's default settings.  Unfortunately, this mounts the partition as root, which, for a single home user is no good.

My final fstab entry to make it mount automatically with user ownership looks like this:
```
UUID=3C18-E4A4 /media/mydrivelabel vfat uid=username,owner,gid=username  0  2

```It should be obvious what to replace with what ("owner" is actually the word "owner" though:)).  There are other ways to do this, and this may not be the best, but it works.  It's would be logical to add the "auto" parameter as well (to tell the system to automatically mount the partition at boot), but strangely inserting "auto", even with the other stuff, made the partition still owned by root.  Why?  Got me.  Maybe its just my system.  Anyway, thanks for the motivation to finally fix this!

Another good fstab tutorial, for future reference, is on this forum [here]("http://ubuntuforums.org/showthread.php?t=283131").

---

