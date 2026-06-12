---
title: "vmware player"
date: 2011-10-29
forum: Virtualisation
---

### Post by Vinger on 2011-10-29
Hello,

I installed VMWare player on my Kubuntu machine, but when i start it, i get this message:

>  **VMware Kernel Module Update**
Before you can run VMware Player, several modules must be compiled and loaded into the running kernal:
**Kernel Headers 3.0.0-12-generic**
Kernal headers for version 3.0.0-12-generic were not found. If you installed them in a non-default path you can specify the path below. Otherwise refer to your distrution's documentation for installation instruction and click Refresh to search again in the default locations.

When i see my package manager, the package
Linux-headers-3.0.0-12-generic 
is installed...

anyone an idea?

tx!

---

### Post by nothingspecial on 2011-10-29
Moved to Virtualization.

---

### Post by Vinger on 2011-11-04
No-one an idea?

tx.

---

### Post by fjgaude on 2011-11-04
You might try this command and try again to install Player:

```
sudo apt-get install build-essential
```

Someone else may have other ideas... you need the headers to the kernels that are not likely installed. I think this command pulls them in, can't remember.

---

### Post by Vinger on 2011-11-05
Thanks!

But it doesn't work (was already installed):
> koenh@koenh-Kubuntu-11:~$ sudo apt-get install build-essential
[sudo] password for koenh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.


grz.

---

### Post by dcstar on 2011-11-05
Re-install the missing headers.

---

### Post by Vinger on 2011-11-06
hello,

i reinstalled 
* linux-headers-generic
* linux-headers-3.0.0-12-generic
* linux-headers-3.0.0-12

afterwards, i started vmware, but succes.

any ideas?
tx!

---

