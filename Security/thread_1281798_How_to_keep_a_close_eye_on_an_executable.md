---
title: "How to keep a close eye on an executable?"
date: 2009-10-03
forum: Security
---

### Post by Mourvedre on 2009-10-03
Hi all,

I've just had a security update on my system: libpq5.

`apt-cache show libpq5` tells me it "is a C library that enables user programs to communicate with the PostgreSQL database server."

I'm not running a Postgres database and I'm never connecting to one either.

How can I keep a close watch on who's calling a lib/file/executable?

Preferably an automated method that does not require my eyes to be glued to the screen...

Thanks a head for any lead,
Cheers,
M.

---

### Post by unutbu on 2009-10-03
```
apt-cache rdepends libpq5
```

returns all the packages that list libpq5 as a dependency. I would start by looking there to find out why libpq5 is installed on the system. Amarok, for instance, is on that list.

---

### Post by -=hazard=- on 2009-10-03
Maybe it's from apache or some ftp server or python.

---

### Post by Mourvedre on 2009-10-06
Thanks a lot Unutbu: I found the guilty one :)

---

### Post by cariboo on 2009-10-06
It may help others, if you explained what the solution was.

---

### Post by -=hazard=- on 2009-10-07
> **cariboo907 said:**
> It may help others, if you explained what the solution was.

Agree, I'm curious too.

---

### Post by unutbu on 2009-10-07
It would be interesting to hear how Mourvedre did it, but upon further thought, one could do it this way:

Save this to ~/bin/find_installed_reverse_dependencies.py

[PHP]#!/usr/bin/env python
import sys
from subprocess import Popen,PIPE,STDOUT
proc=Popen('apt-cache rdepends %s'%sys.argv[1], shell=True, stdout=PIPE, )
rdepends=set([pkg.replace('|','') for pkg in proc.communicate()[0].split()[3:]])
proc=Popen("aptitude -F '%?p' search '~i'", shell=True, stdout=PIPE, )
installed=set(proc.communicate()[0].split())
print '\n'.join(list(installed.intersection(rdepends)))
[/PHP]
Make it executable:
```

chmod +x ~/bin/find_installed_reverse_dependencies.py
```

Run it like this:
```

~/bin/find_installed_reverse_dependencies.py libpq5
```

This will print all installed packages that list libpq5 as a dependency.

PS. Note that if A depends on B depends on C, then 
```

~/bin/find_installed_reverse_dependencies.py C 
```

will only print B, not A.

---

