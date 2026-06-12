---
title: "PDC Setup"
date: 2006-11-29
forum: Server Platforms
---

### Post by cj.smith on 2006-11-29
Hi guys,

Im very new to linux, im quite a well experienced Microsoft engineer (MCSE). I have always kept a keen eye on linux developments and i now have to impliment it at work. We need basically all the features of a 'Windows 2003' Primary Domain Controller. e.g. Active directory ( openLDAP? )for user/group managment, DNS, DHCP, print and file sharing. I think i need samba AND LDAP?

I have been through most of the documentation on the ubuntu site but im still not 100%, Does anyone know of any good resources, there seems to be a lack of an IDIOT GUIDE!! And to clarify, im not looking for someone to 'Do all the work for me', Im just looking for some advise and resources

Thanks

---

### Post by Beernut on 2006-11-30
Here is an excellent guide there are example configurations for all different setups even LDAP.  [http://us3.samba.org/samba/docs/man/Samba-Guide/](http://us3.samba.org/samba/docs/man/Samba-Guide/)

I bought this book quite a while ago and found it very helpful the cool thing is you can read the entire book online for free.

[http://us3.samba.org/samba/docs/using_samba/toc.html](http://us3.samba.org/samba/docs/using_samba/toc.html)

Note:  The third edition of this book is supposed to be coming out in January of 2007 and I am sure it will be available in an online format also.

---

### Post by sgeberl on 2006-12-02
Maybe this is a good source:

[http://home.subnet.at/~max/ldap/#pam-clients-vs-server](http://home.subnet.at/~max/ldap/#pam-clients-vs-server)

I myself only managed to configure a not encrypted connection so I don't know if this is working.

---

