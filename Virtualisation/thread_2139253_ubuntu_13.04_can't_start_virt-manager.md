---
title: "ubuntu 13.04 can't start virt-manager"
date: 2013-04-26
forum: Virtualisation
---

### Post by bmullan on 2013-04-26
I have been using virt-manager for a long time but after upgrade to ubuntu 13.04 I can no longer start virt-manager?

I've done some searches but can't find any bugs reported.

Anyone got any clues how to troubleshoot this?

---

### Post by gwm on 2013-04-28
Hi,
I too am having problems.
I figure that possibly there is some incompatibility in the configuration files. To handle that, I moved the .vdi file to another folder and deleted the Vitrualbox VMs directory that used to contain it.

Next I went looking for a release on the Oracle website. They don't have a 13.04 version. That means we are trying to make the older one work with an unsupported kernel. To recompile the kernel, we need the correct header files and they don't exist . . . etc.

Next I went to the Ubuntu Software Center and installed their version of VirtualBox. As I understand it, this is the OSE version (which I guess probably means something like Open Source Edition) - I read somewhere in the forums that Oracle don't support it.

I started this version and created a new virtual machine without a hard drive. This recreated the directory that I had earlier deleted and I moved the .vdi file into it. Finally, under the settings for my new virtual machine, I added an exisiting hard drive and pointed it to the .vdi file.

Now it all is well in the jungle!!

:guitar:

---

### Post by ibjsb4 on 2013-04-28
When the last time you looked?

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

