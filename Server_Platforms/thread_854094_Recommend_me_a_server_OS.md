---
title: "Recommend me a server OS"
date: 2008-07-09
forum: Server Platforms
---

### Post by ukripper on 2008-07-09
Ok guys i need your help.

i am going to build a web server apache php mysql proftp for production environment -
Athlon XP 1.3ghz
Software RAID1 (mirror set only) - 2IDE drives 10Gb each (as motherboard is not capable of SATA)
750MB SDRAM
1 DVD ROM.

i am currently running 7.10 server in testing environment without RAID array as a file server.

My issue is I can't decide Debian etch server or ubuntu Hardy server LTS for production.

What you guys recommend with above spec of a server, would this be suffucient as a webserver running php/mysql based site filling forms and userlogins from customers or do I need to look for more specific server series?

i don't require GUI for my server, i am happy without it.

thanks in advance!
:)

---

### Post by windependence on 2008-07-09
FreeBSD hands down. It is much lighter for your older hardware and scales to 16 processors.

Some great forums here:

[http://daemonforums.org/index.php](http://daemonforums.org/index.php)

Hey, you asked for a recommendation. :)

-Tim

---

### Post by hagen00 on 2008-07-09
depends what technology you require. We need PHP 5.2.* and MySQL5 so we use Ubuntu servers and not Debian or FreeBSD since we can just install that stuff from apt. 

Ubuntu all the way

---

### Post by ukripper on 2008-07-09
> **windependence said:**
> FreeBSD hands down. It is much lighter for your older hardware and scales to 16 processors.

Some great forums here:

[http://daemonforums.org/index.php](http://daemonforums.org/index.php)

Hey, you asked for a recommendation. :)

-Tim

Thanks for recomendation, but i asked for debian or ubuntu specifically.:)

---

### Post by ukripper on 2008-07-09
> **hagen00 said:**
> depends what technology you require. We need PHP 5.2.* and MySQL5 so we use Ubuntu servers and not Debian or FreeBSD since we can just install that stuff from apt. 

Ubuntu all the way

i am using php5 and mysql5 to develop my website so i guess Ubuntu server is looking more appropriate here? And I would like to stick with apt. 

thanks.

---

### Post by windependence on 2008-07-09
> **hagen00 said:**
> depends what technology you require. We need PHP 5.2.* and MySQL5 so we use Ubuntu servers and not Debian or FreeBSD since we can just install that stuff from apt. 

Ubuntu all the way

Uhhh...both of these are easily installed on FreeBSD. Of course, you are free to use what you want. If you have tunnel vision, you mau never see the rich oprions available to you.

-Tim

---

### Post by windependence on 2008-07-09
> **ukripper said:**
> Thanks for recomendation, but i asked for debian or ubuntu specifically.:)

OK, if I HAVE to pick between the two for your hardware, I would say Debian. It will run better on your older hardware.

-Tim

---

