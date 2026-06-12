---
title: "Alternative for .VMX machines"
date: 2010-03-16
forum: Virtualisation
---

### Post by toineurlings on 2010-03-16
Hi, I'm struggeling with VMware (it captures my shift and ctrl and closes itself after starting it up)... Is there an other program which can open a vmx virtual machine? Or does anyone know how to solve my problems?

I want to play windows xp, my host is ubuntu (normal/newest version)

---

### Post by fjgaude on 2010-03-16
VMware Player 3.0.1 seems to work well with the latest versions of Ubuntu and the VMs created by Server or earlier Player.

---

### Post by toineurlings on 2010-03-18
I'm working with this version... I think I first worked with an older version when the problem showed up... 

I can try again by maken a new machine... but when this works, is there a way to recover my documents and get them out of the old machine becaus it won't start up...

---

### Post by fjgaude on 2010-03-18
You have to be able to load, run the VM (Windows XP) under Player to get to your old files. Can you do that?

---

### Post by Seq on 2010-03-18
Virtualbox can read your vmware disk files (*.vmdk), though it can't load the VM definition (*.vmx files).

You could import the vmware disks, create a new VM with the same settings, and give it a shot. Backup first. Hardware in the VM will change, so if you're running Windows it will need to be reactivated.

[http://blogs.sun.com/VirtualGuru/entry/vmware_vms_amp_virtualbox]("http://blogs.sun.com/VirtualGuru/entry/vmware_vms_amp_virtualbox")

---

### Post by toineurlings on 2010-03-19
> **Seq said:**
> Virtualbox can read your vmware disk files (*.vmdk), though it can't load the VM definition (*.vmx files).

You could import the vmware disks, create a new VM with the same settings, and give it a shot. Backup first. Hardware in the VM will change, so if you're running Windows it will need to be reactivated.

[http://blogs.sun.com/VirtualGuru/entry/vmware_vms_amp_virtualbox]("http://blogs.sun.com/VirtualGuru/entry/vmware_vms_amp_virtualbox")

I don't understand the whole thing youre saying... I made a new user in ubuntu and installed in their VM again but the same problem showed up...

Is this a way to open a VM machine in Virtualbox?

Is it right this link shows how to format the virtual disk? I want to keep my documents...

---

### Post by Seq on 2010-03-22
> **toineurlings said:**
> I don't understand the whole thing youre saying... I made a new user in ubuntu and installed in their VM again but the same problem showed up...

Is this a way to open a VM machine in Virtualbox?

Is it right this link shows how to format the virtual disk? I want to keep my documents...

That link was talking about the virtual disks actual file structure (format), and didn't say anything about erasing your disk. I gave that link as proof that you can use vmware disk images (vmdk) in virtualbox.

Here is another article on [how to use vmware images in virtualbox]("http://blogs.sun.com/thaniwa/entry/en_how_to_use_vmware"). You could also do a [search]("http://lmgtfy.com/?q=use+vmware+in+virtualbox"). If you're moving a windows machine, you may [need to work around problems with windows]("http://www.virtualbox.org/wiki/Migrate_Windows") in addition to it invalidating it's license verification.

Note that VMWare capturing your shift and ctrl keys when it has focus is by design. Virtualbox will do this too. Closing itself is definitely odd though. Have you tried to resolve that issue rather than attempting to port hypervisors? It may be worthwhile.

I've done this in the past at a previous job, but nowdays I'm quite happy with KVM and don't use either vmware or virtualbox. I'm afraid I can't be of much more use. Perhaps the [Virtualbox Community]("http://www.virtualbox.org/wiki/Community") could be of more help.

---

