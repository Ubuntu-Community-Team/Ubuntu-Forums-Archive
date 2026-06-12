---
title: "SLOW  Ubuntu Server vs CentOS - MySQL Disk Access"
date: 2009-01-14
forum: Server Platforms
---

### Post by theparanoidone on 2009-01-14
I don't belive Ubuntu should compile the standard kernel with these options:

CONFIG_HZ_100=y 
CONFIG_HZ=100

They SHOULD BE for any new server or servers no older than say 3 years old:

CONFIG_HZ_1000=y 
CONFIG_HZ=1000

At the very least, Ubuntu should have a standard kernel package we can apt-get that has the clock set at 1000. 

Here's why:

So, we have recently spent a very long time trying to track down problems with our MySQL server.  

Our requirements are high concurrency, high load, and ACID transaction compliance.

We use InnoDB in MySQL for our database.  To increase the safety of the data integrity, we turn "sync-binlog=1" in the MySQL my.cnf.  We notice this basically killed all performance on our server...  essentialy 98% performance hit on our ubuntu64 10GB Ram with Raid-1 sas with battery backed up cache.

We tried configuring MySQL 4.1, 5.0, 5.1, 6.0 and the config logs hundreds of times.  Nothing we did would improve our performance.  

We finally tried to run some tests with sysbench that are heavy write benchmarks. And on a whim... we decided to try another linux distro (CentOS) just to see if that would be a factor... We appear to have hit some sort of operating system specific wall. 

Sysbench _50 TRHEADS_
OS	               [COLOR="Red"]ubuntu32	ubuntu64[/COLOR]	[COLOR="Lime"]centos32[/COLOR]
syncbinlog 0, WB	5600	12600	3800
syncbinlog 1, WB	[COLOR="Red"]348	294[/COLOR]	[COLOR="Lime"]1700[/COLOR]

Sysbench _1 THREAD_ 
OS	                ubuntu32	[COLOR="Lime"]ubuntu64	[/COLOR]centos32
syncbinlog 0, WB	4500	[COLOR="lime"]6000[/COLOR]	2300
syncbinlog 1, WB	3200	[COLOR="lime"]4356[/COLOR]	2300

Obviously... running just 1 thread is not acceptable for a database server.

The interesting thing to note is, the number of context switches in CENTOS will peak above 10,000 where UBUNTU will struggle to get past 3,000 context switches (doesn’t matter 32 bit or 64 bit).

We also notice that CENTOS has 1,000 intr/s while the system is idle where as ubuntu has 0. 

Our theory is that CENTOS is polling more often to see if it needs to switch contexts (which under heavy load… it does), and therefore, CENTOS is handling operations more efficiently. The servers we are testing on are all WriteBack enabled raid servers of different processor speeds (close enough though to get a feel for what is working an what is not working)

We have recompiled the UBUNTU kernel with the following modifications:

CONFIG_HZ_1000=y 
CONFIG_HZ=1000
(whereas previously ubuntu was set to a default of 100 hz).

After making these changes… the system behaves better (see the ubuntu64KRNPTCH column):

Sysbench 50 TRHEADS
OS	[COLOR="Red"]ubuntu32	ubuntu64[/COLOR]	centos32	[COLOR="Lime"]ubuntu64KRNPTCH[/COLOR]
syncbinlog 0, WB	5600	12600	3800	[COLOR="lime"]14000[/COLOR]
syncbinlog 1, WB	[COLOR="Red"]348[/COLOR]	[COLOR="red"]294[/COLOR]	1700	[COLOR="lime"]2100[/COLOR]


Sysbench 1 THREAD
OS	ubuntu32	ubuntu64	centos32	ubuntu64KRNPTCH
syncbinlog 0, WB	4500	6000	2300	5200
syncbinlog 1, WB	3200	4356	2300	2600


For now this appears to be the culprit (what a pain in the ass… I would never have dreamed in a million years the standard kernel configuration for ubuntu was the problem).

FYI, Here are our sysbench commands (be sure to change your mysql username and password):

./sysbench --num-threads=50 --test=oltp --oltp-test-mode=complex --oltp-table-size=100000 --oltp-distinct-ranges=0 --oltp-order-ranges=0 --oltp-sum-ranges=0 --oltp-simple-ranges=0 --oltp-point-selects=0 --oltp-range-size=0 --mysql-table-engine=innodb --mysql-host=127.0.0.1 --mysql-user=ROOT --mysql-password=PASSWORD prepare

./sysbench --num-threads=50 --test=oltp --oltp-test-mode=complex --oltp-table-size=100000 --oltp-distinct-ranges=0 --oltp-order-ranges=0 --oltp-sum-ranges=0 --oltp-simple-ranges=0 --oltp-point-selects=0 --oltp-range-size=0 --mysql-table-engine=innodb --mysql-host=127.0.0.1 --mysql-user=ROOT --mysql-password=PASSWORD run


Side Notes:
We are aware that Ubuntu has a rt (realtime kernel); however, the realtime rt kernel does not appear to work on our Dell 1950/2950's  (we're investigating why).  Even the most basic commands like "ls" and "su" don't work.  Will post more feedback on the realtime kernel here soon.

---

### Post by Macchi on 2009-01-14
Thank you theparanoidone for sharing your experiences! 

I was hoping to use the Ubuntu Server "out-of-the-box" for some applications but realize that I cannot blindly assume that it will perform efficiently. Some form of benchmarking and tweaking maybe necessary.

It would be very nice if you could make your kernels or config settings available for more people around here. But the best alternative would be if Canonical and/or the server development could add it to the repositories.

---

### Post by theparanoidone on 2009-01-15
so... more feedback... apparently there are a lot of posts regarding poor i/o performance... and no one being able to connect the dots.  slashdot just ran an article about these types of problems being related to a specific kernel bug:


this is on slashdot randomly last night:

[http://it.slashdot.org/article.pl?sid=09/01/15/049201](http://it.slashdot.org/article.pl?sid=09/01/15/049201)

[http://bugzilla.kernel.org/show_bug.cgi?id=7372](http://bugzilla.kernel.org/show_bug.cgi?id=7372) (scroll to bottom first and read)
[http://bugzilla.kernel.org/show_bug.cgi?id=12309](http://bugzilla.kernel.org/show_bug.cgi?id=12309)
[http://bugzilla.kernel.org/attachment.cgi?id=19797](http://bugzilla.kernel.org/attachment.cgi?id=19797)


Funny enough... 
centos runs kernel 2.6.18
ubuntu runs kernel 2.6.24

apparently the bug doesn't exist in 2.6.17  (however there are reports of ext3 filesystem problems in 2.6.17  catch/22)

interesting tidbits i read in these posts:
"because the problem first occurs
on my centos system, when I updated from kernel-2.6.18-92.1.10.el5 to
kernel-2.6.18-92.1.13.el5. This patch was also used on Ubuntu Gutsy the first time, on which the problem first occurs on my old system. There is only a small slowdown on my centos system, but there is one."


Finally.. just to follow up regarding our kernel configuration... this is the only thing we changed:

#CONFIG_HZ_100=y 
#CONFIG_HZ=100
#change to:
CONFIG_HZ_1000=y 
CONFIG_HZ=1000

---

### Post by hyper_ch on 2009-01-15
maybe you should open a bug report / request on that issue.

---

### Post by Macchi on 2009-01-15
Yes, as *theparanoidone* pointed in the first place this is a trade-off issue on configuration parameters, besides the kernel bug. 

The mentioned trade-off is:
> 
#CONFIG_HZ_100=y
#CONFIG_HZ=100
#change to:
CONFIG_HZ_1000=y
CONFIG_HZ=1000 

It could be solved by choosing the high performance parameters on the 64 bit versions of the Ubuntu server while keeping the lower settings for 32 bit versions. The former most probably runs on modern hardware and aims at higher performance, while the later could be assumed to have budget constraints and modest hardware. Maybe this hass been already done. I read somewhere in the net about CONFIG_HZ=1000 and preemption choices before compiling the kernel for XEN virtualization hosts.

How about the PREEMPT parameter? Have you experimented with that?




(Clearly off-topic I could say that I know that Canonical has ambitions to climb up in the server market for business enterprises. Some official benchmarks around server performance would be a good addition in the marketing arsenal for the adoption of Ubuntu.)

---

### Post by theparanoidone on 2009-01-15
We are looking into the PREEMPT. We tried these... but not much effect:
CONFIG_PREEMPT_BKL=y
CONFIG_PREEMPT_VOLUNTARY=y
(whereas previously ubuntu had CONFIG_PREEMPT_NONE=y)

Does anyone know what other flags should be set off-hand for PREEMPT?

The linux-image-rt (real-time) package seemd to have the clock set at 1000 and all the preempt flags on. However, that kernel would freeze on our dell 2950 with 10GB ram / sas raid-1

Does anyone know why this would be causing it to freeze?  I don't know much about realtime packages other than they are for instrumentation usually... however... i don't see why this would freeze the machine.

Finally i did post to here (no response yet):
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/131094)

I tried posting to bugs (but the site was down-ish, perhaps slashdotted):
[http://bugzilla.kernel.org/show_bug.cgi?id=12309](http://bugzilla.kernel.org/show_bug.cgi?id=12309)

---

### Post by theparanoidone on 2009-01-15
Quick followup in case anyone is wondering:  

UBUNTU - Linux la 2.6.24-23-server #1 SMP Thu Nov 27 18:45:02 UTC 2008 x86_64 GNU/Linux.  -- BAD BAD BAD

CENTOS - Linux lv 2.6.18-92.el5 #1 SMP Tue Jun 10 18:51:06 EDT 2008 x86_64 x86_64 x86_64 GNU/Linux   -- BETTER

---

### Post by theparanoidone on 2009-01-15
feedback... rolling back to ubuntu 6.06 with kernel 2.6.15 slightly fixes the problem.  still have to configure with clock set to 1000

---

