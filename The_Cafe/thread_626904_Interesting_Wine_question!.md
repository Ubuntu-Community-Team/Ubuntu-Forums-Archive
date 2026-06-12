---
title: "Interesting Wine question!"
date: 2007-11-29
forum: The Cafe
---

### Post by khurrum1990 on 2007-11-29
Hi, what if I copy a fresh install of Windows drive c: into Wine drive c? Will all my programs work, has some one tried it cause then no files required by some programs would be missing.

---

### Post by Dimitriid on 2007-11-29
Short answer? No. The only thing that can use all your windows files to simulate a windows environment right now its a virtual machine appliance ( Qemu, vmware ).

So many applications simply do things wine developers haven't figured out yet how to replicate. And even those who do, if you just copy the files that won't make the necessary changes on the windows registry. So you would have to possibly manually make each change for each program, etc.

---

### Post by boast on 2007-11-29
that doesn't even work between windows computers right?

Well, at least some programs will show registry errors?

---

### Post by Dimitriid on 2007-11-29
That is correct: even on windows copying and pasting programs without the corresponding registry entry with often result in malfunction.

---

### Post by khurrum1990 on 2007-11-29
Thanks for the information.

---

