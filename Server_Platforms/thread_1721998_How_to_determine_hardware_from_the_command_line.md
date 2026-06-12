---
title: "How to determine hardware from the command line?"
date: 2011-04-05
forum: Server Platforms
---

### Post by MakOwner on 2011-04-05
I have a headless server set up with no GUI on board.

I know there is some way to display the installed hardware , I just can't remember how.

What I'm looking for in particular is determine the type and speed of the PCI-e slots.

---

### Post by Doug S on 2011-04-05
The command: lspci
will list the pci hardware.

---

### Post by MakOwner on 2011-04-05
> **Doug S said:**
> The command: lspci
will list the pci hardware.

Thanks.  I had an absolute brain fart.
I was poking around in /proc looking for this output.

](*,)

---

