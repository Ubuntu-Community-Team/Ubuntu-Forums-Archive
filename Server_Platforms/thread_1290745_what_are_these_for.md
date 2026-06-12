---
title: "what are these for?"
date: 2009-10-13
forum: Server Platforms
---

### Post by oospill on 2009-10-13
Hi.  I've got an older desktop computer running ubuntu server, and I've been having fun with SSH, LAMP services, etc..  but I'm just curious, what would I do with these services: DNS server, mail server, tomcat, and the virtual machine host?

what are these? and why or why not would I want to fiddle with them?

thanks!!
oospill

---

### Post by tgalati4 on 2009-10-13
DNS is the domain name server.  You normally get your web addresses decoded by your ISP.  You can run your own DNS server, which can be faster than what your ISP provides.  For instance [www.google.com](www.google.com) points to one of several IP addresses depending on your local area.

```

ping www.google.com

```

Control-C to quit

The number xx.xx.xx.xx assigned while pinging [www.google.com](www.google.com) is provided by DNS.

Mail Server allows you to send and accept mail.  Basically, you become your own post office.  You probably get your email from your ISP or from hotmail, aol, gmail, etc.  All of these services run some sort of mail server.  You can run your own if you wish.

```

apt-cache search tomcat

```

tomcat is a mini server (servlet) that parses and feeds java pages.  This is helpful if your website has java elements that need to be processed and served.  For instance if you are running an on-line shop, you would probably have a java-based shopping cart and check-out routines.

virtual machine host allows you to run Windows or BSD, or another flavor of linux inside of your current Ubuntu server.  This is handy because if Windows crashes, it only shuts down it's own process without taking down the whole system.  It's common to run several operating systems on high-end server hardware to consolidate several servers into one to save space and energy.

Most home users use virtual machines to checkout the latest version of ubuntu without messing up their current installation.  It's also used to play games in Windows or to run some specific Windows software.  It eliminates having to dual boot.

---

### Post by Lori700698 on 2009-10-13
Congratulations on your newish system!

DNS is for dynamic name server, this is for hosting your own website.  Interesting to learn, my IP only changes once about every 6 months, I can handle updating it, if your internet IP changes often it would be a hassle.  In this case it would be better to host elsewhere and set up a dyndns that updates automatically.

Mail server, look at Citadel....very easy to set up and again lots of fun learning it.

Apache is your virtual server for websites, it configures your sites by name instead of IP's.  I have 2 sites and 1 IP address, the [www.domainname.com](www.domainname.com) is resolved here with this applications.

I hope you enjoy your system..and if your into music, check out Jinzora, awesome music server with a website application.

Lori

---

### Post by oospill on 2009-10-13
thanks for the posts!!

yeah, I set up lamp, cause it had apache, and I successfully setup a little webpage.  kinda fun..  learning php.  now the mail server, if I get my own dot.com, I could put up a mail server with addresses that are @mydot.com ??  that'd be kinda fun.

now the virtual machine host..  is this the same kind of thing as VMWare but free?  that'd be fun, too..

oospill

---

