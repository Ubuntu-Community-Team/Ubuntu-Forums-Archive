---
title: "Not a problem, just a newb progress report"
date: 2014-10-21
forum: Ubuntu, Linux and OS Chat
---

### Post by swrichmond on 2014-10-21
First I want to thank the linux community for being here.  Not trying to blow sunshine up anybody's butt, but my disgust level with Microsoft just continues to elevate.  

I remember linux from the days when Nessus was free and Netcat was new (yeah I'm that old).  I drifted away, and now I'm back.

But clients still want Windows, so how to deliver?  Answer: free virtual environment.  Box get screwed up?  I can run the "Windows Recovery Console" ...or spin up a clone. Or I could pay $7K for a VMWare Server license.  Or not.

So as a teaching tool I took an old Dell Dimension 755, upgraded the CPU to a quad core with VT ($20 used on Amazon), bought a new 500GB HD, and away we go!

Don't forget to turn on VT in the BIOS.

Downloaded, burned and launched installer CD for Ubuntu 14.04 desktop.  Installed Ubuntu, ran "sudo apt-get install qemu-kvm libvirt-bin bridge-utils".  Hacked around with it enough to get VMs installed running Ubuntu Desktop and Windows Vista.  They work.  Cloned the Ubuntu vm, copied the file onto an external hard drive, deleted the original, copied the backed up image file into the /var/lib/libvirt/images folder, created a new vm, imported the moved file, and cranked it up.  This is pretty sweet!  I like qemu, the interface makes sense.  Used gparted to add disk space to non-running vm images (though it is a several-step process, it works reliably).  Google is your friend.    

BTW, I can't begin to tell you how nice it is to have the installer determine package dependencies for you and install them automagically...

So next was on to RAID.  Bought another cheapo HD (total investment so far: about $150) and installed it in the can.  Copied the existing vm images onto the external HD.  Downloaded and burned a CD for Ubuntu Server 64 bit, configured software RAID 1, installed it, selecting "virtualization server" option during server install.  Ran "sudo apt-get install --no-install-recommends ubuntu-desktop" (as I said, I like qemu).  I think I had to manually install part of qemu.

And again, it works. Re-imported my existing vms and both of them work.  Not hardware dependent.  Experimenting now with different file formats (RAW, qcow2) and will experiment with backing up / snapshotting, etc.  Also need to learn to write configs for the virtual networks, and optimize disk and network performance.

So far so good.

---

### Post by TheFu on 2014-10-22
Yep. No need for VMware for anyone with fewer than 100 VMs anymore and if you have over 100 VMs, Openstack begins to make sense.

**virt-manager** completely rocks.  I don't think of KVM as being QEMU ... perhaps I should?
```
$ lsmod | grep kvm
kvm_intel             143109  6 
kvm                   451552  1 kvm_intel

```
nope.

If you want lower overhead for Linux, check out LXC. It can be run with many VMs from inside a KVM VM guest too.

If package dependencies get you down - check out **Aptitude**.  It is from Debian and almost a drop in replacement for apt-get. It is much smarter about dependencies - which isn't often a problem, until it is.

Sounds like you're in security?  DevOps can save your butt.  Check out **ansible** for that - also great for CTF contests and NetKotH stuff.  BTW - most people here won't know nc or nessus - desktop users and most pure admins don't need to know that stuff.

Oh - and the reason I even responded .... getting more performance from your VMs: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) - the ideas work across all VM hypervisors, so don't worry about the virtualbox stuff.  I stopped using vbox about 2 yrs ago in any way.  Those tips work for Xen, KVM, and others too.

---

### Post by swrichmond on 2014-10-22
"moved"

So the Virt forum is just for problems, eh?  Ooops.  Looks like a lot of people using virtualbox with mixed success.

Thanks for the reply and the info, I will definitely take a look at the performance link.  I haven't run into any probs yet with apt-get, but will also look into aptitude.  

I am self employed so I need to know all of it...security included.  Clients want to put servers onto the web and I flip out...

---

### Post by TheFu on 2014-10-22
VPN and reverse proxies that are locked down.

Virtualbox mostly works - almost always.  The issues are far apart really.  It is just not as fast as other options and I'm seeing excellent stability+performance for servers on KVM so why not use it, especially if Oracle isn't involved?

---

