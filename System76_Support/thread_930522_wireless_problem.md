---
title: "wireless problem"
date: 2008-09-26
forum: System76 Support
---

### Post by hvacr on 2008-09-26
I have a new Pangolin Performance, which I have had for a few weeks. I have been running in ubuntu until last night, when I booted into vista. I checked my wireless connection speed and found I am only connecting at G, 54m. I checked all settings on the router and all are ok. I booted into ubuntu and ran iwconfig and got this.

wlan0     IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:F3:1D:24   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=100/100  Signal level=-34 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


If I set my router to transmit on N only, the laptop does not see the wireless network, ( windows and ubuntu)

I will have to purchase a new router tonight to check if that is the cause, somehow I doubt it though. As I said all settings in the router are correct. I am using a Linksys wrt300n router.

I have even moved the laptop into the same room as the router, same results.

---

### Post by thomasaaron on 2008-09-26
We're doing some testing on this end, but if you can't see your connection in Ubuntu and Windows in n-only mode, it's probably your router. 

Plus, we CAN *see* the "n" A.P. when the router is set to n-only mode. I'm not sure yet if they've connected to it. I'll follow up as the info flows in.

---

### Post by hvacr on 2008-09-26
> **thomasaaron said:**
> We're doing some testing on this end, but if you can't see your connection in Ubuntu and Windows in n-only mode, it's probably your router. 

Plus, we CAN *see* the "n" A.P. when the router is set to n-only mode. I'm not sure yet if they've connected to it. I'll follow up as the info flows in.

New router, and I am a happy camper, full speed ahead on N.  Thanks

---

### Post by hvacr on 2008-09-26
> **hvacr said:**
> New router, and I am a happy camper, full speed ahead on N.  Thanks


After some testing, in vista I am connecting at 130m. I ubuntu only 54m

iwconfig shows

wlan0     IEEE 802.11g  ESSID:"dlink"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:11:69:1E:6D   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=100/100  Signal level=-37 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


How does one get Ubuntu to use channel N

Just did a fresh install of ubuntu with the system 76 drivers, and Ubuntu will only work at 54M, windows is at 130M This seems to be a Ubuntu problem.


One more test result. I have set the router to N only, widows vista connects, Ubuntu will not. Driver issue?

---

### Post by thomasaaron on 2008-09-29
OK. Thanks. 

We will test this evening, and I'll report back tomorrow.

---

### Post by thomasaaron on 2008-09-30
Here's the news:

It's a bug in Ubuntu, and it looks like the fix has been committed but not released.

[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/241423](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/241423)

It also looks like it is available for testing.

---

### Post by hvacr on 2008-09-30
> **thomasaaron said:**
> Here's the news:

It's a bug in Ubuntu, and it looks like the fix has been committed but not released.

[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/241423](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/241423)

It also looks like it is available for testing.

Thanks very much, I will look into this latter on and give it a try.

---

