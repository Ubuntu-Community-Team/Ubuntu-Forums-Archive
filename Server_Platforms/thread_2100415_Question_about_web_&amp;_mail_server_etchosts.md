---
title: "Question about web &amp; mail server /etc/hosts"
date: 2013-01-01
forum: Server Platforms
---

### Post by renee3 on 2013-01-01
Hi,

I set up web & mail server in same pc and i use Ubuntu 12.04 operating system. For example i have domain name example.org (80.72.130.40) and e-mail: example.org (80.72.130.41).
My server hostname is mail.example.org.

My /etc/hosts look like this:

127.0.0.1 mail.example.org
80.72.130.40 example.org


Is this correct ? Thank you.

---

### Post by volkswagner on 2013-01-02
Is your server behind a router or firewall?

I think what you are asking about is for DNS.  If you want your server to be reached from the Internet via example.org or mail.example.org you will need public DNS entries (A records, MX records and reverse DNS entries).  It is easiest to use your domain provider for creating DNS entries.

For example you will need the following records:

**Record** | **Data** | **Type**
             
example.org  | 80.72.130.40 |   A                  
mail.example.org  |     80.72.130.41     |       A
[www.example.org](www.example.org)   |     example.org      |       CNAME
example.org   |         mail.example.org    |    MX


You can check your public records using the following commands:


```
host example.org
```
```
dig example.org
```

You will want to run these commands from a machine that has not had /etc/hosts entries added for the domains.

---

### Post by TheFu on 2013-01-02
> **volkswagner said:**
> I think what you are asking about is for DNS.  If you want your server to be reached from the Internet via example.org or mail.example.org you will need public DNS entries (A records, MX records and reverse DNS entries).  It is easiest to use your domain provider for creating DNS entries.

Very useful response.  I would point out that you can have a single IP resolve to many, many different DNS, domain, and hostnames.

Use of x.x.x.40 and x.x.x.41 is not necessary. Any number of services can listen on the same IP.  If you want your email and web to be seen on the internet, then you **must use** a public DNS server. Your local /etc/hosts file means ZERO to the external world.

For web, just the name-to-IP DNS is needed.  For email, you need the name-to-IP AND the MX record.

You can check these with **dig**, **host** and **nslookup**. Read the man pages for details.

I'd also point out that many ISPs block all direct SMTP traffic, so before you try to get this working on the internet, you need to **know** if your ISP allows email server traffic at all.  Most residential ISPs force you to use their SMTP gateway so they can control spam.

You didn't mention NAT, so either you are really on an internet connected server or already understand that with port forwarding, etc ... Fantastic.

---

### Post by renee3 on 2013-01-02
Hello,

Thank you for your answers. My server is directly behind a router. I have also public DNS entries and my ISP allows email server traffics.
 I had just question how to /etc/hosts is correct ?

---

### Post by TheFu on 2013-01-02
> **renee3 said:**
> Hello,

Thank you for your answers. My server is directly behind a router. I have also public DNS entries and my ISP allows email server traffics.
 I had just question how to /etc/hosts is correct ?

It is syntactically correct, but it may not do what you want. I can't tell without more knowledge about the router and DNS settings.

Does your router use NAT?  If so, then only internal IPs should be in the /etc/hosts file for **this** server.

If you run an internal DNS so that other internal clients can find these services, it gets more complicated.  Does your network card listen on both external IP addresses? Do you have multiple network cards?  Does your internal network use a 10.x.x.x, 172.16-20.x.x or 192.168.x.x IP address range?

I wish there was an easy answer, but there isn't.  With what you've provided the answer is "perhaps yes, perhaps no."

---

