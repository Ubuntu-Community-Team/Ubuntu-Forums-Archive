---
title: "Ubuntu Server 22.04 cannot update"
date: 2024-04-15
forum: Server Platforms
---

### Post by gorgonea24 on 2024-04-15
Hi, 

In the past two days I have tried to install ubuntu server which seems to get stuck when acquiring packages, mainly because it times out when contacting [http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease](http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease) with the error claiming the following file:  "http://security.ubuntu.com/ubuntu jammy-security/main amd64"

I get two IPs that constantly seem to fail:
[LIST=1]
[*]91.189.91.81
[*]185.125.190.36
[/LIST]

Could someone confirm this is an issue from Ubuntu or is it a local issue on my side? 
 
Thanks!

---

### Post by TheFu on 2024-04-15
```
$ ping 91.189.91.81
PING 91.189.91.81 (91.189.91.81) 56(84) bytes of data.
64 bytes from 91.189.91.81: icmp_seq=1 ttl=42 time=43.0 ms
64 bytes from 91.189.91.81: icmp_seq=2 ttl=42 time=40.2 ms
^C
--- 91.189.91.81 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 40.205/41.590/42.975/1.385 ms


$ ping 185.125.190.36
PING 185.125.190.36 (185.125.190.36) 56(84) bytes of data.
64 bytes from 185.125.190.36: icmp_seq=1 ttl=41 time=106 ms
64 bytes from 185.125.190.36: icmp_seq=2 ttl=41 time=113 ms
64 bytes from 185.125.190.36: icmp_seq=3 ttl=41 time=102 ms
^C
--- 185.125.190.36 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 102.218/107.068/113.209/4.578 ms

```

There are websites that will check if a web server is "down for me". They are easily found. No need to wait for someone else here.

Also, servers, especially those volunteered for no cost, are sometimes down for 10 minutes for different reasons.  Try again in a few hours and see if it works then.

Of course, your ISP or govt may get in the way of access for reasons they don't report too.

---

