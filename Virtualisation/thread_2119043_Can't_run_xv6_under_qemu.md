---
title: "Can't run xv6 under qemu"
date: 2013-02-22
forum: Virtualisation
---

### Post by gwowen on 2013-02-22
Hi folks,

I've been having a bit of a problem getting xv6 working on qemu. I'm running Ubuntu 64-bit, and I've installed libc6-dev-i386 so I can get the code to compile. I typed "make" and it compiled perfectly well, but now I've run into a few problems.

I type "make qemu" next and it says: 
"Error: Couldn't find a working QEMU executable.
*** Is the directory containing the qemu binary in your PATH
*** or have you tried setting the QEMU variable in Makefile?"

Just typing "qemu" in gets me:

"No command 'qemu' found, did you mean:
 Command 'qtemu' from package 'qtemu' (universe)
 Command 'aqemu' from package 'aqemu' (universe)
qemu: command not found"

and I thought it might not have installed correctly, but "whereis qemu" gets me

"qemu: /etc/qemu /usr/share/qemu /usr/share/man/man1/qemu.1.gz"

which seems perfectly fine to me. Has anyone encountered this problem before when trying to build and run xv6?

---

