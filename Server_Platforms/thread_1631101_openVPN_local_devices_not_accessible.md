---
title: "openVPN local devices not accessible"
date: 2010-11-26
forum: Server Platforms
---

### Post by ronkmonster on 2010-11-26
I've setup openVPN using bridging following these guides

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
and
[https://help.ubuntu.com/10.04/serverguide/C/openvpn.html](https://help.ubuntu.com/10.04/serverguide/C/openvpn.html)

I'm running Ubuntu Server 10.10

My clients can connect and get their own IP within my ip range (192.168.1.x)

They can ping each other and I've tested I can use the connection a lan game and a windows RDP connection.

The problem is I cannot access any of the actual local network devices except the vpnServer.

Is their something else that needs to be done to allow full network access?

---

### Post by ronkmonster on 2010-11-26
Sorry for double posting, I've just disabled the firewall (ufw) and I can ping local devices now. Is there a guide to allow VPN traffic through but keeping the firewall on?

---

### Post by SeijiSensei on 2010-11-26
Add some rules like this:

```
ipchains -A INPUT  -i tun0 -j ACCEPT
ipchains -A OUTPUT -o tun0 -j ACCEPT
```

If you're supporting multiple tunnels, make duplicates of these changing tun0 to tun1, tun2, etc.

---

### Post by ronkmonster on 2010-11-26
Thanks, I had already added this:

# VPN Config
-A ufw-before-input -i tap0 -j ACCEPT
-A ufw-before-output -i tap0 -j ACCEPT

to
/etc/ufw/before.rules

Working ok now.

It might be worth adding this step to the openVPN setup. Where do I submit this request?

---

### Post by SeijiSensei on 2010-11-26
> **ronkmonster said:**
> It might be worth adding this step to the openVPN setup. Where do I submit this request?

That's really not possible since there's no guarantee how people are running iptables.  I write my own scripts, for instance.

---

### Post by ronkmonster on 2010-11-26
> **SeijiSensei said:**
> That's really not possible since there's no guarantee how people are running iptables.  I write my own scripts, for instance.

Yes but it's not mentioned at all that the firewall needs to be changed and ufw is the default so it could be should be shown how to configure it. iptables too for people for who write their own. 

At least with one or two examples, people would have an idea what needs to be done with other firewalls.

---

