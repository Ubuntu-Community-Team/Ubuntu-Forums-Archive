---
title: "Locating space consuming files"
date: 2016-12-12
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2016-12-12
Hi all

Running Ubuntu server 14.04 headless on a home network and have been allerted by PuTTy that space is at a critical low.
> 
Filesystem                      Size  Used Avail Use% Mounted on
udev                            1.6G   12K  1.6G   1% /dev
tmpfs                           326M  8.3M  317M   3% /run
/dev/mapper/ecoserver--vg-root  144G  126G   11G  93% /
none                            4.0K     0  4.0K   0% /sys/fs/cgroup
none                            5.0M     0  5.0M   0% /run/lock
none                            1.6G  4.0K  1.6G   1% /run/shm
none                            100M     0  100M   0% /run/user
/dev/sda1                       236M   42M  182M  19% /boot
/dev/sdb1                       147G  2.3G  137G   2% /media/Drive_D
/dev/sdc1                       1.9T  477G  1.4T  26% /media/Elements
/dev/sdd1                       466G  244G  223G  53% /media/Targa
/dev/sde1                       299G  186G  113G  63% /media/Seagate
[https://dav.box.com/dav](https://dav.box.com/dav)          10G     0   10G   0% /home/chris/box.com
The main drive has little on it as all the media files etc are located on attached desktop drives.

Have deleted old log file files (*.gz), run auto-remove etc, etc but would appreciate guidance as where to look for offending space hogging files?

TIA

---

### Post by Fire_Chief on 2016-12-12
It's fairly quick to do some disk usage scans from the cli. You can start at / and then work your way down one level at a time (for easy reading) to find the offending directory or files.
```
sudo du -ah --max-depth=1 /
```Let's say that the largest space usage is shown at /home. You then repeat the command adjusting the target path as needed.```
sudo du -ah --max-depth=1 /home
```This shouldn't take too long to identify the source of the disk consumption.

Cheers!

---

### Post by SeijiSensei on 2016-12-12
You can start by running:
```

cd /
sudo du -sx -X media *

```
which will report the total size of every top-level directory except /media.

---

### Post by Graham_Willis on 2016-12-12
ChrisRChamberlain, I don't understand what you mean by "The main drive has little on it" as it seems to be 93% full:

> /dev/mapper/ecoserver--vg-root 144G 126G 11G 93% /

Second - if the disk was filled to the full or almost to the full, it sometimes happen that deleting files doesn't refresh the total amount of used space correctly. In this case, I recommend reboot & full fsck (**don't do it when the filesystem's mounted!**).

Third, the command that I'd recommend running as first is (it's possible to craft it even better):

[B]du -sh /* --exclude='/media' 2>/dev/null

[/B]It'll automatically exclude /media from checking how much space's used on it, which will save your time (it doesn't make much sense to checking the space used on a mounted file system as it doesn't contribute to overall space used on the root file system).

BTW, it seems that -x option for du doesn't work correctly in Ubuntu.

SeijiSensei: **sudo du -sx -X media** won't work as media's a directory, at least it doesn't work on my machines. The documentation's actually a little bit unclear on this (in both cases, -X and --exclude, they're speaking about files, but the second works with directories while the first doesn't). However, I'm taking back my words about -x not working, it works correctly. So one simple way to go is: **sudo** **du -shx /* 2>/dev/null. **-x will automatically prevent du from traversing into mounted filesystem (just the space used by a directory as if it was umounted's reported, I think).

---

### Post by ChrisRChamberlain on 2016-12-12
Fire_Chief, SeijiSensei and Graham_Willis

Thanks all for your replies.

Using Fire_Chief's suggestion for each directory, ```
sudo du -ah --max-depth=1 /home
```the output was appended to a file for examination.

One early 'villain' found is in ```
/root/update?host=@&domain=mydomain.com&password=e12345678987654321.999
```the result of a dynamic IP address update at 4K a time adding up to in excess of 25MB.

Would ```
sudo rm /root/update?host*
``` resolve that particular issue?

SeijiSensei - your code errored out as suggested by Graham_Willis

Graham_Willis - what I meant was that initially there was very little on the main drive, the desktop drives doing the heavy lifting.

---

### Post by ChrisRChamberlain on 2016-12-13
Thanks to all who contributed to this thread - mission accomplished.

```
sudo du -ah --max-depth=1 /home
```Provided an individual folder view and ```
du -sh /* --exclude='/media' 2>/dev/null
```gave an overall folder view.

Deleting ```
/root/update?host=@&domain=mydomain.com&password=e12345678987654321.999
```remains unresolved and will become the topic of a new thread.

---

