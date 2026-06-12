---
title: "Can not view domain names internally."
date: 2008-08-14
forum: Server Platforms
---

### Post by M374llic4 on 2008-08-14
Hello,
    I am running ubuntu as a web server using webmin to manage everything. Works great minus one issue. I can not hit the domain names internally. Externally everything works fine, but I have to use the IP to hit the servers. Now, our primary domain controller is a server 2008 box now (just upgraded from 2003) but it has never worked. 

Any ideas what may be up, or what I need to do? IF you need more info let me know what you need.

Thanks,
Dan

---

### Post by rickyjones on 2008-08-14
> **M374llic4 said:**
> Hello,
    I am running ubuntu as a web server using webmin to manage everything. Works great minus one issue. I can not hit the domain names internally. Externally everything works fine, but I have to use the IP to hit the servers. Now, our primary domain controller is a server 2008 box now (just upgraded from 2003) but it has never worked. 

Any ideas what may be up, or what I need to do? IF you need more info let me know what you need.

Thanks,
Dan

What is the internal domain name?
Is your /etc/resolv.conf configured with this domain as the domain suffix?
Can other Active Directory clients ping the internal hosts by name?

When you say "it has never worked" what are you referring to, DNS? How is DNS configured? 

I hope this starts you in the right direction. :-)

Sincerely,
Richard

---

### Post by M374llic4 on 2008-08-14
DNS has worked just fine for everything windows. no one internally on any subnet can ping the domains hosted on the linux box internally. 

There are lots of sites that we host on the server, one being. itstechsupport.com well, if you go to it externally, it works fine, if you type that in internally, nothing. 

 You have to go to the ip/itstechsupport.com/public_html to view it. but that causes problems because of the software the sites running.

---

### Post by rickyjones on 2008-08-14
> **M374llic4 said:**
> DNS has worked just fine for everything windows. no one internally on any subnet can ping the domains hosted on the linux box internally. 

There are lots of sites that we host on the server, one being. itstechsupport.com well, if you go to it externally, it works fine, if you type that in internally, nothing. 

 You have to go to the ip/itstechsupport.com/public_html to view it. but that causes problems because of the software the sites running.

Sounds like your internal clients are looking to your Windows DNS server for resolution, correct? Have you added the extra domains (itstechsupport.com) to your DNS server as Forward zones? 

-Richard

---

### Post by M374llic4 on 2008-08-14
Hey bud, thanks for the help! Finally got it working :) I have been so busy, I had not had time to mess with it. So after 8 months of IP's I am happy to use the name : P

---

