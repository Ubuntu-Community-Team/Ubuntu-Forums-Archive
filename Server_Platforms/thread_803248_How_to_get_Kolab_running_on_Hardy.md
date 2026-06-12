---
title: "How to get Kolab running on Hardy ?"
date: 2008-05-22
forum: Server Platforms
---

### Post by scotty64 on 2008-05-22
I am trying to get Kolab running on Hardy, but the provided packages seem to be full of incompatibilities. Has anybody managed to get it running?

I got that far that slapd seems inable to access any file that lives outside the schema directory, so I had to copy the schema files from /usr/share/kolabd/schema and /etc/kolab/rootDSE.ldif into /etc/ldap schema. In addition I had to comment out the two TLS entries in slapd.conf in order to fire up slapd without errors. You find a modified slapd.conf.template attached that can be used to replace the existing file in /etc/kolab/templates in order to successfully run kolab_bootstrap.
Warning: I would use this file for testing only as TLS is disabled.

But now when I try to open the admin interface I just get an empty page....

---

### Post by HermanAB on 2008-05-22
Hmm, I have tried multiple times in the past to install Kolab.  It seems to be a mess, so I use Citadel instead.  Citadel is very easy to install and is zero maintenance - definately in the 'Just Works' category: [http://citadel.org](http://citadel.org)

---

### Post by scotty64 on 2008-05-22
> **HermanAB said:**
> Hmm, I have tried multiple times in the past to install Kolab.  It seems to be a mess, so I use Citadel instead.  Citadel is very easy to install and is zero maintenance - definately in the 'Just Works' category: [http://citadel.org](http://citadel.org)

Hi Hermann,
you are completely right. I have several Citadel installations running - it works like a charm and the easyinstall is simple. I just wanted to test Kolab, because I heared lots of it and one organization I am working for wants to see some alternatives. Citadel is still my favourite :)

---

### Post by HermanAB on 2008-05-22
Yeah, I gave Kolab a serious try - and eventually I gave up.  I guess it works for some people, but it sure is not a mature product.

---

### Post by scotty64 on 2008-06-10
> **HermanAB said:**
> Yeah, I gave Kolab a serious try - and eventually I gave up.  I guess it works for some people, but it sure is not a mature product.

I managed to plug Horde webmail into a Citadel server and it worked fine - specially the new DIMP Ajax mail module. I tried to connect Hordes kolab calender to citadel, but whenever I switched Horde from SQL to Kolab calendering support sadly the whole installation got messed up. I will probably invest some more time in this, as I need an alternative to Citadels Webcit-interface with its poor folder management.

---

