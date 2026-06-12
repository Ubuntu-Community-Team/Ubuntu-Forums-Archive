---
title: "How do I prevent NIC from shutting off while server sleeps?"
date: 2007-12-03
forum: Server Platforms
---

### Post by kikos on 2007-12-03
I installed Ubuntu Desktop 7.10 and installed Zimbra on it.  It runs well.  However, after some period of time, the server seems to sleep and brings the network interface card down with it.  This is problematic because I cannot connect to my Zimbra server remotely while the NIC is off.

My NIC is a USB dongle, so it could also be that the USB powers down while sleeping.

Does anyone have any idea of how I can keep the server responsive to incoming connections 24/7?

---

### Post by crouton on 2007-12-05
You may want to play with the Power Management settings under System->Preferences, or disable apm altogether.  Desktop 7.10 has a few things enabled that would sleep/hibernate a system, and you definitely don't want that in a server.

---

