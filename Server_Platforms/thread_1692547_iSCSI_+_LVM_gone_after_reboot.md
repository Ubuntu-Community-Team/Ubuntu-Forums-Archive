---
title: "iSCSI + LVM gone after reboot"
date: 2011-02-21
forum: Server Platforms
---

### Post by jasonsfa98 on 2011-02-21
I have an iSCSI target on my Ubuntu 10.04 LTS server that is giving me access to 3 x 2TB volumes. I am using LVM to create 1 big volume and using it as a place for my backup software to write to.

Upon initial setup I tested to see if the connection would still be there after a reboot, and it was. After going through the trouble of configuring my backup software (ZManda) and doing a few very large backups I had to reboot my SAN (OpenFiler) for hardware reasons. I took my server down while performing the maintenance and brought it back up only after the SAN work was done. Now, the LVM volume is listed as "not found" when booting.

Using iscsiadm I can see the target but LVM doesn't know of any volumes that exist using those targets. I need to get it back up and running and then troubleshoot the reboot issue.

Any thoughts on iSCSI + LVM on Ubuntu 10.04 LTS?

Thanks,
Jason

---

### Post by dtfinch on 2011-02-21
I don't have any experience with iscsi.

Does the LVM volume appear if you run "vgscan" then "vgchange -ay"?

If that worked, I'd copy /lib/udev/rules.d/85-lvm2.rules to /etc/udev/rules.d, then edit the copy to remove the part that says 'ENV{ID_FS_TYPE}=="lvm*|LVM*",', thereby causing it to run after all added block devices rather than ones udev detects to be LVM. I've had problems with the udev rule incorrectly ignoring my LVM volumes, and that fixed it for me. You might have to follow that up with "update-initramfs -u -k `uname -r`" to copy the updated config to the boot ram disk, but I can't remember for sure.

---

### Post by jasonsfa98 on 2011-02-21
Thanks for th input, but it was a no-go.

I had this issue on Suse and it was because LVM would try to come up before iSCSI and they have a patch. I had already thrown in the towel and moved to Ubuntu before I got their fix.

Back to the drawing board, but I will report back.

---

