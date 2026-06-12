---
title: "Virtualmachine can't connect to a network."
date: 2009-04-10
forum: Virtualisation
---

### Post by tsav87 on 2009-04-10
I am running Ubuntu 9.04 and VirtualBox OSE from the repository.

I have a wireless network PCI card running great, but I can't get it to work for the virtual machine.

Any ideas?

---

### Post by Perryg on 2009-04-10
> **tsav87 said:**
> I am running Ubuntu 9.04 and VirtualBox OSE from the repository.

I have a wireless network PCI card running great, but I can't get it to work for the virtual machine.

Any ideas?

VBox will use what ever you host is using to connect.  Select the Hosted Interface in VBox will get you where you need to be.  Also you can try to select a different Virtual adapter if you find that it will not work on the default.  Chapter 6 of the VBox manual tells you all about it.

---

### Post by tsav87 on 2009-04-11
I am using lo for my network, but lo isn't an option on the Host Interface.

???

---

### Post by tsav87 on 2009-04-11
Screen Shots attached...

---

### Post by Perryg on 2009-04-11
> **tsav87 said:**
> Screen Shots attached...

Put a tick in the cable connected box on your second screen shot.  Should work for you after that.

---

