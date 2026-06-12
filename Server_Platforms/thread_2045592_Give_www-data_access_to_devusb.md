---
title: "Give www-data access to /dev/usb"
date: 2012-08-21
forum: Server Platforms
---

### Post by CrusaderAD on 2012-08-21
Is there a way to give the user www-data permission to /dev/usb devices? I'm trying to execute a shell script via php and it uses a usb device. Any ideas? I can run ping commands just fine.

---

### Post by Yellow Orange on 2012-08-21
What kind of access? You can create users with access to some commands via sudo without passwords.

---

### Post by kgatan on 2012-08-22
It depends on what your script wants to do with the device/devices.

If you want the script to mount the device you can define the mount in fstab with the "user" option. Otherwise only root will be allowed to mount.

---

### Post by SeijiSensei on 2012-08-22
Make sure the device is mounted at boot to a mount point to which the www-data user has write privileges.  You shouldn't be trying to write directly to a /dev device; mount the device into the filesystem first.

---

### Post by sandyd on 2012-08-22
Mount the device into a folder, and 

```

chown www-data:www-data /path/to/folder

```

---

### Post by kgatan on 2012-08-24
Since it is a php script and a removable device i would guess that you cant mount it on boot since the device wont be there. 
You should however still be able to define the mount without the auto option and set it to "user" mount in fstab. 

This will give the user who runs the php script permissions to execute the mount command on the designated folder, ex /mnt/usb.

```
/dev/<your-device>       <filesystem>         /mnt/usb       user      0         0 
```

```
mount /mnt/usb
```

Priveliges depends on what you want to do with the device. I dont think you need to set anything special unless you want to write to the device.

---

