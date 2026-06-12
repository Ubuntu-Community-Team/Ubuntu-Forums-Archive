---
title: "memory leak ubuntu server 10.10"
date: 2011-02-07
forum: Server Platforms
---

### Post by azschorn on 2011-02-07
Hi,
perhaps somebody has an idea. 
I just upgraded (new install) from 8.04 server to 10.10 server (64bit) with 1GB Ram
It is a plain vanilla installation on a vmware, as an virtual machine.
I installed additional  openssh, open-vm-dkms, open-vm-tools, java-jdk, apache2, and the hudson package. As far as i can see, the applications run fine. 
The problem is that the server runs out of memory and kills my applications, mostly once a day. I already ensured that the applications like apache or hudson are not the memory eater. They are limited to a fixed size. The main problem is that the memory consumption don't add up. So i suppose it must be something not visible.
The memory is slowly eaten through the day, so i have to restart the server once a day.
The latest patch-set is installed. I already read about the memory leaks with ureadahead, but these should be fixed, and uninstalling did not help either.
e.g. 
free shows
```
             total       used       free     shared    buffers     cached
Mem:       1022548    1011276      11272          0      12204      51808
-/+ buffers/cache:     947264      75284
Swap:       152580     152580          0


 ./ps_mem.py
 Private  +   Shared  =  RAM used       Program

  4.0 KiB +  15.5 KiB =  19.5 KiB       nullmailer-send
  4.0 KiB +  21.5 KiB =  25.5 KiB       upstart-udev-bridge
 16.0 KiB +  24.0 KiB =  40.0 KiB       atd
 36.0 KiB +  23.5 KiB =  59.5 KiB       daemon
 12.0 KiB +  66.0 KiB =  78.0 KiB       udevd (3)
 24.0 KiB +  72.0 KiB =  96.0 KiB       getty (6)
 88.0 KiB +  35.0 KiB = 123.0 KiB       cron
 88.0 KiB +  36.5 KiB = 124.5 KiB       irqbalance
252.0 KiB +  59.0 KiB = 311.0 KiB       rsyslogd
360.0 KiB + 166.5 KiB = 526.5 KiB       sshd (2)
496.0 KiB +  32.0 KiB = 528.0 KiB       init
536.0 KiB +  87.0 KiB = 623.0 KiB       vmtoolsd
  2.0 MiB +  68.5 KiB =   2.0 MiB       bash
 14.1 MiB +   2.8 MiB =  16.9 MiB       apache2 (21)
690.7 MiB + 452.5 KiB = 691.1 MiB       java
---------------------------------
                        712.6 MiB
=================================
```

I can also show the output from top itself, but it would show the same result. The current output is after 14 hours running, an i am sure that the server will run out of memory in some hours.
I would really appreciate any thoughts on this.I would hate to downgrade ubuntu, and feeling like in old windows times.
Thanks 
Andreas

---

### Post by iMav on 2011-02-15
I am having the same issue.  It is driving me batty!!  This is, also, a VM (under vmware server 2) and is primarily a web server (lighttpd, mysql) running a decent-sized vBulletin community and a couple of joomla sites.

I've been rebooting at least once a day for the past several days...I can watch the memory usage climb but cannot find the culprit at all.  Very frustrating!

---

### Post by azschorn on 2011-02-15
This still makes me crazy, just some additional information, just now after ubuntu killed my server java process.
free shows (in MB)
            total       used       free     shared    buffers     cached
Mem:          1360        988        372          0        161        197
-/+ buffers/cache:        629        730
Swap:          149         46        102

and running process add up to 12 MB
./ps_mem.py
 Private  +   Shared  =  RAM used       Program

  4.0 KiB +  15.5 KiB =  19.5 KiB       nullmailer-send
  4.0 KiB +  21.5 KiB =  25.5 KiB       upstart-udev-bridge
 28.0 KiB +  25.0 KiB =  53.0 KiB       atd
 12.0 KiB +  66.0 KiB =  78.0 KiB       udevd (3)
 24.0 KiB +  72.0 KiB =  96.0 KiB       getty (6)
100.0 KiB +  41.5 KiB = 141.5 KiB       irqbalance
108.0 KiB +  37.0 KiB = 145.0 KiB       cron
304.0 KiB +  65.5 KiB = 369.5 KiB       ntpd
600.0 KiB +  75.0 KiB = 675.0 KiB       rsyslogd
724.0 KiB + 108.0 KiB = 832.0 KiB       vmtoolsd
824.0 KiB +  52.0 KiB = 876.0 KiB       init
  2.0 MiB + 630.5 KiB =   2.6 MiB       sshd (2)
  3.1 MiB + 201.5 KiB =   3.3 MiB       bash
  2.0 MiB +   1.5 MiB =   3.5 MiB       apache2 (7)
---------------------------------
                         12.6 MiB
=================================


Who is using my Memory ? Why is the swap used?.  I hoped some of ubuntu specialist had an idea. This is just extremly frustating, not to have at least a clue, where my memory is gone. I think i will go back to an old version. ubuntu 10.10 is not acceptable for a productive server. Windows has many faults,  but at least you can see there where the memory is gone.

---

### Post by tbone7 on 2011-02-24
I can share that I have memory leaks on ubuntu 10.10 64, too. If I do 'free -m' on continuous intervals throughout the day, I can see the memory slowly but firmly being eaten up, before the system starts choking when the whole 4GB is used up.

Something eats up my memory, but I don't know what!

---

### Post by CharlesA on 2011-02-24
Helps to post the output of free -m.

---

### Post by RuralHunter on 2011-02-24
> **azschorn said:**
> Hi,
perhaps somebody has an idea. 
I just upgraded (new install) from 8.04 server to 10.10 server (64bit) with 1GB Ram
It is a plain vanilla installation on a vmware, as an virtual machine.
I installed additional  openssh, open-vm-dkms, open-vm-tools, java-jdk, apache2, and the hudson package. As far as i can see, the applications run fine. 
The problem is that the server runs out of memory and kills my applications, mostly once a day. I already ensured that the applications like apache or hudson are not the memory eater. They are limited to a fixed size. The main problem is that the memory consumption don't add up. So i suppose it must be something not visible.
The memory is slowly eaten through the day, so i have to restart the server once a day.
The latest patch-set is installed. I already read about the memory leaks with ureadahead, but these should be fixed, and uninstalling did not help either.
e.g. 
free shows
```
             total       used       free     shared    buffers     cached
Mem:       1022548    1011276      11272          0      12204      51808
-/+ buffers/cache:     947264      75284
Swap:       152580     152580          0


 ./ps_mem.py
 Private  +   Shared  =  RAM used       Program

  4.0 KiB +  15.5 KiB =  19.5 KiB       nullmailer-send
  4.0 KiB +  21.5 KiB =  25.5 KiB       upstart-udev-bridge
 16.0 KiB +  24.0 KiB =  40.0 KiB       atd
 36.0 KiB +  23.5 KiB =  59.5 KiB       daemon
 12.0 KiB +  66.0 KiB =  78.0 KiB       udevd (3)
 24.0 KiB +  72.0 KiB =  96.0 KiB       getty (6)
 88.0 KiB +  35.0 KiB = 123.0 KiB       cron
 88.0 KiB +  36.5 KiB = 124.5 KiB       irqbalance
252.0 KiB +  59.0 KiB = 311.0 KiB       rsyslogd
360.0 KiB + 166.5 KiB = 526.5 KiB       sshd (2)
496.0 KiB +  32.0 KiB = 528.0 KiB       init
536.0 KiB +  87.0 KiB = 623.0 KiB       vmtoolsd
  2.0 MiB +  68.5 KiB =   2.0 MiB       bash
 14.1 MiB +   2.8 MiB =  16.9 MiB       apache2 (21)
690.7 MiB + 452.5 KiB = 691.1 MiB       java
---------------------------------
                        712.6 MiB
=================================
```I can also show the output from top itself, but it would show the same result. The current output is after 14 hours running, an i am sure that the server will run out of memory in some hours.
I would really appreciate any thoughts on this.I would hate to downgrade ubuntu, and feeling like in old windows times.
Thanks 
Andreas
To me, the most likely suspect is the java process. Pls check the "mx" setting of the java process. If the values is set too large, it will eat all your memory, especially the value is larger than your actual memory. I have Ubuntu 10.10 64 bits running well for about one month with mysql and apache/tomcat and haven't seen any memory leak yet.

---

### Post by tbone7 on 2011-02-25
> **CharlesA said:**
> Helps to post the output of free -m.

I just rebooted my computer and here is the output of free -m on a "fresh" system:

```
             total       used       free     shared    buffers     cached
Mem:          3886        880       3006          0         37        244
-/+ buffers/cache:        597       3289
Swap:         2863          0       2863
```

I will do another one when the systems starts choking and post it here.

---

### Post by azschorn on 2011-02-25
I checked it before, thanks for the hint nevertheless. 
The process ist runnung with xmx512 and -XX:MaxPermSize=128, so the 691 mb are absolutly reasonable and are the value which i expect at the maximum.

Also the second post shows the memory consumption after ubuntu killed my java process. 988MB from 1360 used, but only 12,6 MB  are used from the visible process, and in this case java does not run anymore.

My problem is, that i am not able to see who is using my memory. The visible process, the cache and the buffers doen't add up to the complete used memory.

---

### Post by RuralHunter on 2011-02-25
> **azschorn said:**
> I checked it before, thanks for the hint nevertheless. 
The process ist runnung with xmx512 and -XX:MaxPermSize=128, so the 691 mb are absolutly reasonable and are the value which i expect at the maximum.

Also the second post shows the memory consumption after ubuntu killed my java process. 988MB from 1360 used, but only 12,6 MB  are used from the visible process, and in this case java does not run anymore.

My problem is, that i am not able to see who is using my memory. The visible process, the cache and the buffers doen't add up to the complete used memory.

OK, not sure how accuracy the ps_mem.py report is...but, what's the sum of the RSS column from the output of 'ps aux'?

---

### Post by tbone7 on 2011-02-25
> **tbone7 said:**
> I just rebooted my computer and here is the output of free -m on a "fresh" system:

```
             total       used       free     shared    buffers     cached
Mem:          3886        880       3006          0         37        244
-/+ buffers/cache:        597       3289
Swap:         2863          0       2863
```

I will do another one when the systems starts choking and post it here.

```
             total       used       free     shared    buffers     cached
Mem:          3886       3813         73          0         99       2844
-/+ buffers/cache:        869       3017
Swap:         2863          0       2863

```

And here is how it looks when I get home, 13 1/2 hours later. Lol. System isn't choking yet, but it's close to it, with almost all memory eaten up. The only two programs I started this morning was Deluge 1.3.0 and Rhythmbox 0.13.1. I wonder if is any of these causing the memory leak, or if it's something else..

edit: perhaps [this]("http://dev.deluge-torrent.org/ticket/1454").

---

### Post by RuralHunter on 2011-02-25
> **tbone7 said:**
> ```
             total       used       free     shared    buffers     cached
Mem:          3886       3813         73          0         99       2844
-/+ buffers/cache:        869       3017
Swap:         2863          0       2863

```And here is how it looks when I get home, 13 1/2 hours later. Lol. System isn't choking yet, but it's close to it, with almost all memory eaten up. The only two programs I started this morning was Deluge 1.3.0 and Rhythmbox 0.13.1. I wonder if is any of these causing the memory leak, or if it's something else..

edit: perhaps [this]("http://dev.deluge-torrent.org/ticket/1454").
No, the code you pasted indicates only 869M is used actually.

---

### Post by tbone7 on 2011-02-26
Oh, really. What about the first line?

---

### Post by CharlesA on 2011-02-26
> **tbone7 said:**
> Oh, really. What about the first line?
The first line shows total memory "used." Linux will use any unused memory for disk caching.

The second line shows how much memory is actually in use. :)

---

### Post by RuralHunter on 2011-02-26
> **tbone7 said:**
> Oh, really. What about the first line?

             2844M is used as file cache by OS to increase I/O performance since you have much free memory . If your memory usage increases, OS will free up the memory from file cache.  You can check the image below to understand the output of 'free'.

---

### Post by tbone7 on 2011-02-26
Ok, thanks for the informative response. I will take this into consideration and conduct new investigations :)

Sorry for hijacking the thread with non-ubuntu server related stuff, btw..!

---

