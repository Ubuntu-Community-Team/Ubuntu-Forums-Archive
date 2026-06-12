---
title: "VBox Gutsy server issue"
date: 2008-02-05
forum: Virtualisation
---

### Post by jdix123 on 2008-02-05
I'm running Gutsy as a host, and installed Ubuntu 7.1 Server into a virtual machine.  No problems with the installation, but when I try to boot into the vm I get a 

Kernel Panic:  CPU too old...

Ideas?

---

### Post by jdix123 on 2008-02-07
bump

---

### Post by fjgaude on 2008-02-07
Are you able to run **sudo /usr/bin/vmware-config.pl** from the Ubuntu command line?

---

### Post by jdix123 on 2008-02-12
No -- I'm not using VMware.  I'm using Virtual Box.

---

### Post by Peter09 on 2008-02-12
is itr 32 bit or 64 bit. Vbox does not support 64 bit guests

---

### Post by johnnybirdman on 2008-02-12
> **jdix123 said:**
> I'm running Gutsy as a host, and installed Ubuntu 7.1 Server into a virtual machine.  No problems with the installation, but when I try to boot into the vm I get a 

Kernel Panic:  CPU too old...

Ideas?

You can [[COLOR="DarkOrange"]_see here_[/COLOR] ]("http://www.virtualbox.org/wiki/Guest_OSes")that VB does not work with server versions.  However, I was able to get 7.10 server to work in VB by following the instructions in [[COLOR="DarkOrange"]_this post_[/COLOR]]("http://forums.virtualbox.org/viewtopic.php?t=2650&highlight=kernel+panic+cpu").
Best of luck.
J.

---

