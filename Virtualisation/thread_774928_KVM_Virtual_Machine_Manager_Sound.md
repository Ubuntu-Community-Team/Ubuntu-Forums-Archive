---
title: "KVM Virtual Machine Manager Sound"
date: 2008-04-29
forum: Virtualisation
---

### Post by rernst99 on 2008-04-29
I successfully managed to install a multiprocessor XP under Hardy on a dual core box. The performance is amazing, far exceeding Virtualbox.

I have a small problem in regards to emulation of sound hardware: I can start the machine from the command line via 'kvm -soundhw all xxxx' and get a soundblaster emulation. However, there seems to be no option in the virtual machine manager or the XML file for that matter to specify any audio hardware. This makes it a bit tedious.

Am I overlooking something? Is there some sort of backdoor for specifying additional tags in the XML definition?

---

### Post by Tomy on 2009-05-19
In the Virtual Machine Manager with the virtual machine shutoff I can click on Edit->VirtualMachineDetails and then select the  Hardware tab and at the bottom of the window is a button for Add Hardware. The drop-down menu has a choice for sound.

I am using Virtual Machine Manager 0.6.1

---

