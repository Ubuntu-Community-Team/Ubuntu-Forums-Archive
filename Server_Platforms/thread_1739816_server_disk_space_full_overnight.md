---
title: "server disk space full overnight"
date: 2011-04-26
forum: Server Platforms
---

### Post by scottad on 2011-04-26
I setup a machine to run Ubuntu Server a few weeks ago. This morning I had issues installing updates due to no disk space left. df -ah shows the following.

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              36G   36G   48M 100% /
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
none                     0     0     0   -  /sys/fs/fuse/connections
none                     0     0     0   -  /sys/kernel/debug
none                     0     0     0   -  /sys/kernel/security
none                  497M  224K  496M   1% /dev
none                     0     0     0   -  /dev/pts
none                  501M     0  501M   0% /dev/shm
none                  501M  252K  500M   1% /var/run
none                  501M     0  501M   0% /var/lock
none                  501M     0  501M   0% /lib/init/rw
nfsd                     0     0     0   -  /proc/fs/nfsd

```

I have tried apt-get clean, autoclean, autoremove but only gained a few MB. "du -sk /* | sort -n" shows /root being completely full.

```

0       /initrd.img
0       /initrd.img.old
0       /proc
0       /sys
0       /vmlinuz
0       /vmlinuz.old
4       /cdrom
4       /media
4       /mnt
4       /opt
4       /selinux
4       /tmp
8       /export
16      /lost+found
20      /srv
128     /home
224     /dev
5696    /etc
6236    /bin
6420    /sbin
30172   /boot
150960  /var
227244  /lib
535788  /usr
35634400        /root

```

And ls -l returns the following:

```
total 92
drwxr-xr-x  2 root root  4096 2011-04-26 10:33 bin
drwxr-xr-x  3 root root  4096 2011-04-26 11:11 boot
drwxr-xr-x  2 root root  4096 2011-04-14 10:50 cdrom
drwxr-xr-x 17 root root  3700 2011-04-26 11:16 dev
drwxr-xr-x 85 root root  4096 2011-04-26 11:16 etc
drwxr-xr-x  3 root root  4096 2011-04-18 15:22 export
drwxr-xr-x  6 root root  4096 2011-04-18 16:55 home
lrwxrwxrwx  1 root root    37 2011-04-14 17:38 initrd.img -> boot/initrd.img-2.6.32-30-generic-pae
lrwxrwxrwx  1 root root    37 2011-04-14 10:51 initrd.img.old -> boot/initrd.img-2.6.32-28-generic-pae
drwxr-xr-x 17 root root 12288 2011-04-15 09:38 lib
drwx------  2 root root 16384 2011-04-14 10:46 lost+found
drwxr-xr-x  2 root root  4096 2011-04-14 10:46 media
drwxr-xr-x  2 root root  4096 2011-01-20 15:36 mnt
drwxr-xr-x  2 root root  4096 2011-04-14 10:47 opt
dr-xr-xr-x 92 root root     0 2011-04-26 07:16 proc
drwx------  4 root root  4096 2011-04-26 11:00 root
drwxr-xr-x  2 root root  4096 2011-04-26 10:33 sbin
drwxr-xr-x  2 root root  4096 2009-12-05 16:55 selinux
drwxr-xr-x  4 root root  4096 2011-04-18 17:28 srv
drwxr-xr-x 13 root root     0 2011-04-26 07:16 sys
drwxrwxrwt  2 root root  4096 2011-04-26 11:16 tmp
drwxr-xr-x 10 root root  4096 2011-04-14 10:47 usr
drwxr-xr-x 15 root root  4096 2011-04-15 09:44 var
lrwxrwxrwx  1 root root    34 2011-04-14 17:38 vmlinuz -> boot/vmlinuz-2.6.32-30-generic-pae
lrwxrwxrwx  1 root root    34 2011-04-14 10:51 vmlinuz.old -> boot/vmlinuz-2.6.32-28-generic-pae

```

Nothing seems to add up to the 35GB that now seems to be full. I'm open to any and all suggestions. Let me know if I need to clarify anything more. Thanks in advance for the help.

---

### Post by collisionystm on 2011-04-26
Sounds to me like someone had a bad script run!!! Happend to me.... Reference your crontab entries, and check the directories.

I would also, cd /home
and run
```

du -chs

```
to check how big the directory is

do the same for other shared directories.

---

### Post by nebileix on 2011-04-26
or u can use this command at /

```
sudo du -h --max-depth=1
```

---

### Post by thinmintaddict on 2011-04-27
I had this happen to me recently. In my case it was a couple daemons not limiting their log file size. check the size of /var/log, and see if you can free up your space there.

---

### Post by brettg on 2011-04-27
OK, sometimes a process will zombie and leave any files it had open "hanging" they don't show up with du but they do with df. I've had apache do this. If the server is not mission critical you can try restarting it. Alternatively, restart processes such as apache. Bu restarting them they will free up any stale handles they have open.

Another thing I have seen is if you run a script in cron that writes files to a mounted drive (such as a backup to an external disk) If for whatever reason the drive was not mounted when the script was run it will simply copy the files into the mountpoint until the drive fills up. If you then mount that drive again later on, du will not be able to see the files that are now "hidden" under the mounted drive. Unmount any extra drives and check there are not a lot of files in the (should be empty) mount points

---

### Post by SeijiSensei on 2011-04-27
> 35634400        /root

It's all in root's home directory, /root. Look there.

---

### Post by Vegan on 2011-04-27
I use Webmin and it has an option to make sure all logs are rotated and it gives you choices on the rotation.

My backup script also rotates after spending a lot of effort to make it do what I wanted.

I suggest Webmin as a solution for managing logs that works on my box

---

### Post by Usa_Tony_Cuba on 2011-04-27
To know what is taking up space you can go to each directory and run **du -h**
To know what is taking up i.e > 100 MB, run
```
find / -size +100000k
```

or, "make deep search", you can use:

```
sudo find / -type f -size +100000k -exec ls -lh {} \; | awk '{ print $8 ": " $5 }'
```

You always have the option of logs...

pd:

You can use this script.. named **71529-ubucleaner.sh**

```

#!/bin/bash

OLDCONF=$(dpkg -l|grep "^rc"|awk '{print $2}')
CURKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
LINUXPKG="linux-(image|headers|ubuntu-modules|restricted-modules)"
METALINUXPKG="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"
OLDKERNELS=$(dpkg -l|awk '{print $2}'|grep -E $LINUXPKG |grep -vE $METALINUXPKG|grep -v $CURKERNEL)
YELLOW="\033[1;33m"
RED="\033[0;31m"
ENDCOLOR="\033[0m"

if [ $USER != root ]; then
  echo -e $RED"Error: must be root"
  echo -e $YELLOW"Exiting..."$ENDCOLOR
  exit 0
fi

echo -e $YELLOW"Cleaning apt cache..."$ENDCOLOR
aptitude clean

echo -e $YELLOW"Removing old config files..."$ENDCOLOR
sudo aptitude purge $OLDCONF

echo -e $YELLOW"Removing old kernels..."$ENDCOLOR
sudo aptitude purge $OLDKERNELS

echo -e $YELLOW"Emptying every trashes..."$ENDCOLOR
rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
rm -rf /root/.local/share/Trash/*/** &> /dev/null

echo -e $YELLOW"Script Finished!"$ENDCOLOR

```

Save and run
```

sudo chmod -c 744 /LOCATION OF THE SCRIPT/71529-ubucleaner.sh
sudo ./71529-ubucleaner.sh

```

---

### Post by Onesimus on 2011-04-27
What does 
```

ls -al
```

give ?

---

