---
title: "Fusion 360 graphic problem"
date: 2018-06-30
forum: Virtualisation
---

### Post by thldq on 2018-06-30
Hi,
I've got a NUC7i5 (Intel) on which I'm running Ubuntu mate 18.04.
I've installed VirtualBox, Windows 10 and Fusion 360.
When I'm using Fusion 360 and I draw in 3D, the solids appearance become weird :
[IMG]https://i.imgur.com/wdWRT8g.png[/IMG]
I checked the "/Help/Graphic Diagnostic/Limit effects to optimize performance" box, with no result.
To be sure it was not due to my computer hardware, I installed Windows 10 then Fusion 360 into a partition on my HDD, checked the "/Help/Graphic Diagnostic/Limit effects to optimize performance" box, and it worked well.

I guess that the problem comes from Ubuntu and maybe from the graphic driver.

I have also ttried to use Simplify 3D in VirtualBox, but when I launch this program a widow pops up saying that Simplify 3D needs OpenGL 2.0 or higher and that my version is only 1.1.

Can you help me please to solve this problem ?
I've erased the Windows 10 partition, and I'd like to be able to use Fusion 360 in VirtualBox (or any other virtualisation program).

Regards
Thierry

---

### Post by thldq on 2018-07-01
Nobody ?
If this can help :
[IMG]https://i.imgur.com/m0L0Tq2l.jpg[/IMG]

---

### Post by deadflowr on 2018-07-01
Typically you need to enable 3d Acceleration in the Virtualbox settings page for the virtual machine in question. (Should be in the Displays section)
And then you double down and install the guest additions inside the virtual machine.

The OpenGL issue is a virtual machine issue (the guest) and not an Ubuntu issue (the host).
Refer:
[https://blogs.oracle.com/scoter/3d-acceleration-for-ubuntu-guests-v2]("https://blogs.oracle.com/scoter/3d-acceleration-for-ubuntu-guests-v2")
[https://help.ubuntu.com/community/VirtualBox/GuestAdditions]("https://help.ubuntu.com/community/VirtualBox/GuestAdditions")

---

### Post by thldq on 2018-07-02
Hi Deadflowr,
hopelessly, it's already done (acceleration and guest addition).
Thierry

---

### Post by deadflowr on 2018-07-02
Oh, reading this makes me sad about it:
[https://forums.virtualbox.org/viewtopic.php?f=2&t=82614#p398391]("https://forums.virtualbox.org/viewtopic.php?f=2&t=82614#p398391")
Seems like a bust at this point.
:(

---

### Post by thldq on 2018-07-02
Let's forget OpenGL.
I would like to be sure that the graphic driver which has been installed by the Ubuntu installer is the best one and - if not - that it can be changed for a better one.
But I don't know how to do.
I've looked into the driver manager and it is not showing any installed  proprietary driver : I thought there might be an Intel driver somewhere.
What I can see in the terminal window above is that something is "unloaded" : fbdev, vesa.
Is it the beginning of a solution ?
Thierry

---

### Post by TheFu on 2018-07-07
In general, virtual machines don't have direct access to the underlying hardware.  That would defeat the purpose of using a VM, most of the time.  There is only 1 GPU driver for vbox VMs - the one provided by the virtualbox.

If you are an expert, and if your system has 2 physical GPUs, and if your BIOS and motherboard support PCI passthru and if 1 of the GPUs is in a "supported list" (which is relatively small), and you enable IOMMU in the BIOS and in the kernel .... if all these things are true, then you'd just need a hypervisor to support GPU passthru.   I know that KVM and Xen support this.  Don't know if any other hypervisors do.  After all that, then you might be able to passthru 1 GPU to the  VM for exclusive use.

Looks like virtualbox can do it: [https://www.virtualbox.org/manual/ch09.html#pcipassthrough](https://www.virtualbox.org/manual/ch09.html#pcipassthrough)

If these seems non-trivial, that is because it is.

---

