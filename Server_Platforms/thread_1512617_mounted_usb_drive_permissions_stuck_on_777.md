---
title: "mounted usb drive permissions stuck on 777"
date: 2010-06-18
forum: Server Platforms
---

### Post by fro1269 on 2010-06-18
Hello.

I am running Ubuntu Server 10.04 LTS with Kernel 2.6.32-22-generic-pae

I was originally using usbmount to autmont the western digital external usb drive I had attached to the system and it was working great. However, while I was adding files to the drive i deleted all of the directories and files that came on the drive out of box such as 'autorun.inf' and an autorun directory containing an icon for the drive.. when I rebooted the drive was no longer mounted, I tried to un/reinstall usbmount a few times but it still didnt work, so I wound up adding the drive into my fstab, my fstab line reads like this

```

/dev/sdb1       /media/Elements auto    defaults 0 0

```

now when I reboot the drive is automatically mounted ; however, the file permissions for /media/Elements and all of the subdirectories are set to file permission 777. I tried 
```

sudo chmod 755 /media/Elements

```
but it would still not change permissions, even though I did not get an error message. before when I was using usbmount the permissions were set to 755, now they are not.

---

### Post by Wayne_V on 2010-06-18
run 'df -T' to see what filesystem type it is (probably FAT).

Then see the FAT options section in 'man mount' - you probably want to set the uid/gid and maybe a mask or two.

But the filesystem should still automount without a fstab entry.  Try unplugging the drive, then "tail -f /var/log/{dmesg,messages,*log}" while you plug it back in.

---

### Post by fro1269 on 2010-06-18
'sudo blkid' returns

/dev/sdb1: LABEL="Elements" UUID="705C5DED5C5DAE9A" TYPE="ntfs"

'df -T'  returns
/dev/sdb1  fuseblk   1465135100  61400188 1403734912   5% /media/Elements

so it looks like it is formatted with NTFS, maybe that is why I can not change permissions. I will look into setting it up via uid

---

