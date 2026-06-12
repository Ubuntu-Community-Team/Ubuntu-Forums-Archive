---
title: "Problems setting up a dns server"
date: 2006-04-13
forum: Server Platforms
---

### Post by jazee on 2006-04-13
Hi

I am trying to set up a dns server. I am having problems with the names resolving. I have registerd the domain with godaddy and have created the 2 name servers with them ns1.nerdynick.net and ns2.nerdynick.net both point to the same ip address. (I know not good. But I only have 1 server and DNS requires 2 name servers.) I have also set with godaddy the main domain's (nerdynick.net) the 2 name servers for it as ns1.nerdynick.net and ns2.nerdynick.net. Now on the server using webmin I have created a master record for nerdynick.net with 2 A records for the 2 name servers by ipaddress and 1 A record for the default(nerdynick.net) I have also created 2 NS records pointing to the 2 name servers by domian address. I have also forwarded port 53 to the server threw the router/firewall.

Now the problem is when I try to go to nerdynick.net it doesn't resolve the ip address to my server. I have tryed nslookup's and dig's on both nerdynick.net and ns1-n2.nerdynick.net and nothing returns back for an answer.

Any ideas why this wont resolve correctly. 

I will post the named.conf and the zone file in a bit. Have to switch to the server.

---

### Post by jazee on 2006-04-13
Named.conf
```

options {
	directory "/etc";
	pid-file "/var/run/named.pid";
	};

zone "." {
	type hint;
	file "/etc/db.cache";
	};
zone "nerdynick.net" {
	type master;
	file "/etc/nerdynick.net.hosts";
	};

```

Nerdynick.net.hosts
```

$ttl 38400
nerdynick.net.	IN	SOA	localhost.localdomain. nerdynick.gmail.com. (
			1143004589
			10800
			3600
			604800
			38400 )
nerdynick.net.	IN	A	192.168.1.10
nerdynick.net.	IN	A	71.196.149.244
ns1.nerdynick.net.	IN	NS	ns1.nerdynick.net.
ns2.nerdynick.net.	IN	NS	ns2.nerdynick.net.
ns1.nerdynick.net.	IN	A	71.196.149.244
ns2.nerdynick.net.	IN	A	71.196.149.244

```

---

### Post by fdoving on 2006-04-14
[QUOTE=jazee]Named.conf
```

options {
	directory "/etc";
	pid-file "/var/run/named.pid";
	};

zone "." {
	type hint;
	file "/etc/db.cache";
	};
zone "nerdynick.net" {
	type master;
	file "/etc/nerdynick.net.hosts";
	};

``` 
[/QUOTE]
Looks OK.

Nerdynick.net.hosts
```

$ttl 38400
nerdynick.net.	IN	SOA	_ns1.nerynick.net_ nerdynick.gmail.com. (
			1143004589
			10800
			3600
			604800
			38400 )
; The two next lines sets up load balancing for nerdynick.net to the two ip's.
; I doubt that's what you want. I commented out the LAN address.
; nerdynick.net.	IN	A	192.168.1.10
nerdynick.net.	IN	A	71.196.149.244

; This is wrong. This makes NS records for ns1.nerdynick.net 
; and ns2.nerdynick.net. You want NS records for nerdynick.net.
; ns1.nerdynick.net.	IN	NS	ns1.nerdynick.net.
; ns2.nerdynick.net.	IN	NS	ns2.nerdynick.net.
; This is what you want.
nerdynick.net.        IN NS ns1.nerdynick.net.
nerdynick.net.        IN NS ns2.nerdynick.net.

; This is correct. BUT you cannot have two nameservers on the same IP. 
; I suggest using a free secondary nameserver service. Like afraid.org or twisted4life.com. 
ns1.nerdynick.net.	IN	A	71.196.149.244
; ns2.nerdynick.net.	IN	A	71.196.149.244

```



I hope the feedback is understandable and useful. 

- Frode

---

### Post by jazee on 2006-04-14
Ya that actualy all makes sences. Thanks I will try it out and see what happens.

---

### Post by jazee on 2006-04-14
should the master zone record stille be named nerdynick.net or should it change to ns1.nerdynick.net

---

### Post by fdoving on 2006-04-15
nerdynick.net

---

### Post by LordHunter317 on 2006-04-15
[quote=jazee]I am trying to set up a dns server. I am having problems with the names resolving. I have registerd the domain with godaddy and have created the 2 name servers with them ns1.nerdynick.net and ns2.nerdynick.net both point to the same ip address. (I know not good. But I only have 1 server and DNS requires 2 name servers.)[/quote]Actually, it doesn't. 

Edit:removed insult

---

### Post by jazee on 2006-04-15
Just trying to learn man sorry.

---

### Post by LordHunter317 on 2006-04-15
Well, wanting to learn is fine.  But Internet-facing DNS isn't the place to do it, frankly, even for a personal site.  Even if it were, your DNS is a prerequisite for your site to work, and you can get people who host DNS on better connections and with more experience for free.  You'd be silly not to take advantage of it, whenever you can.

It's easy to setup a DNS server for your house or internal machines, and doesn't have negative consequences to the rest of the world if you get it wrong, and still offers most of the same learning opportunities.

---

### Post by jazee on 2006-04-16
Thats the thing I have set up internal DNS just fine. Thats what the server was doing in the first place. And I have and still do use afraid.org for free DNS hosting for other sites. I just have never set up a true Name Server that was open to the public. So I thought I would give it a try and see what I could do, and how hard it was to do. Its one thing to get internal made up domains and shit to work and resolve but to throw in a real domain that could be used by the outside world is a diffrent story.

---

### Post by fdoving on 2006-04-16
Go for it. If you continue to use others services for all your needs you'll never learn anything.

- Frode

---

