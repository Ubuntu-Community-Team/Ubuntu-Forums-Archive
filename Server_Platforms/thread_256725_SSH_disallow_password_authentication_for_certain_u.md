---
title: "SSH: disallow password authentication for certain users"
date: 2006-09-13
forum: Server Platforms
---

### Post by mozz on 2006-09-13
Hi,

I am running an openssh server with a handful of clients, until now I've used public-key auth ONLY.

However I need *one* user to able to login with a clear text password - I still want to force all the others to use pubkey auth.
But if I activate

```
PasswordAuthentication yes
```

then *all* clients are able to login with their passwords.

Does anyone know a solution for this? Thanks in advance!

---

### Post by Frank-Hamersley on 2006-09-14
Could you run 2 instances of sshd - on different ports with discrete configs?

Never tried it but it might be possible if you chroot them in the right way.

Cheers, Frank.

---

### Post by mozz on 2006-09-14
good idea .. just have to make sure that I don't mix them up, when they both write to the logs..

thanks!

---

### Post by dante on 2006-09-14
Another alternative: allow password authentication, but lock the passwords
for all but the one user.  The users with locked passwords will still be
able to authenticate with public keys.  I can't test this at the moment,
but I'm pretty sure I've done this before with a chroot'ed user account
setup I was testing at one time.

---

