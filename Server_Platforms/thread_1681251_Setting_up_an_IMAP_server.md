---
title: "Setting up an IMAP server"
date: 2011-02-03
forum: Server Platforms
---

### Post by DarthScape on 2011-02-03
Currently I have a VPS that only has 512mb of memory and 10gb disk space and I want to set it up as a mail server. I specifically need it to be IMAP and it will need to be able to draw in mail from other IMAP or POP servers as well. Will only be having about 4 users. My question is: what distro should I use for it? I originally wanted to use Ubuntu but it seem to use quite a bit of memory. They pretty much give me any choice of distro. Second, can anyone tell me the best IMAP server to use? Courier, Dovecot, UW IMAP? Did some google searches and it seems like Dovecot may be my best bet. Also, it has to run on some *non-standard* ports for IMAP and SMTP. Would appreciate any help. Currently the server is not running anything, so if anyone wants to SSH into it to help me they can; I can format whenever I need. Already have CNAME, A, and MX records set.

Thanks in advance! ;)

---

### Post by HermanAB on 2011-02-04
Howdy,

Firstly, 500MB RAM may not enough for more than a few email users.  Mail servers are memory hogs.

Second, if you want to learn how a mail system works, then by all means, go the Lego way and install all the services separately.  however, if you just want a fully functional mail server that works in no time, look at Citadel.  It installs in about 20 minutes and does everything and every mail protocol.

---

### Post by SeijiSensei on 2011-02-04
> **DarthScape said:**
> Currently I have a VPS that only has 512mb of memory and 10gb disk space and I want to set it up as a mail server. I specifically need it to be IMAP and it will need to be able to draw in mail from other IMAP or POP servers as well. Will only be having about 4 users. My question is: what distro should I use for it? Second, can anyone tell me the best IMAP server to use? Courier, Dovecot, UW IMAP?  Also, it has to run on some *non-standard* ports for IMAP and SMTP.

You shouldn't have a problem serving four users with that machine.

I'd go with either Ubuntu Server 10.04LTE or CentOS 5.5.  If you're more comfortable with the Debian/Ubuntu way of doing things, take the former; if you're more comfortable in a RedHat environment, use CentOS.  If you're using a virtual server, it won't be running a GUI, so you won't have all that overhead.  You might want to consider Debian as an alternative to Ubuntu.

Dovecot is the dominant choice for an IMAP/POP server.  You can tell it to use non-standard ports in its configuration file.

To collect mail from other servers, use the [fetchmail]("http://fetchmail.berlios.de/") program.  It is in all the distros.

---

