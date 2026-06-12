---
title: "ntfs-3g Special Characters - Very Strange"
date: 2009-01-14
forum: Server Platforms
---

### Post by robgolding63 on 2009-01-14
Hi,

I have a really wierd problem here, that I'm not sure I'll get an answer to - but I figure it's worth a try. Here goes...

I have a scheduled backup that runs from a Windows Server 2003 machine, using [Robocopy]("http://en.wikipedia.org/wiki/Robocopy") to mirror my fileserver directory to a Samba share on my Ubuntu server. The Samba share is an external hard drive, formatted with NTFS.

The problem was that I was getting Access Denied errors when robocopy was trying to create directories with special characters (José Gonzales for example). To fix this, I added **iocharset=utf8** to the relevant line in /etc/fstab - so it then read:

```
/dev/sdf1 /mnt/Backup ntfs-3g default,iocharset=utf8 0 0
```

Anyway, the wierd thing is, when I run the scheduled task from the Windows server myself (note that this is running as a seperate user called **backup**) it works fine. When I wait for the task to run itself at 3am, however, I am still getting the Access Denied errors! I simply cannot figure out what is different between me running the task, and it running on its own. When I run the task myself, Windows even runs it under the same conditions as it would be in the middle of the night - so there can't be a difference there.

Since then, I have removed iocharset=utf8 and replaced it with locale=en_GB.UTF-8 to see if that makes a difference (it still works fine when launched manually). When the errors occur, the following is logged over and over in the syslog:

```

Jan 14 03:00:53 vhost ntfs-3g[4847]: Skipping unrepresentable filename (inode 48167): Invalid or incomplete multibyte or wide character

```

Worth noting is that I have a script that unmounts the backup drive and turns it off after all the backups have finished, and then turns it on and mounts it again before they are due to start at night - but I don't see how this could be causing the issues. The script is as follows:

backup_online:
```

#!/bin/sh
sdparm --command=start /dev/disk/by-uuid/7886AF3D86AEFAB0
sleep 5
mount /mnt/Backup
sleep 2

```

backup_offline:
```

#!/bin/sh
umount /mnt/Backup
sleep 4
sdparm --command=stop /dev/disk/by-uuid/7886AF3D86AEFAB0

```
I'd be grateful for any input or suggestions at all!

Thanks,

Rob

---

### Post by robgolding63 on 2009-01-14
If there's no one with the answer to the problem does anyone know where I might start to look or ask in order to get closer to a solution? I'm thinking maybe just format the backup drive in ext3 - but how is the Windows driver for accessing ext filesystems - I know it exists 3rd party, but is it any good?

Rob

---

