---
title: "Can't Configure Sub Domain DNS in BIND"
date: 2012-06-26
forum: Server Platforms
---

### Post by unemployment on 2012-06-26
I can't figure out how to set up sub domains in bind.  My DNS keeps failings when I do a dig.  Any suggestions?  

Here is the dig output:

root@ve:/etc/bind# dig dev.jasonbiondo.com

; <<>> DiG 9.7.3 <<>> dev.jasonbiondo.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 414
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;dev.jasonbiondo.com.        IN    A

;; AUTHORITY SECTION:
jasonbiondo.com.    2439    IN    SOA    ns09.domaincontrol.com. dns.jomax.net. 2012062603 28800 7200 604800 3600

;; Query time: 73 msec
;; SERVER: 64.207.128.222#53(64.207.128.222)
;; WHEN: Tue Jun 26 19:28:18 2012
;; MSG SIZE  rcvd: 105

Here is my zones file

// replace example.com with your domain name. do not forget the . after the domain name!
// Also, replace ns1 with the name of your DNS server
jasonbiondo.com.      IN      SOA     ns1.jasonbiondo.com. dev.jasonbiondo.com. (
// Do not modify the following lines!
                                                        2006081401
                                                        28800
                                                        3600
                                                        604800
                                                        38400
 )

// Replace the following line as necessary:
// ns1 = DNS Server name
// mta = mail server name
// example.com = domain name
jasonbiondo.com.      IN      NS              ns1.jasonbiondo.com.
jasonbiondo.com.      IN      NS              ns2.jasonbiondo.com.
jasonbiondo.com.      IN      MX     10       mail.jasonbiondo.com.

// Replace the IP address with the right IP addresses.
www              IN      A       216.70.***.**
mta              IN      A       216.70.***.**
ns1              IN      A       216.70.***.**
ns2              IN      A       216.70.***.**
dev              IN      A       216.70.***.**


WHERE 216.70.***.** is the IP of my server.

Any thoughts?

---

### Post by SeijiSensei on 2012-06-27
As you show yourself, the authoritative nameserver for jasonbiondo.com is ns09.domaincontrol.com.  Until you change the records at your registrar, the records there will continue to be used, not the ones in your name server.  You need to tell the registrar that your server is now authoritative for the domain.

If you want to set things up so that dev.jasonbiondo.com is a subdomain, then at the registrar add an NS record like this:

```

dev    IN    NS   ns1.jasonbiondo.com.
       IN    NS   ns2.jasonbiondo.com.

ns1    IN    A    1.2.3.4
ns2    IN    A    2.3.4.5

```

Now you can give hosts names like host1.dev.jasonbiondo.com and maintain their records on your nameserver.

---

### Post by unemployment on 2012-06-27
> **SeijiSensei said:**
> As you show yourself, the authoritative nameserver for jasonbiondo.com is ns09.domaincontrol.com.  Until you change the records at your registrar, the records there will continue to be used, not the ones in your name server.  You need to tell the registrar that your server is now authoritative for the domain.

If you want to set things up so that dev.jasonbiondo.com is a subdomain, then at the registrar add an NS record like this:

```

dev    IN    NS   ns1.jasonbiondo.com.
       IN    NS   ns2.jasonbiondo.com.

ns1    IN    A    1.2.3.4
ns2    IN    A    2.3.4.5

```Now you can give hosts names like host1.dev.jasonbiondo.com and maintain their records on your nameserver.

When I specific my nameserver:

ns1.jasonbiondo.com.
ns2.jasonbiondo.com.

on Godaddy and ran a dig I got a server error.  

In godaddy's host summary section I added both nameservers listed above with my servers ip address.  

Did I not understand you correctly or is something else off?

When I dig jasonbiondo.com I get no errors.  It's only when I dig the subdomain.

---

