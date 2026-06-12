---
title: "live view of ssh log"
date: 2011-02-14
forum: Security
---

### Post by giodamelio on 2011-02-14
Is there some way to view the an openssh servers auth logs in real time?

---

### Post by lisati on 2011-02-14
You might need to do a little bit of research to get the correct file name, but you could always use something like this from the command line:
```
tail -f {log-file-name}
```
(leave out the "{}")

---

### Post by giodamelio on 2011-02-14
Thanks that was exactly what i was looking for.:p

For anyone else, this will work very nicely to view auth attempts on you ssh server.
```
tail -f /var/log/auth.log
```

---

