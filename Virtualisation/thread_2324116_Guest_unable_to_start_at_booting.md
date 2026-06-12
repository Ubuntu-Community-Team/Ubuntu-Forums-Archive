---
title: "Guest unable to start at booting"
date: 2016-05-11
forum: Virtualisation
---

### Post by satimis on 2016-05-11
Hi all,

Host  Ubuntu14.04 desktop
VM  Ubuntu16.04 desktop
Oracle VirtualBox

VM fails to start with following warning```

rc.local /sbin/mount.vboxsf mounting failed with the error no such file or directory

```

Please help.

Regards
satimis

---

### Post by MAFoElffen on 2016-05-12
Lets me ask: Did you install your VM to a removable device?

---

### Post by satimis on 2016-05-12
> **MAFoElffen said:**
> Lets me ask: Did you install your VM to a removable device?
Hi,

Sorry I don't follow.

The VM is installed on the HD, a SSD. of the PC.  It has been working before.  The last action taken by me was to make it sharing data with the host. 

I have added following line```

mount -t vboxsf Transfer_Directory_PC1A /home/satimis/Transfer_Directory_PC1A

```
to /etc/rc.local 

-> Settings
Share folders has been created;
Folder Path	/home/satimis/Transfer_Directory_PC1A
Folder Name	Transfer_Directory_PC1A
[check] Auto Mount

I still couldn't read "sf_Transfer_Directory_PC1A" directory.  It has been mounted.
(now it comes to my understanding that I haven't added user "satimis" to /etc/group under) ```
vboxsf:x:999:satimis
```

Then I was fiddling around and suddenly I could restart the VM.

Is there any way to rescue it without running the Live CD?

Thanks

Regards
satimis

---

