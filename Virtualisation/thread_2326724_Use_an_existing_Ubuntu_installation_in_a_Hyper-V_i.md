---
title: "Use an existing Ubuntu installation in a Hyper-V instance?"
date: 2016-06-04
forum: Virtualisation
---

### Post by DMcCunney on 2016-06-04
I'm dual-booting Win10 Pro and Ubuntu 16.04 on a quad-core Xeon box with 8GB RAM.  Win10 and Ubuntu are installed on and boot from and SSD.  Data is mostly kept on a SATA HD.

Since Hyper-V is an option, I turned it on and installed the pieces.  I'm interested in getting Ubuntu up as a guest in Hyper-V.  I am not a gamer or doing other things that push the envelope in either OS, and will be quite happy with adequate performance.

There are lots of tutorials on installing Ubuntu into Hyper-V from an ISO.  What I'd *like* to do is get my *current* Ubuntu install up under it.

Is it doable?  Has anyone done this and can provide pointers?  (I did a quick search here but didn't see anything obvious.  If I missed it, please point me at the thread.)

I'll go the ISO route if not.

Thanks in advance.
________
**Dennis**

---

### Post by houstonbofh on 2016-06-06
Yes.  The easiest way is to use clonezilly to copy the drive to an image file, and mount that with your VM software.  I do not know how to mount raw images with hyper-v however.

---

### Post by DMcCunney on 2016-06-06
> **houstonbofh said:**
> Yes.  The easiest way is to use clonezilly to copy the drive to an image file, and mount that with your VM software.  I do not know how to mount raw images with hyper-v however.
Hmmm.

Okay, but if I understand correctly, I will then *have* two Ubuntu instances: the image file I load into Hyper-V, and the one I boot into going the multi-boot route.  Over time, these will get somewhat out of sync.

I would probably want to reconfigure my Ubuntu installation to put things like Home and Opt on a separate file system, that would get mounted by the running instance, since most of the stuff that might change would be in those locations.

I might be just as well served to install into Hyper-V from an ISO and configure that to resemble the existing instance with the file system changes mentioned, instead of going the clonezilly route..

And there are Win10 imposed quirks to deal with.  The CPU is a quad-core Xeon, but Win10 refuses to recognize all four cores.  The Dell BIOS has a multi-processor option defaulting to On that is currently Off.  Set to off, it enables one virtual CPU with two cores.  Set to On, it enables a second virtual CPU with two more cores.  But if I set it to On, Win10 refuses to load, claiming multi-processor operation is not supported.  Win10 *does* support dual physical CPUs in a box, and multiple core on CPUs, but my older Xeon X3220 model isn't on Intel's official Win10 supported list.  Win10 appears to be a lot fussier about just which hardware it supports than Win7 was.  (Win10 was an upgrade from Win7 Pro, which I don't recall having this limitation.  And Ubuntu appears not to have it - if I set multi-processor operation to On in the BIOS and boot into it, it just runs.)

Not being able to use all four cores in Win10 makes virtualization a more questionable proposition, since I assume Hyper-V would inherit the restriction, and it's something where I think I'd really want all four cores.  In Win10, it's not a huge problem since the sorts of things I do don't normally benefit from multiple cores.  One core gets the foreground task (usually my browser), and the second gets the background OS stuff.  I'm not doing development, or running tasks that can use multiple cores.

Booting off an SSD, exiting one OS and booting into the other is relatively painless.  If I'm in Win10, it takes a minute or less to exit it and boot into Ubuntu.  Virtualization would be a convenience, but I could live without it.  (I have thus far...)

I need to poke around some more about loading a raw image into Hyper-V, to be able to use the existing Ubuntu instance without cloning.

Thanks for the info.  I now have a somewhat better notion of what I'm trying to do.
________
**Dennis**

---

### Post by MAFoElffen on 2016-06-07
Well/No. What he described was an attempt to convert your physical image from disk, into a virtual image. (<-- Migration from physical to virtual). Adapt the same methodology, but with other tools to convert from one to another:
 - [Handy Tool for Converting KVM / VMware Images to Hyper-V]("https://blogs.msdn.microsoft.com/virtual_pc_guy/2015/06/22/handy-tool-for-converting-kvm-vmware-images-to-hyper-v/")
Using the resultant raw from clonezilla to a vhdx image... VirtualBoxes vboxmanage also has a raw to other formats "convertfromraw" option.

Besides clonezilla, to get the intitial physical to raw or vmdk image, also somewhat popular seems to be the VMware vCenter Converter: P2V Virtual Machine Converter...

---

