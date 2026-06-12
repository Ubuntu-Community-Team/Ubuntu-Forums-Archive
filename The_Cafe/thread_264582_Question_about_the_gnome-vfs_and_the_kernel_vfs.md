---
title: "Question about the gnome-vfs and the kernel vfs"
date: 2006-09-24
forum: The Cafe
---

### Post by NoTiG on 2006-09-24
Just a question... supposedly there is already a VFS implemented in the kernel. Doesnt gnome-vfs duplicate this functionality? Wasnt reiserFS reprimanded for this same thing? and also....... Is the reason why gnome has its own VFS so that its portable to other OS's ? Can it be modularized so that it can use the kernels VFS ? would there be any advantages if it did use the kernels VFS? thanks if anyone can answer my questions.

---

### Post by Bloodfen Razormaw on 2006-09-24
The kernel VFS is just an abstraction over the file system internals.  When you implement a filesystem you must do so specifically for the VFS of the target system so that they can communicate.  GNOME VFS is, in theory, an abstraction over all of that, adding network transparency (in practice GNOME VFS is too broken to do that, and is largely unused by applications).

---

### Post by NoTiG on 2006-09-24
so the kernel VFS is to low level to be used ?

---

### Post by xp_newbie on 2006-11-01
My thoughts and questions, too.

What good is Gnome VFS for, if I can list the file inside a pretty window, but I cannot access them using GNU Emacs, xterm and other legacy unix-style command line tools?

I would appreciate any insight regarding the rational behind Gnome's approach.

Thanks,
Alex

---

