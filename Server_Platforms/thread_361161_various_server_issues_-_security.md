---
title: "various server issues - security"
date: 2007-02-14
forum: Server Platforms
---

### Post by ninocass on 2007-02-14
I ran NX (vulnerability) scanner against my site to see what the vulnerabilities were present.

There was only 1 high risk vulnerability to do with the version of mod-ssl and the rest were low risk banner problems:

HTTP Banner Exposure
HTTP Directory Listings
HTTP Server Address Location ( basically a GET request for a directory without the trailing / )
SSH Information obtained

Ive trained in vain to correct these problems but for some reason everything i try doesnt work!  

Could someone tell me how to fix these or if there is a hardening guide for ubuntu servers?

cheers

Nino

---

### Post by elst on 2007-02-14
Perhaps you could outline what changes you've tried to make on your server that haven't worked?

The HTTP issues are Apache settings, and you can avoid most attempts to attack SSH simply by changing the port number that the OpenSSH service uses.

---

### Post by gaten on 2007-02-14
You should check out mod_security. Allows you to restrict all kinds of things (including attacks), kind of like an apache IDS (Intrusion Detection System). Also prevents attacks, not just detects them. 

Read about it here: [http://www.modsecurity.org/](http://www.modsecurity.org/)

Don't worry about the purchase stuff on the website, it's free. Also, check out: [http://www.securityfocus.com/infocus/1786](http://www.securityfocus.com/infocus/1786) for a GREAT article on how to secure Apache2. You can mostly stick to the configuration sections, you don't need to recompile and all that. Also, look at mod_chroot ([http://core.segfault.pl/~hobbit/mod_chroot/]("http://core.segfault.pl/%7Ehobbit/mod_chroot/")) for even more security. Good luck!

---

