---
title: "Ubuntu 20.004 Best VM Software"
date: 2021-06-26
forum: Virtualisation
---

### Post by jackdusty on 2021-06-26
Hi Guys

Following on from a previous post - I am advised if I must have voice and video call available in the Whatsapp system then the best way to do this is to run a Windows 10 VM,  a bit backward I think but hay Ho such is life.

Can any of you exports please advise the best VM software to run on Ubuntu 20.04.


Thanks






jack

---

### Post by QIII on 2021-06-26
Moved to **Virtualisation**.

For my money -- or lack thereof because it is free -- the best way to go is KVM or Kernel-based Virtual Machine.

---

### Post by ajgreeny on 2021-06-26
> **QIII said:**
> Moved to **Virtualisation**.

For my money -- or lack thereof because it is free -- the best way to go is KVM or Kernel-based Virtual Machine.
I totally agree with QIII about this, particularly if it is for running a VM of Windows 10.

I tried Windows 10 using VirtualBox 6.1 plus the Guest-Additions direct from the Oracle repos but Windows was almost unusable, taking about 6 minutes to boot, maybe partly because I don't understand Windows any more.
However, never having used anything but VirtualBox before, I installed KVM/QEMU with virt-manager etc, and the difference was amazing, Windows 10 running a great deal better with no lagging or difficulties this time.

Try it yourself; I suspect you will like it.

---

### Post by MAFoElffen on 2021-06-26
Hands Down. Fully agree: KVM. 

You can do so much with so little of a footprint. It has very little overhead in the way of resources. It translates and integrates hardware acceleration and virtualization so well. And if you need something that requires more, in the way of hardware compatibility, you can tell it to use more of the host's native CPU capabilities, emulate other CPU's that have a combination or subset of those, etc. Your have choices of BIOS'es, chipsets, etc.

A note on your why, related to Whatsapp and others... Have you checked out "Franz for Linux"?

---

### Post by TheFu on 2021-06-27
I use KVM too. Switched after running Xen, Vmware Workstation, VMware ESX, VMware ESXi, VirtualBox, and a few others.

KVM with libvirt and virt-manager isn't too nerdy anymore, but it isn't end-user friendly either.  I've not used any of those tools in some time, but Gnome-Boxes is based on KVM, but claims to be for end-users.

Video and voice calling can be a challenge for any virtual system.  Some sort of microphone and webcam passthrough will need to be setup.  Getting that working under Linux for a Linux VM isn't hard with virt-manager, but I struggled to get it working a few years ago with Windows inside a VM.  

I hate to say this, but perhaps using virtualbox would be the easiest answer, but only if you can accept the not-so-nice license agreement for the required guest additions.  That license is different from the license to run the main vbox stuff and it is mandatory for USB passthru to work.  Anyway, just wanted to throw that extra consideration out here.

---

### Post by CharlesA on 2021-06-27
Another vote for KVM from me.

I used to use VirtualBox a very long time ago, but I haven't looked back after I switched to KVM.

I wasn't fond about how VirtualBox was free as in beer but the extension pack to enable some advanced features had a different license.

---

### Post by monkeybrain20122 on 2021-06-27
Well Virtualbox has a problem in 20.04, it installs python-is-python2 as a dependency and as a result sets the default python to python2, which is obsolete and the repo only has a small set of packages for legacy software, it certainly makes no sense to make it the default python and it may mess up other apps. I have no real need for VM, but always have some other OSes in VB as toys, because of the python issue I switched to kvm and find it very nice and better than VB (at least for Linux guests, don't have a Windows license to try out Win)

---

### Post by dddman on 2021-06-27
> **monkeybrain20122 said:**
> Well Virtualbox has a problem in 20.04, it installs python-is-python2 as a dependency and as a result sets the default python to python2, which is obsolete and the repo only has a small set of packages for legacy software, it certainly makes no sense to make it the default python and it may mess up other apps. I have no real need for VM, but always have some other OSes in VB as toys, because of the python issue I switched to kvm and find it very nice and better than VB (at least for Linux guests, don't have a Windows license to try out Win)box 

I'm running virtualbox, how can I verify which python is default?  Thanks

[COLOR=#ff0000]Edit[/COLOR]
Found this, but it's for 20.10 and beyond.  A reinstall of virtualbox is required after a upgrade.

[https://bugs.launchpad.net/ubuntu/+source/what-is-python/+bug/1899288](https://bugs.launchpad.net/ubuntu/+source/what-is-python/+bug/1899288)

---

### Post by tea for one on 2021-06-27
> **monkeybrain20122 said:**
> don't have a Windows license to try out Win

Here is some light reading for you 
[https://answers.microsoft.com/en-us/windows/forum/windows_10-windows_install/install-windows-10-without-product-key/f0b59b4f-b818-46f4-a0a6-63c85aca695f](https://answers.microsoft.com/en-us/windows/forum/windows_10-windows_install/install-windows-10-without-product-key/f0b59b4f-b818-46f4-a0a6-63c85aca695f)

---

### Post by monkeybrain20122 on 2021-06-27
> **dddman said:**
> box 

I'm running virtualbox, how can I verify which python is default?  Thanks

[COLOR=#ff0000]Edit[/COLOR]
Found this, but it's for 20.10 and beyond.  A reinstall of virtualbox is required after a upgrade.

[https://bugs.launchpad.net/ubuntu/+source/what-is-python/+bug/1899288](https://bugs.launchpad.net/ubuntu/+source/what-is-python/+bug/1899288)

In the terminal type

```
python --version
```

---

### Post by monkeybrain20122 on 2021-06-27
Thanks tea for one. ;)

---

### Post by dddman on 2021-06-27
> **monkeybrain20122 said:**
> In the terminal type

```
python --version
```
Thanks!
Python3
But this is a Windows host and Ubuntu guest.  KVM is for Linux and not available for Windows so I'm running Virtualbox.  Doesn't sound as high tech as KVM, but it works just fine with Windows.

---

### Post by monkeybrain20122 on 2021-06-27
> **dddman said:**
> Thanks!
Python3
But this is a Windows host and Ubuntu guest.  KVM is for Linux and not available for Windows so I'm running Virtualbox.  Doesn't sound as high tech as KVM, but it works just fine with Windows.

OK, I was talking about installing VB in Ubuntu host. In the VM of course the default is python3 since you didn't install VB in the guest.

---

### Post by TheFu on 2021-06-27
VirtualBox was created for desktop-on-desktop virtualization needs by a company before Oracle, before Sun Microsystems, before VT-x/AMD-v CPU extensions existed.  In many ways, it is still an excellent technology for what it does.

KVM started out as a simple, Linux kernel, hypervisor for servers. No GUIs. It provided extreme stability. No crashing since the beginning, while supporting nearly all the hardware that Linux supports, with 1 requirement.  VT-x or AMD-v CPU extensions are mandatory for KVM to be used.  KVM took what QEMU, a software CPU emulator did, and took advantage of crazy-fast context switching that hardware supports.  Over time, it has grown from server farms down to desktops.  Before around 2015, KVM on a desktop wasn't exactly great.  Desktop VM support has gotten better and better and better every 6 months.  Between 16.04 and 18.04, KVM desktop support really became excellent thanks to SPICE which is a nearly hardware speed GPU protocol that works both locally desktop on desktop and over a network like a remote desktop.  The OpenGL performance for remote desktops is impressive with Spice compared to other remote desktop options.  It isn't perfect for all uses, for example, low bandwidth connections.

KVM is used by almost everyone who doesn't sell their own hypervisor.  When people rent a VPS, it is almost always a KVM virtual machine they get.

KVM has been tied to AMD64 CPUs for some time.  The last few years, efforts to make it work on ARM64 has come along. I've never used nor seen it running on ARM, but there is some hope.  I suspect Apple's M1 CPU will be an early winner, though ARM "servers" exist.

---

### Post by MAFoElffen on 2021-06-29
> **TheFu said:**
> KVM has been tied to AMD64 CPUs for some time.  The last few years, efforts to make it work on ARM64 has come along. I've never used nor seen it running on ARM, but there is some hope.  I suspect Apple's M1 CPU will be an early winner, though ARM "servers" exist.
KVM on ARM Servers is well supported since around 2014-2015... Well, announced in 2014. I didn't find it really stable until 2016.

What isn't well supported yet is doing AARM64 guests on x86_amd64's. The code has some bug's still. That KVM/QEMU emulation  drives me crazy trying to get them built and working without error's or me wanting to... Well? LOL Yes.

---

