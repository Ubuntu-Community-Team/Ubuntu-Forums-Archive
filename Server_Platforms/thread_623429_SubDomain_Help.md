---
title: "SubDomain Help"
date: 2007-11-25
forum: Server Platforms
---

### Post by mattc908 on 2007-11-25
Hey was wondering was setting up a subdomain, I type the name I want in, than it gives options:
NS
TXT
CName
A
MX 

Im guessing I fill in one for were I want the subdomain to forward to? Which one though? Or Can I do it via apache?

---

### Post by conjur3r on 2007-11-26
I believe you want a A record.

---

### Post by koenn on 2007-11-26
you need an NS record to indicate which Name Server will do name resolution for your subdomain; 
you need an A record with the address of that name server.
You need A records for the Addresses of those hosts you want to approach by hostname rather than by IP address

If you have a separate mail server for your subdomain, you need MX (Mail Exchange) records to indicate what mail servers wil handle the mail domain, and A records for their addresses

If a machine has multiple names, you'd use CNAME (canonocal Name, Alias) rather than additional A records. 

TXT (text) reords are usually used for special purposes such as kerberos/MS active directory or SPF, or for any additional info, so you probably won't need them.

---

