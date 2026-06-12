---
title: "Ubuntu 18.04  under Vmware workstation 14 how to expand the root partition?"
date: 2018-08-22
forum: Virtualisation
---

### Post by deepakdeshp on 2018-08-22
Hello,
I need to expand the a1 partition for UBuntu 18.04 which is under Vmware workstation 14. sda1 is the root partition.
I tried to create the gparted usb and was able to boot it in Vmware environment. But it wasnt able to see the vmware sda disk .
My partition table is as follows.

```
Number  Start   End     Size    Type      File system     Flags        32.3kB  1049kB  1016kB            Free Space
 1      1049kB  20.4GB  20.4GB  primary   ext4            boot
        20.4GB  20.4GB  1048kB            Free Space
 2      20.4GB  21.5GB  1072MB  extended
 5      20.4GB  21.5GB  1072MB  logical   linux-swap(v1)
        21.5GB  32.2GB  10.7GB            Free Space



```

Please advise.

---

### Post by deepakdeshp on 2018-08-23
Please let me know if you require any other details.

---

### Post by deepakdeshp on 2018-08-25
Bump

---

### Post by KillerKelvUK on 2018-08-25
Did you boot the gparted usb in a different guest to the one whose disk you wish to re-partition?  Your approach was sound so odd that you say you couldn't see it.

---

### Post by deepakdeshp on 2018-08-25
Since I have to increase the root partition, I can't boot the VMware guest and then mount the gparted usb. Somehow I have to boot the gparted USB without booting the guest.

---

### Post by KillerKelvUK on 2018-08-26
So you need to add the USB gparted device to your guests config and set it as a bootable device. That way the guest boots from the USB not local disk so you can then manage the root partition...same principal as if you were doing this on a physical PC

---

### Post by deepakdeshp on 2018-08-26
> **KillerKelvUK said:**
> So you need to add the USB gparted device to your guests config and set it as a bootable device. That way the guest boots from the USB not local disk so you can then manage the root partition...same principal as if you were doing this on a physical PC

Thank you. I have downloaded another program, started it as a virtual guest program. Which helped me boot the gparted USB inside the vm.
Now I can see only the programs her and gparted hdd. I can't see the hdd I want to expand

---

### Post by KillerKelvUK on 2018-08-26
Please can you dump your guest configuration from VMware Workstation so we can see it?

---

### Post by deepakdeshp on 2018-08-26
> **KillerKelvUK said:**
> Please can you dump your guest configuration from VMware Workstation so we can see it?
Excuse my lack of knowledge. But do you mean memory dump of the guest? I googled VMware guest memory dump but didn't get anything satisfactory.

---

### Post by deepakdeshp on 2018-08-27
I was able to access the BIOS using [https://kb.vmware.com/s/article/1004129](https://kb.vmware.com/s/article/1004129)
I used this to access the bios but it does not have any device related to my USB which has the gparted. So in setup I cant set the booting device number 1 for USB and 2 for HDD

---

### Post by deepakdeshp on 2018-08-27
I went to settings and attached the gparted.iso to the cdrom, ticking option to start cdrom at power on. THis has helped solve the problem.
Thanks all for your time and help!

---

