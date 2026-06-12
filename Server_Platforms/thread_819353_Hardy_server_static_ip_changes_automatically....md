---
title: "Hardy server static ip changes automatically..."
date: 2008-06-05
forum: Server Platforms
---

### Post by twgray on 2008-06-05
I have installed Hardy server behind a router.  After installation, I changed my IP address from DHCP to static by editing my /etc/network/interfaces file as follows:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.0.1.xxx
netmask 255.255.255.0
network 10.0.1.0
broadcast 10.0.1.0
gateway 10.0.1.1

The router, of course, has NAT enabled.  Sometime overnight, the static IP address changes to one in the range that the router is assigning using DHCP, as if the static IP were renewing with DHCP.  What am I doing wrong, or missing?

---

### Post by thepurplemonkey on 2008-06-05
I'm having the same issue on a newly installed and updated Hardy Server:

[HTML]uname -a
Linux dlfile1 2.6.24-18-server #1 SMP Wed May 28 21:25:52 UTC 2008 i686 GNU/Linux[/HTML]


[HTML]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.3
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
[/HTML]
cat /var/log/syslog has:
[HTML]...
Jun  5 09:17:01 dlfile1 /USR/SBIN/CRON[11801]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  5 09:17:11 dlfile1 dhclient: DHCPREQUEST of <null address> on eth0 to 255.255.255.255 port 67
Jun  5 09:17:44 dlfile1 last message repeated 2 times
...

Jun  5 10:04:18 dlfile1 last message repeated 2 times
Jun  5 10:04:32 dlfile1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Jun  5 10:04:32 dlfile1 dhclient: DHCPOFFER of 192.168.0.247 from 192.168.0.1
Jun  5 10:04:32 dlfile1 dhclient: DHCPREQUEST of 192.168.0.247 on eth0 to 255.255.255.255 port 67
Jun  5 10:04:32 dlfile1 dhclient: DHCPACK of 192.168.0.247 from 192.168.0.1
Jun  5 10:04:32 dlfile1 dhclient: can't create /var/lib/dhcp3/dhclient.eth0.leases: Permission denied
Jun  5 10:04:32 dlfile1 dhclient: bound to 192.168.0.247 -- renewal in 18024 seconds.
Jun  5 10:17:01 dlfile1 /USR/SBIN/CRON[11825]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  5 10:32:02 dlfile1 dhclient: receive_packet failed on eth0: Network is down
Jun  5 10:32:02 dlfile1 kernel: [87881.616801] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Jun  5 10:32:03 dlfile1 ntpdate[11880]: step time server 91.189.94.4 offset -6.717601 sec
Jun  5 10:32:05 dlfile1 kernel: [87891.933481] eth0: no IPv6 routers present[/HTML]

sudo /etc/init.d/networking restart "fixes" the issue. It seems to happen every ~24 hours.

---

### Post by twgray on 2008-06-05
Thanks for the reply.  After more research, someone suggested that simply resetting the machine after making the change to /etc/network/interfaces might fix the problem.  Another suggests the following change to /etc/dhcp3/dhclient:

alias {
      interface "eth0";
      fixed-address 10.1.0.xxxx;
      option subnet-mask 255.255.255.0;
}

I haven't tried either on yet so if one of these works let me know.

---

### Post by thepurplemonkey on 2008-06-05
We'll see. I just rebooted it. I'll report back tomorrow around this time and let you know if that worked.

---

### Post by cdenley on 2008-06-05
It seems that when you change an adapter from dhcp to static, then restart networking, dhclient3 continues to run, presumably updating the now static adapter's ip. I think this would fix it, but I'm almost positive a reboot would.
```

sudo killall dhclient3

```

---

### Post by thepurplemonkey on 2008-06-06
Rebooting seemed to sure it. I installed/updated (new kernel)/rebooted, THEN I set the static IP (/etc/init.d/networking restart) and didn't reboot after I set it to static.

---

