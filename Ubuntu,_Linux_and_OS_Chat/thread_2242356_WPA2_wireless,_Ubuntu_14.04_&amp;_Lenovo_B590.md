---
title: "WPA2 wireless, Ubuntu 14.04 &amp; Lenovo B590"
date: 2014-09-01
forum: Ubuntu, Linux and OS Chat
---

### Post by RichardET on 2014-09-01
Its amazing, don't you think?  My Lenovo V470 with Windows 8.1 connects to this WPA2 router at the vacation home, my Blackberry Z10 connects to this router, my B&N Samsung Nook connects to this router, but my glorious Ubuntu Lenovo B590 won't!  I have had a linux based computer in use since 1998, in one form or another, and to be fair, this B590 connects to all other routers I have used with it, but even with several hours of experimenting, what connected without tweaking by every other device, no change worked for the B590, and I tried everything.   I have no idea what to say about this beyond, mentioning the straight-up fact that Ubuntu should focus on this type of incompatibility, and forget about Ubuntu phones, tablets, etc., and if I ever travel somewhere again, for 3 days, I will make sure NOT to bring the Ubuntu.  I will stick with commercial OS devices;  I don't have room in my car for anything useless.

The solution is NOT to change the router.  The solution is for Canonical  to make it's OS work with mainstream business computers, period.

---

### Post by grahammechanical on 2014-09-01
What is a B590 when it is on vacation? Your problem means nothing to me. I  want to buy a Ubunu super phone that can become a tablet or a PC. So, I say to Canonical; Carry on with phones and tablets and desktop convergence. Canonical, you are doing Great.

---

### Post by RichardET on 2014-09-01
An internet search turns up many forum posts over the past 3 years on this issue.  But you right - who cares, really?  I don't.  I will take the easy way out and not use it when traveling.

---

### Post by RichardET on 2014-09-01
It is not purely an Ubuntu issue, my son has an ASUS netbook running  Ubuntu and his device does connect.  Obviously NetworkManager has issues  which are beyond the scope of this discussion, but I am amazed that a  cheap tablet from Barnes & Nobles connects, a cheap netbook connects, a cell phone connects, but the latest Ubuntu  won't in this instance even on hardware as mainstream as a Lenovo.

---

### Post by RichardET on 2014-09-01
Back home and back to WEP, and now my B590 connects flawlessly once again!  Ubuntu rocks!

---

### Post by kurt18947 on 2014-09-02
> **RichardET said:**
> Back home and back to WEP, and now my B590 connects flawlessly once again!  Ubuntu rocks!

WEP?  Can you connect at home using WPA2?  And yes, perhaps the problem is with Network Manager.  I haven't used Ubuntu on many different hotel systems but I had noticed that some hotels have 'interesting' (proprietary) WiFi implementations.  Those 'interesting' installs were likely tested with Windows & Mac (and presumably iOS & android) but they're still proprietary.  I've had trouble connecting even with Windows at some hotels - some Hampton Inns come to mind.

---

### Post by RichardET on 2014-09-02
Yes I have hotspot access on my cell phone and it is set to WPA and I can connect to it.  Thus, I am really in the dark as to why i could not connect to a home router using WPA.
It is a cable service - not sure if that has anything to do with it.  Of course, that house is 130 miles from me, so I might be a few days before I would encounter it again!

---

### Post by RichardET on 2014-11-13
I solved it - I upgraded to Ubuntu 14.10.

---

### Post by kurt18947 on 2014-11-13
> **RichardET said:**
> I solved it - I upgraded to Ubuntu 14.10.

I have a 14.10 install as well, only on one machine.  It seems Realtek 8192cu* devices are working more reliably than on previous Uubntu releases.  AFAIK 'baked in' hardware drivers are contained in the kernel so perhaps the 3.16 image used in Ubuntu14.10 has some useful updates.

---

