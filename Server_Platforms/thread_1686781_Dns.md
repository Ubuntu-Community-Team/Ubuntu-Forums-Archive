---
title: "Dns"
date: 2011-02-12
forum: Server Platforms
---

### Post by Monotoko on 2011-02-12
Hi Guys,

I have a server with multiple domains and a DNS service (bind9) my main domain is registered with GoDaddy and it's A-record points to my server, it then has CNAME records with ns1 and ns2.

I use ns1 and ns2 to point my other domains to the DNS server I host, which then manages what happens.

Anyway, what I would like to do is enable the DNS server to manage the subdomains on my main host. For example, if the domain was example.com and I use admin.example.com in the DNS server, it will not follow through unless I set the cname up, whereas my others will. 

How do I do a similar thing for my main domain...does anyone have any ideas?

Monotoko

---

### Post by volkswagner on 2011-02-12
If I understand correctly your only domain with an issue is with Godaddy, correct?

You should not set the records at Godaddy, instead you should set the nameservers (in godaddy's domain manager select set nameserver) to your ns1 and ns2.

---

### Post by hawkmage on 2011-02-12
You need to establish the sub domain name servers in your parent Zone.  In your example domains of example.com and admin.example.com I assume that ns1.example.com and ns2.example.com refer to your DNS servers that you want to delagate admin.example.com to.  

To do this you need to add this to the example.com zone:
```
admin.example.com. IN NS ns1.example.com.
admin.example.com. IN NS ns2.example.com.
```

You also have to be able to resolve ns1.example.com and ns2.example.com in the example.com zone.

---

