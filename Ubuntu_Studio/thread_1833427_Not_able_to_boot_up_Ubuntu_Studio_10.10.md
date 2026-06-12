---
title: "Not able to boot up Ubuntu Studio 10.10"
date: 2011-08-26
forum: Ubuntu Studio
---

### Post by Ombudsman on 2011-08-26
Hi All,
I have installed Ubuntu Studio 10.10. I am using it for almost 6-7 months now. I see a problem now, I am not able to load up my environment. It keeps looking for hard disk. It gets fixed when I boot up a linux live distro and mount the hard disk partitions. This problem is recent. Please give some suggestions to fix the issue.
I have 2 hard drives.
1. ATA - OS and SWAP are on this disk
2. SATA - Home is on this disk.
The SATA hard disk in first on the boot priority of the hard disks.

Thanks in Advance.

P.S. :- Some times I am able to load the gdm but the home folder turns out to be blank and am not able to mount any drives in the SATA hard disk. I get the error "Could not update ICEAuthority file". This too gets fixed once I boot a live distro and mount the drives.

---

### Post by sgx on 2011-08-27
Hi, compare the file  /etc/fstab in the live distro against the
one on your system drive. See if your system created a backup of
your fstab, and compare the differences. You can revert or modify,
and maybe avoid a reinstall. There may be a separate forum here for
technical issue like this. You could try renaming the .gnome folders,
without the  .  and reinstall all of gnome files found in synaptic.

Take notes, and backup your data!
Cheers

google that iceauthority error message, its likely others have rowed the same boat before.

---

### Post by Ombudsman on 2011-08-28
Thanks for your reply sxg
I will try the steps suggested by you and get back.
I would like to share one observation:
I created a new user and is working well. I am not seeing the glitches as earlier, but I would like to continue with my earlier account.

thanks

---

### Post by sgx on 2011-08-30
google seems to point at a common permissions issue from misc updates.


updateshttp://www.absolutelytech.com/2010/01/27/solved-unable-to-update-iceauthority-on-booting/   suggests

    sudo chown username:username .ICEauthority

    sudo chmod 0644 .ICEauthority


Cheers

---

### Post by Ombudsman on 2011-08-31
hi sxg thanks,
when the problem occurs I am not able to access my home folder.
As far as the comparing files is concerned, I am not able to access /etc folder as well. Looks like my hard disk is not working properly. I will try to acquire 11.04 version of ubuntu studio and install it. Thanks for your support.

---

