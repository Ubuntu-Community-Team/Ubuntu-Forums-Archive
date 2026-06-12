---
title: "No connection to Ajenti control panel?"
date: 2013-07-03
forum: Server Platforms
---

### Post by JayUK20 on 2013-07-03
I installed Ajenti and it installed and started the service without a hitch but..... When I go to [http://myip:8000](http://myip:8000) there doesn't seem to be a connection even though the port is open and accepts connection through other software and I've tried changing ports but nothing. Nothing else was bound to that port.

I've looked at Ajenti logs but they are both blank.

---

### Post by DJ_Max on 2013-07-03
Are you sure it's running?

```
netstat -an | grep -P '\:'8000''
```

---

### Post by JayUK20 on 2013-07-04
Ah. Ajenti doesn't seem to be listening on that port, any ideas?

---

### Post by DJ_Max on 2013-07-04
Never heard of Ajenti, but make sure it's actually started.

---

### Post by Simon_WM on 2013-07-11
[http://ajenti.org/](http://ajenti.org/) - website,  I think it might be with the latest update, Because I couldn't get it to connect on my test vm, But i'm trying to try again tonight

---

### Post by bolens1112 on 2013-11-06
I know it may be a little late but for anyone else that stumbles across this it is port 8000 for ubuntu.  I have no idea why but there it is.

---

