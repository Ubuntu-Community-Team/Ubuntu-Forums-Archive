---
title: "Disable access to windows partition from Ubuntu"
date: 2011-05-13
forum: Security
---

### Post by brwiese on 2011-05-13
I have a dual boot system booting Ubuntu 10.04 and Windows 7. I'm using grub2 to boot Windows 7. I would like to completely deny access to the Windows partitions in Ubuntu, while still being able to access my USB drives and my network drives. 


Thanks,
Brian

---

### Post by pastalavista on 2011-05-13
I don't believe you can completely disable access, (unless you uninstall ntfs-3g) but you can disable access by anyone but administrator. You'll need to edit [/etc/fstab]("https://help.ubuntu.com/community/Fstab") and stop auto-mount and require root permission.

---

### Post by Morbius1 on 2011-05-13
So to make that happen:

[1] Create a mount point for the ntfs partition not to mount to ( play along please ):
```
sudo mkdir /Win7
```[2] Add a line to the end of /etc/fstab:
```
UUID=51310292633543B0  /Win7       ntfs  noauto  0  0  
```*[COLOR=Blue]Note:[/COLOR]* To find the right UUID number run the following command:
```
sudo blkid -c /dev/null
```[3] Run the following command:
```
sudo mount -a
```"mount -a" won't actually do anything on a partition with a noauto option but running it will produce errors if you made a typo somewhere.

The next time you boot there will be a folder at /Win7 but it will be empty. The only way to mount it is from the command line by root.

---

