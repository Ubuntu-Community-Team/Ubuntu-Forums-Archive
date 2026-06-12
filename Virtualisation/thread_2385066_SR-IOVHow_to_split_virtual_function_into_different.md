---
title: "SR-IOV:How to split virtual function into different iommu group?"
date: 2018-02-15
forum: Virtualisation
---

### Post by happyljj on 2018-02-15
My platform is
Ubuntu 16.04 lts desktop version;
Cpu is Intel(R) Xeon(R) CPU E5-2620 v4 @ 2.10GHz;
One Intel Corporation 82576 Gigabit Network adapter;
 
I followed the tutorial from intel and redhat
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_host_configuration_and_guest_installation_guide/sect-virtualization_host_configuration_and_guest_installation_guide-sr_iov-how_sr_iov_libvirt_works](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/virtualization_host_configuration_and_guest_installation_guide/sect-virtualization_host_configuration_and_guest_installation_guide-sr_iov-how_sr_iov_libvirt_works)
[https://www.intel.com/content/dam/www/public/us/en/documents/technology-briefs/xl710-sr-iov-config-guide-gbe-linux-brief.pdf](https://www.intel.com/content/dam/www/public/us/en/documents/technology-briefs/xl710-sr-iov-config-guide-gbe-linux-brief.pdf)
 
I can successfully create virtual functions like below, however, they are all in the same iommu group, which I cannot attach any of them to vm:
 
### Group 29 ###
02:04.0 PCI bridge: Integrated Device Technology, Inc. [IDT] PES12N3A PCI Express Switch (rev 0e)
05:00.0 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
05:00.1 Ethernet controller: Intel Corporation 82576 Gigabit Network Connection (rev 01)
06:10.1 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
06:10.3 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
06:10.5 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
06:10.7 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
06:11.1 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
06:11.3 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
06:11.5 Ethernet controller: Intel Corporation 82576 Virtual Function (rev 01)
 
If I attach vf to vm, then I will get this error:
“Group 29 is not viable, please ensure all devices within the iommu_group are bound to their vfio bus driver”
 
I have tried the following approach, but none of them is working for me:
1. Adding pcie_acs_override: “GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_iommu=on pcie_acs_override=downstream,multifunction”
2. Used4.7 kernel from this post [https://ubuntuforums.org/showthread.php?t=2329053&page=2](https://ubuntuforums.org/showthread.php?t=2329053&page=2)
 
 
Does anyone know how to solve this problem?
 
Thank you

---

