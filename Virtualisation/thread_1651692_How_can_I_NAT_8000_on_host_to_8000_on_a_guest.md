---
title: "How can I NAT 8000 on host to 8000 on a guest?"
date: 2010-12-23
forum: Virtualisation
---

### Post by spamalam on 2010-12-23
Using: VirtualBox latest, with kubuntu Host and ubuntu server Guest
Running a python app that binds to 8000 and similarly tomcat on 8080 on the guest.

I set up nat'ing for SSH with no problems using:
```

 2041  2010-12-23 17:25:19 VBoxManage setextradata ubuntu-dev "VBoxInternal/Devices/pcnet/0/LUN#0/Configs/sh/Protocol" TCP
 2042  2010-12-23 17:25:39 VBoxManage setextradata ubuntu-dev "VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/HostPort" 2222
 2043  2010-12-23 17:25:44 VBoxManage setextradata ubuntu-dev "VBoxInternal/Devices/pcnet/0/LUN#0/Config/ssh/GuestPort" 22

```

and I can ssh fine using:
```
ssh -p 2222 localhost-X
```

Problem is, and maybe I've misunderstood something here, I figured I'd be able to forward all traffic for 8000 and 8080 directly onto my guest, simply by change the HostPort and GustPort as well as the Config name:

```

 2041  2010-12-23 17:25:19 VBoxManage setextradata ubuntu-dev "VBoxInternal/Devices/pcnet/0/LUN#0/Configs/django/Protocol" TCP
 2042  2010-12-23 17:25:39 VBoxManage setextradata ubuntu-dev "VBoxInternal/Devices/pcnet/0/LUN#0/Config/django/HostPort" 8000
 2043  2010-12-23 17:25:44 VBoxManage setextradata ubuntu-dev "VBoxInternal/Devices/pcnet/0/LUN#0/Config/django/GuestPort" 8000

```

However, hitting:
[http://localhost:8000/databrowse](http://localhost:8000/databrowse)
does nothing.

Any ideas?

---

### Post by spamalam on 2010-12-23
I should add that I would use bridge mode, but unfortunately this does not appear to work with my Cisco VPN.  If i use NAT i can access corporate infrastructure, if i use bridge i can not.

If there's an easy way to use bridge for bind and NAT for internet, etc. that would be great but I couldn't find a simple / easy guide.

---

### Post by HermanAB on 2010-12-26
Howdy,

You can move things around with either iptables redirect, or with socat.

---

