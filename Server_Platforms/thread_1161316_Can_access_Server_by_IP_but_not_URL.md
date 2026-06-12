---
title: "Can access Server by IP but not URL"
date: 2009-05-16
forum: Server Platforms
---

### Post by dethredic on 2009-05-16
So, a couple days ago my ISP changed my external IP (they do that about twice a year). I updated my nameservers, but I can no longer access my site via URL.
I can type in its IP address (24.150.45.130) and the site loads.

If I type in my domain name (hatchseadgroup.com) the site does not load.

In DynDNS I have this:
[IMG]http://gunnewiek.com/up/hosts.jpg[/IMG]


Then in NameChep I have this:
[IMG]http://gunnewiek.com/up/domain.jpg[/IMG]

Also, if I type in one of those nameservers into my address bar I am taken to my site. I am thinking there is a broken link between DynDNS and namecheap

So, I haven't changed any config files that I may need to. I set this server up a while ago and I forget what else may need changing.

---

### Post by dethredic on 2009-05-16
Ok, I did a nslookup on my server and the IP is still my old one. Where do I go to change that?

---

### Post by hictio on 2009-05-16
Ok, so, you own the domain 'hatchseadgroup.com', which at the moment, its web page IP address is 24.150.45.130.

Ok, and, you have that domain DNS server hosted on NameChep, is that so?

If so, you have to edit the record on NameChep that points 'hatchseadgroup.com' to the current IP address, since its resolving to an older one.

```

tango:~$ host hatchseadgroup.com
hatchseadgroup.com has address 24.150.41.56

tango:~$ dig ns hatchseadgroup.com

; <<>> DiG 9.5.1-P2 <<>> ns hatchseadgroup.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50305
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;hatchseadgroup.com.		IN	A

;; ANSWER SECTION:
hatchseadgroup.com.	80	IN	A	24.150.41.56

;; Query time: 46 msec
;; SERVER: 10.120.11.1#53(10.120.11.1)
;; WHEN: Sat May 16 19:12:39 2009
;; MSG SIZE  rcvd: 52

tango:~$ host www.hatchseadgroup.com
www.hatchseadgroup.com has address 24.150.41.56

```

---

### Post by dethredic on 2009-05-16
> **hictio said:**
> Ok, so, you own the domain 'hatchseadgroup.com', which at the moment, its web page IP address is 24.150.45.130.

Ok, and, you have that domain DNS server hosted on NameChep, is that so?

If so, you have to edit the record on NameChep that points 'hatchseadgroup.com' to the current IP address, since its resolving to an older one.

```

tango:~$ host hatchseadgroup.com
hatchseadgroup.com has address 24.150.41.56

tango:~$ dig ns hatchseadgroup.com

; <<>> DiG 9.5.1-P2 <<>> ns hatchseadgroup.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50305
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;hatchseadgroup.com.		IN	A

;; ANSWER SECTION:
hatchseadgroup.com.	80	IN	A	24.150.41.56

;; Query time: 46 msec
;; SERVER: 10.120.11.1#53(10.120.11.1)
;; WHEN: Sat May 16 19:12:39 2009
;; MSG SIZE  rcvd: 52

tango:~$ host www.hatchseadgroup.com
www.hatchseadgroup.com has address 24.150.41.56

```

I did edit the namecheap nameservers, and you can see those link up to my IP address.

---

### Post by Cheesemill on 2009-05-16
It could just be that the new DNS settings haven't fully propegated to the DNS servers your ISP uses yet, this can take up to 24 hours.

Cheesemill

---

### Post by dethredic on 2009-05-16
> **Cheesemill said:**
> It could just be that the new DNS settings haven't fully propegated to the DNS servers your ISP uses yet, this can take up to 24 hours.

Cheesemill

It has been a week or so.

---

### Post by hictio on 2009-05-16
> **dethredic said:**
> I did edit the namecheap nameservers, and you can see those link up to my IP address.

I see that, but, please forgive me, but there is something that maybe isn't clear to me, but on the namecheap input boxes you are telling them that those hosts are your DNS servers.
Is that correct? Those shouldn't be your DNS server, but your actual servers.
Who is handling the DNS for your domain? I mean where do you edit the records that points and IP address to a host?

---

### Post by dethredic on 2009-05-16
> **hictio said:**
> I see that, but, please forgive me, but there is something that maybe isn't clear to me, but on the namecheap input boxes you are telling them that those hosts are your DNS servers.
Is that correct? Those shouldn't be your DNS server, but your actual servers.
Who is handling the DNS for your domain? I mean where do you edit the records that points and IP address to a host?

I use DynDNS. You can see how I have it configured in the first screenshot.

---

### Post by dethredic on 2009-05-17
anyone?

---

### Post by dethredic on 2009-05-19
bump

---

### Post by redmk2 on 2009-05-19
> **dethredic said:**
> ... I can type in its IP address (24.150.45.130) and the site loads.


The DNS name you want to use should be mapped this address.  If you look below at your JPG you will see that the names mapped to that IP address are not that.

Hitco was correct you should only have the names you want resolved listed in those spots.  What are the other names?  Do you have other sub-sites?

I would expect to only see hatchseadgroup.com and [www.hatchseadgroup.com](www.hatchseadgroup.com) as names mapped to the IP address.  

> 

If I type in my domain name (hatchseadgroup.com) the site does not load.

I believe it will if you map it correctly.  Where it says *Host Services*, you should only have hatchseadgroup.com and [www.hatchseadgroup.com](www.hatchseadgroup.com)
> 
In DynDNS I have this:
[IMG]http://gunnewiek.com/up/hosts.jpg[/IMG]


Then in NameChep I have this:
[IMG]http://gunnewiek.com/up/domain.jpg[/IMG]

Those are not spaces for you to list the nameservers.  That's for you to list the data for the nameservers e.g. hostnames of your webserver.  See the statement that says "Change existing Doman Name server *information*"?
> 
Also, if I type in one of those nameservers into my address bar I am taken to my site. I am thinking there is a broken link between DynDNS and namecheap

Because of the mapping I just spoke of.  Kinda proves that this is where you put the host names and not the nameservers.

> 
So, I haven't changed any config files that I may need to. I set this server up a while ago and I forget what else may need changing.

I think all you need to do is update  to the correct hostnames.  Once again, what do the names that are listed mean to you?  Are they pertinent?

---

### Post by dethredic on 2009-05-20
> **redmk2 said:**
> The DNS name you want to use should be mapped this address.  If you look below at your JPG you will see that the names mapped to that IP address are not that.
Hmm, maybe I am not understanding you correctly, but the IP's in the picture match the IP's of my site.

> Hitco was correct you should only have the names you want resolved listed in those spots.  What are the other names?  Do you have other sub-sites?
I made some new ones when I realized that changing the IP's only old ones didn't work. They are just extra.

> I would expect to only see hatchseadgroup.com and [www.hatchseadgroup.com](www.hatchseadgroup.com) as names mapped to the IP address.
I believe it will if you map it correctly.  Where it says *Host Services*, you should only have hatchseadgroup.com and [www.hatchseadgroup.com](www.hatchseadgroup.com)
It is not possible to do this. I just make a subdomain at one of their 88 other domains, and point that subdomain to my IP. It shouldn't matter what the domain looks like because it points to my IP.

> Those are not spaces for you to list the nameservers.  That's for you to list the data for the nameservers e.g. hostnames of your webserver.  See the statement that says "Change existing Doman Name server *information*"?
Yes those are the spaces to change my nameservers. I have my nameservers there for 3 other domains and they work great.

> 
Because of the mapping I just spoke of.  Kinda proves that this is where you put the host names and not the nameservers.
I think all you need to do is update  to the correct hostnames.  Once again, what do the names that are listed mean to you?  Are they pertinent?
I can delete any of the entries in DynDNS anytime and make new ones anytime.

The only reason I think that you are wrong is because I had it set up this way before my IP changed and it worked flawlessly.

---

### Post by redmk2 on 2009-05-20
> **dethredic said:**
> Hmm, maybe I am not understanding you correctly, but the IP's in the picture match the IP's of my site.


I believe we *are* talking about two different things.  I was saying that the *name* you wish to use (hatchseadgroup.com) **does not appear** on the list.  I can see the numbers as you state.

Now, if you are referring to the hostname as a subdomain of a dyndns.com domain then I would start [*_here_*]("http://www.dyndns.com/services/dns/dyndns/howto.html") and also [*_ here_*]("http://www.dyndns.com/support/kb/why_cant_i_connect_to_my_server.html").  But I bet you have already read this a million times :-(

Then I would be talking to them.

Sorry I couldn't help.

---

### Post by hictio on 2009-05-20
It seems to me that now there are more problems?
Take a look at this tests:

```

% dig ns hatchseadgroup.com

; <<>> DiG 9.3.6-P1 <<>> ns hatchseadgroup.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 37183
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;hatchseadgroup.com.            IN      NS

;; ANSWER SECTION:
hatchseadgroup.com.     604800  IN      NS      ns.hatchseadgroup.com.

;; Query time: 365 msec
;; SERVER: my.dns.server#53(my.dns.server)
;; WHEN: Thu May 21 00:18:42 2009
;; MSG SIZE  rcvd: 53

% dig @ns.hatchseadgroup.com www.hatchseadgroup.com
dig: couldn't get address for 'ns.hatchseadgroup.com': not found

% host ns.hatchseadgroup.com
Host ns.hatchseadgroup.com not found: 3(NXDOMAIN)

```

---

### Post by redmk2 on 2009-05-20
Hi there Hitco,

I'm not sure what the OP has going on.  I got your point earlier.  I don't know how dyndns resolves so I am the wrong guy to comment.  I will say that my dig gets a different response that you.  See below```


redmk2@jaguar$ dig ns hatchseadgroup.com

; <<>> DiG 9.4.2-P2 <<>> ns hatchseadgroup.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 65397
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;hatchseadgroup.com.		IN	NS

;; ANSWER SECTION:
hatchseadgroup.com.	172632	IN	NS	hatseadgroup4.servegame.org.
hatchseadgroup.com.	172632	IN	NS	hsg1.shacknet.nu.
hatchseadgroup.com.	172632	IN	NS	hatseadgroup2.scrapping.cc.

;; Query time: 37 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Wed May 20 20:42:23 2009
;; MSG SIZE  rcvd: 147

```

Edit:  Hmmmm, this resolves :hatseadgroup4.servegame.org and hatseadgroup2.scrapping.cc.  But this does not:hatchseadgroup.com.

Sure sounds like a dyndns prob rather than a pure DNS prob.

---

### Post by suffice on 2009-05-21
I'm also having the same issue with a simple domain without subdomains.

i have a simple web server setup.  i use noip for my dynamic IP, which works on all computers via (www.<somename>.com) but from my own computer i can only access it via localhost, or the ip.  

for me it couldn't be the dynamic IP because it works from other computers, just not mine (the one its running on)

its all really strange because I've had it setup and working properly on other versions of Ubuntu

---

### Post by dethredic on 2009-05-21
When I do a nslookup on my domain here are the results:
>  DNS server handling your query: localhost
 DNS server's address:	127.0.0.1#53
 
 Non-authoritative answer:
 hatchseadgroup.com
 	origin = ns.hatchseadgroup.com
 	mail addr =
 	serial = 10
 	refresh = 86400
 	retry = 86400
 	expire = 2419200
 	minimum = 604800
 Name:	hatchseadgroup.com
 Address: 24.150.41.56
 hatchseadgroup.com	nameserver = ns.hatchseadgroup.com.
 
 Authoritative answers can be found from:


Now, that IP is wrong and so are those nameservers. Now those records could be from when I did use bind9 before (I don't anymore I use DynDNS). Maybe the records some where are messing stuff up.

---

