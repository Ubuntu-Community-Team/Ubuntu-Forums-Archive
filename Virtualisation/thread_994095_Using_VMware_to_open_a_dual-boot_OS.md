---
title: "Using VMware to open a dual-boot OS"
date: 2008-11-26
forum: Virtualisation
---

### Post by PJFinega on 2008-11-26
A friend of mine that helped me set up my laptop to dual-boot Ubuntu and Vista (64-bit) also showed me a program called VMware that allowed him to open the other OS on his machine in another window.  

I'm 75% sure he used VMware Player, but after looking around online, I can't find any help on how to achieve that.

He told me that Vista doesn't like to be virtualized, but really all I want right now is to be able to open Ubuntu in Vista.

Can anyone help me?

---

### Post by Titan8990 on 2008-11-26
The easiest would be to just use the Microsoft Virtual PC. Not the best VM program but it is easy and it works.


Would recommend VirtualBox for ease of use in Ubuntu.

---

### Post by Tom--d on 2008-11-26
VirtualBox is free and open source and works on Windows and Linux and Mac. I would recommend this over VMware for home use.

[www.virtualbox.org](www.virtualbox.org)

And then install the Guest Additions. VERY helpful and adds special additions to the VM. For example, when resize the window, it resizes the resolution of the desktop to that size of the window.

---

### Post by bodhi.zazen on 2008-11-26
You can use VirtualBox or VMWare Server, both are freely available.

I have no experience with the Microsoft product, but somehow it just seems wrong. I suppose Microsoft is filing patent infringements against VMWare , VirtualBox, QEMU, KVM, Xen, etc as we speak.

---

### Post by PJFinega on 2008-11-26
Maybe I need to make myself more clear. 
First thank you for the program suggestions.

But I'm still at a loss for how to do it. Do you have a link to step-by-step instructions?

---

### Post by bodhi.zazen on 2008-11-26
Install VMWare or Virtualbox.

Then make a virtual machine. When selecting the hard drive, select your actual physical hard drive. Take care not to boot windows within the VM or you will likely have problems.

You can look at the mega thread for some links, but the how-to's on these forums will use an Ubuntu host.

If you want a how to for windows, try google, I am sure there are many many how to's on the web.

If you use virtualbox, the best information is in the user guide from their web site which is available as a PDF.

---

### Post by PJFinega on 2008-11-26
Thank you!

---

