---
title: "critique dns zone file"
date: 2014-09-10
forum: Server Platforms
---

### Post by joeaverage2 on 2014-09-10
Thanks for reading.
Bind 9

We're moving an app from a server in our domain to a server hosted by the vendor in their domain.  Below is the vendors note on what DNS changes need to made.
I'm asking for a critique of this zone file to make sure I've got it right.  In particular do I need to comment out the lines for the A records??? 

NOTE:  Vendor also provides an xxx.com domain name for your business (domain.xxx.com) but we recommend you keep your existing hostname and alter your DNS entry to point to the new domain name.  We strongly recommend you CNAME alias [www.mydomain.org]("http://www.mydomain.org") and mydomain.org to vendor_domain.xxx.com.  And *.[www.mydomain.org]("http://www.mydomain.org") and  *.mydomain.org  to *.vendor_domain.xxx.com rather than pointing your DNS to the new IP address.  

; NAMED Configuration for [www.mydomain.org]("http://www.mydomain.org") Domain
 ;
$TTL 6h
$ORIGIN domain.org.
@    IN    SOA    dns_server.domain.org. postmaster.domain.org. (
                2014090902    ; serial
                3h          ; refresh
                1h          ; retry
                1w          ; expire
                1d )         ; minimum
;
;name servers
;
        IN    NS    dns_server.domain.org.
        IN    NS    ns1.secondarynameservers.net.
        IN    NS    ns2.secondarynameservers.net.
        IN    NS    ns3.secondarynameservers.net.
;

        IN    A    192.168.1.55 
;

        IN    MX 5    mailserver.mydomain.org.
;
;
;comment out this line the day of the switch?
www        IN    A    192.168.1.55 
        
;comment out this line the day of the switch?
*.[www.domain.org]("http://www.domain.org"). IN    A    192.168.1.55 

;    Aliases
;uncomment these lines the day of the switch. 

;mydomain.org       IN CNAME   vendor_domain.xxx.com.
;[www.mydomain.org]("http://www.mydomain.org")   IN CNAME   vendor_domain.xxx.com.
;*.mydomain.org     IN CNAME *.vendor_domain.xxx.com.
;*.[www.mydomain.org]("http://www.mydomain.org") IN CNAME *.vendor_domain.xxx.com.

---

### Post by Frogs Hair on 2014-09-10
Hello and Welcome

Moved to ***&#8203;Server Platforms***

---

### Post by joeaverage2 on 2014-09-11
skip it I've got it sorted out.

---

### Post by joeaverage2 on 2014-09-11
Howdy and thanks for moving it to the right group.

---

