---
title: "Is it possible to create master/slave NS records with dynamic IP?"
date: 2008-03-25
forum: Server Platforms
---

### Post by adiaz1214 on 2008-03-25
I installed the Ubuntu server platform and was able to get DHCP up and running, I have also been able to set up LAMP and Bind.

I've worked in the web-hosting industry and worked with these systems for years but never really learned how to set them all up..

Here's what I would like to do..

I want to create a master and slaver DNS record so that I can use them to point my domain to my web-site that is also hosted on this server.

Unfortunately, I don't have any static IPs to my disposal, so I wanted to know if it is possible to create those two records with a dynamic IP?  Can I use a dynamic DNS service to create two records?

I also was curious as to how one would go about doing this in the named.conf records as well as the domain.com.db record.

Also one more thing, whenever I log in to the server as root(or any user) when I ls the home directory, nothing shows.  I can't view any of the folders (/etc /var /usr etc etc.)I know they are there because I can cd in to them.  I just would like to see them, I don't know if it has to do with permissions but i'd like to have these folders viewable.

Thanks!

---

### Post by adiaz1214 on 2008-03-25
:confused:

No one?

---

### Post by Mr. C. on 2008-03-25
> **adiaz1214 said:**
> I want to create a master and slaver DNS record
This doesn't make sense.  Master and slave are terms indicating the type of server with respect to a particular zone.  There is little need for you to run both a master and a slave DNS server when they are both on the same IP.  The reason for master/slave servers is for redundancy, and that requires distinct networks.

> 
... so that I can use them to point my domain to my web-site that is also hosted on this server.

Unfortunately, I don't have any static IPs to my disposal, so I wanted to know if it is possible to create those two records with a dynamic IP?  Can I use a dynamic DNS service to create two records?

You can do this, but the question is what are you trying to accomplish?

[LIST]
[*]Are you trying to make the server publically available, internal-only, o both?
[*]What is your reason from using your own DNS server, and making it public"?
[*]Have you considered using DynDNS or similar to provide your A records for you?
[*]Are you behind a NAT firewall, which allows your server to have a static private IP?
[/LIST]

You really don't want your server to have a dynamic IP; this complicates things.

> 
Also one more thing, whenever I log in to the server as root(or any user) when I ls the home directory, nothing shows.  I can't view any of the folders (/etc /var /usr etc etc.)I know they are there because I can cd in to them.  I just would like to see them, I don't know if it has to do with permissions but i'd like to have these folders viewable.

Demonstrate this via captured/pasted commands and command output.

---

