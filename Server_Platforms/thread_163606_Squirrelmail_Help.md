---
title: "Squirrelmail Help"
date: 2006-04-21
forum: Server Platforms
---

### Post by rwhite59 on 2006-04-21
I get this error when I try to login from the default login page:

Error opening ../config/default_pref
Could not create initial preference file!
/var/lib/squirrelmail/data/ should be writable by user nobody

---

### Post by st0kes on 2006-04-21
did you try: 

```
sudo chown nobody /var/lib/squirrelmail/data/
```

---

