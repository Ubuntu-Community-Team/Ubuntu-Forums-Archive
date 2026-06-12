---
title: "Odd Problem With WiFi"
date: 2013-08-05
forum: Ubuntu Development Version
---

### Post by ReviewSpin on 2013-08-05
So, first off let me state the laptop I am using might have some hardware problem. According to my ex wife, it wouldn't boot with her. It would ask for a boot disc. So since she owes me money on this "broken" laptop, I asked if I could fix it (and once I do, I'll probably keep it since she all ready bought herself a brand new Samsung touch screen desktop). 

Anyway, I installed Ubuntu and then updated from 12.10, to 13.04 then to 13.10. Updated the software of course. Did most of this over Wifi. When I updated to 13.04, however, WiFi wouldn't work. It would ask for my password and then I type it in and it rejects it. Internet does work -- my Roku, Desktop and Phone all connect to the internet using the same connection. I plug my laptop in to the modem and bam I get internet, and I finish upgrading. After it finished upgrading to 13.10, I can now use WiFi. Thought problem was fixed.

But now I can not use WiFi again. I don't know what could be the problem here. Could I need a driver for my WiFi card, and if so how do i find out what type of WiFi card I have?

Any suggestions would be great. Thanks!

---

### Post by wildmanne39 on 2013-08-05
*Thread moved to **Ubuntu +1**.* 13.10 is in development and all questions pertaining to it belong here.  I recommend reinstalling 12.04 or 13.04 then you can post your wifi question in the networking section.  You will most likely have other issues with 13.10 while it is in testing.

---

### Post by grahammechanical on 2013-08-05
Let me see if I understand your situation correctly. You installed Ubuntu 12.10 and set up WiFi. You then used WiFi to upgrade to 13.04 and then on to 13.10 and WiFi was still working but now it is not.

Why would it need drivers? If it needed drivers then you would not have got wireless access with 12.10. This may not be an issue with 13.10. Open a terminal and type

```
rfkill list
```

you should see this

> 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Soft blocked: yes = the wireless adapter is switched off in software.

Hard blocked: yes = the wireless adapter is switched off by hardware. Usually a keyboard combination.

Regards.

---

### Post by ReviewSpin on 2013-08-05
> **grahammechanical said:**
> Let me see if I understand your situation correctly. You installed Ubuntu 12.10 and set up WiFi. You then used WiFi to upgrade to 13.04 and then **USED ETHERNET** to upgrade to 13.10 and WiFi was still working but now it is not.

Why would it need drivers? If it needed drivers then you would not have got wireless access with 12.10. This may not be an issue with 13.10. Open a terminal and type

```
rfkil list
```

you should see this



Soft blocked: yes = the wireless adapter is switched off in software.

Hard blocked: yes = the wireless adapter is switched off by hardware. Usually a keyboard combination.

Regards.


Wellm WiFi is working now, and I am getting what you said I should. I'll remember this, and when the WiFi stops working again I'll try that to see if something different happens.

Thanks. I also edited your quote, because I used Ethernet to upgrade from 13.04 to 13.10.

---

