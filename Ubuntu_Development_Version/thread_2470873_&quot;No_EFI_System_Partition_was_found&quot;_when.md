---
title: "&quot;No EFI System Partition was found&quot; when installing on BIOS/non-EFI VM"
date: 2022-01-14
forum: Ubuntu Development Version
---

### Post by &amp;KyT$0P# on 2022-01-14
Trying to install Xubuntu 22.04 in a Virtualbox VM for pre-release testing.  EFI is not enabled in this VM, so I set up the virtual disk as gpt with two partitions: a 2 MB partition (to be bios_grub) and the rest of the disk a single partition (to be ext4 /).  But after configuring the "Something else" partition layout screen and clicking Install Now, the installer says "No EFI System Partition was found.  This system will likely not be able to boot successfully, and the installation process may fail.  Please go back and add an EFI System Partition, or continue at your own risk."

Does 22.04 actually now require an ESP in non-EFI environments?  If so what for?  Or is the warning erroneous?

I did try clicking through continuing the install anyway, and didn't notice any problems with the installed system, but not sure if that just means the issue(s) are subtle?

---

### Post by &amp;KyT$0P# on 2022-01-21
bump.

I found the git repo for the ubiquity installer which I believe is what Xubuntu uses, and found in the source code where this message is coming from.  But as far as I can tell from git logs, that code hasn't changed compared to 20.04 where this doesn't happen.  Maybe this is caused by something outside of the installer?  Where else to look?

---

### Post by makitso on 2022-01-22
I was testing 22.04 on an older Thinkpad that has BIOS.  This statement in the installer threw me for a loop. Finished the install, booted and no dual boot partition and then the desktop hung.  The lack of OS PROBER and intel_iommu=off to keep from hanging were challenging.

---

### Post by &amp;KyT$0P# on 2022-08-24
Bit late given that I started this thread in "Ubuntu Development Version", but happened to see [this post]("https://ubuntuforums.org/showthread.php?t=2478340&p=14109550#post14109550") today which I think explains it and answers my questions here.

---

