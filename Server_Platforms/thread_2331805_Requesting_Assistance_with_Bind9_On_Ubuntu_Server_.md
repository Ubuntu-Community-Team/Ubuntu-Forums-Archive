---
title: "Requesting Assistance with Bind9 On Ubuntu Server 14.04.4 LTS"
date: 2016-07-25
forum: Server Platforms
---

### Post by patrickkell on 2016-07-25
Hey everyone,

So I'm hitting a brick wall here, and obviously I'm missing/overlooking something, but I'm not seeing it, and the online support for this seems to be...well..non-existent.

The quick statement of the problem: Hosts on the internet do not resolve ANY records on my DNS servers, including my DNS servers themselves.


[LIST]
[*]I've setup DNS servers on two VPS(virtual private servers).
[*]I've designated both of these on my GoDaddy account(who I have my domain with) as Hostnames (NS1 and NS2), then set my name servers on GoDaddy for each (ns1.domain.ca; ns2.domain.ca)
[*]To ensure all of the records work, I have tested by setting my DNS on three different Windows hosts (across two different networks, one corporate, the other home), and all records resolve correctly.
[*]When my host is set with the DNS servers, I can do a dig and get results, but they all lack the "aa" tag to represent authoritative results.
[*]Without the DNS set as the IPs of the DNS servers, no hosts can resolve the records.
[/LIST]

Side Note: My initial setup was based on the Digital Ocean process here: [https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-caching-or-forwarding-dns-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-a-caching-or-forwarding-dns-server-on-ubuntu-14-04)
apt-get update and upgrade were both run prior to starting the process.


Any and all help is appreciated.



To help resolve this, I'm including images of named.conf.local, named.conf.options, my zone file, and the tail-end of the syslog from both NS1 and NS2.
Certain info is blanked out for security, but if something specific is required, feel free to ask.

The album with all of the images is here: [http://imgur.com/a/aXRMd](http://imgur.com/a/aXRMd)

NS1:
[http://imgur.com/6BlcF9D](http://imgur.com/6BlcF9D) -named.conf.options
[http://imgur.com/QrETuDJ](http://imgur.com/QrETuDJ) -zone file
[http://imgur.com/DLJ7cb1](http://imgur.com/DLJ7cb1) -named.conf.local
[http://imgur.com/b8gfd60](http://imgur.com/b8gfd60) -syslog

NS2:
[http://imgur.com/XoQfTld](http://imgur.com/XoQfTld) -named.conf.options
[http://imgur.com/owST4S3](http://imgur.com/owST4S3) -zone file
[http://imgur.com/DLJ7cb1](http://imgur.com/DLJ7cb1) -named.conf.local
[http://imgur.com/pgCZI4T](http://imgur.com/pgCZI4T) -syslog

---

### Post by Frogs Hair on 2016-07-25
Hello and Welcome 

Moved your thread to Server Platforms .

---

### Post by SeijiSensei on 2016-07-26
Are the servers firewalled?  If so, are you permitting inbound traffic to UDP port 53?

---

### Post by patrickkell on 2016-07-26
Hi SeijiSensei,

They are not behind a firewall.

The VPS provider doesn't block anything (a discussion I've had with them a few times), and even then the servers accept queries from systems that have them set as their DNS server.
As a caching server, they'll also do recursive queries out to other DNS servers on the internet, which they perform correctly when a host is given their IPs as DNS servers.

---

### Post by patrickkell on 2016-07-30
UPDATE: So as a thought (due to a random happenstance of the right Google search), I decided to try getting full DNSSEC setup with a key signing key, and a zone signing key.

All was going well until I found out GoDaddy doesn't have the ability to do DNSSEC verification for .ca domains(some jackass out there doesn't consider them a TLDN).
I suspect the lack of DNSSEC is the cause in this case for why no DNS requests on the internet would actually acknowledge my servers.

I've backed up the configs for now, but I'm re-imaging the two VPS to something else for the time being(until I grab a .com, perhaps). If anyone else has an idea, feel free to post it. I can always test and/or re-image.


Thanks

---

