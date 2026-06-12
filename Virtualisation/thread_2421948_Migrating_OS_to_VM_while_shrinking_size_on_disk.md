---
title: "Migrating OS to VM while shrinking size on disk"
date: 2019-06-29
forum: Virtualisation
---

### Post by andre46 on 2019-06-29
Ok, so forgive me if I explain this poorly.

For years, I have done everything off a single install of Ubuntu Mate, treated essentially as a home server. The OS runs on a 120GB drive, but only takes up ~45GB.

I want to install Proxmox, and do everything via VMs now. I have gotten an image of the OS drive using clonezilla. I was able to restore it to an external 128GB virtual storage, and that worked. Great.

But I want to have all my VMs running from the original 120GB drive (which remains untouched, and I've removed it from the device during my testing). Which means I want to restore the original 120GB image to about 55GB.

So it seems I have a few options:
[LIST]
[*]clone the image to a smaller virtual drive using clonezilla and [this magic]("https://superuser.com/questions/1361361/clonezilla-wont-clone-to-a-smaller-disk") (I just tried this, and the transfer failed around 60-70%)
[*]clone it as it is, and resize using Proxmox, which Proxmox says is not supported
[*]shrink the volume on the original drive, then clone again with clonezilla again, and then restore with clonezilla to a smaller drive. I'm not convinced this will work, but it's the only other thing I can think of
[*]create a new VM of a clean install of ubuntu mate - but if I do this... how do I know what to copy from the old install to the new install?
[/LIST]

That last option I came up with while I was writing this. And then I found the app Aptik, which sounds perfect. This might be the route I go, but I would like to know if there is something else I'm not thinking of or if someone knows of a better way?

Thanks for any help

---

### Post by cruzer001 on 2019-06-29
> create a new VM of a clean install of ubuntu mate - but if I do this... how do I know what to copy from the old install to the new install?
I prefer a fresh install, so I would op for this.

I would just copy my home directory over to the new install.  User name must match user of new install, if you changed it.

You can copy all currently installed packages with SynapticPackageManager and transfer to new install.  Have any PPAs?  You need a copy of "/etc/apt/sources.list.d" for the new install.  Same with snap packages check with the command "snap list".

People have their pet ways of doing this.  This would be mine :)  That will get you off to a good start.  Also never used Proxmox, can't help there.

[http://freesoftwaremagazine.com/articles/using_synaptic_package_manager_clone_installed_software_another_computer/](http://freesoftwaremagazine.com/articles/using_synaptic_package_manager_clone_installed_software_another_computer/)

[https://geek-university.com/uncategorized/synaptic/](https://geek-university.com/uncategorized/synaptic/)

---

### Post by andre46 on 2019-06-29
Thanks. That's probably the best route. The other options are just... really complicated.

---

### Post by cruzer001 on 2019-06-29
I did some reading.  Proxmox is a stand alone install containing the complete Debian system.  Now I understand why its a 600MB download.
But you say this is a Ubuntu Mate install?  Must be wiping the current install for Proxmox?

---

### Post by TheFu on 2019-06-29
I've never used proxmox, but have followed it from a VM standpoint.

Proxmox will wipe disks during install.  If you don't want it wiped, I'd unplug the disk to be sure it isn't touched.
I wouldn't assume that you can access proxmox VMs directly on the proxmox machine.  Definitely check that before starting.
For a pure server, i.e. no GUI, there is much to like about proxmox.  I hope you don't plan to game or watch videos using it.

You can resize image backups, but only if you use **fsarchiver** for each partition that you backup.  I don't like image backups for many reasons.  I prefer file-based backups since they are more flexible.

Aptik seems like a good solution, until you try it and it fails.  Basically, it makes tgz file backups, if it works.  I would only use it on single user systems, without any running services or data that isn't in a single HOME directory.

I use **apt-mark showmanual** to make a list of all manually installed packages. Store that list in a file that is included in daily backups.  Then at restore time, after I've restored the settings and data, I'll use apt-mark again to shovel the pkg list file back into APT.  I've written about my backup methods here at least 50 times. A few of those include specific directories, but usually the admin should **KNOW** which directories need to be backed up.  If you don't, then buy a new SSD and do the fresh install onto that so you don't lose the old data until you are 100% positive everything is included in your backups.

When I was first trying this stuff, I failed to get everything about 4-5 attempts.  Since then, I've never failed.  If you start with my list of directories and actually understand why each is included AND follow standard admin rules for where files should go, then success should come sooner than later.

Until you have validated a restore using your backup method, you don't actually know if your backups are useful or not.

---

### Post by andre46 on 2019-06-29
Yeah, Proxmox is just an OS for creating/managing VMs. It has no GUI, and all tasks are done through a web browser. And yes, I will ultimately be wiping the drive and installing Proxmox. I was booting Proxmox off a USB for testing/discovery to try and decide if I should go that route, or alternatively if I should just use a lightweight vanilla OS with VIrtualBox installed to manage/create VMs.

I'm still not sure which system I'm better off with, but I'm definitely moving to VMs. Much easier to take snapshots and make backups, as well as just spinning up a test device.

---

### Post by TheFu on 2019-06-29
You don't need to sell me on using VMs.  My primary desktop has been running on a headless KVM hypervisor since 2010 and on a virtualbox VM for a few years before that.  I can access it from 2 ft away or halfway around the world.  I've accessed it with a GUI from 5 different continents, thanks to x2go.

Snapshots might be easier with VMs, but they aren't as efficient and will slow down a VM over time if you have too many as distinct layers.  If you don't go crazy and create them only prior to big events while you are unsure if the changes will be stable, then roll the changes together after a week or 2 of use, it should be fine.

Using LVM, which is how proxmox does the snapshots, is very different from how virtualbox does them.  It is a file system capability, not a VDI file capability.  Very different.

As for backups, I don't use any VM specific backup capabilities.  Each VM is treated like a physical host when it comes to backups. Initially, I tried to use whole VM backup solutions and found them taking many hours.  Switching to normal versioned, inside the VM, backups and most of my VMs are backed up in 2-5 minutes each instead of 60-120 minutes each. Plus, I can retain 60-180 days of versioned backups which cannot realistically be done using VM-based backup methods.  
Restores are slightly more complex, but still completed in 30-40min. About once a year, I have to restore an OS or move it from 1 system to another.  Even if there isn't an issue, I like to test my backup and restore methods to be certain they are still working as expected.  An untested backup is only "hope" and that isn't a plan.

I wouldn't use virtualbox unless you want desktop-on-desktop virtualization.  If you want the stability of  a server-based hypervisor, I'd strongly suggest using kvm + libvirt on the server, then on the management workstation, use libvirt + virt-manager.  Virt-manager provides a virtualbox-like GUI, except it can use ssh tunnels to manage all VMs and access the GUIs for emergency needs.

If you want pretty impressive LAN-based remote desktop use, then KVM is the only hypervisor that supports the SPICE protocol.  If you want multi-node replication and failover without running a complex storage cluster file system like Gluster, then sheepdog an be used for KVM storage in an N+1 configuration. You have control over the number of copies for every file inside the storage.

But you'll have to decide if you like to know how things work or if you are happy with the "magic" being hidden behind proxmox.  Be aware that when something bad happens, and it will due to some software or hardware issue, if there is too much magic, the risk of total loss is higher.

---

### Post by andre46 on 2019-06-29
Sorry, my last response was to cruzer001. I guess we were typing at the same time. So I'll respond to your first message first.

Yes, proxmox is headless, and that's fine for me.

Aptik did turn out to be a bit lackluster. Not exactly sure how I'm going to do this clean install yet. Can you please provide me with your backup methods? Sounds like you might be able to link to it in your history a bit easier than I would.

The good thing is that I have no shortage of drives. I've just booted the original server back up, as if I had done nothing at all. Ready for me to make my decision of my next steps.

Can you go into more detail about this: "Switching to normal versioned, inside the VM"? Still pretty new to the VM world, tbh.

kvm + libvirt sounds good, too. I'll have to read up on it a bit more. I'm a bit concerned when you say I need software on the management server, as the only linux device that I have is my server. Everything else is Windows or Android. I'm sure it's doable - I just haven't looked into it yet.

---

### Post by cruzer001 on 2019-06-30
> I wouldn't use virtualbox unless you want desktop-on-desktop virtualization.
That pretty much sums up VirtualBox.  Thats why I started using it.  I have ran full desktops and core installs as host, even ran ubuntu-mate-core package for a while. Never really noticed a performance difference with any of them.  I guess vBox has just one speed :)  So my last full desktop host was Gnome desktop.  I find with vBox you need to assign 2core and 3G ram for acceptable guest performance.

Your starting out fresh, might as well go for the performance of KVM over vBox or containers over KVM.

So whatever you decide, good luck

---

### Post by TheFu on 2019-06-30
> **andre46 said:**
> 
Can you go into more detail about this: "Switching to normal versioned, inside the VM"? Still pretty new to the VM world, tbh.

I do backups inside a VM just like I would do backups for a physical machine.  rdiff-backup of the snapshot created just for that backup. Once the backup finishes, I remove the snapshot.  I "pull" backups, never "push" them for security reasons.

> **andre46 said:**
> 
kvm + libvirt sounds good, too. I'll have to read up on it a bit more. I'm a bit concerned when you say I need software on the management server, as the only linux device that I have is my server. Everything else is Windows or Android. I'm sure it's doable - I just haven't looked into it yet.
Don't get stuck reading when 30 min of playing will teach so much more.  Expect the first 2 installs of the hypervisor host to be throwaway installs just for learning.  Git 'er done.  

There is no "management server."  Any linux desktop can be used to manage any KVM+libvirt setup on 1 or 50+ VMhosts.  I have no idea how you might use libvirt/virt-manager on any OS other than Linux with a GUI.  Google found this: [https://serverfault.com/questions/340949/is-there-a-way-to-run-virt-manager-on-windows](https://serverfault.com/questions/340949/is-there-a-way-to-run-virt-manager-on-windows)  The SPICE interface does work well on Windows, but you'd have to setup at least 1 workstation without using a GUI first.  Probably easier to either live-boot into a Linux desktop for that first VM desktop install. Or load virtualbox on Windows and run a tiny Linux VM there to get started.

As an aside, I use x2go most of the time, even where SPICE works well.  This is because x2go lets me reconnect to a running session from different locations and different clients.  My 15 terminals are all there waiting, placed where I like them.  x2go only works for Linux systems, but isn't tied to the virtualization. There are x2go clients for Linux, Windows, and OSX.

 SPICE works with any guestVM, but requires KVM as the hypervisor. I've only gotten it working on the LAN, but I've seen other people use it through firewalls and secured channels.  SPICE is definitely faster than x2go.

x2go feels about 2-3x faster than any VNC/RDP solutions, plus the NX protocol uses ssh credentials and tunnels for security. If you ssh key is already unlocked, then x2go to a remote system using ssh-keys doesn't require any manual credential stuff. It works just like ssh-keys does - well - it should, because it uses ssh-keys when they are available between 2 systems.

---

