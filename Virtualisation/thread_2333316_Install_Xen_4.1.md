---
title: "Install Xen 4.1?"
date: 2016-08-09
forum: Virtualisation
---

### Post by josh168 on 2016-08-09
I have an ASUS Sabertooth 990fx motherboard. Which according to [_this post_]("http://xen.1045712.n5.nabble.com/Xen-IOMMU-disabled-due-to-IVRS-table-Blah-blah-blah-td5716461.html") has an issue: "The problem is with the BIOS; its returning bad information in the IVRS  table for the IO-APICs, which the new parser is catching and causing  AMD-Vi initialization to fail."

However as the Original Poster had mentioned Xen 4.1.2 would disregard this problem and allow you to go about your virtualization without barrier. Since I don't appear to have an alternative it would seem I need to install Xen 4.1.2. I searched [http://packages.ubuntu.com/](http://packages.ubuntu.com/) already to find this version is no longer available. I don't quite know enough about all this to figure out where or how to get it if it isn't as simple as an apt-get.

I don't know what effect this IVRS table for the IO-APICs will have on my system while virtualizing a windows 10 system under xubuntu as the host, but I'm willing to roll my dice.

If someone knows an alternative to Xen which would work for me I am open to it. I've already ruled out Virtual Box due to its PCI Passthrough requiring non shared interrupts. Which, according to my manual, is the case for my motherboard and the video card I want to passthrough. Worse than that it is shared with the SATA controller the host is installed on, as well as my USB 3 controller. Assuming I understood all the documentation involved.



Post link above:
[http://xen.1045712.n5.nabble.com/Xen-IOMMU-disabled-due-to-IVRS-table-Blah-blah-blah-td5716461.html](http://xen.1045712.n5.nabble.com/Xen-IOMMU-disabled-due-to-IVRS-table-Blah-blah-blah-td5716461.html)

---

### Post by MAFoElffen on 2016-08-09
So-- According to your link, that was a problem with that board, when Xen version 4.1 was released, but worked correctly in Xen version previous to that... That would have been a bug. That was noted by that over-3 year old post. That would have also been about the time of Ubuntu 12.04 LTS and Linux kernel 3.1.x. At that time, that mobo was new and cutting edge.

Since the current version of xen-hypervisor-amd64 in the main repo is now xen-hypervisor-4.6-amd64 (Xen version  4.6), have you confirmed that what was said there is still a problem? And now that we are on LTS 16.04 and Linux Kernel 4.4.x... ? That and you would think that here has been enough time past now for there have been  been some compatibility change updates to that board's BIOS image since that board was released.

Just saying that what was true 3 years ago, may have changed.

---

### Post by josh168 on 2016-08-09
I have already double checked BIOS versions to make sure I am still on the most up to date version. As noted in that thread, it was and is unlikely to receive an update. I have the original sabertooth, not r2.0. If an update came out to fix the issue, I am certain r2.0 would have received it but am quite doubtful r1.0 would have been considered. The last update its BIOS received was in August 2012. Around the same time my last good job ended. If I could afford a new motherboard I'd likely investigate that option instead of relying on a bug to fix my problems.

Also, the Mobo was not new or cutting edge 3 years ago.

---

### Post by heiko_s on 2016-08-09
I would try the Xen 4.4 or Xen 4.6, whatever comes with your current Ubuntu release. I have used the "force" option in the past with Xen to make it work (after an update my VM wouldn't start, but the older Xen release continued to work just fine), but over time it became unnecessary as things had been fixed.

---

### Post by josh168 on 2016-08-09
I tried out the boot option "iommu=no-intremap" which according to a couple sources was supposed to _not_ work for this motherboard or apply to the problem the motherboard has.. but it worked. So I am now happily working toward a guest machine. Fingers crossed the PCI passthrough works 100% without issue. Two nvidia cards =/

---

### Post by MAFoElffen on 2016-08-10
Congrats!!! Tell us how it goes for you...

---

### Post by josh168 on 2016-08-10
Sure thing. Is the common practice to use the same thread until the project is done? My experience is to create new threads for each new individual problem.

Right now, I'm stuck at the PCI cards I want to pass through. I can't find a way to disable them at boot in order to allow the passthrough to succeed. Presumably that is what is going wrong anyhow.
```

josh@Hank:~$ sudo xl create win10.cfg
Parsing config from win10.cfg
unable to parse PCI BDF `06.00.0' for passthrough

```

The devices:

```

06:00.0 VGA compatible controller: NVIDIA Corporation GF110 [GeForce GTX 580] (rev a1)
    Subsystem: eVga.com. Corp. GF110 [GeForce GTX 580]
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau
06:00.1 Audio device: NVIDIA Corporation GF110 High Definition Audio Controller (rev a1)
    Subsystem: eVga.com. Corp. GF110 High Definition Audio Controller
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

----
----

09:00.0 Audio device: Creative Labs EMU20k2 [X-Fi Titanium Series] (rev 04)
    Subsystem: Creative Labs EMU20k2 [X-Fi Titanium Series]
    Kernel driver in use: snd_ctxfi
    Kernel modules: snd_ctxfi


```

I've tried using this option on my grub.cfg
```
module    /boot/vmlinuz-4.4.0-34-generic placeholder root=UUID=373c5e29-3f5a-4e0d-871f-99895eb44d3b ro  quiet splash xen-pciback.hide=(06:00.0)(06:00.1)(09:00.0)
```

Then after that I tried a script for my initramfs which I found here
[http://superuser.com/questions/541854/disable-specific-pci-device-at-boot](http://superuser.com/questions/541854/disable-specific-pci-device-at-boot)

Nothing has disabled the devices so far, they still show up using a driver. The video card shows up still as a disabled monitor.

---

### Post by heiko_s on 2016-08-10
Have a look at this thread, step 11: [https://forums.linuxmint.com/viewtopic.php?f=231&t=112013]("https://forums.linuxmint.com/viewtopic.php?f=231&t=112013")

Have you tried that?

The above method uses xen-pciback in the initramfs and hides the graphics card from other drivers. It replaces the grub.cfg method and has worked better for me and many other users of my how-to.

I am currently running kvm and use the vfio-pci driver to bind to the graphics card as explained here: [https://forums.linuxmint.com/viewtopic.php?f=231&t=212692&start=40#p1174032]("https://forums.linuxmint.com/viewtopic.php?f=231&t=212692&start=40#p1174032"). KVM is yet another option to achieve VGA passthrough.

---

### Post by josh168 on 2016-08-10
> **heiko_s said:**
> Have a look at this thread, step 11: [https://forums.linuxmint.com/viewtopic.php?f=231&t=112013](https://forums.linuxmint.com/viewtopic.php?f=231&t=112013)

Have you tried that?

The above method uses xen-pciback in the initramfs and hides the graphics card from other drivers. It replaces the grub.cfg method and has worked better for me and many other users of my how-to.

I am currently running kvm and use the vfio-pci driver to bind to the graphics card as explained here: [https://forums.linuxmint.com/viewtopic.php?f=231&t=212692&start=40#p1174032](https://forums.linuxmint.com/viewtopic.php?f=231&t=212692&start=40#p1174032). KVM is yet another option to achieve VGA passthrough.

Since my earlier post I have been able to get the devices to use the pciback driver, but I still get the same error. I've tried your method as well, and it did work, but again the same error persists.

```

06:00.0 VGA compatible controller: NVIDIA Corporation GF110 [GeForce GTX 580] (rev a1)
    Subsystem: eVga.com. Corp. GF110 [GeForce GTX 580]
    Kernel driver in use: pciback
    Kernel modules: nvidiafb, nouveau, nvidia_304_updates
06:00.1 Audio device: NVIDIA Corporation GF110 High Definition Audio Controller (rev a1)
    Subsystem: eVga.com. Corp. GF110 High Definition Audio Controller
    Kernel driver in use: pciback
    Kernel modules: snd_hda_intel
---
---
josh@Hank:~$ sudo xl create win10.cfg
[sudo] password for josh: 
Parsing config from win10.cfg
unable to parse PCI BDF `06.00.0' for passthrough
josh@Hank:~$ 

```

My best guess at the moment is my card isn't compatible with pci passthrough. I've found some highly detailed walkthroughs using Antergos Linux, should I perhaps try under that OS instead?

Even with high verbosity I don't get a lot of information to run with and try and resolve my situation.

```

josh@Hank:~$ sudo xl -vvvv create win10.cfg
Parsing config from win10.cfg
unable to parse PCI BDF `06.00.0' for passthrough
xc: debug: hypercall buffer: total allocations:7 total releases:7
xc: debug: hypercall buffer: current allocations:0 maximum allocations:1
xc: debug: hypercall buffer: cache current size:1
xc: debug: hypercall buffer: cache hits:6 misses:1 toobig:0

```

I am at the end of my rope. What should I do? Wait until I can afford a newer card?

---

### Post by heiko_s on 2016-08-25
You can still try kvm. See the link in my previous post. Nvidia cards can pose problems to Xen PCI passthrough - actually only the Quadro 2000 and above series and the newer professional cards (Titanium etc.) support VGA passthrough under Xen. Nvidia cripples their consumer grade cards so they won't support a virtual environment. HOWEVER, kvm seems to work pretty straightforward. See my tutorial mentioned before. (I don't want to pull you away from Xen, but if it doesn't work, you might as well try an alternative.)

---

