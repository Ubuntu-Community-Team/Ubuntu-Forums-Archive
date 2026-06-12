---
title: "Used memory -cached -buffers much larger than summed processes"
date: 2009-11-15
forum: Server Platforms
---

### Post by basdoorn on 2009-11-15
I am running an Ubuntu 8.10 machine with 1.5GB RAM configured as an postfix+amavis+clamd+spamassasin mailserver with dovecot for imap access and apache running roundcube webmail. The server is showing higher than expected memory usage and several memory statistics do not seem to add up and explain why. Could anybody shed some light on why a difference of over 300MB exists between 

- used memory excluding buffers and cache as reported by free
- summation of Resident Set Size of all process reported by ps

Below are the details:

I used the x64 Ubuntu version in case I would need to assign more than 4GB memory at some point in the distant future.
```
uname -a
Linux my.host.name 2.6.27-9-server #1 SMP Thu Nov 20 22:56:07 UTC 2008 x86_64 GNU/Linux
```

Free shows me 877MB of memory is used besides buffers and cache. This would imply to me about this amount of memory is used by processes, please correct me if I am wrong here.
```
free -m
             total       used       free     shared    buffers     cached
Mem:          1504       1235        268          0        169        188
-/+ buffers/cache:        877        626
Swap:          953          2        951

```

The ps output below is truncated to show only processes consuming more than 3MB of Residential Set Size (RSS). About 50 smaller processes exist consuming a total of about 60-80MB worth of RRS. Summing up the RSS size of the larger processes below gives me a total of 484MB. The total RSS size would then be about 560M, which is over 300MB short of the 877MB reported used memory by free excluding buffers and cache. 
```
ps -A aux k rss
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root     13950  0.0  0.2  72312  3120 ?        S    Nov08   0:03 dovecot-auth
root     20052  0.0  0.2  70112  3120 ?        Ss   13:50   0:00 sshd: bas [priv]
root     12804  0.0  0.2  70112  3124 ?        Ss   13:10   0:00 sshd: bas [priv]
root     17972  0.0  0.2  72352  3372 ?        S    Nov14   0:00 dovecot-auth -w
postfix  29434  0.0  0.3 106564  5324 ?        S    15:24   0:00 smtpd -n smtp -t inet -u -c -o stress  -o cleanup_ser
www-data 23440  0.0  0.3 258068  5460 ?        S    06:33   0:00 /usr/sbin/apache2 -k start
snmp     12842  0.0  0.3  50228  5592 ?        S    13:10   0:01 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -I -smux -
111      29436  0.1  0.3  49948  6148 ?        Ss   15:24   0:00 /usr/bin/python /usr/bin/policyd-spf
www-data 23438  0.0  0.4 258208  6372 ?        S    06:33   0:00 /usr/sbin/apache2 -k start
root     27189  0.0  0.6 258068 10684 ?        Ss   Nov12   0:04 /usr/sbin/apache2 -k start
mysql     3694  0.0  3.3 181848 51536 ?        Sl   Nov08   4:14 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/my
virtual  29450  0.0  5.5 215900 84928 ?        S    15:24   0:00 amavisd (virgin child)
virtual   4807  0.0  5.5 214700 85932 ?        Ss   Nov08   0:17 amavisd (master)
virtual  28924  0.4  5.6 216584 87100 ?        S    15:18   0:01 amavisd (ch6-avail)
clamav   13594  0.0  7.9 220040 122196 ?       Ssl  Nov08   0:57 /usr/sbin/clamd

```

Please let me know if more information is required or if I have overlooked something 'elementary', as this machine is currently by far the top memory consumer on the virtual host. Reducing it's required memory allocation would be quite welcome.

---

### Post by basdoorn on 2009-11-15
Dug a little bit into the memory usage and compiled a graph of the memory usage before the gap between used and processes became so high. Turns out it got much worse by running a new maintenance script to remove all virusmails older than 30 days (about 1.7GB worth of small files was removed in this operation). The script is shown below, and a picture of the memory graph attached. Basically it seems cached memory is 'becoming' used memory during this operation? Files being removed causing cached memory to shrink makes sense, but why the increase in used? 
Since my last post the memory reported by free as used has dropped from 877MB then to 819MB now. The RSS in the process list does not seem to have changed by any significant amount for any process. Somehow the system has reclaimed 58MB used memory in the last hour. Does the kernel somehow take up lots of memory when removing many small files only to release this later at a very slow rate? The filesystem is ext3 and fstab shows it is mounted with default options.

```
#/bin/bash

/usr/bin/find /var/lib/amavis/virusmails/ -type f -mtime +30 -exec rm -f {} \;
```

---

### Post by basdoorn on 2009-11-15
Solved by looking into the ext3 theory. It seems this is a known problem where the kernel thinks it is doing a good job caching all the inodes, which can cause 400-500MB of memory usage. No way for the kernel to tell the difference of course, but annoying in this case nontheless. Found the following thread detailing the behaviour and manual 'solution'.

[Kernel Mailing-Lists 2006-08 msg01307.html]("http://linux.derkeiler.com/Mailing-Lists/Kernel/2006-08/msg01307.html")

Confirmed by running and checking it was indeed the kernel slab by inspecting /proc/slabinfo

```
cat /proc/slabinfo
slabinfo - version: 2.1
# name            <active_objs> <num_objs> <objsize> <objperslab> <pagesperslab> : tunables <limit> <batchcount> <sharedfactor> : slabdata <active_slabs> <num_slabs> <sharedavail>
ext3_inode_cache   60533 394020    768   42    8 : tunables    0    0    0 : slabdata   9614   9614      0
```

Resolved by running the following command:

```
echo 2 > /proc/sys/vm/drop_caches
```

Which clears the massive inode cache after such an operation, although running this command also hits the cache and will cause slightly more disk activity afterwards.
Now my free output looks more like I expected, with only 485MB being used. Seems the inode cache was good for about 400MB indeed.

```
free -m
             total       used       free     shared    buffers     cached
Mem:          1504        680        824          0        152         41
-/+ buffers/cache:        485       1018
Swap:          953          2        951
```

The issue is now resolved and much has been learned from it :D

---

### Post by Vegan on 2009-11-15
I use the 32-bit of Ubuntu server and it can see 64GB of RAM so there is no rush for me to switch to x64 yet. Besides the Pentium IV is only a 32-bit processor.

I run more services than you and I was OK even on a Pentium III with 768MB before I got a faster machine.

SAMBA seems to want the most memory, I keep my iTunes library on the server so if Windows dies, my music is safe.

I have not seen any out of memory problems so I ignore the situation.

Unless the server complains, I would ignore memory utilization. It varies widely on my machine.

---

### Post by basdoorn on 2009-11-15
You are right on the x64 being a bit early in this case, but you never know beforehand where you might end up one day. The 64GB PAE option on 32 bit Ubuntu server is slower than natively accessing the same memory in 64 bit edition, so I went for x64 when I conveniently had the chance. Using a Xeon L5420 processor in this box and 8GB RAM from the start, I went with x64 for the KVM host environment and picked the same for all virtual hosts for no special reason.
The mail server is now running fine with 1GB RAM and it will likely stay that way for some time to come. So for now, this server is in it's happy place, even though the x64 architecture does not currently help it anywhere.

---

