---
title: "Dropbox, add a folder for sync"
date: 2013-01-28
forum: Server Platforms
---

### Post by anerDev on 2013-01-28
Hi guys !

I installed Dropbox, work !
I would like to add this folder /media/hd-dati/documenti to dropbox folder /user/Dropbox
I tried this command, but don't work !

```
~/.dropbox/dropbox.py exclude add /media/hd-dati/documenti
```

Who can Help me ?

Thank you

---

### Post by hydn79 on 2013-01-28
did you run:
```
chmod +x ~/.dropbox/dropbox.py
```

Check status:
```
~/.dropbox/dropbox.py status
```

---

### Post by dannyboy79 on 2013-01-28
> **anerDev said:**
> Hi guys !

I installed Dropbox, work !
I would like to add this folder /media/hd-dati/documenti to dropbox folder /user/Dropbox
I tried this command, but don't work !

```
~/.dropbox/dropbox.py exclude add /media/hd-dati/documenti
```

Who can Help me ?

Thank youim not sure if symlinking works in dropbox but you can try? to add a symlink in your ~/user/Dropbox/ folder so that it points to /media/hd-dati/documenti that would be the following command
```
ln -s /media/hd-dati/documenti ~/user/Dropbox/documenti
```

---

### Post by anerDev on 2013-01-29
Oh yeah !

THis work:

```
ln -s /media/hd-dati/documenti ~/Dropbox/documenti
```

Thank you guys ! :D

---

### Post by dannyboy79 on 2013-01-29
awesome, use the thread tools in the upper right corner and mark it solved.

---

### Post by ntzrmtthihu777 on 2013-01-29
Yeah, symlinking did the trick for me too

---

