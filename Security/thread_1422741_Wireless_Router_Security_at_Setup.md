---
title: "Wireless Router Security at Setup"
date: 2010-03-05
forum: Security
---

### Post by risingsun on 2010-03-05
I realise this is more of a OS agnostic question and rather specific so I apologise in advance, but I was hoping someone could help :)

I recently reset and re-setup my Wireless router. My main concern is that because these things are so stupidly open at factory default settings it created a brief window of insecurity. 

I reset it a second time (but this time with the antenna disconnected) so I believe it should be fine, but of course the other concern is the potential for any other nasty stuff (I do recall hearing of stuff involving malicious apps sitting on routers for deep packet inspection and the like.) I suspect the chance of this happening in such a brief period is pretty small, and I'm not sure what the avenue of infection might be for such things anyway so any enlightenment that can be offered on the topic will be gratefully received. Is this generally limited to routers capable of running third party firmware?

Many thanks.

---

### Post by Pjotr123 on 2010-03-05
No worries, infection is highly unlikely if the unprotected time span was brief.

You might want to flash the router firmware to a newer version (if available): firmware updates fix both usability and security bugs.

Afterwards, apply these tips to secure your router and your network:
[http://sites.google.com/site/easylinuxtipsproject/securitywireless](http://sites.google.com/site/easylinuxtipsproject/securitywireless)

---

### Post by Ijan on 2010-03-05
The usual intended practice is to flash/reset the router to "factory" while it is disconnected from the internet, then set up a non-default password from a computer connected via LAN-cable. All ok routers don't allow wireless access to that basic security function, so this process is safe from outside interference.

But: Even if your router is badly designed or you didn't follow the intended practice - router malware is very rare. Only very few router models have a theoretical chance to get infected by malware, the chance that this may be possible in the case of your model and in the time frame of your firmware reset seems - very - negligible.

> I do recall hearing of stuff involving malicious apps sitting on routers for deep packet inspection and the like.
You mixed things up a bit. [DPI](http://en.wikipedia.org/wiki/Deep_packet_inspection) is a technique to monitor networks, PC-malware can't, doesn't need to and will in the near future never do DPI. Router based malware is still rare, though it is supposed to become more relevant in the future.

---

