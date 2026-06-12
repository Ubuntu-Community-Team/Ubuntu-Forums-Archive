---
title: "Need help with my fingerprint sensor"
date: 2009-04-23
forum: Security
---

### Post by diablo75 on 2009-04-23
I followed the guide located at this address:

[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops/comment-page-7#fingerprint](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops/comment-page-7#fingerprint)

And I got fprint_demo to work with functioning verification of my fingerprint versus a print that I didn't enroll.

The problem is that, the part of the guide that says to paste in "auth sufficient pam_fprint.so" if you want it to check EITHER your password or your finger print, or "auth required pam_fprint.so" if you want it to check BOTH your password AND finger print.... If you set it to "sufficient", it doesn't care what finger you use, or if they're enrolled or not... just swipe any finger and it works.  And if you set it to "required" instead, no finger works at all, and you have to re-edit the /etc/pam.d/common-auth file to comment out the change made in order to log back into your account with your password alone.

So I was wondering if anyone else has noticed this and if I should submit a bug report about it.  Thanks.

---

### Post by diablo75 on 2009-04-25
Bump...

---

### Post by Dr Small on 2009-04-26
Just avoid fingerprint readers for any form of authentication.

---

### Post by digirandi on 2009-04-26
i am not an expert but what is your problem
finger prints are evolving faster with newer improvements

---

### Post by aldeby on 2009-05-11
I'm sorry, there was a mistake in the tutorial previously. This has been fixed now.

[Check it out here]("http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops/comment-page-7#fingerprint").

---

