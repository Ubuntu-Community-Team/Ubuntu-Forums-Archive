---
title: "Ubuntu Media Server with Virtualisation"
date: 2015-08-27
forum: Virtualisation
---

### Post by nomadictech on 2015-08-27
Hi all,
 
Currently dipping my toes in the world of Linux. I have four systems at home:
 

[LIST]
[*]Desktop: Win 10, 48GB Ram, 12 thread CPU running VMs with MS Server 2012, etc
[*]Self-built AMD running PFSense and assorted plugins
[*]HP Gen 8  with 8GB of RAM and 3TB HD with 60GB SSD
[*]Xeon E3-1245 with 32GB of RAM, 120gb and 240GB SSD
[/LIST]
 
Plan is for the Xeon to become a media server and also run some VMs. The HP will become the backup server (CENTOS,Server2012 or Win 10). 
 
Reading around Ubuntu, seems the most popular Linux distro, but I cannot run OMV on it natively. So once Plex and Subsonic/Madsonic is installed, can I replicate OMV with other plugins? Aim would also be to back everything up to this server and use the backup server to clone the data (yes I am paranoid). Considering even keeping the HP offsite so a weekly incremental backup via Rsync.
 
Also want to run a few GNS 3 emulators with IBM Integration Bus on top. Views?

---

### Post by TheFu on 2015-08-27
Don't know what OMV is. Please clarify.
Don't know what GNS 3 is either.
There are multiple things called "Plex" in Linux - which one?

Besides that, just know that virtualization works best for server processes, not GUI stuff.  If you wouldn't run it over either ssh or a remote desktop from 2K miles away, don't plan to run it inside a VM without extraordinary effort and highly, highly, highly, specialized hardware (2nd GPU/MB/Chips) and software to make it work.

Win10?  Privacy much?

---

### Post by KillerKelvUK on 2015-08-27
Hey so assuming by OMV you mean OpenMediaVault?  If so then the answer is yes...where you call them plugin's the language here is package e.g. you want to share media using NFS...OMV will have a page to config this but in ubuntu you'll need to install the nfs-kernel-server package and configure it using the terminal or CLI.  You can make this more like OMV by using something like webmin which is a web based admin tool for servers...this will give you something similar to OMV but not exactly the same.

You can install a GUI desktop onto the Ubuntu server, this will then enable some GUI tooling for admin of the services but honestly the workhorse here is still bash (like cmd in Win).  However with the GUI you should be able to get GNS3 working, they have a guide on their site for linux...can't comment on the IBM bus sorry.

GNS3 docs shows QEMU and Virtualbox support...so I'd recommend for virtualisation you look into KVM, this is the standard virt package that Ubuntu ships however Ubuntu supports many more options, the key here is that KVM employes QEMU so this should make it compatible with GNS3.

I've run Plex in a VM in the past as a ubuntu guest, no issues just make sure you get your storage solution nailed properly...whilst plex in linux doesn't need to store the media it is pretty hungry on meta-data and associated material so gets intensive on the storage...obviously depends on the size of your media catalogue and what you tell Plex to do!

---

### Post by TheFu on 2015-08-27
If you want virtualization on Ubuntu, then definitely look at KVM+libvirt+virt-manager.  This is the most capable and easiest to get going for server-on-server VMs.  virt-manager (also called VMM sometimes), runs on any client machine with X/Windows from anywhere in the world. It can use ssh as the tunnel and authentication. libvirt can be used to manage a few different hypervisors - kvm, qemu, lxc, xen, esxi, and virtualbox.  KVM and Xen are the easiest for now. There are a few manual items that need to be done from a shell to get the best storage and best networking.

If the Plex is Plex Media Server - I've been running that for years.  PMS will work inside a VM easily, but I'd keep all the media outside the VM and just access it using NFS from the storage or storage server.  Storage servers should run on the hardware, not inside a VM, IMHO. Other people have different opinions about that.  PMS will place metadata in a deep, deep, deep structure under /var (which is using 35G currently on my PMS system).
 
If any of those tools are paid, you don't need them.  The F/LOSS solutions for this stuff works pretty well and it works extremely well if you use the shell, not some GUI.

---

### Post by nomadictech on 2015-08-28
Hi both,

Thanks for the feedback. It looks like Ubuntu will do the job. 

Dan

---

