---
title: "Running a laptop with the 8.04 Server kernel - no Atheros?!"
date: 2008-04-26
forum: Server Platforms
---

### Post by Jim March on 2008-04-26
The REASON I'm running the server kernel is that Hardy has a persistent bug in some systems causing random freezups...in my case every three-four hours on average.  Proper bug reports have been filed by a bunch of people, myself included.

It's been a stone-cold beech to sort out, but one of the few cures known so far is to run the server kernel:

sudo apt-get install linux-server

Problem: when running the server kernel, my Atheros-based WiFi doesn't work.

At this moment I'm running the desktop kernel. And I get:

> jim@thecritter:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Integrity"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:24:A5:A8:E1   
          Bit Rate:12 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-36 dBm  Noise level=-91 dBm
          Rx invalid nwid:7  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jim@thecritter:~$ 


According to Synaptic, the Madwifi module is in the server kernel package I have installed.

Can anybody help sort this out?

Thanks,

Jim

---

