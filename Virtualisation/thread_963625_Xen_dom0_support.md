---
title: "Xen dom0 support"
date: 2008-10-30
forum: Virtualisation
---

### Post by Loranga on 2008-10-30
[http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/virtualization](http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/virtualization) says "Running a Xen host (Dom0) on Ubuntu still requires a community maintained kernel in universe."

Which kernel package is this, and is this kernel "in phase" with the normal kernel in Intrepid 8.10?

---

### Post by wamcvey on 2008-10-30
I've tried used the -server kernel from Intrepid as well as from Hardy, and both give me the error 

> (XEN) *** LOADING DOMAIN 0 ***
(XEN) elf_init: not an ELF binary
(XEN)
(XEN) ****************************************
(XEN) Panic on CPU 0:
(XEN) Could not set up DOM0 guest OS
(XEN) ****************************************


Eagerly awaiting feedback on how to get dom0 support working with an Intrepid install.

---

### Post by bedge on 2008-11-01
I was expecting a recent dom0 kernel with intrepid. This is quite disappointing.

What is everyone else using for their dom0 OS?

---

### Post by klauskiwi on 2008-11-04
I am suffering from the same problem.. Tried using the -server version hoping that it would be 'xen-enabled', but got the message reported by wamcvey above.

---

### Post by albertcz on 2008-11-04
Hi

I'm see in the ubuntu 8.10 doesn't existing kernel support xen dom0, kernel from hardy which support  xen dom0 and domU 2.6.24 is broken,but if you have using xen could you get a kernel from lenny packages [http://packages.debian.org/lenny/xen-linux-system-2.6.26-1-xen-686](http://packages.debian.org/lenny/xen-linux-system-2.6.26-1-xen-686)
I using this kernel with dom0 and it's is ok.

it's a pity that cannonical don't support xen dom0 in ubuntu 8.10

---

### Post by geraldbrandt on 2008-11-07
So, what is everyone using for dom0?  I'd use KVM, but I need to pass through PCI cards.

---

### Post by randallb on 2008-11-11
I hope the Debian/Ubuntu developers will reconsider their decision to remove dom0 support, as I find Xen to be the best virtualization solution for non-VT-capable servers.  It's not fair to all the users of non-VT systems, especially considering that VT is still only couple years old.


In the meantime, I was able to get Ubuntu Intrepid 8.10 to run as a dom0 by manually downloading a Linux image package from Hardy and installing it manually with dpkg -i.

[http://packages.ubuntu.com/hardy-updates/linux-image-2.6.24-19-xen](http://packages.ubuntu.com/hardy-updates/linux-image-2.6.24-19-xen)

(2.6.24-21-xen will probably work too, and is probably safer, but I haven't yet tried it.)

I have Xen 3.3 running with one domU. The only issue I ran into so far was that the domU wouldn't boot if I configured it to use /boot/vmlinuz-2.6.27-7-server and /boot/initrd.img-2.6.27-7-server.  Instead, I am using the 2.6.24-19-xen kernel/initrd in the domU.

---

### Post by C38a7r1zvl on 2008-11-11
I am very annoyed by the dropped dom0 support as well. Is anybody aware of community efforts to bring xen dom0 to Ubuntu's 2.6.27 kernel line?

kvm is not an option for me and I am having big trouble with the hardy kernel (the dreaded "Out of SW-IOMMU space" issue)..

---

### Post by randallb on 2008-11-12
> **dePOLL said:**
> I am very annoyed by the dropped dom0 support as well. Is anybody aware of community efforts to bring xen dom0 to Ubuntu's 2.6.27 kernel line?

kvm is not an option for me and I am having big trouble with the hardy kernel (the dreaded "Out of SW-IOMMU space" issue)..

I'm also seeing those errors.  Occasionally, lots of these appear in the kern.log:

> PCI-DMA: Out of SW-IOMMU space for 65536 bytes at device 0000:04:01.0

lspci shows that the related device is the server's SCSI controller:

> 04:01.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 08)

---

### Post by C38a7r1zvl on 2008-11-13
For me it's SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA. From what I understand the bug is prominent with RAID controllers but might also occur with SATA controllers or NICs. According to [#247148]("https://bugs.launchpad.net/ubuntu/+bug/247148") it [has been fixed upstream a few months ago]("https://bugs.launchpad.net/ubuntu/+bug/247148/comments/2").

Why this is ignored by the kernel team I do not know. It really seems like they are leaving dom0 support out to die slowly and painfully.. 

I will hopefully find some time to look further into the upstream patches and maybe even patch the .27 kernel to xen bliss but was hoping there might already be a community effort underway. Because my kernel knowledge is really quite embarassing..

---

### Post by C38a7r1zvl on 2008-11-13
randalib: I haven't been able to reproduce the errors after applying Amit's patch from [#247148]("https://bugs.launchpad.net/ubuntu/+bug/247148").

If you are willing to give it a try, here's how to patch & rebuild your kernel without having to press return more than once :)

```
sudo aptitude install -y linux-kernel-devel fakeroot build-essential \
&& sudo apt-get build-dep linux-image-$(uname -r) \
&& apt-get source linux-image-$(uname -r) \
&& cd linux-`uname -r | sed 's/-.*$//'` \
&& curl http://launchpadlibrarian.net/17279382/005-swiotlb-fix.patch -o debian/binary-custom.d/xen/patchset \
&& AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules custom-binary-xen \
&& cd .. \
&& sudo dpkg -i linux-image-*xen_*.deb
```
(execute from within a directory you have write access to)

If you have multiple CPUs you can speed compilation up by prepending the build command with DEB_BUILD_OPTIONS=parallel=n. E.g. for two cores:
```
DEB_BUILD_OPTIONS=parallel=2 AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules custom-binary-xen
```

Good luck,
Niels

---

### Post by elwell642 on 2008-12-05
Hi all,

  I'm running a Hardy dom0 with a 2.6.24-19 xen-enabled kernel along with a number of paravirtualized Hardy domUs.  In Googling around and finding this thread (among many others), it sounds like there is no dom0 support in Intrepid.  Okay.  But I'm now wondering about what that implies for upgrading domUs to intrepid or (later) jaunty.

  I tried doing a dist-upgrade to Intrepid on one of the Hardy domUs, and that seemed to work just fine - though it's still using the same [Hardy] kernel.  But I'm not sure if this will cause problems in the future.

  So I suppose the more basic question is: can I run a newer Ubuntu release using an older kernel?  (That's probably a linux newbie question, but, well, that's me! =))

  Thanks for any advice and/or links you can offer!

---

### Post by bodhi.zazen on 2008-12-05
domU is supported in all versions (including 8.10 and I presume 9.04 as well, although 9.04 is in alpha).

dom0 is supported in LTS (8.04).

---

### Post by elwell642 on 2008-12-05
> **bodhi.zazen said:**
> domU is supported in all versions (including 8.10 and I presume 9.04 as well, although 9.04 is in alpha).

dom0 is supported in LTS (8.04).

Bodhi,

  Thanks very much for the quick reply!  Please forgive my lack of understanding, but could you clarify a bit?

  Does that then mean that I can use the 8.04 dom0 and 8.10 domU with the same kernel?  Won't the 8.10 apps expect a more recent kernel?

  Thanks again for your help!!

~Tom

---

### Post by bodhi.zazen on 2008-12-05
I am afraid I do not know enough about Xen, but I do not see why not. By that you can run various versions of Linux in Xen and they certainly do not use the same kernels, so it was not my impression that host and guest had to use the same kernel. But that is just a guess.

---

### Post by tdjb on 2008-12-06
> **albertcz said:**
> Hi

I'm see in the ubuntu 8.10 doesn't existing kernel support xen dom0, kernel from hardy which support  xen dom0 and domU 2.6.24 is broken,but if you have using xen could you get a kernel from lenny packages [http://packages.debian.org/lenny/xen-linux-system-2.6.26-1-xen-686](http://packages.debian.org/lenny/xen-linux-system-2.6.26-1-xen-686)
I using this kernel with dom0 and it's is ok.

it's a pity that cannonical don't support xen dom0 in ubuntu 8.10

Could you elaborate on your usage of the Debian kernel? I've tried this today without success. I just install the kernel/module packages using dpkg (which worked), but the domU's will not boot up. I get an "XENBUS: Waiting for devices to initialise:" message which sits around for about 300s, then an error about not being able to attach to a block device.

---

### Post by Xepra on 2008-12-17
I am not sure how posting blogs entries is viewed on these forums.  Honestly I am not doing it to self-promote, it is just a bit long to put in a forum message.  The blog really is just notes to myself anyway...

[http://cwshep.blogspot.com/2008/12/howto-ubuntu-intrepid-ibex-810-xen-dom0.html](http://cwshep.blogspot.com/2008/12/howto-ubuntu-intrepid-ibex-810-xen-dom0.html)


I am not sure how many of the bugs mentioned this will fix, but perhaps it will clarify somethings for you guys.  I do have a 2.6.27-5 kernel (suse forward port) running as an intrepid dom0, as well as on guests (including an intrepid guest), and it has been stable so far.

To clarify, not all xen kernels can be both dom0 and domU.  dom0 requires "backend" drivers and domUs require "frontend" drivers for networking, block devices, etc.  A kernel can contain either, both, or none of these.

There is something new called "paravirt_ops" which appears to be a standard interface for linux to run on a hypervisor.  The vanilla intrepid kernel has this, but I couldn't get it to recognize my drives (virtual block devices, ie hda1 and hda2).

---

### Post by helgesdk on 2009-05-15
Any news on this matter?
Are there any plans on implementing Dom0 support in Ubuntu?

---

### Post by bodhi.zazen on 2009-05-15
> **helgesdk said:**
> Any news on this matter?
Are there any plans on implementing Dom0 support in Ubuntu?

Dom0 is supported in Ubuntu 8.04.

There are no plans to support Dom0 in 8.10, 9.04, or 9.10.

To be honest, most distros are moving away from Xen to KVM. I know of no distro that plans to support Xen Dom0 moving forward, Ubuntu or otherwise.

Perhaps check with xen.

[http://www.cl.cam.ac.uk/research/srg/netos/xen/](http://www.cl.cam.ac.uk/research/srg/netos/xen/)

The Xen "how-to's" are here ;

[http://wiki.xensource.com/xenwiki/HowTos](http://wiki.xensource.com/xenwiki/HowTos)

I see no OS more up to date then Ubuntu 8.04 or Centos 5.0

So either use Centos 5.0, ubuntu 8.04, Debian etch, build your own kernel, or find an alternate to Xen (OpenVZ, KVM, VirtualBox, or VMWare (ESi).

Ubuntu 8.04 is LTS and is supported for 5 years server side.

---

