---
title: "I think I got hacked"
date: 2010-01-12
forum: Security
---

### Post by astroorion on 2010-01-12
Cpu usage on both cores was at 25%
tried a reinstall of ubuntu 9.10 32bit
with no luck now running on livcd

---

### Post by studmf on 2010-01-12
So.....why do you say you got hacked?

---

### Post by Revolutionary101 on 2010-01-12
I doubt you got hacked (Linux is very secure) these could have been easily been caused by a mistake in the reinstallation of Ubuntu. If you have your CPU at an unusual level of work check what processes are using that 25%, most likely it will be something you were running.

---

### Post by astroorion on 2010-01-12
I notice my cpu usage was real high a couple of day's ago I checked my gmail and the bottom loading bar was acting strange I had to do a reboot I have tried alot thing's pulling the harddrive out putting in another one tried reinstalling updated to the new kernel wouldn't let me boot on the new kernel was able to boot on the old one couldn't install guarddog the desktop looked different as well login was a box

---

### Post by Revolutionary101 on 2010-01-12
I would suggest disconnecting your computer from the internet and see if it does anything different.

---

### Post by astroorion on 2010-01-12
System clock won't keep time

---

### Post by astroorion on 2010-01-12
Even with the live cd

---

### Post by CharlesA on 2010-01-12
> **astroorion said:**
> System clock won't keep time
Sounds like a hardware problem tbh.

---

### Post by astroorion on 2010-01-12
I guess I could do a memtest on memory that would leave motherboard and cpu motherboard plus cpu 
is only one and a half years old 
also will check battery

---

### Post by KarlIvan on 2010-01-13
firefox can create large overhead sometimes...i doubt you were hacked...i think youre overreacting. if anything, you downloaded something that gave you a virus at some other time, and you just so happened to notice it when you were checking your gmail...linux doesnt have many viruses out for it though, and besides, people that would know how to hack into your computer through gmail...wouldnt really care about just some random joes account info...do you understand what i mean?

first things first: what process is generating that much overhead? if its firefox, then i wouldnt really worry. unless you have firefox ver 3.0 (i think that was it) then you should be fine. there was a major vulnerability in that version, but they fixed it pretty quick. and it wouldnt matter anyway, like i said, its unlikely that somebody that has the knowledge to do something like that, would just randomly hack some random guy for petty information...unless your a millionaire or have access to something valuable, i wouldnt worry about that. the only thing in that dept is a virus that you obtained from downloading something, which as i have also said, there arent as many viruses for unix systems as there are windows, so that is probably unlikely too.

so...what happened when you put in the new hard drive? if that failed, then its probably something to do with your motherboard, or maybe your second hard drive was even faulty. what have you put onto your computer recently that would cause that (check your processes)?

---

### Post by astroorion on 2010-01-14
?

---

### Post by astroorion on 2010-01-14
Ran Rkhunter
maddog@maddog-desktop:~$ sudo rkhunter -c
[sudo] password for maddog: 
[ Rootkit Hunter version 1.3.4 ]

```
Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preload file                                [ Not found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /bin/bash                                                [ OK ]
    /bin/cat                                                 [ OK ]
    /bin/chmod                                               [ OK ]
    /bin/chown                                               [ OK ]
    /bin/cp                                                  [ OK ]
    /bin/date                                                [ OK ]
    /bin/df                                                  [ OK ]
    /bin/dmesg                                               [ OK ]
    /bin/echo                                                [ OK ]
    /bin/ed                                                  [ OK ]
    /bin/egrep                                               [ OK ]
    /bin/fgrep                                               [ OK ]
    /bin/fuser                                               [ OK ]
    /bin/grep                                                [ OK ]
    /bin/ip                                                  [ OK ]
    /bin/kill                                                [ OK ]
    /bin/less                                                [ OK ]
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /bin/dash                                                [ OK ]
    /usr/bin/awk                                             [ OK ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/chattr                                          [ OK ]
    /usr/bin/cut                                             [ OK ]
    /usr/bin/diff                                            [ OK ]
    /usr/bin/dirname                                         [ OK ]
    /usr/bin/dpkg                                            [ OK ]
    /usr/bin/dpkg-query                                      [ OK ]
    /usr/bin/du                                              [ OK ]
    /usr/bin/env                                             [ OK ]
    /usr/bin/file                                            [ OK ]
    /usr/bin/find                                            [ OK ]
    /usr/bin/GET                                             [ OK ]
    /usr/bin/groups                                          [ OK ]
    /usr/bin/head                                            [ OK ]
    /usr/bin/id                                              [ OK ]
    /usr/bin/killall                                         [ OK ]
    /usr/bin/last                                            [ OK ]
    /usr/bin/lastlog                                         [ OK ]
    /usr/bin/ldd                                             [ OK ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/mail                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/sort                                            [ OK ]
    /usr/bin/stat                                            [ OK ]
    /usr/bin/strace                                          [ OK ]
    /usr/bin/strings                                         [ OK ]
    /usr/bin/sudo                                            [ OK ]
    /usr/bin/tail                                            [ OK ]
    /usr/bin/test                                            [ OK ]
    /usr/bin/top                                             [ OK ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ OK ]
    /usr/bin/uniq                                            [ OK ]
    /usr/bin/users                                           [ OK ]
    /usr/bin/vmstat                                          [ OK ]
    /usr/bin/w                                               [ OK ]
    /usr/bin/watch                                           [ OK ]
    /usr/bin/wc                                              [ OK ]
    /usr/bin/wget                                            [ OK ]
    /usr/bin/whatis                                          [ OK ]
    /usr/bin/whereis                                         [ OK ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /usr/bin/mawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/bsd-mailx                                       [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/ifdown                                             [ OK ]
    /sbin/ifup                                               [ OK ]
    /sbin/init                                               [ OK ]
    /sbin/insmod                                             [ OK ]
    /sbin/ip                                                 [ OK ]
    /sbin/lsmod                                              [ OK ]
    /sbin/modinfo                                            [ OK ]
    /sbin/modprobe                                           [ OK ]
    /sbin/rmmod                                              [ OK ]
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/rsyslogd                                       [ OK ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/unhide                                         [ Warning ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/sbin/unhide-linux26                                 [ Warning ]

[Press <ENTER> to continue]
```

---

### Post by Neezer on 2010-01-14
If you just did a fresh intall and wiped your hard drive, you aren't going to have any evidence of a root kit or anything like that...If you did in fact get hacked there is no more evidence of it. You can however get hacked again if you don't shore up your security. 

Did you have any open ports? Port forwarding from your router? unencrypted wireless, running server systems like ssh, or vnc without properly securing them?

These are a few things that can be considered high risk....If you continue to do them you could be hacked again unless you change your security.

---

### Post by astroorion on 2010-01-14
My Wireless is wpa2 did a scan with Shield's up all port's show as being stealth

---

### Post by astroorion on 2010-01-14
Plus I am not running a server system

---

### Post by teward on 2010-01-14
Personally, I dont think you got hacked.  My CPUs automatically run at 25% of its total power just idling.  On both computers I have (Laptop and Desktop).

---

### Post by astroorion on 2010-01-14
Ok I did a check on memory
Command line top


top - 16:01:47 up 44 min,  2 users,  load average: 0.00, 0.04, 0.06
Tasks: 150 total,   2 running, 148 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.6%us,  0.7%sy,  0.0%ni, 97.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2057532k total,  1104800k used,   952732k free,    54016k buffers


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                         
 1194 root      20   0  416m  58m 7688 S    2  2.9   1:05.88 Xorg                                                                                                                                                                            
 3321 maddog    20   0 71296  15m 9440 R    1  0.8   0:03.09 npviewer.bin                                                                                                                                                                    
   32 root      20   0     0    0    0 S    0  0.0   0:00.02 pdflush                                                                                                                                                                         
 1221 root      20   0 22180 1240 1040 S    0  0.1   0:01.24 hald-addon-stor                                                                                                                                                                 
 2161 maddog    20   0  260m  14m 9612 S    0  0.7   0:01.37 nm-applet                                                                                                                                                                       
 3208 maddog    20   0  581m 134m  28m S    0  6.7   0:29.98 firefox                                                                                                                                                                         
 3358 maddog    20   0  212m  15m 9.9m S    0  0.8   0:00.76 gnome-terminal                                                                                                                                                                  
    1 root      20   0 19452 1804 1196 S    0  0.1   0:00.51 init                                                                                                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                                                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.10 ksoftirqd/0                                                                                                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                                                                                     
    7 root      15  -5     0    0    0 S    0  0.0   0:00.22 ksoftirqd/1                                                                                                                                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                                                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.01 events/0                                                                                                                                                                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.01 events/1                                                                                                                                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                                                                                          
   12 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                                                                                         
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 netns                                                                                                                                                                           
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 async/mgr                                                                                                                                                                       
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                                                                                                                                   
   16 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                                                                                                                                                                   
   17 root      15  -5     0    0    0 S    0  0.0   0:00.01 kblockd/0                                                                                                                                                                       
   18 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                                                                                                       
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                                                                                          
   20 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                                                                                    
   21 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                                                                                                                                                   
   22 root      15  -5     0    0    0 S    0  0.0   0:00.11 ata/0                                                                                                                                                                           
   23 root      15  -5     0    0    0 S    0  0.0   0:00.22 ata/1                                                                                                                                                                           
   24 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                                                                                         
   25 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                                                                                   
   26 root      15  -5     0    0    0 S    0  0.0   0:00.01 khubd                                                                                                                                                                           
   27 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                                                                                                         
   28 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmmcd                                                                                                                                                                           
   29 root      15  -5     0    0    0 S    0  0.0   0:00.00 bluetooth                                                                                                                                                                       
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd                                                                                                                                                                      
   31 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                                                                                                         
   33 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                                                                                                         
   34 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                                                                                           
   35 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                                                                                           
   36 root      15  -5     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                                                                                                                                                 
   37 root      15  -5     0    0    0 S    0  0.0   0:00.00 crypto/0                                                                                                                                                                        
   38 root      15  -5     0    0    0 S    0  0.0   0:00.00 crypto/1                                                                                                                                                                        
   47 root      15  -5     0    0    0 S    0  0.0   0:00.01 scsi_eh_0                                                                                                                                                                       
   48 root      15  -5     0    0    0 S    0  0.0   0:00.01 scsi_eh_1                                                                                                                                                                       
   51 root      15  -5     0    0    0 S    0  0.0   0:00.01 scsi_eh_2                                                                                                                                                                       
   52 root      15  -5     0    0    0 S    0  0.0   0:00.02 scsi_eh_3                                                                                                                                                                       
   56 root      15  -5     0    0    0 S    0  0.0   0:00.54 scsi_eh_4                                                                                                                                                                       
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                                                                                                                                       
   68 root      15  -5     0    0    0 S    0  0.0   0:00.00 kstriped                                                                                                                                                                        
   69 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmpathd/0                                                                                                                                                                       
   70 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmpathd/1                                                                                                                                                                       
   71 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd                                                                                                                                                                 
   72 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksnapd                                                                                                                                                                          
   73 root      15  -5     0    0    0 S    0  0.0   0:00.03 kondemand/0                                                                                                                                                                     
   74 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/1                                                                                                                                                                     
   75 root      15  -5     0    0    0 S    0  0.0   0:00.00 kconservative/0                                                                                                                                                                 
   76 root      15  -5     0    0    0 S    0  0.0   0:00.00 kconservative/1                                                                                                                                                                 
   77 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd                                                                                                                                                                        

I am only a single user

---

### Post by the8thstar on 2010-01-14
unhide is a false positive. Update your definitions and it will go away.

---

### Post by cariboo on 2010-01-14
If you think you've been hacked, why not check /var/log/auth.log, and see if anything stands out. Just because your cpu's were running at 25%, really means nothing, and it isn't a very good indication you where hacked. Your top output looks normal. I would suggest you type:

```
netstat tnlp
```

to see if you have any services you don't recognize that are listening.

---

