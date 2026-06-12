---
title: "160GB disk, not able to access 98GB"
date: 2024-08-08
forum: Server Platforms
---

### Post by sonofwatt on 2024-08-08
I have Ubuntu server running in Proxmox. The virtual harddrive was originally sized to 32GB, but has since been expanded to 160GB. When I run "df -h" it shows 31G. 
"sudo vgdisplay" showed 31GiB of free space, so I ran "sudo lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv" which grabbed the extra 31GiB. 
When I look at cfdisk, it shows /dev/sda3 is 158G. 

How can I expand the LV to use the rest of the space?

I followed this tutorial so far. [https://packetpushers.net/blog/ubuntu-extend-your-default-lvm-space/](https://packetpushers.net/blog/ubuntu-extend-your-default-lvm-space/)

---

### Post by TheFu on 2024-08-09
Can't really tell from what's provided, but if you used that lvextend command, did you not use the **-r** option?  That would have increased the file system size to use free space in the LV.  Without that, you need to manually resize the file system.

If you want better help, please post the command and output from these:
```
sudo pvs
sudo vgs
sudo lvs
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
```
Wrap those command and output in _forum code tags_ so the columns line up correctly.  Without that, it is too hard to help.

---

