---
title: "Tripple boot with full disk encryption"
date: 2012-05-24
forum: Security
---

### Post by CaptinCaveman on 2012-05-24
Hi, 

I have been trying to make a tripple boot system with each OS having full disk encryption and i am having no luck. 

I would like to have Ubuntu 12.04, Backtrack 5 and Windows 7 all bootable from one hard drive. 

I think for the encryption i need to have Backtack and Ubuntu using LUKS and Windows using truecrypt but I am having trouble with getting grub to see Ubuntu and Backtrack and let me pick between the two, though i could be wrong in my thinking.

Any help would be much appreciative 

Thanks

Captin

---

### Post by ottosykora on 2012-05-26
I am not an expert on this special subject, but under whole disk encryption I understand a system where the **whole** disk is encrypted and not just one partition.
What you are talking about is not a whole disk encryption, but only a partition encryption. This can not work, as each partiton would also need to decrypt other os partition to find the boot files there.

Whole disk encryption, like commercial products offer, will encrypt all partitions and all contents of the hard drive completely and will be not dependent on any operating system at all.

I did not use it for long time, but AFAIK Truecrypt offfers something like that- It will probably need to be installed before any os on the machine.

How such encryption system will cooperate with grub (also having its part in MBR) is difficult to say.

Grub first part in MBR will try to search for its second part in a partition and if this is encrypted it will not find it, so it will not boot.

---

### Post by Blackbird_13 on 2012-05-27
You shouldn't encrypt the boot partition. I have sda1 as a boot partition which boots luks encrypted logical volumes for root home swap (ubuntu 12.4).In principle, I see no reason why you can't use another luks partition for linux operating system no 2. No idea about encrypting windows, but I assume grub should be able to boot it as for windows on a plain partiiton. I knew nothing about luks/lvm but quickly got everything up and running by following a couple of tutorials. I can give you some links if you are interested

---

### Post by CaptinCaveman on 2012-05-28
Hi thanks for all you feed back,

links would be a great help thanks,

I think i can do the windows bit pretty easily with truecrypt and that should allow me to pick between to boot to windows or open up grub. 

Just couldn't find a away to pick between 2 luks partions to boot off of, or get it to show grub and not the text "(initramfs)"

Cheers

---

### Post by Blackbird_13 on 2012-05-28
The tutorial I followed when I first tired full disk encryption was: [HTML]http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04[/HTML]The tutorial is quite old but pretty clear. I also cross referenced with this site for setting up swap and using a key file.
[HTML]https://help.ubuntu.com/community/EncryptedFilesystemHowto3#Encrypted_Swap[/HTML]I experimented in virtualbox before setting up a live system and now find I can do an install automatically. If you are interested in lvm as well let me know.

---

