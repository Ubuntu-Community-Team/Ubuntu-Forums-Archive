---
title: "How would you know???"
date: 2008-02-14
forum: Security Discussions
---

### Post by elcapy on 2008-02-14
I know my Linux box still fine but how would i know if my box has been compromised is there ways that you can tell for someone that does not know Linux so some of you guys in here, I just want to know so I keep an eye out for it if it ever does happen to me. thanks in advanced

---

### Post by Dr Small on 2008-02-14
Watch your auth.log for incoming requests.
/var/log/auth.log

---

### Post by elcapy on 2008-02-14
thanks I will keep an eye on it from time to time.:)

---

### Post by HermanAB on 2008-02-15
Like this:

$ sudo tail -f /var/log/auth.log

and
$ sudo tail -f /var/log/messages

Cheers,

Herman

---

### Post by unoodles on 2008-02-15
you could also install chkrootkit and rkhunter

---

### Post by astrotech226 on 2008-02-16
Another neat way to monitor your system is with "tripwire".  Once installed, it catalogs the files on your computer.  There is some setup involved in what to ignore, etc...

A scan is run from time to time and it will alert you to file changes.  This is big deal when files like "netstat" mysteriously change in the middle of the day and you have run no updates.

---

