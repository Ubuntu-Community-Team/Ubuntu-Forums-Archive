---
title: "Problems with fstab... umount: only root can unmount /dev/sdd1 from /media/sdd1"
date: 2011-04-06
forum: Server Platforms
---

### Post by 980045 on 2011-04-06
Hi,

I've got a 1Tb USB hard drive and want to allow normal users to mount the drive, I've used webmin to edit my fstab file and its given me this.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid           0  0  
# / was on /dev/md1 during installation
# Commented out by Dropbox
# UUID=b466d8d3-2f72-4c28-ac99-067b3e3aa0cc  /            ext4  errors=remount-ro               0  1  
# swap was on /dev/md0 during installation
UUID=a430cd82-06e0-4474-81cc-74efd32bd4e6  none         swap  sw                            0  0  
/dev/sdc1                                  /media/sdc1  ext4  defaults                      0  0  
UUID=b466d8d3-2f72-4c28-ac99-067b3e3aa0cc  /            ext4  errors=remount-ro,user_xattr  0  1  
/dev/sdd1  /media/sdd1  ntfs  user,noauto  0  0

The USB drive is /dev/sdd1 which mounts are sudo root fine but wont allow me to unmount it, I get the error message below.

Can anyone explain why I cant get anyone apart from sudo root to unmount the drive.

Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sdd1 from /media/sdd1

---

