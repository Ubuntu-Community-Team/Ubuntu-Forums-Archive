---
title: "[SOLVED] Apache + Domain Name"
date: 2008-01-24
forum: Server Platforms
---

### Post by dethredic on 2008-01-24
Ok, I built my own mini server, and I would like to know how to make my domain work with it.

My domain register, Namecheap allows for nameserver registration. I made 2 nameservers (ns1.mydomain.com and ns2.mydomain.com). I made both these nameserver point to my IP. I then added both those nameservers for my domain. I have waited +24 hours and I still can't access my site via my domain, but I can access it via my IP.

So, I am thinking I need to configure Apache to use my domain name or something. I looked around but could not find anything.

Any ideas?

---

### Post by koenn on 2008-01-24
> I made 2 nameservers (ns1.mydomain.com and ns2.mydomain.com). I made both these nameserver point to my IP.
Do you actually *have* a name server running at that IP address ?

---

### Post by dethredic on 2008-01-24
I don't think so, well I have no idea.

I just installed Webmin if that makes things easier.

How can I do this, if I don't have the name servers running.

---

### Post by MJN on 2008-01-24
Post the domain, otherwise this could be a somewhat protracted resolution process.

Mathew

---

### Post by dethredic on 2008-01-24
my domain is hatchseadgroup.com

---

### Post by MJN on 2008-01-24
It does indeed look like you don't have any nameservers running.

If your ultimate goal is to host a website, as opposed to learning how to host a DNS server, you might want to delegate your DNS to [www.zoneedit.com](www.zoneedit.com) - it's free and works well.

Mathew

---

### Post by dethredic on 2008-01-24
Well

I would like to know how to host a DNS server. I have bind9 installed and somewhat configured. I would like to learn from this experience, so I don't mind taking the harder route.

[This ]("http://www.howtoforge.com/perfect_server_ubuntu7.10_p4")is what I have set up so far.

---

### Post by MJN on 2008-01-24
That's fair enough.

Have you forwarded port 53 (UDP and TCP) from any router to your server?

Someone else will have to ascertain whether the HowTo is correct - I now refuse on principle to read through the so-called 'Perfect Server' HowTo as it's not teaching anyone anything so you'll understand my reluctance to waste my time fixing it! :)

Mathew

---

### Post by dethredic on 2008-01-24
I now have the port forwarded.

My browser doesn't even search for the connection now.

---

### Post by MJN on 2008-01-24
It looks like you're getting somewhere:

```
dig @24.57.219.152 hatchseadgroup.com a

; <<>> DiG 9.3.2 <<>> @24.57.219.152 hatchseadgroup.com a
; (1 server found)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 40482
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;hatchseadgroup.com.            IN      A

;; Query time: 126 msec
;; SERVER: 24.57.219.152#53(24.57.219.152)
;; WHEN: Thu Jan 24 19:51:25 2008
;; MSG SIZE  rcvd: 36

```

So we're now getting response, albeit 'REFUSED'!

Can you post your zone file?

Mathew

---

### Post by dethredic on 2008-01-24
Sorry I don't know the zone file.

How might I access it, so I may share it.

---

### Post by MJN on 2008-01-24
It sounds like that HowTo didn't actually configure zones, but rather just a local DNS server for local clients.

Look round for another HowTo - a DNS/BIND-specific one - as given you want to learn this (and not just copy-and-paste config and zone files from me) this is best served in a structured article rather than a series of posts here. Then you will understand why things are the way they are and you can then tailor things to suit your needs. It's not rocket science so don't be too apprehensive, but there are a number of points that you'll need to learn and the best way is by being walked through it.

Of course, if anyone wants to walk this through here then don't let me stop you!

Mathew

Edit: There's one [here]("https://help.ubuntu.com/community/BIND9ServerHowto") in the Ubuntu community docs which seems to cover most things, and whilst it lacks detail in some areas it does have some links to other technical resources.
Edit 2: If you're serious about learning DNS, [this]("http://www.oreilly.com/catalog/dns5/") is *the* book on the topic.

---

### Post by koenn on 2008-01-24
Teach Yourself Bind in 24 seconds :

to configure bind, you need to
1/ edit bind config file(s). This file tells bind, among other things,  what zone files to use. 
2/  create a text file, a so called "zone file", that maps host names to ip addresses. Bind uses this to translate host names to addresses.

here's an example. [http://users.pandora.be/mydotcom/howto/linuxsbs/dns1.htm](http://users.pandora.be/mydotcom/howto/linuxsbs/dns1.htm)
It's written for a LAN, but the concept applies to any DNS. You could use this example to try and create create a DNS setup that suits your environment.


edit: The Ubuntu DNS howto Mathew mentions, is probably a better choice.

---

### Post by dethredic on 2008-01-24
> **MJN said:**
> It sounds like that HowTo didn't actually configure zones, but rather just a local DNS server for local clients.

Look round for another HowTo - a DNS/BIND-specific one - as given you want to learn this (and not just copy-and-paste config and zone files from me) this is best served in a structured article rather than a series of posts here. Then you will understand why things are the way they are and you can then tailor things to suit your needs. It's not rocket science so don't be too apprehensive, but there are a number of points that you'll need to learn and the best way is by being walked through it.

Of course, if anyone wants to walk this through here then don't let me stop you!

Mathew

**Edit: There's one [here]("https://help.ubuntu.com/community/BIND9ServerHowto") in the Ubuntu community docs which seems to cover most things, and whilst it lacks detail in some areas it does have some links to other technical resources.**
Edit 2: If you're serious about learning DNS, [this]("http://www.oreilly.com/catalog/dns5/") is *the* book on the topic.

That tutorial worked great. I feel like I know so much more. And it is always fun to understand what and why you do things, so some side googleing was required.

Thanks a lot both of you guys. You have been a great help to me so far.


EDIT:
I can access my site via:
hatchseadgroup.com         but not
[www.hatchseadgroup.com](www.hatchseadgroup.com)

Is there a quick fix for this?

---

### Post by dethredic on 2008-01-24
Ok, I may have jumped the gun. The [http://hatchseadgroup.com](http://hatchseadgroup.com) works for me, but not for my friends...

also, [www.http://www.hatchseadgroup.com](www.http://www.hatchseadgroup.com) is still not working.

Here are the conf files I remember making changes too. Let me know if you need to see others.


named.conf

> 
include "/etc/bind/named.conf.options";

zone "." {
	type hint;
	file "/etc/bind/db.root";
};

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

zone "1.168.192.in-addr.arpa" {
        type master;
        notify no;
        file "/etc/bind/db.192";
};

include "/etc/bind/named.conf.local";


named.conf.local
> 
 zone "hatchseadgroup.com" {
             type master;
             file "/etc/bind/db.hatchseadgroup.com";
        };


named.conf.options
> 
options {
	directory "/var/cache/bind";

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};


db.912
> 
;
; BIND reverse data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.hatchseadgroup.com. root.hatchseadgroup.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      ns.
10      IN      PTR     ns.hatchseadgroup.com.


and finally db.hatchseadgroup.com

> 
;
; BIND data file for local loopback interface
;
$TTL	604800
@	IN	SOA	ns.hatchseadgroup.com. pl.gnneiek.com. (
			10
			604800
			86400
			2419200
			604800 )
;
hatchseadgroup.com.	IN	NS	ns.hatchseadgroup.com.
hatchseadgroup.com.	IN	A	192.168.1.137
[www.hatchseadgroup.com](www.hatchseadgroup.com).	IN	A	192.168.1.137
[www.hatchseadgroup.com](www.hatchseadgroup.com).	IN	NS	ns.hatchseadgroup.com.


---

### Post by MJN on 2008-01-25
Have you turned your port forwarding off? I'm getting no response at all from your name server.

Incidentally, your resource records need to be pointing to your public WAN address (not 192.168.1.137) as that address is unreachable by those of out here in the Internet. Hence, we need to be told your public WAN address then when we end packets to it your router will pass them on to your server.

Mathew

---

### Post by dethredic on 2008-01-25
Well, you couldn't access my server, because I turned it off.

I changed all the IP's and now it seems to be working because some of my friends can access the page.


One problem that still exists is that when I use the [http://www.hatchseadgroup.com/](http://www.hatchseadgroup.com/) it doesn't load but when I use [http://hatchseadgroup.com/](http://hatchseadgroup.com/) it does.

---

### Post by MJN on 2008-01-25
> **dethredic said:**
> I changed all the IP's and now it seems to be working because some of my friends can access the page.
 
Excellent news - and a relief too! ;)
 
> One problem that still exists is that when I use the [http://www.hatchseadgroup.com/](http://www.hatchseadgroup.com/) it doesn't load but when I use [http://hatchseadgroup.com/](http://hatchseadgroup.com/) it does.
 
It's working from here so it's likely you just had an incorrect cached DNS result for it.
 
Mathew

---

### Post by dethredic on 2008-01-25
weird, It still doesn't work for me, or a couple of my Friends. We all have the same ISP though, so could that be it?

Anyways stuff like this has happened before. I will give it some time.


Thanks once again.

---

### Post by MJN on 2008-01-25
> **dethredic said:**
> We all have the same ISP though, so could that be it?
 
Definitely - it's just caching in action.
 
Although here's the bad news - your TTL (Time To Live) is set at 604800 seconds - that's 7 days - so you *could* be in for a bit of a wait.... I'd drop that down to 86400 maximum (24 hours) although it's not going to help in this instance.
 
Mathew

---

### Post by dethredic on 2008-01-25
Ok thanks. I will do that.

---

