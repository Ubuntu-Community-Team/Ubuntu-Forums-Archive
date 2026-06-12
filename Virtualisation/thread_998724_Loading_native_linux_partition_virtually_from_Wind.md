---
title: "Loading native linux partition virtually from Windows"
date: 2008-12-01
forum: Virtualisation
---

### Post by SomeIdiot on 2008-12-01
I am sorry if this has been asked before, but I can't seem to find threads or websites discussing exactly this.

Is it possible to run a native linux partition from e.g. VMWare in Windows? So just to clarify, I am running Kubuntu and windows XP in a dual boot configuration, but I also want to be able to load the linux partition virtually from Windows (for the things that are not too demanding) besides being able to boot linux natively (for the more demanding stuff such as 3D graphics).

Is this possible at all? Feel free to just direct me to the threads/websites discussing this, that I am sure that I missed.

Thanks in advance. :)

---

### Post by Dedoimedo on 2008-12-01
Hello,

I think the first step would be install an ext2/3 driver utility in Windows to allow you to read ext2/3 partitions, and then when you create a virtual machine, use an existing partition and allow raw access.

Never tried it, but it could work. And always remember that these things can lead to data loss and whatnot, so backup thoroughly before testing.

Dedoimedo

---

### Post by bodhi.zazen on 2008-12-01
Yes. Look at the links in the Mega thread at the top of these forums, follow the how-to's on running XP from a physical partition.

The set up is similar, but easier with Linux partitions as there are no licensing or activation issues.

---

