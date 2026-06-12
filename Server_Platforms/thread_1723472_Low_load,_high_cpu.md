---
title: "Low load, high cpu"
date: 2011-04-07
forum: Server Platforms
---

### Post by Guardsystems on 2011-04-07
We run a web server on a litle older version of Ubuntu (9.04). (There are som good reasons for doing that)

However. We do have som monitoring systems that reads out the load on the servers to give us graphs to both tell us that the system i healthy and to also tell us if we getting close to limit of needing more power.

On all our servers the "load average" usually follows the amount of work load the server got, but for the one with Ubuntu we have some strange readong. I have a steady CPU usage (user) of 15 - 25%, but the load is rock bottom 0.00. Here is a typical reading of top:
top - 11:06:43 up 2 days, 21:09,  4 users,  load average: 0.00, 0.00, 0.00
Tasks: 243 total,   2 running, 241 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.9%us,  1.1%sy,  0.0%ni, 82.3%id,  0.2%wa,  0.1%hi,  0.5%si,  0.0%st

Why is the load not sowing anything of what the CPU does?

And a addtional question in case anyone knows: This server had 4x CPU (or cores actually). When is it working at "full speed". At 100% of 400% CPU?

(BTW: The server running 64 bit version if it matters)

---

### Post by elico on 2011-04-07
on what are you talking about???
if it is saying that the load average is 0.0 then it might be the statistics or some lib or bin is damaged\wrong access permissions.
my top is:
Cpu(s):  0.2%us,  0.0%sy,  0.0%ni, 99.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
and my system is pretty often comes to 200% +  load.

did you tried htop?

i really recommend htop.

it will work at 400% when you will have some software that can use it and will need to use it.

most of the servers around the world are working at 15% and lower and this is one of the reasons for VISUALIZATION 
solutions.
to make use of the whole cpu power.(not always smart).

---

### Post by Guardsystems on 2011-04-07
I saw that I was a bit wrong. It shows 0.01 - 0.05 from time to time but soon go down again to 0.00.

htop shows the same. All 4 CPU at 15 - 25 % in average (goes under and over, but stays mostly there) And load avrage of 0.00 (mostlty)

I cant copy out of htop so here are another other pasting where load avrage is not 0,00 (Just had to wait for it to happend.) I think the rutine calculate avrage load is doing something stange, just cant find anything about it.

top - 13:02:41 up 2 days, 23:05,  4 users,  load average: 0.03, 0.01, 0.00
Tasks: 244 total,   1 running, 243 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.2%us,  1.4%sy,  0.0%ni, 83.0%id,  0.0%wa,  0.0%hi,  0.5%si,  0.0%st

And here is a typical "top 20" lines of top.
top - 12:54:25 up 2 days, 22:56,  4 users,  load average: 0.00, 0.01, 0.00
Tasks: 244 total,   2 running, 242 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.0%us,  1.3%sy,  0.0%ni, 83.4%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:  18534352k total,  2145604k used, 16388748k free,   134180k buffers
Swap:  9900024k total,        0k used,  9900024k free,   803156k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND  
18763 www-data  20   0  165m 9904 4160 S    2  0.1   0:56.59 apache2
17758 www-data  20   0  169m  14m 4524 S    2  0.1   0:53.93 apache2
18736 www-data  20   0  170m  15m 4520 S    2  0.1   0:55.22 apache2
17741 www-data  20   0  168m  12m 4528 S    2  0.1   0:54.53 apache2
17750 www-data  20   0  165m  10m 4604 S    2  0.1   0:56.58 apache2
17788 www-data  20   0  168m  13m 4628 S    2  0.1   0:51.89 apache2
18739 www-data  20   0  168m  12m 4524 S    2  0.1   0:53.47 apache2
18758 www-data  20   0  165m  10m 4600 S    2  0.1   0:55.32 apache2
17742 www-data  20   0  169m  14m 4784 S    1  0.1   0:54.11 apache2
17757 www-data  20   0  168m  13m 4620 S    1  0.1   0:51.92 apache2
17763 www-data  20   0  168m  12m 4168 S    1  0.1   0:53.46 apache2
17774 www-data  20   0  169m  14m 4520 S    1  0.1   0:52.74 apache2
17813 www-data  20   0  165m  10m 4532 S    1  0.1   0:56.57 apache2

---

