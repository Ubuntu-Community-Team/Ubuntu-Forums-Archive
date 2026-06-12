---
title: "Using a shell script backup to restore to a new server"
date: 2017-07-31
forum: Server Platforms
---

### Post by dalamaar on 2017-07-31
I used the script I found at [https://help.ubuntu.com/lts/serverguide/backup-shellscripts.html](https://help.ubuntu.com/lts/serverguide/backup-shellscripts.html) to backup a server and want to restore it to a new server to test that the backup is working properly.  The server I am backing up is virtual and running on a home server.  If the hardware dies I want to be able to restore my server to a new vm on a new host with minimal effort.

I completed the backup and have it stored on a network drive. After I created a new vm I mounted the nfs drive and extracted the tar to / .  When I rebooted I got the grub screen and picked ubuntu.  From there it couldn't find the disk and proceeded to look for a btfs drive.  After some time the server fails to boot up and I am left at a prompt I am not familiar with.  The guide doesn't mention any extra steps to restore to a new server.  What am I missing?

---

### Post by deadflowr on 2017-07-31
*Thread moved to **Server Platforms***

---

### Post by TheFu on 2017-07-31
Welcome to the forums.

How do I say this nicely.  Don't use tar to backup an entire machine. Tar (or star/gtar/ or any similar tools) should really be limited to storage of less than 500MB in total.  For larger amounts of storage, there are better methods.

For virtual machines, there are many more methods to backup and restore the entire VM. How depends on the hypervisor being used.

BTW, I 100% agree with using VMs and your other idea about being able to pick up a VM and move it to completely different hardware.  That works.  I use it all the time and have been using it since around 2008.

When I first started using virtual machines for everything here, I would copy the virtual storage as a backup.  That's fine, but not nearly as useful as having 120 days of daily backups.  Copying an entire virtual storage daily for 120 days would require much more storage than I could afford, so I switched about 6 yrs ago to using rdiff-backup and treating virtual machine backups just like physical machine backups.  Also, I don't backup things that are easily replaced - like the OS.  I backup everything needed to recreate the same functions and data in about 30-45 minutes, but not the OS.

So ... with all that said, my first question is which hypervisor are you using?  That will determine the easiest way to make that clone backup.

I've assumed you want to backup virtual machines. Correct?

---

### Post by dalamaar on 2017-07-31
I am running bhyve hypervisor on FreeBSD 11 or more specifically FreeNAS 11.  The ubuntu server I have running has apache, openvpn, deluge, flexget, customized python virtualenv running django, customized python in the regular env, multiple network mounts (Cifs and nfs), user accounts created to run apps and a few custom made service unit files .  My intention is to capture all the customization's on the server so in the event the hardware dies I can bring back my system with minimal effort.  I am open to any recovery method with priority to a simple solution and is not specific to a single hypervisor.

My approach was to use the backup script from the ubuntu web pages without modifying anything other then destination.  The backup was around 250mb in size so I am not to concerned about the space required to store the tar's, all the real data is on the FreeNAS drives.  I was hoping I could build a new ubuntu server and restore the tar over the files but I haven't had luck.  I was going to take a look at the backup list again and see if I can figure out what part would be pulling the system virtual hardware specific information from.  Or maybe generate the backup list from the things I know I need to run my server and nothing else.  This is all on my home server and I was lucky enough to get all this running the first time, would hate to have to figure all this stuff out from scratch again.

---

### Post by TheFu on 2017-07-31
Most Linux hypervisors have an export feature to make backups trivial.  Some quick reading about the BSD thing you are using seems to say it lacks those features.

Ok - I'll forget about the hypervisor and doing things from outside the VM.  You'll want to backup the VM settings, however your hypervisor does that. With KVM and libvirt, there is an XML file for each VM which describes the virtual hardware provided and points directly to the virtual storage device(s) being used.  Grabbing a copy of the XML and the virtual storage is enough. If using qcow2, the storage might be already compressed just depends on the creation settings.  I'll assume you will handle that yourself for your hypervisor.

I'm guessing that you aren't setting up grub as part of the restore process?  You'll need to do that.  Off the top of my head, the process would be:
[LIST=1]
[*]create the VM in the hypervisor
[*]setup the virtual hardware to be identical (or close enough) as the prior VM host
[*]boot from a live-boot ISO running the same version of Ubuntu as you will be restoring - x32 or x64 matter
[*]from the live-boot environment, create the partitions and file systems needed to hold the tgz data
[*]restore the tgz data where you need it.
[*]use the live-boot menu to setup the chroot for /, /boot, and /boot/efi as needed. If you have more partitions lile for /var or /etc, get those into the chroot correctly too
[*]run grub-install
[*]run update-grub
[*]back out of the chroot
[*]reboot the live-boot environment
[*]disconnect the ISO, so it doesn't boot
[*]have the hypervisor to boot from /boot inside the VM
[/LIST]

If you use efi, things could be a little different.  My efi system (only have 1) requires a nested mount, so /boot must be mounted before /boot/efi is.  I don't use efi inside VMs.

This shouldn't take long - perhaps 5 minutes of hands-on work (if you didn't save the partition setup stuff in a machine readable way) and 15-30 min for the tar xvf, then 3 minutes for the grub stuff and last reboot.

If you want to make daily backups that take 1-2 minutes total and can be done on the running OS, use snapshots with LVM **inside** the VM and mount the frozen snapshot storage, then backup that using rdiff-backup.  The most recent rdiff-backup looks like an rsync, but there is a special directory rdiff-backup-data/ which retains all the gzip'd diffs for files. It also keeps the ower/group/permissions/ACLs/xATTRs which would be lost with just rsync backups as changes happen over time.

---

