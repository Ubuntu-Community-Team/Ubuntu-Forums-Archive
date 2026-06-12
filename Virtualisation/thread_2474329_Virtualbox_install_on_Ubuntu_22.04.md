---
title: "Virtualbox install on Ubuntu 22.04"
date: 2022-04-26
forum: Virtualisation
---

### Post by brian.modlin on 2022-04-26
I have downloaded the install files from Virtualbox and would like to install the latest version.  When I do so in says I have unmet dependencies.  Not sure where to go from here.  I would like to install using the Virtualbox repo so it will automatically update. (Hope I described that correctly) . I am new to linux.

---

### Post by &amp;KyT$0P# on 2022-04-26
> **brian.modlin said:**
> I am new to linux.

Sorry but since Oracle has not yet released a VirtualBox build for 22.04, using the official build on 22.04 requires the knowledge level of an advanced, experienced Ubuntu user.  I tried to do it and it may have caused several issues with my system, including boot issues.

Can you take one of these 3 options? -

1) Wait for Oracle to release a 22.04 compatible VirtualBox build.

2) Try the version of VirtualBox available in the standard Ubuntu 22.04 repositories.

3) Install an Ubuntu release which the current Oracle build of VirtualBox does support.  If you choose this option I would recommend 20.04 LTS.

---

### Post by QIII on 2022-04-26
It might be helpful to mention which dependencies are unmet.

Are you trying to install from the Ubuntu repos or directly from Oracle?

---

