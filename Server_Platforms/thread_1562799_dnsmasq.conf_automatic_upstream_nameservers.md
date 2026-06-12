---
title: "dnsmasq.conf automatic upstream nameservers?"
date: 2010-08-28
forum: Server Platforms
---

### Post by richwils on 2010-08-28
Hi,  

First a bit of background. I have Ubuntu server 10.04 and I use dnsmasq for my dns.  For my upstream nameserver I was simply using my router (linksys wrt320n) by having the following line in my dnsmasq.conf

server=192.168.1.1

The router took care of the rest of it.  However, there appears to be a vulnerability with the router related to dns (cache poisoning!?)and I was getting missing images in flickr and facebook redirecting to myspace and some random sites redirecting to google.  These problems were intermittent and very annoying.  Also googling the problem did not give me a solution. (Shame on Linksys from what I could find.)

I resolved the issue by changing the server line in dnsmasq to point directly at the name servers of my ISP, thus bypassing the dns vulnerability of my router.

However, I can see a problem in the future should my ISP update their name servers.  My question is... 

If possible, How can I get the name server addresses automatically from my ISP and have dnsmaq use them? 

I know that if it stops working I can simply update manually, but I'm a bit of a perfectionist and interested to learn.

TIA

Rich

---

### Post by koenn on 2010-08-28
dnsmasq is a cache/forward dns server, so you're always going to need forwarders. 
by default, it uses  /etc/resolv.conf as a list of forwarders, so you could put 4 name servers there, If you select servers at separate networks / from different providers, you're probably OK.

I suppose you could put together a script that reads your ISP's network status web page and grep the ip addresses of the dns servers, but that feels like a kludge. 

The 'ideal' solution is to use bind, without forwarders, so that you force it to recurse through the DNS system to resolve whatever name you throw at it. 

This means you move the single point of failure from your ISP's DNS to your own DNS server. But at least, you'll now when the ip address of the server has been changed :-)

---

