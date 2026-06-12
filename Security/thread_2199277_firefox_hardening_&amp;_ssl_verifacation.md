---
title: "firefox hardening &amp; ssl verifacation"
date: 2014-01-13
forum: Security
---

### Post by jimmyh1972 on 2014-01-13
Hello

I want to harden my firefox browser so it will be able to surf _only_ to Gmail login page
also to verify (in some script or any other way...) that the ssl certificate of Gmail is genuine
how can i do it?

Thanks ahead Jimmi

---

### Post by untrustytahr on 2014-01-13
I wouldn't consider this "hardened" but it will do what you want.  Someone with some decent technical ability could get around it.

Set your proxy to loopback address and put google in the no proxy exception list.  You would then have to lockdown the options that allow such changes (button, checkboxes, etc) in about config so they couldn't be restored.

As for authenticating SSL, browsers already do that through CA's and trust chains.

---

