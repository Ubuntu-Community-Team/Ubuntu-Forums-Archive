---
title: "LVM Snapshot disk use"
date: 2008-02-12
forum: Server Platforms
---

### Post by upnix on 2008-02-12
I'm using LVM snapshots to keep a 5 day history of an important file system. It works great.

However, with each snapshot, I'm making the volume size 25 gigs (for a 200 gig total disk). As I understand it, that 25 gigs is used for the changes that happen.

How can I tell how much of that 25 gigs gets used? I suspect I could get away with a much smaller size, but I'm not sure how I can tell how many gigs of changes are happening to begin with.


Thanks

---

### Post by ikonia on 2008-02-12
lvdisplay the snap shot volume you look at how many PE's are used.

---

### Post by upnix on 2008-02-12
I only see "PE"'s for pvdisplay, not lvdisplay.

The output I get is for lvdisplay:
```

  --- Logical volume ---
  LV Name                /dev/fileserver/cgysnap-fri
  VG Name                fileserver
  LV UUID                JbkAxW-yuy3-ZMT0-8QuB-oOVf-TG4E-5wPwSD
  LV Write Access        read/write
  LV snapshot status     active destination for /dev/fileserver/cgydc002
  LV Status              available
  # open                 1
  LV Size                200.00 GB
  Current LE             51200
  COW-table size         25.00 GB
  COW-table LE           6400
  Allocated to snapshot  23.92%
  Snapshot chunk size    8.00 KB
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:6

```

It looks like there's good information there, I just can't figure out what things like "Current LE" might mean.

Thanks

---

### Post by ikonia on 2008-02-12
LE is logical extent.

It's a bit different with snap shots.


COW-table size         25.00 GB

Allocated to snapshot  23.92%


%24 of your 25GB available is used up by your snap shot data.

---

### Post by upnix on 2008-02-12
That makes sense.

I really appreciate your help.

Thanks

---

