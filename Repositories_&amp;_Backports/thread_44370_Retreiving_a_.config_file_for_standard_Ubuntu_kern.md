---
title: "Retreiving a .config file for standard Ubuntu kernel"
date: 2005-06-25
forum: Repositories &amp; Backports
---

### Post by gimpy on 2005-06-25
How do i get the .config file that made my kernel? I used one from the install cd. uname -r gives me 2.6.10-5-386 and I dont see the source package for this version using synaptic.  Can I recreate that .config file exactly or must I make a new kernel? Would the .config file be the same that comes with the kernel-source-2.6.10 package? Or maybe I'm barking up the wrong tree. I'm assuming I need this to run through making some needed output files. cdemu ([http://cdemu.sourceforge.net](http://cdemu.sourceforge.net)) says it can't find the linux/version.h file and I thought running thru the build process would create that file. Am I just being stupid and missing something obvious? Any information would be appreciated.

---

### Post by az on 2005-06-25
Use the linux-headers for your kernel to make a module.

If you need the config, they are in /boot.

Install linux-tree for the patched source.

---

### Post by gimpy on 2005-06-25
flawless. thank you.

---

