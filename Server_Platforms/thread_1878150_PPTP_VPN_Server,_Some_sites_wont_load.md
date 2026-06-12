---
title: "PPTP VPN Server, Some sites wont load"
date: 2011-11-09
forum: Server Platforms
---

### Post by skej on 2011-11-09
Running Ubuntu 11.10 Server 32bit fresh install configured as a PPTP VPN server.

I am able to connect to my VPN server using both windows 7 and Ubuntu desktop just fine, and using wireshark verify that all packets are being compressed and sent through the VPN tunnel I can also browse computers on the network on the server side of the connection. 

Some websites work but there are several that will not load while using the VPN, one of them is ubuntu forums also sourceforge and vmware.com and several others.

I can ping the web servers while connected but the websites just will not load, and time out. The second I disconnect from the VPN they load instantly.

---

### Post by vasile002 on 2011-11-09
You need to set the MTU of the PPP interface to 1500 I believe. I edited /etc/ppp/ip-up and set:
```

[ -x /etc/ppp/ip-up.local ] && /etc/ppp/ip-up.local "$@"

**/sbin/ifconfig $REALDEVICE mtu 1500**

exit 0

```

---

### Post by skej on 2011-11-09
IT WORKED!

Thank you so much, this has cursed me for 8 months now

---

### Post by skej on 2011-11-09
False alarm, I was stupid enough not to clear my browser cache.

I'm still having the same issue.:(

---

