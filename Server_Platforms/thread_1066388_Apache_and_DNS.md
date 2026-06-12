---
title: "Apache and DNS"
date: 2009-02-10
forum: Server Platforms
---

### Post by moosehadley on 2009-02-10
Hello, I'm rather new to owning my own server, and I just registered a domain name with the free service EveryDNS.

I see a note on the EveryDNS website that says: 

> To have your domain resolve correctly, please use ns1.everydns.net, ns2.everydns.net, ns3.everydns.net, and ns4.everydns.net as your domain's nameservers in your registrar's whois database. Without that, none of your records will resolve properly. (NS1 is in San Diego, while NS2 is in San Jose, NS3 is in the Netherlands, and NS4 is in Washington, D.C.) 


So, my question is, how do I set a domain's nameserver?
Or rather, what do I need to do in Apache?

I've been looking around google for a while now with out much luck...

Thanks a lot!

---

### Post by moosehadley on 2009-02-10
Anyone? Please?
It's a simple question.

---

### Post by y@w on 2009-02-10
You set your domain's nameservers in the registrar's config. EveryDNS should handle this for you if that's who you registered the domain through. I can't speak as to how since I've never registered a domain with them. Check the output of the following command to see if it's setup properly:
> dig <domain>
(replace <domain> with your domain of course)

Apache really doesn't have anything to do with it. Apache's a web server, not a DNS server.

---

### Post by moosehadley on 2009-02-10
Ok, so theres really nothing I need to do?

I really don't know if dig would give a good output
I should still have 1-2 days for propagation.

But anyway, heres its output.
The domain name should be kehadley.com
and the servers IP is dynamic and automaticly updated, but at the time of this posting its 68.21.93.55

> blake@server:~$ dig kehadley.com

; <<>> DiG 9.5.0-P2 <<>> kehadley.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 55371
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;kehadley.com.                  IN      A

;; AUTHORITY SECTION:
com.                    900     IN      SOA     a.gtld-servers.net. nstld.verisign-grs.com. 1234321216 1800 900 604800 900

;; Query time: 148 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Tue Feb 10 22:00:40 2009
;; MSG SIZE  rcvd: 103


I'm really not sure how to read this.

---

### Post by jimv on 2009-02-10
Who did you register your domain name with?

You need to go to that site, log in, and go to the section where you can manage your domain.  You'll see a place where you can set "Nameservers", which you'll want to change to the ones that EveryDNS gave you.

---

