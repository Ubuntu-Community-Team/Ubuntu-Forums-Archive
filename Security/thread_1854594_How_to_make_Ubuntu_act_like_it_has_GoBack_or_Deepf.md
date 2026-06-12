---
title: "How to make Ubuntu act like it has GoBack or Deepfreeze?"
date: 2011-10-04
forum: Security
---

### Post by richterlevania3 on 2011-10-04
Well, the title says it all: I want a server that I'm building to not keep any file modification done, each time it reboots. Like Norton GoBack or Deepfreeze does on Windows.

Any idea?

Thanks in advance.

---

### Post by samigina on 2011-10-04
Take a look to [Ofris]("http://www.youtube.com/watch?v=-79gQG-UGZo&feature=player_embedded")

---

### Post by HermanAB on 2011-10-05
Simple really:
Make a virtual machine on VMware or Virtualbox.  Make a tar ball of the VM directory.  Each time you restart the VM with vmrun, untar the whole ball of wax first.

---

### Post by Pynalysis on 2011-10-05
> **HermanAB said:**
> Simple really:
Make a virtual machine on VMware or Virtualbox.  Make a tar ball of the VM directory.  Each time you restart the VM with vmrun, untar the whole ball of wax first.

You could make a snapshot of the virtual machine. Then, on reboot just restore the snapshot to return the virtual machine back to a previous state.

---

### Post by richterlevania3 on 2011-10-05
Ofris will make it. Virtual Machines are not a viable option.

Thanks for the help.

---

