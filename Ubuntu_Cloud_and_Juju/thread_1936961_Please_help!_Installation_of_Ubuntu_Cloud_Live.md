---
title: "Please help! Installation of Ubuntu Cloud Live"
date: 2012-03-06
forum: Ubuntu Cloud and Juju
---

### Post by bamboorat on 2012-03-06
Please help! University assigned me to do Ubuntu Cloud. But I have the problem about burning installation image "ubuntu-11.10-cloud-live-amd64.img"
 

First, I downloaded "ubuntu-11.10-cloud-live-amd64.img" from here [https://help.ubuntu.com/community/UbuntuCloudInfrastructure](https://help.ubuntu.com/community/UbuntuCloudInfrastructure)
Then, I burn it by using Nero Burning ROM to a CD. 
Then, I restart my computer to startup with this CD, but it didn't boot to the CD.
 
So, I change to write it to USB flashdrive. But, it didn't work again.
 
(I already set BIOS to startup with CD and USB first)

---

### Post by shakabra on 2012-03-07
You need to make sure you use the option burn as "image". Or just use Unetbootin[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")
to make the usb bootable.

Aloha

---

### Post by bamboorat on 2012-03-07
> **shakabra said:**
> You need to make sure you use the option burn as "image". Or just use Unetbootin[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
to make the usb bootable.
 
Aloha
I'm sure that is bootable usb. I try both LinuxLive USB Creator and LiveUSB Installer, but it doesn't work.
 
Thank you for your "Unetbootin" program. But, it doesn't work with .img extension

---

### Post by Habitual on 2012-03-07
Did you md5sum the .iso and compare it to published hashes?

md5sum /path/to/iso
Should be 52d1531eeda0825838b0135951c7bbe2

Also, burn at MaxSpeed-1[FONT=Verdana]

Reference:
[http://cdimage.ubuntu.com/ubuntu-cloud-live/releases/11.10/MD5SUMS](http://cdimage.ubuntu.com/ubuntu-cloud-live/releases/11.10/MD5SUMS)
[/FONT]

---

### Post by bamboorat on 2012-03-07
> **Habitual said:**
> Did you md5sum the .iso and compare it to published hashes?
 
md5sum /path/to/iso
Should be 52d1531eeda0825838b0135951c7bbe2
 
Also, burn at MaxSpeed-1
 
[FONT=Verdana]Reference:[/FONT]
[FONT=Verdana][http://cdimage.ubuntu.com/ubuntu-cloud-live/releases/11.10/MD5SUMS](http://cdimage.ubuntu.com/ubuntu-cloud-live/releases/11.10/MD5SUMS)[/FONT]

 
Yes, I verify md5sum by using WinMD5Free v.120. And it's match.
 
Please HELP!

---

### Post by Habitual on 2012-03-08
burn at MaxSpeed-1[FONT=Verdana]
[/FONT]

---

### Post by dowdberry on 2012-03-11
After you download the image, make sure you can completely erase and reuse a thumb drive. Then "sudo dd if=/path/to/image of=/dev/sdX" where "X" is the partition that the thumb drive appears on (say sdb or sdc).

---

### Post by bamboorat on 2012-03-11
> **dowdberry said:**
> After you download the image, make sure you can completely erase and reuse a thumb drive. Then "sudo dd if=/path/to/image of=/dev/sdX" where "X" is the partition that the thumb drive appears on (say sdb or sdc).
Now, I can make bootable USB (but, on Windows 7).
Next problem: When it boots, it display the command prompt with black screen. But, I didn't know what should I do next.
 
Or, Should I make bootable USB on Linux only?

---

### Post by suoshao on 2012-04-23
Thank you for your "Unetbootin" program. But, it doesn't work with .img extension[IMG]http://www.keyforex.info/iPad.gif[/IMG]

---

