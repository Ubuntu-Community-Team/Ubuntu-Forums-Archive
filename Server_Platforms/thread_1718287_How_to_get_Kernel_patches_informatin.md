---
title: "How to get Kernel patches informatin"
date: 2011-03-31
forum: Server Platforms
---

### Post by Naqib on 2011-03-31
Hi everyone, 
I am really new with LINUX in fact, it is my first time I am working in linux.

How to get the following information using terminal in ubuntu I googled entire internet but could not find it:

1. What patches has been selected(installed) in my installed kernel(current kernel).
2. List of installed drivers.

Thanks for help

---

### Post by BkkBonanza on 2011-03-31
There are two sources for kernel info.

First is the all definitive [kernel.org]("http://kernel.org"). Their main page allows you to view kernel patches. 

Next is the [Ubuntu kernel archive]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") which also has patches/change info. Go there and find the kernel release you have.

For drivers do you mean you want to know which ones are compiled in or loaded currently? For the current drivers loaded you can type **lsmod** to see. But for compiled into the kernel I don't know. I presume that info would also be in the Ubuntu kernel info above.

Edit: ah yes, just checked and the BUILD.LOG file seems to show the drivers built into the kernel.

---

### Post by Naqib on 2011-03-31
Thanks a lot for your help.:P

---

