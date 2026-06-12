---
title: "openvpn regression in ubuntu 16.04"
date: 2016-07-23
forum: Ubuntu, Linux and OS Chat
---

### Post by Jeffrey_Sloan on 2016-07-23
I've run openvpn on Linux dating back to the early 2000s. I've been running it on ubuntu server since 8.04, and it's always been easy peasy. When I want to add a new vpn, I add the config file and keys on both ends, restart openvpn, and we're up and running. 

Starting with 16.04, I've noticed a very annoying regression to a windows-like behavior - namely, that adding a new openvpn configuration and restarting openvpn no longer establishes a new vpn connection. I was disappointed to find, after nearly pulling all my hair out, that a reboot allows the new configuration to be recognized, and the vpn starts up. 

I suspect it's some sort of systemd brokenness. I was able to start the vpn by issuing the proper command (e.g. /usr/sbin/openvpn --daemon ovpn-m2tuc --status /run/openvpn/m2tuc.status 10 --cd /etc/openvpn --script-security) but that's sort of klugey.

I tried various systemctl commands to get it to re-read the openvpn config files, but nothing worked except a reboot. What is this, windows nt?

---

### Post by cariboo on 2016-07-25
Have you created a bug report? Developers don't frequent the forums, so the best way to get their attention is to create a bug report. Use:

```
ubuntu-bug openvpn
```

to create the bug report.

---

### Post by RichardET on 2016-07-28
> **Jeffrey_Sloan said:**
> I've run openvpn on Linux dating back to the early 2000s. I've been running it on ubuntu server since 8.04, and it's always been easy peasy. When I want to add a new vpn, I add the config file and keys on both ends, restart openvpn, and we're up and running. 

Starting with 16.04, I've noticed a very annoying regression to a windows-like behavior - namely, that adding a new openvpn configuration and restarting openvpn no longer establishes a new vpn connection. I was disappointed to find, after nearly pulling all my hair out, that a reboot allows the new configuration to be recognized, and the vpn starts up. 

I suspect it's some sort of systemd brokenness. I was able to start the vpn by issuing the proper command (e.g. /usr/sbin/openvpn --daemon ovpn-m2tuc --status /run/openvpn/m2tuc.status 10 --cd /etc/openvpn --script-security) but that's sort of klugey.

I tried various systemctl commands to get it to re-read the openvpn config files, but nothing worked except a reboot. What is this, windows nt?

Since you are running a server based system, perhaps you might consider OpenBSD?  No systemd there!!

---

