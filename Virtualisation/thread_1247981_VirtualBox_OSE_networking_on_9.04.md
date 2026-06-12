---
title: "VirtualBox OSE networking on 9.04"
date: 2009-08-23
forum: Virtualisation
---

### Post by ugm6hr on 2009-08-23
I have Ubuntu 9.04 desktop + XFCE with a Virtualbox 2.14 OSE (from the repository) running Ubuntu 9.04 Server.

When the host is connected to my router via wifi, I can get the VM to connect as a peer to my router using the VBox "Host Interface" networking option and selecting my wifi interface card.

This gives the VM an ip in the same range as the host, and allows me to access the Apache2 webserver on the VM from the host without having to mess around with port forwarding etc.

**However, how do I access the Apache server on the VM if the host is not connected to any network?**

I found this: [http://tombuntu.com/index.php/2008/12/17/configure-port-forwarding-to-a-virtualbox-guest-os/](http://tombuntu.com/index.php/2008/12/17/configure-port-forwarding-to-a-virtualbox-guest-os/) (and a few other references stating the same thing).  This suggests that using the VBox NAT setting and configuring a *VBoxManage setextradata* port forward with just 3 lines in Terminal, I should be able to access the VM using localhost.  However, this falls down at the first hurdle, since the VM will not even boot once these commands are issued - VBox errors and stops.

Has anyone got a suggestion?

For the time being, I have had to install OpenBox & FirFox (and xorg) on the Server VM in order to test my VM Apache server when I am not networked on the host.  Not exactly ideal...

---

