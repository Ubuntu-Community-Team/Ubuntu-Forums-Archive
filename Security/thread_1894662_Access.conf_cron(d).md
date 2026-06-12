---
title: "Access.conf cron(d)?"
date: 2011-12-13
forum: Security
---

### Post by theraser on 2011-12-13
Hallo everybody,

I'm the new one here. 

I got a (maybe very simple) question: the man page of access.conf told me that 

"The third field, the *origins* field, should be a list of one or  more tty names (for non-networked logins), host names, domain names  (begin with "."), host addresses, internet network numbers (end with "."), internet  network addresses with network mask (where network mask can be a decimal  number or an internet address also), *ALL* (which always matches) or *LOCAL*." ([http://linux.die.net/man/5/access.conf](http://linux.die.net/man/5/access.conf))

But there even this example:

"User *root* should be allowed to get access via *cron*, X11 terminal *:0*, *tty1*, ..., *tty5*, *tty6*. + : root : **crond** :0 tty1 tty2 tty3 tty4 tty5 tty6"


What is "crond" in this context? It should be one of the options above (TTY names, host names etcetera).


Thanks for your time,
theraser

---

### Post by Dangertux on 2011-12-13
It's the service that user root is allowed from. IE : a from job run from root has access as well as xterm and tty1-6

Since a cron job  is run in the context of a user, it can be defined separately.

---

### Post by theraser on 2011-12-13
That could be correct. But why isn't "service" listed in the man page?

---

### Post by theraser on 2012-01-10
*push*

---

