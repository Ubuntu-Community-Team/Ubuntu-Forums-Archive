---
title: "DNS problem"
date: 2011-01-26
forum: Server Platforms
---

### Post by koszta on 2011-01-26
Hi 
my setting is - one external IP, two machines in LAN one of them firewall and DNS (connected directly to internet), the other web server (connected through the first machine)
- Firewall and DNS computer is ubuntu

Now...
I have a bind server running on ubuntu with 192.168.1.0/24 network , www being .2, ns being .1 The thing is as I understand it I cant have 192.168.1.0/24 addresses on a bind server that is supposed to serve queries from  the internet?! Do I have to have external ip for every single host I want to be accessible from outside? 

thanks

---

### Post by HermanAB on 2011-01-26
Howdy,

If every host provides the same service on the same Berkeley port, then you need an IP address per host.  If the hosts provide different services or can be tweaked to use different ports, then you only need one IP address. You have 65000 ports per IP address - try to use them.

---

### Post by koszta on 2011-01-26
> **HermanAB said:**
> Howdy,

If every host provides the same service on the same Berkeley port, then you need an IP address per host.  If the hosts provide different services or can be tweaked to use different ports, then you only need one IP address. You have 65000 ports per IP address - try to use them.

Yeah great that is what I am trying to do...

Is my zone file correct?

myzone.com.db file

myzone.com. IN SOA leonardo.mydomain.com. hostmaster.mydomain.com. (
    200709131 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)

mydomain.com. IN NS leonardo.mydomain.com.
mydomain.com. IN MX 10 leonardo.mydomain.com.
; Set an alias (canonical name) for zenon
www IN CNAME zenon.mydomain.com.
; Set CNAME for mailserver on leonardo
mail IN CNAME leonardo.mydomain.com.

; Set the address for localhost.mydomain.lan
localhost    IN A 127.0.0.1
; Set the hostnames 
leonardo     IN A 192.168.1.1
zenon        IN A 192.168.1.2
mydomain.com.  IN A 192.168.1.2

now /etc/bind/zones/rev.1.168.192.in-addr.arpa

; IP Address-to-Host DNS Pointers for 192.168.1.0 subnet
@ IN SOA leonardo.mydomain.com. hostmaster.mydomain.com. (
    200709131 ; serial
    8H ; refresh
    4H ; retry
    4W ; expire
    1D ; minimum
)
; define the authoritative name server
	IN NS leonardo.mydomain.com.
	IN MX 1 leonardo.mydomain.com.
; our hosts
1 	IN PTR mydomain.com.
2        IN PTR zenon.mydomain.com.



==> I can access it all without a problem localy but nothing of it from the internet...

---

