---
title: "high load! need advice."
date: 2006-12-23
forum: Server Platforms
---

### Post by emocan on 2006-12-23
need advice with high load 

server details:
P4, 3.0GHz
3GB RAM
Raid1 2HDD (seagate barracuda)

thanks in advance.


top - 03:56:51 up 3 days,  2:30,  1 user,  load average: 106.91, 103.13, 75.74
Tasks: 543 total,  90 running, 453 sleeping,   0 stopped,   0 zombie
Cpu(s): 89.4%us, 10.4%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   3116428k total,  3005588k used,   110840k free,    77840k buffers
Swap: 19599224k total,      140k used, 19599084k free,  1620528k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8614 www-data  17   0 24232 9148 3672 R    4  0.3   0:12.42 apache2
 8722 www-data  16   0 24436 9376 3700 S    4  0.3   0:09.36 apache2
 8231 www-data  16   0 25740  10m 3832 S    3  0.3   0:15.04 apache2
 8248 www-data  16   0 25684  10m 3828 S    3  0.3   0:14.94 apache2
 8531 www-data  16   0 24380 9300 3676 S    3  0.3   0:11.53 apache2
 9231 www-data  16   0 24556 9468 3668 S    3  0.3   0:11.83 apache2
 8229 www-data  15   0 25736  10m 3844 S    3  0.3   0:12.07 apache2
 8470 www-data  15   0 24240 9144 3660 S    3  0.3   0:12.08 apache2
 8988 www-data  16   0 24240 9164 3680 S    3  0.3   0:08.93 apache2
 8247 www-data  16   0 26372  11m 4680 S    3  0.4   0:09.25 apache2
 8416 www-data  16   0 24240 9160 3676 S    3  0.3   0:12.23 apache2
 8550 www-data  16   0 24352 9308 3712 S    3  0.3   0:09.29 apache2
 9466 www-data  15   0 24244 9156 3668 S    3  0.3   0:11.44 apache2
 7837 www-data  16   0 25916  11m 4264 S    2  0.4   0:16.35 apache2
 7996 www-data  16   0 26792  12m 4352 S    2  0.4   0:20.11 apache2
 8074 www-data  17   0 26196  11m 3876 S    2  0.4   0:17.11 apache2
 8262 www-data  16   0 24904 9828 3728 S    2  0.3   0:12.46 apache2
 8404 www-data  16   0 24424 9376 3708 S    2  0.3   0:10.23 apache2
 8454 www-data  16   0 24436 9360 3680 S    2  0.3   0:09.60 apache2
 8707 www-data  17   0 24452 9396 3700 S    2  0.3   0:10.19 apache2
 7846 www-data  16   0 26204  11m 3872 S    2  0.4   0:17.11 apache2
 7916 www-data  16   0 29500  14m 4304 S    2  0.5   0:15.31 apache2
 8071 www-data  16   0 26028  11m 4256 S    2  0.4   0:15.61 apache2
 8097 www-data  16   0 28788  13m 3924 S    2  0.4   0:13.88 apache2
 8115 www-data  16   0 26012  10m 3844 S    2  0.4   0:15.14 apache2
 8124 www-data  16   0 25624  10m 3856 S    2  0.3   0:16.23 apache2
 8241 www-data  16   0 25860  10m 3844 S    2  0.4   0:12.59 apache2
 8256 www-data  16   0 24248 9164 3672 S    2  0.3   0:13.37 apache2
 8425 www-data  16   0 24388 9312 3680 S    2  0.3   0:10.81 apache2
 8533 www-data  16   0 24248 9192 3700 S    2  0.3   0:10.61 apache2
 8595 www-data  16   0 24228 9132 3660 S    2  0.3   0:10.44 apache2
 8597 www-data  16   0 24252 9188 3696 S    2  0.3   0:11.61 apache2
 8612 www-data  16   0 24248 9172 3680 S    2  0.3   0:09.96 apache2
 8704 www-data  16   0 24248 9172 3680 S    2  0.3   0:07.86 apache2
 8705 www-data  16   0 24256 9168 3668 S    2  0.3   0:09.74 apache2
 8708 www-data  16   0 24224 9128 3660 S    2  0.3   0:10.48 apache2
 8880 www-data  16   0 24404 9340 3696 S    2  0.3   0:09.40 apache2
 8881 www-data  15   0 24224 9112 3660 S    2  0.3   0:10.53 apache2
 8972 www-data  16   0 24380 9328 3708 S    2  0.3   0:09.08 apache2
 8987 www-data  16   0 24260 9184 3680 S    2  0.3   0:08.86 apache2
 8992 www-data  16   0 24392 9328 3692 S    2  0.3   0:10.04 apache2
 9096 www-data  16   0 24248 9160 3668 S    2  0.3   0:07.79 apache2
 9233 www-data  16   0 24656 9600 3700 S    2  0.3   0:09.77 apache2
 9320 www-data  16   0 24240 9164 3680 S    2  0.3   0:10.89 apache2

---

### Post by kidders on 2006-12-23
What kind of apps are you running on your web server?

---

### Post by emocan on 2006-12-24
hi kidders


MYSQL 5.0.24a 
Apache 2
PHP Version 5.1.6
ubuntu 6.10 server ( no graphical interface )
like you see it is the apach2 consuming all the CPU.

---

### Post by bikeboy on 2006-12-24
It could (read might) help if you limit the number of child processes apache is allowed to spawn. Although that is normally done for limiting memory usage, having that many apache processes all taking a little cpu time adds up. I'm not sure of the best way to do this in apache2 but have a look at these:

[http://httpd.apache.org/docs/2.0/mod/core.html#rlimitcpu](http://httpd.apache.org/docs/2.0/mod/core.html#rlimitcpu)
[http://httpd.apache.org/docs/2.0/mod/core.html#rlimitnproc](http://httpd.apache.org/docs/2.0/mod/core.html#rlimitnproc)

---

### Post by kidders on 2006-12-24
I wonder if something (a PHP script maybe) is failing to terminate when it's supposed to. This shouldn't really happen, since they tend to have a max execution time of around 30 seconds, but it's still my best guess. :-k

It might be interesting to use lsof to see what files the apache processes have open, maybe. Perhaps you've checked this, and some of the other obvious avenues (/var/log/messages, /var/log/apache2/, etc.) for clues already, but just in case, I thought I'd mention it.

How frustrating!

---

### Post by emocan on 2006-12-24
bikeboy I am going check the links 

Kidders Don't know if it is php I am using vbulleting with high traffic.

my previous server was fedoracore 3 some times I had 1500 users online without any problem. now it is not possible to have 600.

---

### Post by kidders on 2006-12-29
That's quite a contrast! I wonder if you've accidentally found a bug in something. :-k

---

