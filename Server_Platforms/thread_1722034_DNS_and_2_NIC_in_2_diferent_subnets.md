---
title: "DNS and 2 NIC in 2 diferent subnets"
date: 2011-04-05
forum: Server Platforms
---

### Post by yield_ on 2011-04-05
Hi There,

I have 1 DNS (bind) server running on Ubuntu 10.04.
The server work fine, I am able to use it as a DNS server... Everything is FINE !

However, as soon as I enable my second NIC, the DNS does not resolv anything anymore.


Here are the NIC config :
The first is for server side, the second one is for Workstation one...

a> uto eth2
iface eth2 inet static
	address 10.53.82.51
	netmask 255.255.255.0
	network 10.53.82.0
	broadcast 10.53.82.255
	gateway 10.53.82.253
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 10.53.82.51
	dns-search mydomain.com

auto eth3
iface eth3 inet static
	address 10.54.193.64
	netmask 255.255.255.0
	network 10.54.193.0
	broadcast 10.54.193.255
	gateway 10.54.193.254
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 10.54.193.64
	dns-search mydomain.com


Here is my named.conf.options :
> 
options {
	directory "/var/cache/bind";

	// If there is a firewall between you and nameservers you want
	// to talk to, you may need to fix the firewall to allow multiple
	// ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

	// If your ISP provided one or more IP addresses for stable 
	// nameservers, you probably want to use them as forwarders.  
	// Uncomment the following block, and insert the addresses replacing 
	// the all-0's placeholder.

	forwarders {
		8.8.8.8;
		8.8.4.4;
	 };

	auth-nxdomain no;    # conform to RFC1035
	listen-on { 10.53.82.51; 10.54.193.64; };
	allow-recursion { 10.53.82.0/8; 10.54.193.0/8;  172.16.0.0/12; };
};

Then, if I go back to only the first NIC to be UP, it work's back again.......
Please help


Thanks !

---

### Post by terazen on 2011-04-05
Connect both nics and try the "route" command.  Then make sure you can ping google's dns.  It might be a networking problem that has nothing to do with bind.  Also, you may want to remove the gateway from the 2nd nic and add any internal routes manually.

---

