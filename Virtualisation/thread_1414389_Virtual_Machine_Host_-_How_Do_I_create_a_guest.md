---
title: "Virtual Machine Host - How Do I create a guest?"
date: 2010-02-23
forum: Virtualisation
---

### Post by neilneil2000 on 2010-02-23
Whoah Whoah Whoah Hold Up!  Before I get flamed to pieces for asking such a simple question I will qualify it, so please bare with me.

I have a standalone server that I have install 9.10 Server Edition on, choosing "Virtual Machine Host" from the install options.  I am aware that this installs KVM and associated tools but that is a bout the limit of my knowledge.

I have done some reading, and I understand the concepts of virtualisation however all the KVM HOW-TOs reference installing additional packages, namely "python-vm-builder".  However I find it difficult to believe I would need additional packages when there is a tasksel function to turn the server into a VM host.

Am I missing something, or is [unlikely] the install CD missing something.

I realise I can just install these extra packages, but the server is not connected to the Internet and it is a bit of a faff to download packages, transfer them, install them, find I have missing dependencies or need others, and repeat...

Any info will be appreciated

Thanks in advance

---

### Post by dcstar on 2010-02-27
> **neilneil2000 said:**
> Whoah Whoah Whoah Hold Up!  Before I get flamed to pieces for asking such a simple question I will qualify it, so please bare with me.

I have a standalone server that I have install 9.10 Server Edition on, choosing "Virtual Machine Host" from the install options.  I am aware that this installs KVM and associated tools but that is a bout the limit of my knowledge.

I have done some reading, and I understand the concepts of virtualisation however all the KVM HOW-TOs reference installing additional packages, namely "python-vm-builder".  However I find it difficult to believe I would need additional packages when there is a tasksel function to turn the server into a VM host.

Am I missing something, or is [unlikely] the install CD missing something.
........

Any install CD has only a finite amount of space and decisions have to be made as to what packages are on the CD and what will only be available by download.

10,000 people will have 10,000 **different** opinions as to what should be on the CD, only one opinion will count and that is the one the Ubuntu developers arrive at.

You can manually download any package from:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by neilneil2000 on 2010-03-03
I understand and appreciate your reply but it doesn't really answer the question I was asking.

Given that Ubuntu have decided that "Virtual Machine Host" should be selectable in the install menu.  Therefore I would assume it would install the relevant packages to install virtual machines.  But it would appear that either:

a) It is missing one or more packages OR
b) There is another way to install virtual machines that I cannot find documented on the web

---

### Post by bodhi.zazen on 2010-03-03
> **neilneil2000 said:**
> I realise I can just install these extra packages, but the server is not connected to the Internet and it is a bit of a faff to download packages, transfer them, install them, find I have missing dependencies or need others, and repeat..

If the CD is missing packages you need, the easiest solution is to connect teh server to the internet.

I advise you file a bug report if you feel there is a package missing from the server CD ;)

I am not sure exactly what you are needing, but you could also build a custom CD or use AptOnCD or perhaps there is a better solution.

---

