---
title: "VirtualBoxose"
date: 2009-02-02
forum: Virtualisation
---

### Post by dontgetshocked on 2009-02-02
If I created a machine on a drive, can I copy it to another drive and then it will work?

---

### Post by Jose Catre-Vandis on 2009-02-02
Read the Help

There is a command line option for VBoxManage called clonevdi which will do this for you, although I have just copied over the vdi to another machine, set up a new VM with this vdi and had it running. You just can't do this on the same machine unless you use clonevdi.

---

