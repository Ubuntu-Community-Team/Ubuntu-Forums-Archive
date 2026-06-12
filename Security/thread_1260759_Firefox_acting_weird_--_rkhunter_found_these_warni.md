---
title: "Firefox acting weird -- rkhunter found these warnings"
date: 2009-09-07
forum: Security
---

### Post by didi32 on 2009-09-07
Hi, my laptop has been acting weirdly recently, especially Firefox. I must say that I have installed Ubuntuzilla a while ago to have Firefox 3.5.

But anyway, I'm logging all logins to a few websites that I manage (not on local machine but shared hosting) , and I noticed a few login accesses with my own username/password that I did not perform myself. My browser is also slow at times and I get the message that a script is running endlessly. When I load a page sometimes the Firefox window becomes gray for a moment, like freezing, before getting back to normal.

I've run rkhunter and got the following warnings:
 /usr/sbin/unhide                                         [ Warning ]
 /usr/sbin/unhide-linux26                                 [ Warning ]
 Checking if SSH root access is allowed                   [ Warning ]
 Checking /dev for suspicious file types                  [ Warning ]

I'm not sure what to do with these.

Not sure what to look for either, so please if you have ideas and recommendations.

---

### Post by cariboo on 2009-09-07
THose are false positives, that is normal when you run rkhunter.

I would suggest you run top to see if there is anything running that shouldn't be.

---

### Post by lovinglinux on 2009-09-08
Also visit [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567) to improve your Firefox experience.

---

### Post by unspawn on 2009-09-08
> **cariboo907 said:**
> THose are false positives, that is normal when you run rkhunter.
Only the "Checking /dev for suspicious file types" and what may be "normal" for you may no be normal for others. The documentation rkhunter comes with and the mailing list archives show the default action is not to run 'top' or something but to *check the rkhunter.log for details and act on those*.

---

### Post by didi32 on 2009-09-08
Hi unspawn,

Thanks for the advice. I'm running top, although not sure what shouldn't be in there. I'm looking up all the services running with names I don't recognize.

Thanks!

---

### Post by wojox on 2009-09-08
Post the output back here:

```
top -b -n 1 > top.out.$(date +%s)
```

---

### Post by didi32 on 2009-09-08
thanks wojox,

here is the output:
```

top - 09:07:21 up 21 min,  2 users,  load average: 0.73, 2.14, 1.41
Tasks: 144 total,   1 running, 143 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.3%us,  4.8%sy,  1.9%ni, 61.8%id,  7.6%wa,  0.2%hi,  0.3%si,  0.0%st
Mem:   3962408k total,  1958256k used,  2004152k free,   133436k buffers
Swap:  5638772k total,        0k used,  5638772k free,   737908k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4618 john      20   0  490m 155m  29m S    6  4.0   7:04.67 firefox-bin        
 4326 john      20   0  299m 6156 4448 S    2  0.2   0:08.23 pulseaudio         
 5560 john      20   0 1218m 494m  37m S    2 12.8   1:22.41 java               
    1 root      20   0  5244 2036  632 S    0  0.1   0:01.15 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.16 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.30 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0            
   13 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/1            
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      
   16 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   17 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   18 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
   20 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue             
   21 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0              
   22 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/1              
   23 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux            
   24 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd      
   25 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd              
   26 root      15  -5     0    0    0 S    0  0.0   0:00.09 kseriod            
   27 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmmcd              
   28 root      15  -5     0    0    0 S    0  0.0   0:00.00 btaddconn          
   29 root      15  -5     0    0    0 S    0  0.0   0:00.00 btdelconn          
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush            
   31 root      20   0     0    0    0 S    0  0.0   0:00.04 pdflush            
   32 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0            
   33 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0              
   34 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1              
   35 root      15  -5     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea    
   38 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0          
   39 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1          
   40 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2          
   41 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3          
   42 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4          
   43 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_5          
   44 root      15  -5     0    0    0 S    0  0.0   0:00.00 kstriped           
   45 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmpathd/0          
   46 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmpathd/1          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd    
   48 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksnapd             
   49 root      15  -5     0    0    0 S    0  0.0   0:00.02 kondemand/0        
   50 root      15  -5     0    0    0 S    0  0.0   0:00.02 kondemand/1        
   51 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd           
  731 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_6          
  733 root      15  -5     0    0    0 S    0  0.0   0:00.07 usb-storage        
  783 root      15  -5     0    0    0 S    0  0.0   0:00.17 kjournald          
  918 root      16  -4 16792  620  292 S    0  0.0   0:00.07 udevd              
 1681 root      15  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused          
 2781 root      20   0  3944  608  512 S    0  0.0   0:00.00 getty              
 2782 root      20   0  3944  600  512 S    0  0.0   0:00.00 getty              
 2789 root      20   0  3944  608  512 S    0  0.0   0:00.00 getty              
 2790 root      20   0  3944  608  512 S    0  0.0   0:00.00 getty              
 2791 root      20   0  3944  604  512 S    0  0.0   0:00.00 getty              
 2856 root      20   0  4604 1392  556 S    0  0.0   0:00.00 acpid              
 2895 syslog    20   0 12376  760  564 S    0  0.0   0:00.03 syslogd            
 2918 root      20   0  8204  620  504 S    0  0.0   0:00.04 dd                 
 2920 klog      20   0  6904 3588  456 S    0  0.1   0:00.09 klogd              
 2943 messageb  20   0 21876 1560  808 S    0  0.0   0:00.27 dbus-daemon        
 2967 root      20   0 48940 1172  648 S    0  0.0   0:00.00 sshd               
 2990 dictd     20   0 34000 4928 4568 S    0  0.1   0:00.01 dictd              
 3496 Debian-e  20   0 48020 1072  648 S    0  0.0   0:00.00 exim4              
 3533 root      20   0 60860 1672 1064 S    0  0.0   0:00.02 nmbd               
 3537 root      20   0 83512 2736 1928 S    0  0.1   0:00.00 smbd               
 3563 root      20   0 83512 1200  392 S    0  0.0   0:00.00 smbd               
 3613 root      20   0 66292 1576  916 S    0  0.0   0:00.00 winbindd           
 3635 haldaemo  20   0 36536 5224 4088 S    0  0.1   0:01.37 hald               
 3638 root      20   0  104m 2752 1836 S    0  0.1   0:00.04 console-kit-dae    
 3701 root      20   0 15816 1260 1016 S    0  0.0   0:00.08 hald-runner        
 3730 root      20   0 28484 2380 2076 S    0  0.1   0:00.02 hald-addon-dell    
 3731 root      20   0 66292 1308  648 S    0  0.0   0:00.00 winbindd           
 3735 root      20   0 28484 2076 1796 S    0  0.1   0:00.06 hald-addon-inpu    
 3776 root      20   0 28484 2060 1784 S    0  0.1   0:00.12 hald-addon-stor    
 3778 root      20   0 28484 2148 1868 S    0  0.1   0:00.10 hald-addon-stor    
 3811 root      20   0 28492 2044 1768 S    0  0.1   0:00.00 hald-addon-cpuf    
 3812 haldaemo  20   0 32392 2040 1748 S    0  0.1   0:00.00 hald-addon-acpi    
 3817 root      20   0  120m 2044 1048 S    0  0.1   0:00.00 gdm                
 3822 root      20   0  140m 3604 2396 S    0  0.1   0:00.01 gdm                
 3825 root      20   0  568m  97m  19m S    0  2.5   2:25.01 Xorg               
 3850 root      20   0 70840 3116 2360 S    0  0.1   0:00.40 NetworkManager     
 3867 root      20   0 21100 2260 1828 S    0  0.1   0:00.07 wpa_supplicant     
 3877 avahi     20   0 31888 1544 1248 S    0  0.0   0:00.00 avahi-daemon       
 3878 avahi     20   0 31764  540  300 S    0  0.0   0:00.00 avahi-daemon       
 3880 root      20   0 68976 3460 2784 S    0  0.1   0:00.01 nm-system-setti    
 3912 root      20   0 67960 2548 1716 S    0  0.1   0:00.00 cupsd              
 3938 root      20   0 33296 1236  952 S    0  0.0   0:00.00 system-tools-ba    
 4017 daemon    20   0 16524  456  304 S    0  0.0   0:00.00 atd                
 4045 root      20   0 19972 1116  836 S    0  0.0   0:00.00 cron               
 4222 root      20   0  3944  604  512 S    0  0.0   0:00.00 getty              
 4249 john      20   0 84092 3324 2504 S    0  0.1   0:00.03 gnome-keyring-d    
 4262 john      20   0  170m 8372 6076 S    0  0.2   0:00.16 x-session-manag    
 4317 john      20   0 35940  684  268 S    0  0.0   0:00.00 ssh-agent          
 4320 john      20   0 23824  724  444 S    0  0.0   0:00.00 dbus-launch        
 4321 john      20   0 21788 1468  656 S    0  0.0   0:00.34 dbus-daemon        
 4327 john      20   0 68048 3080 2432 S    0  0.1   0:00.00 gconf-helper       
 4329 john      20   0 46176 6060 2328 S    0  0.2   0:00.40 gconfd-2           
 4347 john      20   0  161m 7608 4684 S    0  0.2   0:00.09 seahorse-agent     
 4350 john      20   0 40852 2340 1928 S    0  0.1   0:00.01 gvfsd              
 4360 john      20   0  259m  20m  12m S    0  0.5   0:00.93 gnome-settings-    
 4363 john      20   0 71000 2632 1964 S    0  0.1   0:00.00 gvfs-fuse-daemo    
 4375 john      20   0  4024  644  504 S    0  0.0   0:00.00 compiz             
 4438 john      20   0  233m  28m 7536 S    0  0.7   0:05.45 compiz.real        
 4439 john      20   0  328m  28m  16m S    0  0.7   0:05.28 gnome-panel        
 4441 john      20   0  447m  24m  16m S    0  0.6   0:01.78 nautilus           
 4443 john      20   0  148m 4048 2944 S    0  0.1   0:00.09 bonobo-activati    
 4446 john      20   0  351m  14m  10m S    0  0.4   0:00.14 evolution-alarm    
 4450 john      20   0  144m 8136 6272 S    0  0.2   0:00.05 bluetooth-apple    
 4456 john      20   0  211m  18m 9016 S    0  0.5   0:00.26 python             
 4459 john      20   0  187m  15m 8948 S    0  0.4   0:00.38 nm-applet          
 4462 john      20   0  233m  18m  12m S    0  0.5   0:00.32 update-notifier    
 4463 john      20   0  224m  10m 6832 S    0  0.3   0:00.12 gnome-power-man    
 4468 john      20   0  171m  16m  10m S    0  0.4   0:01.45 notify-osd         
 4470 john      20   0 45316 2976 2400 S    0  0.1   0:00.00 gvfsd-trash        
 4476 john      20   0  210m  12m 8240 S    0  0.3   0:00.15 trashapplet        
 4478 john      20   0 80740 4328 3200 S    0  0.1   0:00.02 gvfs-hal-volume    
 4483 john      20   0 54504 3692 2604 S    0  0.1   0:00.02 gvfs-gphoto2-vo    
 4544 john      20   0  236m  18m  12m S    0  0.5   0:00.27 fast-user-switc    
 4547 john      20   0  220m  14m 9120 S    0  0.4   0:00.34 indicator-apple    
 4548 john      20   0  259m  19m  12m S    0  0.5   0:00.28 mixer_applet2      
 4552 john      20   0 40856 2420 2016 S    0  0.1   0:00.00 gvfsd-burn         
 4554 john      20   0  4024  576  480 S    0  0.0   0:00.00 sh                 
 4555 john      20   0  4024  604  492 S    0  0.0   0:00.00 compiz-decorato    
 4557 john      20   0  166m  13m 9640 S    0  0.3   0:01.23 gtk-window-deco    
 4598 root      20   0  6488 1064  896 S    0  0.0   0:00.00 dhclient           
 4602 john      20   0  4024  608  504 S    0  0.0   0:00.00 firefox            
 4614 john      20   0  4024  624  500 S    0  0.0   0:00.00 run-mozilla.sh     
 4702 john      20   0  158m 3696 1872 S    0  0.1   0:01.60 gnome-screensav    
 4729 john      20   0  340m  14m  10m S    0  0.4   0:00.08 evolution-excha    
 4739 john      20   0  379m  10m 7820 S    0  0.3   0:00.04 evolution-data-    
 4866 john      20   0  694m  50m  22m S    0  1.3   0:04.33 pidgin             
 5543 john      20   0 10492  948  784 S    0  0.0   0:00.00 eclipse            
 6044 root      20   0 72664  10m 4072 S    0  0.3   0:00.09 system-service-    
19402 john      20   0  196m  17m  11m S    0  0.5   0:00.29 gnome-terminal     
19403 john      20   0 14412  780  636 S    0  0.0   0:00.00 gnome-pty-helpe    
19404 john      20   0 20908 3716 1528 S    0  0.1   0:00.09 bash               
19435 john      20   0 19112 1228  892 R    0  0.0   0:00.01 top                


```

---

### Post by didi32 on 2009-09-08
I'm using Boot-Up manager to take a look at the services that are running at startup. I'm just wondering, could I just uncheck ssh so that it doesn't start? I have no need to access the computer remotely, or to have someone else do so.

---

### Post by wojox on 2009-09-08
I don't see anything running thats out of the ordinary.

---

### Post by wojox on 2009-09-08
I add this to hosts.allow:

```
ALL : 192.168.1.0/255.255.254.0
```

That way I can access my server from inside the Lan.

---

### Post by didi32 on 2009-09-08
so what this will do is allow all IPs ranging from 192.168.1.0 to 255.255.254.0?

---

### Post by wojox on 2009-09-08
192.168.1.0 / 255

---

