---
title: "How to add another sudoer account"
date: 2012-01-19
forum: Server Platforms
---

### Post by Jefferythewind on 2012-01-19
Hi Everyone,

  I have added a user to my server, and now I would like to let that user have sudo privileges, is this possible?  If so how do I do that.  This way we would have 2 or more users who could sudo.

Thanks!

---

### Post by Buntumatic on 2012-01-19
Easiest way would be adding them to sudo group.

---

### Post by CharlesA on 2012-01-19
```
sudo usermod -a -G admin username
```

---

### Post by Jefferythewind on 2012-01-30
Thanks a lot!  
```
sudo usermod -a -G admin username
```
That was it.

---

### Post by cabaro on 2012-01-30
```
adduser username admin
```

Here username is the user you want to add to admin group.

---

