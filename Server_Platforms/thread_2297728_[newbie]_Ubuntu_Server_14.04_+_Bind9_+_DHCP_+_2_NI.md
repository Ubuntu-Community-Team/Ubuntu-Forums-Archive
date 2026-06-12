---
title: "[newbie] Ubuntu Server 14.04 + Bind9 + DHCP + 2 NICs = Some problems"
date: 2015-10-06
forum: Server Platforms
---

### Post by mborges on 2015-10-06
Hello.

I've searched here and in google without luck, many returns for "bind9 2 nics routing problem" but none was useful.
This configuration I did so far (and most is working, except for our www page which is located externally) has been achieved with the help of articles here in Ubuntu forums, but I may have missed something.

I'm a newbie in linux servers, so please be gentle.

My current goal is to migrate a few (very old: nt4, 2000 and 2003) windows servers we have to something that will not cost us an arm and a leg and is resilient. 
Now I want to configure an all in one DC server, with dhcp, dns, samba (ad replacement) and for it to be a router between 2 networks - the LAN and our VPN with external office.
With this knowledge I will later add secondary server for all this and place routing role in a 3rd machine, but for now and since I don't really have a test server I'm doing this in my desktop (ubuntu) with virtualbox.
As soon as I solve and understand this problem I'll move to SAMBA.

My problem:
On the windows machine (client) I can resolve names and nslookup (except for one, more info bellow) but cannot open sites on the browser.

What I have:
- 1 VM (vbox 5) with ubuntu server (dc01) with isc-dhcp-server, bind9, ssh and 2 NICs (1 internal 10.1.3.200 and 1 external 10.201.31.3 (gateway is .254));
- 1 VM (vbox 5) with Windows XP for client simulation with 1 NIC (internal dhcp);

What I did...
On Ubuntu server:
- installed it, updated it;
- installed ssh (for remote access) but did not secure it, will need help on this too;
- configured network at /etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback

# Rede Interna
auto eth0
iface eth0 inet static
address 10.1.3.200
netmask 255.255.255.0
network 10.1.3.0
broadcast 10.1.3.255
# gateway will be given by dhcp from eth1
dns-nameservers 10.1.3.200
dns-search domain.pt

# Rede Externa
auto eth1
iface eth1 inet dhcp

```

- installed dhcp
changed /etc/default/ics-dhcp-server to set the server to use eth0 (the internal); 
changed /etc/hosts by adding "10.1.3.200      dc01.domain.pt dc01" to hosts;"
changed /etc/dhcp/dhcpd.conf
```

#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "domain.pt";
option domain-name-servers dc01.domain.pt;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.2# gateway 10.201.31.25455.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}
# A slightly different configuration for an internal subnet.
subnet 10.1.3.0 netmask 255.255.255.0 {
range 10.1.3.1 10.1.3.199;
option domain-name-servers dc01.domain.pt;
option domain-name "domain.pt";
option routers 10.1.3.200;
option broadcast-address 10.1.3.255;
default-lease-time 600;
max-lease-time 7200;
}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}
# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

```

- installed bind9
configured zones at /etc/bind/named.conf.local
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

// Zona DNS
zone "domain.pt" {
        type master;
        file "/etc/bind/db.domain.pt";
        };

// Zona Reverse DNS
zone "3.1.10.in-addr.arpa" {
        type master;
        file "/etc/bind/db.10";
        };
zone "61.26.22.195.in-addr.arpa" {
        type master;
        file "/etc/bind/db.www";
        };

```
Configured forwarders at /etc/bind/named.conf.options
```

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

        forwarders {
                10.1.3.200;
                8.8.8.8;
        };

        //========================================================================
        // If BIND logs error messages about the root key being expired,
        // you will need to update your keys.  See https://www.isc.org/bind-keys
        //========================================================================
        dnssec-validation auto;

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```
configured zone files:
db.10
```

$TTL    604800
@       IN      SOA     dc01.domain.pt. root.domain.pt. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
        IN      NS      dc01.
200     IN      PTR     dc01.domain.pt.
;@      IN      NS      localhost.
;1.0.0  IN      PTR     localhost.

```
db.domain.pt
```

$TTL    604800
@       IN      SOA     dc01.domain.pt. root.domain.pt. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
domain.pt.         IN      NS      dc01.domain.pt.
domain.pt.         IN      A       10.1.3.200
;@      IN      A       127.0.0.1
;@      IN      AAAA    ::1
dc01    IN      A       10.1.3.200
www     IN      A       195.22.26.61

```
db.www (this one I&#8217;m definitely unsure)
```

$TTL    604800
@       IN      SOA     www.domain.pt. (
                              1         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
195.22.26.61    IN      PTR     www.
;@      IN      NS      localhost.
;1.0.0  IN      PTR     localhost.

```

- my /etc/resolv.conf is generated like this:
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 10.1.3.200
nameserver 62.28.116.41
nameserver 62.28.40.173
search domain.pt

```

On the Windows XP client:
- ...well nothing, just installed and let it catch network info by DHCP.

My suspects:
I believe it might be something related to routing between the 2 NICs on the server.

Thanks in advance.

Best regards,
Manuel Borges

---

### Post by darkod on 2015-10-06
I don't think you can control a public ip reverse zone like you are trying to. Besides, the reverse lookup is not very important. Is it important to you?
If you have bought hosting for the website you can try the provider control panel if it offers reverse dns creation, or ask them to do it. Otherwise you can't control that zone yourself.

For your server/machine to do routing, you need two things apart from two NICs.
1. In /etc/sysctl.conf you need to uncomment the entry for ipv4.net.ip_forward or something like that. It should have value of 1 and no # character in front. Save and close the file. Reboot the vm.

2. You need basiciptables rule to masquerade/nat the traffic. Try testing with something like this:
```
sudo iptables -t nat -A POSTROUTING -o eth1 -s 10.1.3.0/24 -j MASQUERADE
```

Does that give internet to the windows client?

If it does, you will need to make that iptables rule permanent because like this it gets deleted on reboot. We can discuss that later.

---

### Post by SeijiSensei on 2015-10-06
Only the ISP can control reverse lookups.  Moreover I don't know what's wrong with Windows, but that IP has a valid PTR record:
```

$ host 195.22.26.61
61.26.22.195.in-addr.arpa domain name pointer mail.rpa.com.pt.

```
If, as I suspect, your website is hosted on this machine, there is nothing you can do to change that mapping to point to your website's domain name rather than mail.rpa.com.pt.

---

### Post by mborges on 2015-10-06
Hello darkod, thanks for your help.

I removed the zone and file for reverse lookup for www, and yes I don't really need it. :-)

I changed the sysctl.conf file and ran the iptables command and now I have internet on the client.

Three things I would like your help/suggestion with:
1. Do I need to change anything to secure the ssh access to the machine?
2. any good book/article/faq on iptables you suggest
3. any good book/article/faq on high availability (redundant servers for dns, dhcp, samba, nic teaming, etc)

Thanks again.

Best regards,
Manuel Borges

---

### Post by mborges on 2015-10-06
Hello SeijiSensei, thanks for your help.

That response from 195.22.26.61 is completely wrong because I dont' recognize mail.rpa.com.pt and it should be [www.domain.pt](www.domain.pt), but its not that important.
I've been in this company for almost 15 years but only now am taking over the IT department, and am finding a lot of weird stuff and since Windows 2003 server is our most recent and in need of change I'm doing trials to determine if everything will work fine with Linux servers. So far so good but I've only moved the web server (apache, php and mysql), and the only problem I had was the fact that Linux is case sensitive, but was easy to clean the code. :-)

Thanks.
Best regards,
Manuel Borges

---

### Post by darkod on 2015-10-06
First lets make the iptables permanent. The most common way is to create a file, for example /etc/iptables.rules with content:
```
*nat

:POSTROUTING ACCEPT [0:0]

-A POSTROUTING -o eth1 -s 10.1.3.0/24 -j MASQUERADE

COMMIT
```

That is giving you the basic rule for nat/masquerade. To load this file on each boot, in the /etc/network/interfaces file, in the eth0 definition after dns-search add this line:
```
post-up iptables-restore < /etc/iptables.rules
```

That will load the file on each interface start / each boot.

As for documentation, I really don't have much at hand. The ubuntu server guide is a good place to start: [https://help.ubuntu.com/lts/serverguide/index.html](https://help.ubuntu.com/lts/serverguide/index.html)

For iptables and clustering there is really loads of resources around. Just make sure to check dates, and use tutorials that are recent, not from decade ago. :)

For ssh I also don't have any special hardening tutorials. In fact, if you put your machine(s) behind the ISP / office main router, the router does the firewall protection. So you can run the ubuntu box even without a firewall. It will all depend on your network configuration. Usually the machines behind a main firewall/router have no need of special protection.

---

### Post by mborges on 2015-10-07
Hi darkod.

Thanks again for your valuable help.

I've created the iptables file and made the changes to interfaces file and its now working after a reboot.

I'll read that guide from ubuntu server. Thanks.

I'll now move onto SAMBA.

Best regards,
Manuel Borges

---

### Post by SeijiSensei on 2015-10-07
> **mborges said:**
> That response from 195.22.26.61 is completely wrong because I dont' recognize mail.rpa.com.pt and it should be [www.domain.pt](www.domain.pt), but its not that important.
It may be "wrong," but it is the PTR record in your provider's database.  You'll need to ask them to change it to [www.domain.pt](www.domain.pt).

It will matter if you ever intend to send mail from that address.  Many mail servers treat non-matching forward and reverse DNS entries as evidence of spamming.

---

