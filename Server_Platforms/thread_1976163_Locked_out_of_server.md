---
title: "Locked out of server"
date: 2012-05-08
forum: Server Platforms
---

### Post by sirvoo on 2012-05-08
Hi All,

I have a home file server running Ubuntu 11.10 server edition.

Installed
sftp
samba 
webmin 

The server was running fine but about an hour ago the server does not start.

I was in Webmin>Disk And Network Filesystems> / (ROOT Filesystem) I ticked "yes" to Allow Users to mount the filesystem. 

After I did that everything on the list  Webmin>Disk And Network Filesystems was greyed out except for virtual memory. 

[http://doxfer.webmin.com/Webmin/DiskAndNetworkFilesystems](http://doxfer.webmin.com/Webmin/DiskAndNetworkFilesystems)


After a reboot, I plugged the monitor and it load into the screen which gives me 4 options (GNU GRUB version 1.99-12ubuntu5)

Ubuntu, with linux 3.0.0-17-server
Ubuntu, with linux 3.0.0-17-server (Recovery Mode)
Memory Test
Memory Test ( memtest86 +, serial console 115200)

if I choose the 1st option if get an error message:
mountall: mount / [641]: permission denied

Does anyone know what happened and know what I should do?

---

### Post by darkod on 2012-05-08
And if you choose recovery mode?

It's best not to allow mounting of root anyway. Create separate data partitions.

EDIT PS: Also, if you can, boot the server with a ubuntu live cd, open the root partition and post the content of /etc/fstab.

---

### Post by sirvoo on 2012-05-08
Recovery Mode will give me access to command line.

I wouldn't know what to do after that though.

---

### Post by darkod on 2012-05-08
Look what you have in /etc/fstab with:
cat /etc/fstab

The line for root should be like:
UUID=xxxxx   /   ext4   errors=remount-ro   0   1

See if your choice in webmin changed something in the boot options, whether they are still errors=remount-ro

---

### Post by sirvoo on 2012-05-08
/ was on /dev/sda1 during installation

UUID=5fe7a34b-e886-4a85-99d4-eaec64331bdc / ext4 user 0 1

---

### Post by sirvoo on 2012-05-08
/home was on /dev/sda3 during installation 
UUID=xxxx /home ext4 nosuid, noexec,nodev 0 2

---

### Post by darkod on 2012-05-08
> **sirvoo said:**
> / was on /dev/sda1 during installation

UUID=5fe7a34b-e886-4a85-99d4-eaec64331bdc / ext4 [COLOR=Red]user[/COLOR] 0 1

In this line replace 'user' with: errors=remount-ro

Exactly as it's written. Leave all the rest untouched. Save the file after the edit.

If it says something like you can't save it because it's in read only mode, you will have to boot with a live cd, open this partition, this file and edit it.

---

### Post by sirvoo on 2012-05-08
Now when i select option 1)

I get

```

[67.040296] 
radeon_cp: Failed to load firmware "radeon/R300_cp.bin" [drm:r100_cp_init] *ERROR* Failed to load firmware!
radeon 0000:01:05.0 failed initializing CP (-2)
radeon 0000:01:05.0 disabling GPU acceleration 
[drm:radeion_get_legacy_connector_info_from_bios] *ERROR* Unknown
connector type:8
 
```

---

### Post by darkod on 2012-05-08
That sounds like video issue. But at least it's trying to boot up the root partition now.

I recommend you don't enable the same option in webmin again. :)

Did you have any video issues / similar errors when installing the OS the first time?

---

### Post by sirvoo on 2012-05-08
I haven't updated the fstab file yet.

I have booted the from the ubuntu cd > try now.

I'm in the fstab file but I cannot save the file. It's telling me I don't have permission to save the file.

---

### Post by darkod on 2012-05-08
Did you open it with sudo (or gksu if using the GUI editor, gedit)?

It's best not to mount it with a click on the partition in the file manager. Instead, open terminal and mount it manually because it's easier to open it later:
```
sudo mount /dev/sda1 /mnt
gksu gedit /mnt/etc/fstab
```

That should open it in gedit with permissions to change it.

Note that sda1 needs to be unmounted before you run the first command. Either unmount it if it's mounted, or simly restart with the cd again and work only in terminal.

---

### Post by sirvoo on 2012-05-08
Thanks, it worked

---

