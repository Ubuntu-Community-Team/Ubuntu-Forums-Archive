---
title: "PHP/Apache Issue?"
date: 2007-11-14
forum: Server Platforms
---

### Post by godsfshrmn on 2007-11-14
I just checked out my error.log file and found 1000s of instances of the same entry. The logfile was 11mb saying this repeatedly
```
[Sun Nov 11 06:26:01 2007] [error] an unknown filter was not added: PHP

```

I have no idea what that means. PHP is working just fine on my website:confused:

---

### Post by MJN on 2007-11-14
Do you have any filters in your config? (run **grep -ir filter /etc/apache2/***)

This error can occur if you're using the old filtering mechanism (SetOutputFilter etc) as opposed to the AddType handler format.

Mathew

---

