---
title: "Upgrade JDK From 32 To 64"
date: 2018-11-09
forum: Ubuntu/Debian BASED
---

### Post by bigpappajohn1984 on 2018-11-09
I have the JDK 32 bit installed on my 64 bit system.  I don't recall installing any version of JDK but when I run java -version this is my output
```

openjdk version "1.8.0_181"
OpenJDK Runtime Environment (build 1.8.0_181-8u181-b13-1ubuntu0.16.04.1-b13)
OpenJDK Server VM (build 25.181-b13, mixed mode)

```

I am running the below OS
```

Distributor ID:    Zorin
Description:    Zorin OS 12.4
Release:    12
Codename:    xenial

```

What would be the step by step to upgrade to 64 bit JDK?

EDIT -
But when I execute -[COLOR=#242729][FONT=Consolas]-print-architecture it gives me the below output which would actually be a 32 bit OS, right?
```

[/FONT][/COLOR]dpkg --print-architecture
i386

```

And it looks to me (altho I am new) thisshows I am running a 32 bit OS also
```

uname -a
Linux owner-HP-Compaq-nc8430-RB553UT-ABA 4.15.0-38-generic #41~16.04.1-Ubuntu SMP Wed Oct 10 20:10:45 UTC 2018 i686 i686 i686 GNU/Linux

```

---

### Post by QIII on 2018-11-09
Moved to Ubuntu/Debian BASED.

---

