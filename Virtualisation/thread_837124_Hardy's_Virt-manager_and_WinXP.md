---
title: "Hardy's Virt-manager and WinXP"
date: 2008-06-22
forum: Virtualisation
---

### Post by lithium on 2008-06-22
For a few days I'm trying to install WinXP using Virt-Manager on Hardy (using KVM). It installs just fine but on reboot (or if I try to boot the VM after that) it just goes to the bios and complains about a bad harddisk.

Note: I installed WinXP on KVM manually on the same system, which worked flawlessly.

I wonder, does anyone have installed XP (this is from my SP2 CD) flawlessly with Virt-Manager or is this a common problem?

Any comments and suggestions welcome!

---

### Post by igwk on 2008-06-22
I run kvm directly rather than using virt-manager.  What advantages do you gain by using the virt-manager software over running kvm directly?

---

### Post by lithium on 2008-06-23
A nice GUI.

---

### Post by lithium on 2008-06-27
...also, advanced VM management, starting & controlling VMs using libvirtd.

Someone must have experience with this on Hardy?

---

### Post by msisamonopoly on 2008-06-28
If it's complaining about a harddisk problem, presumably you will get the same error whether you run it directly from the command line, or via Virt-Manager?

If this is so, then the problem is not related to Virt-Manager but a problem with the Windows XP installation.

Suggest trying with the install procedure here>
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

Section >> Create VMs running other operating systems: virt-install

---

### Post by lithium on 2008-06-30
> **msisamonopoly said:**
> If it's complaining about a harddisk problem, presumably you will get the same error whether you run it directly from the command line, or via Virt-Manager?

Thanks for your reply. I tried installing with virt-install using the command line supplied in the Wiki (with my cd device instead of the iso which should work but I only get "Unsupported virtualization type".

I then startet virt-manager again and let it install XP again, which worked fine (as always), showing the corrupted HD message at the first boot. I then tried to boot the image manually using kvm, same error.

But - as stated on the initial post - I can install winxp using kust kvm (no virt-manager / libvirt / virtinstall) just fine. So this *has to be* a problem in those apps.

---

### Post by caspartroy on 2008-07-14
> **lithium said:**
> 
But - as stated on the initial post - I can install winxp using kust kvm (no virt-manager / libvirt / virtinstall) just fine. So this *has to be* a problem in those apps.
I've got the same problem with debian guests, kvm works fine without virt-manager, virt-install just prints out "Unsupported virtualization type". I have copied an example from the man page with the same result!

---

