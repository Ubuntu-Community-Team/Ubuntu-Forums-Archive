---
title: "Viruses and the MBR"
date: 2010-07-15
forum: Security
---

### Post by Steve R. on 2010-07-15
I have a dual boot computer.  The WindowsXP "side" has been infected with a rootkit virus. So far UBUNTU has not been affected to my knowledge.  I have not yet removed the virus from the WindowsXP "side". I am thinking of deleting the NTFS partition and have the computer fully dedicated to UBUNTU.

Now for my question. **Is there a possibility that the virus resides in the MBR and that I need to "rebuild" the MBR** to actually remove the virus?

Even more extreme, should I totally re-install UBUNTU in the name of safety and precaution.

---

### Post by wacky_sung on 2010-07-16
It depend on what type of virus in which you got infected with to affect your master boot record (MBR).It is rare to find virus causing damage to your MBR.

Just a piece of advise,i never like to dual boot Linux with Window as Window is unsecured in design in many ways.If you wanna dual boot with other distro of Linux and it still working fine.The best is to use only one OS type on a single hard disk otherwise it will depreciate the life span of a hard disk over a span of time.

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by OpSecShellshock on 2010-07-16
If you don't know for sure whether the MBR's been affected by the malware or not, and you already intend to remove Windows from the disk anyway, you might just as well zero the whole thing and reinstall. To be honest the only Windows malware I commonly see people get that also hoses the MBR is Torpig/Mebroot, but I'd imagine there are unidentifiable ones out there as well. But as I said, if you're removing Windows anyway there's no harm reinstalling everything.

---

### Post by Steve R. on 2010-07-16
Thanks.  I didn't have anything important on the Windows "side" so it would be no big loss to discard it. A Ubuntu re-install, beyond the operating system itself, would be a bit more involved.

---

