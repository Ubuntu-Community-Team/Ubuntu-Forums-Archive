---
title: "GPG agent"
date: 2015-07-01
forum: Security
---

### Post by fugu2 on 2015-07-01
Does anyone know how to get the gpg agent to forget a cached passphrase from the command line? (like the way "sudo -k" will get sudo to forget)

---

### Post by NoWayWin8 on 2015-07-02
```
$ echo RELOADAGENT | gnome-keyring-daemon
```

---

### Post by fugu2 on 2015-07-09
I think maybe I should have been more clear about what I was looking for
```

$ gpg --armor --detach-sign test 

You need a passphrase to unlock the secret key for
user: "Username <username@example.com>"
2048-bit RSA key, ID 12345678, created 2015-07-09
(it asks for my passphrase)
$ ls test*
test  test.asc
$ gpg --armor --detach-sign test 

You need a passphrase to unlock the secret key for
user: "Username <username@example.com>"
2048-bit RSA key, ID 12345678, created 2015-07-09
(it doesn't ask for my passphrase)

```
i want to reset it at this point. This...
```

$ echo RELOADAGENT | gnome-keyring-daemon

```
...doesn't work in this situation

---

