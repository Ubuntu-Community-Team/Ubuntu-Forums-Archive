---
title: "How do you get moinmoin 1.9.3 to use python 2.6.x rather than 2.7.1?"
date: 2011-08-01
forum: Server Platforms
---

### Post by pyjimbo on 2011-08-01
I am running Ubuntu Desktop 11.04 with the 11.04 server installed on top via tasksel. I keep getting "Unhandled Exception An unhandled exception was thrown by the application." when running moinmoin 1.9.3. I know its trying to run on python 2.7.1 but there is no support for that yet with moinmoin1.9.3. I installed python2.6 and #!/usr/bin/python2.6 at the top of moin.cgi. Is this where 2.6 is located? What do I put in moin.cgi for a python 2.6 path?

I am installing moinmoin by dragging and dropping files with filezilla via FTP.

I have set up moinmoin before and had it working but since I did my 11.04 clean install with python 2.7 I can not install moinmoin.

---

### Post by stlsaint on 2011-08-01
Try removing python 2.7 and just using python 2.6 with the path:

```
 /usr/bin/env pyhon 
```

---

### Post by pyjimbo on 2011-08-01
> **stlsaint said:**
> Try removing python 2.7 and just using python 2.6 with the path:

```
 /usr/bin/env pyhon 
```

From what I understand the ubuntu operating system is very dependent on python 2.7 and removing it would mess things up.

---

