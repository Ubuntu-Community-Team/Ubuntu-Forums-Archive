---
title: "KVM and virt-p2v, can't find it"
date: 2014-08-09
forum: Virtualisation
---

### Post by Glenn_Robinson on 2014-08-09
I have 14.04 server installed and KVM.

I'm looking to p2v an old Windows 7 laptop in to KVM as a VM.

Much of the documentation I've found discusses using oVirt and the virt-p2v tools. Trouble is I can't find virt-p2v for Ubuntu.

I've installed libguestfs and libguestfs-tools as I read virt-p2v had been moved to libguestfs, still nothing.

Can anyone advise where I can obtain this tool, or, an alternative?

Thanks in advance.

---

### Post by TheFu on 2014-08-10
I migrated an older VM (win7) into a new KVM 14.04 VM yesterday.  It had always failed prior to that time, then something "clicked" - **sysprep**.

Overview of the steps:
* Backup the system you are going to modify (Win7)
* Run sysprep - which removes specific settings for an installed system and creates a ready-for-install-on-new-hardware setup.  There are many caveats for sysprep to work - google is your friend. Main things are that "upgrade" Windows license DO NOT WORK. Only a full retain install will work, not OEM installs or any sort of upgrade - even Home into Professional.
* Do NOT boot the Win7 OS on the physical machine.
* Using some imaging/dd software, create a raw image from the partition on the physical disk. I didn't have to do this since I was going from VM to VM.  ddrescue, fsarchive, are the tools I'd use.
* Create the VM settings to install the Windows7 VM into.  This should match the original as closely as possible, but go with Intel PRO/1000 NIC and SATA for the disks.
* Place the "image" of the C: disk onto the VM host machine.  Also, have a Win7 DVD/CD ready to fix the boot issues with the VM image file.
* The first boot inside the VM of the OS will be like a mini-install - new language, new user ID (the old one are there, so don't worry), the OS will determine which drivers need to be setup inside the VM.

All the previous programs were still there after the migration, although 7MC refused to work.  All the other normal, non-hardware related things, worked.  Also had to re-activate over the phone, the automatic re-activation failed.  The 7MC settings were corrupted, but the HDHomeRun drivers and programs showed zero issues.  Uninstalled media center, reboot, reinstalled media center, reboot - still didn't work.  Went through all sorts of 7MC attempts - deregister DLLs, re-register them, reboot .... tons of rebooting.  Eventually, it started working after about 5 hours of different attempts.  I don't know why it worked eventually. Drives me crazy when that happens.

For me, this Windows system is highly specialized. It records OTA TV and runs Quicken. It is not used for any other purpose.  The recorded TV is moved off the system to be processed, viewed.

So the only trick you need it the sysprep and converting a physical partition into VM image files.
After creating an image file, you can convert it to vdmk, vdi, qcow, qcow2 using the qemu or vboxmanage tools.

Be certain you have a good backup of Windows before starting, since you may need to work through this a number of times.

Hopefully, you don't have more than 30G for C: ... and have other drives for data.  I did and the data partition was actually inside a completely different VM image file here. That made that part of the migration easy.

I've never heard of libguestfs. Sorry.

Hope this helps.

---

