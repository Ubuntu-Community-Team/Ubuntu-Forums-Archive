---
title: "Seeking doc to set up mail server"
date: 2009-04-03
forum: Server Platforms
---

### Post by satimis on 2009-04-03
Hi folks,


OpenVZ
host - Ubuntu 8.04 workstation
guest (VE) - ubuntu-8.04-i386-minimal (platform for mail server)


I have been searching a while for documentation to build a mail server running postfix on the guest.  I found follow;

The Perfect Server - Ubuntu Hardy Heron (Ubuntu 8.04 LTS Server)
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)


but NOT from Ubuntu Documentation.  Can any folk help me to find the URL linking to a guide on Ubuntu Doc Wiki for my use.  TIA


B.R.
satimis

---

### Post by hyper_ch on 2009-04-03
why ubuntu doc wiki? That link above is good.

---

### Post by volkswagner on 2009-04-03
I am guessing you already saw [this]("https://help.ubuntu.com/8.04/serverguide/C/email-services.html").

Postfix is not specific to Ubuntu or Debian.  I have followed the [Flurdy]("http://flurdy.com/docs/postfix/") how to which I find comprehensive and works.  Set aside some time because it is involved.

I really appreciated the virtual domains, since I needed to run mail for multiple domains.

---

### Post by vpsville on 2009-04-03
If you're running OpenVZ you might consider just installing the free LxAdmin control panel, or Webmin.

---

### Post by satimis on 2009-04-03
> **hyper_ch said:**
> why ubuntu doc wiki? That link above is good.
Hi hyper_ch,

I just try to find out whether there are documents on Ubuntu wiki for comparison.

I have been following that guide installing mail servers on a Xen box running Debian Etch as OS.  It worked for me.

B.R.
satimis

---

### Post by satimis on 2009-04-03
Hi volkswagner,


Thanks for your advice and links.
 
> **volkswagner said:**
> I am guessing you already saw [this]("https://help.ubuntu.com/8.04/serverguide/C/email-services.html").

I suppose I came across this guide before.  However on my recent search I can't find it.


> 
Postfix is not specific to Ubuntu or Debian.  I have followed the [Flurdy]("http://flurdy.com/docs/postfix/") how to which I find comprehensive and works.  Set aside some time because it is involved.

I really appreciated the virtual domains, since I needed to run mail for multiple domains.
I have followed that guide sometime ago.  It also worked for me.


Previously I succeeded installing virtual domains on a Xen box running Debian Etch as OS.  All domains point to ONE public IP.  Each domain has its own mail server on the Xen box.  I made use of a mail server for routing.  Roaming clients can login remotely to their own servers download mails but they can't send mail via their own mail servers remotely.  All roaming clients must send mails via the routing mail server.  That is NOT my intent.


Now I'm prepared to make another round running OpenVZ as virtualization software and Ubuntu 8.04 as OS on all guests (VE).  I'm trying to solve the last but ONLY problem which remained unsolved on the Xen box previously.


B.R.
satimis

---

### Post by satimis on 2009-04-03
> **vpsville said:**
> If you're running OpenVZ you might consider just installing the free LxAdmin control panel, or Webmin.
Hi vpsville,

I did run/install webmin before.  However I never used it.  I used ssh access the mail servers for configuration and installing new package all the time.

LxAdmin is new to me.  I'll take a look on it.  Thanks


Ah, one important thing I almost forget.  I'm not sure whether OpenVZ supports update globally, i.e. updating the host all guests (VE) will be updated automatically.  I'm not sure whether OpenVZ OR Vserver has this feature.  I ran this feature before.  Any folk has an idea?


B.R.
satimis

---

### Post by Cheesemill on 2009-04-03
I've just used this guide to set up my mailserver:

[http://workaround.org/articles/ispmail-etch/]("http://workaround.org/articles/ispmail-etch/")
I'd previously tried the Flurdy guide but kept getting errors, this one worked first time.

Cheesemill

---

### Post by satimis on 2009-04-04
> **Cheesemill said:**
> I've just used this guide to set up my mailserver:

[http://workaround.org/articles/ispmail-etch/]("http://workaround.org/articles/ispmail-etch/")
I'd previously tried the Flurdy guide but kept getting errors, this one worked first time.

Cheesemill
Hi Cheesemill,


Thanks for your URL.


I have been following this document to set up mail server.  It worked for me.  Actually I followed many documents previously, NOT only one document, to set up the mail servers on the Xen box, altogether >20 mail servers running there.  

The difficulty faced by me was ONE public IP connected to the Xen box which problem I have been trying hard to solve.  If running multiple IP addresses (each domain has its own public IP) I have NO problem at all.

First I ran MySQL to forward the domains to their own mail servers on the Xen box.  It worked.  To overcome the problem allowing roaming mail clients to download and to send mails via their own server I ran "perdition" replacing MySQL.  Then the whole Xen box worked nicely leaving the ONLY problem remained "to allow roaming clients sending mails via their own mail servers instead of via the routing mail server".

Now I'm starting another round.  I have been trying hard searching relevant document on Ubuntu wiki, if any, to solve my ONLY problem remained previiously.


B.R.
satimis

---

### Post by satimis on 2009-04-07
> **vpsville said:**
> If you're running OpenVZ you might consider just installing the free LxAdmin control panel, or Webmin.
Hi vpsville,


As curiosity just browsed the website of LxAdmin;

[http://lxlabs.com/](http://lxlabs.com/)

Are LxAdmin and HyperVM free software?  If they are NOT free they can be download?  I can't resolve.

Any advice?  TIA


B.R.
satimis

---

