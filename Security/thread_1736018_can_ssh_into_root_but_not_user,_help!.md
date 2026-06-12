---
title: "can ssh into root but not user, help!"
date: 2011-04-22
forum: Security
---

### Post by tribalvibes on 2011-04-22
Having trouble adding a regular user with ssh access on Hardy 8.04.  I can ssh into root, but not into the newly created regular user with the same ~/.ssh/authorized_keys

```
sshd_config has:
AllowGroups sshlogin
AllowUsers user root

/etc/group has:
sshlogin:x:199:user,root
```

and ~user/.ssh and ~user/.ssh/authorized_keys are chmod 600 and chown user:user

ssh user  from client results in
Permission denied (publickey).

Could someone please enlighten me what could be preventing ssh login to ~user?   And yes I would like to disable root ssh access, but it would be nice to be able to ssh into user first ;-)

---

### Post by Lars Noodén on 2011-04-22
Is user a member of the group "sshlogin" ?

What is the output of groups?
```

groups user

```

Take out the "AllowUsers user" and work with the groups only, it makes it tidier to manage.

---

### Post by spynappels on 2011-04-22
Have you added the key to authorized_keys in the .ssh folder of the user's home directory? And set the permission of the authorized_keys file to 600 and the .ssh folder to 700?

---

### Post by tribalvibes on 2011-04-22
> **spynappels said:**
> Have you added the key to authorized_keys in the .ssh folder of the user's home directory? And set the permission of the authorized_keys file to 600 and the .ssh folder to 700?

Oops, the chmod 700 ~user/.ssh got us a step further but now ssh -vv from the client shows:

debug1: Offering public key: /Users/user/.ssh/key
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-rsa blen 279
debug2: input_userauth_pk_ok: fp eb:47:91:24:1a:3d:45:dd:a4:d5:b0:ca:ca:65:bd
Connection closed by (hostip)

groups user
user sshlogin

and  /etc/ssh/sshd_config has:
AllowGroups sshlogin


So there's some other access restriction? Thoughts?

---

### Post by tribalvibes on 2011-04-23
Ah, user was missing from /etc/shadow

Thanks! :D

---

