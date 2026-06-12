---
title: "Creating a subdomain in bind9"
date: 2013-10-18
forum: Server Platforms
---

### Post by julia3 on 2013-10-18
So after much struggles and irratation and wanting to throw my computer out the window I finally got the home server set up. 

It now works on all computers by installing bind 9. I set that all up, but once again I am stuck.

How do I create a sub domain in bind 9?

---

### Post by L486XGW on 2013-10-18
Create a zone for the domain you want then add the A record for the subdomain.

---

### Post by SeijiSensei on 2013-10-18
OK, I'm going to put on my didactic hat for a moment.

"Subdomains" are not the same as "hosts."  A host is a single computer; a subdomain is a collection of computers that belong to a portion of a domain for which a delegated nameserver is used.

Suppose we have the domain "example.com".  If I have a machine that provides web services, I might want to name it "www.example.com".  That is the name of a *host*.  In the DNS it is referenced either with an A record that points to the machine's IP address, or a CNAME record that is an alias pointing to a different A record.  So the machine could be named "mywebserver.example.com" with "www.example.com" as a CNAME alias.  In the zone file, you would have

```

[...]
mywebserver     IN     A         10.10.10.10
www             IN     CNAME     mywebserver

```

A subdomain typically is used to represent organizational divisions within a domain.  Suppose, for instance, that the HR department has 25 computers.  We might create a subdomain, "hr.example.com," with hosts named "billspc.hr.example.com," "jillspc.hr.example.com", etc.  Often a reason to create subdomains is to decentralize mail systems.  You might want the mail for people in HR sent to a different server than mail for marketing.example.com.  In this case you actually need to set up two DNS servers, one for "example.com" and another for "hr.example.com".  In the domain-level server, you would have records like this:

```

[...]
hr           IN     NS   hr-dns
hr-dns       IN     A    10.10.10.11

```

and on hr-dns you would have another zone file with an SOA for that subdomain and records like this:

```

@           IN     NS     localhost
            IN     MX     0 hr-mail

hr-mail     IN     A      192.168.1.1

billspc     IN     A      192.168.1.101
jillspc     IN     A      192.168.1.102

```

In this system, the "fully-qualified domain name" for the machine at 192.168.1.101 is "billspc.hr.example.com".

---

### Post by julia3 on 2013-10-18
Thank you so much. 
I have solved it.
Now I can go to 
lifelist.thelearningnerd.com
But how do I edit the subdomain now from my computer. 
I know how to edit thelearningnerd.com

---

