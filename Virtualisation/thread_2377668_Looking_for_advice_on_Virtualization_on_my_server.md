---
title: "Looking for advice on Virtualization on my server"
date: 2017-11-15
forum: Virtualisation
---

### Post by krj7709 on 2017-11-15
Calling on all experts with the right advice :)  Okay. I recently bought a server and would like to USE it, meaning that I don't want to run just a single OS on it that uses like 2% of the resources avail... I'v tried Vmware's ESXi/vSphere/vCenter suite on it however this server is no longer supported anymore. It ran okay but some stuff was funky. Plus I would have to reinstall every 60 days because I'm not rich and don't want to spend that kind of money for a homelab. I now have Ubuntu 17.04 running on it but before I get to doing anything with it I wanted to see what options I have and hear whatever anyone may have to offer. Okay, now on to what I would like to do.

Basically I got this server for one purpose. To run a Media Server (PMS). But running the server with ubuntu and PMS didn't hardly tax the hardware at all. So I want to set up a VM Host (Bare metal). The server fully supports virtualization. I will be running 2 permanent VM's, PMS and a Router/Firewall. Of course I plan on playing with other temporary VM's to learn different variants of linux or what have you.

Server Specs


[LIST]
[*]2x Intel Xeon 5645's (12 cores/24 threads total)
[*]36GB RAM
[*]GFX: Onboard ES1000
[*]GFX Addon: 2x Nvidia NVS 300's (These are mainly for being able to run half-way decent desktop envirs - If they don't work very well I will probably grab a couple Quadro 2000's)
[*]4 Network Interfaces: NetXtreme II BCM5709 Gigabit Ethernet
[*]If you want to know some more detailed specs you can google it! (Proliant DL380 G6) <<<< Yeah, I know! But hey, $50 bucks and free shipping.
[/LIST]

I would like to run this as a headless server stuffed away in a closet somewhere. It is silent as hell, that is until you add the 2 video cards. With that said, I want to be able to have 3d acceleration and sound passed through to the VM's. Server does not have a sound card of its own but after installing the NVS 300's I see (lshw) shows the nvidia sound. But virtual soundcard will be fine too. 


[LIST=1]
[*]What OS? Why? I like ubuntu because for the most part its easy to work with.
[*]What virtualization Visor? Why?
[LIST]
[*]What management software?
[LIST]
[*]Something like VMwares vSphere client or vCenter would be nice.
[*]Something with decent Network mgmt?
[/LIST]
[/LIST]

[*]What software to use to run/use the VM's? (Remember, looking to have 3d acc. something like vm workstation's 3d acc.)
[*]What Firewall distro to use? It'll probably come down to pfSense or OPNsense, which do you prefer? Why?
[/LIST]

I guess that is all I got for questions atm.

Extra note on my plans. The Firewall VM is not only going to wall off the VM's but my entire home network. I tried passing through some of my NIC's when I first tried qemu/kvm however they were only running at 100Mbits. (Maybe it was pfSense that didn't have right driver or set the speed wrong?)

---

### Post by TheFu on 2017-11-17
You are going to learn a bunch.  Much of what you want isn't going to be point-n-click.  I don't know how to accomplish **any** of the graphics stuff. That is non-trivial and highly hardware dependent.  Old server hardware probably cannot do GPU passthru, so if that is mandatory, do your research first before wasting money.

I would never run a WAN-facing router inside a VM.  Don't.  Just don't.  Very poor security practice.  VMs aren't as secure as people claim.  For a LAN-router, using a VM is something that I do, but NEVER for a WAN router.  I use pfSense for both WAN and LAN routing. The WAN router runs on a dedicated device, APU2.

I use KVM+qemu+libvirt. Ran Xen for 3 yrs, never regret switching.  Also ran ESX for 5 yrs, never regret switching to KVM.  Usually, I'll create the VMs using virt-manager, but if I was spinning up VMs over and over and over, then I'd look into some automation.  I bring up a new VM about once a month.  After the initial installation, I don't use virt-manager again except in emergencies where a console is required.  ssh is how I manage all the systems here, VMs included.

Network management can mean all sorts of things. Having been burned with any GUI tools, I do it all via config files.

$50 seems like a deal, but only if you are deaf and don't pay the power costs.  For your needs, a $100 current gen CPU would easily handle it all and be 65W or less. That means less noise, less power, less heat.  I've been retiring old power-sucking systems for standard desktops.  It is amazing what a $50 (4 yr old) G3258 can do.  There is a good reason to play with server hardware, I've just never had to touch it myself the last 15+ yrs.  There are data center people for that.  They put in a DVD/USB flash drive.  I remote in over a console switch or IPMI connection and can do whatever.  No need to *touch* the machines anymore.  Of course, these remote console devices are a huge security issue, so they need to only be run on a locked down subnet that only admin machines can reach.

VMs don't care what the physical hardware is.  Always use virtio for network and disk controllers to VMs, unless the guestOS doesn't support it.  Then use PRO/1000 (e1000) and SATA emulation.  If you require HW passthru, things get harder.  It is a useful skill to passthru NICs and storage controllers, sometimes.  But VM performance is really excellent using virtIO devices.  Network bridges can be a security consideration, BTW.

For a remote desktop, there are a few choices for graphics that will definitely work.  SPICE with the QXL driver loaded on the guest where security isn't important and/or x2go for internet-based access.  x2go is based on NX and uses ssh tunnels. It feels 2-3x faster than VNC or RDP connections which aren't secure w/o a VPN.  I don't expect x2go to work with wayland, but haven't tested it.

If you run a server, stay on an LTS release.

---

### Post by KillerKelvUK on 2017-11-17
Pretty much what @TheFU said.  

Regards the GFX stuff, if you weren't running this headless and for example wanted a gaming rig as a VM then you'd need to ensure your CPU and board supports vt-d and enable these options (iommu) via alternations to grubs boot defaults, then depending on the CPU variant you might need to do some kernel patching to get true IOMMU separation of your pci devices to allow physical device assignments.  However you've said you want this headless so I'm not really seeing the point of all this hassle as remote access to a full GFX desktop gets you no where for gaming.

I'm a big fan on KVM and run this on a 17.04 host (server variant) but then I drop a KDE desktop on my host for day to day stuff and when I need a M$ desktop I just use a kvm+qemu vm and configure it with a virtual QXL adapter and SPICE for remote access, this is perfectly performant on a local network (I spend lots of hours in this configuration).  Like @TheFu, I use virt-manager for a quick and simple GUI for spinning up a VM that I don't need to customise but this app is pretty limited when compared to the customisation's you can achieve at the command line...no way to avoid it and no reason to either!  Why; well Ubuntu, KVM and getting into virt this way I found simple, well supported and well documented in the main, Xen isn't native within Ubuntu but I suspect its integrations are improving over time however I didn't get very far with it once I hit a host hardware issue.  PCI passthrough is more niche so be prepared to do your homework and hit road blocks but the more standard stuff is open-book.

Regards the networking aspects you could also look at SR-IOV for effective assignment of the device per VM, again your physical hardware needs to present a certain set of capabilities to allow your host and KVM to exploit this functionality, I've less experience here as don't have a compatible card to test with.  So with both GFX passthrough and SR-IOV you'll want to research VFIO which is a feature set supported by KVM+qemu+libvirt.

Slight variation to your request, don't discount containers for you linux guest.  I've recently migrated away from a KVM guest to an LXD contain for several web apps and the speed improvements are significant (LXD have seriously less latency than KVM).

---

