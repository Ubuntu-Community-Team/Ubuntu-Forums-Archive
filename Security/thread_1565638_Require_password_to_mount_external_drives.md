---
title: "Require password to mount external drives"
date: 2010-09-01
forum: Security
---

### Post by allaboutsam on 2010-09-01
Is there a way in Lucid to require a sudo password to mount all external drives (e.g. thumb drives, USB CD/DVD drives, USB hard drives)?

Thanks,
allaboutsam

---

### Post by sisco311 on 2010-09-07
You have to overwrite the default policykit settings. Create a .pkla file in /var/lib/polkit-1/localauthority/50-local.d/. 

i.e. 
/var/lib/polkit-1/localauthority/50-local.d/external.drives.pkla:
```

[Mounting, ejecting of external drives]
Action=org.freedesktop.udisks.filesystem-mount;org.freedesktop.udisks.drive-eject;org.freedesktop.udisks.drive-detach
ResultActive=auth_admin_keep

```

Check out:
```
man pklocalauthority
```

---

