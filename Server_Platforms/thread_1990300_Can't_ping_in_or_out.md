---
title: "Can't ping in or out"
date: 2012-05-29
forum: Server Platforms
---

### Post by scovilletech on 2012-05-29
Hi,

I have just installed a setup of Ubuntu 11.10 server and can't ping in or out.  The setup went fine and grabbed stuff from the web and I can ping the server when it is booting up until it gets to the logon prompt.  Obviously it's a service of some kind.  I have disabled ufw by typing sudo ufw disable, but that didn't do it.  Any ideas?  The ip is setup statically.

---

### Post by spynappels on 2012-05-29
What do you get when you do the following:
```
ping 127.0.0.1
```

Please also post the results of /etc/network/interfaces and /etc/resolv.conf

---

### Post by stmiller on 2012-05-29
Is this a virtual machine?

---

### Post by robgr85 on 2012-05-30
Right now I am out of ubuntu OS so I can not check *ufw disable *function, but if You would want to disable it ultimately try using *chkconfig ufw off* command.

Is the network properly configured for manual IP config? Is *dhclient3* service running (I think that it may causing Your problems)? Have You tried to disable it and restart network (*service networking restart*)?

Tell us me what is *route -rn* output? Have You done some changes for hardening of Your OS (modyfied iptables etc)?

---

### Post by rds529 on 2012-05-30
Can you ping successfully if you allow it to receive an IP address from DHCP?

---

### Post by pctx on 2012-05-30
> **scovilletech said:**
> Hi,

I have just installed a setup of Ubuntu 11.10 server and can't ping in or out.  The setup went fine and grabbed stuff from the web and I can ping the server when it is booting up until it gets to the logon prompt.  Obviously it's a service of some kind.  I have disabled ufw by typing sudo ufw disable, but that didn't do it.  Any ideas?  The ip is setup statically.
Couple of things:
Do an:
```
 ifconfig
```Copy and paste that back into this thread. (Omitting your MAC address for security purposes)

As some mentioned:
```
ping localhost
```

ping yourgatewayiphere
If you have a valid IP address an not an RFC private IP, you should be able to ping the gateway.  Next try pinging other known IP's on the network.

Try:
```
sudo ufw status
```
This will display whether or not UFW is indeed disabled.  If it's not, check /var/log/ufw.log for messages on startup/confg/errors

If this is a VM, if it is on a local machine that is using NAT via the host IP, make sure your host has internet connectivity.  If it is bridged, make sure you're getting an IP from your DHCP server (actual server or router).

That should get you closer to getting connectivity.  Let us know.

---

