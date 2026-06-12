---
title: "Ubuntu One on a non-English winXP: folder name bug?"
date: 2013-08-22
forum: Ubuntu One (CLOSED)
---

### Post by tony14 on 2013-08-22
It seems to be impossible to add a local folder if it is located anywhere within a folder tree, and some of them has a name in Cyrillics.

In my case I was not able to add the "C:\Documents and Settings\user\_&#1052;&#1086;&#1080; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;_\**rsync.u1**" folder to UbuntuOne v4.2.0.0, I have had to resort to the "C:\Documents and Settings\user\rsync.u1" instead.

Is it a bug?

---

### Post by jjaison-daniel on 2013-08-22
check your character encoding. If your default encoding is different and the folder name in different encoding then you will face this problem. First find what encoding the Cyrillics character used and try that.

---

### Post by tony14 on 2013-08-22
> **jjaison-daniel said:**
> check your character encoding
Where?
It is the winXP-SP3 Russian, all locales are set to "Russia".
> **jjaison-daniel said:**
> If your default encoding is different...
Different from what?
 > **jjaison-daniel said:**
> ...and the folder name in different encoding...
 The problematic folder ("My Documents" in English) is a system one - I did not give a name to it, it is such by winXP installer.
> **jjaison-daniel said:**
> ...then you will face this problem. First find what encoding the Cyrillics character used and try that.
???

---

