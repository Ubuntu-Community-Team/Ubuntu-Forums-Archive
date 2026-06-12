---
title: "nepenthes configuration files missing"
date: 2010-12-07
forum: Security
---

### Post by geminihzh on 2010-12-07
hi, I am doing a honeypot project, and after I install nepenthes:
$ sudo apt-get install nepenthes

$ nepenthes

I find that there are no configuration files in /etc/nepenthes/, and only a signatures document.

I searched in the internet, all the install guides do not mention this problme, just say that if updating the nepenthes, the /etc/nepenthes/*.conf will not automaticly update.

Does anyone know the problem?

---

### Post by cariboo on 2010-12-07
There usually example configuration files in /usr/share/doc/nepenthes or /usr/share/nepenthes. You may have to copy them to /etc/nepenthes

---

### Post by geminihzh on 2010-12-07
> **cariboo907 said:**
> There usually example configuration files in /usr/share/doc/nepenthes or /usr/share/nepenthes. You may have to copy them to /etc/nepenthes
 
Thanks~
But I have check that there is no these files in /usr/share/doc/nepenthes/
I have find the website below providing these files :
[http://sysinf0.klabs.be/etc/nepenthes/submit-file.conf?dist=;arch](http://sysinf0.klabs.be/etc/nepenthes/submit-file.conf?dist=;arch)=

---

