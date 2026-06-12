---
title: "Backup Script"
date: 2009-08-26
forum: Security
---

### Post by SnarlSlayer on 2009-08-26
Greetings!

I'm looking for a program or script that will do the following:

Mount a drive
Copy my entire home directory to the drive
Unmount the drive

I'd like it to do this every night, but I'm sure I can use cron to schedule that, right? I can probably figure out how to use rsync, but the mounting part is a bit tough for me.

Suggestions?

SS

---

### Post by cdenley on 2009-08-26
```

man mount

```
[https://help.ubuntu.com/community/Mount#line-48](https://help.ubuntu.com/community/Mount#line-48)

---

### Post by Dave_Connor on 2009-08-27
When you plug your drive, the kernel will see the new drive plugged in. What you can do is enter a terminal and enter ```
dmesg/code] and see which letter the kernel assigned it. Example of it being /dev/sdb1. I would mount the drive with [code]sudo mount /dev/sdb1 /(whereyouwantyourdrivetobemounted)
```

The script which you can change can be
```

#!/bin/bash
sudo mount /dev/sdx1 /mountpoint
rsync -v --progress -rpt /home/$USER /mountpoint/backup/home
sudo umount /dev/sdx1

``` 

rsync is MUCH better since it doesn't re-overwrite files so it will be MUCH quicker after the first time copying and only re-writes when a file has changed.

---

### Post by decoherence on 2009-08-27
> **Dave_Connor said:**
> 
```

#!/bin/bash
sudo mount /dev/sdx1 /mountpoint
rsync -v --progress -rpt /home/$USER /mountpoint/backup/home
sudo umount /dev/sdx1

``` 


Just a minor modification to the above

```
rsync -avz /home/$USER /mountpoint/backup/home
```

The "a" flag includes "-rpt" and preserves some other attributes (some of which only apply if you've preface the command with sudo.) The 'z' flag will compress the archive.

note that if the drive you are backing up to is formatted for Windows, rsync may not be able to determine which files have changed and which haven't and thus might back up your entire home whether it needs to or not. There are additional parameters you can give rsync which may or may not fix this.

---

