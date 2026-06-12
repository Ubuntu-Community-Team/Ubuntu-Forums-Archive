---
title: "How do you get rid of kde-minimal"
date: 2012-01-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jebradley on 2012-01-12
I upgraded an Oneiric system to Precise via apt-get (which had been upgraded from Natty via apt-get, and so on), and have a conflict with upgrading kde-standard, getting a conflict with 'kde-minimal'. When I try to remove kde-minimal with dpkg, it tells me that the package doesn't exist. How do I get rid of it so that I don't have the conflict to upgrading kde-standard?

---

### Post by PaulW2U on 2012-01-12
It doesn't seem to exist here either:

```
paul@DELL:~$ apt-cache show kde-minimal
N: Can't select versions from package 'kde-minimal' as it is purely virtual
N: No packages found
```

Running Ubuntu at the moment rather Kubuntu. Not that it matters to the above query. Not listed in Synaptic or aptitude either. :confused:

---

### Post by ventrical on 2012-01-12
dis you try

sudo apt-get remove --purge

 for any config files that may be left behind?

---

### Post by jebradley on 2012-01-16
'sudo apt-get remove --purge' does nothing.
'sudo apt-get remove --purge kde-minimal' gives me an error message, "Virtual packages like 'kde-minimal' can't be removed"

It amazes me as to how a virtual package that doesn't exist and can't be deleted keeps a package from being installed because it breaks a dependency.

---

