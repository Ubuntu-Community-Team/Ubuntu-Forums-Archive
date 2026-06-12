---
title: "login with wrong password"
date: 2008-06-04
forum: Security
---

### Post by chrisdeeley on 2008-06-04
I've just noticed that my Ubuntu file server let me login with the wrong password :(

My password is 9 characters long but if i miss of the last letter (ie only enter the first 8 ) it still logs me in.

Any idea's why?

---

### Post by Dr Small on 2008-06-04
That doesn't make sense.

---

### Post by The Cog on 2008-06-04
What protocol are you using to log in with?
VNC only checks the first 8 characters.

---

### Post by chrisdeeley on 2008-06-04
I mainly use SSH and webmin for remote admin of the machine which both allow me to login without the last character. It also does this when I connect to my e-mails (using Dovecot IMAP) but samba will only accept the full password!!

---

### Post by cdenley on 2008-06-04
Sounds like your /etc/shadow file has DES hashes. Hardy seems to use MD5 hashes by default. What is the output of
```

sudo getent shadow chrisdeeley|cut -d : -f 2|cut -c 1,2,3

```
If it doesn't start with a "$", that is a DES hash, and only the first 8 characters of your password are used. What version of ubuntu are you running. What version were your running when you set that password? Try resetting it.
```

sudo passwd chrisdeeley

```

Also, check this file
```

grep MD5_CRYPT_ENAB /etc/login.defs

```

---

### Post by chrisdeeley on 2008-06-04
I was and still am running 7.10 gutsy. I just reset the password and now everything's back to normal. I don't understand why though because another user that I set up at the same time also has a long password yet when i tested it, I could only log in with the full password.

Everything appears to be back to normal. I'll try it again in the morning and see what happens.

Thanks for your help

---

