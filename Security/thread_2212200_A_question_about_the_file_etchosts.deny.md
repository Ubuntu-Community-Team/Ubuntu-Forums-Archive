---
title: "A question about the file /etc/hosts.deny"
date: 2014-03-19
forum: Security
---

### Post by jsvidyad on 2014-03-19
Hello,

    The manual page for the file /etc/hosts.deny says that to deny network access to my computer for all others over a network, I just add the line 
ALL: ALL
to the file /etc/hosts.deny.

My question is, is there supposed to be a space after the colon symbol(:) in that line or not? Does it matter if there is a space after the colon symbol or not?

---

### Post by Dave_L on 2014-03-20
The example in the man page has a single space after the colon, so I would assume that's correct. I don't know if it really matters.

---

### Post by 7sbaV8Kt5PTh on 2014-03-20
I haven't used that file in a couple of years, but the spaces were necessary.  If you have multiple, comma separated entries, there needed to be a space there too.

---

### Post by jsvidyad on 2014-03-23
So, the consensus is that the space after the colon symbol is necessary ?

---

### Post by Dave_L on 2014-03-24
All the examples I saw in the documention had a space after the colon.

---

### Post by james114 on 2014-03-24
I think the space after the colon symbol is unnecessary but use it in typesetting.

Example:
[http://ubuntuforums.org/showthread.php?t=911128](http://ubuntuforums.org/showthread.php?t=911128)

---

