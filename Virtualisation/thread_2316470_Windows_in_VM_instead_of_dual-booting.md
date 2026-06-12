---
title: "Windows in VM instead of dual-booting"
date: 2016-03-08
forum: Virtualisation
---

### Post by montag dp on 2016-03-08
Hi,

I currently dual boot Windows 10 on my laptop (upgraded from Windows 7, which came preinstalled).  I only use Windows very rarely, and otherwise use Linux.  I am just starting to play with virtualization and was thinking that it would be nice if I could just wipe Windows from my machine and install it in a VM with Linux as the host system instead.  I have a Windows 7 product key on my laptop and I've been searching, but I'm having trouble finding a clear answer as to whether I can use this product key to activate Windows 7 in the VM. My questions are:

1) Is it legal to use my preinstalled Windows key for a VM install?  From what I've read it seems that it does not violate the EULA, but I'd like to be sure.
2) Will I need to wipe Windows from my hard drive first in order to activate it in the VM?
3) Will I have problems activating it because, being in a VM, it will not be able to recognize that it is running on the OEM hardware?

I apologize if this has been answered already, and thanks for any help.

---

### Post by KillerKelvUK on 2016-03-08
Hey, i wouldn't rely solely on the legal advice you get on this forum especially if there is a real chance your legal position will be tested.  I'm not offering advice here but have a google around and make the best call you can... <snip>

Technical responce...

If you were to flatten your laptop, install Ubuntu and then create a virtual machine to install Windows back into then you would need to ensure the virtual machine has the same SMBIOS/ACPI information as your physical laptop.  Not easy, never done it but see here... <snip>.  As you've said your new to virtulisation I'd suggest this is overly complex and not the best intro for you, if money isn't a barrier you maybe better purchasing a retail copy of Windows 7/8.1/10 so the installation is more vanilla.

Regards wiping the original install, I don't think you would have too...I believe OEM activation is based on the SMBIOS/ACPI info and the key, no on-line lookup...you could easily limit this risk by creating the virtual machine without a network card so it couldn't 'phone home' so to speak.

---

### Post by QIII on 2016-03-08
We are not lawyers here.  We can only advise based on the EULA.  We do not allow discussions that might lead to violations of the EULA, whatever legalities may be involved in your local jurisdiction.  The reference to the article about changing the hardware signature above has been snipped, as it appears to violate the EULA.

Answers to you questions:

1.  No, you may not if the installation is an OEM pre-install.  That DOES violate the EULA.

2.  If you have a retail disk, per the EULA you may have Windows installed on only one machine at a time.  A VM is a machine, so you could not have it installed both on the physical machine and the VM.

3.  If you currently have a *retail* installation, you can remove it and contact MS to re-authorize it on the new machine.  If it is an OEM installation, they will not re-authorize.

Since this could lead to discussions of means to violate the EULA, this thread is closed.

---

