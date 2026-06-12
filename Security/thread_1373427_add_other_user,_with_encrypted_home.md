---
title: "add other user, with encrypted home"
date: 2010-01-05
forum: Security
---

### Post by gcbzzzz on 2010-01-05
Need to add another user. I was hoping the new user button would show me the same options  for encrypted home dir as I was shown during the 9.10 install.

but I wasn't. Now all the tutorials I find are to do everything from scratch, and the end result are all different from the way ubuntu done it initially.

Since I want to same procedure for both users, can someone point me to the official way to manually doing that for the 2nd user, please?

thanks

---

### Post by Gourgi on 2010-01-06
```
sudo adduser --encrypt-home new_user
```
man is also useful
```
man adduser
```

---

