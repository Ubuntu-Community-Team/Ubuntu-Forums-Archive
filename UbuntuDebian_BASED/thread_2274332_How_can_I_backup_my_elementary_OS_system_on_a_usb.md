---
title: "How can I backup my elementary OS system on a usb?"
date: 2015-04-19
forum: Ubuntu/Debian BASED
---

### Post by dalvacoder on 2015-04-19
I just installed elementary os alongside my ubuntu install and, unlike ubuntu, it doesn't offer a native backup solution.  I want to be able to make a backup so if I ever need to reinstall elementary I can just restore from my backup on my usb drive and have all my programs/settings in place. Is this possible?

Also, I already did a backup for ubuntu, if i restore in the future from that backup, will i have my programs and settings installed?  Thanks in advance for the help! :)

---

### Post by TheFu on 2015-04-19
There are many ways to accomplish this even on Ubuntu.  The "native backup solution" is just a regular program.  You can install it and use it in elementaryOS if you like it.

Or you can install and use one of the other 20+ programs that make backups - however, many of those will not work with FAT or NTFS storage so be aware if that is your backup storage file system option.

You can make image-based backups or you can make file-based backups. Each has pros/cons of which to be aware.  Whatever you do, it really isn't good to use something like tar for system backups - that is left over from the 1980s - there are many, better options today than ZIP, TAR, dump, or even rsync.

A few guides:
[http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/?PageSpeed=noscript](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/?PageSpeed=noscript)
[https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto)

I prefer rdiff-backup, but it doesn't have a GUI, though not having a GUI is good for automation through cron.

---

