---
title: "LAMP Server Hanging"
date: 2008-04-13
forum: Server Platforms
---

### Post by scambro on 2008-04-13
I've moved over from a WAMP to a LAMP running Ubuntu 7.1 server.  I don't have a lot of traffic on my site, mostly for my own use, but occassionally the server just stops.  It seems to hang for less than a minute.  If I browse to the URL (both the LAN and WAN address), I get a not found.  My SSH connection will get disconnected too.  After about a minute, everything comes back and it moves just as quickly as ever.

I'm new to Linux, so I'm not sure where to start in how to troubleshoot this.  I read in a related topic to get mrtg to monitor some of the resources, so I'll be installing that shortly.  Any other ways to go about tracking this down?  Thanks!

---

### Post by iSplicer on 2008-04-13
Hi mate.

Try and ifconfig your server while this occurs, and post the output. Also, ping [www.google.com](www.google.com)

---

### Post by scambro on 2008-04-13
> **iSplicer said:**
> Hi mate.

Try and ifconfig your server while this occurs, and post the output. Also, ping [www.google.com](www.google.com)

I'm currently remoted into the box (it's in the basement and it's pretty cold down there...).  Here's what I get when I ifconfig right after it came back from dropping me:

user@webserv01:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:56:94:53:B0  
          inet addr:192.168.1.123  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fe94:53b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3996138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5006253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1594360574 (1.4 GB)  TX bytes:1978345820 (1.8 GB)
          Base address:0xdf40 Memory:feae0000-feb00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1062563 (1.0 MB)  TX bytes:1062563 (1.0 MB)

I was running a ping of google.com and right in the middle it happened again.  It was going along well without a problem, then it slowed down.  I tried to connect an extra SSH session, but got 'server not found' on the internal IP.  I noticed the ping came back in the initial session but looked different.  Maybe it doesn't matter, but here's what I had:

64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=290 ttl=244 time=152 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=291 ttl=244 time=208 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=292 ttl=244 time=187 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=293 ttl=244 time=204 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=294 ttl=244 time=178 ms
[COLOR="red"][here's where it got really slow, about 5 - 10 seconds between each line][/COLOR]
64 bytes from 72.14.207.99: icmp_seq=295 ttl=244 time=234 ms
64 bytes from 72.14.207.99: icmp_seq=296 ttl=244 time=183 ms
64 bytes from 72.14.207.99: icmp_seq=297 ttl=244 time=183 ms
[COLOR="Red"][speed picked back up here and pinging went on normally][/COLOR]
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=298 ttl=244 time=243 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=299 ttl=244 time=214 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=300 ttl=244 time=181 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=301 ttl=244 time=179 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=302 ttl=244 time=125 ms

Thanks for looking!

---

### Post by scambro on 2008-04-21
Any other ideas?  I ran memtest86 for the past few days and it hasn't found any issues with the memory in the box.  It might be the network card (it's an integrated one), so I could try swapping it out tonight.  Here's what I get on my serviceuptime.com account for the host name:

Monthly statistics:
Day Uptime 
2008.04.13 66.667 % 
2008.04.14 34.043 % 
2008.04.15 61.702 % 
2008.04.16 100 % 
2008.04.17 100 % 
2008.04.18 100 % 
2008.04.19 100 % 
2008.04.20 100 % 
2008.04.21 100 % 
  

You can see on 4/16 I rolled back to my WAMP server because the Linux box just wasn't holding up.

Thanks!

---

### Post by geertn on 2008-04-21
Check your dmesg and other logs in /var/log 

tail -300 /var/log/dmesg
tail -300 /var/log/daemon.log
tail -300 /var/log/messages

This could be caused by dhcp trying to renew its lease and not getting a lease right away. Do you use dhcp?

---

### Post by scambro on 2008-04-27
> **geertn said:**
> Check your dmesg and other logs in /var/log 

tail -300 /var/log/dmesg
tail -300 /var/log/daemon.log
tail -300 /var/log/messages

This could be caused by dhcp trying to renew its lease and not getting a lease right away. Do you use dhcp?

Thanks for the help!  When I loog at the daemon.log file it's filled with entries:

Apr 27 09:34:57 webserv01 winbindd[32020]: [2008/04/27 09:34:57, 0] nsswitch/idmap.c:idmap_init(687) 
Apr 27 09:34:57 webserv01 winbindd[32020]:   ERROR: Initialization failed for alloc backend tdb, deferred! 
Apr 27 09:34:57 webserv01 winbindd[32020]: [2008/04/27 09:34:57, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Apr 27 09:34:57 webserv01 winbindd[32020]:   ERROR: Initialization failed for alloc backend, deferred! 
Apr 27 09:34:57 webserv01 smbd[32018]: [2008/04/27 09:34:57, 0] auth/auth_util.c:create_builtin_administrators(792) 
Apr 27 09:34:57 webserv01 smbd[32018]:   create_builtin_administrators: Failed to create Administrators 
Apr 27 09:34:57 webserv01 winbindd[32020]: [2008/04/27 09:34:57, 0] nsswitch/idmap.c:idmap_alloc_init(735) 
Apr 27 09:34:57 webserv01 winbindd[32020]:   ERROR: Initialization failed for alloc backend, deferred! 
Apr 27 09:34:57 webserv01 smbd[32018]: [2008/04/27 09:34:57, 0] auth/auth_util.c:create_builtin_users(758) 
Apr 27 09:34:57 webserv01 smbd[32018]:   create_builtin_users: Failed to create Users 
Apr 27 09:34:57 webserv01 winbindd[32007]: [2008/04/27 09:34:57, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Apr 27 09:34:57 webserv01 winbindd[32007]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Apr 27 09:34:57 webserv01 winbindd[32007]: [2008/04/27 09:34:57, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Apr 27 09:34:57 webserv01 winbindd[32007]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend

---

### Post by scambro on 2008-05-12
Hey guys,

I'm still up a creek with this one.  I've rolled back to my windows server, which I don't really want to keep up anymore.  Any other ides, or things I could check?  

I threw in a NIC card from a really old box (10 mbps!), and I couldn't find the Linux drivers for it, so I gave up on that effort for now.

Thanks!

---

