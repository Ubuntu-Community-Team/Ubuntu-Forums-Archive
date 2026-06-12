---
title: "VMWare Workstation VM on VMWare Server"
date: 2008-05-06
forum: Virtualisation
---

### Post by aroddo on 2008-05-06
I created some VMs using the vmware Workstation under Windows.
When trying to load it with vmware Server under Ubuntu, I get this:

> Unable to add virtual machine "/usr/lib/vmware/Virtual Machines/machine_name/machine_name.vmx" to the inventory.

Configuration file was created by a VMWare product with more features than this version. Can I *downgrade* it somehow ?

---

### Post by fjgaude on 2008-05-06
You can comment-out features that Workstation or Player have that Server doesn't in the .vmx file. I'm not sure which but you look over the .vmx file in an editor you might see something that should be commented out.

---

### Post by aroddo on 2008-05-06
hmm.... have to try that. 
i have to admit that i chickened out and set up a new vm, though :)

---

### Post by fjgaude on 2008-05-06
Okay, here's a copy of my .vmx file that you can compare to your Workstation one. Would be interesting to know the differences, would help others.

---

### Post by fjgaude on 2008-05-20
WRT: [http://ubuntuforums.org/showthread.php?p=4893315](http://ubuntuforums.org/showthread.php?p=4893315)

I checked, and the answer is a simple change to 1 line.

	virtualHW.version = "4"

You also have to change the same entry in all .vmdk files:

	ddb.virtualHWVersion = "4"

Set the above and a vmware workstation (version 6) vm will open in
Vmware Server 1.0.5

(Thanks to the good fellow who passed this along to me.)

---

