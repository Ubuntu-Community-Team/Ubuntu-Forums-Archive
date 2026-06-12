---
title: "Small Ubuntu (guest) VMWare images?"
date: 2010-08-08
forum: Virtualisation
---

### Post by misha680 on 2010-08-08
Dear All:

I am trying to make an Ubuntu Desktop 10.04 VMWare image using all default options.

Mine comes out to 
```

misha@misha-d630:~/vmware/Ubuntu$ du -s .
3407600	.

```
3.4 GB using a 20GB, non-preallocated, 2GB chunks.

However, I see other VMWare images are much smaller
[http://chrysaor.info/?page=images&filter=Ubuntu](http://chrysaor.info/?page=images&filter=Ubuntu)
(1.1 GB).

Any ideas how they were able to do this?

Thank you
Misha

p.s. I cannot shrink the image from within VMWare Tools as the disk is ext4. Thank you.

p.p.s. Under VM Settings->Hard Disk->Utilities I tried both Defragment and Compact but unfortunately for a brand new Ubuntu install:
```

misha@misha-d630:~/vmware/Ubuntu$ du -s .
3407272	.

```
no better :(

---

### Post by misha680 on 2010-08-08
According to file-roller, the uncompressed disk image is 3.4 GB.

Misha

---

### Post by TheFu on 2010-08-09
I haven't done this myself, but it should work. I have moved entire Linux installs between disks.

If you don't like the size of an image, you can always check the full disk on a temporary VM by using `df` to see what is actually required.  

Then you can create another virtual disk file sized more appropriate to your needs using VMware at the host, connect the new disk to the same VM, and copy all the data over using `dd` from either the host or inside the client OS (if client be in run level S). Only the boot data needs to be in a specific location on the virtual disk with all the other stuff organized by the file system.  Swap the virtual disks from the VM setup tool and don't connect the old - larger disk at boot.  At the next boot, it should find the new, smaller disk and boot fine.

Usually, the sized disk in the image is good enough for a first install, but not sized for production use.  For example, IME,  10GB is a good size for a desktop Ubuntu - large enough to not be constraining, but not large enough to store media inside the virtual disk (store media on the host OS or on the network instead).

Other options are to use smaller Linux images than Ubuntu (600MB is the smallest Ubuntu Install). You may already be aware of them, but others are not.  Puppy Linux, DSL, or even TinyCore Linux can fill many needs for folks while using smaller disk sizes. I think Puppy and DSL are less than 120MB and I KNOW that TinyCore is under 16MB.  Just options where a smaller install is needed.

Ubuntu is very nice and their application repository is one of the best, but for some folks the size is simply too large when you don't have normal disks OR if you are planning to deploy thousands of images.

Good luck.

---

### Post by misha680 on 2010-08-14
> **TheFu said:**
> I haven't done this myself, but it should work. I have moved entire Linux installs between disks.

If you don't like the size of an image, you can always check the full disk on a temporary VM by using `df` to see what is actually required.  

Then you can create another virtual disk file sized more appropriate to your needs using VMware at the host, connect the new disk to the same VM, and copy all the data over using `dd` from either the host or inside the client OS (if client be in run level S). Only the boot data needs to be in a specific location on the virtual disk with all the other stuff organized by the file system.  Swap the virtual disks from the VM setup tool and don't connect the old - larger disk at boot.  At the next boot, it should find the new, smaller disk and boot fine.

Usually, the sized disk in the image is good enough for a first install, but not sized for production use.  For example, IME,  10GB is a good size for a desktop Ubuntu - large enough to not be constraining, but not large enough to store media inside the virtual disk (store media on the host OS or on the network instead).

Other options are to use smaller Linux images than Ubuntu (600MB is the smallest Ubuntu Install). You may already be aware of them, but others are not.  Puppy Linux, DSL, or even TinyCore Linux can fill many needs for folks while using smaller disk sizes. I think Puppy and DSL are less than 120MB and I KNOW that TinyCore is under 16MB.  Just options where a smaller install is needed.

Ubuntu is very nice and their application repository is one of the best, but for some folks the size is simply too large when you don't have normal disks OR if you are planning to deploy thousands of images.

Good luck.

Thank you. I have ended up getting down to 1.9 GB for my image 
[http://openmrs.org/wiki/OpenMRS_Development_Appliance](http://openmrs.org/wiki/OpenMRS_Development_Appliance)
with some 7zip tricks that I learned from another OpenMRS developer.

Relevant details can be found here:
[http://openmrs.org/wiki/OpenMRS_Development_Appliance/Steps_to_Reproduce](http://openmrs.org/wiki/OpenMRS_Development_Appliance/Steps_to_Reproduce)

But the key was this command (I keep my VMs in ~/vmware):
```

cd ~/vmware
sudo aptitude install p7zip-full -y
7za a -t7z -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on your-vm-name.7z your-vm-name/

```

Misha

---

### Post by akaikaze on 2010-08-30
Maybe this will help

[http://www.insomnihack.com/?p=387](http://www.insomnihack.com/?p=387)

---

