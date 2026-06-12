---
title: "Is PPP necessary?"
date: 2006-01-13
forum: Server Platforms
---

### Post by nordmann on 2006-01-13
I'm running an Ubuntu Breezy web/mail server, and I'm trying to turn off any features from the custom install that I don't really need.  So I was just poking around with dpkg and I noticed the PPP daemon was installed and running.  I'm not aware of any reason I might need PPP on this machine.  Is PPP used for anything other than providing and accessing points of presence for dialup and VPN connections?

I would try turning it off and "see what happens", but I don't have ready access to the physical console, so I hesitate to turn PPP off if it might affect my ability to SSH in.

---

### Post by Mr_Grieves on 2006-01-13
Dialup. VPN I did not know of.. as long as you're connected via regular ethernet/wifi you're safe to turn it off, if it's not there for a reason, like providing a backup connecting if you're regular circuit fails.

---

