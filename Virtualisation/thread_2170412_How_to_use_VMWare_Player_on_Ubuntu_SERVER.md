---
title: "How to use VMWare Player on Ubuntu SERVER"
date: 2013-08-26
forum: Virtualisation
---

### Post by Michel_Cot on 2013-08-26
Hello,

I've install VMWare Player on my 12.04 Ubuntu Server (not Ubuntu Desktop).

I want tou use VMWare Player to run others "small" Ubuntu SERVER Virtual Machines (i mean with little ram and disk configurations).

I've read carrefully (i think...) the vmware player documentation and i think i understand that vmware player is a product that needs a "graphical environment" to run. Does anyone knows if it possible to use it as a server player that runs in background with no graphical interface and that can be monitor only when necessary. 

I believe, "VMWare Server" used to work as described above but it is no longer supported !

Thank in advance for any help. I hope you succed to understand me because my english is not really "academic"....

Regards,

Michel Coté.

---

### Post by TheFu on 2013-08-26
VMware Player is not intended for "servers."  The VMware guys want to sell you either ESX or ESXi for that purpose.
There is good news.  Better alternatives exist ... for free. 

For servers, use KVM with libvirt and virt-manager. These all work together 
* install virt-manager on your desktop.
* setup ssh connections to your "VM host" from the desktop. This will provide the "GUI" interface to create and manage VMs.
* On the VM host, install kvm and virsh. 
That's it.

Now go back to the desktop and make a connection to the VM host using virt-manager over ssh.  Basically, you have the same thing as VMware Player, for free, and it is tuned for running servers.  You can run desktops inside this VM, but honestly, the graphics performance just isn't ready for that.

You can also run virtualbox in a headless mode, but I've found that tool to be
a) from oracle - yuck.
b) not as stable as KVM
c) not as flexible as KVM
d) doesn't support as efficient virtual hardware as KVM - virtio should be used as much as possible.

Also, with a KVM host, you can load up LXC VM-containers when you don't need any fancy networking (think firewalls) and really just need logical separation of the different processes. It has much less overhead compared to vbox, kvm, or anything from vmware. virt-manager will see the LXC capabilities and the GUI will add that as an option.

Xen is also an option, but I cannot recommend it any more.
If you can dedicate a full machine to be a VM host, there are "packaged setups" that try to make this stuff easier. Sometimes the packaged setups are harder, IMHO. A few years ago, they were necessary - it WAS hard - but these days, a straight KVM/LXC + virt-manager setup is pretty simple to get working, tuned, stable.
[http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-12.10](http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-12.10) might be useful - however, if you want stability and more than 9 months of support, definitely use 12.04.

---

### Post by Michel_Cot on 2013-08-27
Thank you for your answer and its precision.

I will investigate in "KVM with libvirt and virt-manager" as it seems to match exactly my need.

---

### Post by Simon_WM on 2013-08-29
You could also look at as suggested VMware ESXi and XenServer or Hyper-V 2012

---

