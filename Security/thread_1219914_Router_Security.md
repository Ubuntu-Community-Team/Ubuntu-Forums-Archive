---
title: "Router Security"
date: 2009-07-22
forum: Security
---

### Post by risingsun on 2009-07-22
Hi, given the recent revelation of the DD-WRT vulnerability, I was just curious as to how someone would go about checking for a compromised router.

In particular I do think back to an occasion a few weeks ago where on checking my webmail there was an unusual character in one of the subject lines ( a spam email, though I think the character was just a character that firefox was unable to render.) Some minutes later my router did seem to have trouble and slowly got slower and slower (possibly a DNS problem) until eventually a power cycle for a few minutes later seemed to fix it (though whether I can attribute this to a router problem or an ISP problem I don't know. Linksys doesn't neccesarily have the best reputation in this regard, though I've never really experienced any major problems with it.) 

My dilema here is was there an actual problem or was it pure coincidence. I'm using a linksys wireless router (though I'm afraid the model name escapes me at the moment) running on the linksys firmware but it should be relatively secure in that it's locked down to login via the wired local network only and with a (hopefully) secure password. Also given that the webmail should hopefully parse the subject lines of emails correctly (from what I can tell anyway) I would hope that the router should have been secure and is all is well. 

Apart from the DD-WRT vulnurability I'm unware of any vulnurabilities for routers that avoid authorisation, in which I would assume I'm thus safe, but any advice anyone can give would be greatly appreciated. :)

---

### Post by rookcifer on 2009-07-22
The DD-WRT vulnerability has nothing to do with login authorization or passwords, etc.  It has to do with a flaw in the HTTP daemon.  First of all the daemon runs as root (which is stupid).  Second, this flaw makes it vulnerable to XSS attacks (which are quite common these days).  Thus, all you have to do is visit a malicious website and your router is pwned.

There are two ways to fix it:

A) Disable remote web GUI administration of the router

B) Wait for a firmware update

---

