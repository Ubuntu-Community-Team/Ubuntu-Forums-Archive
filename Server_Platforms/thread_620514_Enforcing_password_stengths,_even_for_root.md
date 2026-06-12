---
title: "Enforcing password stengths, even for root?"
date: 2007-11-22
forum: Server Platforms
---

### Post by MJN on 2007-11-22
My PAM configuration states the following default restrictions in **/etc/pam.d/common-password**:
**```
password   required   pam_unix.so nullok obscure min=4 max=8 md5
```**And these default restrictions are inherited by the passwd module in **/etc/pam.d/passwd**:
```
**@include common-password**
```Therefore if **passwd **is run by a normal user (e.g.** passwd <user>**) and the new password is too small PAM rejects the change (with '**BAD: new password is too short**').

So far so good...

However, if **passwd** is run as root (i.e. **sudo passwd <user>**) then PAM allows even a short password to be set for <user>.  I am assuming this is due simply and solely to the fact it is being executed as root.

How do I change this behaviour? I want the same password restrictions to apply in all cases, even when root is performing the change.

The actual background behind this request is that I am using a poppassd daemon to change the passwords for Squirremail (webmail) users. Poppassd uses PAM and hence can be configured the same as passwd - however as poppassd needs to be run as root (in order to be able to change any user's password) it too is not restricted by the length options in the PAM config.

Any suggestions?

Mathew

---

### Post by yeleek on 2008-02-22
I'd really like to know this - Any ideas please?

---

