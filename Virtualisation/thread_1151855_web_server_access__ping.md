---
title: "web server access / ping"
date: 2009-05-07
forum: Virtualisation
---

### Post by xtremer on 2009-05-07
[B]i have Ubuntu 8.10 as a host and Debian netinst as a guest on Virtualbox, and the NAT netwrok between them is working fine.
I installed apache on both, but since its a NAT netwrok between them, Debian can access and the internet and access the webserver installed on Ubuntu and can ping its ip(192.169.0.102) and debian has an ip of 10.0.2.15 as default. But the problem is i cant ping debian and access it webserver from ubuntu bcoz the network range is different. some told me to do port forwardig and only access port 80.
so is this the right solution???? if yes, can some one guide me how to do it?
if no, what is the alternative?

NB: am testing snort with acid on debian.[/B]

---

### Post by Perryg on 2009-05-07
You can do this with port forwarding but switching to bridged mode for the guest in the VBox settings will make you life a lot easier.

---

### Post by xtremer on 2009-05-07
> **Perryg said:**
> You can do this with port forwarding but switching to bridged mode for the guest in the VBox settings will make you life a lot easier.

**i see no "bridged mode" in Vbox settings, at the network settings only found: NAT, host interface and internal network and i tried 3 of them and nothing works.**

---

### Post by Perryg on 2009-05-07
> **xtremer said:**
> **i see no "bridged mode" in Vbox settings, at the network settings only found: NAT, host interface and internal network and i tried 3 of them and nothing works.**

Oops older version of VBox.  Host Interface. If it does not work then you have a problem with the settings.  Go into the guest and run the ifconfig after you boot.  You should see the address scheme that is in the same as the host.  If not then you still need to change the setting in the guest or do a dhclient -r to try to renew the dhcp lease from a terminal.

---

