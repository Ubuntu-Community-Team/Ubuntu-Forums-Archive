---
title: "Benefits of Multipass over VirtualBox"
date: 2021-12-23
forum: Virtualisation
---

### Post by cnbiz850 on 2021-12-23
I have been running Ubuntu as guest machine through VirtualBox on MacBook Pro.  I use Ubuntu as my base system for software development.  The guest Ubuntu gets 4GB RAM and 2 cores of CPU.  I also set up the environment so that it shares folders with the host through NFS, and gets forwarded USB ports through which I connect to Android phones.

Recently, I noticed Multipass providing convenient ways of running Ubuntu as virtual machines.  I read that it still lacks some native features like port forwarding but it can provide such features by connecting to VirtualBox.  I am interested in transitioning to using Multipass to set up my Ubuntu virtual environment.  Aside from its ease of setup, I wonder what other pros and cons it has compared with using VirtualBox.  I don't find any article about this on the net.  Anyone please chime in?

---

### Post by TheFu on 2021-12-23
There are many "cons" to using multipass and a few "pros." What each person thinks for pro/con columns is a personal choice.  There are many other options for using KVM/QEMU under Ubuntu - Gnome Boxes and virt-manager+libvirt come to mind.  I've been using the later for over a decade. It provides enterprise stability and capability while still being very user friendly - much like virtualbox or VMware Workstation.  virt-manager and virt-viewer allow controls for USB passthru that work easily with 18.04 and later installs.

Multipass is shipped as a Snap. For me, that is the main downside. My attempts to even run it on 3 different systems have failed completely, since snap packages have problems still. It isn't the only snap that doesn't  work. There are some snaps that do work on those systems, BTW, so it is something specific to the way mine are setup. I haven't a clue what. [https://ubuntu.com/server/docs/virtualization-multipass](https://ubuntu.com/server/docs/virtualization-multipass)

Gnome Boxes provides a simple setup for VMs too. For my needs, the simplification was just a little too much and didn't allow the flexibility needed, but it might work great for others.  [https://wiki.gnome.org/Apps/Boxes](https://wiki.gnome.org/Apps/Boxes)

Too much simplification is a bad thing in my book.

If you are putting a Linux VM onto a Linux host, perhaps using a Linux container would make more sense?  LXD is the container system from Canonical, but it feels more like a VM and works more like a VM from the maintenance standpoint.  LXD is shipped as a snap package, like multipass, but I have it running on 2 or 3 systems here. It works well for normal server needs (not firewalls or other non-standard network needs) and drastically reduces the overhead when compared to a VM.  The major issue I've had with lxd, besides being a snap package, is that it REALLY wants the backend storage to be ZFS. I gave up and created a ZFS block device on my LVM storage. Not my proudest moment.  All the defaults are setup to use ZFS. Oh - and there is no GUI to control stuff - not even an integration with virt-manager.   I have tiny Alpine server, pihole, email gateway and wallabag servers running under lxd. They've been very stable and fast. They use much fewer resources than they did when running in VMs.  Should mention that using NFS inside any container (nfs client or server) requires breaking the non-privileged container feature. They have to run as root - I've done it for a test backup server, but ended up switching to using the native LXD to host storage access capabilities instead.  Running a container as root is bad, and not just because is feels wrong, but there are real security issues in doing it.

IMHO.

Hopefully, some other people with different ideas and experience will chime in.

---

### Post by MAFoElffen on 2021-12-25
I also have an old MacBook here that I use to verify Development... Which I have as a Multi-boot for versions of MAC OSX, Linux and Win. Just because MAC hardware, even though it is Intel based, does still have some specific caveats. It sits most of the time, except when I need to test certain things. I have QEMU/KVM running fine on that also.

I can say, in my own experience, that I do not think that you need "Multipass". Not as a requirement. That would be more as a convenience, and only if you don't mind giving up much resources and flexibility doing it. And except the limitations of it's own installation method.

I do a lot of 'testing', as well as my own development. TheFu and I have talked about this (Multipass)... and Coincidentally, specifically on Canonical's marketing push, and their recommended implementation of "Multipass" recently. On the VM Host side, I am always looking for easier ways to do things... With the least amount of effort and resources.

Multipass is not a VM Host platform. It is meant to be a deployment tool to be able to spin up VM's of 'LTS versions' of Ubuntu using KVM as the base VM Host. The idea is good. But I think the way they went about it (the implementation of) falls short... You would think that they would follow their past path of MAAS, and make it thin resources, easy to install, easy to use and menu driven... You would think it would be a traditional VM Host installation of KVM, where you could use and be able to share it for other things... None of those. Many details on that, that I will not get into. It just turned out to be another animal, altogether.

I got into a discussion with members of Canonical (elsewhere) trying to voice my concerns... It fell on deaf ears, and they did not understand any them. They thought they were great ideas, and made sense... But are pushing what their Marketing is pushing, which I do not say is a lie, but is not exactly the truth.

Mulitipass, in the method they are pushing is Snap's installed, and inside containers. KVM is then Snap installed with it as a dependency. They say "that is the only way to install it." Actually, You can dl the code and compile it yourself, without the resource overhead, and speed concerns of involving Snap's in the process at all... But they still say that Snap's Install is the only way possible(?) IDK. A lot of things didn't pass the commonsense litmus test for me.

Multipass is nothing like oVirt or RHEV, which are products also based on top of KVM, but are GUI and menu driven, at least justifying their extra resources, by making datacenter deployments and management of their VM's easier. They are more like VCenter and System Center SCCM VM . 

Multipass is just only for deployment, and is still, to me, considered a CLI API interface. There is a bit of a learning curve to learn the API and the caveats of it to use it. It is more like just doing a virt-install with some extra tools. I don't see where it would save you time, for what you do. I don't feel it justifies the additional resources and time. I have to say, I am disappointed with it. I wish it was what they said it was, and what it would be.

Since I think you probably would do what I do (similar)... I feel you would be better off just going with Qemu/KVM, Virt-Manager... And some other LibVirt toolsets. You really can't go wrong with KVM, as it is the base for most all modern VM Host toolsets that most all are using commercially (except VMware). As a traditional installation you have a lot of tools to use, that are very flexible with how you might need to use them for development and testing.

To spin up things quickly and easier for me... I create a lot basic OS / Machine platform VM templates, which I can clone and spin up as thin clients... and to quickly modify to my test conditions. That includes for varied architectures and hardware conditions. (x86, amd64, arm32, arm64, Android, MAC OSX, Win, Linux, Unix, VNets, VNet Appliances, etc, etc, etc)

---

