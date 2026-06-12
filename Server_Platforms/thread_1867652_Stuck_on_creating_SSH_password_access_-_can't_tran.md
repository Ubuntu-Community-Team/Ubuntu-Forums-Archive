---
title: "Stuck on creating SSH password access - can't transfer public key priv"
date: 2011-10-23
forum: Server Platforms
---

### Post by babbageii on 2011-10-23
Hi All,

Running 10.04 on Amazon EC2 instance.
Currently logging in via SSH using key file, passed through using:
```
ssh -i key.pem user@xx.xx.xx.xx
```

I'm trying to create *password* access, so I created keys on my own computer with:

```
ssh-keygen -t dsa
```

But then, when I try to pass the public key file to the remote server - I get 'permission denied (public key)':

```
scp .ssh/id_dsa.pub -i key.pem user@xx.xx.xx.xx:
```

Has anyone had a similar problem, or know's what I'm doing wrong here?

---

### Post by koenn on 2011-10-23
please remind me, why do you need keys if uou're going for **password** authentication ?

---

