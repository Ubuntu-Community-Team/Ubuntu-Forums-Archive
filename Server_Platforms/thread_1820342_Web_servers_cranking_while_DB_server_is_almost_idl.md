---
title: "Web servers cranking while DB server is almost idle"
date: 2011-08-07
forum: Server Platforms
---

### Post by NetDoc on 2011-08-07
I own a rather large website/forum devoted to Scuba utilizing vBulletin. The problem is that its become INCREDIBLY slow as of late. I have three Ubuntu web servers under a single Ubuntu load balancer and they draw from a CentOS 5 DB server running MYSQL. 

Here are my concerns:

I am thinking that they are all 32 bit rather than 64 bit.
I am thinking that the problem is an IO issue. 

Alpha (DB Server)
```
top - 15:22:27 up 50 days, 21:40,  1 user,  load average: 0.54, 0.60, 0.60
Tasks: 183 total,   1 running, 182 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.7%us,  0.7%sy,  0.0%ni, 95.1%id,  1.2%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:  16439840k total, 16315116k used,   124724k free,   144620k buffers
Swap:  2096472k total,    59392k used,  2037080k free,  3031716k cached

```
Beta (Web Server)
```
top - 15:30:14 up 2 days,  4:08,  1 user,  load average: 3.48, 3.43, 3.20
Tasks: 170 total,   6 running, 164 sleeping,   0 stopped,   0 zombie
Cpu(s): 27.4%us,  0.9%sy,  0.0%ni, 70.9%id,  0.3%wa,  0.0%hi,  0.4%si,  0.0%st
Mem:   4050108k total,  2937328k used,  1112780k free,   110240k buffers
Swap:  9727224k total,    16680k used,  9710544k free,   885044k cached 
```
Gamma (Web Server)
```
top - 15:31:49 up 2 days,  4:08,  1 user,  load average: 3.32, 3.30, 3.21
Tasks: 172 total,   3 running, 169 sleeping,   0 stopped,   0 zombie
Cpu(s): 27.6%us,  0.9%sy,  0.0%ni, 70.8%id,  0.4%wa,  0.0%hi,  0.4%si,  0.0%st
Mem:   4050108k total,  3053536k used,   996572k free,   103892k buffers
Swap:  9727224k total,    16848k used,  9710376k free,   945872k cached

```
Delta (Web Server) 
```
top - 15:32:44 up 2 days,  4:07,  1 user,  load average: 3.12, 3.12, 3.13
Tasks: 171 total,   4 running, 167 sleeping,   0 stopped,   0 zombie
Cpu(s): 27.2%us,  0.9%sy,  0.0%ni, 71.1%id,  0.3%wa,  0.0%hi,  0.4%si,  0.0%st
Mem:   4050112k total,  2982572k used,  1067540k free,   102172k buffers
Swap:  9727224k total,    18684k used,  9708540k free,   922608k cached
```

---

### Post by NetDoc on 2011-08-07
Alpha
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:48:33:B6:5C
          inet addr:69.28.64.166  Bcast:69.28.64.175  Mask:255.255.255.240
          inet6 addr: fe80::230:48ff:fe33:b65c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:121487546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18812 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:19546280463 (18.2 GiB)  TX bytes:1230133 (1.1 MiB)
          Memory:da320000-da340000

eth1      Link encap:Ethernet  HWaddr 00:30:48:33:B6:5D
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe33:b65d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10486328219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20497968314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1653275984092 (1.5 TiB)  TX bytes:27204823991971 (24.7 TiB)
          Memory:da360000-da380000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1745330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1745330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:155533762 (148.3 MiB)  TX bytes:155533762 (148.3 MiB)

```

Beta
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:48:32:c3:58
          inet addr:192.168.2.20  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe32:c358/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:358929291 errors:0 dropped:161 overruns:0 frame:0
          TX packets:165882205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:461799861831 (430.0 GB)  TX bytes:21854498064 (20.3 GB)
          Base address:0x2000 Memory:c8200000-c8220000

eth1      Link encap:Ethernet  HWaddr 00:30:48:32:c3:59
          inet addr:69.28.64.167  Bcast:69.28.64.175  Mask:255.255.255.240
          inet6 addr: fe80::230:48ff:fe32:c359/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1080175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21046100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:268225610 (255.7 MB)  TX bytes:22849535301 (21.2 GB)
          Base address:0x2020 Memory:c8220000-c8240000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:674797 errors:0 dropped:0 overruns:0 frame:0
          TX packets:674797 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:44074238 (42.0 MB)  TX bytes:44074238 (42.0 MB)

lo:0      Link encap:Local Loopback
          inet addr:69.28.64.162  Mask:255.255.255.255
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
```

Gamma
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:48:32:c1:3e
          inet addr:192.168.2.30  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe32:c13e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:358607407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166665584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:461069314433 (429.4 GB)  TX bytes:23075074748 (21.4 GB)
          Base address:0x2000 Memory:c8200000-c8220000

eth1      Link encap:Ethernet  HWaddr 00:30:48:32:c1:3f
          inet addr:69.28.64.168  Bcast:69.28.64.175  Mask:255.255.255.240
          inet6 addr: fe80::230:48ff:fe32:c13f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1088383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20615356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:275874339 (263.0 MB)  TX bytes:22428764531 (20.8 GB)
          Base address:0x2020 Memory:c8220000-c8240000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:675649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:675649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:43563685 (41.5 MB)  TX bytes:43563685 (41.5 MB)

lo:0      Link encap:Local Loopback
          inet addr:69.28.64.162  Mask:255.255.255.255
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
```

Delta
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:48:32:c0:1c
          inet addr:192.168.2.40  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe32:c01c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:359314779 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168148959 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:460924373339 (429.2 GB)  TX bytes:23449760994 (21.8 GB)
          Base address:0x2000 Memory:c8200000-c8220000

eth1      Link encap:Ethernet  HWaddr 00:30:48:32:c0:1d
          inet addr:69.28.64.169  Bcast:69.28.64.175  Mask:255.255.255.240
          inet6 addr: fe80::230:48ff:fe32:c01d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1080512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20596927 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:267710809 (255.3 MB)  TX bytes:22440739198 (20.8 GB)
          Base address:0x2020 Memory:c8220000-c8240000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:672246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:672246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:43163609 (41.1 MB)  TX bytes:43163609 (41.1 MB)

lo:0      Link encap:Local Loopback
          inet addr:69.28.64.162  Mask:255.255.255.255
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
```

---

### Post by NetDoc on 2011-08-07
So the [size=4]**BIG QUESTION**[/size] is: 

Where do I go from here? What else do I need to know to diagnose this throughput problem? I could just add more web servers, but is that the answer?

---

### Post by NetDoc on 2011-08-07
Here is the result of uname -a

Alpha
```
Linux alpha.scubaboard.com 2.6.18-128.1.10.el5 #1 SMP Thu May 7 10:35:59 EDT 2009 x86_64 x86_64 x86_64 GNU/Linux

```
Beta
```
Linux beta 2.6.24-23-server #1 SMP Wed Apr 1 22:14:30 UTC 2009 x86_64 GNU/Linux

```
Gamma
```
Linux gamma 2.6.24-23-server #1 SMP Wed Apr 1 22:14:30 UTC 2009 x86_64 GNU/Linux
```
Delta
```
Linux delta 2.6.24-24-server #1 SMP Wed Apr 15 15:41:09 UTC 2009 x86_64 GNU/Linux

```

So I guess that they are all 64 bit servers.

---

### Post by SeijiSensei on 2011-08-07
What's remarkable is how busy the web servers are.  Usually I attribute vBulletin lags to slow DB performance on the back end.

Maybe you should consider using a PHP "accelerator" which can improve performance by caching frequently-used code.  You should also look into methods to improve PHP's performance itself.  The default php.ini that comes with most distributions isn't designed for high-traffic sites like yours.  Apache can be tuned for high-traffic sites as well.

This article may have some helpful tips, too: [http://docs.moodle.org/20/en/Performance#Web_server_performance](http://docs.moodle.org/20/en/Performance#Web_server_performance)

I assume you're running PHP as an Apache module and not as a cgi-bin executable.

---

### Post by NetDoc on 2011-08-08
Interesting comments. Actually, I have no idea if we are running a PHP accelerator or if its an Apache Module or run as a cgi-bin executable. How can I find this out?

---

### Post by SeijiSensei on 2011-08-08
Did you set up the servers yourself?  If so, you'd know whether you installed an accelerator.  I'm guessing you don't use one.  I did a bit of browsing and discovered that there's an Ubuntu [package]("http://packages.ubuntu.com/lucid/php-apc") for [APC]("http://php.net/apc").

If you installed the standard Ubuntu LAMP packages, you're using the Apache module version of PHP.  It's rare these days for anyone to use the cgi-bin method.

One other option is to try a different web server instead of Apache like, perhaps, [lighttpd]("http://www.lighttpd.net/").

---

### Post by NetDoc on 2011-08-08
Correct, if I had set up the servers I would know. I didn't so I don't. 

I saw a cgi related comment when I ran [http://beta.scubaboard.com/forums/test.php](http://beta.scubaboard.com/forums/test.php)

---

### Post by SeijiSensei on 2011-08-08
You're using the Apache module version; there's an entry for mod_php5 under apache2handler.

More intriguingly, your server also has the APC accelerator module installed.  Perhaps it needs some tuning?  I don't use it so I can't help with that.

I wonder, though, what happens when an accelerator is used with a site where nearly all the content is dynamically generated.  I would think most vBulletin forums are not well-suited to caching because their content is changing so continuously.  I suggested trying an accelerator just because it's an obvious strategy to improve performance.  Maybe you should try turning off APC on one of the web servers and see if it changes anything?  

I'm hardly an expert on these matters, but it doesn't seem that your question has elicited any other suggestions, so I'm afraid you're stuck with me for the moment!

---

### Post by rubylaser on 2011-08-08
Have you looked at some of the ideas on this page? It's older, but the concepts still apply to running a high traffic website.
[http://linuxbox.co.uk/vbulletin_performance_tuning.php]("http://linuxbox.co.uk/vbulletin_performance_tuning.php")

He also has a caching module...
[http://linuxbox.co.uk/vbulletin_caching_with_lbcache.php]("http://linuxbox.co.uk/vbulletin_caching_with_lbcache.php")

---

