---
title: "Cut &amp; Paste between OS's"
date: 2011-06-16
forum: Virtualisation
---

### Post by brycenesbitt on 2011-06-16
I've set up "Virtual Machine Manager" with a Windows XP guest under QEMU.  I'm finding it awkward to use because I can't cut & paste between Ubuntu and Windows XP.

I'm seeking advice on which combinations of manager,  virtualization, window manager, host and/or guest should support cut & paste.  I've checked the usual FAQ's (e.g. [http://virt-manager.org/faq.html](http://virt-manager.org/faq.html) ) and they are all curiously silent on the topic.

---

### Post by JKyleOKC on 2011-06-16
I use VirtualBox rather than QEMU; vbox provides for "virtual folders" which are similar to mounting external drives. I create a virtual folder in each VM, that's actually my home directory in the host. I can then open the VM's virtual folder and transfer data in and out of it with no problem.

Vbox also provides "bidirectional" clipboard action but I've never been able to make it work as expected. This may be because there are several different kinds of clipboards in a Linux system, and I'm looking in the wrong area, but I've found it far easier to simply create a dummy text file in my home directory, then do my cutting/pasting through that dummy file to make the jump between systems.

---

### Post by Gibsonbc on 2011-06-18
> **brycenesbitt said:**
> I've set up "Virtual Machine Manager" with a Windows XP guest under QEMU.  I'm finding it awkward to use because I can't cut & paste between Ubuntu and Windows XP.

I'm seeking advice on which combinations of manager,  virtualization, window manager, host and/or guest should support cut & paste.  I've checked the usual FAQ's (e.g. [http://virt-manager.org/faq.html](http://virt-manager.org/faq.html) ) and they are all curiously silent on the topic.



I'm using Ubuntu 10.10 and I'm running XP as my guest in Virtualbox 4.0.8.  With the extensions pack and guest additions installed, I have no trouble using the cut and paste function.  I've tested it in Word documents and internet Explorer, going back and forth from each.  It worked fine with the previous version of Virtualbox too.  I also have no problems sharing folders or USB.

I have no experience with QEMU, so I can't help you if you stick with that.  If nothing else you could go to virtualbox's webpage and download the latest version.

---

