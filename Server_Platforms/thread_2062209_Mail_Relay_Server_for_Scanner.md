---
title: "Mail Relay Server for Scanner"
date: 2012-09-24
forum: Server Platforms
---

### Post by mykrob on 2012-09-24
Morning-
I am looking to possible build a small mail server to handle sending scanned documents from a multifunction printer. This would be the sole purpose of the machine. 
that said, I have found lots of documentation on setting up a mail server, but am looking for some information from experienced users. Lots of the documentation varies greatly, so I am looking for advice/opinions on the most concise and understandable documentation for setting up an Ubuntu mail server for server virgins..

Thanks in advance.
-myk

---

### Post by Bachstelze on 2012-09-24
```
sudo apt-get install postfix
```

The default settings are very sensible, they could very well work for you. If they don't, report here the problems you are facing.

---

