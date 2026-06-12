---
title: "Building a new KVM box"
date: 2014-09-05
forum: Virtualisation
---

### Post by satimis on 2014-09-05
Hi all,

I'm prepared to migrate my VirtualBox to KVM on Ubuntu 14.04

I found following documents;

1) KVM installation
Install a KVM host on Ubuntu 14.04 Trusty Tahr 9
[http://www.rivy.org/2014/04/install-a-kvm-host-on-ubuntu-14-04-trusty-tahr/](http://www.rivy.org/2014/04/install-a-kvm-host-on-ubuntu-14-04-trusty-tahr/)

HowTo Install KVM and OpenVSwitch in Ubuntu 14.04
[http://blog.ngineered.co.uk/2014/05/16/howto-install-kvm-and-openvswitch-in-ubuntu-14-04/](http://blog.ngineered.co.uk/2014/05/16/howto-install-kvm-and-openvswitch-in-ubuntu-14-04/)

2) Migration:-
How To Migrate from VirtualBox to KVM on Ubuntu 11.04 (NattyNarwhal)
[http://arjunstechblog.blogspot.hk/2011/06/how-to-migrate-from-virtualbox-to-kvm.html](http://arjunstechblog.blogspot.hk/2011/06/how-to-migrate-from-virtualbox-to-kvm.html)


Please advise;
A1)
1) above:-
Is there a newer document for me to follow?

A2)
Open vSwitch is completely new to me.  Just read it briefly on Internet.

Connecting containers on several hosts with Open vSwitch
[http://s3hh.wordpress.com/2012/05/28/connecting-containers-on-several-hosts-with-open-vswitch/](http://s3hh.wordpress.com/2012/05/28/connecting-containers-on-several-hosts-with-open-vswitch/)

Whether it can connect hosts on another PC via Intranet?  I have 2 PCs, PC1 running VirtualBox and PC2 this new box which I'm prepared to build.

B)
Migration
I suppose the steps will be similar for LVM partition?

Is there a newer document to follow?


Thanks in advice.

Regards
satimis

---

### Post by KillerKelvUK on 2014-09-05
Hey, couple of pointers...

1) I struggled to find an all encompassing guide to setting up KVM, eventually I settled with combining steps and considerations from various posts/threads as well as some direct feedback on this forum.  If you break this down into core of what you need which is a) deploying the packages needed for QEMU, KVM and Virtual Networking...b) configuring the virtual network to meet your requirements...c) deploying guest configs.  For this last part I'd suggest you deploy a new generic guest to ensure the KVM setup is working before you attempt your migration of an existing VBox guest.

For a) above I take the easy route which is to use the tasksel package that Ubuntu ships with the server image, I guess this is not necessary as the dependencies are handled no matter but the key difference here is that the networking package is the linux-bridge and not open-vswitch.  Your choice obviously spins out of your requirements but to the best of my knowledge if your only need is to connect hosts on a LAN this is pretty basic, if you're intending to create a virtual bridge on each host to give the VM's an IP off your LAN instead of NAT then I'd say open-vswitch is overkill.

To simplify the deployment if you have a GUI on your hosts or can connect to your hosts via SSH from a linux GUI then you can use the virt-manager package to configure and control most aspects i.e. guest creation and management but also virtual-networking...with 14.04 virt-manager works fine.

I can't really comment on migration, you'll get some steers from others I hope.

As always if you have some really detailed requirements either in host operation or network design its worth explaining them upfront.  A lot of the forum members/moderators either operate in or have working experience in enterprise deployments and so can talk to quite a detailed level.  My experience and use is the opposite :-) as in home use only...this taints my approach as such thus it may not be the right answer for you.

Best of luck.

---

### Post by satimis on 2014-09-05
Hi KillerKelvUK,

Thanks for your advice.

I ran KVM and qemu before, about 8~9 years ago.  Also I have done migration btw KVM and Virtural Box before.  I might still have documentation on my database in this respective, including KVM installation.  But the steps worked for me in the past may not be suitable for today.  That is the reason for me seeking advice on this forum with this posting.

Linux-bridge allows VM/Guest connect Internet.  Then what is Open vSwitch for?  To remote access distant host running its VM/guest locally, in the past I use remote access displaying remote desktop on local PC.

Regards
satimis

---

### Post by TheFu on 2014-09-06
OVS is only needed for 10G networks or higher.  Standard linux bridges are extremely efficient for 1G network connections. OVS doesn't buy much performance - unless you KNOW you need to added capabilities of OVS. Otherwise, avoid the complexity.  If you plan to use openstack - OVS is mandatory, so get used to it.

KVM can be deployed in a trivial way for point-n-clickers, if that is you, don't over think it.  The dependencies are handled cleanly these days.  Think only 3 packages are needed - bridge-utils, kvm, libvirt-bin - oh - and openssh-server.  That's it. I've posted a link in these forums with a beginning KVM virtualization presentation - it covers everything to use virt-manager with KVM including the bridge settings.

Virt-manager is also needed on the client-management-workstation. This can be either local or remote, completely up to you.

Migration is trivial for Linux VMs. Not so trivial for Windows.
* ensure the VM-host provides the same network MAC under KVM as under VBox - that should solve the worst issue, which honestly isn't really bad.  
* KVM will use VDI files now. I always use RAW, images myself. The performance hit for sparse files on spinning disks is just too great for my needs.  Run with the VDI file if you like to see if the performance is good enough for you or not.
* to migrate Windows - running sysprep just before moving the img/vdi/vdmk file(s) is the only way I've had luck.

When/if you need to transfer to raw image files - ask or RTFM for either vboxmanage or qemu-img. It is really easy.  Of course any backup/restore method working at the file system or higher layer will work too. Just connect a booted-liveCD and use standard Linux tools like fsarchive or tar or {insert-any-backup-program} to migrate the setup to whatever newly created vHDD you prefer.

---

