---
title: "Root HDD being filled up by a mystery!"
date: 2024-09-12
forum: Server Platforms
---

### Post by scottbouch-com on 2024-09-12
Hi all,

(Ubuntu server 22.04 Jammy)

My Ubuntu server has just started to act oddly. I use it for Emby media server, and Zoneminder CCTV, plus Apache and certbot to host some basic websites.

All files associated with these services (such as CCTV recordings, and ,music etc..) are held on other mounted hard disks. The main had disk (in question) with the Ubuntu OS and the applications is quickly and repeatedly filling up to 100%. 

I read some guidance online and performed:

```
apt-get autoremove --purge
```

and

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```


to remove old kernels and packages. This freed up 513 MB.... but 30 minutes later this was down to 94 MB free space!!! You can literally watch the space being consumed by something!!

I don't know what else to delete to watch it fill up again, as it's all system files!

How can I find out what files are being written to, or created?

Many thanks, Scott

---

### Post by Rubi1200 on 2024-09-12
What does this show?
```
du -h / 2>/dev/null | grep '^[0-9]*\.[0-9]G'
```

Please wrap the output with code tags when replying.

---

### Post by oldfred on 2024-09-12
One common issue is an error that is filling log files.

I like to use ncdu over multiple du commans,  which you have to install to view files. If /var then is very large, it is a log file issue.

Review log files, I get a page or two most warning or just entry about an error but not error.
sudo grep -Ei 'warn|error' /var/log/*log
 tail -n 10 /var/log/syslog

---

### Post by scottbouch-com on 2024-09-12
Thanks...

I ran the command suggested by Rubi, but excluded /mnt and /var/www/html as these are mount points for other volumes, including them only lists loads of stuff from non-problematic drives. I didn't try installing ncdu as suggested by oldfred as the root drive is full.

```

$ du -h / 2>/dev/null --exclude=mnt --exclude=var/www/html | grep '^[0-9]*\.[0-9]G'
2.1G    /var/log/zm
4.1G    /var/log/journal/c14637d0633b45b18aa96baad55db587
4.1G    /var/log/journal
5.7G    /var/lib/emby/metadata/library
7.1G    /var/lib/emby/metadata
8.2G    /var/lib/emby
9.6G    /var/lib
1.1G    /usr/lib/firmware
2.5G    /usr/lib
3.4G    /usr
2.5G    /snap

```

Its a little confusing as the HDD is quite big, and the above totals to 50.4 GB.

```

$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL

NAME                      FSTYPE        SIZE MOUNTPOINT         LABEL
....
sda                                   232.9G                    
&#9500;&#9472;sda1                                    1M                    
&#9500;&#9472;sda2                    ext4            1G /boot              
&#9492;&#9472;sda3                    LVM2_member 231.8G                    
  &#9492;&#9472;ubuntu--vg-ubuntu--lv ext4        115.9G / 
....

```



```

$ sudo fdisk -l
....
Disk /dev/sda: 232.85 GiB, 250023444480 bytes, 488327040 sectors
Disk model: LOGICAL VOLUME  
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: FF90F0FD-E1E9-488F-BEB6-948E9F0C4457

Device       Start       End   Sectors   Size Type
/dev/sda1     2048      4095      2048     1M BIOS boot
/dev/sda2     4096   2101247   2097152     1G Linux filesystem
/dev/sda3  2101248 488323071 486221824 231.8G Linux filesystem
....

```

ls from root / location:

```

$ ls -alh
total 8.1G
drwxr-xr-x  20 root root 4.0K Nov  3  2023 .
drwxr-xr-x  20 root root 4.0K Nov  3  2023 ..
lrwxrwxrwx   1 root root    7 Jul 31  2020 bin -> usr/bin
drwxr-xr-x   4 root root 4.0K Sep 12 14:31 boot
drwxr-xr-x   2 root root 4.0K Oct 28  2020 cdrom
-rw-------   1 root root  11M Nov  3  2023 core
drwxr-xr-x  20 root root 4.4K Sep 12 15:16 dev
drwxr-xr-x 123 root root  12K Sep 10 06:57 etc
drwxr-xr-x   5 root root 4.0K Nov  2  2021 home
lrwxrwxrwx   1 root root    7 Jul 31  2020 lib -> usr/lib
lrwxrwxrwx   1 root root    9 Jul 31  2020 lib32 -> usr/lib32
lrwxrwxrwx   1 root root    9 Jul 31  2020 lib64 -> usr/lib64
lrwxrwxrwx   1 root root   10 Jul 31  2020 libx32 -> usr/libx32
drwx------   2 root root  16K Oct 28  2020 lost+found
drwxr-xr-x   2 root root 4.0K Jul 31  2020 media
drwxr-xr-x   7 root root 4.0K Feb  5  2024 mnt
drwxr-xr-x   3 root root 4.0K Nov  3  2023 opt
dr-xr-xr-x 343 root root    0 Sep 12 15:15 proc
drwx------   6 root root 4.0K Sep 12 13:25 root
drwxr-xr-x  32 root root  900 Sep 12 15:49 run
lrwxrwxrwx   1 root root    8 Jul 31  2020 sbin -> usr/sbin
drwxr-xr-x   9 root root 4.0K Oct 29  2020 snap
drwxr-xr-x   3 root root 4.0K Nov 16  2021 srv
-rw-------   1 root root 8.0G Oct 28  2020 swap.img
dr-xr-xr-x  13 root root    0 Sep 12 15:15 sys
drwxrwxrwt  15 root root 4.0K Sep 12 17:09 tmp
drwxr-xr-x  14 root root 4.0K Feb  5  2022 usr
drwxr-xr-x  14 root root 4.0K Oct 28  2020 var

```

There is an 8G swap.img, but still nothing near the problem size.

Are there any clues in the above, or are there any other commands to try?

Daft thing is this server has been working fine for years, then out of nowhere (I hadn't been messing around with it) it starts filling the root HDD up.

---

### Post by oldfred on 2024-09-12
I do not use LVM, but default install typically does not assign volumes to the entire LVM.
It then lets you add swap, /home, data, another / or just expand the one volume you have. Or leaves you some flexiblity.

But that still only shows your volume as 116GB of your 231 available GB. 
Maybe what is in your excluded folders is then the issue?

---

### Post by TheFu on 2024-09-12
230G is not "quite big" by standards for today.  14TB is.  8TB is "average".

Anyway, looks like your zm logs haven't been properly managed.  You should fix that using **logrotate**.   BTW, since I don't use either emby or ZM, I don't know what is "reasonable" for those logs.  There's little reason to allow any individual logs over 10MB and all historical logs to be over 200MB in a home environment. It isn't like you or anyone else will be reading them.  logrotate will let you setup automatic log rotation based on the size or specific times.  There are tutorials online for configuring logrotate. It is a very mature tool, so I'd be surprised if google didn't find a 15 line config file for zm that will get you started - now, today, in 30 seconds.  [https://github.com/ZoneMinder/zoneminder/blob/master/misc/logrotate.conf.in](https://github.com/ZoneMinder/zoneminder/blob/master/misc/logrotate.conf.in) shows an example logrotate conf file for zoneminder, so you probably already have it on your system.  Looking at it, there's no time-based rotation or size limit. Booooo.  That sorta defeats the point, if you ask me.  I guess they can put the ZM log data into syslog or into separate ZM-specific files.  Depends on what you did, I suppose.

As for emby, I use jellyfin.  Jellyfin logs are in 
```
$ ls -l /var/log/jellyfin/
total 61740
-rw-r--r-- 1 jellyfin jellyfin     6952 Sep 12 11:13 FFmpeg.DirectStream-2024-09-12_11-13-21_4092ad420d06a9b67fa043b8449c3167_05240223.log
-rw-r--r-- 1 jellyfin jellyfin    15196 Sep  9 14:02 FFmpeg.Transcode-2024-09-09_14-02-54_16747cd149cfad60fa0680ddbd222d7a_861b9e8f.log
-rw-r--r-- 1 jellyfin jellyfin    58716 Sep  9 14:07 FFmpeg.Transcode-2024-09-09_14-06-37_0b4f708b0c122ef5802b40d143cb1697_0ffb4e9d.log
-rw-r--r-- 1 jellyfin jellyfin    20752 Sep  9 14:15 FFmpeg.Transcode-2024-09-09_14-15-47_7485a6b1a35a43b6a756c8ada85e2beb_92643988.log
-rw-r--r-- 1 jellyfin jellyfin    19534 Sep  9 14:16 FFmpeg.Transcode-2024-09-09_14-15-56_7485a6b1a35a43b6a756c8ada85e2beb_cb5d3ed6.log
-rw-r--r-- 1 jellyfin jellyfin    17025 Sep  9 14:16 FFmpeg.Transcode-2024-09-09_14-16-04_7485a6b1a35a43b6a756c8ada85e2beb_ddc616e2.log
-rw-r--r-- 1 jellyfin jellyfin     7374 Sep 12 11:13 FFmpeg.Transcode-2024-09-12_11-13-21_4092ad420d06a9b67fa043b8449c3167_00e13579.log
-rw-r--r-- 1 jellyfin jellyfin     7374 Sep 12 11:13 FFmpeg.Transcode-2024-09-12_11-13-21_4092ad420d06a9b67fa043b8449c3167_2509a323.log
-rw-r--r-- 1 jellyfin jellyfin    19050 Sep 12 11:15 FFmpeg.Transcode-2024-09-12_11-15-10_89f449b15f3a5d2f2637be5795a637b3_06908d8c.log
-rw-r--r-- 1 jellyfin jellyfin    42165 Sep 12 11:24 FFmpeg.Transcode-2024-09-12_11-24-25_10d1ba56f8a8efcfd626a6e5607c50a7_4cf3dfa1.log
-rw-r--r-- 1 jellyfin jellyfin  7615139 Sep  9 23:31 jellyfin20240909_001.log
-rw-r--r-- 1 jellyfin jellyfin 10485867 Sep  9 13:51 jellyfin20240909.log
-rw-r--r-- 1 jellyfin jellyfin  8527661 Sep 10 23:31 jellyfin20240910.log
-rw-r--r-- 1 jellyfin jellyfin 10485843 Sep 11 22:30 jellyfin20240911_001.log
-rw-r--r-- 1 jellyfin jellyfin  3633574 Sep 11 23:31 jellyfin20240911_002.log
-rw-r--r-- 1 jellyfin jellyfin 10485772 Sep 11 22:23 jellyfin20240911.log
-rw-r--r-- 1 jellyfin jellyfin  1217731 Sep 12 17:01 jellyfin20240912_001.log
-rw-r--r-- 1 jellyfin jellyfin 10490738 Sep 12 09:17 jellyfin20240912.log

$ du -c /var/log/jellyfin/*g
61M     total
```
Not much there. Probably more than I need and I can certainly gzip/compress the older logs with logrotate. Looks like logrotate isn't managing the jellyfin logs at all.  I haven't manually cleaned that directory ... er ... ever, so those few log files are all controlled by jellyfin, I guess.

When looking for large files, I use this alias:
```
alias du-big-sort='du -sh *|sort -h'
```
For example, 
```
$ cd /var
$ du-big-sort
0       lock
0       run
4.0K    local
4.0K    mail
4.0K    opt
16K     lost+found
24K     tmp
128K    snap
4.8M    spool
14M     backups
563M    crash
566M    cache
1.1G    lib
2.3G    log
```

So, I need to work my way down the /var/log directory to figure out which logs are eating 2.3G.  I'll not show the small stuff below, just the largest few files/directories as I go deeper.
```
...
13M     kern.log.1
15M     kern.log
96M     syslog
131M    syslog.1
2.0G    journal
```

By far, the /var/log/journal/ directory is using the most storage.
```
$ du-big-sort 
2.0G    299bc9611c014b03a884708043024ec2

/var/log/journal$ ll
total 12
drwxr-sr-x+  3 root systemd-journal 4096 May 22  2023 ./
drwxrwxr-x  15 root syslog          4096 Sep 12 00:00 ../
drwxr-sr-x+  2 root systemd-journal 4096 Sep 12 14:38 299bc9611c014b03a884708043024ec2/

```
That looks like the systemd journalctl is eating most of the space, so I can run a few commands to clean that up immediately, the I can modify the journald.conf file to prevent it getting that large again. Some examples:
```
  journalctl --disk-usage   # See log file disk use
  sudo journalctl --vacuum-size=200M    # Drop log file size to 200M, if possible.
  sudo journalctl --vacuum-time=10d     # Drop logs, over 10 days old
```
After running a **sudo journalctl --vacuum-size=200M**, 
```
$ du-big-sort 
[COLOR="#FF0000"]161M[/COLOR]    299bc9611c014b03a884708043024ec2
```
It was 2.0G before. Not anymore.  But it will grow to that size again.  Inside /etc/systemd/journald.conf I can change the size limits. Use **sudoedit /etc/systemd/journald.conf** to safely change that file:
Old:
```
#SystemMaxUse=
#SystemKeepFree=
SystemMaxFileSize=200M
#SystemMaxFiles=100
#RuntimeMaxUse=
#RuntimeKeepFree=
RuntimeMaxFileSize=200M
RuntimeMaxFiles=100
```

New:
```
SystemMaxUse=[COLOR="#FF0000"]200M[/COLOR]
#SystemKeepFree=
SystemMaxFileSize=[COLOR="#FF0000"]20M[/COLOR]
#SystemMaxFiles=100
#RuntimeMaxUse=
#RuntimeKeepFree=
RuntimeMaxFileSize=[COLOR="#FF0000"]20M[/COLOR]
RuntimeMaxFiles=100
```
Now I need to reload/restart journald.  A reboot would be the safest, but I have about 20 programs open, so that will need to wait.  Looks like restart isn't a valid option, so I put to commands on the command like to stop/start systemd-journald quickly.
```
$ sudo service systemd-journald status
&#9679; systemd-journald.service - Journal Service
     Loaded: loaded (/lib/systemd/system/systemd-journald.service; static; vendor preset: enabled)
     Active: active (running) since Thu 2024-09-12 17:45:59 EDT; 10s ago
...
```
Looks fine.
That should do it.  I didn't check the manpage to be certain what each specific setting meant, so it is very possible I'm misinterpreting what the descriptive setting truly means.  Oh well.

BTW, my /var/ storage is allocated separately from / ... for exactly this reason.
```
NAME                              TYPE  FSTYPE              SIZE FSAVAIL FSUSE% LABEL       MOUNTPOINT
nvme0n1                           disk                    931.5G                            
&#9500;&#9472;nvme0n1p1                       part  ext2                  1M                            
&#9500;&#9472;nvme0n1p2                       part  vfat                 50M   43.8M    12%             /boot/efi
&#9500;&#9472;nvme0n1p3                       part  ext4                700M  313.9M    46%             /boot
&#9492;&#9472;nvme0n1p4                       part  LVM2_member       930.8G                            
  &#9500;&#9472;vg01-swap01                   lvm   swap                4.1G                            [SWAP]
  &#9500;&#9472;vg01-root01                   lvm   ext4                 35G   24.7G    23%             /
  &#9500;&#9472;vg01-var01                    lvm   ext4                 20G   13.1G    27%           [COLOR="#FF0000"]  /var[/COLOR]
  &#9500;&#9472;vg01-tmp01                    lvm   ext4                  4G    3.3G     9% tmp01       /tmp
  &#9500;&#9472;vg01-home01                   lvm   ext4                 20G    7.3G    58% home01      /home
  &#9492;&#9472;vg01-libvirt--01              lvm   ext4                137G    2.8G    98% libvirt--01 /var/lib/libvirt

```

I use LVM for the flexibility it provides, not just a "Use LVM" checkbox install.

If I'm really worried, I should set a reminder to check the journal size tomorrow, then next week, to ensure the conffile changes worked.  That's easy.
```
$ journalctl --disk-usage
Archived and active journals take up 184.0M in the file system.
```
I'll run that command via 'at' tomorrow morning.  When at runs, I'll get an email with the data.
```
$ echo "/usr/bin/journalctl --disk-usage"| at 6 am
$ echo "/usr/bin/journalctl --disk-usage"| at now + 7 days
```
Now I don't need to remember to do anything more.  There are 3 jobs in my atq
```
$ atq
272     Fri Sep 13 06:00:00 2024 a tf
273     Thu Sep 19 17:50:00 2024 a tf
263     Sun Nov 10 16:32:00 2024 a tf

```
When I need for something to happen later, I often use **at** and forget about it.  I think the Nov task is deleting a file that I may need for the govt, but the file becomes useless in November, so I delete it.

And this is why I love, love, love, Unix-like OSes.  Automation and being able to forget things that aren't important, once handled.

---

### Post by scottbouch-com on 2024-09-13
Thanks, that's helpful. 

So in tracking down the sizes:

root:
```

/$ sudo du -sh *|sort -h
du: cannot access 'proc/50520/task/50520/fd/4': No such file or directory
du: cannot access 'proc/50520/task/50520/fdinfo/4': No such file or directory
du: cannot access 'proc/50520/fd/3': No such file or directory
du: cannot access 'proc/50520/fdinfo/3': No such file or directory
0    bin
0    lib
0    lib32
0    lib64
0    libx32
0    proc
0    sbin
0    sys
4.0K    cdrom
4.0K    media
16K    lost+found
104K    tmp
176K    home
1.6M    run
2.3M    root
11M    core
12M    etc
58M    srv
90M    dev
131M    boot
528M    opt
2.5G    snap
3.4G    usr
8.1G    swap.img
113G    var
6.1T    mnt

```

As I said before, /var/www and /mnt have other larger volumes mounted there, so should be ignored.

```

/var$ sudo du -sh *|sort -h
0    lock
0    run
4.0K    crash
4.0K    local
4.0K    opt
8.0K    mail
76K    tmp
108K    snap
3.2M    backups
3.2M    spool
128M    cache
17G    www
42G    log
54G    lib
```

So, ignoring the 17GB in /www, it seems that /log and /lib look to be the biggest.

Ignoring anything less than 1M to minimise the list:

/var/log:
```

/var/log$ sudo du -sh *|sort -h
...
1.1M    syslog.7.gz
1.2M    syslog.6.gz
2.5M    dist-upgrade
3.5M    cloud-init.log.1
8.3M    apache2
14M    letsencrypt
143M    syslog.2.gz
221M    gitlab
1.5G    zm
4.1G    journal
5.7G    syslog
31G    syslog.1
```


and /var/lib:
```

/var/lib$ sudo du -sh *|sort -h
...
1.9M    fwupd
3.4M    command-not-found
4.3M    ubuntu-advantage
41M    dpkg
197M    apt
1.3G    snapd
8.2G    emby
44G    mysql

```

So some big offenders are /var/log/syslog.1 and /var/lib/mysql

syslog is big, but syslog.1 is massive! Reading online at [https://askubuntu.com/questions/1433356/large-var-log-syslog-1-file-what-should-i-do](https://askubuntu.com/questions/1433356/large-var-log-syslog-1-file-what-should-i-do) I will try some of the tips recommended fo delete and empty syslog files.

This one command from the above link cleared** _33 GB_** of archived logs: rm /var/log/*[0-9] /var/log/*.gz


Exploring /var/lib/mysql shows zoneminder's database to have been **very naughty** too at 44 GB!:

```

/var/lib/mysql$ sudo du -sh *|sort -h
...
4.0M    mysql
13M    ibtmp1
96M    ib_logfile0
141M    ibdata1
524M    phpbb
44G    zm

```

I have headed off the ZM forum for help with this SQL issue. 

Many thanks all, Scott.

---

### Post by ajgreeny on 2024-09-13
I think 8.2G  for /var/lib/emby is pretty big; mine is just 113M so I wonder if you have a much larger library of media than I do, (mine is about 400G) but I do not allow Emby to download a huge amount of metadata so that may also account for some differences.

---

### Post by TheFu on 2024-09-13
```
4.1G    journal
5.7G    syslog
31G    syslog.1
```
Ouch!  Something is pushing lots of crap into your logs.  Making log files smaller often means there's some sort of problem in some programs and the logs are filling due to it.  Time to watch the end of the syslog file as messages are added and track down the issues.

```
$ tail -f /var/log/syslog
```

I'd set a limit in logrotate on the size that syslog can get, then rotate and compress the files more often based on the size.


BTW, this morning, I had an email waiting from the 'at' command shown above.
```
Archived and active journals take up 672.0M in the file system.
```

It appears that my attempt to limit journald logs to 200MB didn't work. But, 
```
$ du -sh 299bc9611c014b03a884708043024ec2/
169M    299bc9611c014b03a884708043024ec2/
```
is still fine.  There must be journals being stored elsewhere with the other 500+MB.  I found 350MB in /tmp/ ....
```
$ df .
Filesystem              Size  Used Avail Use% Mounted on
/dev/mapper/vg01-var01   20G  3.6G   15G  20% /var
```
still has plenty of free space, so I'm not going to worry about it any more, but I'll get another email next week that will clarify things.

The manpage for journald.conf will explain things clearly. I could try again. Seems that 2 settings are needed. Setting just the max size isn't sufficient.  The example shows setting the required disk free amount - which makes little sense to me, but the systemd guys think in odd ways often.  I'll check if it is a problem next week when the next email comes.

I do have logwatch running nightly sending me reports of any issues across all my systems.   Takes about 15 seconds per system to review it.  That's part of being a sysadmin. Reviewing logs.

---

### Post by scottbouch-com on 2024-09-13
I have 6 TB of media, but I suppose it's down to the number of items, ie: TV series will require more lines in a database than one film.

---

### Post by scottbouch-com on 2024-09-13
> **TheFu said:**
> ```
4.1G    journal
5.7G    syslog
31G    syslog.1
```
Ouch!  Something is pushing lots of crap into your logs.  Making log files smaller often means there's some sort of problem in some programs and the logs are filling due to it.  Time to watch the end of the syslog file as messages are added and track down the issues.

```
$ tail -f /var/log/syslog
```


Turns out to be Zoneminder writing a LOT to syslog... I have found settings to stop it doing so. Every time a spider's web blew in the wind, the Ubuntu syslog was recording the event!

I still have a big problem with the Zoneminder SQL file, but I need the ZM forum to tell me how to fix that.

Thanks for the Ubuntu support, much appreciated!!

---

### Post by TheFu on 2024-09-13
> **scottbouch-com said:**
> I have 6 TB of media, but I suppose it's down to the number of items, ie: TV series will require more lines in a database than one film.

I'm afraid to say how much TV and movies I've recorded over the decades.  Probably 5x that much.  Plex was eating over 100G for metadata even with thumbnails and "optimization" disabled.  I switched to Jellyfin and it uses ...
```
Filesystem                                   Size  Used Avail Use% Mounted on
/dev/mapper/WDBLK_8T-jellyfin                 22G  9.6G   11G  48% /var/lib/jellyfin
```
Very little. Under 10G.  That is for 35K+ photos, 400G+ of music, and all the video/TV/Movies.  Note how I have a separate LV just for jellyfin metadata?  Split that off when I was using Plex and it kept filling up the disk, crashing the server. When I migrated to Jellyfin, just seemed like a good idea to keep the storage separate.

---

### Post by scottbouch-com on 2024-09-13
Just looked up Jellyfin... turns out I started using Emby at about the same time that Jellyfin was first released, but I have only heard of it today through this thread here. 

Back in circa 2018 I was previously using Plex, but  wanted a more open-source alternative so switched to Emby. 

Jellyfin reads as a little more down the FLOSS route though, so I may give it a go, as privacy is important to me, but I need to see how good the apps are for smart TV, android devices etc.. Last thing I want to do is upset the family again when they can't use the wonderful services I provide.... Such as when ZM killed Emby this week by filling up my HDD... Honestly you provide a service that works perfectly for 364 days of the year, as soon as there's one hiccup they start saying "Why can't we just use Netflix and Spotify like everybody else?" And round we go again with the conversation about privacy and big data, and countryside limitations of broadband speeds.

---

### Post by TheFu on 2024-09-13
Jellyfin isn't perfect. There are lots of issues with it, but if those issues don't matter to you, great.  I like it because it works with my network OTA TV tuners without any addons.  They support just 1 brand - Silicon Dust - no others.  But Silicon Dust tuners are excellent and I've had them long before switching to Plex or Jellyfin.

For DRM stuff, we have a Roku.  Roku isn't available world wide, but I just got tired of streaming services breaking with my preferred playback devices.  I seldom use the Jellyfin system to watch anything.  It is basically a storage, media, and VM server that I could put into a closet with a power cable and ethernet cord.  For playback, I use raspberry pis running OSMC with the Jellyfin addon and an Android tablet as the media controller and sometimes viewer.  I've hated the Plex app interface since about 3 minutes after trying it out.  I much prefer the Kodi interface for playback.  Captions don't disappear when playback is paused like on Plex.  Plus there's zero privacy with Plex.  I considered emby, but I'll pick F/LOSS over proprietary almost every time.  It is a personality flaw, I know.

---

### Post by ajgreeny on 2024-09-14
The biggest problem i found with jellyfin,  which may not matter to you, is that it will not work with or show my large library of photos.
All other  media-servers I've looked at were fine for this including DLNA and Emby which is a surprise to me as jellyfin was forked from Emby.

I realise there are other ways to show photos which might be OK for me but other family members feel that is very annoying abe expect everything to appear in the Emby library. If jellyfin added that I would move to it immediately but as things are it will remain Emby for me.

---

### Post by TheFu on 2024-09-14
I honestly haven't looked too much at photos in jellyfin.  

I tend to use **feh** to show slideshows and only if the other people demand it.  

Just looked and Jellyfin doesn't have a content type for photos at all.  Got an update this morning, so I'm on the latest.  Googled the jellyfin documentation and it says that photos aren't a supported content type, but that in a mixed library, they will be shown. The official documentation specifically says > Use of the mixed library type is currently discouraged due to unreliable metadata results. We encourage the use of the dedicated library types. so it isn't recommended.  I'll stick with feh.  

Photos are stored on read-only NFS here, so any client can view them anyway.  I'm positive that Nextcloud has access, so everyone in the house can view them from any device already if they want a fancy GUI.

---

### Post by ajgreeny on 2024-09-14
Yes, I saw that info about mixed library but still could not get it to work properly, hence sticking with Emby as my full media-server.

I do sometimes also use minidlna which is fine for photos and much smaller in terms of the metadata it requires, at least in my library, but that may be because of the small amount of metadata I want for the photos; all I want is to show them on my smart TV.

---

### Post by TheFu on 2024-09-14
> **ajgreeny said:**
> ... much smaller in terms of the metadata it requires, at least in my library, but that may be because of the small amount of metadata I want for the photos; all I want is to show them on my smart TV.

I don't trust outside DBs with my metadata.  I put photo metadata into the directory structure and EXIF.

---

### Post by mike.berkley@gmail.com on 2024-09-16
I would suggest using `lsof` to look for temporary files that have been deleted, but are still in use.

How does one easily clean up temporary files after a program?  If the program exits abnormally, leftover files are not removed, so they are left on the hard disk.
Let me introduce the `unlink()` call.  In your program, you `open()` the file as usual, but then you `unlink()` the file's name from the directory structure.  You have a valid open file descriptor that the kernel honours, so you can continue to read and write to the file as much as you need.  When your program exits, even aborts, the file space is automatically freed.  There is no filesystem corruption.

I suspect that some of your programs are using "(deleted)" files, and for some reason, one of them is using more space than it used to.  You can search for them with:

      > lsof / | egrep 'REG.*(deleted)' | grep -v /memfd | less

This command looks for programs using REG (regular) files in the root filesystem.
On my laptop, I found that firefox, chrome, tmux and KDE were all using deleted files for temporary storage.

---

### Post by sgt-mike on 2024-10-14
Not to distract shift this thread.
I would like to thank everyone whom has responded to the OP's Post. 
Had a similar occurrence with a headless server, I used what folks posted to diagnose the OP's issue.
This post helped me to resolve my issue. 
So again Thank you

---

