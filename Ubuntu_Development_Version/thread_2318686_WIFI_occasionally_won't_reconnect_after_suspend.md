---
title: "WIFI occasionally won't reconnect after suspend"
date: 2016-03-28
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2016-03-28
I've been testing UM 16 on my Dell laptop [in a separate partition] that's been running Ubuntu 14 LTS for close to 2 years now [never had this symptom].
The symptom is WIFI **occasionally** won't reconnect after suspend. ```
lspci |grep Network
08:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
uname -a
Linux Dell-1749 4.4.0-15-generic #31-Ubuntu SMP Fri Mar 18 19:08:31 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
``` I execute apt update & upgrade daily. I've compared working and non-working entries in syslog, kernlog, and authlog but I believe the differences are beyond my understanding level.
I think this might be an anomaly with:
[LIST=1]
[*]the new kernal 
[*]3rd os on the machine 
[*]some setting I'm missing 
[/LIST]
I want to officially report this, if and only if, it's not something trivial that I've missed.

---

### Post by enricobe on 2016-03-28
I have the same problem

08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter

but I had this problem also with previous versions. I have to say that this seems to occur only when I suspend and wake up the PC 2 times or more. With my wifi card I have much less problems with 16.04 than previous versions.

Edit: I use Ubuntu, but I had the same problem with Xubuntu. I think this problem is not depending on the flavor

---

### Post by pfeiffep on 2016-03-29
> **enricobe said:**
> I have the same problem

08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter

but I had this problem also with previous versions. I have to say that this seems to occur only when I suspend and wake up the PC 2 times or more. With my wifi card I have much less problems with 16.04 than previous versions.

**Edit: I use Ubuntu, but I had the same problem with Xubuntu. I think this problem is not depending on the flavor**I suspect it's related to 16.04 version. This symptom is extremely intermittent for me.

---

### Post by cariboo on 2016-03-29
I have the same problem, though, it may go a couple of weeks before it happens again. I use:

```
sudo service NeworkManager restart
```

to get wifi working again.

---

