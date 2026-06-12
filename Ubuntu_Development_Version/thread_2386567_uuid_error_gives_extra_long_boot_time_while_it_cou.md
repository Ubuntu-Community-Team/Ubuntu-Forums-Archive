---
title: "uuid error gives extra long boot time while it counts down"
date: 2018-03-07
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2018-03-07
I get very long boot times which I think is related to this

In the past, I had 4 hard drives installed, now only one drive.
So is there an easy way to fix this?

```
Processing triggers for initramfs-tools (0.130ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-10-generic
[B]W: initramfs-tools configuration sets RESUME=UUID=e2731c91-afe6-405e-9876-1e25ac9cd77e
W: but no matching swap device is available.[/B]
I: The initramfs will attempt to resume from /dev/sda6
I: (UUID=388b3c4a-93a3-473c-89ec-77e8688e5845)
**I: Set the RESUME variable to override this.**
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/i386-linux-gnu_GL.conf: No such file or directory
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf: No such file or directory
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf: No such file or directory
Processing triggers for libc-bin (2.27-0ubuntu2) ...
Processing triggers for menu (2.1.47ubuntu1) ...

```

---

### Post by oldfred on 2018-03-07
Post these in code tags:
       sudo blkid -c /dev/null -o list 
      
 lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT 
    
cat /etc/fstab

---

### Post by sdowney717 on 2018-03-10
I solved by putting those 3 drives back into the PC.

---

### Post by flocculant on 2018-03-11
> **sdowney717 said:**
> I solved by putting those 3 drives back into the PC.

That would work - I suspect also that commenting out the swap line in fstab would have done so too :)

---

### Post by AtesComp on 2018-06-20
```
Processing triggers for initramfs-tools (0.130ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-10-generic
[B]W: initramfs-tools configuration sets RESUME=UUID=e2731c91-afe6-405e-9876-1e25ac9cd77e
W: but no matching swap device is available.[/B]
I: The initramfs will attempt to resume from /dev/sda6
I: (UUID=388b3c4a-93a3-473c-89ec-77e8688e5845)
**I: Set the RESUME variable to override this.**
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/i386-linux-gnu_GL.conf: No such file or directory
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf: No such file or directory
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf: No such file or directory
Processing triggers for libc-bin (2.27-0ubuntu2) ...
Processing triggers for menu (2.1.47ubuntu1) ...

```
The &#8203;**initramfs-tools ****RESUME** implies you have hibernation turned on.  Hibernation relies on swap space that is >= memory.
Your swap partition was on one of the removed drives.  You can remove your old drives and setup a new swap on the single disk.  The new swap can be a partition or a swap file.  Using a swap file has the benefit of being easier to change/grow than a partition, especially when you have used up the rest of the drive with other partitions.  Hibernation adds a little more effort for the swap file.  When you boot without a defined swap space, your system may create a swap file at [FONT=courier new]/swapfile[/FONT] automatically.

[LIST=1]
[*]Turn off swap:
[FONT=courier new]sudo swapoff -a[/FONT]
[*]Edit /etc/fstab:
 [FONT=courier new]sudo nano /etc/fstab[/FONT] and remove / comment out (#) the swap line
[*]Remove the partition / drive / swap file:
 [FONT=courier new]gparted[/FONT], [FONT=courier new]parted[/FONT], [FONT=courier new]sudo rm /swapfile[/FONT] or similar.  In your case, just power off and remove the drives (you can do this for the reboot later).
[*]Create the SWAP space file (for a 16GiB RAM system + 2GiB, adjust if different):
[FONT=courier new]  sudo dd if=/dev/zero of=/swapfile bs=1024 count=18874368[/FONT]
--OR--
[FONT=courier new]  sudo fallocate -l 18g /swapfile[/FONT] (but this may allow for holes in the file, see others for problems)

[FONT=courier new]sudo chmod 600 /swapfile[/FONT]
[FONT=courier new]sudo mkswap /swapfile[/FONT]
[FONT=courier new]sudo swaplabel -L SWAP /swapfile[/FONT]
[*]Turn on swap:
[FONT=courier new]sudo swapon /swapfile[/FONT]
[*]Edit the file "[FONT=courier new]/etc/fstab[/FONT]"  and add / un-comment and change the swap line:
[FONT=courier new]  sudo nano /etc/fstab[/FONT]
  Add/Change: [FONT=courier new]/swapfile none swap sw 0 0[/FONT]
--OR--
[FONT=courier new]  echo '/swapfile none swap defaults 0 0' | sudo tee -a /etc/fstab[/FONT]
[*]Get the swap file's partition info:
[FONT=courier new]blkid
[/FONT]The UUID can be used as you have above or the device path.
[*]Get the swap file's partition offset:
[FONT=courier new]sudo filefrag -v /swapfile[/FONT]
Use the first extent line to get the physical offset to the file in the partition.
```
[FONT=courier new]Filesystem type is: ef53
File size of /swapfile is 19327352832 (4718592 blocks of 4096 bytes)
 ext:     logical_offset:        physical_offset: length:   expected: flags:
   0:        0..       0:  **106084352**.. 106084352:      1:[/FONT]
```
Then, [FONT=courier new]106084352[/FONT] is the physical offset.
[*]Edit the hibernate resume configuration:
[FONT=courier new]sudo nano /etc/initramfs-tools/conf.d/resume
[/FONT]Modify/Add the "[FONT=courier new]RESUME[/FONT]" and "[FONT=courier new]RESUME_OFFSET[/FONT]" lines and values:
* The "[FONT=courier new]RESUME[/FONT]" value is from the "[FONT=courier new]blkid[/FONT]" command for the partition containing the swap file.
[FONT=courier new]**RESUME=**/dev/sda1[/FONT] (or similar)
--OR--
[FONT=courier new]**RESUME=**[/FONT][FONT=&amp][FONT=courier new]UUID=<your UUID here>[/FONT]
[/FONT]* The "[FONT=courier new]RESUME_OFFSET[/FONT]" value is from the "[FONT=courier new]filefrag[/FONT]" command and is the file's offset location from the beginning of the partition.
[FONT=courier new]**RESUME_OFFSET=**[/FONT][FONT=&amp][FONT=courier new]<your offset here>[/FONT]
[/FONT]
[*]Edit the GRUB configuration to include the "[FONT=courier new]resume[/FONT]" and "[FONT=courier new]resume_offset[/FONT]" values:
[FONT=courier new]sudo nano /etc/default/grub[/FONT]
Modify: [FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **resume=**<as above> **resume_offset=**<as above>"[/FONT]
[*]Update the initramfs:
[FONT=courier new]sudo update-initramfs -u -k all[/FONT]
[*]Update GRUB:
[FONT=courier new]sudo update-grub[/FONT]
[*]Reboot
[/LIST]

Enjoy!

---

### Post by slickymaster on 2018-06-21
Ubuntu 18.04 is already released.

Thread closed

---

