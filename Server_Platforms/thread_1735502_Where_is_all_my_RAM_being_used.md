---
title: "Where is all my RAM being used?"
date: 2011-04-21
forum: Server Platforms
---

### Post by LingaringBell on 2011-04-21
Hello everyone

I have a server that is running Ubuntu 8.04 TLS server 64 bit.  It has 26 GBs of memory in it.  The server hosts vmware server 2.0.2 (I'm suspecting this is somehow the culprit) and runs 7 guests consisting of Windows 2003 servers and some Linux distros.  They are set to use 14 GBs of memory.  However, something is slowly using up all the available RAM on the server and I can't figure out what.  If I run top I get this:

This is slightly hard to read in this format so I bolded the memory %'s of the top few

```
top - 11:28:34 up 28 days, 18:34,  1 user,  load average: 3.22, 3.14, 3.35
Tasks: 185 total,   1 running, 184 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.0%us, 12.9%sy,  0.0%ni, 82.5%id,  0.9%wa,  0.3%hi,  0.4%si,  0.0%st
Mem:  24725712k total, 23219564k used,  1506148k free,    85704k buffers
Swap:  3229024k total,        0k used,  3229024k free, 21788192k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                           
 7207 root      20   0 1955m 161m 115m S  135  **0.7**  15432:30 vmware-vmx                                                                                                                                                                         
 7223 root      20   0 1899m  99m  52m S   22  **0.4**   4832:15 vmware-vmx                                                                                                                                                                         
 7234 root      20   0  843m 587m 575m S   17  **2.4**   5354:34 vmware-vmx                                                                                                                                                                         
 7248 root      20   0 1930m 1.3g 1.3g S   14  **5.7**   3508:49 vmware-vmx                                                                                                                                                                         
 7264 root      20   0 2020m 171m  64m S   11  **0.7**   3505:08 vmware-vmx                                                                                                                                                                         
 7292 root      20   0 1356m 1.1g 1.0g S    7  **4.5**   2708:18 vmware-vmx                                                                                                                                                                         
 7280 root      20   0  648m 407m 394m S    2  **1.7**   1072:49 vmware-vmx                                                                                                                                                                         
 4354 root      20   0 18996 1320  924 R    0  0.0   0:00.23 top                                                                                                                                                                                
 7011 root      20   0  141m  65m  19m S    0  0.3 112:39.15 vmware-hostd                                                                                                                                                                       
    1 root      20   0  4024  892  604 S    0  0.0   0:03.19 init                                                                                                                                                                               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                                                                           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.06 migration/0                                                                                                                                                                        
    4 root      15  -5     0    0    0 S    0  0.0   0:54.56 ksoftirqd/0                                                                                                                                                                        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                                                                                         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/1                                                                                                                                                                        
    7 root      15  -5     0    0    0 S    0  0.0   0:03.31 ksoftirqd/1                                                                                                                                                                        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                                                                                         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/2                                                                                                                                                                        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.36 ksoftirqd/2                                                                                                                                                                        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2                                                                                                                                                                         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/3                                                                                                                                                                        
   13 root      15  -5     0    0    0 S    0  0.0   0:00.12 ksoftirqd/3                                                                                                                                                                        
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3                                                                                                                                                                         
   15 root      RT  -5     0    0    0 S    0  0.0   0:00.20 migration/4                                                                                                                                                                        
   16 root      15  -5     0    0    0 S    0  0.0   0:10.48 ksoftirqd/4                                                                                                                                                                        
   17 root      RT  -5     0    0    0 S    0  0.0   0:00.02 watchdog/4                                                                                                                                                                         
   18 root      RT  -5     0    0    0 S    0  0.0   0:00.16 migration/5                                                                                                                                                                        
   19 root      15  -5     0    0    0 S    0  0.0   0:08.70 ksoftirqd/5  
```



Unless I'm reading this wrong, the server says it is using 25 GBs of RAM, but the running processes are only using about 17%  If I reboot the server memory usage goes back down to where it should be but then slowly climbs back to this state.  Anyone have any ideas?  Thanks!

---

### Post by ChipOManiac on 2011-04-21
It Says «vmware-vmx» for the processes you highlighted... are you using any virtual machines (running another OS on your current one)?

---

### Post by LingaringBell on 2011-04-21
Yup, like i said, the server hosts vmware server 2.0.2 and runs 7 guests consisting of Windows 2003 servers and some Linux distros.

---

### Post by ~Plue on 2011-04-21
> Mem:  24725712k total, 23219564k used,  1506148k free,    85704k buffers
its including the space taken by disk caching (which shouldn't be a problem)
what does *free -m* show?

---

### Post by LingaringBell on 2011-04-21
Hmm, I don't think so because free gives the same information:

```
             total       used       free     shared    buffers     cached
Mem:         24146      22694       1452          0         87      21294
-/+ buffers/cache:       1311      22834
Swap:         3153          0       3153
```

---

### Post by SeijiSensei on 2011-04-21
Linux always uses most of the available memory.  Whatever isn't dedicated to processes is used for disk caching.  That's what the "cache" figure reports.

Are you seeing some problem with performance that makes you concerned about memory usage?

---

### Post by ~Plue on 2011-04-21
take look at the -/+ buffers/cache line, thats the ram used by the applications you're running. 

cached memory is available to the applications on the fly, so you shouldn't worry too much about running out of ram in this case.
a brief explanation can be found [here]("http://www.linuxatemyram.com/") and [here]("http://egloo.wordpress.com/2008/10/29/linux-cached-memory/")

[ ]("http://www.linuxatemyram.com/")

---

### Post by LingaringBell on 2011-04-21
AAh, that makes more sense! Thanks!  I am seeing some performance issues.  The 5 minute load average on the server while running the 7 guests is about 3.  If I turn on one more guest (I've tried many different guests) suddenly the load jumps to around 10-20.  I was thinking that some sort of memory loop could be causing this.

---

### Post by SeijiSensei on 2011-04-21
It's more likely a horsepower problem.  It could be CPU, but I'm guessing it's contention over the disks.

You might see a short-term jump in load average as the next server starts up, but you should see it fall back to a reasonable level afterward.

What kind of drives are these?  With that many VMs I'd think you want at least [10K RPM]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007603+600003344&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=14&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=") drives, or maybe even [15Ks]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007603%20600003343&IsNodeId=1&bop=And&ShowDeactivatedMark=False&Order=PRICE&PageSize=100").  Are you using a RAID array?  RAIDs are slower for writing, but usually faster for reading.

---

### Post by LingaringBell on 2011-04-22
The load average does jump up but then doesn't fall back to a reasonable level.  I am using a software RAID 5 with 7200 RPM drives.  According to hdparm I'm getting good read speeds like you say:


/dev/md0:
 Timing cached reads:   14266 MB in  1.99 seconds = 7153.16 MB/sec
 Timing buffered disk reads:  872 MB in  3.00 seconds = 290.55 MB/sec


What is a good way to test the write speeds from the command line?  I've read that you can use dd but I haven't found many specifics about how.  It is probably a good theory to say that since it is a software RAID, the CPU just doesn't have the horsepower for all these reads/writes.  Thanks for the input.

---

### Post by iissmart on 2011-04-22
To test write speeds:

```
dd if=/dev/zero of=/raid/array/testfile bs=1M count=x
```

Where x is the number of MB you want to write. Read speeds are similar:

```
dd if=/raid/array/testfile of=/dev/null bs=1M
```

"if" and "of" mean "input file" and "output file". Try varying sizes when using the write test to make sure you get a good average.

---

### Post by LingaringBell on 2011-04-22
Thanks for the explanation.  I'm not sure if I'm doing this right though because I got some really high numbers.  My write looked like this:

dd if=/dev/zero of=/media/RAID5/test.txt bs=1M count=100
100+0 records in
100+0 records out
104857600 bytes (105 MB) copied, 0.132844 s, 789 MB/s

dd if=/dev/zero of=/media/RAID5/test.txt bs=1M count=1000
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 1.88809 s, 555 MB/s

dd if=/dev/zero of=/media/RAID5/test.txt bs=1M count=10000
10000+0 records in
10000+0 records out
10485760000 bytes (10 GB) copied, 94.9499 s, 110 MB/s

Then my read:

dd if=/media/RAID5/test.txt of=/dev/null bs=1M
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 0.199954 s, 5.2 GB/s

I'm  assuming the read is so fast because it isn't actually getting copied anywhere?  But what about the write speed, that seems really fast?

---

### Post by iissmart on 2011-04-22
Your commands look OK, I'm not sure how mdadm caches the files but since you have an incredibly high amount of RAM it's probably all being cached there. That means you can read at 5.2 GB/s from your RAM :)

If you've got the space, write a file that is a few gigs larger than your RAM, then try reading it back. Should see numbers closer to 100-200MB/s. That 10GB write looks normal, everything else looks like it just went into/out of RAM.

Take for example my hardware RAID-6 on a system with 2GB of RAM. Writes 1GB files at 332MB/s, reads it back at 876MB/s. Writes 3GB files at 289MB/s, reads it back at 304MB/s.

---

### Post by 1clue on 2011-04-22
Careful with that dd command for read speeds.

If the file has already been cached in RAM (read once in other words) then it will measure the speed of the read from disk cache to /dev/null, which will be too short.

I have a bunch of RAM too, and only a couple VMs.  The slow growing is your disk cache.  Linux caches anything your system reads in from the disk as long as there is memory, and after awhile you'll notice that disk access drops off unless you do a lot of writes.

If you add "noatime" to the options in /etc/fstab you will speed things up quite a bit, because for any access your system will try to write the access time to your drive for the file descriptor.  Noatime turns that off.  For a VM the guest OS will probably write access times on the files inside the virtual devices so you don't want that anyway.

Another thing, you probably want to put no more than a couple VMs on any spindle if they're running concurrently with a bunch of disk activity.  And use better drives too.

---

### Post by SeijiSensei on 2011-04-24
**bonnie++** is a highly-regarded disk testing utility.  It's in the repositories.

---

### Post by Dasoren on 2012-03-28
hi, I am some what new to RAM in linux. I have been using linux for about 3 years now, and most of the time with my on hardware, and lots of RAM, but I got a VPS from a Host, to host a TeamSpeak3 server for me that can be up 100% of the time and have a good network to the net. 

anyway, here is whats up, the server uses about 200-300MB of RAM, but now and then it uses up to 1GB, but lately it is using 1GB all the time. I have read alot about this and understand most of it, but I do not understand why it is using 1GB of RAM, when it should only be using 200-300MB, at most. 

here is the info from "ps -aux"

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23548  1664 ?        Ss   Feb26   0:06 init
root      1285  0.0  0.0  14760  1096 ?        Ss   Feb26   0:00 /usr/sbin/xinetd -dontfork -pidfile /var/run/xinetd.pid -stayalive -inetd_compat
root      1299  0.0  0.1  49424  2668 ?        Ss   Feb26   0:42 /usr/sbin/sshd -D
root      1313  0.0  0.0  18888  1016 ?        Ss   Feb26   0:14 cron
syslog    1335  0.0  0.0  12536   772 ?        Ss   Feb26   0:34 /sbin/syslogd -u syslog
root      1349  0.0  0.0   6712   648 ?        Ss   Feb26   3:59 /usr/sbin/vnstatd -d
root      1390  0.0  0.0  68268  2072 ?        Ss   Feb26   3:23 sendmail: MTA: accepting connections
root      1414  0.0  0.3 108572  7400 ?        Ss   Feb26   6:24 /usr/sbin/apache2 -k start
root      1478  0.0  0.0  22124  1712 ?        Ss   Feb26   0:00 SCREEN -S ts3serverdasoren
root      1479  0.0  0.1  18040  2116 pts/1    Ss   Feb26   0:00 /bin/bash
root      1500  0.0  0.0   4180   624 pts/1    S+   Feb26   0:00 /bin/sh ./ts3server_minimal_runscript.sh start inifile=ts3server.ini
root      1503  3.4  1.1 277540 24156 pts/1    Sl+  Feb26 1522:43 ./ts3server_linux_amd64 start inifile=ts3server.ini
root      1598  0.0  0.0  22124  1644 ?        Ss   Feb26   0:00 SCREEN -S minecraft
root      1599  0.0  0.1  18040  2100 pts/3    Ss+  Feb26   0:00 /bin/bash
root      3247  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3274  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3337  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3658  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3685  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3876  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      5495  0.0  0.2 108572  4584 ?        S    01:58   0:00 /usr/sbin/apache2 -k start
root      5747  0.0  0.2 108572  4584 ?        S    02:40   0:00 /usr/sbin/apache2 -k start
root      5762  0.0  0.2 108572  4584 ?        S    02:42   0:00 /usr/sbin/apache2 -k start
root      7904  1.4  2.5 1055924 53928 pts/4   Sl+  04:31   1:05 java -Xms10M -jar JTS3ServerMod.jar
root      9333  0.0  0.0  15064  1124 pts/0    R+   05:46   0:00 ps -aux
root      9424  0.0  0.1  70796  3472 ?        Ss   Mar23   0:04 sshd: root@pts/0
root      9436  0.0  0.1  18064  2144 pts/0    Ss   Mar23   0:00 -bash
root      9453  0.0  0.0  22124  1712 ?        Ss   Mar23   0:00 SCREEN -S ts3bot
root      9454  0.0  0.1  18088  2120 pts/4    Ss   Mar23   0:00 /bin/bash
root     29807  0.0  0.0  22128  1716 ?        Ss   Mar23   0:00 SCREEN -S ts3servermcrealm
root     29808  0.0  0.1  18092  2168 pts/5    Ss   Mar23   0:00 /bin/bash
root     30380  0.0  0.0   4180   624 pts/5    S+   Mar23   0:00 /bin/sh ./ts3server_minimal_runscript.sh start inifile=ts3server.ini
root     30383  2.7  0.4 198508  9836 pts/5    Sl+  Mar23 174:02 ./ts3server_linux_amd64 start inifile=ts3server.ini
root     30596  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root     32633  0.0  0.0  21860  1424 ?        Ss   Mar18   0:00 SCREEN -S mc
root     32634  0.0  0.1  18096  2164 pts/2    Ss+  Mar18   0:00 /bin/bash

and "free -m"

             total       used       free     shared    buffers     cached
Mem:          2048       1032       1015          0          0          0
-/+ buffers/cache:       1032       1015
Swap:            0          0          0


any ideas? as to why it is using so much RAM? it is a VPS with 2GB.

---

### Post by Dasoren on 2012-03-28
```

"free -m"

             total       used       free     shared    buffers     cached
Mem:          2048       1032       1015          0          0          0
-/+ buffers/cache:       1032       1015
Swap:            0          0          0

"ps -aux"

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23548  1664 ?        Ss   Feb26   0:06 init
root      1285  0.0  0.0  14760  1096 ?        Ss   Feb26   0:00 /usr/sbin/xinetd -dontfork -pidfile /var/run/xinetd.pid -stayalive -inetd_compat
root      1299  0.0  0.1  49424  2668 ?        Ss   Feb26   0:42 /usr/sbin/sshd -D
root      1313  0.0  0.0  18888  1016 ?        Ss   Feb26   0:14 cron
syslog    1335  0.0  0.0  12536   772 ?        Ss   Feb26   0:34 /sbin/syslogd -u syslog
root      1349  0.0  0.0   6712   648 ?        Ss   Feb26   3:59 /usr/sbin/vnstatd -d
root      1390  0.0  0.0  68268  2072 ?        Ss   Feb26   3:23 sendmail: MTA: accepting connections
root      1414  0.0  0.3 108572  7400 ?        Ss   Feb26   6:24 /usr/sbin/apache2 -k start
root      1478  0.0  0.0  22124  1712 ?        Ss   Feb26   0:00 SCREEN -S ts3serverdasoren
root      1479  0.0  0.1  18040  2116 pts/1    Ss   Feb26   0:00 /bin/bash
root      1500  0.0  0.0   4180   624 pts/1    S+   Feb26   0:00 /bin/sh ./ts3server_minimal_runscript.sh start inifile=ts3server.ini
root      1503  3.4  1.1 277540 24156 pts/1    Sl+  Feb26 1522:43 ./ts3server_linux_amd64 start inifile=ts3server.ini
root      1598  0.0  0.0  22124  1644 ?        Ss   Feb26   0:00 SCREEN -S minecraft
root      1599  0.0  0.1  18040  2100 pts/3    Ss+  Feb26   0:00 /bin/bash
root      3247  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3274  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3337  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3658  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3685  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3876  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      5495  0.0  0.2 108572  4584 ?        S    01:58   0:00 /usr/sbin/apache2 -k start
root      5747  0.0  0.2 108572  4584 ?        S    02:40   0:00 /usr/sbin/apache2 -k start
root      5762  0.0  0.2 108572  4584 ?        S    02:42   0:00 /usr/sbin/apache2 -k start
root      7904  1.4  2.5 1055924 53928 pts/4   Sl+  04:31   1:05 java -Xms10M -jar JTS3ServerMod.jar
root      9333  0.0  0.0  15064  1124 pts/0    R+   05:46   0:00 ps -aux
root      9424  0.0  0.1  70796  3472 ?        Ss   Mar23   0:04 sshd: root@pts/0
root      9436  0.0  0.1  18064  2144 pts/0    Ss   Mar23   0:00 -bash
root      9453  0.0  0.0  22124  1712 ?        Ss   Mar23   0:00 SCREEN -S ts3bot
root      9454  0.0  0.1  18088  2120 pts/4    Ss   Mar23   0:00 /bin/bash
root     29807  0.0  0.0  22128  1716 ?        Ss   Mar23   0:00 SCREEN -S ts3servermcrealm
root     29808  0.0  0.1  18092  2168 pts/5    Ss   Mar23   0:00 /bin/bash
root     30380  0.0  0.0   4180   624 pts/5    S+   Mar23   0:00 /bin/sh ./ts3server_minimal_runscript.sh start inifile=ts3server.ini
root     30383  2.7  0.4 198508  9836 pts/5    Sl+  Mar23 174:02 ./ts3server_linux_amd64 start inifile=ts3server.ini
root     30596  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root     32633  0.0  0.0  21860  1424 ?        Ss   Mar18   0:00 SCREEN -S mc
root     32634  0.0  0.1  18096  2164 pts/2    Ss+  Mar18   0:00 /bin/bash

"ps -axfu"

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23548  1664 ?        Ss   Feb26   0:06 init
root      1285  0.0  0.0  14760  1096 ?        Ss   Feb26   0:00 /usr/sbin/xinetd -dontfork -pidfile /var/run/xinetd.pid -stayalive -inetd_compat
root      1299  0.0  0.1  49424  2668 ?        Ss   Feb26   0:42 /usr/sbin/sshd -D
root      9424  0.0  0.1  70796  3472 ?        Ss   Mar23   0:04  \_ sshd: root@pts/0
root      9436  0.0  0.1  18064  2144 pts/0    Ss   Mar23   0:00      \_ -bash
root      9556  0.0  0.0  15060  1072 pts/0    R+   06:01   0:00          \_ ps axfu
root      1313  0.0  0.0  18888  1016 ?        Ss   Feb26   0:14 cron
syslog    1335  0.0  0.0  12536   772 ?        Ss   Feb26   0:34 /sbin/syslogd -u syslog
root      1349  0.0  0.0   6712   648 ?        Ss   Feb26   3:59 /usr/sbin/vnstatd -d
root      1390  0.0  0.0  68268  2072 ?        Ss   Feb26   3:23 sendmail: MTA: accepting connections
root      1414  0.0  0.3 108572  7400 ?        Ss   Feb26   6:24 /usr/sbin/apache2 -k start
root      3337  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root      3685  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root      3876  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root     30596  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root      3247  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root      3274  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root      3658  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root      5495  0.0  0.2 108572  4584 ?        S    01:58   0:00  \_ /usr/sbin/apache2 -k start
root      5747  0.0  0.2 108572  4584 ?        S    02:40   0:00  \_ /usr/sbin/apache2 -k start
root      5762  0.0  0.2 108572  4584 ?        S    02:42   0:00  \_ /usr/sbin/apache2 -k start
root      1478  0.0  0.0  22124  1712 ?        Ss   Feb26   0:00 SCREEN -S ts3serverdasoren
root      1479  0.0  0.1  18040  2116 pts/1    Ss   Feb26   0:00  \_ /bin/bash
root      1500  0.0  0.0   4180   624 pts/1    S+   Feb26   0:00      \_ /bin/sh ./ts3server_minimal_runscript.sh start inifile=ts3server.ini
root      1503  3.4  1.1 277540 24156 pts/1    Sl+  Feb26 1523:07          \_ ./ts3server_linux_amd64 start inifile=ts3server.ini
root      1598  0.0  0.0  22124  1644 ?        Ss   Feb26   0:00 SCREEN -S minecraft
root      1599  0.0  0.1  18048  2108 pts/3    Ss+  Feb26   0:00  \_ /bin/bash
root     32633  0.0  0.0  22136  1652 ?        Ss   Mar18   0:00 SCREEN -S mc
root     32634  0.0  0.1  18096  2164 pts/2    Ss+  Mar18   0:00  \_ /bin/bash
root      9453  0.0  0.0  22124  1712 ?        Ss   Mar23   0:00 SCREEN -S ts3bot
root      9454  0.0  0.1  18088  2120 pts/4    Ss   Mar23   0:00  \_ /bin/bash
root      7904  1.4  2.6 1055924 55952 pts/4   Sl+  04:31   1:18      \_ java -Xms10M -jar JTS3ServerMod.jar
root     29807  0.0  0.0  22128  1716 ?        Ss   Mar23   0:00 SCREEN -S ts3servermcrealm
root     29808  0.0  0.1  18092  2168 pts/5    Ss   Mar23   0:00  \_ /bin/bash
root     30380  0.0  0.0   4180   624 pts/5    S+   Mar23   0:00      \_ /bin/sh ./ts3server_minimal_runscript.sh start inifile=ts3server.ini
root     30383  2.7  0.4 198508  9836 pts/5    Sl+  Mar23 174:25          \_ ./ts3server_linux_amd64 start inifile=ts3server.ini


```

---

### Post by spynappels on 2012-03-28
You should start a new Thread about this, not resurrect one from 11 months ago. If you click on the "Report abuse" button on one of your own posts and ask an Admin to move it to it's own thread, you may get answers quicker.

---

