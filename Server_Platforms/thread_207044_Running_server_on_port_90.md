---
title: "Running server on port 90?"
date: 2006-07-01
forum: Server Platforms
---

### Post by ExMachina on 2006-07-01
Beacause for some odd reason all ( gaim,and trillain) seem to hijack port 80 i though i coudl just run apache on 90.

I would like to do HOW to switch everything over to 90?
Do DNS' usually point to 80? does it matter?
if i forward port 90 to my server will it work?

Im jsut worried i will mess my server up.

PM / Post wiht tips and advice.

---

### Post by hda on 2006-07-01
DNS has nothing to do with ports. Just edit your /etc/apache2/ports.conf file to include 'listen 90' and you're fine. Of course, if you want to point your browser to this apache you have to include the port number in the URL, like:

[http://www.yourserver.tld:90/](http://www.yourserver.tld:90/)

_hda_

---

### Post by MJN on 2006-07-01
I not familiar with either Gaim or Trillian however given that port 80 is universally accepted to be used for HTTP, and indeed has a long-standing registration in the IANA port list, I would look to be moving Gaim/Trillian to other ports and leaving Apache where it is.

Why are they using port 80?

Mathew

---

### Post by nagilum on 2006-07-01
Since only programs with superuser privileges are able to listen on ports below 1024 you seem to run Gaim / Trillian as root. Am I correct? This is not a good idea, you better run them as a regular user. This will additionally solve your problem with Apache.

---

