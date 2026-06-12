---
title: "Strange server login issues (hangs)."
date: 2011-07-27
forum: Server Platforms
---

### Post by intrepid125 on 2011-07-27
It's my first post here - the first time I've needed to ask a question due to the fantastic support facilities and documentation the community provide.

For the last couple of months a strange login issue has been troubling me for all types of connection (local, ssh, webmin, sudo etc). The server will just hang and not respond for a few minutes on any attempt to login. Local logins timeout, over ssh the server drops the connection after a couple of minutes and the webmin login page hangs. Sudo commands never get executed. These 'hangs' can last for about 5 minutes at a time and seem to be provoked by incorrect password attempts and also right after boot.

It's running bind, dhcp, apache, mysql, tftp, ssh, samba and vmware (off the top of my head). I'm on Ubuntu Server 10.04 LTS. I can't see anything odd in the syslog. This is for all users on the server (both with encrypted homes and without).

I would be incredibly grateful for any light you can shed on this for me, a rebuild isn't the most appealing option as you can see!

intrepid125

---

### Post by intrepid125 on 2011-07-30
Bump! Willing to provide any other info.

---

### Post by Entilza on 2011-07-30
During this time what are the ping results to the server, traceroute to it and see any delays.

Can you get to the local console during this time?

---

### Post by intrepid125 on 2011-07-30
Thanks for replying. I can't log in to a local console when this happens - it eventually says "Login timed out after 60 seconds."

The ping results are as follows, interestingly it dropped out in the middle.

```

mbp:~ adam$ ping 10.0.0.2
PING 10.0.0.2 (10.0.0.2): 56 data bytes
64 bytes from 10.0.0.2: icmp_seq=0 ttl=64 time=0.769 ms
64 bytes from 10.0.0.2: icmp_seq=1 ttl=64 time=0.865 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=64 time=0.893 ms
64 bytes from 10.0.0.2: icmp_seq=3 ttl=64 time=0.858 ms
64 bytes from 10.0.0.2: icmp_seq=4 ttl=64 time=0.852 ms
64 bytes from 10.0.0.2: icmp_seq=5 ttl=64 time=0.818 ms
64 bytes from 10.0.0.2: icmp_seq=6 ttl=64 time=0.836 ms
64 bytes from 10.0.0.2: icmp_seq=7 ttl=64 time=0.909 ms
64 bytes from 10.0.0.2: icmp_seq=8 ttl=64 time=0.861 ms
64 bytes from 10.0.0.2: icmp_seq=9 ttl=64 time=0.881 ms
64 bytes from 10.0.0.2: icmp_seq=10 ttl=64 time=0.877 ms
64 bytes from 10.0.0.2: icmp_seq=11 ttl=64 time=0.763 ms
64 bytes from 10.0.0.2: icmp_seq=12 ttl=64 time=0.883 ms
64 bytes from 10.0.0.2: icmp_seq=13 ttl=64 time=0.854 ms
64 bytes from 10.0.0.2: icmp_seq=14 ttl=64 time=0.864 ms
64 bytes from 10.0.0.2: icmp_seq=15 ttl=64 time=0.916 ms
64 bytes from 10.0.0.2: icmp_seq=16 ttl=64 time=0.859 ms
64 bytes from 10.0.0.2: icmp_seq=17 ttl=64 time=0.717 ms
64 bytes from 10.0.0.2: icmp_seq=18 ttl=64 time=0.842 ms
64 bytes from 10.0.0.2: icmp_seq=19 ttl=64 time=0.814 ms
64 bytes from 10.0.0.2: icmp_seq=20 ttl=64 time=0.865 ms
64 bytes from 10.0.0.2: icmp_seq=21 ttl=64 time=0.867 ms
64 bytes from 10.0.0.2: icmp_seq=22 ttl=64 time=0.782 ms
64 bytes from 10.0.0.2: icmp_seq=23 ttl=64 time=0.864 ms
64 bytes from 10.0.0.2: icmp_seq=24 ttl=64 time=0.720 ms
64 bytes from 10.0.0.2: icmp_seq=25 ttl=64 time=0.698 ms
64 bytes from 10.0.0.2: icmp_seq=26 ttl=64 time=0.731 ms
64 bytes from 10.0.0.2: icmp_seq=27 ttl=64 time=0.860 ms
ping: sendto: No route to host
ping: sendto: No route to host
Request timeout for icmp_seq 28
ping: sendto: No route to host
Request timeout for icmp_seq 29
Request timeout for icmp_seq 30
64 bytes from 10.0.0.2: icmp_seq=31 ttl=64 time=0.562 ms
64 bytes from 10.0.0.2: icmp_seq=32 ttl=64 time=0.865 ms
64 bytes from 10.0.0.2: icmp_seq=33 ttl=64 time=0.644 ms
64 bytes from 10.0.0.2: icmp_seq=34 ttl=64 time=0.673 ms
64 bytes from 10.0.0.2: icmp_seq=35 ttl=64 time=0.706 ms
^C
--- 10.0.0.2 ping statistics ---
87 packets transmitted, 84 packets received, 3.4% packet loss
round-trip min/avg/max/stddev = 0.533/0.804/0.943/0.088 ms

```

Traceroute results below:

```

traceroute to 10.0.0.2 (10.0.0.2), 64 hops max, 52 byte packets
 1  fs1 (10.0.0.2)  0.911 ms  0.448 ms  0.448 ms

```

After I finally log in, these are the results:

```
mbp:~ adam$ ping 10.0.0.2
PING 10.0.0.2 (10.0.0.2): 56 data bytes
64 bytes from 10.0.0.2: icmp_seq=0 ttl=64 time=0.796 ms
64 bytes from 10.0.0.2: icmp_seq=1 ttl=64 time=0.868 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=64 time=0.875 ms
64 bytes from 10.0.0.2: icmp_seq=3 ttl=64 time=0.904 ms
64 bytes from 10.0.0.2: icmp_seq=4 ttl=64 time=0.848 ms
64 bytes from 10.0.0.2: icmp_seq=5 ttl=64 time=0.873 ms
64 bytes from 10.0.0.2: icmp_seq=6 ttl=64 time=0.883 ms
64 bytes from 10.0.0.2: icmp_seq=7 ttl=64 time=0.870 ms
64 bytes from 10.0.0.2: icmp_seq=8 ttl=64 time=0.809 ms
64 bytes from 10.0.0.2: icmp_seq=9 ttl=64 time=0.836 ms
64 bytes from 10.0.0.2: icmp_seq=10 ttl=64 time=0.885 ms
64 bytes from 10.0.0.2: icmp_seq=11 ttl=64 time=0.885 ms
^C
--- 10.0.0.2 ping statistics ---
12 packets transmitted, 12 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.796/0.861/0.904/0.031 ms

```

and traceroute:

```

traceroute to 10.0.0.2 (10.0.0.2), 64 hops max, 52 byte packets
 1  fs1 (10.0.0.2)  0.910 ms  0.448 ms  0.439 ms
```

Thanks again!

---

### Post by intrepid125 on 2011-07-30
From messing around a bit it seems that the problem is triggered when the vmware services start, I can log in on startup if i'm quick and do it before vmware begins. The problem isn't fixed when I remove it from startup using rcconf - any ideas?

intrepid125

---

### Post by Entilza on 2011-07-30
Local console lags and times out as well?  That's strange is it using standard /etc/passwd /etc/shadow authentication?

Is your hard disk dying?

So you can reproduce this by stopping and restarting vmserver? I know it may not be vmserver specific but if it's somehow triggering the bad hardisk area?  If you can reproduce the freeze you are 90% in finding out your answer...

Check any syslog messages during this time as well if you already haven't...

---

### Post by intrepid125 on 2011-08-01
I can't seem to reproduce the problem by stopping and starting the service. I have moved the install over 3 different hard disks over the last year - it's on a brand new one now but i'll run SpinRite on it later to see if there's anything wrong with the hard disk. Nothing seems to show in syslog either.

Thanks again!

intrepid125

---

