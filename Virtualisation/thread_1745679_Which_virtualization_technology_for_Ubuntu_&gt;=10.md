---
title: "Which virtualization technology for Ubuntu &gt;=10.04"
date: 2011-05-01
forum: Virtualisation
---

### Post by aruzsi on 2011-05-01
Hi,

I'm looking for the most convenient virt. platform for me which can be administered and used remotely.

I have a two node PC (AMD Phenom II X4 840 + 8GB RAM) as host machine and I want to use them over network.

I tried out VBox 4.0.4, VMware Server 2/WS 7/VMplayer 3.x, QEmu and now I want to install Xen.

I usually use VBox+VMware. I've no experience with Xen. I've got some OS/2 VM-s under QEmu.

VBox+phpVirtualBox is almost perfect for me expect RDP+Host keys problem and the doubled mouse cursors if GA installation is not possible (for example installing Ubuntu or any other Linux with GUI; any Live Linux version like TinyCore or Puppy)

VMware Server 2.0.2 is not working under my recent openSuSE 11.3. The problem is the kernel like in the newest Ubuntu 11.04.

KVM (or QEmu?) not supported on my test machines because no VT-x support in my CPUs (intel Xeon 3GHz which was built in 2004-5).

Xen. I've never used it. I've tried out with a LiveCD. That's all.

Some words about guest VMs.
Usually Linux. SuSE 7.3; 9.3; SLES11, Ubuntu >=8.10, RHEL 4;5. There are some Win XP or 7. OS is not a problem. Problem is the desktop. I mentioned above the the problem with VBox's RDP host keys + mouse coursors.
2nd problem is more than two screens under X. No, multi-monitor monitor wasn't successful for me. I don't want 2x1024x768 resolution. I want two 1024x768 like a real dual head VGA system.

Any ideas?

TIA,

---

### Post by falko on 2011-05-03
> **aruzsi said:**
> 
Xen. I've never used it. I've tried out with a LiveCD. That's all.
Ubuntu doesn't include or support a dom0 capable kernel from Intrepid Ibex onward.
[https://help.ubuntu.com/community/Xen#Ubuntu%27s](https://help.ubuntu.com/community/Xen#Ubuntu%27s)

---

### Post by aruzsi on 2011-05-03
Thanks.
I don't have too many possibilities then.
KVM+Xen unusable. On 11.04 VMware Server + (Player: kernel source problem.

VBox... Hmmm.
It is working, but ...

TIA,

---

### Post by majorpay on 2011-05-03
> **aruzsi said:**
> Thanks.
I don't have too many possibilities then.
KVM+Xen unusable. On 11.04 VMware Server + (Player: kernel source problem.
 
VBox... Hmmm.
It is working, but ...
 
TIA,
 
Since you listed >= 10.04, VMWare Server and 10.10 work fine (besides the pain in the butt to get it setup). With 11.04, your options are pretty much nothing. If you want virtualization, go backwards, not forwards.  If you happen to be lucky enough to have a network card that's compatible, go for ESXI over any of the available options.

---

### Post by makmiler on 2011-05-22
> **falko said:**
> Ubuntu doesn't include or support a dom0 capable kernel from Intrepid Ibex onward.
[https://help.ubuntu.com/community/Xen#Ubuntu%27s](https://help.ubuntu.com/community/Xen#Ubuntu%27s)

I am a little bit confused about this. How so?

If you read this document [http://blog.xen.org/index.php/2011/01/14/linux-2-6-37-first-upstream-linux-kernel-to-work-as-dom0/]("http://blog.xen.org/index.php/2011/01/14/linux-2-6-37-first-upstream-linux-kernel-to-work-as-dom0/"), it clearly states that every kernel >= 2.6.37 has a built in support for xen. Dom0 support is **upstream **in all linux kernels.

> Linux 2.6.37: first upstream Linux kernel to work as Dom0

Linux 2.6.37, released just few days ago, is the first upstream Linux kernel that can boot on Xen as Dom0: Linus pulled my &#8220;xen initial domain&#8221; patch series on the 28th of October and on the 5th of January the first Linux kernel was released with early Dom0 support!

Dom0 is the first domain started by the Xen hypervisor on boot and until now adding domain 0 support to the Linux kernel has required out of tree patches (note that NetBSD and Solaris have had Dom0 support for a very long time). This means that every Linux distro supporting Xen as virtualization platform has to maintain an additional kernel patch series.

Distro maintainers, worry no more: Dom0 support is upstream! It is now very easy to enable and support Xen in the standard kernel distro images and I hope this will lead to an upsurge in distribution support for Xen. Just enabling CONFIG_XEN in the kernel config of a 2.6.37 Linux kernel allows the very same Linux kernel image to boot on native, on Xen as Dom0, on Xen as normal PV guest and on Xen as PV on HVM guest!

That said, the kernel backends, in particular netback and blkback, are not yet available in the upstream kernel. Therefore a 2.6.37 vanilla kernel can only be used to start VMs on the very latest xen-unstable. In fact xen-unstable contains additional functionalities that allow qemu-xen to offer a userspace fallback for the missing backends. This support will become part of the Xen 4.1 release which is due in the next couple of months.

In the short term the out of tree patch set has been massively reduced. It is expected that the xen.git kernel tree will soon contain the proposed upstreamable versions of the backend drivers. I strongly encourage everyone to pull these and start testing upstream dom0 support!

That said, just type grep -i xen /boot/config* (replace * with your kernel config file), and you'll see if your kernel supports xen. Mine on Ubuntu 11.04 does **out of the box**!

Have I misunderstood something?

---

