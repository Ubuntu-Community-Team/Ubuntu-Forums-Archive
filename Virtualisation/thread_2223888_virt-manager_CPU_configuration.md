---
title: "virt-manager CPU configuration"
date: 2014-05-13
forum: Virtualisation
---

### Post by redrumrogue on 2014-05-13
Hello folks,

I have recently installed a Windows 7 Professional 64bit guest on my Ubuntu 14.04 64bit KVM/QEMU host.  My host CPU is an AMD 8350 FX 8-core black edition.  When I go to the Processor settings for the VM I see that in the Configuration section there is a button called "Copy host CPU configuration" and when I press that the Model gets set to "Opteron_G5".  I've read online that you can start a VM up via command line with argument "-cpu host" which is supposed to expose the actual host CPU to the VM (correct me if i'm wrong).  Will pressing the "Copy host CPU configuration" button give me the same result?  Will my VM make full use of all CPU features using this button and having the model set to "Opteron_G5"?

Thanks,
JB

---

### Post by TheFu on 2014-05-15
I didn't look this up today, but have previously, a few yrs ago. The intent of that button, as I understand it, is to force a specific CPU model so that live-migrations of VMs to other physical servers goes smoothly.  Also, it helps for cluster configurations. By default, the hostOS CPU capabilities ARE used on recent libvirts.  If you aren't migrating or clustering, don't touch it.  

[http://libvirt.org/formatdomain.html#elementsCPU](http://libvirt.org/formatdomain.html#elementsCPU)

I don't know much about AMD the last 5 yrs - so I'll put it in Intel terms.  I have Core 2Duo, Core i5 and Core i7 KVM servers here. I force all the VMs to be Core2Duo so that live migrations can end up on any server without issue.  That means that migrations from the i7 to the C2D work. Otherwise ...er ... it would be bad, assuming the migration were even allowed.

To understand any of these settings, the best place to look is the libvirt documentation.  Found this bug: [http://wiki.libvirt.org/page/Libvirt_identifies_host_processor_as_a_different_model_from_the_hardware_documentation#Solution](http://wiki.libvirt.org/page/Libvirt_identifies_host_processor_as_a_different_model_from_the_hardware_documentation#Solution) which could be something you're seeing.

---

