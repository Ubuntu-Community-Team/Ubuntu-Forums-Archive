---
title: "Many viruses found on my ubuntu system!!!"
date: 2010-09-01
forum: Security
---

### Post by Zacinfinite on 2010-09-01
My system was getting damn slow internet speed and i suspected something was wrong. I downloaded KlamAV antivirus and scanned my system. As soon as I found these viruses I wrote this thread. System check is still going on.

---

### Post by ex_isp on 2010-09-01
Doesn't necessarily mean you have infected files.  Probably just labeling encrypted zip files as suspicious.  Not enough info in your screen shot to tell more

---

### Post by ac7ss on 2010-09-01
It looks like clam is merely flagging the files as "Encrypted Zip" files. A .so file is a shared library file.

If there are any real viruses, then be concerned. If the system is slowing down, run top and see what is taking the timeslices.

try typing
```
ac7ss@thor:~$ top -b -n1 >temptop
ac7ss@thor:~$ less temptop

```
example output:

System is mainly idle, a little waiting. but clean.

```
top - 21:31:14 up  2:19,  2 users,  load average: 0.35, 0.44, 0.38
Tasks: 170 total,   1 running, 169 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.9%us,  2.4%sy,  1.2%ni, 88.9%id,  1.4%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   1016692k total,   991156k used,    25536k free,   101748k buffers
Swap:  2980016k total,     2472k used,  2977544k free,   571896k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
12478 ac7ss     20   0  2544 1096  800 R    7  0.1   0:00.07 top                
  860 root      20   0 41864  16m  10m S    2  1.7   4:38.66 Xorg               
 1742 ac7ss     20   0 40728  19m 5152 S    2  2.0   0:33.31 ubuntuone-syncd    
 1929 ac7ss     25   5  123m  25m  13m S    2  2.6   0:15.87 chrome             
    1 root      20   0  2808 1700 1220 S    0  0.2   0:01.14 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.06 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         

```

I had a hacker run some IP scanning programs called "a" and "b". I caught this before it sent out any packages because it was dogging the system down.

---

### Post by linux18 on 2010-09-01
klam AV raises many many many false alarms

---

### Post by carl4926 on 2010-09-01
This is typical behaviour

You are more likely to rootkit trouble than a virus.

---

### Post by Zacinfinite on 2010-09-01
_[U]HI AC7SS, Here is the out put of_[/U]: 

zac@zac-desktop:~$ top -b -n1 >temptop
zac@zac-desktop:~$ less temptop

---

### Post by Zacinfinite on 2010-09-01
why the hell so many entries in the output of:-

zac@zac-desktop:~$ top -b -n1 >temptop
zac@zac-desktop:~$ less temptop


OUTPUT:-
----------------------------------------------------------------------------------------------------
top - 10:21:23 up 13:29,  2 users,  load average: 1.18, 1.16, 1.27
Tasks: 150 total,   2 running, 148 sleeping,   0 stopped,   0 zombie
Cpu(s): 10.8%us,  1.8%sy,  0.3%ni, 78.4%id,  8.6%wa,  0.1%hi,  0.2%si,
Mem:    735372k total,   717824k used,    17548k free,    27872k buffe
Swap:   489940k total,    79012k used,   410928k free,   355956k cache

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  
 4395 zac       20   0  102m  99m  816 R 94.4 13.9  43:03.13 clamscan 
 4665 zac       20   0  2468 1056  776 R  1.9  0.1   0:00.02 top      
    1 root      20   0  2664  768  472 S  0.0  0.1   0:01.17 init     
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd 
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration
    4 root      15  -5     0    0    0 S  0.0  0.0   0:08.86 ksoftirqd
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.41 events/0 
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset   
    8 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper  
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 netns    
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 async/mgr
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrit
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.92 kblockd/0
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid   
   14 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_not
   15 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_hot
   16 root      15  -5     0    0    0 S  0.0  0.0   0:05.45 ata/0    
   17 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux  
   18 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_
   19 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd    
   20 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod  
   21 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd    
   22 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 bluetooth
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khungtask
   26 root      15  -5     0    0    0 S  0.0  0.0   0:17.70 kswapd0  
   27 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0    
   28 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-
   29 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 crypto/0 
   33 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
   34 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 scsi_eh_1
   36 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kstriped 
   37 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmpathd/0
   38 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmpath_ha
   39 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksnapd   
   40 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kondemand
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kconserva
   42 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd 
  237 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2
  238 root      15  -5     0    0    0 S  0.0  0.0   0:11.18 usb-stora
  268 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 usbhid_re
  360 root      15  -5     0    0    0 S  0.0  0.0   0:03.80 kjournald
  361 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ext4-dio-
  418 root      20   0  2156  372  252 S  0.0  0.1   0:00.09 upstart-u
  420 root      16  -4  2652  412  232 S  0.0  0.1   0:00.08 udevd    
  608 root      18  -2  2648  392  208 S  0.0  0.1   0:00.02 udevd    
  609 root      18  -2  2648  304  188 S  0.0  0.0   0:00.00 udevd    
  651 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused
  736 root      20   0  1852  204  188 S  0.0  0.0   0:00.09 dd       
  758 messageb  20   0  3172  984  344 S  0.0  0.1   0:01.63 dbus-daem
  759 syslog    20   0 33704  812  608 S  0.0  0.1   0:00.12 rsyslogd 
  779 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kgameport
  780 haldaemo  20   0  6180 1324  824 S  0.0  0.2   0:00.67 hald     
  786 root      20   0  8380 1304  916 S  0.0  0.2   0:00.08 NetworkMa
  787 avahi     20   0  2824  540  448 S  0.0  0.1   0:00.02 avahi-dae
  790 avahi     20   0  2824  140  124 S  0.0  0.0   0:00.00 avahi-dae
  797 root      20   0  3908  932  780 S  0.0  0.1   0:00.09 modem-man
  802 root      20   0 19416 1100  872 S  0.0  0.1   0:00.11 console-k
  868 root      20   0  3344  592  480 S  0.0  0.1   0:00.04 hald-runn
  897 root      20   0  4780  376  376 S  0.0  0.1   0:00.00 wpa_suppl
  958 root      20   0  8580 1248 1000 S  0.0  0.2   0:00.11 gdm-binar
 1006 root      20   0  1704  236  236 S  0.0  0.0   0:00.00 getty    
 1008 root      20   0  1704  236  236 S  0.0  0.0   0:00.00 getty    
 1020 root      20   0  1704  236  236 S  0.0  0.0   0:00.00 getty    
 1026 root      20   0  1704  236  236 S  0.0  0.0   0:00.00 getty    
 1028 root      20   0  1704  236  236 S  0.0  0.0   0:00.00 getty    
 1030 root      20   0  1980  296  296 S  0.0  0.0   0:00.00 acpid    
 1039 root      20   0  2092  396  336 S  0.0  0.1   0:00.09 cron     
 1040 daemon    20   0  1960  184  172 S  0.0  0.0   0:00.00 atd      
 1089 root      20   0  8524 1144 1000 S  0.0  0.2   0:00.04 gdm-simpl
 1090 root      20   0  8572  712  560 S  0.0  0.1   0:00.23 nmbd     
 1092 root      20   0  166m  25m 5436 S  0.0  3.6  13:11.37 Xorg     
 1096 root      20   0 15268  324  324 S  0.0  0.0   0:00.00 smbd     
 1106 root      20   0 15268  172  172 S  0.0  0.0   0:00.00 smbd     
 1140 root      20   0 11672  648  484 S  0.0  0.1   0:00.09 winbindd 
 1150 root      20   0 11672  500  372 S  0.0  0.1   0:00.02 winbindd 
 1195 root      20   0  6788  924  620 S  0.0  0.1   0:00.03 cupsd    
 1227 haldaemo  20   0  3264  368  368 S  0.0  0.1   0:00.00 hald-addo
 1246 root      20   0  3424  512  424 S  0.0  0.1   0:07.02 hald-addo
 1268 root      20   0  3424  660  528 S  0.0  0.1   0:41.93 hald-addo
 1278 root      20   0  3424  544  440 S  0.0  0.1   0:00.09 hald-addo
 1368 root      20   0 17320  756  452 S  0.0  0.1   0:01.35 apache2  
 1372 www-data  20   0 17792  860  304 S  0.0  0.1   0:00.00 apache2  
 1373 www-data  20   0 17792  868  304 S  0.0  0.1   0:00.00 apache2  
 1374 www-data  20   0 17792  876  304 S  0.0  0.1   0:00.00 apache2  
 1375 www-data  20   0 17792  876  304 S  0.0  0.1   0:00.00 apache2  
 1378 www-data  20   0 17792  864  304 S  0.0  0.1   0:00.01 apache2  
 1394 root      20   0  8600  896  896 S  0.0  0.1   0:00.02 gdm-sessi
 1432 zac       20   0 25328 2736 2164 S  0.0  0.4   0:00.39 gnome-ses
 1490 root      20   0  1704  236  236 S  0.0  0.0   0:00.00 getty    
 1512 zac       20   0  4712  128  100 S  0.0  0.0   0:00.05 ssh-agent
 1515 zac       20   0  3384  364  288 S  0.0  0.0   0:00.00 dbus-laun
 1516 zac       20   0  3160 1112  492 S  0.0  0.2   0:01.39 dbus-daem
 1520 zac       20   0 94164 1512  724 S  0.0  0.2   0:07.68 pulseaudi
 1523 zac       20   0 10624  860  860 S  0.0  0.1   0:00.01 gconf-hel
 1525 zac       20   0  7576 2592 1308 S  0.0  0.4   0:02.40 gconfd-2 
 1531 root      20   0  5128 1020  768 S  0.0  0.1   0:00.05 devkit-po
 1565 zac       20   0  103m 5184 3396 S  0.0  0.7   0:46.33 gnome-set
 1567 zac       20   0 40876 1284  944 S  0.0  0.2   0:00.03 gnome-key
 1570 zac       20   0 22324 2456 2056 S  0.0  0.3   0:00.23 seahorse-
 1575 zac       20   0  5984 1144  952 S  0.0  0.2   0:00.10 gvfsd    
 1581 zac       20   0 28724 4764 3240 S  0.0  0.6   0:00.88 notify-os
 1582 zac       20   0 38128 1068  884 S  0.0  0.1   0:00.01 gvfs-fuse
 1586 zac       20   0  103m 7896 5076 S  0.0  1.1   0:32.48 metacity 
 1618 zac       20   0 44060  11m 5628 S  0.0  1.6   1:20.67 gnome-pan
 1624 zac       20   0  108m  18m 6472 S  0.0  2.6   2:06.12 nautilus 
 1626 zac       20   0 40736  948  948 S  0.0  0.1   0:00.12 bonobo-ac
 1629 zac       20   0 42536 2900 2060 S  0.0  0.4   0:00.23 evolution
 1631 zac       20   0 28300 3924 2972 S  0.0  0.5   0:00.45 polkit-gn
 1634 zac       20   0 39272 5556 2800 S  0.0  0.8   0:00.99 nm-applet
 1635 zac       20   0 27316 4528 3004 S  0.0  0.6   0:05.81 update-no
 1637 zac       20   0 29332 3572 2544 S  0.0  0.5   0:00.50 python   
 1639 zac       20   0  164m 5064 2968 S  0.0  0.7   0:00.63 gnome-vol
 1645 zac       20   0 16888 2600 2224 S  0.0  0.4   0:00.13 bluetooth
 1646 zac       20   0 17052 2640 2064 S  0.0  0.4   0:00.20 gdu-notif
 1649 root      20   0  7240 1520  876 S  0.0  0.2   0:00.16 polkitd  
1656 root      20   0  5276 1300  880 S  0.0  0.2   0:00.33 devkit-di
 1657 root      20   0  4828  360  260 S  0.0  0.0   0:07.38 devkit-di
 1658 zac       20   0 17220 1324  864 S  0.0  0.2   0:00.09 gnome-scr
 1660 zac       20   0 40268 1484  976 S  0.0  0.2   0:00.35 gvfs-gdu-
 1669 zac       20   0  6172 1264  944 S  0.0  0.2   0:01.12 gvfsd-tra
 1673 zac       20   0  6472  960  800 S  0.0  0.1   0:00.02 gvfs-gpho
 1679 zac       20   0 32384 4824 3024 S  0.0  0.7   0:00.55 indicator
 1681 zac       20   0 31104 4384 2676 S  0.0  0.6   0:00.48 indicator
 1683 zac       20   0 11932 1096  972 S  0.0  0.1   0:00.13 indicator
 1685 zac       20   0  6308 1040  900 S  0.0  0.1   0:00.04 indicator
 1687 zac       20   0  6876 1160  996 S  0.0  0.2   0:00.10 indicator
 1689 zac       20   0  8060 1696 1328 S  0.0  0.2   0:00.38 indicator
 1722 zac       20   0  5748  856  856 S  0.0  0.1   0:00.00 gvfsd-bur
 1749 root      20   0 11700 1988  704 S  0.0  0.3   0:00.23 system-se
 2057 www-data  20   0 17792  816  304 S  0.0  0.1   0:00.00 apache2  
 2525 zac       20   0 96452  35m 5204 S  0.0  5.0   0:17.95 evince   
 2586 zac       20   0 65572 3896 3256 S  0.0  0.5   0:04.02 Tasque   
 3103 root      20   0     0    0    0 S  0.0  0.0   0:00.56 pdflush  
 3271 root      20   0     0    0    0 S  0.0  0.0   0:01.53 pdflush  
 4311 clamav    20   0  3112  664  420 S  0.0  0.1   0:06.95 freshclam
 4364 zac       20   0 70060  12m 4616 S  0.0  1.7   2:16.47 klamav   
 4369 zac       20   0 25368 2056  940 S  0.0  0.3   0:00.03 kdeinit  
 4374 zac       20   0 25304 1928  872 S  0.0  0.3   0:00.38 dcopserve
 4377 zac       20   0 25864 2440 1316 S  0.0  0.3   0:00.02 klauncher
 4379 zac       20   0 26720 3084 1736 S  0.0  0.4   0:00.21 kded     
 4390 zac       20   0 25664 2560 1340 S  0.0  0.3   0:00.03 kio_file 
 4394 zac       20   0  1756  232  164 S  0.0  0.0   0:00.00 sh       
 4457 zac       20   0 29332 4460 1976 S  0.0  0.6   0:24.41 knotify  
 4473 zac       20   0  1756  268  192 S  0.0  0.0   0:00.00 firefox  
 4478 zac       20   0  1756  276  192 S  0.0  0.0   0:00.00 run-mozil
 4482 zac       20   0  222m  49m  13m S  0.0  6.8   1:19.17 firefox-b
 4639 zac       20   0 37880  12m 9812 S  0.0  1.8   0:00.74 gnome-ter
 4640 zac       20   0  1904  700  576 S  0.0  0.1   0:00.00 gnome-pty
 4641 zac       20   0  6268 3524 1500 S  0.0  0.5   0:00.32 bash

---

### Post by rookcifer on 2010-09-01
My output looks about the same as that, so it's nothing abnormal.  I am wondering, though, why you have Apache installed.  Is that a server box?

---

### Post by Zacinfinite on 2010-09-01
Thats the point "ROOKCIFER". I havent installed apache. If you see the users, u will find "www-data" and "avahi" which dont exist on my system. I only got "zac" account and root.

---

### Post by Ryan Dwyer on 2010-09-01
This thread seems to indicate you were at least about to install Apache:
[http://ubuntuforums.org/showthread.php?t=1561979](http://ubuntuforums.org/showthread.php?t=1561979)

Are you sure you've never installed it on that computer? I can see it's running based on your top output.

The www-data and avahi accounts do exist, but they're system accounts so you won't see them usually. Look at /etc/passwd to see all your users.

---

### Post by Zacinfinite on 2010-09-01
OMG, u found that thread. Well ha ha I was planning to setup web server on my dads spare PCs not on my own. Anyways as soon as i removed apache and www-data userid, my system started to catch good internet speed.

But why did antivirus catch so many viruses on my filesystem?

---

### Post by spynappels on 2010-09-01
Other posters pointed out that these were not actual viruses, just files or folders it could not identify or read, possibly due to encryption.

---

### Post by rookcifer on 2010-09-01
> **spynappels said:**
> Other posters pointed out that these were not actual viruses, just files or folders it could not identify.

Yes, but he has no intention of actually listening to anyone, so, eh, whatever.

---

### Post by 4ebees on 2010-09-01
> **Zacinfinite said:**
> OMG, u found that thread. Well ha ha I was planning to setup web server on my dads spare PCs not on my own. Anyways as soon as i removed apache and www-data userid, my system started to catch good internet speed.

But why did antivirus catch so many viruses on my filesystem?

The short answer is that the scanner could not read the files it has identified. As such it considers them potential sources of harmful material/software etc.

However, as others have mentioned, the files are encrypted zip files and highly unlikely to be the source of any problem.

They are what are called 'false positives' - much like if you put all the socks you find into your drawers at home. Some are likely to belong to other people :))

Viruses are not an issue with GNU/Linux (theoretically maybe, but not in practice). They are problems only if you pass them on to other people who use Windows or similar.

Your concerns are understandable, but there is nothing is what you've shown us that you should be concerned about.

I hope this helps.

---

