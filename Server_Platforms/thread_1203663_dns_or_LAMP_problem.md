---
title: "dns or LAMP problem"
date: 2009-07-03
forum: Server Platforms
---

### Post by zeek333 on 2009-07-03
i have a fqdn registred in 123-reg.com  example.com

on ubuntu 9.04 server i configured dns server from  [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)  and looks like its working

then i puted on LAMP configure virtual host and now i have a problems when i type from local network [http://www.example.com](http://www.example.com) = OK but [http://example.com](http://example.com) = NO OK (Connection Interrupted) and from outside both addreses show Connection Interrupted???

does anyone know whre is the problem? 

p.s i have router but there i forwarded my server ip and ports

---

### Post by aesis05401 on 2009-07-03
Hello,

If you are functioning properly from the LAN when using the FQDN then that is a good start.

The incomplete address may not return results based on a couple of things like whether you are forwarding unresolvable requests to an external DNS provider, whether your browser is set to utilize 'domain guessing' or 'internet keywords,' to attempt resolution of partial addresses.

If you are set to forward unresolvable requests to another authority, then I believe this would take place before your browser had the opportunity to auto correct.

As to why you are not showing up from the WAN, have you allowed proper time for your DNS info to propogate across name servers?  It used to take days for this to happen, maybe it is less time now.

---

### Post by zeek333 on 2009-07-04
so what i should look for?  i noticed 
that in 123-reg.com i need to add NS1.example.com NS2.example.com and Ip of it (123.123.123.123) wich is my provider IP
but my DNS and LAMP is setup on 10.0.0.125 and now when i ping example.com it shows me 10.0.0.125  

i think i mist something but what ?

---

### Post by zeek333 on 2009-07-05
ok i checked my web form outside and it works with 123.123.123.123 (provider ip) but don't work when i type [www.example.com](www.example.com), when i ping [www.example.com](www.example.com) it shows me 10.0.0.125 (ip which i setup for my dns) 

please help!!!

---

