---
title: "dhcpd with Vista clients"
date: 2009-02-04
forum: Server Platforms
---

### Post by sq377 on 2009-02-04
I'm running Intrepid, though I had the same problem with hardy.  Vista clients are unable to get an IP address from the dhcp server.  I have functional XP and linux clients, but the Vista machines don't seem to get the packet.  I read about the broadcast flag issue, but nothing I've tried has seemed to work.

dhcpd.conf
[PHP]# This declares host names for the static leases for servers
use-host-decl-names on;

# This tells the server that it is the dominant dhcp server, 
# keep handing out requests even if another server pops up.  
# and replace it's leases
authoratative;

# Testing for vista client machines
always-broadcast on;

# These 2 classes declare the 2 groups.  The MAC Addresses are defined in their respective .conf files
class "collectors" {
        match pick-first-value (option dhcp-client-identifier, hardware);
}
class "managers" {
        match pick-first-value (option dhcp-client-identifier, hardware);
}
class "wyse-thin-clients" {
	match if substring (hardware, 1, 2) = 00:80:64;
}

# Include MAC Addresses for collectors and managers
include "/etc/dhcp3/collectors.conf";
include "/etc/dhcp3/trusted.conf";

# Include assigned leases for servers
include "/etc/dhcp3/servers.conf";

# This is the subnet for trusted systems
subnet 192.168.100.0 netmask 255.255.255.0 {
	server-identifier dhcp-server;
	max-lease-time 28800;
	option domain-name "dunstone.local";
	option routers 192.168.100.1;
	option domain-name-servers 192.168.100.12;
	option broadcast-address 192.168.100.255;

	# This is the pool for Admin, its pxe server is for FOG only.
	pool {  
		allow members of "manager";
		option ntp-servers 192.168.100.12;
		option domain-name-servers 192.168.100.12, 208.67.222.222;
		range dynamic-bootp 192.168.100.30 192.168.100.99;
		next-server 192.168.100.3;
		filename "pxelinux.0";
	}

	# This is the pool for collectors.  Its PXE server should only serve Thinstation
	pool {
		allow unknown-clients;
		deny members of "manager";
		allow members of "collector";
		allow members of "wyse-thin-clients";
		range dynamic-bootp 192.168.100.100 192.168.100.254;
		option domain-name-servers 192.168.100.12;
		next-server 192.168.100.24;
		filename "pxelinux.0";
	}	
}
[/PHP]

The included files are just mac address declarations for the servers and classes.

The DHCP Server is responding (Syslog)
[PHP]Feb  4 09:34:35 dhcp-server dhcpd: DHCPDISCOVER from 00:21:6b:XX:XX:XX (Mark-Vista) via eth0
Feb  4 09:34:35 dhcp-server dhcpd: DHCPOFFER on 192.168.100.31 to 00:21:6b:XX:XX:XX (Mark-Vista) via eth0
[/PHP]

Does anyone know what I could possibly do to fix this?  If I can't get this to work I'm going to have to switch to the Windows server, and I would really prefer that I don't have to do that.

Thanks everyone.

---

### Post by HermanAB on 2009-02-04
Windows is broken, so the best solution is to fix it.

See these:
[http://support.microsoft.com/kb/928233](http://support.microsoft.com/kb/928233)

[http://www.reviewingit.com/index.php/content/view/29/2/](http://www.reviewingit.com/index.php/content/view/29/2/)

Cheers,

Herman

---

### Post by sq377 on 2009-02-04
Thanks, but that's not an answer that I can push on to upper management.  They have another location that uses a Microsoft DHCP server, and their Vista machines work fine unaltered.  If ISC's DHCP server can't use the legacy broadcast flag, then they will just see Linux as flawed.

---

### Post by sq377 on 2009-02-05
Sorry, gotta bump.

I really don't want to have to change back to Windows servers to fix this issue.  There has got to be a fix for this.  My roommate runs our home router off of a FreeBSD machine using the ISC DHCP server.  It has nothing special in it's config and Vista clients work just fine. (he's running isc-dhcpd-V3.0.5).

Can anyone think of anything I can try to make this work?

---

### Post by jstraw on 2011-02-01
I've been struggling with this problem myself.  I did the registry edits, tried to force broadcast on for my Vista clients, etc. and nothing worked.

Then I stumbled across [http://www.russellconsultants.com/information/how-to-mainmenu-15/21-networking/43-dhcp-and-windows-vista.html](http://www.russellconsultants.com/information/how-to-mainmenu-15/21-networking/43-dhcp-and-windows-vista.html)

TL;DR: move the domain-name, domain-name-servers, netbios-name-servers and subnet-mask declarations in dhcpd.conf out of any subnet section for your network and into the global section.

I did this and my Vista clients started accepting the DHCPOFFER responses dhcpd was giving them.

---

### Post by SeijiSensei on 2011-02-01
Is this just true for Vista, or does it apply to Windows 7 as well?

---

