---
title: "Self control of password requirements"
date: 2015-04-08
forum: Security
---

### Post by BarneyG on 2015-04-08
Is there anyway for me to take control of the password requirements. It seems that with each version there are different requirements. 

I'd like to control what they are instead of just going along with whatever Ubuntu decides they should be. 

How do I do this?

Thank you

---

### Post by TheFu on 2015-04-08
Check the files in /etc/pam.d/ ... [https://askubuntu.com/questions/156850/how-do-you-set-requirements-such-as-minimum-length-on-passwords](https://askubuntu.com/questions/156850/how-do-you-set-requirements-such-as-minimum-length-on-passwords) explains. I don't think this really has changed, but we require 16 character password with upper/lower/numbers and punctuation.  12 characters (completely random) and less can be hacked in 24 hrs these days.

---

### Post by BarneyG on 2015-04-08
Thank you TheFu.

I'll check it out.

---

### Post by HermanAB on 2015-04-13
Hmm, just bear in mind that PAM is a very sensitive girl.  If you make the slightest mistake in a PAM file, then she may not allow you to log into your machine - at all...

---

