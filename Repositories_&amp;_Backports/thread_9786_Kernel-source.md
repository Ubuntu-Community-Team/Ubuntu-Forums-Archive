---
title: "Kernel-source"
date: 2005-01-01
forum: Repositories &amp; Backports
---

### Post by dersmi on 2005-01-01
I need to recompile my kernel, to add the USB Sagem 800 modem drivers. Where can I find the kernel source? Ubuntu is great!! I just want to get online now.

---

### Post by Randabis on 2005-01-01
[QUOTE=dersmi]I need to recompile my kernel, to add the USB Sagem 800 modem drivers. Where can I find the kernel source? Ubuntu is great!! I just want to get online now.[/QUOTE]
 sudo apt-cache search kernel-source

That should give you some choices

---

### Post by HankB on 2005-01-01
[QUOTE=Randabis]sudo apt-cache search kernel-source

That should give you some choices[/QUOTE]

Where is 2.6.8? 2.6.9? I can see no 2.6.9 since the installed kernel is at 2.6.8, but I would expect sources for the running packaged kernel.

My sources.list includes:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted universe multiverse


Do folks building custom kernels usually just go to the usual places? (kernel.org)

Is there anything customized in the Ubuntu kermel source package? Perhaps the .config?

thanks,
hank

---

### Post by az on 2005-01-01
It's linux-source-2.6.8

for the ubuntu kernel.

---

### Post by HankB on 2005-01-01
What's the difference between linux-source and kernel-source?

I would have never thought to search for linux-source. Really. ](*,) 

thanks,
hank

---

