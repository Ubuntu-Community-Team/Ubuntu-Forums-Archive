---
title: "How do I set up my email server?"
date: 2011-03-15
forum: Server Platforms
---

### Post by jhsu802701 on 2011-03-15
This is my first time ever working with a mail server.  Thus, I don't know what I'm doing, but I'm trying to learn.  
  All I'm trying to do right now is send and receive email messages through my free DynDNS account. Let's say it's subdomain1.dyndns-free.com .


  The OS is Debian Lenny.  The mail server is exim4.


  Let's say that the host name listed in my /etc/hosts file is subdomain2.domain.com .


  I have been able to run the exim4 configuration script by entering "dpkg-reconfigure exim4-config". However, I don't know what I'm supposed to enter for all those fields I'm asked about. If I'm even slightly wrong on just one thing, my system won't work properly.


  Do I need an MX hostname?  There are so many unknowns that I don't know where to begin.
  What do I need to do in my DynDNS account?


  Once I have done that, what parameters do I need to enter when I run "dpkg-reconfigure exim4-config"?  The parameters are: 



1. General type of mail configuration 



2. System mail name 



3. IP-addresses to listen on for incoming SMTP connections 



4. Other destinations for which mail is accepted 



5. Domains to relay mail for 



6. Machines to relay mail for 



7. IP address or host name of the outgoing smarthost 



8. Hide local mail name in outgoing mail? 



9. Keep number of DNS-queries minimal (Dial-on-Demand)? 



 10. Delivery method for local mail 



11. Split configuration into small files?

---

