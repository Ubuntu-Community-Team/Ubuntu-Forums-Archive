---
title: "Dell XPS 1330 with Vista -&gt; Ubuntu: Ubuntu impresses, Dell not"
date: 2008-11-29
forum: Testimonials &amp; Experiences
---

### Post by buncikp on 2008-11-29
Hi,
I decided to share a few thoughts about Ubuntu and Dell machine I (unfortunately) have. The machine I'm talking about is Dell XPS 1330 (not the Linux version Dell said to be selling).
I managed to install Hardy on this Dell machine and after some tweaking of (very bad) Broadcom Wifi card I was successful to get it working. In fact everything worked out the box but the damned Wifi card...
Overall I was so happy with Ubuntu! It did everything I needed so I had no (not really, no!) idea to get back to Vista "Business" (meaning it is busy all the time it runs), which in fact decreases power of this notebook and contains literally nothing usable, forcing you to spend another money on apps you must use in order to have computer for a daily work (mails, word processing, etc...) I really had no idea to mess up with Windows Mail nor with anything like this, I had already all e-mails in transferable form (not the gigantic PST file) from my previous Linux machine and I didn't want to spend hours to import the mails to this Microsoft mess.
Using the Broadcom (well, they claim "Dell") XP drivers via ndiswrapper was sometimes hard, but overall it was possible to do. Of course with some magical outages, when the card just disconnected and was unable to connect again for some time.
After time I found native driver from Broadcom and compiled it for my kernel -- and the networking was even better. However I noticed that still after some time the Wifi dropped and was unable to get working again. After some struggling it looked like Network Manager had some issues with wpa_supplicant -- both in some point of time desynced, resulting in Wifi disconnect. The solution was to enable proposed versions of NetworkManager, which worked. Simply the combination of Hardy, NM proposed packages and native Broadcom driver got the results.
Well after the time, I would say that I would done better to avoid Dell -- the notebook is rather bulky (annoying wifi switch, alluminium-like housing which in fact is sooo bulky that allows to develop holes when you move the open laptop to another location), plastic feel of the laptop, poor battery life...And literally NO SUPPORT from Dell to the damned Broadcom thing for Linux. I'm not impressed by the notebook and I would happily switch back to Fujitsu-Siemens. I was planning to buy a Lifebook and I'm sorry I have not done so.

---

### Post by 3rdalbum on 2008-11-30
From what I hear, Dell put pressure on Broadcom to release Linux drivers. I'm sorry to hear of your experience, and I can sympathise having wireless problems myself.

---

### Post by Gausian on 2008-11-30
im actually really happy with my xps.  although i have the intel wireless adapter.  

its actually really easy to swap wifi cards on the xps.  theres a little door right under the touchpad.  the wifi card sits there.  intel wifi cards arent expensive, and work perfectly in ubuntu.

---

### Post by buncikp on 2008-11-30
> **Gausian said:**
> im actually really happy with my xps.  although i have the intel wireless adapter.  

its actually really easy to swap wifi cards on the xps.  theres a little door right under the touchpad.  the wifi card sits there.  intel wifi cards arent expensive, and work perfectly in ubuntu.
Woow :) That sounds like a good idea! Will check local retailers if they stock some of mobile wifi devices, thanks!

---

