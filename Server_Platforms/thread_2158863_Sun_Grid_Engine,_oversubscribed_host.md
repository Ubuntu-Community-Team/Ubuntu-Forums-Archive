---
title: "Sun Grid Engine, oversubscribed host"
date: 2013-06-30
forum: Server Platforms
---

### Post by zee on 2013-06-30
Hi,
  Because of a hard dribe failure I had to reinstall Ubuntu 12.04, which entails reinstalling Sun Grid Engine.

  The problem I am facing now is that jobs are not queued anymore but they start immediately after they're submitted instead of waiting for the CPUs to become available which leads to my workstation being oversubscribed. This happens whether I use threaded or openmpi versions of the codes (Gromacs, CHARMM). The workstation is a 12-core, 24-threaded HP workstation. 

  I tried changing the settings to lower the number of available CPUs but that didn't seem to help.

  Any ideas why I'm observing such a strange behaviour?

Thanks,
zee

---

