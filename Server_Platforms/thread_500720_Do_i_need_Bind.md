---
title: "Do i need Bind ????"
date: 2007-07-14
forum: Server Platforms
---

### Post by CHUCKYCHUCK on 2007-07-14
Hi !

I have a question about Bind, i don't know a lot of things about dns, only that a dns server translates ip adresses to  readable domain names

I read some tutorials about server administration ( for hosting websites ), there is always a chapter about bind..

When you have a single dedicated server, with only one domain and no subdomains, why do you need to have bind installed ???


For example, when i type in mysite.com in my browser, i ask the people who sells the .com domaine names what is the ip adress of mysite.com. Those people set up dns servers for that, those servers redirect my request to the server where is hosted the content of mysite.com

then why does that end server, the one which holds my website, also need to have bind installed ????

thanks

---

### Post by koenn on 2007-07-14
> **CHUCKYCHUCK said:**
>  i don't know a lot of things about dns, only that a dns server translates ip adresses to  readable domain names
no, it's domain / hostnames to IP addresses
> **CHUCKYCHUCK said:**
> 
When you have a single dedicated server, with only one domain and no subdomains, why do you need to have bind installed ???


For example, when i type in mysite.com in my browser, i ask the people who sells the .com domaine names what is the ip adress of mysite.com. Those people set up dns servers for that, those servers redirect my request to the server where is hosted the content of mysite.com

then why does that end server, the one which holds my website, also need to have bind installed ????

You don't really need it to have it installed **yourself**.
However, the people who manage .com will at most have a DNS record that says "the name server for mysite.com is called [name of server] / is at address (ip addres of DNS server"
So there must be a domain name server for that domain, and it will at least have a record saying something "I am the DNS server for domain mysite.com". It will probably also have some records such as " [www.mysite.com](www.mysite.com) is at [your.ip.address.here]"

So, you can run bind yourself, our have a third party to do it for you. Most internet providers / webhosting providers / ... offer this type of simple DNS service ("DNS hosting") for free. You could also check OpenDNS or DynDNS, the offer similar services.

---

### Post by Mr. C. on 2007-07-14
> **koenn said:**
> no, it's domain / hostnames to IP addresses

Just for clarity and to remove confusion, it does both name->IP and IP->name tranlsation, and other things.

CHUCKYCHUCK, there are a multitude of reasons to run a name server, with some obvious reasons being:

[LIST=1]
[*]Total control over the name space for the domain
[*]Fast, rich local DNS cache
[*]You run system services that require fast DNS lookups (eg. mail servers)
[*]You have many hosts in private IP space and want name translation for them
[/LIST]

For simple needs, the 3rd party host that provides authoritative DNS records for your zone (domain) is almost always sufficient, and there is no need for you to take authoritative control over your DNS zone.  When your zone gets more complex, or you have special needs not supported by your DNS registrar/host, you might need to run your own DNS server.

MrC

---

### Post by CHUCKYCHUCK on 2007-07-14
thanks,

if i understood, the organization which manages the .com domain names, redirects to another dns server, not to a "regular" computer

---

### Post by Mr. C. on 2007-07-14
Its a little more complicated than that.  Basically, your system queries the DNS server it is configured to use.  It in turn recursively follows referrals starting with the root DNS servers which in turn indicate which servers handle the .com, .net, etc. first level domains.  The .com and .net servers, return referrals for the authoritative name servers for, say, yourdomain.com or mydomain.net, etc. etc.

If you want to little overview about DNS, review the Week 8 DNS notes, lab, and homework here:

[http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

MrC

---

