---
title: "Diagnose Why Server Slow"
date: 2014-12-11
forum: Server Platforms
---

### Post by Lubd on 2014-12-11
Hi,

I am running Ubuntu Server 11.04. I have SugarCRM, a couple of Wordpress websites and a Ruby Webapp running.

I have done full rootkit and malware scans and found nothing.

Examining processes using Top shows that even with zero CPU load (middle of the night and no users) that the memory usage is constantly around 3GB out of an available 4GB.


Here is a snapshot of the Top command:

```
 top - 05:33:28 up 10 days,  6:59,  1 user,  load average: 0.00, 0.03, 0.01
Tasks: 106 total,   1 running, 104 sleeping,   1 stopped,   0 zombie
Cpu(s):  0.3%us,  0.2%sy,  0.0%ni, 99.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4194304k total,  3000268k used,  1194036k free,        0k buffers
Swap:   418816k total,     2116k used,   416700k free,  2053624k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  265 root      20   0 76252  59m 1748 S  0.3  1.5  49:56.11 ruby
  402 root      20   0 28200  16m 1728 S  0.3  0.4  36:47.74 ruby
  573 root      20   0 28188  16m 1708 S  0.3  0.4  36:53.37 ruby
 2232 root      20   0  2584 1220  952 R  0.3  0.0   0:00.47 top
    1 root      20   0  2612 1540 1292 S  0.0  0.0   0:04.47 init
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd/155577
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper/1555778
  104 root      20   0  2184  860  856 S  0.0  0.0   0:00.00 xinetd
  118 root      20   0  2224  908  744 S  0.0  0.0   0:04.31 cron
  140 syslog    20   0  2028  732  592 S  0.0  0.0   7:42.74 syslogd
  188 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:07.89 mysqld
  227 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:00.00 mysqld
  228 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:01.73 mysqld
  229 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:00.01 mysqld
  230 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:01.02 mysqld
  256 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:53.69 mysqld
  257 mysql     20   0  671m 129m 6824 S  0.0  3.2   1:08.28 mysqld
  258 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:02.96 mysqld
  259 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:12.32 mysqld
  260 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:01.99 mysqld
  303 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:04.52 mysqld
  326 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:04.87 mysqld
  952 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:04.05 mysqld
 1107 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:03.68 mysqld
12841 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:02.14 mysqld
22904 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:01.37 mysqld
31886 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:24.80 mysqld
25918 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:24.07 mysqld
10876 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:51.92 mysqld
10879 mysql     20   0  671m 129m 6824 S  0.0  3.2   1:00.08 mysqld
19703 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:18.38 mysqld
23158 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:13.27 mysqld
 3328 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:13.18 mysqld
 5932 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:11.81 mysqld
 5933 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:10.45 mysqld
12789 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:04.14 mysqld

```
Can anyone explain why it is using so much memory and if that would be the reason why things are grinding to a crawl when the server has users? Also why are there so many mysqld processes? Please help me to solve this issue and improve the server configuration. Questions most welcome.

Cheers.

S.

P.S. I am pretty new to server stuff so please be gentle.

---

### Post by bab1 on 2014-12-11
> **Lubd said:**
> Hi,

I am running Ubuntu Server 11.04. I have SugarCRM, a couple of Wordpress websites and a Ruby Webapp running.

I have done full rootkit and malware scans and found nothing.

Examining processes using Top shows that even with zero CPU load (middle of the night and no users) that the memory usage is constantly around 3GB out of an available 4GB.


Here is a snapshot of the Top command:

top - 05:33:28 up 10 days,  6:59,  1 user,  load average: 0.00, 0.03, 0.01
Tasks: 106 total,   1 running, 104 sleeping,   1 stopped,   0 zombie
Cpu(s):  0.3%us,  0.2%sy,  0.0%ni, 99.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4194304k total,  3000268k used,  1194036k free,        0k buffers
Swap:   418816k total,     2116k used,   416700k free,  2053624k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  265 root      20   0 76252  59m 1748 S  0.3  1.5  49:56.11 ruby
  402 root      20   0 28200  16m 1728 S  0.3  0.4  36:47.74 ruby
  573 root      20   0 28188  16m 1708 S  0.3  0.4  36:53.37 ruby
 2232 root      20   0  2584 1220  952 R  0.3  0.0   0:00.47 top
    1 root      20   0  2612 1540 1292 S  0.0  0.0   0:04.47 init
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd/155577
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper/1555778
  104 root      20   0  2184  860  856 S  0.0  0.0   0:00.00 xinetd
  118 root      20   0  2224  908  744 S  0.0  0.0   0:04.31 cron
  140 syslog    20   0  2028  732  592 S  0.0  0.0   7:42.74 syslogd
  188 mysql     20   0  671m 129m 6824 S  0.0  3.2   0:07.89 mysqld
...

Can anyone explain why it is using so much memory and if that would be the reason why things are grinding to a crawl when the server has users? Also why are there so many mysqld processes? Please help me to solve this issue and improve the server configuration. Questions most welcome.

Cheers.

S.

P.S. I am pretty new to server stuff so please be gentle.

I don't see anything out of order.  The machine is just idling according to this```
top - 05:33:28 up 10 days, 6:59, 1 user,** load average: 0.00, 0.03, 0.01**
```

You only have 1 process active out of 100+ according to this```

Tasks: 106 total,   **1 running**, 104 sleeping,   1 stopped,   0 zombie
```

Linux tends to use RAM and not release it until some other process asks for it.  Multiple instances of MySQL are common.  If you are concerned, shut down the  SugarCRM,  Wordpress and Ruby and see what happens.  The "things are grinding to a crawl" is not indicated by your *top* listing.

Try a post again when you really have the machine "at a crawl".  When you post use the [noparse]```
 
```[/noparse] blocks.  The easy way to do this is to use the [SIZE=5]#[/SIZE] icon at the top of the ***advanced editor***.

---

### Post by sammiev on 2014-12-11
When I used top it would show me what I was using but as I closed programs the memory stayed at same rate.
I tried htop after using top and got a different output which seemed to match what I was using.

---

### Post by mörgæs on 2014-12-11
Are you aware that 11.04 is unsupported?

---

### Post by houstonbofh on 2014-12-15
check out [www.linuxatemyram.com](www.linuxatemyram.com) for why your memory is full.

---

