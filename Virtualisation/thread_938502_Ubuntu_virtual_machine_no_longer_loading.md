---
title: "Ubuntu virtual machine no longer loading?"
date: 2008-10-04
forum: Virtualisation
---

### Post by nbakewell on 2008-10-04
I've been playing with an Ubuntu VM for sometime now, loaded on an external hard drive.  Today I go to boot it up and I get this error:

> Cannot open the disk '/media/My Passport/vmachines/ubuntu-804-RH5.vmdk' or one of the snap shot disks it depends on.  Reason: read only file system.

I didn't change any configurations and nothing on my external hard drive, so I'm not sure what prompted this error.  Any ideas?

Note: this is also happening to my Redhat VM

---

### Post by bluefrog on 2008-10-05
you could check the properties/permissions of your drive as suggested in the error message...

in a console:
mount
will give you the status (rw, ro) of your drives.

---

### Post by nbakewell on 2008-10-05
/dev/sdb1 on /media/My Passport type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

---

