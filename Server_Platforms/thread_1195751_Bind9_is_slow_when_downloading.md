---
title: "Bind9 is slow when downloading"
date: 2009-06-24
forum: Server Platforms
---

### Post by Serangan on 2009-06-24
Hi, 

My problem is this, if I start to download any file, bind9 slows down, alot.

i.e.  I start downloading a test file, and ping google. each response takes 3 - 4 seconds. (this is behind bind9 and squid )

if i bypass bind9 (just use my routers address) and do the exact same thing. ping times are 0.3 - 0.5 of a second. (this is using direct connecting to the net - no proxy or bind9)

I am using squid proxy, it works, and is caching sites well. I installed bind9 today, and this has happened. It really slows down the net. Im assuming this isnt right. Also, squid proxy, is configured to using 127.0.0.1 & 192.168.1.250 for dns server.

**named.conf**
```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
	type hint;
	file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
	type master;
	file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
	type master;
	file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
	type master;
	file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
	type master;
	file "/etc/bind/db.255";
};

include "/etc/bind/named.conf.local";

```

**named.conf.options**
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


	auth-nxdomain no;    # conform to RFC1035
	// listen-on-v6 { any; };
forwarders {
	192.231.203.3;
	192.231.203.132;
};
forward first;

allow-query {
192.168.1/24;
127.0.0/24;
};

};


```

**named.conf.local**
```
//
// Do any local configuration here
//
        zone "home.internal" {
             type master;
             file "/etc/bind/db.home.internal";
        };
zone "1.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
};
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

```

---

### Post by Serangan on 2009-06-25
Also, i have 2 nic's, but while i was looking for a solution, I disable on of the nic having net access.

So now, eth0 --> net
eth1 --> internal only

that doesnt mean that its like this;

internet <--> eth0 <--> eth1 <--> client pcs

its done via

router --> switch --> client pc's and server (server just has 2 ip's)

---

### Post by windependence on 2009-06-25
You don't have to set up a DNS server to surf the net. In fact, you don't need one to serve websites either. Why are you running Bind?

Edit your /etc/resolv.conf like this:

```
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 4.2.2.2
```

Restart the network and try it again. You can shut down Bind, you don't need it.

-Tim

---

### Post by Serangan on 2009-06-25
well, i know i dont need bind.

Im trying to use it, because I want to have urls and not ip address's.

ie. with bind, i can have [www.home.internal](www.home.internal), proxy.home.internal, gateway.home.interal etc...

I know i dont need this, but im curious about how it works / setting up.

---

### Post by windependence on 2009-06-25
I understand you wanting to know how to set it up, but to be able to resolve names on a small network, you can also use the /etc/hosts file on each machine, just FYI. :-)

-Tim

---

### Post by Serangan on 2009-06-26
yeah, i was going to use that... but i really couldnt be bothered :P

but im now thinking it isnt a bind issue... cause its still happening. using the router as dns it still really slow with pings. slower than using on of the other pcs. so yeah. odd

---

### Post by windependence on 2009-06-27
I don't think you quite understand how DNS works. First off, use some public DNS servers in your resolv.conf file instead of relying on your router for DNS. 

As for the hosts file, just use the same hosts file for all your machines. You could even write a script to deploy it on all your machines. It's certainly easier than setting up and maintaining bind.

-Tim

---

### Post by Serangan on 2009-06-27
mk, well, my router gets its dns servers from my isp...


There shouldn't be anything wrong with using my router as my dns server address. I could use my isp's dns address' but they say that this isn't necessary due to the router having it already.

Also, its fixed now. i disabled both nics having internet and it just worked.

---

