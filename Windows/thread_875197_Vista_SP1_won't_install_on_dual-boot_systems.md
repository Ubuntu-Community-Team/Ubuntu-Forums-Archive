---
title: "Vista SP1 won't install on dual-boot systems"
date: 2008-07-30
forum: Windows
---

### Post by solitaire on 2008-07-30
Don't know if anyone has posted this already but Vista SP1 will not install if you are using GRUB or LILO to dual boot Vista with Linux:

[http://apcmag.com/vista_sp1_wont_install_on_dualboot_systems_microsoft.htm](http://apcmag.com/vista_sp1_wont_install_on_dualboot_systems_microsoft.htm)

> 
If you’re dualbooting Windows Vista Enterprise or Ultimate alongside a Linux distro, and have installed the Linux bootloader into the MBR, then you’re guaranteed to run into problems when installing Vista Service Pack 1, Microsoft has admitted.

The service pack has a couple of prerequisite updates and one of them, KB935509, contains an update to the Windows Vista bootloader. However, this bootloader is often replaced by open source bootloaders like Grub when installing Linux onto a system. 

Microsoft has excused itself by saying Vista SP1 contains an update to the BitLocker feature, and replacing the bootloader is a necessary prerequisite just in case the system being serviced contains a drive encrypted with BitLocker or worse, an encrypted boot partition.

However, the update performs a “chain of trust” integrity check on the system’s boot sequence, from the onboard TPM chip, through the MBR and into the operating system itself. In a dualbooting scenario where the Vista bootloader has been replaced (eg: with GRUB or LILO), the integrity check fails and the update aborts, halting the service pack installation.


Microsoft's fix suggestion...
> 
If the Linux and Vista partitions are installed on the same hard drive, you have to restore the Vista MBR, either using the Vista recovery DVD or using the MBR reinstall feature contained within EasyBCD, before installing SP1.


---

### Post by motang on 2008-07-30
Well that's not very nice, is it?  Good thing I am running Vista or else I would be pissed.

---

### Post by niyonk on 2008-07-30
Well, that's just silly!! :rolleyes:

When is M$ gonna learn.
I thought the requirements for SP1 where some drivers, all current updates...bla bla..
But, Vista bootloader :shock:

I am not very much amused really. 
Since I use Vista's bootloader for my xp and Ubuntu, I don't think I am affected.
I am using home premium, they will never get my money for Ultimate :biggrin:

Cheers!

---

### Post by rockface on 2008-07-30
Most of the time I put issues such as this down to Microsoft's sloppy quality control testing (as I did after the Zone Alarm fiasco).

But sometimes...

---

### Post by nerd0795 on 2008-08-01
Good thing, I installed Ubuntu after upgrading to Windows Vista SP1  	\\:D/

---

### Post by Naiki Muliaina on 2008-08-01
Does this effect vista home premium edition?

---

### Post by Joeb454 on 2008-08-01
> **nerd0795 said:**
> Good thing, I installed Ubuntu after upgrading to Windows Vista SP1  	\\:D/

Me too. I just had my laptop back from repair. So I reinstalled everything, and updated it fully. Then installed Ubuntu (I can never be bothered to configure grub myself)

---

### Post by niyonk on 2008-08-01
> **Naiki Muliaina said:**
> Does this effect vista home premium edition?

No, not to worry ;)
The article says that it affects versions with Bitlocker.
And only Ultimate and Enterprise have that feature

---

### Post by Thameslink on 2009-01-05
> **niyonk said:**
> No, not to worry ;)
The article says that it affects versions with Bitlocker.
And only Ultimate and Enterprise have that feature

Well It affected home premium over here, I installed
> vista home premium
> ubuntu 8.10
> service pack 1
... oh dear vista won't boot now.
Start over then.

---

### Post by halovivek on 2009-01-05
I am using vista ultimate 64 bit. Till now i did not get any problem. I hope the problem with the home version only.

---

