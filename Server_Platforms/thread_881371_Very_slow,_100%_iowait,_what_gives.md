---
title: "Very slow, 100% iowait, what gives?"
date: 2008-08-05
forum: Server Platforms
---

### Post by Carleas on 2008-08-05
I recently upgraded to Feisty, and since the change my server's been *extremely* slow.  I'm not that experienced, so I don't know how to begin addressing the problem.  I've tried to track down the problem, and I noticed that all my cpu is being tied up in iowait.  Here's my top output:
```
top - 03:51:07 up 1 day,  1:11,  2 users,  load average: 16.80, 12.08, 7.48
Tasks:  90 total,   2 running,  88 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,  0.0%id, 99.7%wa,  0.0%hi,  0.0%si,  0.3%st
Mem:    434300k total,   429516k used,     4784k free,    10344k buffers
Swap:   524280k total,       56k used,   524224k free,   225412k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
    1 root      18   0  1660  800  576 S  0.0  0.2   0:00.01 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 xenwatch           
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 xenbus             
   13 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   15 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
   55 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
   56 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush            
   57 root      11  -5     0    0    0 S  0.0  0.0   0:00.26 kswapd0            
   58 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
   59 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 xfslogd/0          
   60 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 xfsdatad/0         
  668 root      10  -5     0    0    0 D  0.0  0.0   0:00.05 kjournald    
```
Notice %wa.  I'm pretty sure that shouldn't be, but I haven't a clue how to approach the issue.  I've looked into apache, but it's not just my website that loads slowly, the whole server is slow when I'm accessing it by ssh, and when there's otherwise low activity.  I've also looked into mysql a little, but I can't get phpmyadmin working to optimize the database.
Can someone give me direction?  I've been trying to hunt this down all day, searching for everything I can think of, I'm running out of things to type into google!

---

### Post by arvevans on 2008-08-06
I'm not the expert here, but since nobody else has responded I'll give it a try:
[LIST]
[*]Go to a terminal screen and enter "man ps" to see how the ps command works.
[*]Probably "ps -ael" will tell you what processes are running.  Take a look at the output to see if there is any obvious problem (like many multiple spawnings of the same process)?  You can kill unwanted processes by using "sudo kill -9 [process_ID_number]".  It is relatively safe to do this because if you kill something critical you just have to re-boot to get everything started again.
[/LIST]

Linux operation makes a number of logs that may tell you if something is really going astray.  Check in:
[INDENT]=> /var/log/auth.log : User login and authentication logs

=> /var/log/daemon.log : Running services such as squid, ntpd and others log message to this file

=> /var/log/dmesg : Linux kernel ring buffer log

=> /var/log/dpkg.log : All binary package log includes package installation and other information

=> /var/log/faillog : User failed login log file

=> /var/log/kern.log : Kernel log file

=> /var/log/lpr.log : Printer log file

=> /var/log/mail.* : All mail server message log files

=> /var/log/mysql.* : MySQL server log file

=> /var/log/user.log : All userlevel logs

=> /var/log/xorg.0.log : X.org log file

=> /var/log/apache2/* : Apache web server log files directory

=> /var/log/lighttpd/* : Lighttpd web server log files directory

=> /var/log/fsck/* : fsck command log

=> /var/log/apport.log : Application crash report / log file[/INDENT]

This may not help fix your problem but should give you an idea of which question to ask next.

Arv
_._

---

### Post by Carleas on 2008-08-07
The logs got PhpMyAdmin working.  I had a 500 error, and I found in my apache logs that PhpMyAdmin wasn't being allowed to follow symlinks.  So that's good.

But the iowait problem is still around after repairing and optimizing my DBs.  My working solution was to kill postfix, which has improved things but not solved them.  I sill see high his iowait times fairly often, but at least it isn't constant.

Are there known problems with Postfix that would cause a problem like this?  I'm kind of thinking that it isn't postfix's doing at all, because high iowaits are still so frequent.  I'm thinking it's something that postfix interacts with regularly. . . like logging.  Is that possible?

---

### Post by cariboo on 2008-08-07
I was fooling around the other day and built a server using the mini cd on a 400Mhz celeron with 96MB ram. Things ran quite smoothly until I installed gallery2 then I had the same problem as you 97%wa with a little looking and poking around I found that mysql was causing the problem. If I kill all the mysql processes  it went down to 17%wa which is what I would expect from the low specs especially serving dynamic pages. I have since upgraded to 128MB ram (thats all the pc-110 ram I have) and haven't had the time to experiment any further. Tomorrow, time permitting I'll try the server kernel to see if this makes any difference.

Jim

---

### Post by RealPSL on 2008-08-07
A high IO wait is normally a result of a significant amount of disk activity and will make your machine crawl. Assuming you are not running any large applications on your machines running a lot of disk reads the problems will then most likely be caused by paging in and out between RAM and swap. 

This is normally the case if you do not have enough RAM in your PC and your swap space is used to supplement it. The output of

```
vmstat 3 20 
```while the problem is happening would help confirm.

---

### Post by Carleas on 2008-08-08
OK, vmstat is informative:

```
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  1     56 167896   1696 149488    0    0    35    24   57   53  3  0 52 44
 0  0     56 166996   1696 150360    0    0   299     0  178   53  0  0 78 21
 0  0     56 164228   1696 151276    0    0   299     0  187   84  3  0 80 16
 0  2     56 165240   1696 151916    0    0   213    21  202   66  1  0 57 42
 0  2     56 164828   1696 152308    0    0   128     0  119   32  0  0  0 99
 0  0     56 164228   1712 152924    0    0   213    23  127   51  0  0 16 82
 0  0     56 163328   1712 153836    0    0   299     0  174   52  0  0 78 21
 0  2     56 162360   1716 154756    0    0   307     1  167   80  2  0 60 37
 2  2     56 160476   1720 155900    0    0   384     4  189   82  2  0  0 95
 0  3     56 160296   1720 156080    0    0    59     7   54   23  0  0  0 98
 0  2     56 158924   1732 157440    0    0   456    19  215   82  0  0  0 99
 0  3     56 157508   1732 158280    0    0   279     0  143   66  0  0  0 97
 0  0     56 158156   1736 159128    0    0   279     0  184   76  2  0 45 53
 0  2     56 157264   1736 160012    0    0   300    27  179  100  4  0 69 23
 0  0     56 156356   1744 160924    0    0   299    21  212  130  1  0 40 58
 0  1     56 155208   1752 161836    0    0   299     8  212  103  1  0 49 48
 0  0     56 154308   1752 162716    0    0   299     0  209   59  0  0 91  9
 0  0     56 153036   1764 163600    0    0   300     5  168   85  3  0 69 24
 0  0     56 152136   1764 164512    0    0   299     4  165   57  0  0 88 10
 0  1     56 150612   1772 165312    0    0   265    25  172   86  2  0 24 72
```

Top says I have swap, but it doesn't look like it's used.  Is that right?  What do I have to do to fix that?  
Also, the bi is pretty high.  I'm trying to cut down the amount of logging that my system does, is that a reasonable approach?  So far I'm commented out access logging on apache, and maintained only error logging.  Or is there something farther upstream that I should be looking for?

---

### Post by RealPSL on 2008-08-09
The "bi" column is more of an indication that data is being read in. More detail can be received from the iostat command but you would have to install the systat package with ```
sudo apt-get install systat
``` to get that.

---

### Post by windependence on 2008-08-09
> **Carleas said:**
> OK, vmstat is informative:

```
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  1     56 167896   1696 149488    0    0    35    24   57   53  3  0 52 44
 0  0     56 166996   1696 150360    0    0   299     0  178   53  0  0 78 21
 0  0     56 164228   1696 151276    0    0   299     0  187   84  3  0 80 16
 0  2     56 165240   1696 151916    0    0   213    21  202   66  1  0 57 42
 0  2     56 164828   1696 152308    0    0   128     0  119   32  0  0  0 99
 0  0     56 164228   1712 152924    0    0   213    23  127   51  0  0 16 82
 0  0     56 163328   1712 153836    0    0   299     0  174   52  0  0 78 21
 0  2     56 162360   1716 154756    0    0   307     1  167   80  2  0 60 37
 2  2     56 160476   1720 155900    0    0   384     4  189   82  2  0  0 95
 0  3     56 160296   1720 156080    0    0    59     7   54   23  0  0  0 98
 0  2     56 158924   1732 157440    0    0   456    19  215   82  0  0  0 99
 0  3     56 157508   1732 158280    0    0   279     0  143   66  0  0  0 97
 0  0     56 158156   1736 159128    0    0   279     0  184   76  2  0 45 53
 0  2     56 157264   1736 160012    0    0   300    27  179  100  4  0 69 23
 0  0     56 156356   1744 160924    0    0   299    21  212  130  1  0 40 58
 0  1     56 155208   1752 161836    0    0   299     8  212  103  1  0 49 48
 0  0     56 154308   1752 162716    0    0   299     0  209   59  0  0 91  9
 0  0     56 153036   1764 163600    0    0   300     5  168   85  3  0 69 24
 0  0     56 152136   1764 164512    0    0   299     4  165   57  0  0 88 10
 0  1     56 150612   1772 165312    0    0   265    25  172   86  2  0 24 72
```

Top says I have swap, but it doesn't look like it's used.  Is that right?  What do I have to do to fix that?  
Also, the bi is pretty high.  I'm trying to cut down the amount of logging that my system does, is that a reasonable approach?  So far I'm commented out access logging on apache, and maintained only error logging.  Or is there something farther upstream that I should be looking for?

Actually, if you have enough physical RAM, you don't want your machine using swap if at all possible. If swap is being used heavily, that usually is an indication you are short on physical memory. Some people nowadays run with no swap at all with no problems.

-Tim

---

