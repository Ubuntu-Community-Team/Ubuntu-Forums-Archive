---
title: "iSCSI files not updating until u/mount"
date: 2012-09-18
forum: Server Platforms
---

### Post by mboeschen on 2012-09-18
I have a Dell MD3200i which is connected via iSCSI to two new Ubuntu Server machines.  I have configured it using open-iscsi and multipath.  It has a partition formatted in ext3.  However, when I create or edit a file on one machine (machine 1), the other machine (machine 2) does not see it... UNLESS I unmount, then re-mount the multipath device.  Also, if I edit a file on machine 1, machine 2 still sees the unedited file, again, until I unmount and remount.  Any ideas?

---

