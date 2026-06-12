---
title: "Bind settings - ns1 and ns2 for www"
date: 2012-03-17
forum: Server Platforms
---

### Post by gfieraru on 2012-03-17
Hello,

I am a newbie so I will try to explain to the best of my knowledge.

I have an Ubuntu server setup with 2 internet connections with 2 public ips.

I set BIND up so it will answer for ns1 - IP1 and ns2 - IP2.

My problem is that I do not know how to setup the www for the server to do the following:

- when main connection is down (ns1) for example I want the visitors when they write [www.domain-name.com](www.domain-name.com) to be redirected through ns2 to the same website

What do I need to setup in addition?

- an additional DNS server connected to the internet and the server with the website connected to the DNS server in LAN
- do I have to setup some special commands in named.conf or the zone file
- is this done by some other service?

I hope I explained correctly. My hope is to have something like a hosting company that has multiple ns (ns1, ns2, ns3) and the website in one place. No matter which ns is requested he should return [www.domain-name.com](www.domain-name.com).

Thank you in advance for your help.

---

### Post by SeijiSensei on 2012-03-18
One simple solution is to use "round-robin" DNS entries.  This doesn't provide "failover" as you would like.  Instead it randomizes requests across a set of IP addresses.  You'd have an entry like this in your zone file:

```

www     IN     A     10.1.1.1
        IN     A     10.1.1.2

```

Now half the requests get the first address, and half get the second.  You can alter the odds by repeating one or the other entry.  

Anything more complex than this probably requires implementing the "[high-availability]("http://www.linux-ha.org/wiki/Main_Page")" solutions for Linux where the servers keep tabs on each another.

---

### Post by gfieraru on 2012-03-18
Thank you very much for your help.

This is the best answer I got/found so far. Everybody was saying to change the TTL to 60 but that would have created a lot of traffic for the DNSs. I do not believe this to be a solution.

By doing what you recommended requires only 2 good internet connections.

**Question:** You said half will go one way half the other. But for example if I enter the website www in my browser let's say I get on ns1. If I click a link there is a possibility to be redirected to ns2?

I think my question is: Are there any rules to how I as a visitor am redirected to the server's ns?

Also you said I can alter the odds by repeating one of the entries. Does it work proportionally (e.g. If I have 3 declarations for ns1 and 1 for ns2 the proportion will be 75% will go on ns1 and 25% on ns2 (considering they are both up))?

Again thank you for your answer.

---

### Post by SeijiSensei on 2012-03-19
> **gfieraru said:**
> **Question:** You said half will go one way half the other. But for example if I enter the website www in my browser let's say I get on ns1. If I click a link there is a possibility to be redirected to ns2?

Yes.  HTTP is called a "stateless" protocol since each request is handled entirely independently of all others.  However it's less likely to happen in real-life because DNS queries are usually cached by the operating system.  So if [www.example.com](www.example.com) points to both 10.1.1.1 and 10.1.1.2, and I get the 10.1.1.1 address when I query the DNS server, it's pretty likely that I'll continue to get that address in future queries as well.  

This can pose a problem with web sites that use sessions to track users across pages.  The session information stored on one machine will be unavailable to the other.  You can work around this problem in a variety of ways like sharing the directory where the session data are stored between the machines with NFS, or using an SQL database in the backend to store all the session information.

Another possible solution is to use a Redirect directive in the Apache configuration.  Suppose [www.example.com](www.example.com) and ns.example.com are the same machine.  You could create a VirtualHost like this:

```

<VirtualHost *:80>
    ServerName www.example.com 
    Redirect / http://ns.example.com/
</VirtualHost>

<VirtualHost *:80>
    ServerName ns.example.com
    DirectoryRoot /path/to/the/site
    etc.
</VirtualHost>

```

Now requests for [www.example.com](www.example.com) will be rewritten to ns.example.com.  The latter address will appear in the browser's address bar.  

Another option is to use the [<base href=>]("http://www.w3schools.com/tags/tag_base.asp") tag in HTML to specify the server part of the base URL.
 
> Does it work proportionally (e.g. If I have 3 declarations for ns1 and 1 for ns2 the proportion will be 75% will go on ns1 and 25% on ns2 (considering they are both up))?

Yes, precisely.

---

