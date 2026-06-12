---
title: "Newbie Question: List all accounts"
date: 2006-04-12
forum: Server Platforms
---

### Post by cnich23 on 2006-04-12
I know that users command list current users logged in but how do I list all user accounts?

---

### Post by cnich23 on 2006-04-12
How to list all groups would also be helpful

---

### Post by IYY on 2006-04-13
```
cat /etc/passwd | cut -d: -f1
```

and likewise for groups:

```
cat /etc/group | cut -d: -f1
```

Really all we are doing is looking in the /etc/group and /etc/passwd files, and formatting it nicely.

---

### Post by fdoving on 2006-04-14
I would suggest

Listing accounts:
```

getent passwd

```

Listing groups:
```

getent group

```

---

