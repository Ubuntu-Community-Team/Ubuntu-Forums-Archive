---
title: "Hard-disk (incorrectly?) full"
date: 2010-08-29
forum: Server Platforms
---

### Post by dtech on 2010-08-29
Hi,

I have a problem with a Ubuntu 8.04 LTS x86_64 server, it's HD is nearly full (and was 100% full until I deleted some old kernel images and logfiles)

The strange thing is that I cannot determine what makes it full.
The / partition has 30GiB space, which should be enough. /home and /media/sde1 are mounted seperatly

I made the following disk-space report using du:
```

username@computer:/$ sudo du -sh /* --exclude home --exclude media --exclude proc --exclude dev
6.3M    /bin
20M     /boot
0       /cdrom
25M     /etc
4.0K    /initrd
0       /initrd.img
103M    /lib
0       /lib64
16K     /lost+found
8.0K    /mnt
4.0K    /opt
2.5M    /root
7.6M    /sbin
4.0K    /srv
0       /sys
56K     /tmp
1.1G    /usr
507M    /var
0       /vmlinuz

```

As you can see it barely adds up to 2GB, while df reports this:
```

username@computer:/$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/raid-root 30G    28G  331M  99% /
varrun                999M  1.1M  998M   1% /var/run
varlock               999M     0  999M   0% /var/lock
udev                  999M  128K  999M   1% /dev
devshm                999M     0  999M   0% /dev/shm
/dev/md0              942M   38M  857M   5% /boot
/dev/mapper/raid-data 711G  310G  365G  46% /home
/dev/sde1             925G  736G  142G  84% /media/sde1

```

Does anyone have any idea what the problem might be? I've excluded:

[list]
[*] Hidden files in the root directory (there are 2 of less then 1 KB)
[*] Not enough inodes (df -i tells me only 3% used)
[/list]

Other things I have considered are:
[list]
[*] Cluster overhead (e.g. 100 byte files using 4 KiB), but I don't think this could use 25 GiB (or something like that)
[*] Files in /home and/or /media/sde1 which aren't really written to their "correct" partitions. I find this unlikely and can't easily test this as this needs downtime which is possible at its earliest at 7PM this evening
[/list]

If anyone has any ideas I'll gladly try them

---

### Post by graphius on 2010-08-29
I may be out of my league here, but I have noticed that "trashed" files, as opposed to fully deleted files, can take up room, but not register with df.

---

### Post by dtech on 2010-08-29
Files get "Trashed" by Gnome or KDE, neither runs on the server (and shouldn't on any server)

---

### Post by craigp84 on 2010-08-29
Has the box been rebooted?

Sounds like there's a process(es) holding a file(s) handle open that has now been deleted.

Do you run with dircolors in your shell? If so (i've got dangling symlinks a nice bright red) an "ls -l /proc/*/fd/" as root will turn up the PID(s) and the file(s) without a reboot and just a bounce of those pids.

EDIT: p.s. the -c option and the -x options to du are handy

---

### Post by David Andersson on 2010-08-29
1) Another way to exclude /home and /media/sde1 is to use the -x option. I also think it is easier to compare lines if all have the same unit.

```
sudo du -xm --max-depth 1 /
```

Or add sort, so the culprit is shown near the end of the list:

```
sudo du -xm / | sort -n
```

2) Files can be hidden in a mount point, if they were written there before mounting. They will be reported by "df" but not by "du" while things are mounted there. (at least in xubuntu 10.04). What if you unmount /media/sde1 and /home and see if any files was mistakenly written there while they were unmounted?

---

### Post by dtech on 2010-08-29
> **David Andersson said:**
> 1) Another way to exclude /home and /media/sde1 is to use the -x option. I also think it is easier to compare lines if all have the same unit.

```
sudo du -xm --max-depth 1 /
```

Or add sort, so the culprit is shown near the end of the list:

```
sudo du -xm / | sort -n
```



I ran the first command but I am not sure what it means
```

1       /boot
113     /lib
1       /initrd
1       /media
0       /proc
1       /mnt
1       /opt
1       /srv
0       /dev
1       /lost+found
512     /var
8       /sbin
1081    /usr
25      /etc
1       /home
3       /root
1       /tmp
7       /bin
0       /sys
1745    /

```

idem with the second command:
```

sudo du -xm / | sort -n | tail -n 10

```
```

116     /var/lib/clamav
153     /usr/lib/jvm
153     /usr/lib/jvm/java-6-sun-1.6.0.20
196     /usr/bin
294     /var/lib
327     /usr/share
406     /usr/lib
512     /var
1081    /usr
1745    /

```

> **David Andersson said:**
> 
2) Files can be hidden in a mount point, if they were written there before mounting. They will be reported by "df" but not by "du" while things are mounted there. (at least in xubuntu 10.04). What if you unmount /media/sde1 and /home and see if any files was mistakenly written there while they were unmounted?

Interesting, I'll try that as soon as there are no people wroking on the server anymore

---

### Post by varunendra on 2010-08-30
I guess GParted running off a Live CD won't tell a lie.

Again, running nautilus in the same environment with **gksudo nautilus**, and then checking properties of drives or individual folders (with "Show hidden files" enabled) should also be trustworthy.

How you manage the space thereafter, however, may be a different story. But at least you would have a clear picture of your data distribution across the drive.

---

### Post by craigp84 on 2010-08-31
Go on, put us out our misery, what did it turn out to be?

---

### Post by varunendra on 2010-08-31
> **craigp84 said:**
> Go on, put us out our misery, what did it turn out to be?

..yeah, waiting desperately........................................[-o<:lolflag:.

---

### Post by dtech on 2010-09-10
I haven't been able to determine the cause. I think the report is definitly wrong though.

I've just made an (uncompressed) backup of the system and it was 1.7GB, so there is definitly something wrong.
```

tar -cvpf /home/backup/full-backup-`date '+%d-%B-%Y'`.tar --directory / --exclude=proc --exclude=cdrom --exclude=media --exclude=home --exclude=tmp .

```

---

### Post by dtech on 2010-09-11
Do you guys think it's safe to remove all files from a live CD and then copy all files from the tar archive?

---

### Post by dtech on 2010-09-25
I have found the problem: it was indeed files being written under a directory that is normally mounted but wasn't at the time.

Using a live-cd I saw that /media/sde1 wasn't empty but contained a 27GB backup and a failed half-backup of 1.1GB, that was what caused the HD to be full. After deleting the directories everything was fine again.

---

