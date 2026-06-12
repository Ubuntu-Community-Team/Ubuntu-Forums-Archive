---
title: "Unbound Syntax Error"
date: 2011-04-27
forum: Server Platforms
---

### Post by Blairboy on 2011-04-27
Hey all, started configuring Unbound DNS, but it complains about syntax in the first line of one of my zones.  The line reads ```
local-zone: "kincke.com." static
```

running unbound-checkconf yields ```
error: syntax error
```

and ```
read /etc/unbound/zones/kincke.com.zone failed: 1 errors in configuration file
```

According to the documentation and multiple other websites, that line is perfect, but it still won't work.  I also tried a newer version from a svn ppa, but no dice.  Running ubuntu 10.04.

---

