---
title: "Cannot access regular http, only https"
date: 2015-02-20
forum: Security
---

### Post by Kaaiman on 2015-02-20
I'm using Ubuntu 14.04 LTS on my home computer I have 2 accounts: a regular account to do all my stuff on and an account to do my work on, with some restrictions to avoid procrastination (e.g. no access to games). I have had Nanny (former GNOME Nanny) installed, but this seemed to have things screwed up a bit.

On the regular account I can access both http and https without any problems, but on my work account I can only access https.

Curl output:
curl -I [http://randomsite.com/](http://randomsite.com/) gives
curl: (51) SSL: no alternative certificate subject name matches target host name [http://randomsite.com/](http://randomsite.com/)

Wget output:
wget [http://randomsite.com/](http://randomsite.com/) finds the host, but gives this error:
ERROR: no certificate subject alternative name matches requested host name '&#8216;randomsite.com&#8217;'.
To connect to randomsite.com insecurely, use `--no-check-certificate'.

When I bypass the SSL check with curl -k or wget --no-check-certificate, the output is normal. The same goes for accessing https sites.

How can I enable the access to http sites again? On neither account I'm using proxies, VPN or whatsoever.

---

### Post by haplorrhine on 2015-02-20
You could check the integrity of /etc/services

> http		80/tcp		www		# WorldWideWeb HTTP
http		80/udp				# HyperText Transfer


---

### Post by Kaaiman on 2015-02-27
Seems to be nothing wrong with /etc/services:

> http		80/tcp		www		# WorldWideWeb HTTP
http		80/udp				# HyperText Transfer Protocol
and
> https		443/tcp				# http protocol over TLS/SSL
https		443/udp

---

