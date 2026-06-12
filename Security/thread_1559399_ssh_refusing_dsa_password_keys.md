---
title: "ssh refusing dsa password keys"
date: 2010-08-23
forum: Security
---

### Post by Onesimus on 2010-08-23
I am trying to log in remotely to my server using ssh.  But the server refuses to accept my keys (when they are generated using dsa).  Here's what I do:

```
ssh-keygen -t dsa
ssh-copy-id user@server-ip
```

and when I try to log in I get:

```
Agent admitted failure to sign using the key.
```

And I can't login. However, when I do:

```
ssh-keygen -t rsa -b 1024
ssh-copy-id user@server-ip
```

Everything works fine !

Any suggestions ?

---

### Post by CharlesA on 2010-08-23
Same thing happened to me when I tried dsa keys. I've just using rsa keys instead.

---

### Post by Bachstelze on 2010-08-23
```
ssh-copy-id -i ~/.ssh/id_dsa.pub user@host
```

You need to give it the path to the identity file.  If you don't, it defaults to id_rsa.pub, so it won't find your DSA key.

---

### Post by Onesimus on 2010-08-23
Many thanks !

Problem solved

---

### Post by rookcifer on 2010-08-23
I would use RSA keys over DSA keys any day.

---

