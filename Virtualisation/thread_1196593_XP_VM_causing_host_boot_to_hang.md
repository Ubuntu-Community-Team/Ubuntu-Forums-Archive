---
title: "XP VM causing host boot to hang"
date: 2009-06-25
forum: Virtualisation
---

### Post by stubrownuk on 2009-06-25
I have 9.04 set up with a 300MB boot partition, 8GB swap and the balance of the 250GB hard drive for the main filesystem. The boot and filesystem partitions *were* ext4, but I've now reverted to ext3 because some of my diagnostic utilities can't yet cope with ext4.
The following situation occurred with the ext4 set-up as described above.
I had been successfully running Windows XP SP3 as a VM using VMware Workstation 6.5.2 build-156735. The VM had a virtual hard drive of 8GB, split into 2GB files (that being the VMware default set-up). It ran perfectly, no issues. I then increased the hard drive size to 32GB, successfully, and the Ubuntu 9.04 host re-booted without any problems.
So far, so good.
I then performed a full install of Microsoft Office 2003 and Adobe Acrobat 9 Pro within the XP VM. Installation went fine. I closed down the guest VM, closed VMware and tried to re-boot the host system. The Grub loader got as far as telling me that it was booting from my hard drive ext4 boot partition, flashed up the word "Loading" and then did nothing for the next five minutes; it did not progress to the Ubuntu load splash screen.
Since I was due to fly out of the country the next day on a business assignment, I could not afford to start messing around with things that I had no certainty of being able to diagnose, so I just re-installed the entire system from a one-day-old hard drive image. No damage done, but I'd like to know what might have caused the Ubuntu boot to hang in that way. Is it likely to be a function of the VM configuration, seeing as that was the only thing that changed between the system working and it not working?

---

### Post by stubrownuk on 2009-06-25
p.s. The Home folder on the host was shared with the VM.

---

