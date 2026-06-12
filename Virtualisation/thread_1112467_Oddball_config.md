---
title: "Oddball config"
date: 2009-03-31
forum: Virtualisation
---

### Post by freakalad on 2009-03-31
Hi guys,

Been digging around a bit (i.e. homework), and have sorta finalised on a solution, but I'd like to get your valued input before committing on a solution.

I've bought myself a pretty hard-core machine (low-end of a high-scale) & want to set it up in a particular manner.
* Multi 64-bit Intel-VT PCU; upgradable
* 4GB RAM; many slots still available
* 120 GB SATA HDD; many slots still available, so I'll add some RAID's later
* High-end video with VGA, DVI, HDMI & s-video out
* Surround-sound
* Multi PCI/PCI-express slots open
* multiple NIC's
* Multiple DVD-RW's
* USB IR-receiver; bruetooth to come
* considering TV-tuner/satellite card; may a VoIP board too (sangoma?)
* have PC monitor & LARGE Sony Bravia TV as my monitor :popcorn:

As it stands, this is a very decent gaming/video-edit/dev machine, and I'd like to continue using the hardware set

What I'm having trouble with is the details of the setup.
I'd like my KVM clients to be pretty hi-performance, as I'd like to:
* leverage my 3D card (well, I've forked out the cash for the card; might as well use it) for an immersive 3D OS environment, possibly compiz
* play games on a windoze VM (this is as close Is I'd comfortably like to get to that OS)
* have my media centre in a separate VM (more on this below); maybe with it's video output mapped to the HDMI interface (HDMI A/V is currently working fine)
* VoIP (maybe FreeSwitch in pfSense), but more on this later

Once I can get the system working satisfactory, I can scale hardware accordingly.

On the media front, I've looked at a few candidates, but performance & lag is just absolutely terrible:
* MythBuntu (of course)
* LinuxMCE (yea, I know this is more home automation than media-cen, but that's why it's in a VM - testing options)
* XBMC
* GeekBox
* Elisa
The best performance I've gotten thus far was from a stock-standard live distro & running Totem/VLC/some-standard-media-player from it.
Looking at making use of the ubuntu-MID interface for the BIG screen; to make it more IR/controller friendly.

So there you have it, though some of these notions seem counter-intuitive.
Want to build a host that'll provide best performance (i.e. as close to realtime as possible) to it's clients, quite possibly a (3D) graphical interface with some clients mapped to specific interfaces (media centre to my TV & controlled using IR), so direct hardware access for clients would be a big benefit

Thinking of an Ubuntu (this is what I know best), Debian (closely related), or Fedora (due to it's native KVM implementation & admin tools like oVirt; resource allocation it a boon too) base, and then loading my clients dynamically & assigning resources as needed. Ideally I'd like to remain in the .deb universe

I know this is a tall order, so any suggestion that'll help me finalise on a decision would be greatly appreciated

Thanks

- J

---

### Post by bodhi.zazen on 2009-03-31
Well the problem, I think, is you do not fully understand virtualization.

A virtualized OS does not directly access your hardware. High end graphics / 3d is in "Beta" although I think it is in pre-alpha as it basically does not work.

I have had better success with audio, although there may be some lag there as well.

I suggest Proxmox, although that is more server oriented.

With that in mind, what are you wanting exactly ?

---

### Post by azredwing on 2009-03-31
If you're looking for a full Windows experience via VM, you shouldn't be. It hasn't come that far yet. I barely got Silverlight running in time for March Madness in the last couple weeks, and gaming is terrible. 3D rendering is [hit or miss]("http://ubuntuforums.org/showthread.php?t=1111832") depending on your VM environment, and from what I can tell your graphics card isn't doing a whole lot of rendering.

That said, if you're looking to replicate a full Windows media center using a VM, good luck. The VM adds another layer between your hardware and the guest OS's software, so you'll never see truly native performance for graphics or CPU-intensive applications.

If you want to try, I'd suggest VMware Workstation, depending on your personal free-vs-non-free philosophy. 3D rendering there is good (see above), and I have been able to live-stream video in HD with no artifacts. I haven't had either with, say, VirtualBox.

On another note, make sure you keep the location of your VMs separate from your main HD, i.e., don't run the VMs on the same drive as your / directory. You don't want the guest OS competing with the host for resources from the same drive.

---

### Post by freakalad on 2009-03-31
Thanks for the replies, guys. This is exactly the sort of info I'm looking for.

I've been getting to grips with Paravirtualization (Xen/XenSource?) vs Full-VM (KVM, Virtualbox). 
There's a lot of these terms flying around (like HyperVisor, etc), and it can be pretty tricky sifting through them all

If I understand it correctly (and please feel free to correct me here if I'm off), is that Para is an entire NEW kernel for the host, and the clients have to be modified to take advantage of these features. Full VM is an application layer between the host OS/Hardware & the clients, and does not require a modified OS.
It's a balance between performance & stability/compatibility.

Since I'll be doing extensive testing of various systems, I'll have to run them un-modded, and therefore I'm (sort of) settled on KVM, since this seems to be becoming the de-facto VM platform for both Ubuntu & RedHat/Fedra.

bodhi.zazen : ProxMox was IDEALLY what I was looking for, a Debian based base-bones custom-VM hosting system with web-admin, but I had HEAPS of hassles trying to install, with no luck (first it couldn't find the CD I was booting off, I was unable to create a USB install candidate, and when I finally managed to boot using an external USB CDROM, was unable to locate my /dev/sda & quit). I may have to do it the hard way: install Etch & manually install the ProxMox kernel (something I'm NOT looking forward to)
If only I could get it to work, I'd then be able to pimp the host.

azredwing : I'll look into that a bit more. Once I've got something stable, I'll acquire mode HDD's & base my VM's on LVM's physically separate from my OS & host environment. 
I had a look at VMWare, and it really IS a fantastic piece of work, but I'm making a concious effort to try & make extensive use of FOSS. KVM also had the great ability to base the client/guest OS on a partition, so that's great for stuff like data recovery or bringing back a shelved server without having to rebuild the hardware (the free version of VMWare does not support this). But VMWare's network, hardware & resource management is fantastic. The seamless web-based user interface is also pretty awesome

On the 3D front, I was contemplating [VMGL]("http://www.linux-kvm.org/page/HOWTO_VMGL") to allow clients 3D video. Hope I'm doing this the right way round...

But I think this is on the right track, and I have a feeling that more users may start using systems in a similar manner; instead of having a monolithic system, have a server comprising of several smaller & fairly independent services. That way if one system croaks (like a win or media system), it won't affect the others.

Thanks for the links & advise & please keep 'em coming

---

### Post by freakalad on 2009-04-01
Been digging a bit more, and I'm seeing something that's a little bit odd.

KVM is technology developed by [QumraNet]("http://www.qumranet.com"), which was acquired by RedHat in September 2008, indicating RH's commitment to the project insofar that they're actually integrating it into their kernel.
QumraNet had a product available, namely [Solid ICE]("http://www.qumranet.com/products-and-solutions") (download unavailable), which is an "integrated desktop virtualization environment" (i.e. terminal services VM host), which is pretty close to what I'm looking for, as some functionality of it seems to have been rolled into [oVirt]("http://ovirt.org/").

So by all accounts, it seems that RedHat had adopted KVM in a big way, at the expense of Xen. But some of the cooler RH toys have yet to be ported.

I also had a look at some other technologies, such as [OpenNebula]("http://www.opennebula.org") & [Eucalyptus]("http://eucalyptus.cs.ucsb.edu/"), due to be integrated into the Jaunty release, so I'll have to wait until then to see what it's all about, though I suspect his is more to do with the back-end than exactly what I'm looking for.

At present, my options don't look to promising:
* VMWare: EXCELLENT product, but not FOSS (I'm making a concious effort here)
* RedHat/Fedora: I can, but I'd rather stick to the deb's; it's what I know best (Ubuntu's treated me well thus far)
* Proxmox: Debian-based (Etch), but unable to install, so I may have to install Etch & compile on top, which I'm not exactly too eager to do

Anyway, enough info for now. Will add more info as I find it.
Any comments & suggestion welcome.

- J

---

### Post by freakalad on 2009-04-04
Still reading...

Still really have very few options. 

VirtualBox offers virtualized 3D hardware, but not my cup of tea.
Xen/XenSource/XenServer offers direct hardware access via paravirtualization, but requires modified client kernels, so may not suit my needs, as I'll be testing numerous platforms.
VMWare offers best hope of 3D Hardware Acceleration, but not to disks/partitions, and not FOSS, so trying to avoid it.

KVM seems by all account to be the de-facto VM for Ubuntu & RedHat, so want to slug it out here.

Seems that the VMGL project has run dead a while back, so there doesn't seem to be much solutions available out there for the moment.

errrrr.....seems a good criteria is one posed earlier; gaming or video-editing within VM client

- J

---

### Post by freakalad on 2009-04-18
Been looking more into block-level devices or block devices, in an attempt to pass hardware-level access control through to respective clients.

A quick google search doesn't yield a lot of info, other than info already on the [linux-KVM site]("http://www.linux-kvm.org/page/Paravirtualized_block_device") by virtue of virtio_blk or virtio-blk

Looking at passing other devices (PCI, USB) directly to clients, or as close as I can, such as IR, USB mixer, keyboard, mouse, and any other legacy devices I've got around.

Another brain-fart I had was to create a multi-headed system on a single box:
The video card I'm using has 3 video-outs: VGA, DVI & HDMA
If I can create 2 or 3 GUI VM clients, map each to, say, a TTY terminal (<ctrl><alt><F1> to <F3>), and bind each, along with a corresponding keyboard/mouse pair, to a video-out, I can have like a 3-in-1 system.

Use may not be immediately clear, but this would be SERIOUSLY cool application for, say, an office, home or net-cafe scenario. Pooling some resources (networking & security, memory-management, power-savings, disk storage, static OS areas, etc)

Any ideas?

---

### Post by bodhi.zazen on 2009-04-18
X can do this with out all that fancy binding stuff ;)

See these threads (you should be able to use the information to adapt it to your situation, basically ssh into your VM and forward X to a new session).

[How-to run Multiple (Virtual) X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=271674") 

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948")

---

### Post by freakalad on 2009-04-19
Hi bodhi.zazen,

Thanks for that great info; I was thinking along similar lines.

I posted [this thread]("http://ubuntuforums.org/showthread.php?t=1129631") relating to "multiseat" X configurations.
SOLUTION found:
[http://wpkg.org/Configuring_multiseat_X_workstation](http://wpkg.org/Configuring_multiseat_X_workstation)
[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

Once I have a working, stable solution, I'll look at establishing remote-X sessions to my VM clients.

3D hardware acceleration is still an issue, but at least we're getting there.
Unfortunately I've COMPLETELY cooked the X on my host (again!), so I may only have a working solution after the Jaunty release later this week :p

Been looking a bit closer at the virtualized block devices, as listed in *lsusb* & *lspci*, and I see little reason I cannot pass those through to my clients in a similar manner as [described here]("http://www.linux-kvm.com/content/virt-manager-and-usb-device-support").
Such direct control not be available yet, but may be feasible in future.

---

