---
title: "The VGA passthrough club - did you succeed, and how?"
date: 2013-02-01
forum: Virtualisation
---

### Post by heiko_s on 2013-02-01
I can't do away with Windoze, but I hate dual-boot. I also need native (or near-native) graphics support in the Windows VM.

In the end I chose Xen to host Linux and a Windows 7 VM which uses a dedicated graphics card for native graphics performance. It works extremely well, with what I consider top-notch performance that doesn't stand (much) behind a native Windows installation on bare metal.

In fact, I'm so thrilled about it that I wonder why not every dual-booter is switching to virtualization. (I'm actually not that surprised since it was quite challenging to get it working.)

Here my questions:

Has anybody tried VGA passthrough?

If yes, which hypervisor/method did you use (Xen, KVM, VMware, etc.)?

How easy or difficult was it?

In the end I would like to know if there are perhaps better or easier ways to get it working. Thanks in advance for your feedback!

---

### Post by xelra on 2013-02-02
I once tried to setup a xen virtualization with Linux as Host and Win7 as guest with VGA passthrough, because I believed that I can get 99%+ native performace.
At the time tough it was very new and undocumented, so I gave up on it.

I know that to get it working you need hardware that supports both VT-x and VT-d.

My goal was to get fast switching on 2 desktops, the way you would have 2 full OSes booted simultaneously.
Can you confirm your Windows 7 installation behaves as native? What about other peripherals? Scanner, printer, gamepad, etc.?

Do you have a guide?

---

### Post by heiko_s on 2013-02-02
> **xelra said:**
> I once tried to setup a xen virtualization with Linux as Host and Win7 as guest with VGA passthrough, because I believed that I can get 99%+ native performace.
At the time tough it was very new and undocumented, so I gave up on it.

I know that to get it working you need hardware that supports both VT-x and VT-d.

My goal was to get fast switching on 2 desktops, the way you would have 2 full OSes booted simultaneously.
Can you confirm your Windows 7 installation behaves as native? What about other peripherals? Scanner, printer, gamepad, etc.?

Do you have a guide?

You indeed need suitable hardware. Here is what you need:

1. CPU with VT-d (Intel) or AMD-Vi (AMD) support. This feature is also called IOMMU. See [http://en.wikipedia.org/wiki/IOMMU_hardware_list]("http://en.wikipedia.org/wiki/IOMMU_hardware_list"), or for Intel CPU's see [http://ark.intel.com/search/advanced/?s=t&VTD=true]("http://ark.intel.com/search/advanced/?s=t&VTD=true").

2. A motherboard that supports VT-d. See the Wikipedia link above, as well as [http://www.overclock.net/t/1338063/vt-d-compatible-motherboards]("http://www.overclock.net/t/1338063/vt-d-compatible-motherboards") and [http://wiki.xen.org/wiki/VTd_HowTo]("http://wiki.xen.org/wiki/VTd_HowTo").

3. A motherboard BIOS that supports VT-d. I'm not joking here, one BIOS release may support VT-d, the next one doesn't. In some cases there is no way going back to the earlier BIOS that does support it. See links under 2.

4. A graphics card that supports VGA passthrough. In general, most modern AMD (ATI) graphics cards will work, but it's best to check here [http://wiki.xen.org/wiki/XenVGAPassthroughTestedAdapters]("http://wiki.xen.org/wiki/XenVGAPassthroughTestedAdapters") and [www.overclock.net/t/1307834/xen-vga-passthrough-compatible-graphics-adapters]("www.overclock.net/t/1307834/xen-vga-passthrough-compatible-graphics-adapters").
Some Nvidia graphics adapters are also supported, namely the Quadro series of "Multi-OS" capable cards starting with the Quadro 2000 model upwards (the Quadro 600 for example isn't specified as "Multi-OS"). There are some more Nvidia graphics adapters that work, but first check the links above if it's listed.
The newer Xen 4.2 hypervisor supposedly improves graphics cards compatibility, though I haven't tried it.

It is MUCH easier if you have two graphics cards, or a CPU internal GPU (like on most new Intel desktop CPUs) and a discrete graphics card for passthrough.One will serve Linux, the other your Windows guest.

If your hardware doesn't meet the above, either replace the incompatible part, or forget the whole thing!

I've written a how-to for Linux Mint 13/14, which should likewise work with Ubuntu 12.04 and 12.10: [http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013").

Now to your questions.

> My goal was to get fast switching on 2 desktops, the way you would have 2 full OSes booted simultaneously.
My PC works as if I have two PCs. I could hook up two screens, keyboards and mice and two people would be able to use it at the same time, with full video acceleration on both. Right now I switch from one to the other via KVM button and the input selector on my screen, but if I have to go forth and back a lot I run a remote desktop in Windows to connect to my Linux dom0, or vice versa. I use a SAMBA share under Linux to copy files between the two.

> Can you confirm your Windows 7 installation behaves as native?
95% yes. Everything except the following two issues work as if I was running Windows directly on the hardware. The two issues I've found are:
I) Youtube video stops after a few seconds, hangs for a while, and continues, just to stop again after a few seconds. This is most likely a networking issue with the bridge, though I haven't figured out what exactly. Somehow Windows "looses" the DNS server, or access to it. One work around would be to pass through a dedicated NIC. I haven't tried it though.
II) I can't watch video using VLC when the video file is on a network drive. I believe this is the same network problem as above.
EDIT: Both problems are solved now using the latest GPLPV drivers under Windows.

Other than these two issues I haven't found any problem.

> What about other peripherals? Scanner, printer, gamepad, etc.?
In addition to the graphics card, I'm passing 2 USB controllers through to Windows. Everything connected to these ports is fully controlled by Windows, with Windows native drivers.
Just an example how well this works: I use Windows for photo editing. To calibrate my screen I use a spectrophotometer (some device that measures light / colors) which is connected via USB. The software then shows different color patches on the screen which my calibrating device reads and reports back to the PC (via USB port). At the end, the software loads the corrected color curve directly into my screen via the DVI port of the graphics card. This can only work when the calibration software is able to communicate with the graphics card.
Other external devices I frequently use under Windows are:
- Keyboard and mouse are connected via KVM USB switch;
- CF card reader (to transfer photos from the camera's CF cards to the PC);
- External hard drive for backup - it's automatically detected by the backup program when I connect it to the USB port;
- USB audio controller - a low-cost ~5$ USB stick that works without any issues, it's permanently plucked in;
- USB flash drives - they work as expected.

I haven't set up my printer yet to work with Windows. But I can't see any reason why it shouldn't work. I have both a USB 2.0 and a USB 3.0 controller passed to Windows. The transfer speed is as expected. If you have an external HDD or memory card reader to connect, use a USB 3.0 controller - it makes a huge difference.

Good luck!

---

### Post by hurenkam on 2013-02-07
> **heiko_s said:**
> I can't do away with Windoze, but I hate Has anybody tried VGA passthrough?

Yes, I have a setup with 2 desktops, each running in their own virtual machine with passed through radeon4350 and usb cards.
Apart from that, a few other virtual machine servers run on the same hardware.

> **heiko_s said:**
> 
Which hypervisor/method did you use (Xen, KVM, VMware, etc.)?

I'm using Xen 4.2 at the moment, it seems to me that in general Xen is way ahead of the game when it comes to PCI Passthrough.

> **heiko_s said:**
> 
How easy or difficult was it?

Once i started to use the catalyst driver instead of the open source driver (which complains about not being able to find the bios), everything was pretty straight forward. 
I installed ubuntu and windows7 in a vnc session and later installed Catalyst. Windows 8 was even easier, it installed a working vga driver out of the box.
Note that i just used pci-passthrough, not the advanced vga-passthrough patches.
Besides the vga adapter itself, i also passthrough the onboard audio of the adapter (hdmi), and an usb controller, so basically i have 2 seperate terminals, each running their own os (either Ubuntu/Windows7/Windows8).
All operating systems behave asif they run on native hardware, only difference is that the boot screen doesn't appear on my vga cards, because i chose to do only pci-passthrough. The boot window appears on the VNC session.

Note that as stated above, using the right CPU, Mainboard and VGA Card is essential here.
In my case: Intel Core i7 860, Asus P7P55D Evo, Asus EAH4350 Silent.

---

### Post by heiko_s on 2013-02-16
@hurenkam: Thanks for sharing your experiences with virtual machines and VGA/PCI passthrough. It really looks like Xen is ahead of the game, as I've seen very few reports about successful KVM or other passthrough.
Yes, having the right hardware is essential.

---

### Post by heiko_s on 2013-04-18
Update: Things seem to be changing lately. I see more and more people using kvm for VGA passthrough. While there are problems like host freezing when exiting/rebooting guest, which has a solution or work-around, some report that it's been easier to implement and has less problems with graphics adapters and drivers under the host OS (Linux).

So far it seems that Xen is still troubled with proprietary Nvidia driver support under dom0, and generally with VGA passthrough support of Nvidia cards. I don't know if kvm is better in that, but it may be worth a try.

Last not least, Xen has moved to 4.2.1 and xl toolstack and the xm toolstack has been discontinued. Some report problems with vga passthrough using the xl toolstack. I can't say as I'm still using xm / xend.

Note: My network / Youtube problems have been solved after installing the latest GPLPV drivers from [http://www.meadowcourt.org/downloads/]("http://www.meadowcourt.org/downloads/").

---

### Post by jaripetteri on 2013-05-10
Just drop in couple lines about my HTPC Home Virtual Server setup. I have build this same time as finishing my house during past year. Haven't have time to this but need to something to get my mind of house building time to time.

I have now i7 3770T CPU and Asrock Z68 Extreme 4 Gen 3 MB with 24GB memory. 256GB OCZ Vertex 4 SSD for root fs's and VM's plus 2x 3TB and 1,5TB HDD's for media and MythTV recordings. Also 2x 3TB WD My Book Elements USB 3.0 as backup drives. Most of media drives are bypassed to VM giving it Asmedia AS1061 SATA3 -PCIe card and USB 3.0 host from MB. Also two GPU (Radeon HD7750 & HD7770, did try GTS450 without success) are PCI Pass through to two VM's, another one as my main HTPC and another I'm planing to use as daily desktop (currently still using x220).

I'm using KVM as visualize platform and mainly Lubuntu and Ubuntu 12.04's. HTPC is Lunux Mint and Desktop Windows 7. With Windows I have some stability issues and therefore not using it daily yet. There is three VM's serving as MythTV backend, MySQL server and that NAS. Also DVB-C card is pass through to VM. During building I have had issues with IRQ's, getting short off those all a time and very few PCIe card is capable to pass through. Now I like to change my MB to something Z77 without PCI slots to get more PCIe slots since I'm running out of those and could use couple more... :)

And this all was possible because I run little web store and need VM server to test different things before to take those in use. I kinda got hooked to this VM thing... :) All of above was earlier on AMD x2 4580e server with single Linux Mint 12 installation.

---

### Post by heiko_s on 2013-05-12
> **jaripetteri said:**
> Just drop in couple lines about my HTPC Home Virtual Server setup. I have build this same time as finishing my house during past year. Haven't have time to this but need to something to get my mind of house building time to time.

I have now i7 3770T CPU and Asrock Z68 Extreme 4 Gen 3 MB with 24GB memory. 256GB OCZ Vertex 4 SSD for root fs's and VM's plus 2x 3TB and 1,5TB HDD's for media and MythTV recordings. Also 2x 3TB WD My Book Elements USB 3.0 as backup drives. Most of media drives are bypassed to VM giving it Asmedia AS1061 SATA3 -PCIe card and USB 3.0 host from MB. Also two GPU (Radeon HD7750 & HD7770, did try GTS450 without success) are PCI Pass through to two VM's, another one as my main HTPC and another I'm planing to use as daily desktop (currently still using x220).

I'm using KVM as visualize platform and mainly Lubuntu and Ubuntu 12.04's. HTPC is Lunux Mint and Desktop Windows 7. With Windows I have some stability issues and therefore not using it daily yet. There is three VM's serving as MythTV backend, MySQL server and that NAS. Also DVB-C card is pass through to VM. During building I have had issues with IRQ's, getting short off those all a time and very few PCIe card is capable to pass through. Now I like to change my MB to something Z77 without PCI slots to get more PCIe slots since I'm running out of those and could use couple more... :)

And this all was possible because I run little web store and need VM server to test different things before to take those in use. I kinda got hooked to this VM thing... :) All of above was earlier on AMD x2 4580e server with single Linux Mint 12 installation.

Thanks for sharing your setup - this sounds really good! A little over a year ago I had a hard time finding documentation on VGA passthrough using kvm. Things have changed and I've found a few places to consult with, specifically [http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19770787]("http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19770787").

I'm using Xen at the moment, with Linux Mint 14 as dom0 and Windows 7 Pro as domU, and am hesitant to switch to kvm, as everything so far has been rock solid. My installation uses the regular Linux Mint and Ubuntu repositories, no development packages or kernel compilations. From what I gathered kvm would need a newer kernel and perhaps some patches to get all the functionality?

What did impress me about kvm was what looks to be better support for graphics cards, in particular Nvidia cards. With Xen, one better sticks to AMD cards. I would have liked to run a Nvidia card under dom0, but Nvidia proprietary drivers don't seem to play well with a Xen hypervisor.

You've got a bunch of VMs running, 5 if I'm not mistaken. I'm curious about your CPU resource allocation? I'm really not familiar with kvm and have no idea how the kvm CPU scheduler works. The reason I'm asking is that in my setup I would need all CPU resources I can get for my Windows VM, but I do not want to pin these resources to the Windows VM. Is there a way to overbook CPU resources under kvm, for example assign 10 VCPUs to VM-1 and another 10 VCPUs to VM-2, while the host gets a guaranteed minimum VCPUs of 2 (I've got a 6-core CPU giving me 12 VCPUs)? Then if VM-1 doesn't need all the CPU resources they would be available under VM-2 or even the host.

My setup is somewhat flawed in that I use dom0 as my regular desktop, which I think isn't such a good idea. If I move to kvm I would want to change that, using a server distro for the host and running my Linux Mint desktop in a VM, same as the Windows VM.

Contrary to your approach of passing through most of the media drives (i.e. the controllers), I use LVM volumes for both the host and the Windows VM. So my host (dom0) has access to all the drives and backup is very simple (snapshot the volume, then dd and pigz/gzip to compress the data). Note: My Windows VM uses RAW storage on LVM. Here some Passmark benchmarks run within the Windows VM:

Xen with Windows VM using a Sandisk Extreme 120GB SSD:
[IMG]http://www.pbase.com/merhav/image/149363644/original.jpg[/IMG]


Xen with Windows VM using two LVM striped WD20EARX 2TB HDDs:
[IMG]http://www.pbase.com/merhav/image/149363645/original.jpg[/IMG]


Xen with Windows VM using LVM concatenated WD1001FALS and WD5000AAKS drives:
[IMG]http://www.pbase.com/merhav/image/149363646/original.jpg[/IMG]

---

### Post by GizmoChicken on 2013-05-14
> **heiko_s said:**
> My setup is somewhat flawed in that I use dom0  as my regular desktop, which I think isn't such a good idea. If I move  to kvm I would want to change that, using a server distro for the host  and running my Linux Mint desktop in a VM, same as the Windows  VM.

Following your incredibly detailed and well-written  [guide]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013"),  I was able to set up GPU passthrough to a Windows 7 guest using a  Radeon HD6670 card and Ubuntu 12.10 Desktop as dom0. Thanks for the guide!

But I too would prefer a server-based dom0, and so I've been experimenting with [XCP 1.6]("http://www.xenproject.org/downloads/xen-cloud-platform-archives/xen-cloud-platform-16.html"), which is an open source version of XenServer.  Using XCP 1.6, I've had good luck with GPU passthrough to a Windows 7  guest using the Catalyst 13.4 driver with a Radeon HD6670 card.  

However, at least for me, getting GPU  passthough to work with a _Linux guest_ has been much more of a  challenge, regardless of whether I use XCP 1.6 or Ubuntu 12.10 as dom0.   Using XCP 1.6 as dom0, I've tried Ubuntu 12.04, 12.10 and 13.04 as guests, each  with various display drivers.  So far, of the nearly innumerable combinations that I  tried, the only combination that has worked for me has been Ubuntu 12.04  combined with whatever default version of Catalyst (not the update)  that is found in the Ubuntu repository.  

So to reiterate, in addition to GPU passthrough to a Windows 7 guest, GPU passthrough to an Ubuntu 12.04 guest is also possible using XCP 1.6 as dom0.  Passthrough to other Linux guests may also be possible using proper settings.  _I would greatly appreciate  hearing about any successes others have had with GPU passthough to other  Linux guests, whether using vanilla Xen, XCP or even KVM._

Regarding XCP 1.6, although passthrough of the primary GPU to a guest is possible, based on my experiences, I do _not_  recommend doing so.  Rather, I recommend devoting the primary video  card to the XCP console.  But the good news is that even a cheap card is sufficient for use as primary video  card for the XCP console.  And if the bios settings of your motherboard allow for selecting  between PCI and PCIe as the primary boot graphics card (my Asus M5A99FX  motherboard allows for this),  to conserve your PCIe slots, I recommend  devoting a cheap PCI card (not PCIe card) to the XCP console.  In may  case, an ATI Rage 8 MB PCI Video Graphics Card ($10), which only offers  VGA output, works great for me as the primary graphics card devoted to the  XCP console.  (Other PCI cards, such as those having DVI and/or HDMI output  my be more suitable for some applications.)

The XCP console  provides an easy (menu-based) means for starting and stopping VMs.   From its menus, you can also find lots of system information.  However,  XCP relies on "xe" rather than "xm" or "xl" for management.  And  unfortunately, "xe" commands can be a bit cumbersome.  So many prefer a GUI based approach for managing more complicated tasks in XCP, with the Windows-based [XenCenter]("http://community.citrix.com/xencenter") currently being  the most popular option. (XenCenter can be run from a network-attached laptop.)   Although XenCenter isn't open source, it is,  at least as of the time of this writing, freely [downloadable]("http://citrixxperience.com/2012/02/24/download-and-install-citrix-xencenter-6-0/") from  [Citrix]("http://www.citrix.com/products/xenserver/resources-and-support.html") after creating a free Citrix account.  ([XenOrchestra]("https://xen-orchestra.com") is an open source web GUI that is currently  under development, but not yet ready for production.)

Even if you use   XenCenter for VM management, you'll still need to use "xe" commands on  limited occasions, such as for setting up PCI passthrough to USB  controllers, etc.  The PCI passthrough command in "xe" takes the  following form:

```
xe vm-param-set other-config:pci=0/<pci-id#0>,1/<pci-id#1>,2/<pci-id#2>,n/<pci-id#n>  uuid=<uuid>
```

The  <uuid> for a given VM is obtainable from XenCenter and each  <pci-id#> can be obtained using the familiar "lspci" command after connecting to XCP, such as via ssh.  Here's an example using an "xe" command for passthrough of seven usb controllers to one VM:

```
xe  vm-param-set  other-config:pci=0/0000:00:12.0,1/0000:00:12.2,2/0000:00:13.0,3/0000:00:13.2,4/0000:00:14.5,5/0000:00:16.0,6/0000:00:16.2  uuid=0370e4b4-5d5b-10b5-245b-74317cc049aa
```

To add or  remove devices from passthough, shut down the VM, edit the command to  add or remove the <pci-id#>, rerun the edited command, and then  restart the VM.  For example, to remove all devices from the VM in the  above example, shutdown the VM and run the following command:

```
xe vm-param-set  other-config:pci=  uuid=0370e4b4-5d5b-10b5-245b-74317cc049aa
```

I hope that the above is of help to anyone who wants to give XCP a try.

---

### Post by heiko_s on 2013-05-14
@GizmoChicken: Thanks for sharing your experience with XCP ! Good to see that you ventured into new territory.

I never gave XCP a try as I heard that some things are easier to accomplish while others are more difficult. Once I solved the hardware part (graphics card), I felt that Xen is rather straight forward.

With regard to the Linux domU VGA passthrough, I suppose you had the Linux guest configured as HVM guest. I'm wondering how a PV guest would work, and if it could use the proprietary graphics drivers, just like dom0? Actually I never gave it much thought, as I assumed that dom0 was nothing but a privileged PV domU. Did you try a Linux domU as a PV guest?

---

### Post by GizmoChicken on 2013-05-14
> **heiko_s said:**
> I never gave XCP a try as I heard that some things are easier to accomplish while others are more difficult. Once I solved the hardware part (graphics card), I felt that Xen is rather straight forward.

Yep, in many ways, vanilla Xen is much more straight forward.  And so at this point, I'm mostly just experimenting with XCP.  I like the management features provided by XenCenter, especially the ease of configuring GPU passthrough, but aside from that, I don't care much for the "blackbox" nature of XCP.

> **heiko_s said:**
> With regard to the Linux domU VGA passthrough, I suppose you had the  Linux guest configured as HVM guest. I'm wondering how a PV guest would  work, and if it could use the proprietary graphics drivers, just like  dom0? Actually I never gave it much thought, as I assumed that dom0 was  nothing but a privileged PV domU. Did you try a Linux domU as a PV  guest?

Yes, GPU passthrough was to an Ubuntu 12.04 HVM guest.  Although I've created several PV Linux guests in XCP, I've never tried GPU passthrough with any of them.   Based on a [Xen wiki page]("http://wiki.xen.org/wiki/Xen_VGA_Passthrough#Why_can.27t_I_do_VGA_passthrough_to_Xen_PV_.28paravirtual.29_guest.3F"), I was under the impression that GPU passthrough only works with HVM guests.  But maybe my impression is wrong.  When I get a chance, I'll try again.

I was only able to get GPU passthrough working with the Ubuntu 12.04 HVM guest using whatever default version of Catalyst (not the update)  that is found in the Ubuntu 12.04 repository.  Considering that the open source drivers work fine with Ubuntu as dom0, I think it's odd that GPU passthrough does _not_ seem to work with Ubuntu 12.04 HVM guest when using the open source Radeon graphics drivers. 

 Since I hope to get GPU passthrough working with a greater variety of Linux guests (whether with XCP or vanilla Xen), I submitted a "[suggestion]("http://xenorg.uservoice.com/forums/172169-xen-development/suggestions/3950715-gpu-passthrough-to-linux-guests-using-open-source-")" to Xen's new uservoice page requesting that the Xen Project work more closely with the developers of open source video drivers to enable GPU passthrough to Linux guests using open source drivers. See [http://xenorg.uservoice.com/forums/172169-xen-development/suggestions/3950715-gpu-passthrough-to-linux-guests-using-open-source-](http://xenorg.uservoice.com/forums/172169-xen-development/suggestions/3950715-gpu-passthrough-to-linux-guests-using-open-source-)

If you're also interested in  getting GPU passthrough working with a greater variety of Linux guests, I hope that you'll consider adding your vote and comments to my [suggestion]("http://xenorg.uservoice.com/forums/172169-xen-development/suggestions/3950715-gpu-passthrough-to-linux-guests-using-open-source-").

Oh, I found this thread while searching for examples of GPU passthrough using KVM.  If I'm not mistaken, GPU passthrough using KVM will be much easier using [qemu 1.5]("http://wiki.qemu.org/ChangeLog/1.5#Device_assignment") combined with [kernel 3.9](https://bbs.archlinux.org/viewtopic.php?pid=1270712).  Daily builds of [Ubuntu 13.10]("http://cdimage.ubuntu.com/daily-live/current/") (featuring kernel 3.9) are now available.  At present, only qemu 1.4 is available from the Ubuntu 13.10 repository, but hopefully version 1.5 will be available soon.  Once it is, Ubuntu 13.10 would seem to be a good prospect for testing GPU passthrough using KVM.  I like Xen.  But if KVM provides better support for GPU passthough to Linux guests, I'll consider switching to KVM.

---

### Post by heiko_s on 2013-05-14
I didn't mean VGA passthrough with Linux PV guest, but having the PV guest use the driver of dom0 or so. As I said, I never looked into it so it may sound naive.

Regarding kvm, here is a how-to that may be useful: [http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19770787]("http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19770787").

I'm almost always using the proprietary drivers, probably out of a habit when using Nvidia cards. I think the gap between AMD proprietary and open source drivers isn't that big as it is with Nvidia. I still would want the best driver available for my graphic card, as it often makes a big difference. Even if its only the power consumption, i.e. switching the card into low power mode when doing easy stuff. I'll have a look at the link you posted, sounds like a good idea.

So my first wish would be that Nvidia adds support for Xen to their closed source drivers, followed by support for VGA passthrough. They could easily do the latter, in fact I have the feeling they prevent it somehow. Have a look at this link: [http://www.eevblog.com/forum/projects/hacking-nvidia-cards-into-their-professional-counterparts/]("http://www.eevblog.com/forum/projects/hacking-nvidia-cards-into-their-professional-counterparts/"), specifically [here]("http://www.eevblog.com/forum/projects/hacking-nvidia-cards-into-their-professional-counterparts/msg207550/#msg207550"). As you know, the professional Nvidia Quadro etc. cards support VGA passthrough.

---

### Post by GizmoChicken on 2013-05-14
> **heiko_s said:**
> So my first wish would be that Nvidia adds support for Xen to their closed source drivers, followed by support for VGA passthrough. They could easily do the latter, in fact I have the feeling they prevent it somehow.

Yep, I too get the feeling that Nvidia intentionally prevents GPU passthrough.  If so, that's just shameful.  But hopefully open source drivers, although inferior in many ways, would at least allow for reliable GPU passthrough to Linux guests, which is a feature that the proprietary drivers can't currently boast.

Thanks much for the link to the thread discussing GPU passthrough with KVM.  In coming weeks (once qemu 1.5 finds its way into the Ubuntu 13.10 repository), I'll be looking further into the possibility of using KVM as an option for GPU passthrough to Linux guests.

---

### Post by hannes3 on 2013-09-17
Hi,

I'm trying to set up a new machine for hardware compability testing and therefore I'd like to have a host machine for VGA passthrough.

My question is now, if anybody has already tried multiple passthrough with different graphic cards such as Nvidia Quadro fx1800 or Quadro 2000 (Nvidia Multi-OS certified)? And if so, is this only possible with Xen or also with Virtual Box or VMWare?

Ideally I would like to set up a different VM for each different graphics card (planned 4 per host).

Thank you in advance for your help!

---

### Post by sivel27 on 2013-10-04
hello,

i was successful with pci passthrough following [http://http://forums.linuxmint.com/viewtopic.php?t=112013&f=42]("http://http://forums.linuxmint.com/viewtopic.php?t=112013&f=42")
i was banging my head trying to figure out why i was getting error 22 when starting the vm, only to realize the pciback script i had wasnt grabbing the 2nd vga quickly enough.

virtually same fps in games, which is good for my son, since thats the only reason i still use windows.

thanks,
mike

---

### Post by adam-9 on 2014-02-20
Can anyone please confirm that Virtual Box really is capable of VGA Passthrough, as advertized on [manual]("http://www.virtualbox.org/manual/ch09.html#pcipassthrough")?

I heavily use VirtualBox already.

---

### Post by pendulous on 2014-02-22
> **adam-9 said:**
> Can anyone please confirm that Virtual Box really is capable of VGA Passthrough, as advertized on [manual]("http://www.virtualbox.org/manual/ch09.html#pcipassthrough")?

I heavily use VirtualBox already.


Doesn't seem so, it's still experimental.


>              According to the manual this is only supported on Linux hosts:

  [http://www.virtualbox.org/manual/ch09.html#pcipassthrough](http://www.virtualbox.org/manual/ch09.html#pcipassthrough)

  [EDIT - I also confirmed with the VBox dev team. This is not supported (and still experimental even on Linux)]

      



Source:
[http://superuser.com/questions/663837/cannot-setup-pci-passthrough-for-display-adapter-in-virtualbox](http://superuser.com/questions/663837/cannot-setup-pci-passthrough-for-display-adapter-in-virtualbox)
[https://forums.virtualbox.org/viewtopic.php?f=7&t=56568](https://forums.virtualbox.org/viewtopic.php?f=7&t=56568)



I know VMWare supports it. Personally, haven't gotten into HyperV that much, since my systems are still LGA775's, once I obtain Skylake I'm all in.

---

### Post by tuxinteger on 2014-03-19
> **heiko_s said:**
> I can't do away with Windoze, but I hate dual-boot. I also need native (or near-native) graphics support in the Windows VM.

In the end I chose Xen to host Linux and a Windows 7 VM which uses a dedicated graphics card for native graphics performance. It works extremely well, with what I consider top-notch performance that doesn't stand (much) behind a native Windows installation on bare metal.

In fact, I'm so thrilled about it that I wonder why not every dual-booter is switching to virtualization. (I'm actually not that surprised since it was quite challenging to get it working.)

Here my questions:

Has anybody tried VGA passthrough?

If yes, which hypervisor/method did you use (Xen, KVM, VMware, etc.)?

How easy or difficult was it?

In the end I would like to know if there are perhaps better or easier ways to get it working. Thanks in advance for your feedback!

#
Successful with PCI & USB passthrough ,using hd7870 and quadro fx1600,passing through the hd7870 card ,GL & DX 
performance is only 4% less than win8 ,but seems to out perform win7 baremetal.

Not using KVM ,using 2 monitors ,2 kb's & mice,on different usb controllers hubs,seems less troublesome and better perf.

The primary xen monitor switches over to the domu guest on hvm startup,so i still have access to the host ubuntu machine
 on the 2nd monitor ,i prefer this setup to a kvm.

Hardware -Mainboard Asrock ext4 z77,xeon 1200 cpu 4 core -8 threads,xen dom0 working on 2 cores fine.

An ssd would be favourable to increase o/all performance.

I based the HVM method on ubuntu 13.10 ppa of Xen ( 4.3) on the linux mint reference with kernel mode and 
Runlevel pciback script .I found the manual script to pass throug hdevices in RL20 to halt the host if it wasnt loaded
 between runlevel 19&20 -see ref to this in pciback scripts in the linux mint reference in this thread 
[http://forums.linuxmint.com/viewtopic.php?t=112013](http://forums.linuxmint.com/viewtopic.php?t=112013)

The grub loader settings are critical for the machine performance if ram memory is limited ,ie 8gb ,16gb is preferable if 
you plan to use both the host and the guest simultaneously,as compiz can be intensive at times,with 8gb ram i have to
use the lighter desktop to work on the host and guest screens /machines.

Warning : Do not isntall ccc or the whole amd package with ccc into the machine as it will give a nasty bs/od,extract and install
manually !.

Heres my happy grub default ;

GRUB_DEFAULT="Xen 4.3-amd64"
# GRUB_HIDDEN_TIMEOUT="0"
# GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash # took out nomodeset as issues with display on quadro card"
#
GRUB_CMDLINE_LINUX_DEFAULT="radeon.blacklist=1 quiet splash"
# above line prev had "quiet splash intel_iommu=on"
# GRUB_CMDLINE_LINUX="apparmor=0" #took out again poss cause high disk access a 
# testing below issues with disk access and host mem 
# GRUB_CMDLINE_XEN="intel_iommu=on dom0_mem=512M,max:1024M dom0_max_vcpus=2 dom 
# if the below line isnt in the perf is poor on host 
GRUB_CMDLINE_XEN="iommu=1 dom0_max_vcpus=2 dom0_vcpus_pin"


It's great not to have to reboot for win work & i Havent tried w8 as yet. 


Cons ; -No real issues.

 
1- Dom0 doesnt seem to release memory back to the host well after the HVM Domu is shutdown,still working on this as max mem & static mem settings do not help.
2- When using pci passthrough the domain guest cannot be saved.
 
#

---

### Post by heiko_s on 2014-04-14
> **adam-9 said:**
> Can anyone please confirm that Virtual Box really is capable of VGA Passthrough, as advertized on [manual]("http://www.virtualbox.org/manual/ch09.html#pcipassthrough")?

I heavily use VirtualBox already.

I don't think so. AFAIK at the moment only Xen, kvm, and VMware support VGA passthrough.

Sorry for the late reply.

---

### Post by heiko_s on 2014-04-14
@tuxinteger: Thanks for your detailed answer.

> I based the HVM method on ubuntu 13.10 ppa of Xen ( 4.3) on the linux mint reference with kernel mode and
Runlevel pciback script .I found the manual script to pass throug hdevices in RL20 to halt the host if it wasnt loaded
between runlevel 19&20 -see ref to this in pciback scripts in the linux mint reference in this thread
[http://forums.linuxmint.com/viewtopic.php?t=112013](http://forums.linuxmint.com/viewtopic.php?t=112013)
Sorry, I don't follow you here. Can you explain?

By the way, the method of binding the graphics card to pciback has changed - check again the how-to, step 11. Instead of the pciback script it use now:
```
echo "xen-pciback passthrough=1 hide=(02:00.0)(02:00.1)" >> /etc/initramfs-tools/modules
update-initramfs -k all -c
```
for the graphics card (and/or any PCI device that should be bound to pciback during the PC boot process).

---

### Post by heiko_s on 2014-04-20
Some updates from my side. I've successfully tested Ubuntu 14.04 Beta2 with Xen 4.4 and an AMD 6450 card for VGA passthrough (AMD 7770 for dom0) using the xl toolstack.

It looks like Xen 4.4 and the 3.13 kernel have improved things a lot over previous releases, particularly with passing through AMD cards. There has been a issue hunting AMD GPU cards when using the xl toolstack that would either cause performance loss or prevent a reboot of the domU, or even crash the dom0. With Ubuntu 14.04 and Xen 4.4 I wasn't able to reproduce this issue and everything worked as it should.

The xl toolstack still requires the old qemu-xen-traditional as device model version in the domU configuration file, the new qemu-xen (upstream) would allow installation of a Windows guest but not support VGA passthrough.

Some of the software updates on older Ubuntu or Linux Mint releases could break VGA passthrough support when using the xm toolstack - the "error 22" problem, but in this case it seems like a new bug (the old "error 22" bug was fixed long ago). Since xm is deprecated and Xen 4.4 works well with xl, it doesn't make much sense to beat a dead horse.

While Xen and xl worked fine with Ubuntu 14.04, I discovered some nasty bugs in other applications:

1. xtightvncviewer: doesn't allow empty password strings :(. The workaround is to define a 6-8 letter password in the /etc/xen/guest.cfg file.
2. vnc4viewer: It crashes randomly after startup. At some point I couldn't get it to start up at all.
3. Ubuntu 14.04 detects both VGA cards and automatically sets up dual screen, which is not what I want. In addition I had problems installing the proprietary fglrx driver under Xen. To solve problem #1 I removed the second VGA card before installing Ubuntu, and only after I created an initramfs with the (not yet installed) graphics card bound to pciback did I shut down and install the card.
Problem #2 requires shutting down the X server and running a initialisation routine of the AMD driver to set up a configuration file for the screen(s).

More on that [here]("http://ubuntuforums.org/showthread.php?t=2216910").

---

### Post by Nickolai_Leschov on 2014-07-24
I would like to set up VGA passthrough when I will be reinstalling Ubuntu on ThinkPad X200 ([Core 2 Duo SL9400]("http://ark.intel.com/products/36689/Intel-Core2-Duo-Processor-SL9400-6M-Cache-1_86-GHz-1066-MHz-FSB?q=L94") CPU). The machine supports VT-x, but not VT-d. The next model, X201, seems to have the necessary technology in CPUs like [i7-620LM]("http://ark.intel.com/products/43559/Intel-Core-i7-620LM-Processor-4M-Cache-2_00-GHz?q=i7-620LM"). Can I do it or is it a show-stopper?

I thought of using Ubuntu 14.04 64-bit with KVM as dom0 and Ubuntu and Windows as guests.

Does it make sense?

---

### Post by ubeauty on 2014-08-15
For anyone looking through the forums trying to get VGA passthrough tow ork with XEN (I've only worked with vanilla xen 4.4.x & dom0 ubuntu 14.4) my big conclusion is a simple one - VGA passthrough won't work with HVM's allocated over 2GB of RAM but will work with HVM's with less - beautifully.

There appear to be patches and modules that may fix the issue with 4.4, but for me not an acceptable approach for a production machine, so I will wait for XEN 4.5 and hope the memory/vga passthrough issue is resolved by then. 4.5 is expected in December according to this: [http://wiki.xenproject.org/wiki/Xen_Project_Hypervisor_Roadmap/4.5](http://wiki.xenproject.org/wiki/Xen_Project_Hypervisor_Roadmap/4.5)  

Seems like our archlinux brothers are getting some success with compiling xen 4.5 [https://bbs.archlinux.org/viewtopic.php?id=183994](https://bbs.archlinux.org/viewtopic.php?id=183994) and VGA passthrough.

---

### Post by redger on 2014-09-05
I have been using VGA passthrough for the last 5 months or so. Starting with Arch using the instructions here [https://bbs.archlinux.org/viewtopic.php?id=162768]("https://bbs.archlinux.org/viewtopic.php?id=162768") and referene information here [http://vfio.blogspot.com.au/]("http://vfio.blogspot.com.au/")
Then I moved to Ubuntu Trusty and am happily running a variety of guests using KVM - both Ubuntu and Windows 7 guests.
VGA passthrough works, performance is great - I run 3 1080P monitors for gaming on a Windows 7 guest with the following hardware
-CPU Intel 4670 (use the IGP for host graphics)
-Motherboard Asrock Z87-Extreme 6
-RAM 16GB
-GPU AMD HD6950 (used by Windows to drive triple monitors)

-KUbuntu Trusty
-Libvirt / Virt-Manager   (works nicely but requires some reconfiguration, so I created a simple shell program fpr the Windows guest and attached that to the KDE menu, then run Ubuntu guests using Virt-Manager)

Basic steps are to 
-Follow the Grub and VFIO setup as described in the Arch forum.
-Patch the kernel (and update the Config as recommended)
-Allocate the storage (LVM partition in raw format recommended)
-Create the necessary Qemu command (you will need to run this as root)

For host based sound I found the best results are achieved with Alsa rather than Pulse (pulse induced lag which is not good for gaming) BUT the easiest is to purchase a cheap add-in USB card and a cheap USB sound device.

I tried Xen, the earlier versions work but are much slower for gaming than KVM and KVM continues to improve

---

### Post by Germano_Cesari on 2014-10-09
[COLOR=#000000][FONT=Arial]I've** succesfully** set up VGA passthrough with a Quadro 4000 and everything is working great.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]My motherboard is a SuperMicro H8DGi/F with 2x opterons 6140, an onboard Matrox G200 and a discrete Quadro 4000. On guest startup xl complains the Quadro, sound device, usb controller, keyboard and mouse dont support FLR, but keeps on going just fine anyway...[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
Dom0 is Ubuntu server 14.04 LTS with vanilla xen 4.4[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]DomU is HVM win7 Pro x64, NV driver latest quadro[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
I have 2 monitors, one is connected to the Quadro, the other to the onboard G200, Bios have been set to boot from the Matrox G200 and the integrated Matrox is the one I use for Dom0 control.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I had to setup the Quadro as the *primary* adapter, (gfx_passthrough = 1) otherwise the NV driver in win7 would randomly (and pretty easily) crash even after trivial operations like a window resize. If the Quadro is the primary adapter, there is no problem whatsoever.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
The annoying part of having it as the primary adapter is that it boots from the Matrox (and the connected monitor), and keeps on using the onboard Matrox until the windows logo shows up, from that point on it switches to the Quadro.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Keyboard and mouse also are PCI passed-through only *after* the window logo shows up.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]This is not a problem per se, since I dont use more than a single VM at once, it is just annoying because a) Im left with no Dom0 screen, and b) the onboard Matrox is not reset after guest shutdown, so I have to SSH to get control of the system or type without seeing anything.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
Note that the onboard Matrox is never referenced in the guest configuration file, I dont get why xen takes it anyway..[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
Is there a way to avoid switching to the integrated Matrox at first, or at least to reset it somehow? I tried difefrent things (like echo 1 > /sys/bus/pci/devices/*device*/reset) but with no luck..[/FONT][/COLOR]

---

### Post by Germano_Cesari on 2014-10-09
[FONT=Verdana]> **ubeauty said:**
> For anyone looking through the forums trying to get VGA passthrough tow ork with XEN (I've only worked with vanilla xen 4.4.x & dom0 ubuntu 14.4) my big conclusion is a simple one - VGA passthrough won't work with HVM's allocated over 2GB of RAM.

[/FONT]I strongly disagree with your conclusion, VGA passthrough with vanilla xen 4.4 + Dom0 Ubuntu 14.04 is working great for me for a HVM win7 x64 DomU with 4/8 vcpu + 8GB of RAM, see my previous post

---

### Post by hurenkam on 2015-01-15
Almost two years have passed, since my earlier post. Recently I've been experimenting with a more recent kernel & hypervisor (Ubuntu 14.04.1 / Xen 4.4), however I found this to be rather unstable.
Looking a bit beyond Xen, I found several reports of KVM/VFIO being quite stable, and capable of doing proper VGA passthrough, so I thought I'd give that a try.
And I must say, I'm happily surprised, KVM is proving to be even more stable than my previous Xen 4.2 setup, and although I had some drivers behaving weird in one of my VMs, the host is rock stable.

Host:
My hardware is still the same: Intel i7 860, Asus P7P55D Evo main board, Asus EAH4350 silent graphics cards (2x).
One caveat though: I am unable to use the primary graphics card for VGA passthrough using qemu/kvm, it will lock-up the machine. Hence i added another graphics card, so that the 2 4350's can be used in the VMs.
Running a recent Arch linux, with Qemu v2.1.2, kernel 3.17.6-1-ARCH.

VMs (am able to run any two of these in parallel, each passed a graphics card and usb card, the third can run in parallel using vnc):
1) Arch linux runs fine with default opensource radeon driver. No issues installing, virtio-net, virtio-block and balloon is all functioning fine.
2) Windows 8, had some issues getting it to update to recent version, but eventually managed. Upgrading to 8.1 fails, perhaps I need to play with the machine layout to get it to work. Some info on the web seems to suggest i should install catalyst drivers to get it to upgrade properly, i haven't tried that yet. Installed redhat virtio-net, virtio-block and balloon drivers, all seems to work fine.
3) Gave OSX Mavericks a try, and much to my surprise was able to run it (after retrieving the OSK keys from my macbook, and providing it on the command line). To run it with proper radeon, usb & network support requires downloading and installing some kext files. I managed to get almost all devices to work, with the exception of my intel hd audio card.

Would be great if i could use the Primary VGA card as well, Xen was able to pass it through, I'm not sure what's preventing Qemu/KVM from doing so.

---

### Post by hurenkam on 2015-02-17
> **hurenkam said:**
> 
Would be great if i could use the Primary VGA card as well, Xen was able to pass it through, I'm not sure what's preventing Qemu/KVM from doing so.

Managed to get the primary card working too, it requires booting in text-only mode, passing 'nomodeset' and 'nofb' to the linux kernel, blacklisting the radeon driver, and switching grub to use text mode only.

---

### Post by redger on 2015-02-26
I created a new post to describe how to establish a UEFI based Windows VM using KVM
[http://ubuntuforums.org/showthread.php?t=2266916&p=13235279#post13235279]("http://ubuntuforums.org/showthread.php?t=2266916&p=13235279#post13235279")

I've found this to produce the best overall result for me. Easy to manage with the gui, stable, secure and doesn't require any kernel patches (unlike the method I was previously using which required VGA-arbiter and other patches)

Note that (a) the host need not be booted via UEFI and (b) even older AMD graphics cards can be "enhanced" for UEFI boot

---

### Post by jamel-maison on 2015-03-12
Hello everyone,

I've just want to take you aware of my little success to give hopeness to others.

VGA-Passthrough became plug and play with current version of ubuntu and kvm

What I did :
- buying an HP DC7900 with 8 Gb of RAM and E8400 CPU (very low cost dc7800 may works too) and a radeon 5450 1G.
- configuring machine to expose vt-d (activating MEBx in bios, rebooting, Ctrl+P to enter MEBx, configuring vt-d, reboot, activating vt-d in bios, reboot)
- configuring machine to boot on integrated video and graphic card put in in slot2 (4X)
- installing ubuntu 14.04
- installing kvm and virt-manager (and all that come with) from depot
- installing W7_64 in VM in VNC window, stopping it
- modifiying VM in virt-manager to add graphic card and usb device
- booting VM and installing driver
- that all folks. I'd just tried hot pursuite unleashed and very impressive. Rate from windows at 4,1, exactely equal as native windows on this machine.

Rest to make VM work with primary card and in slot 1 (16x). I will change cpu from 2 to 4 cores and try with 16Go RAM. When all will works, I will put VM on SSD to speedup running.

And voila. Next news when I will go ahead.

---

### Post by jamel-maison on 2015-03-12
I forget to mention a tuto that I will follow for next test :
[http://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](http://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)

---

### Post by jamel-maison on 2015-03-17
Hello,

after many unsucessuful try, I'll stay with present config :
DC7900 8GoRAM-250GoHD, integrated video intel, radeon 5450 passingthrough as secondary card. Performance equal native install (windows indice : 4,1/7,9)

to enable vt-d
[http://jaredlxl.blogspot.com/2009/04/enable-amt-on-hp-dc7800-dc7900.html](http://jaredlxl.blogspot.com/2009/04/enable-amt-on-hp-dc7800-dc7900.html)
to configure machine (majority copy-past)
[http://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](http://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)
and of course :
[https://bbs.archlinux.org/viewtopic.php?id=162768](https://bbs.archlinux.org/viewtopic.php?id=162768)

My machine doesn't allow booting on integrated graphic with first slot x16 filled. It is mutually exclusive.

When I try to boot on a second card (ati or nvidia in place of integrated card), I encountered BSOD with radeon passingthrough and a code 43 with nvidia passingthrough. From my reading, error disapeared with qemu 2.2, which I tried. Unfortunally (my fault, I don't know how do properly), it didn't correct and, I was tired to experiment.

I leave card passingthrough in a x16 slot, but it is x4 electrical. Due to limitation of my machine. It is not a gamer pc.

For all, it cost to me 150 euros for HP + 35 euros for radeon. I've just added 2 DVB-S and in one machine, I have 3 (VDR - Windows Game - Linux server and Labs)

I obtained what I want (windows inside linux avoiding reboot with descent performances) and I will stay as is.

May be, I'll try again with more edge device.

Good luck for everyone who will try and I take my hat off to developer and all people involved.

---

### Post by mogliii on 2015-09-24
Hello,

I want to give a short report that I succeeded to get VGA Passthrough working. It was not easy

1. I tried with an Asus **A88X-Pro** and an **A10-7850K APU**. First I tried with an ATI 6570, but could not succeed. IOMMU seemed to separate well (had to use the second pcie16 slot from top). I used OVMF bios. I tried everything but didnt work.

2. I got an **MSI GTX750 Ti Gaming** (as it has UEFI bios), and tried again with passthrough, but I could not resolve the Code 43 problem. Oddly, there was loss of video signal after boot screen. There is a thread in the vfio-user mailing list archive [https://www.redhat.com/archives/vfio-users/2015-September/msg00302.html]("https://www.redhat.com/archives/vfio-users/2015-September/msg00302.html")
I tried different versions of QEMU (up to 2.2), but nothing changed.

3. I got a new motherboard and CPU (**ASRock Z87 Extreme6** and **Intel Core i5 4460**), and just switching the motherboard and adjusting the grub boot parameters, I could boot with passthrough and driver (340.52) worked.

4. I had some laggy mouse issues. As it turns out, this was due to the fact that I was running the VM from an LVM volume on a software Raid1. After moving to its own physical hard drive, the mouse lag is gone and the VM feels like native.

5. For USB, I got a **AREA SD-PEU3V-2E2IL** PCIe1x card with a Via VL800 chip. It seems all USB ports on the Z87 Extreme6 are in the same PCI device, so only all ports can be passed to the VM. First I thought this could resolve my laggy mouse issue. I first tried to pass the USB card to the VM, but there was some serious boot trouble, high CPU load, host instability and the card was not usable in the guest. So now I am passing through the onboard USB controller and using the USB card for the host.

6. I'm now using a KVM switch to switch between host and VM. TightVNC is also installed.

On Unigine Valley Benchmark, I get ~850 points in Ultimat HD setting.

This was very frustrating experience but happy it works now. **But the initial problem was definitely the motherboard/APU.**

---

### Post by zexelon2 on 2015-09-24
Okay, so I have gotten 98% of the way to what I want to achieve with VGA pass through. I have been using the latest Xen 4.5 on Ubuntu 15.04, my hardware is as follows:

CPU: Intel i5 (with Vt-d & Vt-x)
MB: MSI Z97 PC Mate (comes with Vt-d)
RAM: 16Gb DDR3
Video #1: ATI 7970
Video #2: ATI 7870 XT

Guest OS: Windows 7 x64

So far I have two booting installations of Windows 7 x64 with full graphics from the passed through videocards. Linux runs on the IGP provided by the intel chip. The ATI 7970 runs full speed and phenomenally well. 

I am having major issues with the 7870 XT though. Something is screwed up between the drivers and xen for the 7870 XT. After a few minutes of running it corrupts the video memory, initially I thought it might be hardware related but after booting it in a native windows environment and stress testing it with several games, it ran perfectly fine. I then found that the 7870 XT also has the exact same issues with Qemu/KVM the solution there was to dissable hugepage support. I can not figure out how to do this with Ubuntu 15.04 so I just finished re-compiling the kernel to strip out all huge page support, havent been able to test it yet though to see if it worked. 

As this whole experiment is to get a flight simulator working I only needed to pass through the mouse and keyboard to the main VM (the 7970). After that I used an awesome piece of software called [Multiplicity]("http://edgerunner.com/multiplicity") that basically works as a software KVM and auto combines the two VMs as if they were simply an extended desktop (obviously you can not pass windows between them but the mouse and keyboard travel as if they were one and you can drag and drop files seamlessly). It is a paid app but its 19$ for 2 machines... Conversely there is another FOSS one called [Synergy]("http://synergy-project.org/") that claims to do the same thing but across Linux/Win/OSX. I have not tried this one yet, spending to much time trying to fix the corruption issues with the 7870XT. 

So far I have been extremely happy with the performance of Xen, the flexibility of LVM2 and VGA passthrough of the 7970. If my re-compiled kernel does not fix the 7870XT I may just replace that card.

Once I get VM2 stabilized I will be testing the PV drivers for Windows 7. 

On thing I absolutely love right now is thinprovisioning with LVM2, I "goldmaster'ed" my initial install of Windows 7 and now I am able to spawn/test/destroy VMs on a whim! If something works I just update the gold image then. 

Very very happy with the current state of VGA passthrough and Xen. To be honest it has brought me back to Linux after many years of being a disillusioned Linux'ite.

**_Edit:_**

For ease of success stick to Intel hardware for CPU/MB/Ram and discrete ATI hardware for Graphics. I tried doing this several times in the past on laptop hardware, it is almost impossible due to technologies like optimus (from nvidia) really messing with passthrough. I have heard reports of success with Nvidia cards but only the Quadro series. Its odd, Nvidia has the best binary drivers for Linux by far... and the worst VM support... ATI has the worst Linux binary drivers but by far the best VM support.

---

### Post by themainliner2 on 2016-05-24
> **zexelon2 said:**
> For ease of success stick to Intel hardware for CPU/MB/Ram and discrete ATI hardware for Graphics. I tried doing this several times in the past on laptop hardware, it is almost impossible due to technologies like optimus (from nvidia) really messing with passthrough. I have heard reports of success with Nvidia cards but only the Quadro series. Its odd, Nvidia has the best binary drivers for Linux by far... and the worst VM support... ATI has the worst Linux binary drivers but by far the best VM support.
With the greatest of respect have you tried any AMD/Nvidia hardware? The Quadro myth needs putting to bed and I suspect all your Nvidia issues may be wholly laptop related. As for Intel having "by far the best VM support" I can't comment because I've only used AMD/Nvidia.

CPU: AMD FX 8350 Black Edition | AMD Phenom II X4 965 Black Edition
MB: ASUStek Sabertooth 990FX (r1.0)
RAM: 16Gb DDR3
Video #1: Nvidia Geforce 760 | Nvidia Geforce 750Ti
Video #2: Nvidia Geforce 750Ti | Nvidia Geforce 460 768MB

Guest OS: Windows 7 x64 | Windows 10 Enterprise
Host OS: Xubuntu 15:10 & 16:04 | antiX MX-15

I use *Synergy* and can report that it works seamlessly and effortlessly.

There are plenty of great resources on the 'net that can assist you in virtualising with VGA Passthrough using AMD/Nvidia hardware. I got very close to bare metal level performance and I will write up [my method]("http://vacillate.weebly.com/vacillate-blog/kvm-and-vga-passthrough") not because it's my own or very clever (I stand on the shoulders of giants), but in the hope that the way I *explain* the process might prove helpful when used next to others guides.

---

### Post by heiko_s on 2016-09-08
3 1/2 years have gone since I started this thread. I started with Linux Mint 13 (Ubuntu 12.04, I believe), today I'm running Linux Mint 17.3 (Ubuntu 14.04). Back then I ran Xen with the xm toolstack, later I switched to Xen with xl. Since December 2015 I'm running kvm and pass through a Nvidia GTX 970.

Here my observations:

1. Both Xen and kvm are capable contestants, the preference depends on your hardware.
2. Xen has problems with some Nvidia cards, but nowadays one can patch the Nvidia driver inside Windows and the "incompatibility" is a thing of the past.
3. kvm seems to work fine with Nvidia, I had some issues with an AMD card in the past, but probably nothing serious.
4. Given the right hardware, Xen is actually much easier to set-up and configure **for performance**. Out of the box, Xen is better in handling different workloads. There aren't many "performance tweaking" options to begin with, and they are simply not necessary in Xen. No weird or undocumented options in the config file. The fact that Xen xm/xl uses a plain ole clear text config file is a bonus.
5. kvm seems to have gotten the upper hand in compatibility with graphics cards (though to be honest, I haven't tried any newer Xen releases). It's quite easy to set up, especially when using vfio-pci to bind the graphics card at boot (versus the pci-stub method) together with UEFI (and graphics cards with UEFI BIOS).
6. The BIG downside of kvm is its documentation, or the lack of it. Today kvm has zillions of features and options, many of which aren't really documented. Probably because of this, people use virt-manager, a GUI to configure virtual machines. EDIT: Redhat has some detailed documentation [here]("https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Virtualization_Tuning_and_Optimization_Guide/chap-Virtualization_Tuning_Optimization_Guide-Introduction.html"). Unfortunately it's RedHat centric and only covers the virt-manager and libvirt utilities, not qemu. My how-to over at the Linux Mint forum uses a plain bash script to start the VM with the qemu command and options.
7. Talking about qemu: aside from its many options, developers changed some syntax. I haven't found a good documentation yet that gives a comprehensive description.
8. kvm performance: each little qemu command line option can have a huge impact on performance. The only thing that is not influenced by VM boot options is the passed through graphics card - that one seems to perform consistent. On my hardware changing the -machine pc to -machine q35 had a huge impact on drive performance, but also on CPU and general performance. It took me endless trials with different qemu options and system configurations as well over 100 benchmarks to tweak kvm in order to get to the performance level of Xen. In all fairness, others have reported that kvm gave them better performance (compared to Xen) to begin with.
9. I'm still not sure the HV extensions in kvm have any impact on Windows performance, and I need to check if Windows actually is "enlightened" (i.e. uses the HV extensions).
10. I'm currently using kvm. The reason is twofold: kvm allowed me to easily pass through my new Nvidia GTX 970 card (using the -cpu host,kvm=off option), and kvm plays nicely with the graphics card in the host, which means I can have an Nvidia GPU on the host with proprietary drivers, something that has been problematic under Xen (though I've read about a workaround). The installation was the easiest part and went quite smooth, performance tweaking is another story.

[SIZE=5]Conclusion[/SIZE]

kvm is developing rapidly and kvm VGA passthrough has become the hipp thing to do. I do appreciate the hard work of the developers, but I do have a wish:
Get your documentation updated! The easiest way to debug kvm is to improve the documentation of qemu-kvm. Because in all honesty, kvm is littered with undocumented or poorly documented features. Many of the qemu command line options that surface when searching the net have no documentation, or the documentation is so poor that it's literally useless. Even the performance tuning sections within the documentation are often outdated, or simply misleading. The simplest task, for example finding feature lists for different releases, means wading through forum posts, mailing lists, etc.

Potential VGA passthrough candidates: don't give up on Xen. It has a lot going for, and if you have the right hardware, it will probably be easier to get a system running with good performance. I like the way Xen handles CPU resources - it balances nicely between VM(s) and host. As for passing through Nvidia cards (the consumer models), one can patch QEMU to disable PCI snooping, or patch the Nvidia driver under Windows (the latter will void the license to use the driver).

---

### Post by patpro on 2016-10-16
Hi,

I'm going to share my experience with passthrough in general (VGA, USB, Sound). My setup is different from most of yours, because I'm using VMware ESXi 5.5 as my hypervisor. I've made this choice because I'm very comfortable using it (part of my job), and because I need to host a Mac OS X guest.
My hardware is: 
- SuperMicro X10SRA-F
- Intel Core i7-5930K
- 32 GB RAM
- several SSDs and HDDs
- MSI Radeon R9 270X 2GB for Windows 7 pro guest
- MSI Radeon R9 270X 2GB for Ubuntu guest
- ATI Radeon HD 5770 2GB Mac Edition for Mac OS X guest

The motherboard sports 3 USB controllers, so I've dedicated one for each guest. Each USB controller has either 2 or 4 USB ports. Due to ESXi 5.5 limitation, USB 3 ports are seen as USB 2. No big deal for me.
It sports a Realtek HD Audio controller that I've setup to passthrough for Windows guest. Other guests can use a headset plugged in a USB soundcard for sound playback and mic.

This is working great for Mac OS X and Windows. I can use every software I want with full GPU power on Mac OS X and Windows, I can listen to my music form the Windows guest while typing this post on the Mac guest. 

But unfortunately, I can't make the Ubuntu guest use the MSI Radeon R9 270X. I've tried 14 LTS, and 16 LTS, but none will succeed in using the ATI GPU. I've tried FreeBSD/PCBSD/TrueOS too, no success. Both OSes will detect the ATI GPU and properly identify it, but they fail at using it.

You can find more info about my setup here:
[https://www.patpro.net/blog/index.php/2016/08/12/3031-escaping-the-apple-ecosystem-a-view-of-the-setup/](https://www.patpro.net/blog/index.php/2016/08/12/3031-escaping-the-apple-ecosystem-a-view-of-the-setup/)
[https://www.patpro.net/blog/index.php/2016/08/11/3026-escaping-the-apple-ecosystem-part-3/](https://www.patpro.net/blog/index.php/2016/08/11/3026-escaping-the-apple-ecosystem-part-3/)

---

