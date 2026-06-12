---
title: "Need help to make a Fail2Ban regex"
date: 2013-09-08
forum: Security
---

### Post by Nil_Pointer on 2013-09-08
Hello. I need to configure Fail2Ban to ban when following entries appear in log:

[I YY-MM-DD HH:MM:SS] <IP>:<PORT>-[] USER '<USERNAME>' failed login.

But I'm confused as to how do Fail2Ban regexes work. Apparently, they're extended in some way. I tried to write one, but they refuse to work. Can anyone help?

---

### Post by unspawn on 2013-09-09
> **Nil_Pointer said:**
>  I tried to write one, but they refuse to work. Can anyone help?
To help us help you efficiently it's better if you post the regex you tried and the way you tested it (see 'man fail2ban-regex'?).

---

### Post by Nil_Pointer on 2013-09-10
Well, I've decided to use SFTP instead of FTP server, and therefore I don't need to match those auth fails anymore.

As for regexes... I didn't save them and tested them with fail2ban-regex. If I understand correctly, timestamps must be matched somewhere else (I had an error, where it said something about "no valid date/time found"). If I'd have to write standard regex to match entire string, it'd be easy. But I those seems to be extended, I don't know where to write timestamp-matching regex and I was unable to find adequate docs.

---

### Post by unspawn on 2013-09-10
> **Nil_Pointer said:**
> As for regexes... I didn't save them and tested them with fail2ban-regex.
That would be the obvious and preferred way to test them.


> **Nil_Pointer said:**
> If I understand correctly, timestamps must be matched somewhere else (I had an error, where it said something about "no valid date/time found"). If I'd have to write standard regex to match entire string, it'd be easy. But I those seems to be extended, I don't know where to write timestamp-matching regex and I was unable to find adequate docs.
Date formats are listed in [datedetector.py](http://fail2ban.sourceforge.net/docs/datedetector_8py.html).

---

