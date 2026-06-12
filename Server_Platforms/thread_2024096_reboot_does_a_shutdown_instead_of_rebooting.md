---
title: "reboot does a shutdown instead of rebooting"
date: 2012-07-13
forum: Server Platforms
---

### Post by bitbuck3t on 2012-07-13
I have a supermicro board with a SSD drive and I just installed 12.04 x64 server.  Anytime I type reboot, or shutdown -r the system halts and powersoff.  This is problematic because I'm getting ready to deploy this to a datacenter and I would rather not have to manually push the power button everytime I need to reboot the machine.

I have searched the internet and found a post suggesting that you can pass a reboot=efi (or acpi,pci, and a few other options) in grub and it may fix the problem, however none of these options worked for me.  Any help would be appreciated.

---

### Post by bitbuck3t on 2012-07-17
Has anybody else at least experienced this?

---

### Post by thomasberger on 2012-07-19
Yes, I experience the same thing.  Running supermicro with SCSI disk (HW Raid controller).  Same behaviour on mulitple machines.

---

### Post by Churnd on 2012-07-21
Count me in... I'm having the same problem.  Supermicro X9SCA-F board w/ Crucial SSD drive running Ubuntu 12.04.  Reboot shuts down.  I was about to file a case with Supermicro, but did some googling & saw this.  I haven't tried modifying grub, but the motherboard isn't in EFI mode so I don't see how that'd help.  I think it's more a Ubuntu problem.

---

### Post by bitbuck3t on 2012-07-21
This is at least related to Ubuntu because the machine I bought came with Fedora installed and I was able to reboot that without an issue.  I also have another one of these with OpenBSD installed and that reboots fine as well.  I did go into the BIOS and set one of the boot options from "UEFI and Legacy" to just "Legacy" but no luck.  I may try reinstalling now that I made that change, but I would like to actually figure out what is going on rather than just blindly trying things.

I'll update this thread if I find a solution.

---

### Post by thomasberger on 2012-07-22
I have a work-around. That is to black list the MEI driver. Putting  this into /etc/modprobe.d/blacklist.conf  seems to make my systems reboot properly:

[I]
# Make system reboot
blacklist mei
[/I]

I do not know of any potential issues with this but it seems like MEI driver is a useful thing to have. Not sure what applications would suffer from its removal.  At least is my IPMI interface still working as expected!

---

### Post by bitbuck3t on 2012-07-24
Blacklisting mei seemed to work for me too.  Thanks so much for the reply.

---

### Post by Churnd on 2012-07-25
> **thomasberger said:**
> I have a work-around. That is to black list the MEI driver. Putting  this into /etc/modprobe.d/blacklist.conf  seems to make my systems reboot properly:

[I]
# Make system reboot
blacklist mei
[/I]

I do not know of any potential issues with this but it seems like MEI driver is a useful thing to have. Not sure what applications would suffer from its removal.  At least is my IPMI interface still working as expected!

Just verifying this worked for me too.  I'm interested to know how you found it out.

---

