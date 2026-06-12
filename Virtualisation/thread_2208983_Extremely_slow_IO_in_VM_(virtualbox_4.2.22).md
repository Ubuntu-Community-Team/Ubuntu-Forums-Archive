---
title: "Extremely slow I/O in VM (virtualbox 4.2.22)"
date: 2014-03-03
forum: Virtualisation
---

### Post by fizikz on 2014-03-03
I'm doing a simple copy/paste operation from the guest OS (Win7) to the host OS (Ubuntu 12.04) through shared folders and the transfer is proceeding at barely 1MB/s. That's after I defragmented the guest OS hdd, as before that the rate was around 200KB/s. Any tips would be appreciated.

---

### Post by TheFu on 2014-03-04
[http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox](http://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox)

---

### Post by fizikz on 2014-03-08
Thanks, lots of good tips in that article, even if it is a bit dated. The most important point is to avoid dynamic allocation for the hard disk file, which unfortunately I am currently using. I'll have to find a way to make a fixed sized hard disk file and copy the existing installation onto it.

---

### Post by TheFu on 2014-03-09
* Create a new, fully allocated vHDD for the VM in the real size needed. 15-20G is almost always enough.
* Get a gparted ISO file ... or any liveCD that you can boot and install Gparted into (system rescue, etc.)
* Connect the ISO to the VM and force it to be booted.

The OS will be running of the ISO, and both the sparce storage AND the fully pre-allocated storage are available.  Using gparted, copy the partitions over to the new vHDD.

* Change the /etc/fstab in the new storage to use device names.
* Use grub-install to the new vHDD - write to the MBR, not any specific partition and force it to use /sda1/boot/ - that is NOT the correct location/cmd.  Or use **boot-repair** (see my signature for links).
* Shutdown the VM.
* In the VM settings, remove the old vHDD and ISO.
* Boot into the new box.
* Change the /etc/fstab back to using UUIDs. Might be able to see this when gparted.iso is booted and merge this step before the reboot. If possible, that would be easier.

---

### Post by fizikz on 2014-03-09
Thanks for these instructions! My guest OS is Windows 7 so how would the MBR steps be adapted? The other problem is that I don't have enough free space to make a second vHDD. The vHDD is 35GB (dynamic), with almost 30GB used. I'm surprised it got so huge. There is about 5GB of data on it and just a few special programs. I have an external USB2 NTFS external hard drive with enough free space, but not sure if that would work and be practical for this purpose.

---

### Post by TheFu on 2014-03-09
Host OS partitions don't matter. The guest vHDDs are just files, so those will be MBR "inside the vHDD file". There is no risk to the hostOS when using virtualization - besides the hypervisor drivers.  All those steps happen "inside the VM" unless it is with the VM settings. Nothing will touch the hostOS.

USB2 is too slow for VM use, IMHO.  USB has issues that make running a general purpose OS on it a bad experience - even USB3 has these issues.

Uh ... I've been using the same 10-15G for my main desktop VM since 2009-ish.  Find the junk and delete it.  I still have 3G free. See my signature for nominal Ubuntu System Maintenance - especially the cleanup stuff.  Of course, I don't keep any media files inside VMs - those are all stored on the network - OUTSIDE the VM.  I use the **du -sh** command to find where the largest files are stored and work my way done the directory tree until the issue is found.  I suspect your HOME has lots of crap.  From time to time, that happens to all of us. ;)

---

### Post by fizikz on 2014-03-09
Just to be clear, are you saying that the grub/MBR steps apply to *Windows* guest OSes? Since you mention /etc/fstab, I take it you think my guest OS is linux. My host OS is linux, and I realize the host is not affected by the guest. 

The USB2 external hard drive would only be used for the dynamic-to-fixed vHDD swapping operation, not for regular use. Even so I'm not sure this would work well.

I had initially started with a 10GB partition but it got full to the point having 0% (just a few MB) free space. Is your guest OS Windows? I think a linux OS is typically much cleaner and smaller. I'm at a loss as to what used up all that space. Things like Windows, java, MS Office updates consistently eat up space which I don't know how to reclaim.

---

### Post by TheFu on 2014-03-09
Ooooooh!!!! My mistake. Too many sleeping sessions since we started and I didn't review.

For a MS-Windows guest-OS  - reinstall. I think 30G is the smallest I've used for Win7. 15G for XP, but nobody should be installing that anywhere these days - support ends in a few weeks.

---

### Post by fizikz on 2014-03-09
No problem. Yes, Windows eats up the space. 

So, looks like I'll have to reinstall the Windows guest. I was afraid it would come to this.

In an unrelated question, would it be possible to have the same vHDD used by two different installations of VirtualBox? i.e. have VB installed in Ubuntu and also Windows (dual boot system), and have the vHDD in a shared data partition. Then regardless of which OS I boot, would I still be able to access the same VM? I realize the VM settings in both VB installations would need to match but aside from that would this be feasible?

---

### Post by JKyleOKC on 2014-03-10
> **fizikz said:**
> would it be possible to have the same vHDD used by two different installations of VirtualBox?
Yes, you can attach the same *.vdi file to more than one VM in VBox, but if you do, only one of the VMs can run at a time. I do this with a couple of "archive" virtual disks, and I hardly ever have more than one VM running at once. Of course, the VDI file has to be someplace that both of the dual-boot systems can access it, and since Windows doesn't support Linux file types, while NTFS doesn't have the same permission structure, this might be difficult to achieve.

BTW, I usually make my virtual disks only 10 GB, but only one of my VMs uses a current Windows install. Most of my Windows VMs are either Win2K or XP, and each is used for only a single specific task, not for general computing. All my internet connections go through a **very** locked-down Xubuntu system and I'm pretty paranoid about safe computing, so I don't feel a need for all the Windows security updates and EOL conditions of the versions I use. The Xubuntu hosts, on the other hand, get updated regularly!

---

### Post by fizikz on 2014-03-10
> **JKyleOKC said:**
> Of course, the VDI file has to be someplace that both of the dual-boot systems can access it, and since Windows doesn't support Linux file types, while NTFS doesn't have the same permission structure, this might be difficult to achieve.

I was planning to have the vHDD on a shared NTFS partition. What kind of difficulties might I expect?

---

### Post by JKyleOKC on 2014-03-11
I don't actually know. I did temporarily install VBox on my wife's Win8 machine but due to a problem with USB2.0 had to replace it with VMWare Player almost immediately. There didn't seem to be a problem with having its VDI file on NTFS rather than EXT4, but I didn't work with it long enough to be sure. It's worth trying; just be sure that the common disk is formatted with NTFS since Windows won't read the Linux filesystem types.

---

