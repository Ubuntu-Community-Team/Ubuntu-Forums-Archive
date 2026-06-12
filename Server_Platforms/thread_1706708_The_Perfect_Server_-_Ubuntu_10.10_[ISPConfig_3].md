---
title: "The Perfect Server - Ubuntu 10.10 [ISPConfig 3]"
date: 2011-03-14
forum: Server Platforms
---

### Post by maildemon on 2011-03-14
Hello, 

I have 3ghz/1gb ram PC used for LAMP server. 
Several times installed ISPConfig 3, by guide posted in howtoforge.com steb by step. Then also reinstalled only as LAMP server. Everything is just wonderfull except one thing.

I just installed latest wordress on it, and its kind a slow. When i do refresh about 30 times, server load looks like this:

```
top - 18:10:34 up 45 min,  1 user,  load average: 90.92, 45.12, 18.20
Tasks: 230 total,   1 running, 229 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.0%us,  4.9%sy,  0.0%ni,  0.0%id, 89.6%wa,  0.0%hi,  0.4%si,  0.0%st
Mem:    370416k total,   366520k used,     3896k free,      660k buffers
Swap:  1155068k total,   980608k used,   174460k free,    13836k cached
```

top shows

```
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
   26 root      20   0     0    0    0 D  2.0  0.0   0:03.81 [kswapd0]
27060 www-data  20   0 57824 8564 1428 D  0.7  2.3   0:00.42 /usr/sbin/apache2 -k start
27059 www-data  20   0 56792 8004 1308 D  0.6  2.2   0:00.35 /usr/sbin/apache2 -k start
27119 www-data  20   0 57032 8740 1456 D  0.6  2.4   0:00.33 /usr/sbin/apache2 -k start
27052 www-data  20   0 56536 8000 1292 D  0.5  2.2   0:00.34 /usr/sbin/apache2 -k start
27082 www-data  20   0 56792 8404 1324 D  0.5  2.3   0:00.33 /usr/sbin/apache2 -k start
27085 www-data  20   0 56792 8996 1316 D  0.5  2.4   0:00.34 /usr/sbin/apache2 -k start
27101 www-data  20   0 56792 8128 1324 D  0.5  2.2   0:00.31 /usr/sbin/apache2 -k start
27118 www-data  20   0 56772 7276 1352 D  0.5  2.0   0:00.32 /usr/sbin/apache2 -k start
27112 www-data  20   0 56792 7620 1324 D  0.5  2.1   0:00.31 /usr/sbin/apache2 -k start
27088 www-data  20   0 55484 6652 1220 D  0.5  1.8   0:00.30 /usr/sbin/apache2 -k start
27117 www-data  20   0 55484 5400 1176 D  0.5  1.5   0:00.29 /usr/sbin/apache2 -k start
27051 www-data  20   0 56028 6784 1172 D  0.4  1.8   0:00.31 /usr/sbin/apache2 -k start
27091 www-data  20   0 56028 6660 1228 D  0.4  1.8   0:00.28 /usr/sbin/apache2 -k start
27092 www-data  20   0 56028 6456 1208 D  0.4  1.7   0:00.29 /usr/sbin/apache2 -k start
27100 www-data  20   0 56028 6092 1208 D  0.4  1.6   0:00.28 /usr/sbin/apache2 -k start
27102 www-data  20   0 55484 5624 1208 D  0.4  1.5   0:00.30 /usr/sbin/apache2 -k start
27104 www-data  20   0 55980 7044 1324 D  0.4  1.9   0:00.30 /usr/sbin/apache2 -k start
27114 www-data  20   0 55484 6360 1188 D  0.4  1.7   0:00.28 /usr/sbin/apache2 -k start
25200 mysql     20   0  179m    0    0 D  0.4  0.0   0:02.31 /usr/sbin/mysqld
27103 www-data  20   0 53672 4620 1180 D  0.3  1.2   0:00.23 /usr/sbin/apache2 -k start
27054 www-data  20   0 52304 4868 1160 D  0.3  1.3   0:00.24 /usr/sbin/apache2 -k start
27087 www-data  20   0 52068 4704 1160 D  0.3  1.3   0:00.23 /usr/sbin/apache2 -k start
27069 www-data  20   0 52068 4244 1128 D  0.3  1.1   0:00.21 /usr/sbin/apache2 -k start
27078 www-data  20   0 52068 4716 1152 D  0.3  1.3   0:00.21 /usr/sbin/apache2 -k start
27099 www-data  20   0 51932 4112 1272 D  0.3  1.1   0:00.20 /usr/sbin/apache2 -k start
27071 www-data  20   0 51932 4260 1204 D  0.3  1.2   0:00.21 /usr/sbin/apache2 -k start
27079 www-data  20   0 51932 3852 1208 D  0.3  1.0   0:00.21 /usr/sbin/apache2 -k start
27098 www-data  20   0 52068 3800 1160 D  0.3  1.0   0:00.20 /usr/sbin/apache2 -k start
27070 www-data  20   0 52068 4544 1156 D  0.2  1.2   0:00.21 /usr/sbin/apache2 -k start
27076 www-data  20   0 50780 3268 1168 D  0.2  0.9   0:00.19 /usr/sbin/apache2 -k start
27072 www-data  20   0 51040 3548 1172 D  0.2  1.0   0:00.20 /usr/sbin/apache2 -k start
27083 www-data  20   0 50188 2720 1164 D  0.2  0.7   0:00.17 /usr/sbin/apache2 -k start
27184 www-data  20   0 47192 2828 1384 D  0.2  0.8   0:00.09 /usr/sbin/apache2 -k start
```


In the same time server is just down and cant do anything. Complete standstill.

I tried this on two different machines, also the same.

And thats it. Please give me any clue where could be the prob.

---

### Post by falko on 2011-03-15
Do you have a PHP opcode cacher such as eAccelerator, Xcache, or APC installed?

Did you enable caching in Wordpress?

---

