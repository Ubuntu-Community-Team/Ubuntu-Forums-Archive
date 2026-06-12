---
title: "Grub fails to load"
date: 2008-06-27
forum: Windows
---

### Post by sri1025 on 2008-06-27
This is what I did:

1) I installed XP first, then
2) I installed Xubuntu on a different partition, and then
3) I booted Windows and deleted Xubuntu partitions (swap and main)
4) I rebooted my machine

That's it, everything got screwed up. When the booting happens grub says:

Error 17

All I wanted to do was uninstall Xubuntu (I mean, on this machine. I don't mean to go back to XP completely). I obviously uninstalled Xubuntu in a wrong way. Looks like deleting the partition is not the way to do. So, this is what I want now. I want to boot my XP back.

Could some guide me or point me in the right direction? And, if I install Xubuntu back again, both the OS starts working. How do I uninstall Xubuntu but keep my XP?

Thanks!

---

### Post by PmDematagoda on 2008-06-27
The problem you caused is that you removed the GRUB configuration files in the process of removing Xubuntu, do you have the Windows install CD? You can boot that, choose the Recovery Console and restore the Windows MBR back on. If that doesn't work, or if you don't have the Windows install CD, then download the [Super GRUB CD]("http://forjamari.linex.org/frs/download.php/987/super_grub_disk_0.9726.iso"), burn it onto a CD, boot the PC using it and use it to recover the MBR.

---

### Post by maestrobwh1 on 2008-06-27
EDIT: I went to reply but PmDematagoda is much more concise and finished before I was done:-)

I'll leave this here for other info:

I am assuming that with error 17, you don't even get your grub OS list.  I did this once as a newbie... deleted the install partition.  Several years later I intuitively know this: The issue is that Grub installed as your bootloader, and it stored the config files in your Xubuntu partition: those are not there anymore obviously.  

If you have your "regular" XP install CD, you could also boot from that and use the recovery console option/fix MBR.  It will usually reinstall the MS bootloader if it finds that missing.

If not: Boot off of your original Xubuntu and last I knew, there was a "repair" option.  Follow through the logical steps and you might at least be able to get XP back?  I think there is even an option to boot off the first partition and it might be able to load XP... 

If that fails, there is a "Grub Superdisk" iso on the internet that creates a bootable grub CD that can get you into your operating system(s).  I think it can even restore the MS MBR (master boot record).

There are several options, but if these options fail, you'll need to reinstall Xubuntu or some flavor of Ubuntu.  You'd have to leave it, though I imagine, you could boot into a live linux distro (slax, knoppix, etc), remove all but the /boot/ folder and resize that partition using gparted to some really small size to get your space back.  I know knoppix has qtparted as part of it's distro.  

This is no slight to you, but you seem not too knowledgeable regarding all of this.  Be careful and do the "least" approach to fix the problem.

---

### Post by sri1025 on 2008-06-29
Thanks to both of you.

The super grub disk worked beautifully.

---

