---
title: "Kernel issue"
date: 2006-04-12
forum: Server Platforms
---

### Post by Roxxor on 2006-04-12
Hi!

I will enable kernel encryption support, but first, I have do download the newest kernel from kernel.org. 

Where is the preinstalled Ubuntu kernel located? All modules etc.?

---

### Post by tseliot on 2006-04-12
[QUOTE=Roxxor]Hi!

I will enable kernel encryption support, but first, I have do download the newest kernel from kernel.org. 

Where is the preinstalled Ubuntu kernel located? All modules etc.?[/QUOTE]
The kernel is in /boot
The modules: /lib/modules/name_of_the_kernel


I hope you're not planning to remove the files physically without uninstalling the packages.

---

### Post by Roxxor on 2006-04-12
No, I am just going to replace the kernel in /boot with a newer one.

What will happen if I uninstall the kernel packages? Won't I be able to teboot then?


Is it possible to configure and recompile the currently installed Ubuntu kernel?

---

### Post by tseliot on 2006-04-13
[QUOTE=Roxxor]No, I am just going to replace the kernel in /boot with a newer one.

What will happen if I uninstall the kernel packages? Won't I be able to teboot then?


Is it possible to configure and recompile the currently installed Ubuntu kernel?[/QUOTE]
It's all explained in my guide (which is very esy to follow):
[HOWTO: Kernel Compilation for Newbies]("http://www.ubuntuforums.org/showthread.php?t=85064")

---

