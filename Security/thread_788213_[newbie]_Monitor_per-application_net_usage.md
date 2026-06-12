---
title: "[newbie] Monitor per-application net usage"
date: 2008-05-09
forum: Security
---

### Post by Beelzebuddy on 2008-05-09
Is there any way of seeing which applications are using the internet, and how much bandwidth each is soaking up?  How about the ability to deny certain applications network access?

I ask because I've come across my first real EULA (not counting GPL copy+paste) in a linux program, for RealPlayer.  It's a standard EULA of the Windows variety, saying essentially "we're going to monitor every single thing you do on your computer while our software is running, and half the stuff you do when it's not.  We're going to keep this data forever and do whatever we want with it without telling you, but we promise not to share it with anyone except select business partners.  You can trust us.  Srsly."  Naturally, I deselected every phone-home checkbox I could find and told the program to proxy into nowhere, but it would be nice to be sure.  

As linux becomes increasingly mainstream I can only see this kind of stunt becoming more common.  On a windows box I consider a good firewall to be as necessary to guard against spyware as outside attacks.  Tools like firestarter do a great job of pointing out how I might be vulnerable to the outside world.  Is there anything that looks with a more inward eye?

---

### Post by The Cog on 2008-05-10
I don't think there really is. I don't think the unix types have really felt that much of a need before - it's only recently that windows type users have started taking their habits to Linux and running untrustworthy applications. 

The one way I can think of controlling this is with app armour. It's available on Hardy. You basically list everything a program is allowed to do - which files it can read/write etc. You can run a program in learning mode to learn what its normal behaviour is, then edit and enforce that as a policy. It's not quite the same thing as a firewall that identifies the owning process - in some ways it's worse (only polices selected applications) and in some ways better (polices all activity not just network).

---

### Post by durand on 2008-11-12
I'd also like to know if such a program exists. I'm a "unix type" and I think it would be cool to have a top like program for the network card since System Monitor only does so much..

---

