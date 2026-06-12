---
title: "successful su for a-user by root"
date: 2009-11-23
forum: Security
---

### Post by peterroots on 2009-11-23
I am running Kubuntu9.10
while looking for another issue I noticed my auth.log file was filling up with lines like this

Nov 23 12:11:34 PeterLT su[32643]: Successful su for peter by root
Nov 23 12:11:34 PeterLT su[32643]: + ??? root:peter
Nov 23 12:11:34 PeterLT su[32643]: pam_unix(su:session): session opened for user peter by (uid=0)
Nov 23 12:11:34 PeterLT su[32643]: pam_unix(su:session): session closed for user peter
Nov 23 12:11:51 PeterLT su[32671]: Successful su for peter by root
Nov 23 12:11:51 PeterLT su[32671]: + ??? root:peter
Nov 23 12:11:51 PeterLT su[32671]: pam_unix(su:session): session opened for user peter by (uid=0)
Nov 23 12:11:51 PeterLT su[32671]: pam_unix(su:session): session closed for user peter
Nov 23 12:12:07 PeterLT su[32699]: Successful su for peter by root
Nov 23 12:12:07 PeterLT su[32699]: + ??? root:peter
Nov 23 12:12:07 PeterLT su[32699]: pam_unix(su:session): session opened for user peter by (uid=0)
Nov 23 12:12:07 PeterLT su[32699]: pam_unix(su:session): session closed for user peter
Nov 23 12:12:24 PeterLT su[32728]: Successful su for peter by root
Nov 23 12:12:24 PeterLT su[32728]: + ??? root:peter
Nov 23 12:12:24 PeterLT su[32728]: pam_unix(su:session): session opened for user peter by (uid=0)
Nov 23 12:12:24 PeterLT su[32728]: pam_unix(su:session): session closed for user peter
Nov 23 12:12:41 PeterLT su[32763]: Successful su for peter by root
Nov 23 12:12:41 PeterLT su[32763]: + ??? root:peter
Nov 23 12:12:41 PeterLT su[32763]: pam_unix(su:session): session opened for user peter by (uid=0)
Nov 23 12:12:41 PeterLT su[32763]: pam_unix(su:session): session closed for user peter

I first thought it may relate to a download by DownThemAll in firefox but I was getting the same yesterday when I was not dowloading anything.
Is this normal behaviour?
If so can anyone tell my why root is su-ing to me for fractions of a second at a time?
I have never noticed this behaviour before (but then again I have never looked for it before either)
Any help or comments would be welcomed

---

### Post by cdenley on 2009-11-23
I've never seen that before. Every 17 seconds, something running as root su's to peter. Is it still running? I would try to figure out what process might be doing that. I would be concerned if I found that in auth.log. I don't think an ubuntu script/daemon would su to your user that often.
```

sudo ps -fu 0
sudo netstat -tulnp
sudo netstat -tunp

```

---

### Post by peterroots on 2009-11-23
Yes it is still happening though now I am at home my wireless network and before i was at work on a wired network
```

peter@PeterLT:~$ sudo ps -fu 0
[sudo] password for peter:    
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 18:12 ?        00:00:01 /sbin/init
root         2     0  0 18:12 ?        00:00:00 [kthreadd]
root         3     2  0 18:12 ?        00:00:00 [migration/0]
root         4     2  0 18:12 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 18:12 ?        00:00:00 [watchdog/0] 
root         6     2  0 18:12 ?        00:00:00 [events/0]   
root         7     2  0 18:12 ?        00:00:00 [cpuset]     
root         8     2  0 18:12 ?        00:00:00 [khelper]    
root         9     2  0 18:12 ?        00:00:00 [netns]      
root        10     2  0 18:12 ?        00:00:00 [async/mgr]  
root        11     2  0 18:12 ?        00:00:00 [kintegrityd/0]
root        12     2  0 18:12 ?        00:00:00 [kblockd/0]    
root        13     2  0 18:12 ?        00:00:00 [kacpid]       
root        14     2  0 18:12 ?        00:00:00 [kacpi_notify] 
root        15     2  0 18:12 ?        00:00:00 [kacpi_hotplug]
root        16     2  0 18:12 ?        00:00:00 [ata/0]        
root        17     2  0 18:12 ?        00:00:00 [ata_aux]      
root        18     2  0 18:12 ?        00:00:00 [ksuspend_usbd]
root        19     2  0 18:12 ?        00:00:00 [khubd]        
root        20     2  0 18:12 ?        00:00:00 [kseriod]      
root        21     2  0 18:12 ?        00:00:00 [kmmcd]        
root        22     2  0 18:12 ?        00:00:00 [bluetooth]    
root        23     2  0 18:12 ?        00:00:00 [khungtaskd]   
root        24     2  0 18:12 ?        00:00:00 [pdflush]      
root        25     2  0 18:12 ?        00:00:00 [pdflush]      
root        26     2  0 18:12 ?        00:00:00 [kswapd0]      
root        27     2  0 18:12 ?        00:00:00 [aio/0]        
root        28     2  0 18:12 ?        00:00:00 [ecryptfs-kthrea]
root        29     2  0 18:12 ?        00:00:00 [crypto/0]       
root        33     2  0 18:12 ?        00:00:00 [scsi_eh_0]      
root        34     2  0 18:12 ?        00:00:00 [scsi_eh_1]      
root        36     2  0 18:12 ?        00:00:00 [kstriped]       
root        37     2  0 18:12 ?        00:00:00 [kmpathd/0]      
root        38     2  0 18:12 ?        00:00:00 [kmpath_handlerd]
root        39     2  0 18:12 ?        00:00:00 [ksnapd]         
root        40     2  0 18:12 ?        00:00:00 [kondemand/0]    
root        41     2  0 18:12 ?        00:00:00 [kconservative/0]
root        42     2  0 18:12 ?        00:00:00 [krfcommd]       
root       309     2  0 18:12 ?        00:00:00 [usbhid_resumer] 
root       348     2  0 18:12 ?        00:00:00 [kjournald]      
root       413     1  0 18:12 ?        00:00:00 upstart-udev-bridge --daemon
root       416     1  0 18:12 ?        00:00:00 udevd --daemon              
root       611     2  0 18:12 ?        00:00:00 [ktoshkeyd]                 
root       635     2  0 18:12 ?        00:00:00 [kpsmoused]                 
root       672     2  0 18:12 ?        00:00:00 [pccardd]                   
root       673     2  0 18:12 ?        00:00:00 [pccardd]                   
root       677     2  0 18:12 ?        00:00:00 [ipw2200/0]                 
root       727     2  0 18:12 ?        00:00:00 [scsi_eh_2]                 
root      1002     2  0 18:14 ?        00:00:00 [kjournald]                 
root      1007     2  0 18:15 ?        00:00:00 [kjournald]                 
root      1057     1  0 18:15 ?        00:00:00 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
root      1118     1  0 18:15 ?        00:00:00 kdm                                           
root      1167     1  0 18:15 ?        00:00:00 /usr/sbin/console-kit-daemon                  
root      1188     1  0 18:15 ?        00:00:00 NetworkManager                                
root      1254     1  0 18:15 ?        00:00:00 /usr/sbin/modem-manager                       
root      1264  1117  0 18:15 ?        00:00:00 hald-runner                                   
root      1265  1118  5 18:15 tty7     00:00:20 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-
root      1283     1  0 18:15 tty4     00:00:00 /sbin/getty -8 38400 tty4                                    
root      1290     1  0 18:15 tty5     00:00:00 /sbin/getty -8 38400 tty5                                    
root      1296     1  0 18:15 tty2     00:00:00 /sbin/getty -8 38400 tty2                                    
root      1297     1  0 18:15 tty3     00:00:00 /sbin/getty -8 38400 tty3                                    
root      1299     1  0 18:15 tty6     00:00:00 /sbin/getty -8 38400 tty6                                    
root      1303     1  0 18:15 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket           
root      1314     1  0 18:15 ?        00:00:00 cron                                                         
root      1350     1  0 18:15 ?        00:00:00 /sbin/wpa_supplicant -u -s                                   
root      1369  1264  0 18:15 ?        00:00:00 /usr/lib/hal/hald-addon-ipw-killswitch                       
root      1397   416  0 18:15 ?        00:00:00 udevd --daemon                                               
root      1452  1264  0 18:15 ?        00:00:00 /usr/lib/hal/hald-addon-generic-backlight                    
root      1456  1264  0 18:15 ?        00:00:00 /usr/lib/hal/hald-addon-generic-backlight                    
root      1568  1264  0 18:15 ?        00:00:00 hald-addon-input: Listening on /dev/input/event2 /dev/input/e
root      1621  1264  0 18:15 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq                              
root      1697  1264  0 18:15 ?        00:00:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)           
root      2092   416  0 18:15 ?        00:00:00 udevd --daemon                                               
root      2094  1118  0 18:15 ?        00:00:00 -:0
root      2149     1  0 18:15 ?        00:00:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      2418     1  0 18:15 ?        00:00:00 dbus-launch --autolaunch 84a761edfb0fc8b81cbaefbb4a1fc89b --b
root      2419     1  0 18:15 ?        00:00:00 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --ses
root      2424     1  0 18:15 tty1     00:00:00 /sbin/getty -8 38400 tty1
root      2808     1  0 18:16 ?        00:00:00 /usr/lib/policykit-1/polkitd
root      2956  1188  0 18:16 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.
root      9536  9003  2 18:21 pts/3    00:00:00 ps -fu 0

```
```

peter@PeterLT:~$ sudo netstat -tulnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:56128           0.0.0.0:*               LISTEN      1046/rpc.statd
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      1024/portmap
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      2149/cupsd
tcp        0      0 127.0.0.1:32473         0.0.0.0:*               LISTEN      2828/gdl_indexer
tcp6       0      0 ::1:631                 :::*                    LISTEN      2149/cupsd
udp        0      0 127.0.0.1:34752         0.0.0.0:*                           2718/skype.real
udp        0      0 0.0.0.0:68              0.0.0.0:*                           2956/dhclient
udp        0      0 0.0.0.0:56905           0.0.0.0:*                           1046/rpc.statd
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1108/avahi-daemon:
udp        0      0 0.0.0.0:111             0.0.0.0:*                           1024/portmap
udp        0      0 0.0.0.0:631             0.0.0.0:*                           2149/cupsd
udp        0      0 0.0.0.0:52252           0.0.0.0:*                           1108/avahi-daemon:
udp        0      0 0.0.0.0:798             0.0.0.0:*                           1046/rpc.statd

```
```

peter@PeterLT:~$ sudo netstat -tunp
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address

```

Does any of this help, I can not see anything obvious?

---

### Post by cdenley on 2009-11-23
Are you running an NFS server? Is it accessible from the internet?

```

sudo lsof -p 2418
sudo lsof -p 2419

```

---

### Post by peterroots on 2009-11-23
No NFS though I was linking (until a few days ago) to a nfs share on another machine.  nfs common is installed but not the server


```
peter@PeterLT:/var/log$ sudo lsof -p 2418
[sudo] password for peter:               
COMMAND    PID USER   FD   TYPE     DEVICE SIZE/OFF   NODE NAME
dbus-laun 2418 root  cwd    DIR        8,1     4096      2 /   
dbus-laun 2418 root  rtd    DIR        8,1     4096      2 /   
dbus-laun 2418 root  txt    REG        8,1    22132 515963 /usr/bin/dbus-launch
dbus-laun 2418 root  mem    REG        8,1    26400 282425 /lib/tls/i686/cmov/libnss_compat-2.10.1.so
dbus-laun 2418 root  mem    REG        8,1    42572 282427 /lib/tls/i686/cmov/libnss_files-2.10.1.so 
dbus-laun 2418 root  mem    REG        8,1   113320 261824 /lib/ld-2.10.1.so                         
dbus-laun 2418 root  mem    REG        8,1  1319364 282418 /lib/tls/i686/cmov/libc-2.10.1.so         
dbus-laun 2418 root  mem    REG        8,1   120380 515845 /usr/lib/libxcb.so.1.1.0                  
dbus-laun 2418 root  mem    REG        8,1  1233824 516843 /usr/lib/libX11.so.6.2.0                  
dbus-laun 2418 root  mem    REG        8,1    16628 517563 /usr/lib/libXdmcp.so.6.0.0                
dbus-laun 2418 root  mem    REG        8,1   116920 282432 /lib/tls/i686/cmov/libpthread-2.10.1.so   
dbus-laun 2418 root  mem    REG        8,1     9564 515788 /usr/lib/libXau.so.6.0.0                  
dbus-laun 2418 root  mem    REG        8,1    38504 282429 /lib/tls/i686/cmov/libnss_nis-2.10.1.so   
dbus-laun 2418 root  mem    REG        8,1     9736 282421 /lib/tls/i686/cmov/libdl-2.10.1.so        
dbus-laun 2418 root  mem    REG        8,1    79676 282424 /lib/tls/i686/cmov/libnsl-2.10.1.so       
dbus-laun 2418 root    0u   CHR        1,3      0t0   1201 /dev/null                                 
dbus-laun 2418 root    1u   CHR        1,3      0t0   1201 /dev/null                                 
dbus-laun 2418 root    2u   CHR        1,3      0t0   1201 /dev/null                                 
dbus-laun 2418 root    3u  unix 0xd71ba200      0t0   6638 socket                                    
dbus-laun 2418 root    4u   CHR        1,3      0t0   1201 /dev/null                                 
dbus-laun 2418 root    5u  unix 0xd71ea600      0t0   6657 socket
dbus-laun 2418 root    8r  FIFO        0,6      0t0   6644 pipe
peter@PeterLT:/var/log$ man lsof
peter@PeterLT:/var/log$ sudo lsof -p 2419
COMMAND    PID USER   FD   TYPE     DEVICE SIZE/OFF   NODE NAME
dbus-daem 2419 root  cwd    DIR        8,1     4096      2 /
dbus-daem 2419 root  rtd    DIR        8,1     4096      2 /
dbus-daem 2419 root  txt    REG        8,1   292728 228955 /bin/dbus-daemon
dbus-daem 2419 root  mem    REG        8,1    30684 282434 /lib/tls/i686/cmov/librt-2.10.1.so
dbus-daem 2419 root  mem    REG        8,1   157064 261682 /lib/libexpat.so.1.5.2
dbus-daem 2419 root  mem    REG        8,1  1319364 282418 /lib/tls/i686/cmov/libc-2.10.1.so
dbus-daem 2419 root  mem    REG        8,1    38504 282429 /lib/tls/i686/cmov/libnss_nis-2.10.1.so
dbus-daem 2419 root  mem    REG        8,1     9736 282421 /lib/tls/i686/cmov/libdl-2.10.1.so
dbus-daem 2419 root  mem    REG        8,1   104148 261744 /lib/libselinux.so.1
dbus-daem 2419 root  mem    REG        8,1   113320 261824 /lib/ld-2.10.1.so
dbus-daem 2419 root  mem    REG        8,1    42572 282427 /lib/tls/i686/cmov/libnss_files-2.10.1.so
dbus-daem 2419 root  mem    REG        8,1    79676 282424 /lib/tls/i686/cmov/libnsl-2.10.1.so
dbus-daem 2419 root  mem    REG        8,1    26400 282425 /lib/tls/i686/cmov/libnss_compat-2.10.1.so
dbus-daem 2419 root  mem    REG        8,1   116920 282432 /lib/tls/i686/cmov/libpthread-2.10.1.so
dbus-daem 2419 root    0u   CHR        1,3      0t0   1201 /dev/null
dbus-daem 2419 root    1u   CHR        1,3      0t0   1201 /dev/null
dbus-daem 2419 root    2u   CHR        1,3      0t0   1201 /dev/null
dbus-daem 2419 root    3u  unix 0xd7466600      0t0   6649 socket
dbus-daem 2419 root    4u   CHR        1,3      0t0   1201 /dev/null
dbus-daem 2419 root    5r   DIR       0,10        0      1 inotify
dbus-daem 2419 root    6u  unix 0xd76cba00      0t0   6650 socket
dbus-daem 2419 root    7u  unix 0xf6780c00      0t0   6651 socket
```

---

### Post by cdenley on 2009-11-23
I'm out of ideas for determining what is running "su". Maybe you check to see what it is running after switching to your user.
```

tail ~/.bash_history

```

---

### Post by peterroots on 2009-11-23
I have been trawling through various log files, learning quite a bit but nothing relevant to this problem so far.
I also tried running a tail -f on my auth.log along side a tail -f on messages after turning on full logging of ufw to see if any internet or network activity turned up at the same time as the su's - it didn't

---

### Post by PainAndDelight on 2009-12-07
I'm running Debian, but it might be the same problem, or this may help you debug it.  I noticed my hard disk writing every 2 seconds, and using "iotop -o" found that it was from syslog.  I guess syslog flushes the files (makes sense) so the write actually runs the hard disk. 
I changed su to be a script to record which process called it, which parent process, and list all the processes at that time so I could see the root.  Here is the code:

Contents of su script:
[FONT=Fixedsys]#!/bin/sh
FILE=/tmp/out
echo Parameters $* >> $FILE
echo Process $$ >> $FILE
cat /proc/$$/cmdline >> $FILE
echo >> $FILE
echo PProcess $PPID >> $FILE
cat /proc/$PPID/cmdline >> $FILE
echo >> $FILE
ps -eaf >> $FILE
echo "--------------" >> $FILE
exec /bin/su.real "$*"
[/FONT]
I wrote this file in my home directory, then chmod 755 it, and ran:
mv /bin/su /bin/su.real;cp ~/su /bin/su

Reading the file /tmp/out, you could see all the information you need.

My root problem was acpid calling some dcop messaging call to do who knows what.
I ran apt-get remove --purge acpid to remove it.

No more HD access.
Hope that helps!

---

### Post by bodhi.zazen on 2009-12-07
A better question, who is peter ?

---

### Post by peterroots on 2009-12-08
I did a completely fresh install (as running 9.10 as an upgrade from 9.04), to try and resolve some other issues (did not) but the frequency of the su has dropped.
A desktop I recently upgraded from 8.04 to 9.10 does not have the multiple su at all.

P&D - I tried your script, interesting when I copied it to bin it recorded some interesting stuff but the problem went away!
when i copied the real su back the problem returned - very odd

su is rws for root but your script was rwx so I though, maybe...? but changing permissions on su had no effect.

Interesting that you problem as acpid as one of my problems is temperature control (or lack of it since I upgraded) so maybe the two are related some how

---

