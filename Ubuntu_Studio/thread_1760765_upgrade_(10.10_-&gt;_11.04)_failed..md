---
title: "upgrade (10.10 -&gt; 11.04) failed."
date: 2011-05-17
forum: Ubuntu Studio
---

### Post by billg04 on 2011-05-17
My upgrade filed at the last moment. 

Now, it's running the release 11.04, but could not load the kernel 2.6.38-8 (failed loading). I have to load the older kernel (2.6.35-28). 

How to fix the problem?

Thanks in advance.

---

### Post by jejeman on 2011-05-17
Try to reinstall that kernel.

---

### Post by billg04 on 2011-05-17
> **jejeman said:**
> Try to reinstall that kernel.

Thanks for the tip.

How to re-install it?  

Thanks for the help.:P

---

### Post by jejeman on 2011-05-17
Open synaptic, select the package you want to reinstall, right mouse click on it, choose "mark for reinstall", click apply on toolbar.
Youre package should look something like this
linux-image-2.6.38-8-generic

---

### Post by billg04 on 2011-05-17
> **jejeman said:**
> Open synaptic, select the package you want to reinstall, right mouse click on it, choose "mark for reinstall", click apply on toolbar.
Youre package should look something like this
linux-image-2.6.38-8-generic

Thanks. I'll give it a try.

---

### Post by cdoebbler on 2011-05-18
I load Ubuntu 10.10 then beta 11.04, but now everytime I run apt-get upgrade I get the following error: 

~$ sudo apt-get upgrade
[sudo] password for XX: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

---

