---
title: "Settings Notifications."
date: 2024-02-01
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2024-02-01
Is it me, or is the notifications section in settings missing printer option to turn of printer notifications.

Henry

---

### Post by corradoventu on 2024-02-01
Not only printer notifications but some other are missing on my Noble.
Filed a bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/2051945](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/2051945)
please subscribe my bug if you have a launchpad account

---

### Post by Hewjr100 on 2024-02-01
Any indication they will be restored, or does it look like they are being deprecated.

Henry

---

### Post by corradoventu on 2024-02-01
Sebastien Bacher (seb128) wrote 13 minutes ago: 			#2

Thank you for your bug report, that's a wanted change upstream to stop listing system components, see [https://gitlab.gnome.org/GNOME/gnome-control-center/-/merge_requests/1592](https://gitlab.gnome.org/GNOME/gnome-control-center/-/merge_requests/1592)

If applications are missing it probably means their .desktop Categories need to be updated
Changed in gnome-control-center (Ubuntu):
importance: 	Undecided &#8594; Low
status: 	New &#8594; Invalid

---

### Post by Hewjr100 on 2024-02-02
If printer notifacion is to be remove, there should be another way to disable printer notifications.  I do not  know about other users, but my printer is near me and I can hear it.  Also I always check paper tray occasionally and never run out of paper.

Henry

---

