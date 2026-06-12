---
title: "Can't get on the internet"
date: 2006-12-14
forum: Server Platforms
---

### Post by dj50 on 2006-12-14
Hello,

I'm trying to set up a home router using ubuntu server 6.10 and I can't seem to get over the first step: getting on the internet.

Both my ethernet cards are detected correctly - and I try to set up eth0 using the information from my ISP (no DHCP service available).

Here's the output from ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:C0:4F:24:F8:AD
          inet adder: xxx.xxx.xxx.85  Bcast: xxx.xxx.xxx.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0 0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16434  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:960 (960.0 b)  TX bytes:968 (968.0 b)

gateway is xxx.xxx.xxx.1 and seems to be well set considering /etc/network/services

and DNS servers seem also to be well set considering /etc/resolv.conf

I have no idea how to make it work ... Any help?

Thanks

---

### Post by floke on 2006-12-14
Don't know if this will help but I had a similar problem when switching from Windows.
My router settings etc. were all set up in WinXP so I knew it worked (is this the first time you're setting it up or was it already set up in Win?). My mistake was trying to enter in all the settings into Ubuntu, when all I had to do was leave everything blank except for the ESSID and the Hex code. I left it on automatic configuration (DHCP) and everything worked fine - so no need to enter lots of meaningless numbers etc.

Any good?

---

### Post by dj50 on 2006-12-14
> **Steve.K said:**
> Don't know if this will help but I had a similar problem when switching from Windows.
My router settings etc. were all set up in WinXP so I knew it worked (is this the first time you're setting it up or was it already set up in Win?). My mistake was trying to enter in all the settings into Ubuntu, when all I had to do was leave everything blank except for the ESSID and the Hex code. I left it on automatic configuration (DHCP) and everything worked fine - so no need to enter lots of meaningless numbers etc.

Any good?

I've had an old win98 box and everything was working fine, but now I'm trying to install on another box. My provider doesn't offer DHCP and I have a static IP.

---

### Post by floke on 2006-12-15
Have you tried connecting via wi-fi without entering any connection details - i.e. by leaving it all blank except for the bits I outlined above?

---

### Post by dj50 on 2006-12-15
> **Steve.K said:**
> Have you tried connecting via wi-fi without entering any connection details - i.e. by leaving it all blank except for the bits I outlined above?

Well, I don't have wi-fi ...

It's just a plain cable connection.

Anyway, in the meantime I've pulled one of the network cards out of the computer and did a reinstall, and it still refuses to see anything on the internet, or the gateway.

---

### Post by floke on 2006-12-15
Well, I must apologise - I misunderstood 'router' and assumed you were talking about wireless.
Am still new to much of this myself and read your problem as having similarities to my own, when it doesn't look like this is the case.

Can you connect direct to the web via cable without the router?

---

