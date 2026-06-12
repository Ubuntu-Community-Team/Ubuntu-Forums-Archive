---
title: "ubuntu dom0 vmx problem"
date: 2010-04-21
forum: Virtualisation
---

### Post by chenchao on 2010-04-21
hi, guys
 
I am using a dual boot configuration, one with Ubuntu 9.10 and the other with Xen 3.4.2 with Ubuntu 9.10 as **Dom0**.
I have enabled the **VMX** **support** in the BIOS.
Native Linux shows the presence of the **VMX** flag in /proc/cpuinfo
Xen **Dom0** doesn't have the flag set in /proc/cpuinfo
but, xm dmesg shows that **VMX** is enabled in the BIOS. 


How can I resolve this? I want to install a fully virtualized guest OS on Intel Q8400 CPU with **VMX** **support**. 

I have another question. How to change dom0 cpus? 
 
Please help me.
 
Thanks

---

### Post by meatpan on 2010-04-21
If 'xm dmesg' mentions that VMX is enabled, you should be ok.  

For example, on my system, running 'xm dmesg | grep VMX' returns:
(XEN) VMX: Supported advanced features:
(XEN) VMX: EPT is available.
(XEN) VMX: VPID is available
(XEN) HVM: VMX is enabled.

However, /proc/cpuinfo does not show a vmx flag.

Also, another useful way to check for VMX support is the 'xm info' command.  Run this command, and look for 'hvm' somewhere in the xen_caps and virt_caps values.

I'm not sure why /proc/cpuinfo no longer contains the vmx flag.  This threw me off a bit at first, too.  It hasn't been a problem though, as I'm using nearly all VMX features (including VT-d and HAP) on a set of processors that do not explicitly state 'vmx'.

A quick suggestion:  If you can, boot a xen livecd and try to initialize one of the prepackaged HVM's.  This will quickly show you the limit of your VMX capabilities.

---

### Post by chenchao on 2010-04-22
Thank you for your help.
 
I run 'xm info' and find 'hvm' in virt_caps.
 
But, I still can't use virt-manager to install a fully virtualized guest OS. I cannot choose 'Local install media (ISO image or CDROM)'. It shows 'CDROM/ISO installs not available for paravirt guests.'
 
I try xenlivecd. Everything is good. I can install an HVM guest OS.
 
Do you have any good idea?
Please help me. Thank you very much

---

### Post by meatpan on 2010-04-22
How are you certain that you are creating an HVM?  Was there a step in the setup process where you selected "Full Virtualization"?  

I can't help you much here because I don't use the virt-manager tool.  It sounds like your machine is capable of VT, but your toolset is mis-configured or mis-operated.

---

