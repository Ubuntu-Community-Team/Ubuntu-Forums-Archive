---
title: "forgot my &quot;SU&quot; password"
date: 2009-09-02
forum: Security
---

### Post by shariefbe on 2009-09-02
Hello friends,
  I created root password. But when i type "su" and then password, but my result is below one

```
sharief@sharief-desktop:/$ su
Password: 
su: Authentication failure
sharief@sharief-desktop:/$
```

Now i dont know how to retrieve the password or how to rest the password...Can anyone help me

---

### Post by aysiu on 2009-09-02
This is not a supported way of doing things. Ubuntu does not have a root password by default.

If you need to accomplish something as root, enter ```
sudo -i
``` in the terminal.

---

### Post by aysiu on 2009-09-02
This is not a supported way of doing things. Ubuntu does not have a root password by default.

If you need to accomplish something as root, enter ```
sudo -i
``` in the terminal.

No worries, though. You can easily disable the root account again:
[https://help.ubuntu.com/community/RootSudo#Re-disabling your root account](https://help.ubuntu.com/community/RootSudo#Re-disabling your root account)

---

