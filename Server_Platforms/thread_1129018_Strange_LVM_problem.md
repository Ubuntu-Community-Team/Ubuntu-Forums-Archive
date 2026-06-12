---
title: "Strange LVM problem"
date: 2009-04-18
forum: Server Platforms
---

### Post by Sampa on 2009-04-18
My lvm device/array wont show up in /dev/vgname/lvname
It does however show up in /dev/mapper/vgname-lvname.
But it refuses to be mounted.

Also noticed im getting some file descriptor errors when issuing lvm commands.

such as pvscan:
File descriptor 6 left open
  PV /dev/sdi1          VG tvvg   lvm2 [372.56 GB / 0    free]
  PV /dev/block/254:4   VG tvvg   lvm2 [372.56 GB / 0    free]
  Total: 2 [745.12 GB] / in use: 2 [745.12 GB] / in no VG: 0 [0   ]

The second device makes me confused, it is infact /dev/sdj1 (which is in dev) but lvm wont recoqnize it as anything but /dev/block/254:4

Now if I remove /dev/block/254:4 I get this instead:

File descriptor 6 left open
  PV /dev/sdi1                    VG tvvg   lvm2 [372.56 GB / 0    free]
  PV /dev/mapper/pdc_dhhgbihag1   VG tvvg   lvm2 [372.56 GB / 0    free]
  Total: 2 [745.12 GB] / in use: 2 [745.12 GB] / in no VG: 0 [0   ]

And if I remove /dev/mapper/pdc_dhhgbihag1 I finally get the correct disk to show up.

File descriptor 6 left open
  PV /dev/sdi1   VG tvvg   lvm2 [372.56 GB / 0    free]
  PV /dev/sdj1   VG tvvg   lvm2 [372.56 GB / 0    free]
  Total: 2 [745.12 GB] / in use: 2 [745.12 GB] / in no VG: 0 [0   ]

It still wont show up in /dev/tvvg/tvlv, and the one in /dev/mapper/ cant be mounted.
And also still getting file descriptor errors.
I dont get this. 

Does anyone have a clue?

---

