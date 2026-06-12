---
title: "Tough Network Question"
date: 2012-02-10
forum: Server Platforms
---

### Post by bonesjones256 on 2012-02-10
Got a weird one.

Here's my current setup.

WANIP=>>>>\ Firewall\ Server
WANIP2=>>>/ Firewall/ Server

Basically our company is in an area where all we can get is cable modem and Uverse. The cable modem is fast 50 down 5 up. but goes down at least once a month (it's a constant fight with charter)

So I've got two static ips that point to the same stuff. one firewall with same ports open.
Outbound is fine my sonicwall knows if the WAN is out to send traffic out of WAN2.

But incoming is the issue. I found a company that gives me a linux server for 20 bucks a month. What i am looking for is to redirect my dns to the ip of that linux server, have that linux server somehow monitor both of my WANS, normally i would want the server to forward all traffic to 80,25,5053 to the WAN1, however if wan one dies i want the server then send traffic to WAN2.
And onces wan1 comes back send it back to wan1
That way if WAN one dies our website stays up, we can still get e-mail on our phones, and our monitoring system (port 5053) will still function.

Everything i've read is for server failover, but i never have servers issues, but i have WAn issues constantly.

So in short I would change my dns records to point to the virtual server then from there send to either one of the servers,
I realize there'd still be a single point of failure but a linux server failure rate is much less than that of my cable modem.

---

### Post by HugoSerrano on 2012-02-10
Hello!

For how long does the WAN1 fails?

There's the DNS time propagation, so when you change the DNS to WAN2, you will get the propagation time delay, and when WAN1 it's back online, you change DNS back to WAN1 IP, so you will get more time (but in this case it's not a big problem, because WAN2 still works).

Regards!

---

### Post by uRock on 2012-02-10
Please do not create duplicate threads. Duplicate thread here [http://ubuntuforums.org/showthread.php?p=11676491#post11676491](http://ubuntuforums.org/showthread.php?p=11676491#post11676491)

Thread Closed

---

