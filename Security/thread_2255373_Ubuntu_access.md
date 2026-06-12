---
title: "Ubuntu access"
date: 2014-12-04
forum: Security
---

### Post by niki85 on 2014-12-04
Hello,

When i give to someone my root password for optimize server,
After i change password and he can't anymore login there ? or can via ssh key ?
How i can be sure when i change password only i can login there ?

Thanks.

---

### Post by lisati on 2014-12-04
By root password, do you mean your admin account's password? The root account is locked by default in Ubuntu. For more information, see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Once you have changed your password, other people shouldn't be able to log in using your old password.

---

### Post by niki85 on 2014-12-05
Friend tell me he can access via ssh key always ?
How i can remove ssh key and able login only via normall password, and if i change password then nobody can't login ?

Thanks.

---

### Post by ian-weisser on 2014-12-05
If you do not trust your 'friend', then reinstall. You have already compromised your system by turning over admin access to someone you do not trust.
Don't do that again.

Next time, have your friend teach you how to 'optimize' your server yourself instead of doing it for you.
Then come here and show us.
In what way did your system need to be optimized?

  One way prevent all ssh logins is to uninstall the openssh-server  package...unless, of course, your friend installed a secret backdoor  somewhere.

---

