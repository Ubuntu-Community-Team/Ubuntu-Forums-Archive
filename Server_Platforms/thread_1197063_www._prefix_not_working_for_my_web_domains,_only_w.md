---
title: "www. prefix not working for my web domains, only works without www.mydomainname.."
date: 2009-06-25
forum: Server Platforms
---

### Post by audaciousweb on 2009-06-25
I set up an apache mysql server on my ubuntu cloud server its working fine except that when I type in [www.mydomainname.com]("http://www.mydomainname.com") it does not work but only works directly with [http://mydomainname.com](http://mydomainname.com)  

As I understand this has to do with the DNS server so I am wondering if anyone can point me in the right direction as to what I need to install on my Ubuntu server to set it up so it is accessible through [www..]("http://www.."). or is this something that has to do with my domain name registrar or cloud hosting company?

Thanks for any advice as I'm kind of lost when it comes to DNS issues.

---

### Post by R.Bucky on 2009-06-25
Take a look at your A record and make sure that you have a www pointed at your ip

---

### Post by raisinglinux on 2009-06-25
Are you hosting your own dns or are you using your hosts control panel?
 
 
*// Replace the IP address with the right IP addresses.*
www              IN      A       192.168.0.2

 
 
 
-----------------------------
[Raising Linux . com]("http://raisinglinux.com/blog")

---

### Post by audaciousweb on 2009-06-25
Thanks for the replies, yeah I think its something I can do through the cloud host's control panel, I need to just add the A record as you suggested.

---

