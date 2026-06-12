---
title: "Jammy won't accept full disk luks encryption password"
date: 2023-05-10
forum: Security
---

### Post by bulgin on 2023-05-10
Hello, and I hope everyone is safe and healthy.

See attached 3 screen shots for geometry of dual boot system jammy 22.04 and windows.

I wanted to change the password for the boot and jammy partition using instruction here:

[https://www.cyberciti.biz/security/how-to-change-luks-disk-encryption-passphrase-in-linux/](https://www.cyberciti.biz/security/how-to-change-luks-disk-encryption-passphrase-in-linux/)

Doing so was successful using those instructions.

However, now there are two entries that must be entered when re-booting (which was how it was before, too): the one to boot the system which accepted the new password and the one to gain access to user directory **which is not being accepted**.  This was the usual boot sequence which previously worked and now does not grant me access to user directory.

However, running ubuntu 22.04 off of a thumb drive I can access the user directory and can see all files and manipulate those files when booted on the virtual system, from command line prompt.

Suggestions

Thanks

---

### Post by TheFu on 2023-05-10
By default, Ubuntu uses LVM when setting up LUKS encryption.  This is an enterprise volume manager.  Simple partitions are just part of the containers used by LVM.  LVM is what's important.  Because there's only 1 LUKS container, everything inside that container is encrypted.  This makes it convenient - only 1 disk unlock is needed.

To see the storage information after the LUKS container is unlocked/opened using cryptsetup (or by the OS during boot), use these commands:
```
sudo pvs
sudo vgs
sudo lvs
```
Below is an image trying to explain the LUKS/LVM layout. Hope this helps.

I suspect you are confusing 2 passwords.
a) LUKS open/unlock passphrase  - this opens the storage
b) end-user login password - this logs in with a username. Doesn't have anything to do with encrypted storage.

If there are issues accessing storage once the LUKS container is "opened", then normal Unix file permissions are likely the problem.

Lastly, hiding of UUIDs isn't really needed. They aren't special, just unique.  There's nothing anyone can do with the information. Same for the LUKS name. Nothing special about it.  Of course, you can choose to hide that stuff, if you like.  Doesn't hurt to hide it, not really worth the effort, IMHO.

---

### Post by bulgin on 2023-05-10
Thank you TheFu.  This is very useful.

I did know that the LUX and files are different entities, but couldn't figure out why, after succesfully getting past LUX with the LUX password, I couldn't open the files and I know I was using the correct password.  Thanks for the tip, also on the images.  Next time that'll save me image manipulation time.

If normal linux file permissions are the problem how does one go about solving that if they can't get into the system?

I eventually was able to get access by following the tutorials here and here:

[https://support.system76.com/articles/password/](https://support.system76.com/articles/password/)


[https://www.cyberciti.biz/security/how-to-change-luks-disk-encryption-passphrase-in-linux/](https://www.cyberciti.biz/security/how-to-change-luks-disk-encryption-passphrase-in-linux/)

Maybe you can advise me wherein those steps I've gained access to the file system wherein I was able to make a new password and ultimately gain access.

Thank you for your feedback it was very useful.

Have a great day.

---

### Post by TheFu on 2023-05-10
I don't know what LUX is.  LUKS is the encryption used with dmcrypt on most Linux systems.

If there are issues with any system, then use a Try Ubuntu (iso) flash drive and manually fix things.  From there, you'll unlock the crypt container (usually on sda3), then tell LVM to activate all PVs, VGs, and LVs, then mount the LV storage locations as needed, probably under /mnt/ somewhere.  Then you can use the normal chroot techniques to change the password for the user you want.  There are how-to guides for doing the chroot.  These typically don't say anything about LVM or encryption.  For many people, it is just easier to do a new install, since that usually takes 15 minutes, then require their HOME directory files, and re-install all the manually installed applications.  What works best for you - depends.  Whenever using encryption, having excellent backups is not optional.  It is required.

---

### Post by bulgin on 2023-05-10
Yes, thank you.  Got it now!

Have a great spring and summer!!!!

---

### Post by TheFu on 2023-05-11
I have some of the manual commands in my notes.  Your system will be different, but here are the ones for an older system here:
```

# sdf5 is the normal partition that contains the LUKS container. c720 is the "name" of the LUKS container
sudo cryptsetup luksOpen /dev/sdf5 c720

# Need some temporary directories to mount things
sudo mkdir /mnt/root /mnt/Stuff

# Activate the LVM VGs
sudo vgchange -ay

# Mount any LVs that you need from inside the encrypted storage  - it might be easier to use /dev/{vgname}/{lvname} links than the mapper links. YMMV
sudo mount /dev/mapper/c720--vg-lv--Stuff /mnt/Stuff
sudo mount /dev/mapper/c720--vg-root /mnt/root
```

After commands similar to those you'll still need to setup a chroot to change the passwd.  I always have to look  up those steps on my tablet. Remember, the goal of the chroot is just to use the installed OS and to have access to the system programs, system boot files, and system settings AFTER we've already booted.  [https://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation](https://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation) has a guide.  Ignore the Arch/Gentoo stuff. Any Ubuntu ISO for the same release can be used to boot into a "Try Ubuntu" environment.  I always have an old 8GB flash drive laying around with Ubuntu-Mate on it for emergency use like this.  The key is that the OS version on disk and the OS version on the flash drive need to be for the same release ... say 20.04 on both or 22.04 on both.

When you know what you are doing, fixing a corrupted boot issue takes 5 minutes, assuming zero hardware issues. The first time, it will take longer.  This is also how we can access log files on a system that won't boot for troubleshooting needs. ** Lots of uses of the Try Ubuntu + chroot setup.**

---

