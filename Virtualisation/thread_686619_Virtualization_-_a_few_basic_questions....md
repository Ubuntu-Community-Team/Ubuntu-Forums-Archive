---
title: "Virtualization - a few basic questions..."
date: 2008-02-03
forum: Virtualisation
---

### Post by perixx on 2008-02-03
> Windows, why not virtualize? 
Due to this forum post, I'm coming up with some questions on virtualisation, maybe you can answer (some)?

- I do have to make a 'virtualized' install of the OS in question, don't I? Will this stay persistent on system? 
- is a virtualized XP (on a native VT-CPU) comparable in terms of speed to a normal installation?
- can I also virtualize on CPU's that don't have native VT support (like sub-AM2 CPU's)? Or will I be left with utterly slow 'soft-virtualization' then?
- will a compromised XP (e.g. virusses/hacked) pose any threat to its host-OS (Linux)?

perixx

---

### Post by fjgaude on 2008-02-03
> **perixx said:**
> Due to this forum post, I'm coming up with some [http://distrowatch.com/yquestions](http://distrowatch.com/yquestions) on virtualisation, maybe you can answer (some)?

- I do have to make a 'virtualized' install of the OS in question, don't I? Will this stay persistent on system? 

VM server goes on the hose; you install the OS that is virtual after installing the VM server. It all stays when you reboot the host.

- is a virtualized XP (on a native VT-CPU) comparable in terms of speed to a normal installation?

My experience with VBox and VMware Server is you get about 50 to 90% of your host speed and quickness. You have to have enough real RAM so that paging doesn't occur. My laptop gets by with 1G; desktop, 2G.

- can I also virtualize on CPU's that don't have native VT support (like sub-AM2 CPU's)? Or will I be left with utterly slow 'soft-virtualization' then?

My earlier AMD box didn't have VT and worked as well as my new one which does have VT.

- will a compromised XP (e.g. virusses/hacked) pose any threat to its host-OS (Linux)?

Short answer, yes.

perixx

Give virtualization a try... I'm completely happy with what I have now.

---

### Post by hyperair on 2008-02-03
- I do have to make a 'virtualized' install of the OS in question, don't I? Will this stay persistent on system?
It will. The virtualized install of the OS will be made on the virtual hard disk belonging to that virtual machine, and is persistent, unless you delete the disk of course. Virtual machines are also able to pause and resume later despite the host restarting. This is done without the guest OS knowing so you can even suspend a LiveCD session in a VM, and completely power off the host.

- is a virtualized XP (on a native VT-CPU) comparable in terms of speed to a normal installation?
My virtualized XP on a CPU without the VT extensions is already comparable to my Windows XP back when I was dual-booting. And I do lots and lots of Photoshopping in my VM.

- can I also virtualize on CPU's that don't have native VT support (like sub-AM2 CPU's)? Or will I be left with utterly slow 'soft-virtualization' then?
Refer to my previous answer. By the way, virtualization without VT support works really well with Virtualbox, but VMWare runs sluggishly for me.

- will a compromised XP (e.g. virusses/hacked) pose any threat to its host-OS (Linux)?
Little if any. Perhaps any shared files that you have between the host and guest may be compromised. Apart from that, nothing much. Either way I keep my VM in a rather sandboxed environment (behind two NATs, Router and Virtualbox NAT), so the risk of it catching a virus is tiny.

---

### Post by perixx on 2008-02-03
Thank you, fjgaude and hyperair, for your answers!

:) ok, I have some more questions! 

- Is a virtualized Windows roughly the same as a Windows in a sandbox? How could it pose a threat to its host - speaks, break out of this box? Only through loopholes in the VM server or also in different ways?

- Can I keep the guest OS from accessing the internet reliably (e.g. to prevent 'phoning home' issues / unintented upgrading)?

- ```
- is a virtualized XP (on a native VT-CPU) comparable in terms of speed to a normal installation?
``` I'm referring to gaming-abilities mainly - would this also apply? 

- Currently, I have an AMD dual-core. Would this qualify as a 'virtual native VT' environment, by dedicating at least one core completely to the guest OS?

perixx

---

### Post by fjgaude on 2008-02-03
If you keep the guest from Internet access, which you can reliably in VMware Server, then you are home free.

The dual-core AMD works fine, if you only use one core. I don't know of a way to dedicate which one. But VMware only can handle one core presently. The next version will have more than one from what I've read on their site: vmware.com.

---

### Post by hyperair on 2008-02-03
No gaming. Absolutely not. Virtual machines currently don't have the 3d capability required for gaming, though I hear there's some preliminary support in Virtualbox in the trunk, the next VMWare Workstation, and Parallels.

- Is a virtualized Windows roughly the same as a Windows in a sandbox? How could it pose a threat to its host - speaks, break out of this box? Only through loopholes in the VM server or also in different ways?
No. It's much better than that. A virtual machine is like an isolated machine of its own. A guest OS CANNOT access the hardware of the host, unless you explicitly allow it to. In VMWare Server, you can by say... sharing the physical disk. Virtualbox doesn't have physical disk sharing support yet if I'm not mistaken. 
EDIT: There are no loopholes which I know of, considering the guest OS usually doesn't even know it's a guest. Any security issues posed by a compromised virtual machine are only there if you have a network interface connected directly to the host (Host only/Bridged networking), and even then the threat posed is akin to that of a compromised computer in your LAN.

- Can I keep the guest OS from accessing the internet reliably (e.g. to prevent 'phoning home' issues / unintented upgrading)?
Yes. Definitely. All virtualization products which I know of (Qemu, KQemu, Virtualbox, VMWare) can prevent internet access. In fact the question is more of "Can I allow internet access?" because virtual machines being virtual machines, they need virtual network devices in order to connect to the internet. If not implemented, then they cannot connect. So in this context, leave the network devices unconfigured and it pretty much doesn't have a network device and hence cannot connect to the Internet. It becomes pretty much like an isolated machine which isn't even connected to a single network.

---

### Post by perixx on 2008-02-03
Ah, well... so no core-distribution by now. 
An off-topic question here - is it possible to switch of one core via a kernel-switch at boot? A person told me to use 'nosmp' in menu.lst, but that only resulted in errors and a freezing splash screen...

Would you say that VMware (which is commercial, isn't it?) and Virtualbox are on par with each other? Because I'd prefer to use open source software...
And does Virtualbox also have virtual network devices? I've met a guy here that had serious needs for using IE for some sites - maybe this would be a good solution for him!

perixx

---

### Post by hyperair on 2008-02-04
I have no idea how to switch off a core, sorry. I've only got one core so I've never been able to experiment.

VMWare and Virtualbox each have several flavours. VMWare is divided into three: VMWare player, VMWare Server, VMWare Workstation. VMWare Player is crippleware, but open source and free. VMWare Server is freeware, but not open source. VMWare Workstation is neither freeware nor open source, so you need to pay to use it.

Virtualbox is divided into two: The full version and the Open-Source Edition. I've never tried the OSE, but from what I know, OSE has a few less features from the full version, such as USB support and remote RDP. The full version is freeware, not open source, and the OSE is, well, open source. 

Comparison of performance: On my computer, Virtualbox (with all guest additions installed) works at a speed comparative to Windows XP when dual-booting on my computer, and switching from desktop to desktop works without lag. CPU usage is as said above. VMWare Server (with all guest additions installed) however, works so sluggishly on my computer that both the Host and the Guest are affected. The CPU usage is at a constant 80% and above.

Comparison, feature-wise: I believe both Virtualbox (full) and VMWare Server are on par in terms of configuration. Both have their pros and cons. For example, VMWare Server's configuration of bridged networking and host-only networking is very easy compared to Virtualbox's. However, Virtualbox has the feature to pause the virtual machine temporarily without unloading the RAM, so you can pause and resume it very easily, whereas in VMWare server, pausing is akin to suspending the virtual machine, unloading the RAM and storing it on the disk and so on. As you can imagine, it takes a considerable amount of time to pause the VM in VMware Server. Virtualbox has both the pause-without-unloading-RAM feature and the suspending VM feature (pause, unload RAM so it can resume on a later date (and powerup session). Virtualbox also has Remote RDP and USB-over-RDP features, as well as shared folders, all of which VMWare doesn't have.

---

### Post by perixx on 2008-02-04
Thank you hyperair, for that profound feature comparison! I suppose that Virtualbox will be a good choice for me to try out...

perixx

---

