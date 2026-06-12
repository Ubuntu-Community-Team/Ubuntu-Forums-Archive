---
title: "ltsp dhcp3.conf error"
date: 2010-12-21
forum: Server Platforms
---

### Post by joeoshawa on 2010-12-21
I have been at this for what seems like forever but i am getting somewhere after many errors i got dhcp3 reading the file and everything is almost there but now i got an error i cannot figure out.

first my config file
[HTML] shared-network local {
    subnet 192.168.0.0 netmask 255.255.255.0 {
        range 192.168.0.6 192.168.0.254;
        option subnet-mask 255.255.255.0;
        option ntp-servers 192.168.0.2;
        option domain-name "robinson.ca"; 
        option domain-name-servers 207.164.234.193, 207.164.234.129;
        option broadcast-address 192.168.0.255;
        option routers 192.168.0.2;
        allow unknown-clients;
        option root-path "/opt/ltsp/i386";
if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {   
           filename "/ltsp/i386/pxelinux.0";
} else {
        filename "/ltsp/i386/nbi.img";
    }
}
 [/HTML][HTML] dhcpd self-test failed. Please fix the config file.
The error was: 
Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
/etc/dhcp3/dhcpd.conf line 17: unexpected end of file

^
Configuration file errors encountered -- exiting
root@joe-M61PME-S2P:/var/log# gedit /etc/dhcp3/dhcpd.conf
root@joe-M61PME-S2P:/var/log# /etc/init.d/dhcp3-server restart
dhcpd self-test failed. Please fix the config file.
The error was: 
Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
/etc/dhcp3/dhcpd.conf line 17: unexpected end of file

^
Configuration file errors encountered -- exiting
 [/HTML]I have no idea where to go from here  if anyone can help it would be appreciated the thin client is my for my daughters.

---

### Post by brettg on 2010-12-21
I am not going to go through and count your opening and closing braces, but that error would be indicative of a missing closing brace.

Try indenting your config file differently. Put your closing braces  at the same tabstop as their corresponding opening brace to make it easier to see where one is missing;

Example;

```
if substring( option vendor-class-identifier, 0, 9 )="PXEClient"
{   
    filename "/ltsp/i386/pxelinux.0";
} 
else 
{
    filename "/ltsp/i386/nbi.img";
}
```

---

### Post by joeoshawa on 2010-12-21
i was hoping to get a working thin client running for my daughter if you are wanting to do this here is how.

step 1) shave your head (saves the hair loss later)
step 2) listen to the tons of bs tutorials that don't work and leave you writing files you have no idea what your doing and tutorials that are harder to understand then the files your trying to write.
step 3) take a sledge hammer to your computer
step 4) do what you should have done in the first place and go buy a few pre built computers with windows and make back up disks so you can just reinstall constantly and say to hell with ubuntu cause its too much stress.

---

### Post by joeoshawa on 2010-12-21
ok this is where i am at once again where i started the end of the file is what was written by the program and i have no way of possibly knowing how to fix it change it or anything so if that is what needs to be done please tell me i have no experience with dhcp whatsoever so i am flying blind.

dhcpd.conf taken from a working set-up very close to my own with slight changes for my system 
[HTML] subnet 192.168.0.0 netmask 255.255.255.0 {     #This is a subnet which the dhcpd server controlls, note the { this is required
default-lease-time 345600;             #Sets the time loan time in seconds before computers must renew thier leases
max-lease-time 691200;                 #Set the maximum amount of time a pc can hold a lease for
option domain-name "robinson.ca";         #Sets the domain name
option domain-name-servers 207.164.234.193, 207.164.234.129; #Sets the dns servers you can have one or multiple ones ip address"s seperated by commas
option routers 192.168.0.2;             #Sets the network gateway / router
option broadcast-address 192.168.0.255;     #Sets the network broadcast address
range 192.168.0.20 192.168.0.30;         #Defines a range of ips to be used as leases
}
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }

} [/HTML][HTML]/etc/init.d/dhcp3-server restart
 * Stopping DHCP server dhcpd3                                           [fail] 
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]
  [/HTML][HTML]
tail syslog
Dec 21 20:39:01 joe-M61PME-S2P dhcpd: Wrote 0 leases to leases file.
Dec 21 20:39:01 joe-M61PME-S2P dhcpd: 
Dec 21 20:39:01 joe-M61PME-S2P dhcpd: No subnet declaration for eth1 (0.0.0.0).
Dec 21 20:39:01 joe-M61PME-S2P dhcpd: ** Ignoring requests on eth1.  If this is not what
Dec 21 20:39:01 joe-M61PME-S2P dhcpd:    you want, please write a subnet declaration
Dec 21 20:39:01 joe-M61PME-S2P dhcpd:    in your dhcpd.conf file for the network segment
Dec 21 20:39:01 joe-M61PME-S2P dhcpd:    to which interface eth1 is attached. **
Dec 21 20:39:01 joe-M61PME-S2P dhcpd: 
Dec 21 20:39:01 joe-M61PME-S2P dhcpd: 
Dec 21 20:39:01 joe-M61PME-S2P dhcpd: Not configured to listen on any interfaces!
[/HTML]what am i missing here i copied this in both dhcpd config files

ps i did put eth1 in the file i was supposed to so this is why i am at a loss

---

### Post by joeoshawa on 2010-12-21
ok well believe it or not i have dhcp working. The problem was apparently only eth0 was configured eth1 was not. Now when i do network restart it works but it won't use eth1.
here is the new error

[HTML] Dec 21 22:46:42 robinson NetworkManager[1183]: <info> (eth1): device state change: 7 -> 9 (reason 5)
Dec 21 22:46:42 robinson NetworkManager[1183]: <info> Marking connection 'Auto eth1' invalid.
Dec 21 22:46:42 robinson NetworkManager[1183]: <warn> Activation (eth1) failed.
Dec 21 22:46:42 robinson NetworkManager[1183]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) complete.
Dec 21 22:46:42 robinson NetworkManager[1183]: <info> (eth1): device state change: 9 -> 3 (reason 0)
Dec 21 22:46:42 robinson NetworkManager[1183]: <info> (eth1): deactivating device (reason: 0).
Dec 21 22:46:42 robinson avahi-daemon[1187]: Withdrawing address record for 192.168.0.1 on eth1.
Dec 21 22:46:42 robinson NetworkManager[1183]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Dec 21 22:46:42 robinson NetworkManager[1183]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Dec 21 22:46:43 robinson ntpdate[12748]: step time server 91.189.94.4 offset -0.004891 sec
 [/HTML]

can anyone tell me what i have to do to get this working

---

### Post by HugoSerrano on 2010-12-22
Post your eth0 and eth1 configuration.

Regards!

---

### Post by joeoshawa on 2010-12-22
I had a person on the ubuntu irc chat helping me and this is where we are.

/etc/network/interfaces
[HTML] auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.0.3
netmask 255.255.255.0 [/HTML]
/etc/dhcp3/dhcpd.conf
[HTML] authoritative;
shared-network local{
subnet 192.168.0.0 netmask 255.255.255.0 {     #This is a subnet which the dhcpd server controlls, note the { this is required
default-lease-time 345600;             #Sets the time loan time in seconds before computers must renew thier leases
max-lease-time 691200;                 #Set the maximum amount of time a pc can hold a lease for
option domain-name "robinson.ca";         #Sets the domain name
option domain-name-servers 207.164.234.193, 207.164.234.129; #Sets the dns servers you can have one or multiple ones ip address"s seperated by commas
option routers 192.168.0.3;             #Sets the network gateway / router
option broadcast-address 192.168.0.255;     #Sets the network broadcast address
range 192.168.0.20 192.168.0.30;         #Defines a range of ips to be used as leases
}
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
host kerr {
    hardware ethernet 00:50:fc:54:c4:8e;
    filename "/ltsp/i386/pxelinux.0";
    server-name "kerr.robinson.ca";
} [/HTML]
syslog from networking restart
[HTML] robinson dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 12052
Dec 22 11:58:29 robinson dhclient: killed old client process, removed PID file
Dec 22 11:58:29 robinson dhclient: Internet Systems Consortium DHCP Client V3.1.3
Dec 22 11:58:29 robinson dhclient: Copyright 2004-2009 Internet Systems Consortium.
Dec 22 11:58:29 robinson dhclient: All rights reserved.
Dec 22 11:58:29 robinson dhclient: For info, please visit https://www.isc.org/software/dhcp/
Dec 22 11:58:29 robinson dhclient: 
Dec 22 11:58:29 robinson dhclient: Listening on LPF/eth0/00:24:1d:08:02:a5
Dec 22 11:58:29 robinson dhclient: Sending on   LPF/eth0/00:24:1d:08:02:a5
Dec 22 11:58:29 robinson dhclient: Sending on   Socket/fallback
Dec 22 11:58:29 robinson dhclient: DHCPRELEASE on eth0 to 10.0.0.1 port 67
Dec 22 11:58:29 robinson avahi-daemon[1248]: Withdrawing address record for 10.0.1.33 on eth0.
Dec 22 11:58:29 robinson avahi-daemon[1248]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.0.1.33.
Dec 22 11:58:29 robinson avahi-daemon[1248]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 22 11:58:29 robinson avahi-daemon[1248]: Interface eth0.IPv6 no longer relevant for mDNS.
Dec 22 11:58:29 robinson avahi-daemon[1248]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::224:1dff:fe08:2a5.
Dec 22 11:58:29 robinson avahi-daemon[1248]: Withdrawing address record for fe80::224:1dff:fe08:2a5 on eth0.
Dec 22 11:58:29 robinson NetworkManager[1355]: <info> (eth0): carrier now OFF (device state 1)
Dec 22 11:58:31 robinson avahi-daemon[1248]: Interface eth1.IPv4 no longer relevant for mDNS.
Dec 22 11:58:31 robinson avahi-daemon[1248]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.0.3.
Dec 22 11:58:31 robinson avahi-daemon[1248]: Withdrawing address record for 192.168.0.3 on eth1.
Dec 22 11:58:31 robinson dhclient: Internet Systems Consortium DHCP Client V3.1.3
Dec 22 11:58:31 robinson dhclient: Copyright 2004-2009 Internet Systems Consortium.
Dec 22 11:58:31 robinson dhclient: All rights reserved.
Dec 22 11:58:31 robinson dhclient: For info, please visit https://www.isc.org/software/dhcp/
Dec 22 11:58:31 robinson dhclient: 
Dec 22 11:58:31 robinson NetworkManager[1355]: <info> (eth0): carrier now ON (device state 1)
Dec 22 11:58:31 robinson kernel: [ 1251.974558] forcedeth 0000:00:07.0: irq 41 for MSI/MSI-X
Dec 22 11:58:31 robinson dhclient: Listening on LPF/eth0/00:24:1d:08:02:a5
Dec 22 11:58:31 robinson dhclient: Sending on   LPF/eth0/00:24:1d:08:02:a5
Dec 22 11:58:31 robinson dhclient: Sending on   Socket/fallback
Dec 22 11:58:31 robinson dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 22 11:58:31 robinson dhclient: DHCPOFFER of 10.0.1.33 from 10.0.0.1
Dec 22 11:58:31 robinson dhclient: DHCPREQUEST of 10.0.1.33 on eth0 to 255.255.255.255 port 67
Dec 22 11:58:31 robinson dhclient: DHCPACK of 10.0.1.33 from 10.0.0.1
Dec 22 11:58:31 robinson avahi-daemon[1248]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.1.33.
Dec 22 11:58:31 robinson avahi-daemon[1248]: New relevant interface eth0.IPv4 for mDNS.
Dec 22 11:58:31 robinson avahi-daemon[1248]: Registering new address record for 10.0.1.33 on eth0.IPv4.
Dec 22 11:58:31 robinson avahi-daemon[1248]: Withdrawing address record for 10.0.1.33 on eth0.
Dec 22 11:58:31 robinson avahi-daemon[1248]: Leaving mDNS multicast group on interface eth0.IPv4 with address 10.0.1.33.
Dec 22 11:58:31 robinson avahi-daemon[1248]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 22 11:58:31 robinson avahi-daemon[1248]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.1.33.
Dec 22 11:58:31 robinson avahi-daemon[1248]: New relevant interface eth0.IPv4 for mDNS.
Dec 22 11:58:31 robinson avahi-daemon[1248]: Registering new address record for 10.0.1.33 on eth0.IPv4.
Dec 22 11:58:31 robinson dhclient: bound to 10.0.1.33 -- renewal in 114464 seconds.
Dec 22 11:58:31 robinson ltsp: # Creating dsa-hostkey for robinson.ca
Dec 22 11:58:31 robinson ltsp: # Creating rsa-hostkey for robinson.ca
Dec 22 11:58:31 robinson ltsp: # Creating dsa-hostkey for 192.168.0.3
Dec 22 11:58:31 robinson ltsp: # Creating rsa-hostkey for 192.168.0.3
Dec 22 11:58:31 robinson ltsp: # Creating dsa-hostkey for 10.0.1.33
Dec 22 11:58:31 robinson ltsp: # Creating rsa-hostkey for 10.0.1.33
Dec 22 11:58:31 robinson init: ssh main process (12300) terminated with status 255
Dec 22 11:58:32 robinson avahi-daemon[1248]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::224:1dff:fe08:2a5.
Dec 22 11:58:32 robinson avahi-daemon[1248]: New relevant interface eth0.IPv6 for mDNS.
Dec 22 11:58:32 robinson avahi-daemon[1248]: Registering new address record for fe80::224:1dff:fe08:2a5 on eth0.*.
Dec 22 11:58:32 robinson avahi-daemon[1248]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.3.
Dec 22 11:58:32 robinson dnsmasq[1394]: reading /etc/resolv.conf
Dec 22 11:58:32 robinson avahi-daemon[1248]: New relevant interface eth1.IPv4 for mDNS.
Dec 22 11:58:32 robinson dnsmasq[1394]: using nameserver 10.0.0.1#53
Dec 22 11:58:32 robinson avahi-daemon[1248]: Registering new address record for 192.168.0.3 on eth1.IPv4.
Dec 22 11:58:32 robinson kernel: [ 1253.493045] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 22 11:58:32 robinson ltsp: # Creating dsa-hostkey for robinson.ca
Dec 22 11:58:32 robinson ltsp: # Creating rsa-hostkey for robinson.ca
Dec 22 11:58:32 robinson ltsp: # Creating dsa-hostkey for 192.168.0.3
Dec 22 11:58:32 robinson ltsp: # Creating rsa-hostkey for 192.168.0.3
Dec 22 11:58:32 robinson ltsp: # Creating dsa-hostkey for 10.0.1.33
Dec 22 11:58:32 robinson ltsp: # Creating rsa-hostkey for 10.0.1.33
Dec 22 11:58:32 robinson init: ssh main process (26416) terminated with status 255
Dec 22 11:58:37 robinson ntpdate[26410]: adjust time server 91.189.94.4 offset -0.052857 sec
Dec 22 11:58:41 robinson kernel: [ 1262.400016] eth0: no IPv6 routers present
Dec 22 11:58:43 robinson ntpdate[26567]: step time server 91.189.94.4 offset -0.051261 sec [/HTML]
syslog from /etc/init.d/dhcp3-server restart
[HTML] Dec 22 12:00:34 robinson dhcpd: Wrote 0 deleted host decls to leases file.
Dec 22 12:00:34 robinson dhcpd: Wrote 0 new dynamic host decls to leases file.
Dec 22 12:00:34 robinson dhcpd: Wrote 0 leases to leases file.
Dec 22 12:00:34 robinson dhcpd: Can't bind to dhcp address: Address already in use
Dec 22 12:00:34 robinson dhcpd: Please make sure there is no other dhcp server
Dec 22 12:00:34 robinson dhcpd: running and that there's no entry for dhcp or
Dec 22 12:00:34 robinson dhcpd: bootp in /etc/inetd.conf.   Also make sure you
Dec 22 12:00:34 robinson dhcpd: are not running HP JetAdmin software, which
Dec 22 12:00:34 robinson dhcpd: includes a bootp server. [/HTML]

---

### Post by joeoshawa on 2010-12-22
Last post was huge so I will say this here. Thank you to all those trying to help. This experience is teaching me a lot but I must admit it is a frustrating and painful process. I am a never give up kinda person and even to me this is beginning to feel like a lost cause. Unfortunately for me that means I will be doing this till the day I die so thank you to anyone who feels like taking it to the end.

---

### Post by HugoSerrano on 2010-12-23
try to add this to your dhcpd.conf after the "authoritative;" :

DHCPD_INTERFACE = "eth1";

Cumps!

---

