---
title: "Change language in console"
date: 2006-06-28
forum: Server Platforms
---

### Post by trac on 2006-06-28
lo.
Does anyone know how to change the default language on the server?
I dont have X11 on it, so it has to be done from ssh.
thz.

---

### Post by smyrman on 2008-03-06
Hi.

To change the language, just edit the /etc/enviroment file:

```
sudo nano /etc/enviromen
```

Then add these two lines:

```
LANG="en_GB.UTF-8"
LANGUAGE="en_GB:en"
```

Tell me if you have any problems on this one.

EDIT: of course, replace the "en" and "GB" with what suits you best.

---

