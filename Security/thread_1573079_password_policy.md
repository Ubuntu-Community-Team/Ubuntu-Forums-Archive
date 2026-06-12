---
title: "password policy"
date: 2010-09-12
forum: Security
---

### Post by Obould on 2010-09-12
Hello,

I am relatively new to ubuntu. Is there a way to change the password policy. I know you can change the expiration date but I also want to set password complexity (min chars, ...)

Best regards

---

### Post by HermanAB on 2010-09-12
Howdy,

It is configured in PAM.  However, PAM is a very sensitive girl - if you make a mistake then you won't be able to log in anymore.

Anyhoo, poke around in /etc/pam.d and google a bit.  Maybe read this:
[http://www.faqs.org/docs/Linux-HOWTO/User-Authentication-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/User-Authentication-HOWTO.html)

---

### Post by Aerospaztic on 2010-09-30
I ran into this a while back.  The best thing to do is to go into synaptic and get libpam_cracklib.

Then go to etc/pam.d/common-password.

On the line that has pam_cracklib.so, add the following:

```
minlen=12 ucredit=-1 lcredit=-1 dcredit=-1 ocredit=-1
```

Use this code, for instance, for a minimum length of 12.  Also, this will stipulate that you must have one of each type of character - upper and lower case, a digit, and other (special) characters.  If you do not specify the credits, then the default for each character type is 1, and it will credit the use of that character towards your minimum length.  That means if your minlen is 12 with no specification for dcredit, then you can actually choose a password with 11 characters as long as you have 1 digit, because it will credit a +1 for the assumed dcredit=1.  The -1 value will require at least one of that type of character but will not credit the use of that character type towards your minlen.

---

