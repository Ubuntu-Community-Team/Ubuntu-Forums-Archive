---
title: "OpenSSH flaw... Patch backported?"
date: 2009-05-22
forum: Security
---

### Post by whoop on 2009-05-22
There's a design flaw in openssh (debian):
[http://news.zdnet.com/2100-9595_22-303182.html](http://news.zdnet.com/2100-9595_22-303182.html)
I believe it is fixed in 5.2, but ubuntu uses 5.1. Does anybody know if a patch for this flaw is backported to the ubuntu package?

---

### Post by cdenley on 2009-05-22
[http://openssh.com/txt/cbc.adv](http://openssh.com/txt/cbc.adv)

The counter-measure patch I believe you are referring to seems to have been backported.

[http://changelogs.ubuntu.com/changelogs/pool/main/o/openssh/openssh_5.1p1-5ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/o/openssh/openssh_5.1p1-5ubuntu1/changelog)
> 
openssh (1:5.1p1-5) unstable; urgency=low

  * Backport from upstream CVS (Markus Friedl):
    - packet_disconnect() on padding error, too. Should reduce the success
      probability for the CPNI-957037 Plaintext Recovery Attack to 2^-18.


---

