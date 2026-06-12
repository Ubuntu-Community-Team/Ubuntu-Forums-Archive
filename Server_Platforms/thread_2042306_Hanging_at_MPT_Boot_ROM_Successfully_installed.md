---
title: "Hanging at MPT Boot ROM Successfully installed"
date: 2012-08-14
forum: Server Platforms
---

### Post by flycast on 2012-08-14
I have a Dell Precision 690 with a hardware RAID 1 installed. 4 disks (2x 160 Gb system and 2x 2Tb data). One of the 2 Tb drives had a cable that was slightly unplugged. I noticed a few days back that the SAS utility was reporting RAID degraded.

I was running out of RAM because of the Tomcat server so I purchased new RAM and installed today. While I was there, reseated my drive cables as well. The BIOS recognized the new RAM and recognized that the previously unplugged drive was back but the machine boots and hangs at:
> MPT Boot ROM Successfully installed
I have tried removing the RAM and while the system recognizes the changed configuration it still hangs. I am certain it is not the new RAM. I tried powering down and unplugging the drive that had the bad cable connection and the SAS utility reports a degraded RAID but my system still hangs.

How can I fix this?

Ubuntu server 12.04
64bit

---

### Post by flycast on 2012-08-14
I think what is happening here is the secondary RAID drive is being rebuilt. This RAID controller does not have hot swap capability.
Ahhh patience...
> All men commend patience, although few are willing to practice it.
Thomas Kempis

---

### Post by flycast on 2012-08-15
Nope. Raid is rebuilt and it still hangs at > Dell Corp. MPT boot ROM successfully installed.
Any ideas?

---

### Post by flycast on 2012-08-15
Dell thinks it is the RAID controller. I don;t. I ran the GRUB repair utility and it is seeing all the drives. It does not see an OS on the root drive.

Here is a link to the GRUB repair results:

[http://paste.ubuntu.com/1149235/]("http://paste.ubuntu.com/1149235/")

Any help would be appreciated, I really need to get this back up and running.

---

### Post by flycast on 2012-08-17
Fixed. I used the GRUB repair utility. When the RAID disk rebuilt it must have messed up my boot records.

---

