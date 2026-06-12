---
title: "ramdisk question"
date: 2011-09-17
forum: Server Platforms
---

### Post by tckotb on 2011-09-17
Is there a simple and safe way to:
-mount a ramdisk at boot
-copy over files from a folder on a hard drive to the ramdisk
-execute a shell script on the ramdisk

then upon shutdown recopy the ramdisk back to the hard drive

---

### Post by tgalati4 on 2011-09-17
I run firefox from a ramdisk using these scripts:

tmpfs_firefox.sh:
----------------

#!/bin/bash
# Created 31 Jul 09
# Change this to match your correct profile--firefox's cache directory
PROFILE="4n0pfp5v.default"

cd "${HOME}/.mozilla/firefox"

if test -z "$(mount | grep -F "${HOME}/.mozilla/firefox/${PROFILE}" )"
then
    mount "${HOME}/.mozilla/firefox/${PROFILE}"
fi

if test -f "${PROFILE}/.unpacked"
then
    rsync -av --delete --exclude .unpacked ./"$PROFILE"/ ./profile/
else
    rsync -av ./profile/ ./"$PROFILE"/
    touch "${PROFILE}/.unpacked"
fi

exit

--------------------

Put this in your /etc/fstab:


# Added 31 Jul 09 to improve firefox speed using ramdisk
firefox /home/tgalati4/.mozilla/firefox/4n0pfp5v.default tmpfs size=128M,noauto,user,exec,uid=1000,gid=1000 0 0

-----------

This mounts a directory called 4n0pfp5v.default (firefox's cache directory) to a temporary filesystem (RAMdisk) of 128 MB.

-----------

Run firefox using a script that I call firefast located in /usr/local/bin

tgalati4@tpad-Gloria7 ~/Projects/scripts $ cat /usr/local/bin/firefast


#!/bin/bash
# Created 31 Jul 09 to speed up firefox
~/tmpfs_firefox.sh
firefox &
exit

----------------

Check to see if the RAMdisk exists:

tgalati4@tpad-Gloria7 ~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              39G   25G   12G  69% /
tmpfs                 944M     0  944M   0% /lib/init/rw
varrun                944M  388K  944M   1% /var/run
varlock               944M     0  944M   0% /var/lock
udev                  944M  152K  944M   1% /dev
tmpfs                 944M  2.5M  942M   1% /dev/shm
firefox               128M   74M   55M  58% /home/tgalati4/.mozilla/firefox/4n0pfp5v.default

----------------------

An important part:  using cron to resync the disk cache with the RAMdisk every 10 minutes.

crontab -e

# m h  dom mon dow   command
*/10 * * * * $HOME/tmpfs_firefox.sh


So although this does not do specifically what you want, it has worked for me over 2 years.  So you can modify the scripts to do something similar.

---

### Post by papibe on 2011-09-17
Ubuntu by default has a ramdisk mounted on /dev/shm

Check if yours is mounted like this:
```
$ df -Th /dev/shm/
```
The output should be something like this:
```
Filesystem    Type    Size  Used Avail Use% Mounted on
none         tmpfs    2.0G  272K  2.0G   1% /dev/shm

```
Since it's mounted and ready to use, you could start testing your scripts on that partition. 

If you need a custom ramdisk (for example a smaller one), you could create one doing this:
```
mkdir /tmp/myramdisk
sudo mount -t tmpfs -o size=512M tmpfs /tmp/myramdisk/
```
Hope it helps,
Regards.

---

### Post by SlugSlug on 2011-09-22
just as a side note to this I mounted my /tmp in a tmpfs via fstab and experienced random system crashes (complete freeze up)

---

### Post by dabbi2000 on 2011-09-25
since Ubuntu already has the dev/shm, can I then mount /tmp to this target? I don't really see why we need a special tmpfs disk in fstab if Ubuntu has a ramdisk by default?

---

