---
title: "fail to change mysql root password"
date: 2010-03-29
forum: Server Platforms
---

### Post by satimis on 2010-03-29
Hi folks,

Ubuntu 910 64bit

# mysqladmin -u root p'oldpasswd' password newpasswd```

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

However with the oldpasswd I can login mysql.

$ mysql -u root -p
Enter password: oldpasswd
...
mysql >


Please help.  TIA


B.R.
satimis

---

### Post by Ryan Dwyer on 2010-03-29
You missed the dash (-) before the p.

---

### Post by satimis on 2010-03-29
> **Ryan Dwyer said:**
> You missed the dash (-) before the p.

I see.  Thanks


B.R.
satimis

---

