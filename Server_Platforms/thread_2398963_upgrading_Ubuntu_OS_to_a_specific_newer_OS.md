---
title: "upgrading Ubuntu OS to a specific newer OS"
date: 2018-08-20
forum: Server Platforms
---

### Post by urimda on 2018-08-20
Hi,

I've Ubuntu 16.04.2 Os and I wish to upgrade it to Ubuntu 16.04.4 version.
Anything I try, It is either being upgraded to 16.04.5 or to 18.01 versions.

could anyone please explain how can I upgrade my Ubuntu to a specific version I want?

Thanks in advance.

---

### Post by westie457 on 2018-08-20
16.04.2 and 16.04.4 have both reached EOL and those repos have been removed.
Your available choices are here and in the links on that page. [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by PaulW2U on 2018-08-20
> **urimda said:**
> I've Ubuntu 16.04.2 Os and I wish to upgrade it to Ubuntu 16.04.4 version.
Anything I try, It is either being upgraded to 16.04.5 or to 18.01 versions.
In a terminal, what do the following commands show?
```

lsb_release -a
uname -a

```
If you start with a .2 minor release of an LTS and continue to update you will in turn reach .3, .4 and .5. There's no way to stop that happening and keep fully updated.

Why do you wish to stop at 16.04.4 and not progress to 16.04.5 which will contain bug fixes and security updates?

Is it the [LTS Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") that is forcing an upgrade of parts of the OS that you wish to not upgrade?

---

