---
title: "Which VM Software is easiest to install and use on Ubuntu Server 14.04 LTS?"
date: 2014-11-29
forum: Server Platforms
---

### Post by PartisanEntity on 2014-11-29
Hi all,

I have Ubuntu Server 14.04 LTS running on a laptop at home, I am currently using it as a home NAS and Webserver.

I would like to install Win 7 as a vritual machine on my Ubuntu Server. I have no experience with VMs on Linux.

What's the easiest VM system to use that's compatible with Ubuntu Server?

Thanks!

---

### Post by sammiev on 2014-11-29
I can not speak for servers but have used both VM's ( VMware and VMbox ) and prefer VMware myself for speed. Both worked well.

---

### Post by PartisanEntity on 2014-11-29
I just installed VirtualBox. Was relatively easy and hassle free. Installing my first vm-based OS right now. Thanks for the feedback :)

---

### Post by nerdtron on 2014-11-30
If it's a server and no GUI. Better use KVM and use Ubuntu virt-manager for managing the VMs remotely.

---

### Post by Doug S on 2014-11-30
> **nerdtron said:**
> If it's a server and no GUI. Better use KVM+1 on that recommendation. And I have only ever used [the Ubuntu Serverguide]("https://help.ubuntu.com/lts/serverguide/libvirt.html") as a reference > **nerdtron said:**
> and use Ubuntu virt-manager for managing the VMs remotely.-1 one that recommendation. I have had difficulty making virt-manager work. In the end, I don't, and haven't, used it.

---

### Post by nerdtron on 2014-11-30
> **Doug S said:**
>  -1 one that recommendation. I have had difficulty making virt-manager work. In the end, I don't, and haven't, used it.

That is sad to here as I only manage all VMs using it. The only commands I know for vm management are the simple ones, virsh list, virsh start, and virsh console.

---

### Post by MAFoElffen on 2014-11-30
> **nerdtron said:**
> That is sad to here as I only manage all VMs using it. The only commands I know for vm management are the simple ones, virsh list, virsh start, and virsh console.
+1

I have KVM host servers. Many guests installed on each. I used to use virt command line tools... but then I installed virtual manager on two of my admin console desktops to install and manage guests. So much easier and faster. I can still use both methods, but a lot of things are still just easier and faster from that tool.

Whatever you do, you just need to learn to use those tools. I have a mixed environment here. Do a lot of testing and am back in school, so-- on other's VirtualBox, VMWare, HyperV, Xen... But my main personal preference on servers is still KVM. I did my MS Server cert training last year, doing my homework w/ MS Server guests running in KVM...

---

### Post by PartisanEntity on 2014-11-30
Thanks for the tips guys, I have no experience with KVM, but since it has received good recommendations from you all I will definitely try it out.

---

### Post by brubaker2 on 2014-12-04
VirtualBox with virtualboxPHP.  For basic stuff it runs win7 fine.

---

### Post by TheFu on 2014-12-05
> **PartisanEntity said:**
> Thanks for the tips guys, I have no experience with KVM, but since it has received good recommendations from you all I will definitely try it out.

Throw my hat in with the KVM + virt-manager group.  I've run Xen, virtualbox, ESX, ESXi, VMware Player, VMware Server, VMware Workstation over the years.  For servers, use KVM+virt-manager.  For desktop on desktop, use virtualbox, but be certain you understand the license for each part of virtualbox - the guest additions have a specific license that people seem to forget isn't NOT F/LOSS.

I've also been playing with LXC and Docker recently - wouldn't use those for any production stuff yet.

Stopped using all the other VM options in that list above a few years ago - only KVM used in production here now for a number of reasons which I've outlined in these forums over the years - check out the virtualization sub-forum for those.

If you google "jdpfu kvm virt-manager" - a presentation I did last spring to setup KVM and virt-manager should come up.  The key difference that seems to stump most people is the manual creation of a Linux bridge for VM use - unlike the auto-created bridge for virtualbox.  I've found the automatic bridge made when KVM is installed to be less-than-solid - don't know why.  OTOH, the manually created bridge is 100% solid and has been for about 4 yrs.  KVM is what OpenStack uses by default, so if you have any desire to move in that direction, it makes sense to learn it on a simple config first.  Best of all, running kvm + virt-manager means never needing to use root to manage the VMs.  Just your normal userid is needed and having it added to a few std UNIX groups.

If this all seems to hard and you can dedicate the hardware as a VM host, many people are happy with the kvm/openvz option provided by Proxmox. I'd rather see that used for servers than anything from vmware or oracle. Call it a burn-me-once thing.

---

### Post by Rick St. George on 2014-12-09
Could you please explain your statement - "the guest additions, in virtualbox, have a specific license that people seem to forget isn't NOT F/LOSS"?

Thanks!

---

### Post by TheFu on 2014-12-09
> **Rick St. George said:**
> Could you please explain your statement - "the guest additions, in virtualbox, have a specific license that people seem to forget isn't NOT F/LOSS"?

Thanks!

Should be: "is not F/LOSS"

Bad wording above. Sorry - 
[https://www.virtualbox.org/wiki/VirtualBox_PUEL](https://www.virtualbox.org/wiki/VirtualBox_PUEL) Section 2, paragraph 2.

Of course, you can use virtualbox without the guest additions and there are times when that makes sense, but if you are doing that - use KVM.
Virtualbox should be used for desktop-on-desktop virtualization or playing with VMs, not for production and NOT for servers, IMHO.

---

### Post by newbie-user on 2014-12-10
I'm happy with Proxmox. Very straight-forward installation, web client (unlike those Windows only clients for VMware, Xen, etc.), and it does both containers and VMs.

---

### Post by TheFu on 2014-12-10
> **newbie-user said:**
> I'm happy with Proxmox. Very straight-forward installation, web client (unlike those Windows only clients for VMware, Xen, etc.), and it does both containers and VMs.

Only VMware/ESXi had Windows-only management. All the others support Linux or ssh-based management. I've heard that VMware ESXi has changed and doesn't require Windows for management (vsphere) anymore too.

Any of the libvirt compatible hypervisors can be managed easily these days from multiple clients or through a web interface (if you are a glutton for punishment and don't care about security, IMHO).  Libvirt can manage LXC containers too - it just doesn't create them.  Since 14.04, making lxc containers is trivial.

Perhaps my proxmox data is old? Nothing against proxmox - well - except doesn't it require dedicating the entire system just for it? Just want to share all the options.  KVM and lxc will happily work on a desktop OS or pure server and do not need to be the only thing installed and running on the system.

---

