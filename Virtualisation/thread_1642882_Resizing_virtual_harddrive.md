---
title: "Resizing virtual harddrive"
date: 2010-12-11
forum: Virtualisation
---

### Post by kfleten on 2010-12-11
I have two 10.04 servers running on a VMware ESXi 4.0. Unfortunately, I gave one of the servers to much space, and the other to little. So, I resized the harddrive in my hypervisor - giving more space to virtual server 2. Unfortunately, when logging in to server 2, it still believes that it has just 10 GB of hardrive space. How can I make the server use all the new available space I have dedicated to it from the hypervisor ?

---

### Post by Sam Lars on 2010-12-11
You may have added space to the "drive" while the old partition is still the same size.
You could expand the partition using Gparted, but I think you'd have to mount the drive on another system.
See here:
[http://communities.vmware.com/thread/140025](http://communities.vmware.com/thread/140025)

---

### Post by kfleten on 2011-01-08
Exellent suggestion. Unfortunately, my partition is LVM. Gparted can not cope with that. I found this, that helped me: [http://syslog.tv/2010/02/16/howto-guest-virtual-machine-disk-extend-online-with-debian-ubuntu-lvm2-and-vmware-esx/](http://syslog.tv/2010/02/16/howto-guest-virtual-machine-disk-extend-online-with-debian-ubuntu-lvm2-and-vmware-esx/)

I have been successful with this until the last line. I am not able to resize the LVM-root to the entire free space of the LVM-group. I booted into Knoppix, and succeded with: lvresize /dev/mapper/[name_of_LVM]-root -l+100%FREE

But, when I rebooted into the Ubuntu server, the Knoppix LVM-fix had not been saved. How can I do that ?

---

### Post by kfleten on 2011-01-15
Extend the existing volume group 
# vgextend [volume name] /dev/sda3 

Extend the existing logical volume 
# lvextend --extents +100%FREE /dev/[volume name]/root 

Check the root filesystem for defects and fragmentation 
# e2fsck -f /dev/[volume name]/root 

Extend the root filesystem 
# resize2fs /dev/[volume name]/root 

# exit 

"Reboot the system"

---

