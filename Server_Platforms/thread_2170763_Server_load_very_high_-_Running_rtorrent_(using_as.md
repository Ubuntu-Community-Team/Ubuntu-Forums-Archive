---
title: "Server load very high - Running rtorrent (using as a seedbox)"
date: 2013-08-27
forum: Server Platforms
---

### Post by Trueill on 2013-08-27
Hello,

I am running on ubuntu 12.04 (amd 64) server. I have installed apache and rtorrent on LVM. I am using my server as a seedbox, however my server load is around 5 - 24. Only 3 users are on it.

Server Specs - 
Intel(R) Xeon(R) CPU X3440  @ 2.53GHz
RAM - 8 GB
HDD - 1 TB X 2 in RAID 0

Can anyone please help me find the reason behind it.

---

### Post by sanderj on 2013-08-27
Open a terminal, run "top -bn1 | head -15" and post the output here.

---

### Post by Trueill on 2013-08-27
> **sanderj said:**
> Open a terminal, run "top -bn1 | head -15" and post the output here.
```

top - 22:00:06 up  3:12,  1 user,  load average: 9.06, 7.15, 4.50
Tasks: 155 total,   2 running, 153 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5%us,  0.4%sy,  0.0%ni, 89.9%id,  8.8%wa,  0.0%hi,  0.4%si,  0.0%st
Mem:   8169404k total,  8002752k used,   166652k free,    13332k buffers
Swap: 31247356k total,        0k used, 31247356k free,  7344772k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1448 trueill   20   0  326m  65m  42m D    6  0.8   2:16.38 rtorrent           
   53 root      20   0     0    0    0 S    2  0.0   0:01.31 kworker/5:1        
   58 root      20   0     0    0    0 S    2  0.0   1:43.83 kswapd0            
 1446 mattypd   20   0  295m  35m  10m S    2  0.5   2:27.93 rtorrent           
 1468 trueill   20   0  210m  41m 6544 S    2  0.5   0:04.21 irssi              
 6989 mattypd   20   0  168m  11m 6852 D    2  0.1   0:00.01 php                
 6994 mattypd   20   0  168m  11m 6424 R    2  0.1   0:00.01 php                
    1 root      20   0 24304 2276 1360 S    0  0.0   0:01.89 init   
```

---

### Post by sanderj on 2013-08-27
"Cpu(s):  0.5%us ...  89.9%id," ... that's good: CPU is 90% idle.

So what do you mean with "my server load is around 5 - 24. "?

What is the output of "uptime": the last three numbers are important ... lower is better. Below 1 is perfect.

---

### Post by Trueill on 2013-08-27
As you can see in the top dump,

load average: 9.06, 7.15, 4.50

When I said "my server load is around 5 - 24", I meant that load average which is "9.06 , 7.15, 4.50", it goes upto 24 or 30 even

---

### Post by sanderj on 2013-08-27
Ah. Strange. I have no further ideas.

---

### Post by Doug S on 2013-08-27
Try to run top for awhile and watch it. See if you can observe what is using CPU time during periods when the 1 minute load average is increasing.
You can also change the default sort column to time (two presses of the ">" will change the sort column from %CPU to TIME. Press "<" to go back).
Maybe also observe each CPU (depress the "1" key).
I think you have 8 CPU's.

After observing for awhile you should be able to determine the correlation between load average and what is effecting it.

The other possibility is that reported load average are actually incorrect. As far as I know (and I spent many many months the issue a year ago), all incorrect load average reporting issues have been fixed.

---

### Post by SeijiSensei on 2013-08-27
I would reboot the server, then run top after it restarts.  Watch and see what happens over time.

Is there some reason why you can't run just one rtorrent instance to handle all the traffic?

---

### Post by Trueill on 2013-08-28
> **Doug S said:**
> Try to run top for awhile and watch it. See if  you can observe what is using CPU time during periods when the 1 minute  load average is increasing.
You can also change the default sort column to time (two presses of the  ">" will change the sort column from %CPU to TIME. Press "<" to go  back).
Maybe also observe each CPU (depress the "1" key).
I think you have 8 CPU's.

After observing for awhile you should be able to determine the correlation between load average and what is effecting it.

The other possibility is that reported load average are actually  incorrect. As far as I know (and I spent many many months the issue a  year ago), all incorrect load average reporting issues have been  fixed.

Whenever there is high I/O operations the load increases dramatically. Like when I unrar while downloading 3 torrent files simultaneously.

> **SeijiSensei said:**
> I would reboot the server, then run top after it restarts.  Watch and see what happens over time.

Is there some reason why you can't run just one rtorrent instance to handle all the traffic?

After, rebooting the server got back to its normal load as unraring stopped. Can I have 1 rtorrents instances with multiple users ? 

My I/O wait is around 10% but my load becomes 25. Does that mean I/O wait is causing this or some else might be at play here ?

---

### Post by Doug S on 2013-08-28
> **Trueill said:**
> Whenever there is high I/O operations the load increases dramatically. Like when I unrar while downloading 3 torrent files simultaneously.
After, rebooting the server got back to its normal load as unraring stopped. Can I have 1 rtorrents instances with multiple users ? 
My I/O wait is around 10% but my load becomes 25. Does that mean I/O wait is causing this or some else might be at play here ?I don't know anything about rtorrent, so can not answer that part.
An I/O wait of 10% shouldn't lead to a load of 25. Maybe there are some pending processes in the queue adding to the load average. Myself, would sure like to understand your case.

---

### Post by Trueill on 2013-08-29
> **Doug S said:**
> I don't know anything about rtorrent, so can not answer that part.
An I/O wait of 10% shouldn't lead to a load of 25. Maybe there are some pending processes in the queue adding to the load average. Myself, would sure like to understand your case.

Hey, 

I noticed something and I think I found the problem. 
I was getting 10% io wait from just iostat command, but iostat 10 30 gave me a better look at the picture, io wait for going to 40 % with an average staying around 30%.

I tested the write speeds and found it to be 35MB/s on RAID 0 with 2 drives. I used the command

dd if=/dev/zero of=testfile bs=100k count=60k && sync

This was when I used RAID 0 with LVM. I reinstalled OS with just RAID 0 and my write speeds have increased dramatically to 210 MB/s

Can LVM cause this ?

---

### Post by houstonbofh on 2013-08-30
LVM is an additional abstraction on top of the drive.  So, in a I/O bound application, it can cause some serious load.

I avoid LVM like the plague, personally, as it has caused me lots of bizarre problems with no real benefit.

---

### Post by Doug S on 2013-09-04
Interestingly, but perhaps completely unrelated, I just got this on my computer:```
top - 20:54:47 up 1 day,  5:19,  3 users,  [COLOR=#ff0000]load average: 57.13, 32.02, 13.19[/COLOR]
Tasks: 150 total,   1 running, 149 sleeping,   0 stopped,   0 zombie
Cpu0  :  3.7%us,  1.3%sy,  0.0%ni,  2.0%id, 93.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  7.4%us,  1.3%sy,  0.0%ni, 88.3%id,  3.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  5.6%us,  1.3%sy,  0.0%ni, 92.4%id,  0.7%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  6.7%us,  0.7%sy,  0.0%ni, 91.9%id,  0.7%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu4  :  0.0%us,  0.0%sy,  0.0%ni, 99.3%id,  0.7%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu5  :  0.0%us,  0.3%sy,  0.0%ni, 99.3%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu6  :  0.7%us,  0.0%sy,  0.0%ni, 98.7%id,  0.7%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu7  :  0.0%us,  0.3%sy,  0.0%ni, 98.3%id,  1.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  16004108k total, 14997788k used,  1006320k free,   559244k buffers
Swap:  8294396k total,        0k used,  8294396k free,  6668344k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
26954 libvirt-  20   0 12.5g 6.6g 6952 S   31 43.2   1:46.81 kvm
   52 root      25   5     0    0    0 S    0  0.0   7:41.99 ksmd
    1 root      20   0 24568 2476 1360 S    0  0.0   0:01.45 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:00.47 ksoftirqd/0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.24 migration/0
```I do not know why the load average shot up so high. I also recall several months seeing, and capturing data for, a sudden severe spike in load average, but I have never had time to investigate further:

---

