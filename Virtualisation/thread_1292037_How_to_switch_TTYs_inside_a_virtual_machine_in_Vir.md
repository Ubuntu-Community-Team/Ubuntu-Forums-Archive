---
title: "How to switch TTYs inside a virtual machine in VirtualBox?"
date: 2009-10-15
forum: Virtualisation
---

### Post by Cuddles McKitten on 2009-10-15
I'm running MINIX in VirtualBox and I can't switch between TTYs.  Whenever I try, it switches on the host machine!  Anyone have any suggestions to try?

(Note: MINIX doesn't come with chvt, so I can't even use that).

---

### Post by prshah on 2009-10-15
> **Cuddles McKitten said:**
> I'm running MINIX in VirtualBox and I can't switch between TTYs.  Whenever I try, it switches on the host machine!  

Use the "host" key; typically right ctrl. Eg, instead of Ctrl+Alt+F1, use RIGHT CTRL+F1. (Ctrl+Alt+Del = RIGHT CTRL+DEL) etc.

---

### Post by Cuddles McKitten on 2009-10-15
> **prshah said:**
> Use the "host" key; typically right ctrl. Eg, instead of Ctrl+Alt+F1, use RIGHT CTRL+F1. (Ctrl+Alt+Del = RIGHT CTRL+DEL) etc.

Worked perfectly.  Thanks!

---

