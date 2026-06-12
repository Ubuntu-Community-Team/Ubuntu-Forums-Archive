---
title: "Just changed my password - Keyring is acting funny!"
date: 2010-08-25
forum: Security
---

### Post by ki4jgt on 2010-08-25
I just changed my password now every time I start my computer the keyring wants my old password and it keeps doing weird things even after I type it in. Like Ubuntu will say No keyring found or something to that effect anyway. Any suggestions

---

### Post by FuturePilot on 2010-08-25
Open Applications > Accessories > Passwords & Encryption Keys. Right click Passwords: login and Change Password. Your old password will be your previous login password and make sure your new one is the same as your current login password. For future reference do not change your own password with System > Administration > Users and Groups. Use System > Preferences > About Me instead.

---

### Post by ki4jgt on 2010-08-25
Thanks I'll remember that! So why exactly do they have that option?

---

### Post by OpSecShellshock on 2010-08-25
> **ki4jgt said:**
> Thanks I'll remember that! So why exactly do they have that option?

It's so that administrators can configure other users' accounts, group memberships, and permissions.

---

### Post by ki4jgt on 2010-08-25
Just did what you said, now I've got another problem. When I try to install software I get this.

```
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 126, in _process_transaction
    self.install_packages(self.trans.packages[0])
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 207, in install_packages
    self._commit_changes()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 551, in _commit_changes
    changes = self._cache.get_changes()
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 179, in get_changes
    for pkg in self:
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 161, in __iter__
    yield self[pkgname]
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 154, in __getitem__
    pkg = self._weakref[key] = Package(self, self._cache[key])
KeyError: ''
```

---

