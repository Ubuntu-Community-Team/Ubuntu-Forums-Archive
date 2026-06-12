---
title: "Problem DHCPd Server"
date: 2007-10-10
forum: Server Platforms
---

### Post by adamjs on 2007-10-10
I am unable to start my DHCP server which is ISC DHCPd version 3.0.4.  Pasted below is the exact input/output when I try to start it.

```
adamjs@ajsserv:/etc/init.d$ ./dhcp3-server start
dhcpd self-test failed. Please fix the config file.
The error was:
adamjs@ajsserv:/etc/init.d$
```


Can anyone tell me what is wrong?

```
ddns-updates off;
option netbios-name-servers 102.168.0.60;
option ntp-servers pool.ntp.org;
option time-servers pool.ntp.org;
option domain-name-servers 192.168.0.60;
option domain-name "ajs-domain.local";
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;

# AJS Local Net
shared-network AJSnet {
	ddns-updates off;
	# AJS Local Domain
	subnet 192.168.0.0 netmask 255.255.255.0 {
		ddns-updates off;
		range 192.168.0.100 192.168.0.120;
		}
	}
```

Any help would be appreciated.
AJS

---

