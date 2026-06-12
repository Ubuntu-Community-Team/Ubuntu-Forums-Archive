---
title: "Homemade router w/ Ubuntu server"
date: 2012-10-24
forum: Server Platforms
---

### Post by skipsbro on 2012-10-24
Hello all

I've been having an interesting problem. In the past, I've set up an ubuntu server for use as a wired router (which I much prefer to the little plastic variety) and I figured I would try my hand at creating a wireless router with an old PC and Ubuntu server.

...and I'm having an interesting problem. Everything appears to be functioning normally (Broadcasting SSID, WPA auth, makes connection, client is assigned IP address, internet access, etc), however, it only works for a few minutes at a time. Pages stop loading and any active SSH connections stop responding. (If I were having this issue on a wired connection, I would suspect the cable from the router to the computer had been pulled.) The PC this is running on does not seem to be having issues with the processing (load averages of about 0.05). There are no errors in any config files that I could see.

Turning the wireless hardware off and on again on the client side fixes the connection, but only temporary. Does anyone here have any experience with this sort of thing? I've tried a bit of googling, but I can't seem to find any other cases like this.

Help me Ubuntu forms, you're my only hope.

---

### Post by chadk5utc on 2012-10-31
it has been a few years since I did what your doing but from what I remember there are a few things to check.
 wireless card/device that your using for the AP must be able to run in master mode
and I remember having an issue with the wifi driver and had to compile a new one before it worked reliably. what I do now is routing with server and added another NIC and a commercial linux based AP.

---

### Post by kennethconn on 2012-10-31
Is it possible that it is a non-OS issue (i.e. wireless issue)?

---

