---
title: "Luks encryption, usb key to unlock at boot. Question."
date: 2022-05-11
forum: Security
---

### Post by penciltester on 2022-05-11
Hey Folks, i'm still very new to linux and Ubuntu and was wondering if I could get some help with something i'm about to attempt. I would like to unlock my Luks encrypted system at boot with a key file on a usb thumb drive. I have found what looks to be a step by step tutorial but being a n00b i still had some questions. Here is the link to said tutorial [https://www.arminpech.de/2018/11/18/unlock-luks-root-device-on-lvm-by-an-usb-key/](https://www.arminpech.de/2018/11/18/unlock-luks-root-device-on-lvm-by-an-usb-key/) and I will follow with a section of said tutorial in which i could use some clarification.

in the following, do i include the brackets surrounding USB_DEVICE and LUKS_MAPPER_NAME when entering in the correct names or do i remove/delete the brackets? Thanks.

Format your USB device and create a filesystem on it
# WARNING: Existing data on your USB device will be erased!!!
fdisk ${USB_DEVICE} <<EOF
o
n
p
1
 
+64M
w
EOF


mkfs.ext4 ${USB_DEVICE}1
mkdir /root/usbkey-${LUKS_MAPPER_NAME}
mount ${USB_DEVICE}1 /root/usbkey-${LUKS_MAPPER_NAME}

---

### Post by TheFu on 2022-05-12
[Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it) might be helpful.  He creates a USB flash drive with encryption and sets it up to be automatically mounted from 1 machine, but not by others.

When looking for tutorials, I'd recommend that you seek sources with "ubuntu" somewhere in the domain name AND for the specific Ubuntu release you are running.  Things don't always change between releases, but sometimes they drastically change making old guides useless or even harmful.

I've never used a keyfile.  I have some Yubikey devices which can unlock my LUKS systems pre-boot using challenge-response methods.

---

### Post by #&amp;thj^% on 2022-05-12
Memory Jog great link, I remember this very well, because I did the exact same thing.
> Update: January 16, 2018 &#8211; after using one such encrypted drive for nearly a year, I accidentally filled it beyond capacity and my system locked up. I rebooted at that point, and then forward could not mount my drive. I scared myself thinking I&#8217;d broken my LUKS system, but as it turns out it was quite easy to fix.
Unfortunately I was not privy to the solution. At that time.

---

