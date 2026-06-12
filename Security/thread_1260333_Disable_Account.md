---
title: "Disable Account"
date: 2009-09-07
forum: Security
---

### Post by joe2012 on 2009-09-07
How can you disable an account, but not remove it from the system? Something from the terminal is preferable.

Thanks

---

### Post by Rob_H on 2009-09-07
Try:

```
sudo passwd -l <user>
```

---

### Post by arrange on 2009-09-07
From man passwd
> -l, --lock
           Lock the password of the named account. This option disables a password by changing it to a value which matches no possible encrypted value
           (it adds a ´!´ at the beginning of the password).

           _Note that this does not disable the account._ The user may still be able to login using another authentication token (e.g. an SSH key). [U]To
           disable the account[/U], administrators should use usermod --expiredate 1 (this set the account´s expire date to Jan 2, 1970).

           Users with a locked password are not allowed to change their password.

---

