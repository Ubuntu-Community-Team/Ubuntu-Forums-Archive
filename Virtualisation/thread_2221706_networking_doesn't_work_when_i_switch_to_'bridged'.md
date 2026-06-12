---
title: "networking doesn't work when i switch to 'bridged'"
date: 2014-05-03
forum: Virtualisation
---

### Post by jim50 on 2014-05-03
Hi all, I'm just getting up and running with ubuntu server in a virtualbox vm. I'm still pretty new, but everyone has been super helpful thus far.

I was recommended in an another thread on ssh to use bridged rather than port forwarding. Hoever when I shutdown my VM and switch my netwroking adapter from NAT to Bridged (called eth0) then start ubuntu server, I have no internet.

I've tried following a few other threads, but my case never quite seems the same.

I ran ```
ifconfig >> ~/status 
``` to capture my ifconfig output with NAT and with bridged. I notice my bridged has no 'inet' ?

```
eth0      Link encap:Ethernet  HWaddr 08:00:27:5d:d1:1f           
          inet6 addr: fe80::a00:27ff:fe5d:d11f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:26982 (26.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7520 (7.5 KB)  TX bytes:7520 (7.5 KB)

```

Any ideas? I'm not sure where to start in a command line only server.

Jim

PS guest additions are installed

---

### Post by steeldriver on 2014-05-03
What's in your server's /etc/network/interfaces file? Do you want the bridged connection to get its IP and DNS servers via DHCP from your LAN router, or use a static LAN IP / DNS?

---

### Post by Double.J on 2014-05-03
Hi there,

If it's not already been said, welcome to the forums!

the inet is what we call ipv4 if it helps. Are you by any chance using wifi between this computer and the router? If so try changing the 'name' in virtualbox to 'wlan0'

let us know how you get on

Jj

---

### Post by jim50 on 2014-05-03
Thanks for the replies guys!

Double that worked! I'm online :guitar:

Thank you!

Jim

---

### Post by Double.J on 2014-05-03
Hi there,

Glad to hear it's working. Test it a couple of restarts and tasks, then mark this thread as solved if it's permanent. 

If not, please keep us updated.

Jj

---

