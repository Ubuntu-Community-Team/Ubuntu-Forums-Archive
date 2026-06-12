---
title: "[SOLVED] Server full - conflicting views - how do I detect the cause?"
date: 2008-02-19
forum: Server Platforms
---

### Post by altonbr on 2008-02-19
Right now I have a 4.7GB Ubuntu Server running inside VMware.

I copied over an Apache virtualhost file, edited it but couldn't re-save it. The server said it's full.

Sure enough I ran ```
df -h
``` and it said I have 4.7GB all used up.

I ran Baobab ("Disk Usage Analyzer") over SSH and it returned that I only have 1.6GB used up.

What can I do to find the cause of this problem or how can I remove some unneeded files?

This is all I know of so far to clear up some space...
```
sudo apt-get clean
```

---

### Post by astrotech226 on 2008-02-19
Try a disk usage report on each of the directories of root and let's see the output of it.  Interesting to see if they add up to 4.7G.

```
sudo du -sh /*
```

---

### Post by justleen on 2008-02-20
slighty nicer way of getting the du of /
(do a sudo -i  or su -  first)
```
 for dirs in `ls -1`; do du -hs $dirs; done 
```

> root@leen-laptop:/# for dirs in `ls -1`; do du -hs $dirs; done
4.8M    bin
18M     boot
0       cdrom
116K    dev
9.8M    etc
52M     home
4.0K    initrd
0       initrd.img
155M    lib
16K     lost+found
^[[D63G media
4.0K    mnt
4.0K    opt
0       proc
148K    root
6.3M    sbin
4.0K    srv
0       sys
172K    tmp
1.8G    usr
296M    var
0       vmlinuz

---

### Post by altonbr on 2008-02-20
EDIT:

I just posted my results here, but upon further investigation of running
```
for dirs in `ls -1`; do du -hs $dirs; done
```
In /, then /var, then /var/lib, I found that /var/lib/amavis/tmp is taking up 2.8GB!

Thank you, thank you, thank you for that script! I saved that one for sure!

---

### Post by justleen on 2008-02-20
glad to be of help!

---

### Post by nab on 2008-03-02
well, I ran into a similar problem:

Up to now I used allways baobab to clean up my hard disk and locate my space wasters, but this time baobab missed about 3 GB. (total space used 7.2, used in / 4.2)

With your script I found the missing 2.9 GB in the root directory!

Thanks a lot!
Niko

---

### Post by altonbr on 2008-03-03
That script needs to escape spaces, such as when I run it on customers' Windows partitions:
> $ for dirs in `ls -1`; do du -hs $dirs; done
1.8M    31f292e6e12d224bfd7a
52K     75e594bafc3c0501a8507d72fe54
du: cannot access `ACS': No such file or directory
du: cannot access `Backup': No such file or directory
12M     AUDIO
0       AUTOEXEC.BAT
0       CONFIG.SYS
268K    Config.Msi
du: cannot access `Documents': No such file or directory
du: cannot access `and': No such file or directory
du: cannot access `Settings': No such file or directory
304M    Downloads
0       IO.SYS
0       MSDOS.SYS
du: cannot access `My': No such file or directory
du: cannot access `Shared': No such file or directory
du: cannot access `Folder': No such file or directory
48K     NTDETECT.COM
du: cannot access `Program': No such file or directory
du: cannot access `Files': No such file or directory
856M    RECYCLER
684K    StubInstaller.exe
du: cannot access `System': No such file or directory
du: cannot access `Volume': No such file or directory
du: cannot access `Information': No such file or directory
du: cannot access `WINDOWS/RegisteredPackages/{3FDF25EE-E592-4495-8391-6E9C504DAC2B}$BACKUP$/System/setup_wm.exe': Input/output error
du: cannot access `WINDOWS/Microsoft.NET/Framework/v1.1.4322/mscorwks.dll': Input/output error
6.8G    WINDOWS

---

### Post by astrotech226 on 2008-03-03
> **altonbr said:**
> That script needs to escape spaces, such as when I run it on customers' Windows partitions:

Try what I posted originally.  You don't need to escape anything to make it work:

```
du -sh *
```

---

### Post by altonbr on 2008-03-03
Hey, that works well too, but is there anyway to sort the numbers without using the -b (bytes) flag?

```
du -sb * | sort -n
```
> ...
3496348424      videos
4710272547      vmware
5062424540      my_documents
6803576371      music
8149764109      torrents
10345385339     my_videos
10493645115     my_photos
15285703828     software
17111556546     television
20032484056     operating_systems

It'd be nice if it could stay human readable.

---

### Post by astrotech226 on 2008-03-03
What you have to do is do a "du -sk" and sort it so the size can be ordered correctly.  Then, do a "du -sh" of each line returned.  It's ugly, but this could be put in a script:

du -sk * | sort -n | awk -F'\t' '{print $2}' | xargs -ia du -sh "a"

---

### Post by altonbr on 2008-03-04
> **astrotech226 said:**
> What you have to do is do a "du -sk" and sort it so the size can be ordered correctly.  Then, do a "du -sh" of each line returned.  It's ugly, but this could be put in a script:

du -sk * | sort -n | awk -F'\t' '{print $2}' | xargs -ia du -sh "a"

Wow. Saved that one for sure. I see what it's doing, albeit it's a little over my head. Fantastic!

---

