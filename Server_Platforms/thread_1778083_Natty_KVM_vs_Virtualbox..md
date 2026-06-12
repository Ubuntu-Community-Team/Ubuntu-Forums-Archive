---
title: "Natty KVM vs Virtualbox."
date: 2011-06-08
forum: Server Platforms
---

### Post by collisionystm on 2011-06-08
Fresh Install of Natty Server. Chose to install KVM and give it a go. It was quick and very easy to get going. Just chose it during the install of Natty, installed the Virtual Manager on my desktop, and boom, I was making ViM's!!

That being said, I decided to switch to Virtualbox on an Ubuntu 10.04 Desktop Install because I find KVM isn't up my alley. 

I couldn't figure out how to swap the cd's out in the guest os. I edited the XML file, applied the appropriate .iso and still, no change unless I did a reboot of the guest os. I would have to say, This scared me a little bit. If it is this complicated to do simple things that you normally need done in a hurry, why use it?

I guess I am just curious what the opinion of others are. Has anyone else used KVM and found it to exceed their expectations? What are its advantages?

---

### Post by rubylaser on 2011-06-08
I normally just use Proxmox as my virtualization platform.  It comes bundled with support for both KVM and OpenVZ all with a simple web gui. Also, it's built on top of Debian Lenny, so you can always add packages if necessary.

[http://pve.proxmox.com/wiki/Main_Page]("http://pve.proxmox.com/wiki/Main_Page")

---

### Post by collisionystm on 2011-06-08
Thanks! I will look into it. I saw this is a webbased virtualbox you can put together, but that's a hassle I don't want

---

### Post by dragonslayr on 2011-07-16
Sounds like you edited the .xml file directly.
If you edit directly, you have to do a /etc/init.d/libvirt-bin restart
Alternatively, you can do virsh edit nameofvm and the change will be applied for you, or you could have used the gui in virt-manager.

However, one giant big glaring bug with ubuntu libvirt, is the inability to have vms gracefully shut down when a shutdown or restart is issued. If you try to make a script and put it in a run level, sendsigs will kill libvirt before your script runs..  All a big pita..

Also, if you have a web based tool like Proxmox offers, you do not have to have another linux box around to run virt-manager from. That's a big plus if you deliver a server to a windows group of folks. I've not tried Proxmox yet, but I'm a bit fed up with ubuntu/kvm and I've been using it for several years now..


BTW, if you use qcow or raw partitions with KVM, make sure to include the cache=none option or performance with be terrible. I believe I read where Proxmox does this by default..

qcow on servers use none
<driver name='qemu' type='qcow2' cache='none'/>

raw disk or partition use cache=none
<driver name='qemu' type='raw' cache='none'/> 

BTW, I find virtualbox useful on desktops, but not servers.

---

