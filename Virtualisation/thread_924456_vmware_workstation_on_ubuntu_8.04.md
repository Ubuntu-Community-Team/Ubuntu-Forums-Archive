---
title: "vmware workstation on ubuntu 8.04"
date: 2008-09-19
forum: Virtualisation
---

### Post by redgsturbo on 2008-09-19
It installs fine... when I try to start any VM it says:

VMware Workstation unrecoverable error: (vcpu-0)
VCPU 0 RunVM failed: Operation not permitted.
A log file is available in "/home/hunter/vmware/Windows XP Professional/vmware.log".  Please request support and include the contents of the log file.  
To collect data to submit to VMware support, select Help > About and click "Collect Support Data". You can also run the "vm-support" script in the Workstation folder directly.
We will respond on the basis of your support entitlement


Log is attached

---

### Post by trmentry on 2008-09-20
do you have other virtualization programs on the computer?


I found this googling around.

> 
What I found was that /var/log/messages reported that VMware couldn't
get a lock on VT because it was already in use by something else...

Solution: Uninstall all other things virtualization on the box. I still
had some KVM/QEMU components lying around.

That said, it doesn't make sense to me because I have a full KVM/QEMU
installation running on my laptop with the same F9 setup. Workstation
works there with no issues. 

another thing I found was this.

> 
This was the hint I needed: I had to disable the virtualization in the kernel itself, meaning either unloading kvm_foo or disabling it altogether in the make menuconfig. 


found this nice post.
[http://www.nowhere.dk/archives/2008/07/23/vmware_workstation_6_0_4_on_ubuntu_intrepid_ibex_kernel_2_6_26/index.php?show_id=e2008-07-23T15_08_35.txt](http://www.nowhere.dk/archives/2008/07/23/vmware_workstation_6_0_4_on_ubuntu_intrepid_ibex_kernel_2_6_26/index.php?show_id=e2008-07-23T15_08_35.txt)

not sure if any of this will help.. but hope so.

---

