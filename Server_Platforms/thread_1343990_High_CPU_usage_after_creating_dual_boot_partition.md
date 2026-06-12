---
title: "High CPU usage after creating dual boot partition??"
date: 2009-12-02
forum: Server Platforms
---

### Post by sizzleplatter on 2009-12-02
Just wondering if this is typical.  I have been running Ubuntu 9.10 Server Edition for about a month on an older dell dimension with a 1TB external hard drive attached.  I recently installed Kubuntu 9.10 on a 40 gig partition on the external hard drive. I will be dual booting between the Server and Desktop versions.  Whats strange is that before partitioning and installing Kubuntu, I was typically seeing about 1% cpu usage when the system is running.  After the install, I'm seeing about 15% cpu usage on average.  Specifically I've noticed that hald is running constantly at about 4% cpu usage.  Is the new partition causing this to happen or could this be a coincidence?  

Thanks for the help.

---

### Post by dnvikram on 2009-12-02
When you say external drive,how exactly is it connected to the system?Using firewire or usb or a usb-sata docking station?And does your main /boot and / partition reside on the external drive?

Coz'I have seen this kind of cpu spikes at times as a result of I/O.

---

### Post by sizzleplatter on 2009-12-02
The external drive is connected through USB.  Ubuntu server is installed on the master disk and Kubuntu is installed on the external drive.   Both the /boot and / partitions are on the master disk, not the external.

---

### Post by dnvikram on 2009-12-02
Can you paste the output of the below commands:

top

iostat -d 10

sar 5 10

Do you see lot of cpu for the gui in top?

---

### Post by sizzleplatter on 2009-12-02
top - 12:46:00 up 51 min,  1 user,  load average: 1.17, 1.35, 1.35
Tasks:  97 total,   6 running,  91 sleeping,   0 stopped,   0 zombie
Cpu(s):  8.6%us,  6.6%sy,  0.0%ni, 84.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1283636k total,   352292k used,   931344k free,   116088k buffers
Swap:  3219448k total,        0k used,  3219448k free,   158176k cached



 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  
                                                             
 3287 haldaemo  20   0  6444 4248 3496 S  4.0  0.3   1:46.09 hald                                                                   
  751 root      16  -4  2224  536  316 S  1.3  0.0   0:31.67 udevd                                                                  
   17 root      15  -5     0    0    0 D  0.3  0.0   0:15.51 khubd                                                                  
    1 root      20   0  3084 1888  564 S  0.0  0.1   0:01.48 init                                                                   
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                               
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                            
    4 root      15  -5     0    0    0 S  0.0  0.0   0:01.23 ksoftirqd/0                                                            
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                             
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 events/0                                                               
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0                                                                
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                          
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                                                              
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                 
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                           
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                                                 
   14 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                  
   15 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                
   16 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                          
   18 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                
   19 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                                  
   20 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btaddconn                                                              
   21 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 btdelconn                                                              
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                
   24 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                
   25 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                  
   26 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea                                                        
   29 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0        




root@sizzle:/home/tracer# iostat -d 10
Linux 2.6.28-16-server (sizzle)         12/02/2009      _i686_  (1 CPU)

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               3.66        99.67        52.59     310686     163938
sda1              3.63        97.89        52.59     305130     163936
sda2              0.00         0.00         0.00          6          0
sda5              0.02         1.67         0.00       5198          2
dm-0              9.31        96.85        52.59     301898     163936
dm-1              0.07         0.55         0.00       1720          0
sdb               0.53        65.21         0.00     203251          1
sdb1              0.51        64.75         0.00     201829          1
sdb2              0.00         0.00         0.00          4          0
sdb5              0.01         0.18         0.00        568          0
sdb6              0.01         0.18         0.00        554          0

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               1.50         0.00       188.00          0       1880
sda1              1.50         0.00       188.00          0       1880
sda2              0.00         0.00         0.00          0          0
sda5              0.00         0.00         0.00          0          0
dm-0             23.50         0.00       188.00          0       1880
dm-1              0.00         0.00         0.00          0          0
sdb               0.00         0.00         0.00          0          0
sdb1              0.00         0.00         0.00          0          0
sdb2              0.00         0.00         0.00          0          0
sdb5              0.00         0.00         0.00          0          0
sdb6              0.00         0.00         0.00          0          0

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda               1.00         0.00        28.00          0        280
sda1              1.00         0.00        28.00          0        280
sda2              0.00         0.00         0.00          0          0
sda5              0.00         0.00         0.00          0          0
dm-0              3.50         0.00        28.00          0        280
dm-1              0.00         0.00         0.00          0          0
sdb               0.00         0.00         0.00          0          0
sdb1              0.00         0.00         0.00          0          0
sdb2              0.00         0.00         0.00          0          0
sdb5              0.00         0.00         0.00          0          0
sdb6              0.00         0.00         0.00          0          0

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda              14.30         0.00       167.20          0       1672
sda1             14.30         0.00       167.20          0       1672
sda2              0.00         0.00         0.00          0          0
sda5              0.00         0.00         0.00          0          0
dm-0             20.90         0.00       167.20          0       1672
dm-1              0.00         0.00         0.00          0          0
sdb               0.00         0.00         0.00          0          0
sdb1              0.00         0.00         0.00          0          0
sdb2              0.00         0.00         0.00          0          0
sdb5              0.00         0.00         0.00          0          0
sdb6              0.00         0.00         0.00          0          0



root@sizzle:/home/tracer# sar 5 10
Linux 2.6.28-16-server (sizzle)         12/02/2009      _i686_  (1 CPU)

12:47:24 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
12:47:29 PM     all      6.79      0.00     10.78      0.00      0.00     82.44
12:47:34 PM     all      7.20      0.00      9.20      0.00      0.00     83.60
12:47:39 PM     all      7.60      0.00      8.60      0.00      0.00     83.80
12:47:44 PM     all      5.40      0.00     12.60      0.00      0.00     82.00

---

### Post by sizzleplatter on 2009-12-02
I'm not showing anything from a GUI because I don't have one installed on this partition. Just curious how installing Kubuntu on a second partition could cause an increase in cpu usage??

---

### Post by dnvikram on 2009-12-02
hald is hardly taking 4% cpu...this is not abnormal..at the same time we cannot conclude anything from one iteration of this output.Can you try killing the hald pid and see what happens.Make sure you are running the top command in another terminal to see the effect of that.Also,try switching to runlevel 2 and leave the system like that for sometime and see if you still have the cpu spikes.

---

### Post by dnvikram on 2009-12-02
Ideally,if you see lot of cpu being used by hald daemon,that means its polling for some devices and on io wait.There have been instances where in killing hald or disabling some peripherals which are causing this ,shows a drop is cpu consumption.

---

### Post by sizzleplatter on 2009-12-02
Yep, killing hald worked just fine.  I'm not sure why, but killing hald and udevd freed up a considerable amount of resources...  


02:35:01 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
02:35:06 PM     all      0.00      0.00      0.00      0.60      0.00     99.40
02:35:11 PM     all      0.00      0.00      0.40      0.00      0.00     99.60

---

