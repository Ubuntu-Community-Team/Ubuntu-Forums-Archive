---
title: "Cannot access web server from the Internet"
date: 2009-05-16
forum: Server Platforms
---

### Post by Face_Man on 2009-05-16
Hello All, 
I really don’t know where to start however I am trying to host my domain on my server.  Therefore, I register a domain with godaddy.com and add 2 host name dns1.mydomain.com and ns1.mydomain.com and set the IP address to my static IP Address. Also in godaddy.com I set the domain Name Server to dns1.mydomain.com and ns1.mydomain.com. 

 I install Ubuntu 9.04 server with 2 Ethernet and DNS server.


Configuration:

	interfaces:

		auto lo
		iface lo inet loopback

		auto eth0
		iface eth0 inet static
			#IP address is static from ISP 
	        	address         62.xxx.xxxx.xxx
        		netmask         255.255.255.252
       			gateway       	62.xxx.xxx.xxx
        

		auto eth1
		iface eth1 inet static
        		address         10.0.1.1
		        netmask         255.255.255.248
        
===============================================================
	/etc/resolv.conf:

	//ISP dns
 	nameserver xxx.xxx.xxx.xxx
	nameserver xxx.xxx.xxx.xxx

==============================================================

	/etc/bind/named.conf.options:

options {
	directory "/var/cache/bind";
 	forwarders {
		//ISP dns
		xxx.xxx.xxx.xxx;
		xxx.xxx.xxx.xxx;
	};
	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};
==============================================================
	/etc/bind/named.conf.local:

zone "mydomain.com" {
	type master;
        file "/etc/bind/zones/db.mydomain.com";
	
};

zone "0.1.10.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/zones/db.10";

};
===============================================================
	/etc/bind/zones/db.mydomain.com:

;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     dns1.mydomain.com. root.mydomain.com. (
                              6         ; Serial
                           3000       	; Refresh
                           3600         ; Retry
                        2419200         ; Expire
                         3600   )       ; Negative Cache TTL
;
@       IN      NS      dns1.mydomain.com
@       IN      A       127.0.0.1
@       IN      AAAA    ::1
dns1    IN      A       10.0.1.1
iis     IN      A       10.0.1.2
www     IN    	CNAME  	iis
===============================================================
	/etc/bind/zones/db.10:

;
; BIND reverse data file for local loopback interface
;
$TTL	604800
@	IN	SOA	dns1.mydomain.com. root.aldimna.com. (
				5       ; Serial
                             3000	; Refresh
                             3600       ; Retry
                             2419200    ; Expire
                             3600   )   ; Negative Cache TTL
 
;
@	IN	NS	dns1.
10	IN	PTR	dns1.mydomain.com.
==============================================================


The web server is on anthor server(10.0.1.2) in the local network. locally evrey thing is fine however i cannot access the web server from the Internet. 

Any help would be much appreciated.

---

### Post by gobbledigook on 2009-05-17
hi!

i'm no expert but i recently set up a website on my home server, just because i could;) i had a very frustrating time getting it all to work, before i realised a couple of fundamental errors!!

initially when you register the domain with a dns it takes a few hours (in my case a few days) before you can access it locally, there's a technical reason for this, but the way round is to initially use a proxy server to check the site is up and running, something like this works well: [http://anonymouse.org/anonwww.html]("http://anonymouse.org/anonwww.html") another thing is to try with www. and without the www. prefix.

a different issues is some isp's don't like you using port 80? so first check it is forwarded correctly on your router, adn you can test the connectivity by using a port test tool, if your server id headless then a command line browser like lynx is good:) 

usage:
```
lynx www.canyouseeme.org/
```

i use that site because it is simple and loads up with the test 'port' box already highlighted, so all you need to is type your port and press enter:)

if these answers are any help to you, i will be glad.

Dan

---

