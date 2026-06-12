---
title: "mpt-status cannot find disks on 7.04 Dell PE860"
date: 2009-10-30
forum: Server Platforms
---

### Post by smagister on 2009-10-30
Hi,

I'm running a Dell PowerEdge 860 with Ubuntu 7.04, 64 bit, kernel 2.6.20-17.  For unrelated reasons, I can't upgrade to the LTS 8.04 release and I can't go back to 6.06 LTS.

I recently upgraded from 6.06 LTS to 7.04 and the mpt-status command I was using to get the RAID status of my LSI Logic SAS1068 B0 RAID card no longer works. I now get the following:

```

$ sudo mpt-status

You seem to have no SCSI disks attached to your HBA or you have
them on a different scsi_id. To get your SCSI id, run:

    mpt-status -p

$ sudo mpt-status -p
Nothing found, contact the author

```

However, lsiutil seems to work, but I need mpt-status to work for monitoring reasons:

```

$ sudo lsiutil

LSI Logic MPT Configuration Utility, Version 1.47, September 21, 2006

1 MPT Port found

     Port Name         Chip Vendor/Type/Rev    MPT Rev  Firmware Rev  IOC
 1.  /proc/mpt/ioc0    LSI Logic SAS1068 B0      105      000a3100     0

```

I've looked on a bunch of forums, but couldn't find anything related. Any suggestions would be greatly appreciated.

Thanks!

Sam

---

