---
title: "HP lights out - is anyone using it"
date: 2006-10-23
forum: Server Platforms
---

### Post by huggy77 on 2006-10-23
I was wondering if anyone is using HP's lights out card?  Is it worth purchasing for my webserver...

---

### Post by bsussman on 2006-10-23
> **huggy77 said:**
> I was wondering if anyone is using HP's lights out card?  Is it worth purchasing for my webserver...

I am involved with a 300 server server farm - every machine has ilo.

It does allow you complete control over the machine, without going through the operating system.

You need to compare the hourly costs of physical access to the machine, how often you have an incident that requires physical intervention or access when the os is inoperable against the board and communication costs.

Is it worth purchasing for your web server?

(  funny - that's the question YOU asked ;) )

---

### Post by huggy77 on 2006-10-23
i can get the card for less than 2oo bucks - i am starting to host my uncles site - he brought me in as his total it solution... i am more of a programmer but i love linux... i converted his 2 servers over to linux the first week....

What would you recommend on my webserver...
was going to go with firestarter as the firewall
apache for the web
mysql for db...

DO you know of a good article on ubuntu hardening?

Thanks for taking the time to answer my NOOB questions...

---

### Post by bsussman on 2006-10-23
Our public servers run specially built/hardened OSs.

Clearly it would be possible to harden an ubuntu system to make it right for public webserving but I am no expert.

You need very expert advice and configuration before exposing a highly visible machine to the public - and if it is a web server and not highly visible, why bother :)

Good luck.

---

