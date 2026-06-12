---
title: "Having issues setting up DNS"
date: 2012-07-20
forum: Server Platforms
---

### Post by styphon on 2012-07-20
I'm fairly new to Linux (played with Ubuntu desktop somewhat, this is my first server install). I work as a web developer and I'm trying to set up a local development server for me and two other guys in the office to work off of.

I installed LAMP and Samba during the initial installation process and have managed to get everything working fine if we use windows HOST file to point the different domain names to the server, however having followed several tutorials (all saying roughly the same thing) to set up bind9 and then set my main domain as fluid.dev and then fluidcms.dev and fluideshop.dev as CNAME records of fluid.dev. I then have then set the windows machines primary DNS to point to the ubuntu server, however they cannot resolve any of those three names to IP addresses.

I know everything else is set up correctly because if I set the IP address using the HOSTS file on the windows machines it connects through to the websites correctly. What do I need to check on the DNS server? I don't know the troubleshooting process.

---

### Post by sandyd on 2012-07-20
> **styphon said:**
> I'm fairly new to Linux (played with Ubuntu desktop somewhat, this is my first server install). I work as a web developer and I'm trying to set up a local development server for me and two other guys in the office to work off of.

I installed LAMP and Samba during the initial installation process and have managed to get everything working fine if we use windows HOST file to point the different domain names to the server, however having followed several tutorials (all saying roughly the same thing) to set up bind9 and then set my main domain as fluid.dev and then fluidcms.dev and fluideshop.dev as CNAME records of fluid.dev. I then have then set the windows machines primary DNS to point to the ubuntu server, however they cannot resolve any of those three names to IP addresses.

I know everything else is set up correctly because if I set the IP address using the HOSTS file on the windows machines it connects through to the websites correctly. What do I need to check on the DNS server? I don't know the troubleshooting process.
Can you post the output of
```

nslookup fluid.dev

```
on the window machine?

---

### Post by styphon on 2012-07-20
I've finished work for the weekend now. I'll post the results on Monday.

---

### Post by styphon on 2012-07-23
Morning, this is the result from one of the windows machines.
C:\Users\Fluid>nslookup fluid.dev
Server:  UnKnown
Address:  192.168.254.60

*** UnKnown can't find fluid.dev: Server failed

---

### Post by styphon on 2012-07-24
Can nobody help me get DNS working?

---

### Post by tenmoi on 2012-07-24
> **styphon said:**
> Can nobody help me get DNS working?

No one can help because your problem is too big.There are so many issues that prevent your dns server from running. Here are some books for serious work: Pro DNS and BIND, DNS and BIND. Only specific issues can be answered here, I think.

---

### Post by styphon on 2012-07-24
That's what I was afraid of :(. I guess we'll just have to live with HOST files. Thanks anyway.

---

### Post by tenmoi on 2012-07-24
> **styphon said:**
> That's what I was afraid of :(. I guess we'll just have to live with HOST files. Thanks anyway.

Wait! There's these two useful utilities to help you: name-checkconf to check your dns conf file and name-checkzone to check your zone files for any errors.

Try them and google solutions to the errors before getting help here.

---

### Post by styphon on 2012-07-24
OK, I made some progress. It wasn't opening the file, I'd not referred to it in the correct place. I cleared my HOST file and flushed my DNS on the windows machine. Now when I do nslookup from the windows machine I get the correct IP and I can also ping it successfully.

However, when I browse to it I get website unavailable. When I was using the HOST file and browsed to it it worked perfectly fine. Why would this change when using DNS?

---

### Post by styphon on 2012-07-24
Done some testing, tried googling a few things and still cannot get this to work. The domain is configured correctly as far as I can see. I can type the domain address in on the local machine and it will bring up the website perfectly fine.

On the windows machine I can use nslookup and ping and it resolves the IP address correctly, however when I use any browser to try an reach the site I get website unavailable and OpenDNS kicks in (my secondary DNS server). If I manually link the IP address to the website address using the HOST file and then browse to the website it works perfectly fine.

Does anyone know what could cause this, or have any ideas on how to track down the problem?

---

### Post by Doug S on 2012-07-24
It would help us if you would post your bind config files.
Myself, I have no clue what is wrong from the description.
I also recommend using the [ubuntu server guide]("https://help.ubuntu.com/12.04/serverguide/index.html") ([pdf]("https://help.ubuntu.com/12.04/serverguide/serverguide.pdf")). I have found the DNS chapter to be pretty good. It was the only reference I used to setup my internal DNS.

---

### Post by styphon on 2012-07-24
This is named.conf.local:
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "fluid.dev" {
	type master;
        file "/etc/bind/db.fluid.dev";
};
zone "pathways-plus.dev" {
	type master;
	file "/etc/bind/db.pathways-plus.dev";
};
zone "254.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/rev.db.192";
};
```

db.fluid.dev:
```
; BIND data file for fluid.dev
; 
$ORIGIN fluid.dev.
$TTL 	604800
@ 	IN 	SOA 	ns1.fluid.dev. admin.fluid.dev. (
				2012072404 ; Serial
				28800 ; Refresh 
				3600 ; Retry 
				604800 ; Expire 
				38400 ) ; Negative Cache TTL 
;  

		IN	NS	ns1.fluid.dev.
		IN	MX 10	mail.fluid.dev.

localhost	IN	A	127.0.0.1
fluid.dev. 	IN	A	192.168.254.60
ns1		IN	A	192.168.254.60

www		IN	A	192.168.254.60
ftp		IN	A	192.168.254.60
mail		IN	A	192.168.254.60
```

db.pathways-plus.dev:
```
; BIND data file for pathways-plus.dev.
; 
$ORIGIN pathways-plus.dev.
$TTL 	604800
@ 	IN 	SOA 	ns1.pathways-plus.dev. admin.pathways-plus.dev. (
				2012072402 ; Serial
				28800 ; Refresh 
				3600 ; Retry 
				604800 ; Expire 
				38400 ) ; Negative Cache TTL 
;  

			IN	NS	ns1.pathways-plus.dev.
			IN	MX 10	mail.pathways-plus.dev.

localhost		IN	A	127.0.0.1
pathways-plus.dev.	IN	A	192.168.254.60
ns1			IN	A	192.168.254.60

www			IN	A	192.168.254.60
ftp			IN	A	192.168.254.60
mail			IN	A	192.168.254.60
```

rev.db.192:
```
;
; BIND reverse data file for local 192.168.254.XXX net
;
$TTL    604800
@       IN      SOA     ns1.fluid.dev. admin.fluid.dev. (
                     2012072402         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.
60      IN      PTR     ns1.fluid.dev.
```

fluid.dev points to the main apache folder and I consider it the "main" website. Pathways-plus.dev is the first website I have set up as an extra virtual host to work on.

---

### Post by Doug S on 2012-07-24
For db.fliud.dev, try this (I don't know why it is not formatting properly, tabs seems to have changed to spaces):```
; BIND data file for fluid.dev
; 
$TTL  604800
@  IN  SOA  fluid.dev. admin.fluid.dev. (
    2012072404 ; Serial
    28800 ; Refresh 
    3600 ; Retry 
    604800 ; Expire 
    38400 ) ; Negative Cache TTL 
;  
@  IN NS ns1.fluid.dev.
  IN MX 10 mail.fluid.dev.
ns1  IN A 192.168.254.60
www  IN A 192.168.254.60
ftp  IN A 192.168.254.60
mail  IN A 192.168.254.60
```Similarly for the other one, if this helps.

---

### Post by tenmoi on 2012-07-24
> **styphon said:**
> This is named.conf.local:
```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "fluid.dev" {
	type master;
        file "/etc/bind/db.fluid.dev";
};
zone "pathways-plus.dev" {
	type master;
	file "/etc/bind/db.pathways-plus.dev";
};
zone "254.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/rev.db.192";
};
```

db.fluid.dev:
```
; BIND data file for fluid.dev
; 
$ORIGIN fluid.dev.
$TTL 	604800
@ 	IN 	SOA 	ns1.fluid.dev. admin.fluid.dev. (
				2012072404 ; Serial
				28800 ; Refresh 
				3600 ; Retry 
				604800 ; Expire 
				38400 ) ; Negative Cache TTL 
;  

		IN	NS	ns1.fluid.dev.
		IN	MX 10	mail.fluid.dev.

localhost	IN	A	127.0.0.1
fluid.dev. 	IN	A	192.168.254.60
ns1		IN	A	192.168.254.60

www		IN	A	192.168.254.60
ftp		IN	A	192.168.254.60
mail		IN	A	192.168.254.60
```

db.pathways-plus.dev:
```
; BIND data file for pathways-plus.dev.
; 
$ORIGIN pathways-plus.dev.
$TTL 	604800
@ 	IN 	SOA 	ns1.pathways-plus.dev. admin.pathways-plus.dev. (
				2012072402 ; Serial
				28800 ; Refresh 
				3600 ; Retry 
				604800 ; Expire 
				38400 ) ; Negative Cache TTL 
;  

			IN	NS	ns1.pathways-plus.dev.
			IN	MX 10	mail.pathways-plus.dev.

localhost		IN	A	127.0.0.1
pathways-plus.dev.	IN	A	192.168.254.60
ns1			IN	A	192.168.254.60

www			IN	A	192.168.254.60
ftp			IN	A	192.168.254.60
mail			IN	A	192.168.254.60
```

rev.db.192:
```
;
; BIND reverse data file for local 192.168.254.XXX net
;
$TTL    604800
@       IN      SOA     ns1.fluid.dev. admin.fluid.dev. (
                     2012072402         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns1.
60      IN      PTR     ns1.fluid.dev.
```

fluid.dev points to the main apache folder and I consider it the "main" website. Pathways-plus.dev is the first website I have set up as an extra virtual host to work on.

Both ns1.fluid.dev and ns1.pathways-plus.dev use ONE IP address. What are you trying to achieve? Redundancy? If you want redundancy, set up another dns server and add an entry in ns1.fluid.dev to point to it. 
Leave out the localhost. It's already handled when you install bind9. That's the way it is with ubuntu.

In your rev.db.192. It should be
@ IN NS ns1.fluid.dev.

Tackle one target at a time. Leave out the pathways-plus zone and make sure that your fluid.dev zone is running fine before you add more zones.

Please run the following commands on your DNS server machine and paste the results here: 
cat /etc/hosts and /etc/resolv.conf

---

### Post by styphon on 2012-07-25
Thanks guys for the help.

tenmoi, I've got both pointing to the same IP because it's a LAMP server with virtual hosts, this is our in-house development server. Eventually I will have hundreds of sites each with a DNS record, all pointing to this server.

I have commented out the pathways-plus zone from named.conf.local for now until we can get fluid.dev working. I changed the record to look as above, both for the forward and reverse lookup files.

If I browse to fluid.dev on the ubuntu server it works perfectly fine. However still no joy on the windows machine.

nslookup from Win7 machine:
```
C:\Users\Fluid>nslookup fluid.dev
Server:  ns1.fluid.dev
Address:  192.168.254.60

Name:    fluid.dev
```

ping fluid.dev comes up with could not find host, however ns1.fluid.dev comes up with the correct IP now. I had to change my secondary DNS from OpenDNS to my router to get this though (seems OpenDNS was interfering).

Browsing to ns1.fluid.dev now works, as does [www.fluid.dev](www.fluid.dev) but still not fluid.dev on it's own, what's missing? I tried adding a * A record but that didn't work.

EDIT: I'm being slow this morning. For some reason I forgot how to add a blank A record. I've got it working now, and the pathways-plus.dev domain. Thank you all for your help on this :).

---

