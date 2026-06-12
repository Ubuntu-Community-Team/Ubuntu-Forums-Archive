---
title: "Virtualization - Available From Command Line?"
date: 2009-07-04
forum: Virtualisation
---

### Post by justinmiller87 on 2009-07-04
Hello,

So what I want to do is set up a minimal CLI system and then install one of the virtual machines on top of it in order to be able to run multiple OSs with minimal resources running in the background. Is this possible and if so, which of the big VMs is best for it?

---

### Post by kaivalagi on 2009-07-04
> **justinmiller87 said:**
> Hello,

So what I want to do is set up a minimal CLI system and then install one of the virtual machines on top of it in order to be able to run multiple OSs with minimal resources running in the background. Is this possible and if so, which of the big VMs is best for it?

KVM would be the first that comes to mind for CLI only usage, you can start off here: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

I am not sure whether the likes of VMWare or VirtualBox can be setup purely on the CLI...

---

### Post by x33a on 2009-07-04
virtualbox supports the commandline, take a look here:

[http://www.ubuntugeek.com/how-to-control-virtual-machines-virtualbox-using-vboxmanage.html](http://www.ubuntugeek.com/how-to-control-virtual-machines-virtualbox-using-vboxmanage.html)

---

### Post by walter554 on 2009-07-04
Don't know if this will help:
[http://ubuntuforums.org/showthread.php?t=1204202](http://ubuntuforums.org/showthread.php?t=1204202)

---

### Post by HermanAB on 2009-07-04
VMware vmrun command can do pretty much anything.  I don't have GUIs on my servers and they all run VMware.

---

### Post by Seq on 2009-07-04
I'm running kvm+libvirt on a headless box. It works pretty well. It will share the console out using vnc if it is needed. I use virt-manager to manage remotely from my regular desktop, and virsh for some more advanced functions right on the server.

Also look into vmbuilder if you're wanting to create a bunch of Ubuntu VMs, it allows you to essentially define templates and will rebuild VMs from scratch in minutes.

---

### Post by patryk77 on 2009-07-05
[https://help.ubuntu.com/9.04/serverguide/C/virtualization.html](https://help.ubuntu.com/9.04/serverguide/C/virtualization.html)

Read the sections on libvirt and JeOS ;)

Now, if only I can get networking working on my VPS I will be happy :lolflag:

---

