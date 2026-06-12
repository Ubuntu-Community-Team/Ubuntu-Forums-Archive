---
title: "synch samba users with unix users?"
date: 2009-02-26
forum: Server Platforms
---

### Post by kooldino on 2009-02-26
So I'm running a samba server on a machine with a bunch of users on it.

As it sits right now, I don't know of any way for the samba users to change their own password, however they can change their linux password by logging into the shell.

Is there any way to permanently synch or merge these, so I only have to manage one acct per person?  Or is there at least some way to allow a user to change his password?

---

### Post by kooldino on 2009-02-27
looks like "security = user" in the smb.conf might do the trick...

---

### Post by capscrew on 2009-02-27
Close.  "security = user" means that auth will be checked and it is based on the Linux account.

To sync the smbpasswd to the /etc/passwd you should use this:```
# This controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
      unix password sync = yes

```

---

