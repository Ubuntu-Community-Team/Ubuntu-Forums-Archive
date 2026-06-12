---
title: "Server not giving command prompt"
date: 2011-02-28
forum: Server Platforms
---

### Post by Jefferythewind on 2011-02-28
Hi Everyone,
  I have a pretty fresh install on Ubuntu 10.10 Server, with the LAMP bundle installed.  Anyway, I just restarted the computer after changing the /etc/network/interfaces script to connect via dhcp.  Now when I boot into the server, there is no command prompt and seems to hang there forever, with one blinking cursor in the top left hand corner of the screen.  It will not respond to any input besides ctrl-alt-delete.
  I was able to press control-alt-delete and the computer automatically restarted itself, but it returns to the same state after each reboot.  I booted from the grub menu into recovery mode and made sure the /etc/network/interfaces script was correct, and it is.  Also I don't think an error in this file should cause the computer to not boot into the command prompt. 
  Any help would be greatly appreciated.

---

### Post by dtfinch on 2011-02-28
Did you make any /etc/fstab changes as well? If that was the issue, pressing 's' (skips waiting on missing mount devices) during the blank screen would tell you pretty quickly. If it can't find a device in fstab, mountall can delay bootup for several minutes at a blank screen waiting for it to appear. A long filesystem check can look like a boot hang, but it's gotten rarer unless you a large number of files and ext3.

Otherwise it'd help to see your /etc/network/interfaces and your fstab.

---

### Post by Jefferythewind on 2011-03-01
Hi, 
  Wow thanks for that, actually i did make considerable changes to fstab.  I was mounting 2 windows shares at startup, I feel silly that I didn't think of that.  
  Fortunately it was a very fresh installation with nothing important yet stored on the server, so I completely re-installed the OS already.  I will definitely remember this in the future though.
  thanks for the help!

---

### Post by volkswagner on 2011-03-01
Live CD can be your friend.  In the future, if you know what file needs to be changed you can boot a live Linux CD, edit the file such as comment out your /etc/fstab entries that caused the no boot.

Not sure if you discovered it was /etc/fstab after or before reinstalling.

---

### Post by dtfinch on 2011-03-01
In the future you can use the nobootwait mount option in fstab to make it not wait on certain entries.

---

### Post by Jefferythewind on 2011-03-01
Cool,
  I will look into that nobootwait option, because most likely i will have to mount these windows shares again on this new installation.

- volkswagner  
  Thanks for the advice -> boot from live cd.  That is what I would have had to do if I needed to recover that system.  My problem was that it did not occur to me that mounting (or being unable to mount) those windows shares could have been causing the problem that I saw.  That is why this Ubuntu community is so awesome!

Thanks to all.

---

