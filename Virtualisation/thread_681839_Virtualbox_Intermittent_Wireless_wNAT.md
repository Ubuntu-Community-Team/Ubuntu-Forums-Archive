---
title: "Virtualbox: Intermittent Wireless w/NAT"
date: 2008-01-29
forum: Virtualisation
---

### Post by ashughes on 2008-01-29
[http://ubuntuforums.org/showthread.php?t=596077](http://ubuntuforums.org/showthread.php?t=596077)

I am having a weird issue with VirtualBox on Ubuntu 7.10 related to wireless.  On my host, I connect to any network (school or home, doesnt matter).  Whenever I start up my WinXP VM (which is configured to use NAT) the VM appears to freeze almost instantly.  The only way to unfreeze it is to move the mouse on the VM window which subsequently causes my host wireless to disconnect and reconnect.  The process repeats itself on average every 15-30 seconds.  It is really annoying.  I do not have this issue if I use the same network settings for the VM but connect via wired connection on my host.

I have scoured this thread to no avail.  It seems to describe a similar issue to mine but does not provide a solution.
[http://ubuntuforums.org/showthread.php?t=596077](http://ubuntuforums.org/showthread.php?t=596077)

I have also spent hours jumping from google search to google search to no avail.  I even tried the VirtualBox forums and was not able to find a solution.

If anyone can shed some light on this issue, It would be greatly appreciated.

Thank you.

---

### Post by trycage on 2008-03-16
Dear All

keywords: Virtualbox Ubuntu gutsy Wireless hangs

I have the same problem of frequent disconnections (with guest os hangs) of my Wireless in UBUNTU gutsy using VBOX 1.5.x. with guest os WINXP.

I tried the following workaround

Checking from WinXp guest OS, VBox assign an DHCP IP 
in the domain 10.0.2.x
with gateway 10.0.2.2
and
DNS                10.0.2.3


Hence I forced my virtual network interface to the static address
IP 10.0.2.200
Mask 255.255.255.0
Gateway 10.0.2.2
DNS 10.0.2.3
<it was mistyped... sorry, now it is correct>

And until now it is working fine (I completed the total windows update process
from the scratch)

I seems to be something related to the DHCP service of the NAT

I hope it can Help

Trycage

---

### Post by bdentremont on 2008-12-29
trycage,
Thanks for the advise. Assigning a fixed IP in the WinXP guest worked for me.  However, correct configuration is:

IP 10.0.2.200
Mask 255.255.255.0
Gateway **10.0.2.2**
DNS **10.0.2.3**

I believe the discrepancies between the Gateway and DNS addresses that you said that you found via DCHP and assigned manually must be a typo.

---

### Post by trycage on 2008-12-29
Yes,
Thanks it was a mistype. I'm glad it worked... i'm correcting the post now.

Trycage

---

