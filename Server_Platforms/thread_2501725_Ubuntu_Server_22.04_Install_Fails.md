---
title: "Ubuntu Server 22.04 Install Fails"
date: 2024-10-18
forum: Server Platforms
---

### Post by deltaprime25 on 2024-10-18
Hello,

I recently purchased a Mini PC from Cybergeek and I would like to install Ubuntu Server on it. When I run the install I get all the way thru the menus to where it starts actually installing and then it gets to installing "Grub to target devices" and it errors out saying that there was a problem completing the install. I can install Debian Server just fine if that helps. I am not the best when it comes to linux. Here are the specs for the mini pc in case that is needed.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294388&stc=1[/IMG]
AMD Ryzen 7 (4.3ghz)
64gb DDR4 Ram
1TB NVME SSD 

[https://www.amazon.com/dp/B0CTKLPNSN](https://www.amazon.com/dp/B0CTKLPNSN)

I have no way of dumping the logs or I would provide them as well. Any help or direction would be greatly appreciated. Thank you for your time. 

-Jake

---

### Post by oldfred on 2024-10-18
UEFI install to gpt partitioned drive.
If you partitioned in advance did you add an ESP - efi system partition, FAT32 with esp,boot flags?
Grub has to have either ESP or a bios_grub unformatted partition if installing in very old BIOS boot mode to gpt drive.
You should not be using MBR(msdos) unless using Windows in old BIOS boot mode.

Post this to see drive & partitions.
sudo parted -l

---

