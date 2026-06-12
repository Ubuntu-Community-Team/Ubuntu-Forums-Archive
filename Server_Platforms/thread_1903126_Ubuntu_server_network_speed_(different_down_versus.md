---
title: "Ubuntu server network speed (different down versus up)"
date: 2012-01-01
forum: Server Platforms
---

### Post by mikegleasonjr on 2012-01-01
Hi,

I'm connected with Gigabit Ethernet with my server 11.10 (via a Apple Airport Extreme router).

When I run iperf, I get different speed when I download or I upload to the server:

```
-- From the server (10.0.1.2) --

mike@localserver:~$ iperf -c 10.0.1.105 -d
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 10.0.1.105, TCP port 5001
TCP window size:  178 KByte (default)
------------------------------------------------------------
[  5] local 10.0.1.2 port 35473 connected with 10.0.1.105 port 5001
[  4] local 10.0.1.2 port 5001 connected with 10.0.1.105 port 1791
[ ID] Interval       Transfer     Bandwidth
[  5]  0.0-10.0 sec   973 MBytes   816 Mbits/sec
[  4]  0.0-10.0 sec   180 MBytes   151 Mbits/sec



-- From the client (10.0.1.105), (iperf.exe -c 10.0.1.2 -d) --

[1860] local 10.0.1.105 port 1785 connected with 10.0.1.2 port 5001
[1836] local 10.0.1.105 port 5001 connected with 10.0.1.2 port 35471
[ ID] Interval       Transfer     Bandwidth
[1836]  0.0-10.0 sec   958 MBytes   804 Mbits/sec
[1860]  0.0-10.0 sec   175 MBytes   146 Mbits/sec
```

The server is using the onboard gbit NIC

I've installed an Ubuntu Server on a dual core 2Ghz CPU and 1 gig RAM with onboard NIC (Motherboard: Gigabyte Ga-k8n-f9 rev.1)

The cables are CAT5E (server to Airport Extreme) & CAT5 (client to aiport extreme)

Should I buy CAT6 cables and a new standalone nic for the server ? The client is a Thinkpad R61i.

Thank you !

---

### Post by Haneef Mubarak on 2012-01-01
That's how it usually is, here's why:
[LIST=1]
[*]Download speeds are often faster than upload because your ISP or your router knows that most users download more and download more often (visit websites, check email, etc) than they upload (upload attachments, host a website, etc).
[*]Every speedtest is always different.
[*]The less data you send over a network (for a speedtest), the less accurate the data is. If possible, use large files sizes like 1-5 GB.
[*]In general, wired is way faster than wireless.
[/LIST]

If you really want faster/more even network speeds, consider looking at Fibre Channel networking and/or [making your own router from an old machine]("https://help.ubuntu.com/community/Router").

---

### Post by mikegleasonjr on 2012-01-01
I'm really sorry I should have stated that this is occuring in my LAN.. nothing is going "outside"...

I'll try to buy a gbit lan adapter tomorrow to see if it solves the problem..

But if you guys have an idea in the meantime, thanks in advance

---

### Post by kylewhittington on 2012-05-23
I'm having the same issue. Wired LAN, both gigabit onboard network adapters, all CAT6 cable. Both terminals are running Ubuntu 12.04 and show a full duplex 1000Mbit connection.

Using iperf, from server to client I get 980Mbit/s. From client to server, I get 590Mbit/s. Quite a large difference and I have no idea why. Both terminals are showing very low CPU usage during the tests, too. Both terminals are also very decent spec PC's - at least dual core, fast RAM etc.

The results are also very consistent on each test.

Not sure whether the asker solved this or found out anything more about it? Anybody else have any ideas?

---

### Post by d4m1r on 2012-05-23
Did you have anything else running on the network when you attempted the client to server transfer? It could be not that the clients isn't uploading fast enough, but the server isn't accepting/is reducing the transfer speed...

---

### Post by kylewhittington on 2012-05-29
Nope, nothing was running. I've also run the checks since then and the speeds are always consistent, so it's nothing to do with any potential concurrent bandwidth usage.

---

### Post by sPENKMAN on 2012-06-01
Typical, I've the exact same problem between a Windows (2008 R2 SP1) and a Ubuntu box (10.04 LTS x86_64).

Ubuntu is server
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec    550 MBytes    461 Mbits/sec
[  5]  0.0-10.0 sec    541 MBytes    453 Mbits/sec

Windows is server:
[280]  0.0-10.0 sec  1.07 GBytes   920 Mbits/sec
[300]  0.0-10.0 sec  1.07 GBytes   920 Mbits/sec

Both servers are connected to the same blade on our Cisco Catalyst 4506. No packet errors have been recorded.

Don't really have a clue what to check / try out next...

---

### Post by Gyokuro on 2012-06-02
Hi

It depends also which network cards are used and standard installations or not tuned for high performance transfers so I can only suggest that you try to tune your TCP/IP stack:

like test it temporary:

# change wmem_max and rmem_max to highter values
echo  'net.core.wmem_max=12582912' >> /etc/sysctl.conf
echo 'net.core.rmem_max=12582912' >> /etc/sysctl.conf

# change minimum size, initial size, and maximum size in bytes
echo 'net.ipv4.tcp_rmem= 10240 87380 12582912' >> /etc/sysctl.conf
 echo 'net.ipv4.tcp_wmem= 10240 87380 12582912' >> /etc/sysctl.conf

and recheck whether more data get pushed through your wire. Please note that this settings need some RAM.

---

### Post by sPENKMAN on 2012-06-02
The machines in question are a G7 HP server and a supermicro with an Intel Pro dual Gbit adapter. I've never needed tweaks to get full bandwidth from a Gbit network (even with lesser hardware (broadcom cards) at home) using benchmark tools like iperf.

Doesn't hurt to give it a go though, will give it a try monday :)

---

