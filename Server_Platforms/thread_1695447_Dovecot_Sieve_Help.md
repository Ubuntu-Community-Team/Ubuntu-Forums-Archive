---
title: "Dovecot Sieve Help"
date: 2011-02-25
forum: Server Platforms
---

### Post by nmahadkar on 2011-02-25
I am trying to get the sieve plugin in dovecot to work on 10.10.  The problem is very time I enable the dynamic plugin by editing the dovecot.conf using the following lines
'```
protocol lda {
..
  # Support for dynamically loadable plugins. mail_plugins is a space separated
  # list of plugins to load.
  mail_plugins = sieve # ... other plugins like quota
}
```

dovecot refuses to start.

There is not a lot of help out there regarding this so any help is appreciated.

---

### Post by Zenguy on 2011-12-22
Did you ever get a solution for this? I am experiencing the same problem.

---

