---
title: "Amazon EC2 DNS, Mail and Web Server"
date: 2014-09-05
forum: Server Platforms
---

### Post by addictedboy on 2014-09-05
Hi,

I am planning to move my website to Amazon EC2 servers. I have a budget for creating one paid instance and one free instance, so there will be two instances.

1) Ubuntu 14.04 - Web and FTP server and most probably  DNS master server (ns1)

  Elastic IP => 1.2.3.4 (just for e.g)
  fqdn => helios.mydomain.com
 Region => virginia east
 internal ip = > 10.1.1.3
  
2) Ubuntu 14.04 -> Mail server and ns2 DNS slave server

     Elastic IP => 5.4.3.2
     fqdn => mail.mydomain.com
    Region => California
   Internal ip => 172.16.1.4

I will be following this guide - [https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-an-authoritative-only-dns-server-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-configure-bind-as-an-authoritative-only-dns-server-on-ubuntu-14-04)

The doubts I am having here is that those three servers are on same subnet. However here on EC2, it is on different subnet, so how to configure the reverse dns zones and set the mx records?

---

### Post by addictedboy on 2014-09-08
Can anyone tell me how to create the reverse dns zone files?

---

### Post by Habitual on 2014-09-08
See [Q: Can I configure the reverse DNS record for my Elastic IP address?]("http://aws.amazon.com/ec2/faqs/")

---

### Post by addictedboy on 2014-09-09
> **Habitual said:**
> See [Q: Can I configure the reverse DNS record for my Elastic IP address?]("http://aws.amazon.com/ec2/faqs/")

Thanks for the reply. I saw that and created the forwarded zone accordingly. Does that also mean I have not to create the reverse zone locally on my server ?
Also for the hostname, how can I setup two hostnames based on one domain? My idea is to create server 1 as authoritative and server 2 as slave server.

domain name => [www.example.com]("http://www.example.com") (hosted on server1)

Server 1 => prod[.example.com]("http://www.example.com") => 1.2.3.4 => ns1

Server 2 => dev.example.com => 5.6.7.8 => ns2

---

### Post by Habitual on 2014-09-09
> **addictedboy said:**
> Does that also mean I have not to create the reverse zone locally on my server ? I don't know. sorry.

> **addictedboy said:**
> 
Also for the hostname, how can I setup two hostnames based on one domain? My idea is to create server 1 as authoritative and server 2 as slave server.
domain name => [www.example.com]("http://www.example.com") (hosted on server1)
Server 1 => prod[.example.com]("http://www.example.com") => 1.2.3.4 => ns1
Server 2 => dev.example.com => 5.6.7.8 => ns2

NS names can be anything you like, eg:
fredflintstone.domain.com =>  1.2.3.4
barneyrubble.domain.com => 5.6.7.8 
As long as they point to valid DNS-serving hosts (determined by the IP or A Record) of the entry at the Registrar.

multiple hostnames can exist on the system as determined by their A Record entry, a valid zone file on the DNS-serving Nameserver, and an a http server configured to use [NameBasedVirtual hosts]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html")
both of these, for example can exist at 1.2.3.4
mykewldomain.com
myuncooldomain.com

When the query is made for say, mykewldomain.com it goes to the Registrar.
The Registrar's record should point to a nameserver and says "give me the IP for mykewldomain.com's nameserver"
The request is then re-asked at the nameserver but asks for the A Record of the domain. This is the A Record and should point to an http-serving host, (the "server")

The rDNS for an ip can only have 1 record however.

I hope that helps.

---

