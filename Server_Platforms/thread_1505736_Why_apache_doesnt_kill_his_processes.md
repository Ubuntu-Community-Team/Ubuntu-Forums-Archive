---
title: "Why apache doesnt kill his processes ?"
date: 2010-06-09
forum: Server Platforms
---

### Post by limpbrains on 2010-06-09
Im using fresh ubuntu 10.04 64bit apache2-mpm-itk with php 5.2 from karmic I've istalled 5.2 using this [this script]("http://mrkandy.wordpress.com/2010/04/16/install-php-5-2-x-in-ubuntu-10-04-lucid/")

apache2 settings:

```
StartServers        5
MinSpareServers     5
MaxSpareServers     30
MaxClients          30
MaxRequestsPerChild 200
```
I've tried strace -p and get the following

```
sched_yield()                           = 0
sched_yield()                           = 0
sched_yield()                           = 0
sched_yield()                           = 0
sched_yield()                           = 0
sched_yield()                           = 0
sched_yield()                           = 0^C
Process 16839 detached
```
htop displays this picture

```
 3887 vu2032    20   0  337M 11644  2116 R 78.0  0.1  1:00.30 /usr/sbin/apache2 -k start
 3891 vu2017    20   0  337M 11308  1828 R 64.0  0.1  0:58.64 /usr/sbin/apache2 -k start
 3893 vu2032    20   0  337M 11652  2120 R 57.0  0.1  1:01.35 /usr/sbin/apache2 -k start
 3896 vu2033    20   0  337M 11248  1776 R 57.0  0.1  0:36.78 /usr/sbin/apache2 -k start
 3842 vu2033    20   0  337M 11244  1772 R 51.0  0.1  2:00.18 /usr/sbin/apache2 -k start
 3857 vu2025    20   0  337M 11288  1812 R 49.0  0.1  1:38.70 /usr/sbin/apache2 -k start
All sites works under php

```
All logs clear

---

### Post by Xianath on 2010-06-09
Apache would start with <StartServers> child processes, then fork additional ones as request came in, while trying to keep <MinSpareServers> processes on the side to handle new requests. You're seeing 6 processes, one being the parent and five being <MinSpareServers>. This was the 1.x behavior, not sure how much it changed in 2.x-mpm but seeing as how the options are still the same...

---

### Post by cdenley on 2010-06-09
That looks normal to me. What is the problem?

---

### Post by limpbrains on 2010-06-09
Time to time apache starting eat 100CPU and LA become more than 10.

I have showed only part of the htop output. I have 2 quad core Intel CPU. And ~ 30 apache processes.

As you can see each apache process eats ~ 70 CPU%.

From that moment server works very slowly.

---

### Post by dtfinch on 2010-06-09
Is it running any scripts (like .php pages) that might account for the cpu usage?

---

### Post by limpbrains on 2010-06-10
> **dtfinch said:**
> Is it running any scripts (like .php pages) that might account for the cpu usage?
I have few sites all running by mod-php but they cant create this  cpu usage. 

using AB I've benchmarked my server. It can serve 1000 requests per second.
running AB dont reproduce the problem after he finished everything works fine.

No. During hiload of CPU I've stopted nginx frontend. And still have CPU 100%

---

