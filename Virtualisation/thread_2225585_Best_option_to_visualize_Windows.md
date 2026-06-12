---
title: "Best option to visualize Windows?"
date: 2014-05-22
forum: Virtualisation
---

### Post by jackyDon on 2014-05-22
I've already tried vmware player, which runs (especially games) pretty well - and it's generally faster than Virtualbox

But I'm also looking into running windows completely headless.


is there any option for that? since vmware player doesn't allow headless virtualization

---

### Post by tripp98 on 2014-05-24
Check out proxmox.com 
Gui to set things up.  Makes it easy.

---

### Post by KillerKelvUK on 2014-05-26
Ubuntu Server with KVM, use SPICE for remote server/client display+audio although I doubt this would be robust for game play, installation is a doddle, just select "VM Virtual Host" as one of the package options when installing Ubuntu Server.  Post install on your server your client can then be either Windows or Linux i.e. SSH from both works fine and the SPICE tools are available for Windows.  If your client is linux you can use Virt-Manager over SSH to control the VM host and install the guest OS, I use a package called remote-viewer to access my Win7 guest using Spice and the quality is really good.

If you're new to linux the steps can take a little getting used too but overall I find linux very powerful and the community support is excellent IMO.

I've tried Proxmox in the past, whilst it does what it says on the tin if your only requirement is for personal/home use I'd suggest Ubuntu Server 14.04 with KVM using Virt-Manager is a simple well supported route.

---

### Post by TheFu on 2014-05-26
Running any OS headless has lots of options.
* KVM
* Xen
* Qemu
* ESXi
* VirtualBox
* probably others.

Then there are the 'all-in-1' solutions like proxmox - which is a fine solution that provides a web-gui over the VMs.
If you need to have hundreds-to-thousands of physical servers, then openstack needs to be on the list.
For server-on-server virtualization, KVM is my choice with great stability and low price. For a small number of servers, this is an easy choice.  KVM + libvirt + virt-manager for management and whatever remote access you like (ssh / FreeNX).

I haven't a clue about trying to run games - don't do it.  Have been running my daily desktop inside a KVM VM for about 2 yrs happily and a number of other "servers" inside KVM for longer than that. I've used ESXi, VirtualBox, Xen previously. Each as pros/cons. My blog has articles about those experiences (most are not current anymore). 

I wouldn't use Xen on a Debian/Ubuntu host based on my own experience with kernel compatibility. Nothing is worse than patching a bunch of VMs and the hostOS only to reboot and see the hostOS refuse to boot.  That happened too many times with Xen.

So - you have many options to consider.

---

