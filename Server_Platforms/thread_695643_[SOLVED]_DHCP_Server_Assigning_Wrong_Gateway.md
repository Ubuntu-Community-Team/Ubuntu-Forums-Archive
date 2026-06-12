---
title: "[SOLVED] DHCP Server Assigning Wrong Gateway"
date: 2008-02-13
forum: Server Platforms
---

### Post by chris.zeman on 2008-02-13
This is a strange problem indeeed, as everything had been working fine for months.

```
Server 1 (Router): BrazilFW (172.16.100.200/201) - Default gateway to the internet

Server 2 (Router): Windows XP Pro (172.16.100.202) - Gateway to corporate network

Server 3 (Web Server): Ubuntu 7.10 (172.16.100.203) - Web & DHCP Server
```

I could have BrazilFW's DHCP Server enabled, but I need certain machines to PXE boot from the Ubuntu machine. BrazilFW's DHCP server doesn't allow for such configuration (that I have found).

Suddenly, all machines on my network were being assigned 172.16.100.202 as their default gateway. The only time that machines on my network should use 172.16.100.202 as their gateway is when the attempt to access 2 specific subnets. The DHCP configuration is set to assign 172.16.100.200 as the default gateway. The only odd thing I found is that 172.16.100.202 was showing up as a network Plug and Pray device. Could that have anything to do with it?

I hope I have provided enough information. Please let me know if I have not, and I'll provide any added information.

Thank you,
Chris

---

### Post by kyriakos1977 on 2008-02-14
Are you sure the windows XP Pro DHCP Server is not assining IP's ?

post your dhcpd.conf please

---

### Post by chris.zeman on 2008-02-14
I wasn't aware of a DHCP server being installed in XP Pro. I'll check into it.

Here is my dhcpd.conf:
```
option routers 172.16.100.200;
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
ddns-update-style none;

option domain-name "domain.net";
option domain-name-servers 172.16.100.200, 208.67.222.222;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# Cyber
subnet 172.16.0.0 netmask 255.255.0.0 {
	max-lease-time 7200;
	default-lease-time 3600;
	option static-routes 10.115.0.0 172.16.100.202 , 10.128.0.0 172.16.100.202;
	option time-servers 172.16.100.200;
	option domain-name-servers 172.16.100.200;
	option domain-name "domain.net";
	option broadcast-address 172.16.255.255;
	option subnet-mask 255.255.0.0;
	option routers 172.16.100.200;
	authoritative;
	allow client-updates;
	range 172.16.1.200 172.16.1.254;
	}
# Workstations
group {
	option routers 172.16.100.200;
	# Mary
	host CyberMary {
		hardware ethernet 00:1b:78:ab:1b:b0;
		fixed-address 172.16.1.1;
		}
	# Christopher
	host RC4 {
		hardware ethernet 00:02:e3:3f:9a:de;
		fixed-address 172.16.1.2;
		}
	# Tony
	host CyberTony {
		hardware ethernet 00:11:d8:40:ac:d6;
		fixed-address 172.16.1.3;
		}
	# Dennis
	host RC2 {
		hardware ethernet 00:e0:18:e6:ff:75;
		fixed-address 172.16.1.4;
		}
	# Jerome
	host RC3 {
		hardware ethernet 00:13:20:55:1a:10;
		fixed-address 172.16.1.5;
		}
	# Jennifer
	host CyberGal-2007 {
		hardware ethernet 00:13:20:67:85:ea;
		fixed-address 172.16.1.6;
		}
	# Harold
	host RC1 {
		hardware ethernet 00:a0:c9:0f:ba:93;
		fixed-address 172.16.1.7;
		}
	# Mark
	host CyberMark {
		hardware ethernet 00:11:d8:18:5f:9c;
		fixed-address 172.16.1.8;
		}
	# Technician Workstation
	host TechDesk {
		hardware ethernet 00:0f:fe:1c:8b:6e;
		fixed-address 172.16.1.10;
		}
	# Automated Message System
	host AMS {
		hardware ethernet 00:e0:18:e6:ff:37;
		fixed-address 172.16.1.17;
		}
	# Engineering Workstation
	host Engineering {
		hardware ethernet 00:02:a5:e5:3f:9d;
		fixed-address 172.16.1.20;
		}
	# Haunted House
	host Studio13 {
		hardware ethernet 00:02:a5:e5:3e:ff;
		fixed-address 172.16.1.100;
		}
	# Loss Prevention Workstation
	host MonitorRoom {
		hardware ethernet 00:b0:d0:2a:18:27;
		fixed-address 172.16.1.130;
		}
	}
# Wireless Access Points
group {
	# Switchboard 5
	host CyberSWB5 {
		hardware ethernet 00:0f:3d:ca:4e:9c;
		fixed-address 172.16.2.1;
		}
	# Operations
	host CyberPkOps {
		hardware ethernet 00:11:95:d9:46:ca;
		fixed-address 172.16.2.2;
		}
	# Salloon
	host CyberCrzyB {
		hardware ethernet 00:11:95:d9:46:78;
		fixed-address 172.16.2.3;
		}
	# Electronics Office
	host CyberOffice {
		hardware ethernet 00:11:95:da:13:12;
		fixed-address 172.16.2.4;
		}
	# Engineering Office
	host CyberEngineering {
		hardware ethernet 00:14:bf:73:03:25;
		fixed-address 172.16.2.6;
		}
	}
# Servers
group {
	# Cybernetics Server 1
	host Cybernet {
		hardware ethernet 00:02:b3:62:37:dc;
		fixed-address 172.16.100.100;
		}
	# Cybernetics Server 3
	host Cybernet3 {
		hardware ethernet 00:11:d8:18:57:b0;
		fixed-address 172.16.100.102;
		}
	# Status Display
	host RideStatus {
		hardware ethernet 00:10:dc:7c:ce:9e;
		fixed-address 172.16.100.210;
		}
	}
# Printers
group {
	# HP LaserJet 4V (Electronics)
	host HPLaserJet4V {
		hardware ethernet 00:60:b0:25:79:27;
		fixed-address 172.16.101.1;
		}
	# HP LaserJet 2200 (Control)
	host HPLaserJet2200 {
		hardware ethernet 00:01:e6:6d:07:8f;
		fixed-address 172.16.101.2;
		}
	# HP DesignJet 750C Plotter (Office)
	host HPDesignJet750C {
		hardware ethernet 08:00:09:8d:e1:f6;
		fixed-address 172.16.101.10;
		}
	}
# Energy Management
group {
	filename "netboot/pxelinux.0";
	# Energy Management Development Workstation
	host EnMan-Devel {
		hardware ethernet 00:08:74:d2:b8:21;
		fixed-address 172.16.24.254;
		}
	}

```

Thank you,
Chris

---

### Post by faulkes on 2008-02-14
Note sure, although at the very top of your dhcp.conf you have "options rouers 172 etc" listed and then below in your scopes you relist it.  You may wisht to remove the extraneous  line at the top.

Faulkes

---

### Post by kyriakos1977 on 2008-02-14
your dhcpd.conf looks ok

"all machines on my network were being assigned 172.16.100.202 as their default gateway"
look on these machines whitch server assinged the IP

have in mind that there should be ONLY ONE dhcp server !
and disable the dhcp service form windows XP

---

### Post by chris.zeman on 2008-02-14
I forgot to check the XP machine when I was in the "data center". XP doesn't come with a DHCP server, does it? I never installed one on the XP box, and I am the one who installed Windows on it.

Thank you,
Chris

---

### Post by faulkes on 2008-02-14
> **chris.zeman said:**
> I forgot to check the XP machine when I was in the "data center". XP doesn't come with a DHCP server, does it? I never installed one on the XP box, and I am the one who installed Windows on it.

Thank you,
Chris

I don't recall XP (professional or otherwise) having by default a DHCP server installed or available.

This may not be true of your installation if you used any type of slipstreaming.

Faulkes

---

### Post by chris.zeman on 2008-02-20
I got sidetracked. lol

There isn't a DHCP server installed on the Windows box, and the problem hasn't happened again. The best I can figure is that the Windows workstations saw the Windows box as a gateway due to Universal Plug'n'Pray. The firewall on the Windows box was turned off for some reason, so I turned it back on and blocked UPnP traffic. We'll see how that goes.

Thank you everyone for your help.

Chris

---

