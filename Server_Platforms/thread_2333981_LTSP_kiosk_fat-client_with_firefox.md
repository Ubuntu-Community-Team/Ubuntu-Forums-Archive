---
title: "LTSP kiosk fat-client with firefox"
date: 2016-08-15
forum: Server Platforms
---

### Post by nikosbellias on 2016-08-15
Hi all,

I have installed a 64bit Ubuntu Server 14.04.5 LTS. I have also installed ltsp-server-standalone and created a client with ltsp-build-client --fat-client --kiosk.
All configuration with network interfaces and dhcp, as well as with my lts.conf (SCREEN_07=kiosk, KIOSK_EXE="/usr/bin/firefox") is correct and fully functional.
I can boot from a remote client and follow the booting sequence (the remote PC booting from NIC with PXE, gets an IP address from dhcp server, finds kiosk image from tftp and starts booting to fullscreen firefox).

My question is whether there is a way to start firefox to a specific web site (my personal one) rather than the sites firefox launches when first time runs.  
What settings and where should I touch?

Can anybody help...

Thanx in advance,
Nick

---

### Post by howefield on 2016-08-15
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by cariboo on 2016-08-16
In Firefox go to Settings-> Preferences to set what start page you want.

---

