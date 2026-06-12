---
title: "Buggy FreeNAS installation, then hangs."
date: 2010-11-20
forum: Server Platforms
---

### Post by j3lz on 2010-11-20
Hey Experts,
Newbie here. ;)

I installed a FreeNAS, and tried to mount it on to my ubuntu server (10.10) using a command similar to this:
**sudo mount -t nfs [freenas ip]:/mnt /var/www/mount**

(of course, I had created /var/www/mount folder beforehand)

When I typed this command, it hanged for a bit, so I cancelled out with Ctrl+C. That's when all the trouble began.
I can cd into /var/www, butI cannot show the list of files ("ls" command), and when I do "df" to see my disks, it also hangs after showing the local drives.

My guesses for the cause of this problem are:
1)FreeNAS shouldn't be nfs?
2)Cancellation of the mount command (if this is the problem, how long should I wait?)

I hope my explanation makes sense.

Is there any way to fix this problem without re-installing my ubuntu server? (such as unmounting the drive, etc. and if it is unmounting the drive, what command should I use?)

Thanks a lot~

---

