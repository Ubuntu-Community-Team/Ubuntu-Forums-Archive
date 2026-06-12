---
title: "P2V Failed (Error message attached)"
date: 2014-08-25
forum: Virtualisation
---

### Post by shadin2 on 2014-08-25
Hi there
I want to convert physical Ubuntu 12.04 to a virtual server using VMware converter 5.5.2 


you can see in the following image the hard disk settings for the physical server in the conversion wizard


[IMG]http://i.stack.imgur.com/IeOY2.png[/IMG]




after the conversion complete I tried to power up the converted one but this is what I got 


[IMG]http://i.stack.imgur.com/ncrSC.png[/IMG]

Would you please advise me how to fix it
Thank you

---

### Post by KillerKelvUK on 2014-08-25
Doesn't necessarily look like your P2V has failed...you're at an EFI Shell which is asking you to point to the efi bootloader for the OS.  The default path for Ubuntu's efi (at least on mine its the default) is /boot/efi/EFI/ubuntu/grubx64.efi, you should be able to browse to the same file on your install via the shell and execute the efi which should start the OS.  If you put the /boot mount in a different partition on the physical disk then you'll need to find the correct device mapping to use in the shell e.g. blk0...blk4

Permanent fixes for this are possible by editing the EFI to point to the grubx64.efi, couple of ways to do this but in a virtual image I've less experience however one way would be to edit the startup.nsh file the shell itself is referring to and adding the path to grubx64.efi.

Alternatively if the physical was a legacy boot from BIOS you may not have a grubx86.efi, so disable the EFI option in the VM guest config.

---

