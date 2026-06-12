---
title: "Ubuntu Server keeps overriding static IP."
date: 2010-01-27
forum: Server Platforms
---

### Post by unimatrix on 2010-01-27
My ISP offers me a static IP and 2 dynamic IPs. I want to use the static one.
When I run ```
/etc/init.d/newtorkings restart
``` the static IP will be used.
But the next morning (not every morning though) my IP will be the dynamic one again. Something seems to be overriding it. The last time it changed was today at around 8:30 AM.

Why does it keep doing that?

---

### Post by volkswagner on 2010-01-27
What type of isp connection do you have?  

What type of hardware is between isp and server?  

Please post your /etc/networking/interfaces file.

---

### Post by unimatrix on 2010-01-27
> **volkswagner said:**
> What type of isp connection do you have?  

What type of hardware is between isp and server?  

Please post your /etc/networking/interfaces file.

It's a FTTH connection, established via DHCP (unless of course you set your own static IP). Between my ISP and the server there is a FTTH-to-Ethernet switch (the server then acts as a router).

Here is the content of my /etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
#auto lo eth0 eth1

iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
	address 192.168.2.1
	netmask 255.255.255.0
	broadcast 192.168.2.255
	network 192.168.2.0

auto eth0
iface eth0 inet static
	address ***.***.***.***
	netmask 255.255.0.0
	broadcast 93.103.0.255
	network 93.103.0.0
	gateway 93.103.0.1
	post-up iptables-restore < /etc/iptables.up.rules

```
*(Forgive me for censoring out my static IP)*

---

### Post by BkkBonanza on 2010-01-27
Maybe you're still running a dhcp client. Check the output of,

ps afx

to see if dhclient or dhcpd or similar named daemon is running. That's the only reason I can think off hand that the IP would get updated. You'll want to kill any such program.

---

### Post by unimatrix on 2010-01-27
> **BkkBonaza said:**
> Maybe you're still running a dhcp client. Check the output of,

ps afx

to see if dhclient or dhcpd or similar named daemon is running. That's the only reason I can think off hand that the IP would get updated. You'll want to kill any such program.

```

4378 ?        Ss     0:36 /usr/sbin/dhcpd3 -q -pf /var/run/dhcp3-server/dhcpd.pid -cf /etc/dhcp3/dhcpd.conf eth1

```
This is the only dhcp-related thing running (the DHCP server for my internal network on eth1 - the external is on eth0).

---

### Post by BkkBonanza on 2010-01-27
Doesn't sound like that's the problem then. What do you see in your logs around the time that you think the IP change occurs? It may give a hint as to what's happening. I think both syslog and messages could have something. Maybe also make sure there isn't a cron job or cron.daily set that may be doing something.

---

### Post by unimatrix on 2010-01-27
OK it took a while to find, but this seems to be it from *syslog*:

> 
Jan 27 07:12:53 bojler dhclient: DHCPREQUEST of <null address> on eth0 to 255.255.255.255 port 67
Jan 27 07:13:35 bojler last message repeated 3 times
Jan 27 07:14:34 bojler last message repeated 3 times
Jan 27 07:14:48 bojler dhclient: DHCPREQUEST of <null address> on eth0 to 255.255.255.255 port 67
Jan 27 07:14:58 bojler dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jan 27 07:14:58 bojler dhclient: DHCPOFFER of ***.***.***.*** from 89.212.0.1
Jan 27 07:14:58 bojler dhclient: DHCPREQUEST of ***.***.***.*** on eth0 to 255.255.255.255 port 67
Jan 27 07:14:59 bojler dhclient: DHCPACK of ***.***.***.*** from 89.212.0.1
Jan 27 07:14:59 bojler dhclient: bound to ***.***.***.*** -- renewal in 42309 seconds.


****.***.***.**** is, obviously, my dynamic IP.


Also this is what I have in /etc/cron.daily:
```
apache2  apt  apt-get  aptitude  bsdmainutils  chkrootkit  exim4-base  find  find.notslocate.dpkg-new  logrotate  man-db  mlocate  rkhunter  samba  slocate  standard  sysklogd  tomcat55

```

EDIT: Didn't find anything relevant in */var/log/messages*.

---

### Post by BkkBonanza on 2010-01-27
It seems that dhclient must be running or gets started by something. Are you still running network-manager or wicd? These typically will mess up manual changes to the interfaces file because they use their own config to determine what they do, and then they update interfaces sometimes (usually during a boot).

If either of these is installed I would remove them or at least try to alter their config to not interfere, if you need it for wifi.

---

### Post by unimatrix on 2010-01-27
Nope, neither of those are running (I did not install X).

---

### Post by BkkBonanza on 2010-01-27
Is it possible those dhclient log entries are just left overs from previous config that has been fixed now? Maybe this problem has already been fixed. You could try a reboot and make sure that nothing shows up trying to do a dhcp request as whatever is doing it is likely to try during the boot.

Other than that I'm out of ideas, for now.

---

### Post by unimatrix on 2010-01-27
Well it can't be fixed, as this happened today. It happens roughly once a day. Sometimes 2 or 3 days apart.

I have however found something else: the */var/lib/dhcp3/dhclient.leases* file.

This is the content:
> 
lease {
  interface "eth0";
  fixed-address ***.***.***.***;
  option subnet-mask 255.255.0.0;
  option routers 89.212.0.1;
  option dhcp-lease-time 86400;
  option dhcp-message-type 5;
  option domain-name-servers 84.255.209.79,84.255.210.79;
  option dhcp-server-identifier 89.212.0.1;
  option domain-name "t-2.net";
  renew 3 2010/1/27 18:00:08;
  rebind 4 2010/1/28 03:14:59;
  expire 4 2010/1/28 06:14:59;
}
lease {
  interface "eth1";
  fixed-address 192.168.2.199;
  option subnet-mask 255.255.255.0;
  option routers 192.168.2.1;
  option dhcp-lease-time 600;
  option dhcp-message-type 5;
  option domain-name-servers 192.168.2.1;
  option dhcp-server-identifier 192.168.2.1;
  option broadcast-address 192.168.2.255;
  option domain-name "example.org";
  renew 1 2008/7/21 20:06:01;
  rebind 1 2008/7/21 20:10:27;
  expire 1 2008/7/21 20:11:42;
}
lease {
  interface "eth0";
  fixed-address ***.***.***.***;
  option subnet-mask 255.255.0.0;
  option routers 89.212.0.1;
  option dhcp-lease-time 86400;
  option dhcp-message-type 5;
  option domain-name-servers 84.255.209.79,84.255.210.79;
  option dhcp-server-identifier 89.212.0.1;
  option domain-name "t-2.net";
  renew 4 2010/1/28 03:14:50;
  rebind 4 2010/1/28 15:00:08;
  expire 4 2010/1/28 18:00:08;
}


Apparently it is scheduled to renew tomorrow.
Where did this come from?


EDIT: I've deleted the file. We'll see what happens.

---

### Post by unimatrix on 2010-02-02
Yes, deleting the file seems to have worked.

I'm sure a more elegant solution exists though.

Marking as solved.

---

### Post by harisund on 2010-03-02
Did you find a more elegant solution?

---

### Post by unimatrix on 2010-03-06
> **harisund said:**
> Did you find a more elegant solution?

Unfortunately no, but at least deleting the file works for sure.

---

