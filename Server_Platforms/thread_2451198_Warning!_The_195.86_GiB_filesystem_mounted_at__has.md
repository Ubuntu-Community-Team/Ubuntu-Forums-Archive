---
title: "Warning! The 195.86 GiB filesystem mounted at / has only 656.12 MiB of free disk spac"
date: 2020-09-29
forum: Server Platforms
---

### Post by Raymond Day on 2020-09-29
About a week ago installed a fresh Ubuntu 20.04.1 Did make a backup of the 2GB SSD stick use as the OS. It was 18.04.3 or something like that. Took me over a day to get it back how it was copied the /etc/fstab and made links how I had them. Restored the database.

When I installed it I said to install some things. I guess one thing was snap. It seems like that was filling up a lot so I removed it. With a apt remove snap command.

Copied and deleted a log file made a link to it were I copied it to a 2TB hard drive.

On the old 18 I had like 80% free space on the boot 2TB SSD.

Here is some commands I did to try and find out what is using the space.

```
root@rayday:~# du -h --max-depth=1 /
2.9M    /run
2.7G    /usr
4.0K    /dev
0       /sys
110M    /boot
40T     /media
du: cannot access '/proc/5228/task/5228/fd/4': No such file or directory
du: cannot access '/proc/5228/task/5228/fdinfo/4': No such file or directory
du: cannot access '/proc/5228/fd/3': No such file or directory
du: cannot access '/proc/5228/fdinfo/3': No such file or directory
0       /proc
4.0K    /srv
11M     /etc
16K     /lost+found
4.0K    /opt
4.0K    /mnt
4.0K    /cdrom
20G     /var
60K     /tmp
40T     /
root@rayday:~# du -h --max-depth=1 /var
4.0K    /var/local
211M    /var/cache
18M     /var/webmin
1.7G    /var/log
20K     /var/www
344K    /var/crash
18G     /var/lib
4.0K    /var/mail
9.9M    /var/spool
2.0M    /var/backups
4.0K    /var/opt
36K     /var/tmp
20G     /var
root@rayday:~# du -h --max-depth=1 /var/log
792K    /var/log/installer
8.0K    /var/log/dbconfig-common
4.0K    /var/log/dist-upgrade
268K    /var/log/apt
20K     /var/log/letsencrypt
32K     /var/log/unattended-upgrades
4.0K    /var/log/private
28K     /var/log/mysql
3.7M    /var/log/samba
4.0K    /var/log/landscape
152K    /var/log/squeezeboxserver
628K    /var/log/apache2
1.6G    /var/log/journal
1.7G    /var/log
root@rayday:~# du -h --max-depth=1 /var/lib
4.0K    /var/lib/boltd
4.0K    /var/lib/plymouth
428K    /var/lib/phpmyadmin
8.0K    /var/lib/sudo
276K    /var/lib/cloud
20K     /var/lib/alsa
40K     /var/lib/polkit-1
504K    /var/lib/fwupd
4.0K    /var/lib/mysql-upgrade
36K     /var/lib/PackageKit
12K     /var/lib/AccountsService
17G     /var/lib/plexmediaserver
96M     /var/lib/apt
4.0K    /var/lib/dbus
32K     /var/lib/letsencrypt
608K    /var/lib/usbutils
4.0K    /var/lib/unattended-upgrades
4.0K    /var/lib/mysql-keyring
4.0K    /var/lib/private
4.0K    /var/lib/mysql-files
8.0K    /var/lib/vim
512K    /var/lib/systemd
28K     /var/lib/pam
651M    /var/lib/mysql
8.0K    /var/lib/shim-signed
2.2M    /var/lib/samba
3.0M    /var/lib/command-not-found
36K     /var/lib/php
4.0K    /var/lib/landscape
39M     /var/lib/dpkg
4.0K    /var/lib/misc
284K    /var/lib/ucf
4.0K    /var/lib/ubuntu-release-upgrader
4.0K    /var/lib/ubuntu-advantage
4.0K    /var/lib/python
12K     /var/lib/postfix
4.0K    /var/lib/tpm
4.0K    /var/lib/dhcp
16K     /var/lib/grub
4.0K    /var/lib/git
169M    /var/lib/squeezeboxserver
20K     /var/lib/update-notifier
36K     /var/lib/apache2
8.0K    /var/lib/os-prober
91M     /var/lib/mecab
8.0K    /var/lib/logrotate
4.0K    /var/lib/man-db
8.0K    /var/lib/initramfs-tools
12K     /var/lib/update-manager
18G     /var/lib
root@rayday:~#
```

Got allmost 700 MiB free after a long time trying to make room. At lest the Database works again now. Because it did not there was 0 space left on filesystem.

What else can I do to show what it using all the space?

-Raymond Day

---

### Post by agvantibo on 2020-09-29
This one may help
1. wget [https://raw.githubusercontent.com/jabarihunt/Ubuntu-Cleanup-Script/master/clean.sh]("https://github.com/jabarihunt/Ubuntu-Cleanup-Script/blob/master/clean.sh")
2. nano clean.sh (remove what you wouldn't want)
3. bash clean.sh
4. ???????
5. Profit!

---

### Post by Raymond Day on 2020-09-29
I did this:

```
root@rayday:~# wget https://raw.githubusercontent.com/jabarihunt/Ubuntu-Cleanup-Script/master/clean.sh
--2020-09-29 09:26:12--  https://raw.githubusercontent.com/jabarihunt/Ubuntu-Cleanup-Script/master/clean.sh
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 199.232.76.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|199.232.76.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1200 (1.2K) [text/plain]
Saving to: ‘clean.sh.2’

clean.sh.2                       100%[=======================================================>]   1.17K  --.-KB/s    in 0s

2020-09-29 09:26:13 (29.1 MB/s) - ‘clean.sh.2’ saved [1200/1200]

root@rayday:~#
```

The file at clean.sh looks like this:

```
#!/bin/bash
###############################################################################
# This script removes unneeded files and libraries, including log files and snaps.
# I originally created it to combat the /var directory filling up (when on a
# seperate partition). I know there is redundency with apt vs apt-get commands,
# but I alsways seem to have more drive space after running both!
#
# I created this for Ubuntu 18.04 (Desktop), but it should run on other distros
# based on Ubuntu without issue.
#
# To run this script from anywhere, place it in your /usr/local/bin directory
#
# To list your partition sizes run: df -Th | sort
###############################################################################

# Remove apt / apt-get files
sudo apt clean
sudo apt -s clean
sudo apt clean all
sudo apt autoremove
sudo apt-get clean
sudo apt-get -s clean
sudo apt-get clean all
sudo apt-get autoclean

#Remove Old Log Files
sudo rm -f /var/log/*gz

# Remove Thumbnail Cache
rm -rf ~/.cache/thumbnails/*

# Remove old snaps
set -eu
snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
        sudo snap remove "$snapname" --revision="$revision"
    done
```

How do I edit that?

Then the next command you said to do looked like this:

```
root@rayday:~#  bash clean.sh
Del /var/cache/apt/archives/* /var/cache/apt/archives/partial/*
Del /var/lib/apt/lists/partial/*
Del /var/cache/apt/pkgcache.bin /var/cache/apt/srcpkgcache.bin
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Del /var/cache/apt/archives/* /var/cache/apt/archives/partial/*
Del /var/lib/apt/lists/partial/*
Del /var/cache/apt/pkgcache.bin /var/cache/apt/srcpkgcache.bin
Reading package lists... Done
Building dependency tree
Reading state information... Done
clean.sh: line 34: snap: command not found
root@rayday:~#
```

Then this code still says 100% full:

```
root@rayday:~# df -h /
Filesystem                         Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv  196G  186G  656M 100% /
root@rayday:~#
```

-Raymond Day

---

### Post by Raymond Day on 2020-09-29
I looked at that file and made one like it said in /usr/local/bin/ named it drive-full.sh chmod 755 on it and this is how it looked:

```
root@rayday:~# /usr/local/bin/drive-full.sh
Del /var/cache/apt/archives/* /var/cache/apt/archives/partial/*
Del /var/lib/apt/lists/partial/*
Del /var/cache/apt/pkgcache.bin /var/cache/apt/srcpkgcache.bin
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Del /var/cache/apt/archives/* /var/cache/apt/archives/partial/*
Del /var/lib/apt/lists/partial/*
Del /var/cache/apt/pkgcache.bin /var/cache/apt/srcpkgcache.bin
Reading package lists... Done
Building dependency tree
Reading state information... Done
/usr/local/bin/drive-full.sh: line 19: snap: command not found
root@rayday:~# df -Th | sort
/dev/mapper/ubuntu--vg-ubuntu--lv ext4      196G  186G  656M 100% /
/dev/sda1                         ext4      916G  427G  443G  50% /media/WD-3D-NAND-Stick
/dev/sdb1                         vfat      511M  7.8M  504M   2% /boot/efi
/dev/sdb2                         ext4      976M  104M  805M  12% /boot
/dev/sdc1                         ext4       11T  6.2T  4.2T  60% /media/12TB_replace_5
/dev/sdd1                         ext4       11T  7.0T  3.4T  68% /media/12TB-backup
/dev/sde2                         ext4      1.8T  134G  1.6T   8% /media/3TB-Black-laptop-size
/dev/sdf1                         ext4      2.7T  1.9T  694G  74% /media/3TB_USB
/dev/sdg1                         ext4      458G  121G  314G  28% /media/500GB-blue-ssd
/dev/sdh1                         ext4      458G  5.3G  429G   2% /media/500GB-3D-NAND
/dev/sdi1                         ext4      916G  860G  9.9G  99% /media/WD-1TB
/dev/sdj1                         ext4      9.1T  6.1T  2.6T  71% /media/WD-10TB-2
/dev/sdk1                         ext4      9.1T  6.2T  2.5T  72% /media/WD-10TB-3
/dev/sdl1                         ext4      9.1T  5.6T  3.0T  66% /media/WD-10TB
/dev/sdm1                         ext4      9.1T  5.7T  3.0T  66% /media/WD-10TB-4
Filesystem                        Type      Size  Used Avail Use% Mounted on
tmpfs                             tmpfs      16G     0   16G   0% /sys/fs/cgroup
tmpfs                             tmpfs      16G  4.0K   16G   1% /dev/shm
tmpfs                             tmpfs     3.2G     0  3.2G   0% /run/user/0
tmpfs                             tmpfs     3.2G  2.9M  3.2G   1% /run
tmpfs                             tmpfs     5.0M  4.0K  5.0M   1% /run/lock
udev                              devtmpfs   16G     0   16G   0% /dev
root@rayday:~#
```

Seems like it made a little more room but on my webmin info the top still says this:

**Warning! The 195.86 GiB filesystem mounted at / has only 655.66 MiB of free disk space**

I could boot a desktop Ubuntu 20.04 from a USB stick. I think there is a way to show it in a pie type graph then and maybe that will help not sure.

Wow maybe I should just install this fresh again and not fill any checks to install other things. I think I did 3 more things when I installed it about a week ago now. My old one just would not upgrade over itself. 

-Raymond Day

---

### Post by ahbart on 2020-09-29
what does sudo df -h report?
edit. Oh sorry, you already did.

---

### Post by darkod on 2020-09-29
You seem to have 40TB in /media. Is there a way to stop the process using that data and unmount the disks/share you have there?

The point is you need to unmount that disk and take a look at the media folder on /.

If something continued to write data in /media while you didn't have the disk mounted there, it would write in the folder media in /, thus filling up space in / which is not what you expect.

The rest of the du -h command looks good. I would focus on /media, it's the only path with huge amount of data.

---

### Post by darkod on 2020-09-29
PS. I just noticed in your post #4. You have way too many HDDs to make this manageable. You need to reconsider how you attach and use storage on your server.

If only one of those disks fails to mount at /media then your apps will start filling up your root volume. It's as simple as that, and I think that might be what happened.

---

### Post by Raymond Day on 2020-09-29
I got a lot of drives on USB 3.0 on it. Have Plex server on it and a lot of videos. Music too.

Have it set up the same way about when I had Ubuntu 18 server and like I said it only used about 20% of the 2GB space on the boot SSD. I had that SSD for over a year I think and it worked like that.

It did have swap.img on the root folder and I have a swap partition on a drive and it put that in /etc/fstab like this:

```
#/swap.img	none	swap	sw	0	0
UUID=5f09c29a-1209-481b-bb8c-c36f37413f72	swap			swap	sw,pri=-1	0	0
```

Deleted the swap.img because that took up all the space on the 2TB SSD.

Then the next day it filled it up with something else that I don't know what.

All them same hard drives I had on Ubuntu server 18.04 and it never filled up the boot SSD. I got them mounted the same and I know because all is working the same as it did. But don't know why it's filling up the boot SSD.

-Raymond Day

---

### Post by Raymond Day on 2020-09-29
The new 20.04 server made a OS looks like on:

```
/dev/mapper/ubuntu--vg-ubuntu--lv ext4
```

That is what is full. On 18.04 I know it was not mounted in this way.

-Raymond Day

---

### Post by Raymond Day on 2020-09-29
This my show more info to help:

```
root@rayday:~# lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                         8:0    0 931.5G  0 disk
&#9492;&#9472;sda1                      8:1    0 931.5G  0 part /media/WD-3D-NAND-Stick
sdb                         8:16   0   1.8T  0 disk
&#9500;&#9472;sdb1                      8:17   0   512M  0 part /boot/efi
&#9500;&#9472;sdb2                      8:18   0     1G  0 part /boot
&#9492;&#9472;sdb3                      8:19   0   1.8T  0 part
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0   200G  0 lvm  /
sdc                         8:32   0  10.9T  0 disk
&#9492;&#9472;sdc1                      8:33   0  10.9T  0 part /media/12TB_replace_5
sdd                         8:48   0  10.9T  0 disk
&#9492;&#9472;sdd1                      8:49   0  10.9T  0 part /media/12TB-backup
sde                         8:64   0   2.7T  0 disk
&#9500;&#9472;sde1                      8:65   0   512M  0 part
&#9492;&#9472;sde2                      8:66   0   1.8T  0 part /media/3TB-Black-laptop-size
sdf                         8:80   0   2.7T  0 disk
&#9492;&#9472;sdf1                      8:81   0   2.7T  0 part /media/3TB_USB
sdg                         8:96   0 465.8G  0 disk
&#9492;&#9472;sdg1                      8:97   0 465.8G  0 part /media/500GB-blue-ssd
sdh                         8:112  0 465.8G  0 disk
&#9492;&#9472;sdh1                      8:113  0 465.8G  0 part /media/500GB-3D-NAND
sdi                         8:128  0 931.5G  0 disk
&#9492;&#9472;sdi1                      8:129  0 931.5G  0 part /media/WD-1TB
sdj                         8:144  0   9.1T  0 disk
&#9492;&#9472;sdj1                      8:145  0   9.1T  0 part /media/WD-10TB-2
sdk                         8:160  0   9.1T  0 disk
&#9492;&#9472;sdk1                      8:161  0   9.1T  0 part /media/WD-10TB-3
sdl                         8:176  0   9.1T  0 disk
&#9492;&#9472;sdl1                      8:177  0   9.1T  0 part /media/WD-10TB
sdm                         8:192  0   9.1T  0 disk
&#9492;&#9472;sdm1                      8:193  0   9.1T  0 part /media/WD-10TB-4
root@rayday:~#
```

-Raymond Day

---

### Post by ahbart on 2020-09-29
The problem is probably as Darkod said:
You have mounted these drives on /media 
If for one reason one off these drives is not mounted, but you are not aware of that, and you where writing to this 'disk', then you are writing to /media/disk folder in /media and not as expected to the mounted drive.
If you mount the drive later, this folder /media/disk with files is hidden behind the mounted drive. 
You can check that by unmounting these drives and check these folders.

---

### Post by oldfred on 2020-09-29
As Darko mentioned if your media drive files, you may get data written into / at /media.
> /dev/sdi1                         ext4      916G  860G  9.9G  [COLOR=#ff0000]99%[/COLOR] /media/WD-1TB

You need to make sure drives are not too full.

---

### Post by TheFu on 2020-09-29
USB3 connections are prone to failure from a number of issues.  I use autofs for USB storage, since I don't want it mounted until needed. I only use USB storage for temporary needs.  Important files are on sata, esata or infiniband connected storage.  The eSATA connections are the least trusted in that list.

Would love to understand your backup techniques for all this storage.

As for storage management on a file system on my plex server, I limit all LVs to 4G or less because that's the max size my backup storage can handle. My backups are at the file system level.  For media, 
```

ionice rsync -av --stats --progress $EXCLUDES --delete /d/D1/ /d/b-D3/
ionice rsync -av --stats --progress $EXCLUDES --delete /d/D2/ /d/b-D4/
ionice rsync -av --stats --progress $EXCLUDES --delete /d/D3/ /d/b-D5/
```
None media files get real, daily, automatic, versioned, backups. It is just the media that gets the rsync treatment. I don't use RAID for media storage. Long ago, I did, but found it wasn't worth the hassles.  Plus, if /d/D2/ storage dies, it only takes 15 seconds to mount /d/b-D4/ on the other location.

Plex likes to store stuff in /var/lib/...... .... .... .... .... ..... .... ... ....  so that gets a separate LV. It is all about having clean backups.

When I need to find what is using storage, I look for huge files first. 
```
find . -type f -size +3G -exec ls -lh {} \; 
```

Of course, there can be thousands of smaller files that won't be found with that too, so something like **ncdu** is handy to have around. I tend to use **du -sh *|sort -rh** and work my way down from / to directories where I don't expect to find stuff. ncdu can make that easier, but it is slow since it is doing the same command that I use manually.

/dev/mapper/ubuntu--vg-ubuntu--lv just means that you chose to use LVM during the install.  That's a good thing if you understand LVM, but can be confusing if you don't.  LVM is a professional volume management tool with lots of nice capabilities and a few dangerous capabilities when used improperly.  Long ago, I lost 80% of my data because I didn't pay attention to one of the most important rules for LVM. Don't span file systems across multiple disks without having 100% perfect backups.

---

### Post by ajgreeny on 2020-09-29
I used to run a plexmediaserver but my /var/lib/plexmediaserver folder never went above about 4G; I note yours is 18G so you must have an absolutely enormous amount of media, presumably in those disks mounted at /media.

Whilst 18G may be relatively little in relation to the total space used for your media, I wonder if you can make any changes to the plexmediaserver settings to save space in any way.  I haven't used plex for some time now having replaced it with emby-mediaserver, so I can't remember much about its settings but I think I remember making changes after I found lots of unnecessary space being used by cached files of some sort.

Worth investigating I think.

---

### Post by darkod on 2020-09-29
With all of the above being said, I repeat again:

1). Stop the plexmediaserver service.
2). Unmount all HDDs from /media.
3). Go into /media and check its content. It looks fairly certain you will find data you don't expect there. Because it serves only as mount point, it should be empty. If it has around 170-180GB of data, then that is where your issue is.

I base this on your results of df for the root volume. I can only see signficant size of the /var folder with 20GB. While that is big size, it is still only 10% of 200GB volume so I would worry about that later. Like ajgreeny said you can investigate how to optimize the plex library.

Your immediate problem is root being 99% full, so leave cleaning up /var for later. The only other significant size in your df output is the 40TB in /media. With the HDDs mounted you can't really tell between data on them and in the local folder. But unmounting the disks will show you the size of the local folder only. I repeat again, it should be zero because it should serve only as mount point.

---

### Post by TheFu on 2020-09-29
When you post du output, please run it through sort too.

```
sudo du -sh /var/* | sort -h
```
No need to worry about directories that aren't huge.

---

### Post by Raymond Day on 2020-09-29
/dev/mapper/ubuntu--vg-ubuntu--lv just means that you chose to use LVM during the install.  That's a good thing if you understand LVM, but can be confusing if you don't.  LVM is a professional volume management tool with lots of nice capabilities and a few dangerous capabilities when used improperly.  Long ago, I lost 80% of my data because I didn't pay attention to one of the most important rules for LVM. Don't span file systems across multiple disks without having 100% perfect backups.[/QUOTE]

Wow I was thinking of adding a 128GB USB flash drive to the LVM boot to make more room. I guess that would be bad ha? I know LVM can add other drives to look like one drive.

-Raymond Day

---

### Post by Raymond Day on 2020-09-29
> **TheFu said:**
> When you post du output, please run it through sort too.

```
sudo du -sh /var/* | sort -h
```
No need to worry about directories that aren't huge.

```
root@rayday:~# du -sh /var/* | sort -h
0       /var/lock
0       /var/run
4.0K    /var/local
4.0K    /var/mail
4.0K    /var/opt
20K     /var/www
36K     /var/tmp
344K    /var/crash
2.1M    /var/backups
12M     /var/spool
18M     /var/webmin
49M     /var/log
97M     /var/cache
18G     /var/lib
root@rayday:~#
```

I guess all that adds up to about 2GB. Hard to know what the OS is not using or things I installed.

I don't use /var/www I have a link in Apache to **Document Root /media/USBdisk2-3TB/var/www** The /var/www is just the default install. Guess I can delete that folder.

-Raymond Day

---

### Post by Raymond Day on 2020-09-29
Did the same command you said but on the /var/lib folder that seems like it's the biggest:

```
root@rayday:~# du -sh /var/lib/* | sort -h
4.0K    /var/lib/boltd
4.0K    /var/lib/dbus
4.0K    /var/lib/dhcp
4.0K    /var/lib/git
4.0K    /var/lib/landscape
4.0K    /var/lib/man-db
4.0K    /var/lib/misc
4.0K    /var/lib/mysql-files
4.0K    /var/lib/mysql-keyring
4.0K    /var/lib/mysql-upgrade
4.0K    /var/lib/plymouth
4.0K    /var/lib/private
4.0K    /var/lib/python
4.0K    /var/lib/tpm
4.0K    /var/lib/ubuntu-advantage
4.0K    /var/lib/ubuntu-release-upgrader
4.0K    /var/lib/unattended-upgrades
8.0K    /var/lib/initramfs-tools
8.0K    /var/lib/logrotate
8.0K    /var/lib/os-prober
8.0K    /var/lib/shim-signed
8.0K    /var/lib/sudo
8.0K    /var/lib/vim
12K     /var/lib/AccountsService
12K     /var/lib/update-manager
16K     /var/lib/grub
20K     /var/lib/alsa
20K     /var/lib/postfix
20K     /var/lib/update-notifier
28K     /var/lib/pam
32K     /var/lib/letsencrypt
36K     /var/lib/PackageKit
36K     /var/lib/apache2
36K     /var/lib/php
40K     /var/lib/polkit-1
276K    /var/lib/cloud
284K    /var/lib/ucf
428K    /var/lib/phpmyadmin
504K    /var/lib/fwupd
512K    /var/lib/systemd
608K    /var/lib/usbutils
2.2M    /var/lib/samba
3.0M    /var/lib/command-not-found
40M     /var/lib/dpkg
91M     /var/lib/mecab
96M     /var/lib/apt
167M    /var/lib/squeezeboxserver
668M    /var/lib/mysql
17G     /var/lib/plexmediaserver
root@rayday:~#
```

Looks like it my be plexmediaserver. I don't know why it did not fill that up on my old load. plexmediaserver was the last thing I got to work on this new load.

-Raymond Day

---

### Post by Raymond Day on 2020-09-29
Checked on my backup and the /var/lib/plexmediaserver was 16GB so not sure if that's it.

My just reload this again fresh.

-Raymond Day

---

### Post by Raymond Day on 2020-09-29
Copied the plexmediaserver with this command:

```
rsync -avP /var/lib/plexmediaserver/ /media/3TB-Black-laptop-size/plexmediaserver

```
Then deleted it with ```
rm -rf /var/lib/plexmediaserver
```

Made a link to the new place **/media/3TB-Black-laptop-size/plexmediaserver**

I had to uninstall Plexmediaserver and install it again from the .deb package. It worked then.

But I don't think that is what was taking up the room.

Webmin still shows this:

**Warning! The 195.86 GiB filesystem mounted at / has only 653.51 MiB of free disk space**

Only getting a little space deleting things.

Thinking more of just reload this fresh. Takes about a day to get it all set up like it was.

Plex is "Refreshing guide data: Initializing" I guess it was doing that when the boot SSD ran out of space.

-Raymond Day

---

### Post by TheFu on 2020-09-29
post #15 above is likely correct.     do that.  The space being used is probably hidden underneath a mount.

The point of the du|sort is so you don't waste lines with unimportant data here. No need to clutter posts.

I run plex.  There are settings to reduce the storage of extra data in /var/lib/ .. but 18G isn't much for all "optimized" media, posters, and other imgs created for pretty ffwd and rev feedback.

---

### Post by agvantibo on 2020-09-30
> **Raymond Day said:**
> 
How do I edit that?
-Raymond Day
Use a file editor, preferrably nano because of its simplicity.
Just enter ```
nano <filename>
```, then you edit it, then press Ctrl+S Ctrl+X to exit, and you're good. You should probably remove all the snap lines too. 
If it errors out with command not found, do apt install nano, that will fix it. Also, try moving /home to an external disk and editing FStab to mount it at boot

---

### Post by TheFu on 2020-09-30
The safest way to edit all system files is with **sudoedit**. There are multiple reasons for this fact.  You can chose any editor you like to be used. On Ubuntu, nano is probably the default, pre-selected, editor.  But if you want, you can have it use gedit or geany or vim or **any** editor that an end-user might prefer.  Just set the EDITOR environment variable to which ever editor you like. Put it inside the appropriate startup file - often ~/.bashrc:
```
export EDITOR=geany
```
from that point on, when you say **sudoedit /etc/fstab**, it will use geany to safely edit the file.

However, if there isn't a GUI running, then geany or gedit or kate won't work.  On a desktop, that shouldn't be any issue.

People trying to be helpful sometimes forget important details, like when to use sudo and when when not to use sudo. They do this thinking that everyone is using the same setup they use. We see this with people who use VPS a bunch. They don't know that the root account is disabled on Ubuntu, so we don't have root logins. Further, it is against Ubuntu Forums policy to provide the commands to enable the root account. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
For editing system files, sudoedit will handle that for us automatically. When editing personal files, just run the edit you prefer, or get it from the menu or right-click on the file and the EDITOR environment variable should be honored by the file manager to launch the EDITOR command specified.

Sometimes the short answer isn't the best answer for any particular need.

---

### Post by Raymond Day on 2020-09-30
I ended up reinstalling it fresh and it took me about all day to set it up. I still have to set up Plex and **/etc/php/7.4/apache2/php.ini** so I can drag and drop videos in my WordPress. Then that should be it.

Now when I look at the space on the boot drive I have a lot left. This time too when I installed it. I unchecked "Set up this disk as an LVM group" That's how I had it on my old server. Ubuntu 18.

```
root@rayday:~# df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb2       1.8T  3.8G  1.7T   1% /
root@rayday:~#
```

That's more like it 1% used. Or 3.8GB out of 1.8TB It's a 2TB SSD or M.2 stick.

Wow this was a hard one never found out what was using all that space.

-Raymond Day

---

### Post by Raymond Day on 2020-09-30
I love nano it is so easy to edit files.

---

