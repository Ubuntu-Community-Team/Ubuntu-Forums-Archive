---
title: "How can I find out when user X last logged in?`"
date: 2006-12-20
forum: Server Platforms
---

### Post by apjone on 2006-12-20
How can I find out when user X or user Y last logged in?`

---

### Post by wylfing on 2006-12-20
Try this:
```
last
```

If you need to narrow down the list (if your system gets a lot of logins), then:
```
last | grep *username*
```

---

