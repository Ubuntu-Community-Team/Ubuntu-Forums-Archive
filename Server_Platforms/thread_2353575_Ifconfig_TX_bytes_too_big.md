---
title: "Ifconfig TX bytes too big"
date: 2017-02-23
forum: Server Platforms
---

### Post by hungryOrb on 2017-02-23
Hi all,

I have a problem. A computer on the network is causing my router to exceed CPU system usage (90%). When I disconnect the computer, the router stops complaining. When I check the ifconfig of that computer, I get this result:

```
eth1      Link encap:Ethernet  HWaddr 00:1a:64:a0:2a:c0
          inet addr:10.4.56.3  Bcast:10.4.56.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:64ff:fea0:2ac0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99435738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9332121 (9.3 MB)  TX bytes:6901313683 (6.9 GB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:617845 (617.8 KB)  TX bytes:617845 (617.8 KB)

```

That 6.9 GB does not look good. When you restart the server, this resets, but isn't that too high? This 6.9 GB was earlier today, and now it's at 16.7 GB. This server is used for very small amounts of packets being transferred. A single mysql database, which backs up to about 4mb in size, is used sometimes for small data changes. That's it. 

My question is this:
How can I find out what is causing this great size? Is there a way to stop it? How does it work exactly?

---

### Post by DuckHook on 2017-02-24
No server guru, I, but what exactly are you running on the server? You've already said a mysql database, but size has little relation to activity.

You can try some of the tools summarized in the following site: [https://blog.serverdensity.com/80-linux-monitoring-tools-know/](https://blog.serverdensity.com/80-linux-monitoring-tools-know/)

For any more help than that, I'm afraid a real expert is needed and I don't qualify.

---

