---
title: "scponly with chroot setup but user can STILL forward ports..."
date: 2009-09-24
forum: Security
---

### Post by graysky on 2009-09-24
I'm using scponly and have chrooted a user to his home directory.  I noticed however that I can ssh into the box enabling port forwarding which is a dangerous security breach in my opinion.  I'd like to have the ability keep port forwarding for other users, but for the scponly user, I'd like to disallow ssh port forwarding.  Anyone know how?

```
$ ssh nightshade -P 8081
username@nightshade's password:
Welcome to nightshade


```

---

### Post by cdenley on 2009-09-24
I believe the only way to prevent TCP forwarding is to set AllowTcpForwarding, which is a global setting. If you need to disable it for only some users, then you will need to run a seperate instance of sshd with a seperate configuration file listening on a different port.

---

### Post by bodhi.zazen on 2009-09-24
> **cdenley said:**
> I believe the only way to prevent TCP forwarding is to set AllowTcpForwarding, which is a global setting. If you need to disable it for only some users, then you will need to run a seperate instance of sshd with a seperate configuration file listening on a different port.

Actually you can set it on a per user basis if you use ssh keys. The documentation on this is hard to find however.

search on ssh forced commands

Basically on the server you add to your keys in ~/.ssh/authorized_keys

command=scp,no-port-forwarding,no-agent-forwarding,no-X11-forwarding,no-pty

See this blog for how I set this up for a svn server :

[http://blog.bodhizazen.net/linux/svnssh/](http://blog.bodhizazen.net/linux/svnssh/)

---

### Post by graysky on 2009-09-25
Thanks for the replies, all.  Turns out this can be accomplished by the addition of two new lines to the sshd_config:

```
Match user USERNAME
AllowTcpForwarding no
```

---

