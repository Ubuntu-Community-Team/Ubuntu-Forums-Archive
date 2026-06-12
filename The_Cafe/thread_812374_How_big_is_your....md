---
title: "How big is your..."
date: 2008-05-29
forum: The Cafe
---

### Post by wdaniels on 2008-05-29
...root filesystem? (no home data, used space only)

I was just wondering how much space should be allocated to a root partition. I've always tended to allocate around 10-20GB, but never used more than about 5.5GB in practice, so I'm interested to do a quick survey to get an idea of the average...

---

### Post by swoll1980 on 2008-05-29
3 gb for me

---

### Post by Joeb454 on 2008-05-29
14GB

/home is 15 :)

---

### Post by Istonian on 2008-05-29
143 KB on my lappy.

---

### Post by qazwsx on 2008-05-29
19 GB barely enough. From df -h
/dev/sda5              19G   15G  3,1G  83% /
/dev/sda3             123G   89G   30G  75% /home

Bit boated :-k

---

### Post by Dr Small on 2008-05-29
Running Arch:
```
[drsmall@darkghost ~]$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             7.3G  2.1G  4.9G  30% /
none                  442M     0  442M   0% /dev/shm
/dev/sda1              38M  9.6M   27M  27% /boot
/dev/sda4             139G  1.2G  131G   1% /home

```

---

### Post by -grubby on 2008-05-29
```

nathan@linda:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb3             9.3G  4.4G  4.5G  50% /
/dev/hdb4              27G   11G   15G  42% /home
/dev/hdb1              38G   13G   26G  34% /media/xp

```

---

### Post by cardinals_fan on 2008-05-29
35 gigs, because I keep a couple virtual machines in there.

---

### Post by gn2 on 2008-05-30
1.7 of 6.0gb used on my Xubuntu laptop
2.2 of 15.0gb used on my Xubuntu desktop

---

### Post by freduardo on 2008-05-30
7 GB, which is more than enough for me.

---

### Post by Bungo Pony on 2008-05-30
I've given it a nice happy 30G. Just enough that I should never have to worry about space, but not too much that it's overkill.

---

### Post by dje on 2008-05-30
For me:
```
dj@dj-laptop ~ $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.7G  3.7G  5.6G  40% /
/dev/sda3              45G   17G   27G  38% /home
```

---

### Post by DexterLB on 2008-05-30
/ 15GB
/home 150GB

---

### Post by vishzilla on 2008-05-30
/ - used 3G / 10G alloted
I wonder if I should resize the partition

---

### Post by jolx on 2008-05-30
i use 3.9 GB on my root partition and allocated 10

but on my home partition ive used 60GB which was 30 last week but ive downloaded soo much :)

---

### Post by helliewm on 2008-05-30
Being a girl I was hoping for more interesting statistics here :lolflag:

Well it worked you got my attention.:)

---

### Post by aaaantoine on 2008-05-30
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              37G  4.0G   32G  12% /

```

So... 4 GiB.

I made a 40GB root partition because I didn't know what to expect.  I've wanted to change the size, but for some reason, my swap partition is sitting between my root and home partitions, which complicates things.  I'll have to back my stuff up, play with a LiveCD, and see what I can do.

---

### Post by quanumphaze on 2008-05-30
```
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1             7.8G  5.1G  2.3G  70% /
varrun                501M  224K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
procbususb            501M   64K  501M   1% /proc/bus/usb
udev                  501M   64K  501M   1% /dev
devshm                501M  1.9M  500M   1% /dev/shm
lrm                   501M   38M  464M   8% /lib/modules/2.6.24-16-generic/volatile
/dev/sda2              23G   17G  4.6G  79% /home
```

I don't even know what half this /var and stuff is for

Not shown here is the other ~25GB that holds Gutsy and soon to be some other distro.

---

### Post by ViRMiN on 2008-05-30
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/nvidia_ihegheeh3
                       29G  5.1G   24G  18% /
varrun                1.9G  288K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  144K  1.9G   1% /dev
devshm                1.9G  208K  1.9G   1% /dev/shm
lrm                   1.9G   43M  1.9G   3% /lib/modules/2.6.24-16-generic/volatile
/dev/sdc5              73G   72G  1.2G  99% /home
/dev/mapper/nvidia_ihegheeh1
                      190M   44M  137M  25% /boot
/dev/mapper/nvidia_ihegheeh5
                      233G  225G  8.4G  97% /mnt/volm1
/dev/mapper/nvidia_ihegheeh6
                      233G   75G  158G  33% /mnt/volv3
/dev/mapper/nvidia_ihegheeh7
                      250G   20G  231G   8% /mnt/volv2
/dev/sde1             298G  294G  4.6G  99% /media/voli1
/dev/sdg1             115G  114G 1005M 100% /media/volv1

```Plenty of unallocated space too :) Good job too, as I need to grow a few partitions...

---

### Post by ViRMiN on 2008-05-30
Awww... just noticed, I've not got all my partitions mounted either... hey-ho!

---

### Post by fluteflute on 2008-05-30
4.5GB (That's everything except /home /media /root and /cdrom )

---

### Post by ViRMiN on 2008-05-30
Only reason I gave a 24GB / partition was for big apps that would sit under /opt.  Doesn't really matter though; if I rebuilt, I'd reinstall those apps anyway.

---

### Post by SyL on 2008-05-30
results are quite homogeneous

---

### Post by Xanatos Craven on 2008-05-30
20gb.

---

### Post by klange on 2008-05-30
*/me runs another disk usage analyzer scan...*

**Total**: 24.5GB / 120GB (*Reads as 109GB total*)
**/home**: 3.9GB (*I have a lot of pictures*)
**/media/sda1**: 13.8GB (*10.9GB of which is videos*)
**/media/sda2**: 20KB (*Unused*)
**/**: _6.8GB_ (*sans /home, lots of libraries and headers*)
****/usr/**: 5.2GB
****/opt/**: 795.5MB
****/var/**: 582.6MB
****/lib/**: 87.7MB

/ is sda3, and /home is on sda3. I do plan on moving it.

---

### Post by lswest on 2008-05-30
here's mine:
```
/dev/sda6  16G  4.0G   11G  28% /
```

---

### Post by vrangforestillinger on 2008-05-30
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              47G  5,0G   39G  12% /
/dev/sdb1             459G  235G  201G  54% /home
/dev/sda6              46G  709M   43G   2% /usr/local
/dev/sda1              94G   82G   12G  88% /media/WindowsXP

```

Made space for future installation of maple, matlab, UT2004 and such on /usr/local. Thinking of decreasing the root size and increasing WinXP-partition (games only, they take alot of space).

---

### Post by pape on 2008-05-30
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             5.9G  3.4G  2.6G  58% /


From the responses, it seems that 6-7Gb will cover any 'normal' needs..
Mine is actually an OpenSUSE 10.3

---

