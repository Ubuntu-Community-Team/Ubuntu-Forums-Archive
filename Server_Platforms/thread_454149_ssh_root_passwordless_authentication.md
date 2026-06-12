---
title: "ssh root passwordless authentication"
date: 2007-05-25
forum: Server Platforms
---

### Post by erasmo.da.rotterdam on 2007-05-25
HI!
I need to do an automate backup on a remote server so it is necessary to log in as root through ssh with passwordless authentication
I can log in using my keys as a normal user however it isn't possible as root.
I put my public key in /root/.ssh/authorized_keys in the same way I did in /home/user/.ssh/authorized_keys
```
#cat /etc/ssh/sshd_config | grep oot
PermitRootLogin without-password
```
(I already restarted ssh ;))
I do not have any active root user and I am wondering if this could be the problem and if I'll be forced to enable it or not...
Any ideas?

---

### Post by turinglabs on 2007-05-25
You don't need to activate the root user to use key-based authentication. Check the permissions on your /root/.ssh/authorized_keys file to make sure they are 600 (you probably have StrictModes set to yes, which is the default). If that doesn't work, try logging in with the '-v' or '-vv' switches to get debug info.

---

### Post by erasmo.da.rotterdam on 2007-05-25
Yesss!!
I found it!!!
authorized_keys permissions were right but not the owner

```
#sudo chown root:root /root/.ssh/authorized_keys
```

StrictModes yes is not a problem

Thank you very much

:popcorn:

---

### Post by hartz on 2007-05-28
You need to make backups via ssh - fine. But why does it have to log in as root?

---

