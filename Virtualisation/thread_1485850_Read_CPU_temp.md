---
title: "Read CPU temp ?"
date: 2010-05-17
forum: Virtualisation
---

### Post by karmic-koala on 2010-05-17
I am running an Ubuntu server on a XP desktop in VMware. Is it possible to read the system's temperature and shutdown the VM down if temperature is too much.

Easy if this was ubuntu running ubuntu but this is windows running ubuntu.

Because VMs run in emulated environment they are almost never able to read the system values like cpu temp.

---

### Post by phrostbyte on 2010-05-18
You can try using WMI or some such to read the CPU temperature from the host, and then kill the process hosting Ubuntu when the CPU temp is too high.

---

### Post by karmic-koala on 2010-05-20
ooh fancy windows stuff, not familiar with windows, any linux like solution maybe? :)

---

