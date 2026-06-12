---
title: "Is kvm sound possible in both Ubuntu 9.04 host and winXP guest?"
date: 2009-05-19
forum: Virtualisation
---

### Post by Tomy on 2009-05-19
IANAP just an end user.

I set up my winXP guest using virt manager but run it using virsh with this simple scipt.

```
virsh start winXP3
virt-viewer --connect qemu:///system 6bd3bad9-f21e-c387-3bbd-c0e8267e7472 
virsh shutdown winXP3
```I have sound in winXP but my Ubunutu sound doesn't work until I shutdown the winXP guest. Is it possible to shutdown the sound in my winXP guest without shutting down kvm?

The manual page for virsh shows device commands (attach-device and detach-device) that sound (pun intended) like what I'm looking for. or maybe not.

update: I found this info but don't know how to use it.

[http://libvirt.org/formatdomain.html#elementsSound](http://libvirt.org/formatdomain.html#elementsSound)
> Sound devices         

                A virtual sound card can be attached to the host via the       sound element. Since 0.4.3     
               ...
      <sound model='es1370'/>
      ...

---

### Post by Techie03 on 2009-05-20
I am having this same issue too.  Except, when I shut down my Win XP guest, I do not get sound back through Ubuntu until I reboot.

---

### Post by Tomy on 2009-05-20
> **Techie03 said:**
> I am having this same issue too.  Except, when I shut down my Win XP guest, I do not get sound back through Ubuntu until I reboot.

I had to reboot to get sound back before I started using "virsh shutdown winXP3". I was turning off winXP and then closing the kvm window but this didn't really shut down the virtual machine.

If I use the Virtual Machine Manager gui I don't get sound back when I "turn off" winXP -- I only get it back when I click on Virtual Machine->Shutdown->Shutdown or right-click on the "running" status and and then click on Shutdown->Shutdown.

---

