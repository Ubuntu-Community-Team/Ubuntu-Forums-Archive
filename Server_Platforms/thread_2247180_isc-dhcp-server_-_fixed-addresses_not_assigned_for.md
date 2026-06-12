---
title: "isc-dhcp-server - fixed-addresses not assigned for some hosts?"
date: 2014-10-06
forum: Server Platforms
---

### Post by daniel201 on 2014-10-06
Hello,

I'm configuring a home server running Ubuntu Server 14.04.1. I have installed and configured isc-dhcp-server and it is mostly working. I am getting some strange behaviour though. I'd really appreciate some fresh eyes on this as I've spent far too long trying to sort it out. I appreciate the problem is not a show stopper, but previously I had a dd-wrt router handling DHCP with the reservations and abandoning them seems like a retrograde step.

I have (so far) five dhcp clients which include:

Linux Mint 17 workstation      -      *Hostname*: colnago
Crunchbang netbook      -      *Hostname*: moulton
Syno NAS box      -      *Hostname*: carradice
Android phone      -      *Hostname*: littlestinky
Windows 7 laptop      -      *Hostname*: airnimal

I have created dhcp reservations (fixed-address) for each of the above in my dhcpd.conf. I removed entries for them from /var/lib/dhcp/dhcpd.leases and restarted isc-dhcp-server. I also deleted any dhclient leases on the linux machines.
On rejoining machines to the network with the newly configured dhcp server running, the Linux Min 17 workstation (colnago) and the Syno NAS (carradice) received the correct IP address.

The other clients receive addresses from the subnet's pool of available dhcp addresses instead of receiving their reserved IPs.

Here is an excerpt from syslog which shows the DHCPOFFER to the netbook (moulton)  with the incorrect IP address: 
```
[FONT=arial]Oct  5 21:22:15 brox dhcpd: DHCPDISCOVER from 1c:75:08:0a:f2:bf via p4p1[/FONT][FONT=arial]Oct  5 21:22:16 brox dhcpd: DHCPOFFER on 172.16.3.1 to 1c:75:08:0a:f2:bf (moulton) via p4p1[/FONT]
[FONT=arial]Oct  5 21:22:16 brox dhcpd: DHCPREQUEST for 172.16.3.1 (172.16.1.51) from 1c:75:08:0a:f2:bf (moulton) via p4p1[/FONT]
[FONT=arial]Oct  5 21:22:16 brox dhcpd: DHCPACK on 172.16.3.1 to 1c:75:08:0a:f2:bf (moulton) via p4p1[/FONT]

```

Incidentally, the dhclient.config on both the netbook (moulton) and Linux Mint workstation (colnago) are the same.

If I remove the pool of IP addresses from dhcpd.conf in order to try and force isc-dhcp-server to use the fixed address for this host, I get:
[FONT=arial]Oct  5 21:10:36 brox dhcpd: DHCPDISCOVER from 1c:75:08:0a:f2:bf via p4p1: network [172.16.0.0/21]("http://172.16.0.0/21"): no free leases[/FONT]
[FONT=arial]Oct  5 21:13:09 brox dhcpd: Internet Systems Consortium DHCP Server 4.2.4[/FONT]
[FONT=arial]Oct  5 21:13:09 brox dhcpd: Copyright 2004-2012 Internet Systems Consortium.[/FONT]
[FONT=arial]Oct  5 21:13:09 brox dhcpd: All rights reserved.


This is my dhcpd.conf file:
```
#
```[/FONT]```

[FONT=arial]# bikeshed.internal DHCP configuration
#


default-lease-time 43200; # 12 hours
max-lease-time 86400; # 24 hours


log-facility local7;
lease-file-name "/var/lib/dhcpd/dhcpd.leases";
authoritative;


# option definitions
option domain-name "bikeshed.internal";
option domain-search "bikeshed.internal";
option domain-name-servers 172.16.1.51, 208.67.222.222, 208.67.220.220;
option routers 172.16.1.1;
option broadcast-address 172.16.7.255;
option ntp-servers 172.16.2.51;
option netbios-name-servers 172.16.2.51;
option subnet-mask 255.255.248.0;


# dDNS
key "rndc-key" {
        algorithm hmac-md5;
        secret "4DXtfrGLPXfyUWJsTEMTAg==";
};


ddns-updates on;
ddns-update-style interim;
update-static-leases on;
update-conflict-detection false;
ddns-domainname "bikeshed.internal";
ddns-rev-domainname "in-addr.arpa";
allow unknown-clients;
allow client-updates;


# Zone definitions for dDNS
zone bikeshed.internal. {
        primary localhost;
        key rndc-key;
        }


zone 0.16.172.in-addr.arpa. {
        primary localhost;
        key rndc-key;
        }


zone 1.16.172.in-addr.arpa. {
        primary localhost;
        key rndc-key;
        }


zone 2.16.172.in-addr.arpa. {
        primary localhost;
        key rndc-key;
        }
zone 3.16.172.in-addr.arpa. {
        primary localhost;
        key rndc-key;
        }


zone 4.16.172.in-addr.arpa. {
        primary localhost;
        key rndc-key;
        }


zone 5.16.172.in-addr.arpa. {
        primary localhost;
[/FONT]
[FONT=arial]        key rndc-key;
        }


zone 6.16.172.in-addr.arpa. {
        primary localhost;
        key rndc-key;
        }


zone 7.16.172.in-addr.arpa. {
        primary localhost;
        key rndc-key;
        }




subnet 172.16.0.0 netmask 255.255.248.0 {
  range 172.16.3.1 172.16.3.254;




        host moulton {
                hardware ethernet 1c:75:08:0a:f2:bf;
                fixed-address 176.16.2.112;
        }


        ### DHCP Reservations


        ## Infrastructure and servers


        # Netgear wndr3700v2
        # Uses static, but defined here for completeness
        # This needs to updated with new MAC address
        # when the firewall is installed
        host gateway {
        hardware ethernet a0:21:b7:a9:6f:88;
        fixed-address 172.16.1.1;
}


# Netgear wndr3700v2
        # Uses static, but defined here for completeness
        # This needs to be uncommended when the firewall 
        # is installed
        #host wap { 


        #       hardware ethernet a0:21:b7:a9:6f:88;
        #       fixed-address 172.16.1.31;
        # }


        # This needs to be removed when the firewall is 
        # installed and the Netgear wireless router
        # becomes the wireless access point
        host bikeshed-24ghz {
                hardware ethernet 44:94:fc:7e:77:55;
                fixed-address 172.16.1.32;
        }


        #host brox { 
        #       Uses static but defined for completeness
        #       hardware ethernet 60:a4:4c:21:ca:0b;
        #       fixed-address 172.16.1.51;
        # }


        # Storage Options Network Camera
        host ipc1 {
                hardware ethernet 00:a8:f8:00:99:7c;
                fixed-address 172.16.1.181;
        }
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]        # NAS box used for backups
        host carradice {
                hardware ethernet 00:11:32:0d:3d:aa;
                fixed-address 172.16.1.71;
        }


        ## Computers
        host colnago {
                hardware ethernet d4:3d:7e:20:00:a1;
                fixed-address 172.16.2.111;
        }




        host airnimal {
                hardware ethernet 00:26:6c:75:6b:c2;
                fixed-address 172.16.2.113;
        }


        host moulton-wifi {
                option host-name moulton;
                hardware ethernet 4c:0f:6e:4a:84:8a;
                fixed-address 176.16.2.122;
        }


        host airnimal-wifi {
                option host-name airnimal;
                hardware ethernet e0:b9:ba:21:32:b6;
                fixed-address 172.16.2.123;
        }


        host raspberrypi {
                hardware ethernet b8:27:eb:2e:51:29;
                fixed-address 172.16.2.171;
        }


        host littlestinky {
                hardware ethernet 5c:0a:5b:8c:82:63;
                fixed-address 176.16.2.231;
        }
[/FONT]
[FONT=arial]}[/FONT]
```[FONT=arial]

As you can see from my configuration, the correct hardware addresses are assigned. I can't see why this would work for some hosts (e.g. colnago) and not others (moulton).

Thanks in advance for your help.
Daniel[/FONT]

---

### Post by Doug S on 2014-10-06
Hi and welcome to Ubuntu forums.

It would help us to understand your issue better if you could add the host names to your list of clients. For example, I can not figure out what "Crunchbang netbook" is in the list of stuff.

> **daniel201 said:**
> I have (so far) five dhcp clients which include:

Linux Mint 17 workstation [COLOR=#ff0000]... maps to ??? host name (or mac address)[/COLOR]
Crunchbang netbook  [COLOR=#ff0000]... maps to ??? host name [/COLOR]
Syno NAS box[COLOR=#ff0000]   ... maps to ??? host name [/COLOR]
Android phone[COLOR=#ff0000]   ... maps to ??? host name [/COLOR]
Windows 7 laptop[COLOR=#ff0000]   ... maps to ??? host name [/COLOR]
[FONT=arial]
...

As you can see from my configuration, the correct hardware addresses are assigned. I can't see why this would work for some hosts (e.g. [COLOR=#ff0000]Linux Mint 17 workstation[/COLOR]) and not others ([COLOR=#ff0000]Crunchbang netbook[/COLOR]).[/FONT]

---

### Post by daniel201 on 2014-10-06
Hi Doug,
Thanks for pointing that out. Huge oversight on my part!! :)
I've added hostnames to the original post.

Thanks again for your interest.
Daniel

---

### Post by Doug S on 2014-10-06
The only thing I can see that is different than what I have is for this: ```
[FONT=arial]subnet 172.16.0.0 netmask 255.255.248.0 {
  range 172.16.3.1 172.16.3.254; [/FONT]
```I have this:```
[FONT=arial]subnet 172.16.0.0 netmask 255.255.248.0 {
  range 172.16.3.1 172.16.3.254;
}[/FONT]
```The other thing I wonder is a host name of "gateway" and might that be some reserved type name. As a test (after trying the above change), I would try to move the declaration for "[FONT=arial]moulton" to after that declaration, just as [/FONT]"colnago" is now (and I do not have a good explaination for suggesting it).

---

### Post by daniel201 on 2014-10-06
Hi Doug,Thank you for those suggestions.I started out with the subnet declaration as you suggested, but then noticed in a lot of examples the hosts are nested in it before the final "}"I've also tried commenting out the gateway declaration and moving the declaration for moulton to various places in the file.I might try removing everything that's not necessary and leave only the declaration for moulton and see if it then works.Cheers

---

### Post by daniel201 on 2014-10-06
Okay, I've simplified my configuration to:```
## bikeshed.internal DHCP configuration#log-facility local7;lease-file-name "/var/lib/dhcp/dhcpd.leases";authoritative;# option definitionsoption domain-name "bikeshed.internal";option domain-search "bikeshed.internal";option domain-name-servers 172.16.1.51, 208.67.222.222, 208.67.220.220;option routers 172.16.1.1;option subnet-mask 255.255.248.0;subnet 172.16.0.0 netmask 255.255.248.0 {  range 172.16.3.1 172.16.3.254;}host moulton {        hardware ethernet 1c:75:08:0a:f2:bf;        fixed-address 176.16.2.112;}host colnago {        hardware ethernet d4:3d:7e:20:00:a1;        fixed-address 172.16.2.111;}
```Moulton is still getting assigned the address 172.16.3.1 from the dhcp range.

---

### Post by daniel201 on 2014-10-06
```
## bikeshed.internal DHCP configuration
#log-facility local7;lease-file-name "/var/lib/dhcp/dhcpd.leases";
authoritative;

# option definitionsoption domain-name "bikeshed.internal";
option domain-search "bikeshed.internal";
option domain-name-servers 172.16.1.51, 208.67.222.222, 208.67.220.220;
option routers 172.16.1.1;
option subnet-mask 255.255.248.0;

subnet 172.16.0.0 netmask 255.255.248.0 {
    range 172.16.3.1 172.16.3.254;
}

host moulton {
    hardware ethernet 1c:75:08:0a:f2:bf;
    fixed-address 176.16.2.112;
}

host colnago {
    hardware ethernet d4:3d:7e:20:00:a1;
    fixed-address 172.16.2.111;
}
```

---

### Post by daniel201 on 2014-10-06
Seem to be missing carriage returns there...

---

### Post by Doug S on 2014-10-06
> **daniel201 said:**
> Seem to be missing carriage returns there...Yes, that is making it hard to read the posts. It is not clear to me what is wrong.

Edit: Thanks papibe for fixing the above post.

I am baffled. I have been testing on my own system, taking one of my computers back and forth in and out of the pool range, and simply have not been able to get it to behave like the above. It gets a pool range IP address whenever I have it set that way and it gets a dedicated IP via MAC address when I have it set that way.

---

### Post by papibe on 2014-10-06
Hi daniel201.

A few thoughts:

In my experience, when this doesn't work is because the previous lease is still valid, and then renewed instead of getting a new one.

Try this:
[LIST]
[*]Take down the isc-dhcp-server on the server.
[*]Remove the lease from /var/lib/dhcp/dhcpd.leases.
[*]Go to the client machine (moulton) and set up a static IP, on Network-Manager, or in the /etc/network/interfaces in case you are not running NM.
[*]Start isc-dhcp-server again.
[*]Go again to the client, and set back the network to get an IP from DHCP.
[*]
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by daniel201 on 2014-10-07
Hi,
Thank you all for your input. I don't know what was going on last night trying to post that configuration. My attempts to edit the posts simply timed out.

I made the mistake of only leaving moulton's ethernet MAC address in the configuration file when I was testing with it on Wi-Fi. I swapped it for the correct MAC address, deleted the dhcpd.leases file from the server and dhcp.leases files from the client. That seemed to do the trick. I then re-added the ddns configuration, and it still worked.

I'll re-add fixed-addresses for the other hosts I'd like reservations for tonight, one and a time and see what happens.
Thanks again for all your help.

---

