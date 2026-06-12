---
title: "1and1 domain point to my server?"
date: 2011-10-06
forum: Server Platforms
---

### Post by Spardra on 2011-10-06
Hello, I am new to the whole hosting a server from home for something other than testing purposes. But anyways, I am using Ubuntu 11.10 on an old upgraded Dell Poweredge 2800. I am trying to point my domain names(4 of them all pointing to the same site) registered with 1and1.com to my web server at my homes static ip address. I have tried using bind9 but don't think I am doing it correctly because it hasn't worked yet... Are there any alternatives to bind9 that I could to point my domain to my server? I can't edit much from the control panel on my domains control panel. Any thoughts would be really appreciated thanks!

---

### Post by Doug S on 2011-10-07
Note before: I am not an expert on this subject, and I only reply because it has been 14 hours and nobody else did.
There is a good thread on why a public facing DNS is not a good idea here: [http://ubuntuforums.org/showthread.php?t=1787730](http://ubuntuforums.org/showthread.php?t=1787730)
I run a bind9 based DNS, but only for my local LAN.
For my public facing domain name and static IP addresses: My ISP told me the two name servers to list with my domian name registrar, which I was able to enter myself in my account; My ISP added the"A" and "MX" and "CNAME" and such records to those name servers.

---

### Post by Jonathan L on 2011-10-07
> **Spardra said:**
> Hello, I am new to the whole hosting a server from home for something other than testing purposes. But anyways, I am using Ubuntu 11.10 on an old upgraded Dell Poweredge 2800. I am trying to point my domain names(4 of them all pointing to the same site) registered with 1and1.com to my web server at my homes static ip address. I have tried using bind9 but don't think I am doing it correctly because it hasn't worked yet... Are there any alternatives to bind9 that I could to point my domain to my server? I can't edit much from the control panel on my domains control panel. Any thoughts would be really appreciated thanks!

Hi Spardra 


If what want is to run a web server, you don't need to run BIND at all.  You add 'A' (address) records to your domain's information at 1&1.  You'd normally do this from the control panel they give you on their web site.

```
www.yourdomain1.com. A 1.2.3.4
www.yourdomain2.com. A 1.2.3.4
www.yourdomain3.com. A 1.2.3.4
```where 1.2.3.4 is your real static IP address and yourdomain1 etc are your domain names.

Normally you'd run apache2 with name-based virtual hosts, and have the router direct port 80 to the internal adress of your web server host.  (Ask again if this sentence is mysterious.)

The domain server runs at 1&1, the web server runs at your house.   This is the sensible way to do it: don't run your own domain server unless you have a real reason to.  But certainly run a webserver just for the fun of it or to get some real sites running.  Watch out, as everyone will tell you, about getting hacked, too much bandwidth, and all the rest: but certainly, have a go.

Hope that helps.

Kind regards
Jonathan.

---

### Post by bbqroast on 2011-10-08
Web servers can use surprisingly little bandwidth!
It's just a matter of telling your register to point your domain name to your IP :).

---

