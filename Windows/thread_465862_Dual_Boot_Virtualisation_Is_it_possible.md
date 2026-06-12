---
title: "Dual Boot Virtualisation: Is it possible?"
date: 2007-06-06
forum: Windows
---

### Post by zoqaeski on 2007-06-06
Heylo all
I'm running a dual boot XP - Ubuntu Feisty system, of which approximately half my hd capacity is devoted to each. However, I never use Windows unless I have to print or something (I can't seem to configure it properly; I'm on a Windows network and it just don't wanna work), and I find it a bit of a hassle to have to reboot if I wish to do some Windows-only stuff.
I was wondering if there is a way to set up a virtualisation system such that I can retain my existing system setup, and simply boot Windows from inside Ubuntu. My knowledge on the subject is **very** limited, and from what I've read, it seems one has to reinstall the guest OS on a virtual partition or something. 
Reinstalling Windows, and all its extras, is almost as painful as having your toenail extracted, and right now I don't really have the time to do so (I'm in the middle of my last year of high school, so yer... big stuff ... EXAMS - argh!!! ... a few months down the track)
Also, since I'm on a Windows server oriented network, would virtualisation even *work*? I mean, the Windows half of this machine is controlled by the server anyway, and unfortunately I'm not an admin, so I cannot really make any big changes to the Windows bit...

Can anyone help me here?

cheers
Robbie

---

### Post by Dedoimedo on 2007-06-06
Hello,

You could install VMware Server or VirtualBox in a Linux distro.
Then, install Windows as a guest operating system in one of these, as a virtual machine.
Then you would have Windows running in Linux.

Or vice versa. Your only limitation is space and RAM. You can install dual and triple-boot virtual machines. You can do practically anything.

Dedoimedo

---

### Post by zoqaeski on 2007-06-07
The problem is, it seems I still need to install guest operating systems, rather than take advantage of a pre-existing setup. That's what I'd like to be able to do...

---

### Post by Dedoimedo on 2007-06-07
Hello,

This is also doable.

VMware Converter
[http://www.vmware.com/products/converter/](http://www.vmware.com/products/converter/)

Dedoimedo

---

