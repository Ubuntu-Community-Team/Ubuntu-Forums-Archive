---
title: "Source of mkpasswd?"
date: 2010-05-14
forum: Security
---

### Post by m6a2x6 on 2010-05-14
Hi!

I am trying to find the source code behind mkpasswd which I apt-getted from universe. I am trying to code a similar app in Java and want to see how the salt is implemented in the /etc/shadow file.

Bu I just can't seem to find any source about that particular program...

Can anybody more familiar with Ubuntu's sources help?
Thank you!

---

### Post by cdenley on 2010-05-14
```
apt-get source whois
gedit whois*/mkpasswd.c

```

---

### Post by m6a2x6 on 2010-05-14
Thank you so much! That's exactly what I was looking for!

---

