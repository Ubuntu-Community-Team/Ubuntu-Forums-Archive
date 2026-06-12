---
title: "Installing Ubuntu 12.04 as HVM guest on Citrix XenServer 6.1"
date: 2013-11-26
forum: Virtualisation
---

### Post by jpthompson23 on 2013-11-26
Hi, I have a problem with the way Ubuntu 12.04 is virtualized on Citrix XenServer 6.1.  I'm not entirely sure about this, but I believe the system uses paravirtualization.  I want to use the GPU passthrough feature, so I believe I need to be in hardware virtualization mode, because if I try to start up the VM as it is currently configured, with the vgpu assigned to it, I get the error message "The VM is set up to use a feature that requires it to boot as HVM."  So how do I install Ubuntu 12.04 so that it boots as HVM?  Thanks.

---

### Post by KillerKelvUK on 2013-11-30
I briefly played around with Xen (non-Citrix ver) before switching to KVM so please treat this response with the caution it deserves...

Have you confirmed that all your hardware components are capable of supporting directed IO?  CPU/mobo/Gfx card...just because you can visualise an OS doesn't mean you must be capable of doing this.

Have a read thru here...[http://wiki.xen.org/wiki/Xen_VGA_Passthrough](http://wiki.xen.org/wiki/Xen_VGA_Passthrough)

Lastly I believe the PV / HVM specification is when you provision the guest using whatever tooling you are...not when you are installing the guest.  If my memory serves me the process for making Ubuntu run as a HVM domU is similar to the guest creation steps you'd take for installing Windows as a domU...see this [http://wiki.xenproject.org/wiki/Xen_Beginners_Guide#Creating_a_Windows_HVM_.28Hardware_Virtualized.29_Guest](http://wiki.xenproject.org/wiki/Xen_Beginners_Guide#Creating_a_Windows_HVM_.28Hardware_Virtualized.29_Guest).

---

### Post by jpthompson23 on 2013-12-24
Yes, I figured out how to provision the VM as HVM and install Ubuntu on it.

---

