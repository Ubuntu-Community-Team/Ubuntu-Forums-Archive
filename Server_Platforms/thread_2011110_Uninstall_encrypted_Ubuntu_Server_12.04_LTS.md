---
title: "Uninstall encrypted Ubuntu Server 12.04 LTS"
date: 2012-06-26
forum: Server Platforms
---

### Post by chuvachok on 2012-06-26
I am trying to learn Linux server and installed 12.04 LTS on an older company Dell PowerEdge 840 with hardware RAID 1, 2x250GB drives, 6GB of RAM. I've used regular Linux OS before, so I am somewhat familiar with Linux. I don't know terminal commands, though.

The problem is that I selected the encrypted option. For some reason, my network card wouldn't communicate with the network inside or outside the company. I couldn't even download a GUI module. Now I would like to remove the installation completely and start over.

Can you please help me figure out how to do that?

Thanks!

---

### Post by Cheesemill on 2012-06-26
Just reinstall from the CD you used originally.

When you get to the partitioning stage you can either choose 'Use entire disk' to let the installer set up the partitions for you or select 'Manual Partitioning' and then delete the partitions from your previous installation and set up new ones.

I don't think this will solve your networking problem though, the functionality is the same whether or not the installation is encrypted.
If you want help with your networking then start a new thread with your network card details in it and we can probably help.

---

### Post by chuvachok on 2012-06-26
The problem is that the CD no longer picks up, even though it's first in the boot sequence. But I will try it again now.

I also tried removing the hard drives one by one and using them in my home desktop. They are not recognized. 

I think it all has to do with encryption.

Tried DBAN. The program couldn't format the disks.

Thank you for your response, Cheesemill!

---

### Post by LHammonds on 2012-06-26
> **chuvachok said:**
> The problem is that I selected the encrypted optionAre you talking about the option during the server install when it prompts you if you want the home directory encrypted?

I wouldn't think that would prevent you from wiping your disks and starting over.  That only encrypts the /home folder...not the entire drive/partition.   Even if you did encrypt an entire drive, that should only prevent people from accessing / unencrypting the data.  It should not protect from being erased.

If your CD is 1st in the boot sequence, the most-likely problem is that you may still need to press a certain key to boot from the CD.  It is possible the CD is messed up and no longer recognized as a bootable device or that the drive is physically not working.

LHammonds

---

### Post by chuvachok on 2012-06-27
Absolutely! That's why I am confused. I've tried two separated downloads on separate disks now. And it's not like I don't have my passwords or the encryption key. The CD is still first in the sequence, but I just don't know how to get it recognized. DBAN, for example, boots from CD without any problems. I tried Ubuntu 12.04 and Debian 6.0.5. The boot process skips right over the OS disks and ends up at the GRUB screen.

Thank you, LHammonds!

---

