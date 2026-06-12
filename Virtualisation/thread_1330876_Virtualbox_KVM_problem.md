---
title: "Virtualbox KVM problem"
date: 2009-11-18
forum: Virtualisation
---

### Post by Gresley on 2009-11-18
I've got a problem with Virtualbox since upgrading to 9.10. The modules kvm-intel and kvm are running and prevent virtualbox from starting a VM. I've added the lines

blacklist kvm_intel
blacklist kvm

to the blacklist.conf file, however after a reboot these modules still load.

every time I start virtualbox I need to preceed this with:

sudo rmmod kvm_intel kvm

Anyone got any ideas how to get rid of this nasty beastie thats making my Koala far from Kalm?

Any idea what might be starting the kvm module? I never had this problem before upgrading to kalmic and latest version of virtualbox?

I dont run any other virtualisation other than virtualbox.

---

### Post by james_xxx on 2009-12-08
Bump.

I am experiencing the same issues. However, in my case, this problem did not start until after I had installed KVM, libvirt, etc., and then later removed them. 

To my knowledge, I removed everything associated with KVM, and yet I cannot use VirtualBox without first running 'sudo rmmod kvm-intel'.

Anyone have an idea how this could be corrected?

---

### Post by james_xxx on 2009-12-10
Bump. [again].

---

### Post by Druke on 2009-12-10
strange, are you sure there isn't a kvm virtualmachine running in the background? I'm able to boot virtual box vms just fine (and have kvm and libvirt stuff installed (and use them from time to time)

also this pc has an old amd64 proc (from when amd 64 just came out)

I'm curious if it's an intel issue.

---

### Post by Druke on 2009-12-10
light googleing reveals this -> [http://sidux.com/PNphpBB2-viewtopic-t-16956.html](http://sidux.com/PNphpBB2-viewtopic-t-16956.html)

---

### Post by james_xxx on 2009-12-10
Thank you for the input.

I ran both 'sudo update-rc.d -f kvm remove' and 'sudo update-rc.d -f kvm-intel remove', and rebooted only to find that I still get this error:

> VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot (VERR_VMX_IN_VMX_ROOT_MODE).

---

### Post by Druke on 2009-12-10
thats no fun...

this is getting into murky waters so I offer help, but know that I'm no professional, and YMMV.

will VBox start up at all now? I have no idea if it will do anything but options to try would include doing a reinstall of the latest kernel (via synaptic would be fine), or maybe seeing if vmx root mode is a bios setting that can be flipped off.

Many people on here say the compiling your won kernel is really easy, so you may want to look into that as well.

---

### Post by Druke on 2009-12-10
also: [https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/292588](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/292588)

---

### Post by james_xxx on 2009-12-10
Thank you for that last link. 

Although I had already run aptitude a few times to make doubly sure I had removed any packages related to KVM, running 'sudo aptitude purge qemu qemu-kvm' did remove qemu-kvm (or maybe just the config files related to qemu-kvm?).

Will 'aptitude purge packagename' still purge config files for packages that had already been removed? 

I am hopeful that my problem will be gone when I reboot next.

Additionally, Yes, I had been able to use VirtualBox, but I had to rmmod kvm-intel each time I booted up in order to do so.

---

### Post by Druke on 2009-12-10
I have never done a purge on a deleted package so I cannot tell you, though if it doesn't you can install it then purge delete it i assume.

---

### Post by pupi1985 on 2010-01-02
Hi! I've been having this issue and, after removing kvm I noticed kvm was still running. When checking with Synaptics the package kvm seemed to be removed. However after checking the "Installed Files" tab noticed there still where some files installed.

I just performed a "Complete removal" of the package kvm and it seems to work fine now.

Hope this helps!

---

