---
title: "Problem updating DNS with DHCP."
date: 2008-08-12
forum: Server Platforms
---

### Post by baldychap on 2008-08-12
Hello All, 

I have search the 'net far and wide to find the 'right' way to configure a DHCP and DNS server (using dhcp3 and bind9) I've got the servers working, to a degree, but cannot get the dhcp server to update the dns with details of new clients. 

I have used the very helpful pdf at [http://www.realmtech.net/documents/DynamicDNS.pdf](http://www.realmtech.net/documents/DynamicDNS.pdf) and also some information from [http://ubuntuforums.org/showthread.php?t=267974](http://ubuntuforums.org/showthread.php?t=267974) to get where I am today and my named.conf.options is:- 

```
include "/etc/bind/rndc.key";
options {
  directory "/var/cache/bind";
  forwarders {
	212.159.13.49;
        212.159.13.50;
  };
  auth-nxdomain no;
};
controls {
  inet 127.0.0.1 allow { localhost; } keys { "rndc-key"; };
};
zone "example.com" {
  type master;
  file "/etc/bind/zones/example.com.db";
  allow-update { key "rndc-key"; };
};
zone "1.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
  allow-update { key "rndc-key"; };
};
```

and my dhcpd.conf is:-

```
server-identifier 192.168.1.3;
authoritative;
ddns-domainname "example.com";
ddns-rev-domainname "rev.1.168.192.in-addr.arpa";
ddns-update-style interim;
include "/etc/dhcp3/rndc.key";
zone example.com. {
  primary 192.168.1.0;
  key rndc-key;
}
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.30 192.168.1.99;
  option subnet-mask 255.255.255.0;
  option broadcast-address 192.168.1.255;
  option domain-name "example.com";
  one-lease-per-client on;
  default-lease-time 604800;
  max-lease-time 604800;
  # Gateways and DNS servers
  option routers 192.168.1.1;
  option domain-name-servers 192.168.1.3;
}
```

The problem can be seen in the daemon.log when a client requests a DHCP address from the server:-

```
Aug 13 00:03:53 nameserver named[1794]: starting BIND 9.4.1-P1.1 -u bind
Aug 13 00:03:53 nameserver named[1794]: found 1 CPU, using 1 worker thread
Aug 13 00:03:53 nameserver named[1794]: loading configuration from '/etc/bind/named.conf'
Aug 13 00:03:53 nameserver named[1794]: listening on IPv4 interface lo, 127.0.0.1#53
Aug 13 00:03:53 nameserver named[1794]: listening on IPv4 interface eth0, 192.168.1.3#53
Aug 13 00:03:53 nameserver named[1794]: listening on IPv4 interface vmnet8, 192.168.65.1#53
Aug 13 00:03:53 nameserver named[1794]: listening on IPv4 interface vmnet1, 192.168.81.1#53
Aug 13 00:03:53 nameserver named[1794]: automatic empty zone: 254.169.IN-ADDR.ARPA
Aug 13 00:03:53 nameserver named[1794]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Aug 13 00:03:53 nameserver named[1794]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Aug 13 00:03:53 nameserver named[1794]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Aug 13 00:03:53 nameserver named[1794]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Aug 13 00:03:53 nameserver named[1794]: automatic empty zone: D.F.IP6.ARPA
Aug 13 00:03:53 nameserver named[1794]: automatic empty zone: 8.E.F.IP6.ARPA
Aug 13 00:03:53 nameserver named[1794]: automatic empty zone: 9.E.F.IP6.ARPA
Aug 13 00:03:53 nameserver named[1794]: automatic empty zone: A.E.F.IP6.ARPA
Aug 13 00:03:53 nameserver named[1794]: automatic empty zone: B.E.F.IP6.ARPA
Aug 13 00:03:53 nameserver named[1794]: command channel listening on 127.0.0.1#953
Aug 13 00:03:53 nameserver named[1794]: zone 0.in-addr.arpa/IN: loaded serial 1
Aug 13 00:03:53 nameserver named[1794]: zone 127.in-addr.arpa/IN: loaded serial 1
Aug 13 00:03:53 nameserver named[1794]: /etc/bind/zones/rev.1.168.192.in-addr.arpa:1: no TTL specified; using SOA MINTTL instead
Aug 13 00:03:53 nameserver named[1794]: zone 1.168.192.in-addr.arpa/IN: loaded serial 2006081401
Aug 13 00:03:53 nameserver named[1794]: zone 255.in-addr.arpa/IN: loaded serial 1
Aug 13 00:03:53 nameserver named[1794]: zone localhost/IN: loaded serial 1
Aug 13 00:03:53 nameserver named[1794]: /etc/bind/zones/example.com.db:1: no TTL specified; using SOA MINTTL instead
Aug 13 00:03:53 nameserver named[1794]: zone example.com/IN: loaded serial 2006081402
Aug 13 00:03:53 nameserver named[1794]: running
Aug 13 00:04:13 nameserver dhcpd: DHCPRELEASE of 192.168.1.66 from 00:08:74:9d:ec:d5 (clienthostname) via eth0 (found)
Aug 13 00:04:14 nameserver dhcpd: DHCPDISCOVER from 00:08:74:9d:ec:d5 via eth0
Aug 13 00:04:15 nameserver dhcpd: DHCPOFFER on 192.168.1.66 to 00:08:74:9d:ec:d5 (clienthostname) via eth0
Aug 13 00:04:15 nameserver dhcpd: Unable to add forward map from clienthostname.example.com to 192.168.1.66: connection refused
Aug 13 00:04:15 nameserver dhcpd: DHCPREQUEST for 192.168.1.66 (192.168.1.3) from 00:08:74:9d:ec:d5 (clienthostname) via eth0
Aug 13 00:04:15 nameserver dhcpd: DHCPACK on 192.168.1.66 to 00:08:74:9d:ec:d5 (clienthostname) via eth0
```

The problem being "nameserver dhcpd: Unable to add forward map from clienthostname.example.com to 192.168.1.66: connection refused". 

Does anyone know why permission is being refused? I've made sure that the bind group has read/write access on the /etc/bind directory and that the dchpd group has read/write access on the /etc/dhcp3 directory. I presume it's a problem with the keys, but I can't see where it is!

Any help would be gratefully received. I've searched the web/forums for advice and have not found anything, so apologies if this has been answered elsewhere :-)

Kind Regards,

Baldychap.

---

### Post by simonbaev on 2010-01-08
Hey Baldychap,

I guess I know the reason for "connection refused" but it doesn't help in the way to turn the thing out to work :) 

In the dhcpd.conf you probably need to change "primary 192.168.1.0;" to "primary 192.168.1.1;" (or whatever is going to be your NS) since x.x.x.0 IP address is reserved and can't be used for regular hosts. 

Now I'm struggling as having different error message: "dhcpd: Unable to add forward map from wxp1.dyn.aliens to 192.168.2.111: timed out" and I have no idea how to resolve the issue. 

I just found your post, tried your configs, compared to mine ones...

If you solved the problem, could you please share the steps? Thanks.

---

### Post by BkkBonanza on 2010-01-09
I don't have an answer to your question here. I just wanted to throw something out here for when you get fed up with bind. If you're not running a big organization with lots of complex sites in your lan then you may find it a lot easier and less resource heavy to just use dnsmasq. It handles both dhcp and dns together in one lightweight package and is very easy to setup.

[http://freshmeat.net/projects/dnsmasq/](http://freshmeat.net/projects/dnsmasq/)

[http://www.linux.com/archive/articles/149040](http://www.linux.com/archive/articles/149040)

This is what is used in common router firmware upgrades like DD-WRT, Tomato etc. Works very well as a gateway. Does not serve DNS publicly though, which is usually fine for networks.

---

### Post by noway2 on 2010-01-09
Check this link:[http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/](http://lani78.wordpress.com/2008/08/12/dhcp-server-update-dns-records/)

I used it within the first few hours of my initial server install (read I didn't know squat yet) and successfully configured DHCP and BIND so that it automatically adds clients and identifies them by name.

---

