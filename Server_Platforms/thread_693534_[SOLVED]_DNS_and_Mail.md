---
title: "[SOLVED] DNS and Mail"
date: 2008-02-11
forum: Server Platforms
---

### Post by tompickles on 2008-02-11
I am playing about with servers in a virtual machine with Ubuntu Server as my base. Basically, LAMP server, which is really easy to set up - tried lots of different methods for installing it - in the ubuntu installer itself, and with apt-get afterwards.

Could someone please explain to me:

1) DNS server - what is it, do I need one, and how to set one up anyway!

2) Mail server - as 1)

Thank you for your expertise!

---

### Post by twistedtwig on 2008-02-11
I would start with google my self...

[http://www.google.co.uk/search?source=ig&hl=en&rlz=&q=what+is+a+dns+server&btnG=Google+Search&meta=](http://www.google.co.uk/search?source=ig&hl=en&rlz=&q=what+is+a+dns+server&btnG=Google+Search&meta=)

[http://www.google.co.uk/search?num=100&hl=en&safe=off&q=what+is+a+mail+server&btnG=Search&meta=](http://www.google.co.uk/search?num=100&hl=en&safe=off&q=what+is+a+mail+server&btnG=Search&meta=)

---

### Post by tompickles on 2008-02-11
Ok, i get that a DNS server translates my IP into a memerable name - so, for free, can I do that myself?

Also, a mail server i get that it allows you to send e-mails to you and other people on different networks - so how do i set one up?!

---

### Post by faulkes on 2008-02-11
> **tompickles said:**
> Ok, i get that a DNS server translates my IP into a memerable name - so, for free, can I do that myself?

You first need to register a domain name.  Many registrars will also host DNS for you for free after registering the domain.  If you want to host the domain yourself (i.e. run bind), you need a static IP and preferably an off-network DNS as a secondary.  When you register the domain, you tell it that the static IP is the DNS server for that domain.

You could also investigate using a Dynamic DNS provider.

You would then need to configure DNS (aka bind) to have the appropriate records for your domain.

See the DNS section at 

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

or 

[https://help.ubuntu.com/7.10/server/C/dns.html](https://help.ubuntu.com/7.10/server/C/dns.html)

> 
Also, a mail server i get that it allows you to send e-mails to you and other people on different networks - so how do i set one up?!

See [https://help.ubuntu.com/7.10/server/C/email-services.html](https://help.ubuntu.com/7.10/server/C/email-services.html)

Postfix is the default server install (but not the only one).

Faulkes

---

