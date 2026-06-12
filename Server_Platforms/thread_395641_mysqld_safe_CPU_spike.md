---
title: "mysqld_safe CPU spike"
date: 2007-03-28
forum: Server Platforms
---

### Post by theaxis69 on 2007-03-28
The problem I'm having is the mysqld_safe process is taking up all spare cpu cycles. I haven't changed any of the mysql default settings, just went through the standard install of MythTv and associated packages through synaptic. Any ideas? This is on 7.04 with mysql 5
I should add that the mysqld_safe process takes up all spare CPU cycles whether I'm running the MythTV Frontend or not. There should be nothing using mysql on my system until I start MythTV. mysqld_safe just wants to grab as much CPU time as it can, even when it doesn't need it and should be sleeping.

---

### Post by theaxis69 on 2007-03-28
output from top:

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                               
 6391 root      28   3  1716  540  444 R 95.5  0.1   1303:37 mysqld_safe                                                           
 5327 root      15   0  312m 254m 9108 S  2.7 25.2   8:26.35 Xorg                                                                  
11442 alan      15   0 60112  23m  12m S  1.7  2.3   1:12.61 gnome-system-mo                                                       
 8589 alan      15   0 37880  18m 5336 S  0.3  1.8   0:42.32 compiz.real                                                           
    1 root      18   0  2908 1844  524 S  0.0  0.2   0:01.27 init                                                                  
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                           
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                           
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                            
    5 root      10  -5     0    0    0 S  0.0  0.0   0:01.00 events/0                                                              
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                               
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                                               
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                                                             
   31 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                          
  152 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kseriod                                                               
  177 root      22   0     0    0    0 S  0.0  0.0   0:00.17 pdflush                                                               
  178 root      15   0     0    0    0 S  0.0  0.0   0:00.32 pdflush                                                               
  179 root      10  -5     0    0    0 S  0.0  0.0   0:00.25 kswapd0                                                               
  180 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                 
 1994 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                         
 1995 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                 
 2015 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                 
 2016 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                               
 2020 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                              
 2246 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                           
 2437 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 reiserfs/0                                                            
 2636 root      21  -4  2816 1184  368 S  0.0  0.1   0:00.30 udevd                                                                 
 3582 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd                                                            
 3602 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                             
 3783 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 ivtv_vbi/0                                                            
 3784 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 ivtv_yuv/0                                                            
 3917 root      10  -5     0    0    0 S  0.0  0.0   0:00.14 msp34xx                                                               
 4276 dhcp      22  -2  2456  836  508 S  0.0  0.1   0:00.00 dhclient3                                                             
 4440 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 xfslogd/0                                                             
 4441 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 xfsdatad/0                                                            
 4444 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 xfsbufd                                                               
 4445 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 xfssyncd                                                              
 4674 root      18   0  1648  508  440 S  0.0  0.0   0:00.00 getty                                                                 
 4675 root      18   0  1648  508  440 S  0.0  0.0   0:00.00 getty

---

### Post by pnotequalsnp on 2007-09-11
Same problem here with mythtv and mysqld_safe process.  Any solutions?

---

### Post by pnotequalsnp on 2007-09-13
FYI, I killed the process and rebooted.  All works well now, how about you?

---

### Post by AirLace on 2008-01-01
This might be caused by low disk space. If so, please file a bug in the distribution's bug tracker and mark it with a high priority. In fact, file a bug even if this isn't the case. Thanks!

---

### Post by eeried on 2008-01-04
Same problem here.

I disabled tracker some time before even installing LAMP (local server only).

Tracker, to me, is a bug in itself, it means installing ubuntu on older machines impossible. ah well

Plenty of space on disk!

---

### Post by dfidler on 2008-05-11
I'm seeing this to except that I'm just running LAMP (no MythTV).  

Do we know what the problem is because I can't just bounce the box as it's a commercial site.

---

### Post by dlehman on 2008-05-15
dfidler I don't know if you found a solution yet but I had the same problem with a slandered server setup no mythtv.  I run a small site nothing commercial but I don't like to reboot it will mess up my uprecords.  anyway the solution 

```
 sudo /etc/init.d/mysql stop
```

```
 sudo killall mysqld_safe
```

```
 sudo /etc/init.d/mysql start
```


the database will be down for less then 30 sec do it during low traffic time and no one should notice if you haven't already rebooted.  

currently mysqld_safe is sleeping hopefully this fixes it we will wait and see.

I will post back if it spikes again, let me know if it works for you

dlehman

---

### Post by bvidinli on 2008-06-06
last one worked for mee too..

i had same problem,
i did:

/etc/init.d/mysql stop
killall mysqld_safe
killall mysqld_safe

/etc/init.d/mysql start



now, everything seems normal.
i dont know original cause of problem... i did not reboot my machine..
i dont know if this will repeat after reboot...

---

