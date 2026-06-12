---
title: "Virtualbox."
date: 2011-02-06
forum: Virtualisation
---

### Post by sam1981 on 2011-02-06
virtualbox giving error upon installing guest OS 
FATAL: NO BOOTABLE MEDIUM FOUND SYSTEM HALT.

---

### Post by CharlesA on 2011-02-07
Did it actually install? The error means that either:

A) The OS didn't install
B) Grub isn't loaded correctly

My guess is A. Try running the install again.

---

### Post by slooksterpsv on 2011-02-07
> **CharlesA said:**
> Did it actually install? The error means that either:

A) The OS didn't install
B) Grub isn't loaded correctly

My guess is A. Try running the install again.

I agree A is probably it, I've ran into this error before. Mine was due to corrupt data on my drive, corrupt ISOs. so I'd try to install again.

---

### Post by Paul.E.T on 2011-02-09
What it's really saying is that you don't have a bootable image file ( .iso ) in your CD or DVD.
U could have used the copy command to make the bootable CD -- will not work !
Need to make a data image file in this case an iso.  Get a special program in MS Win's to do this.  Linux has the tool.

I still haven't figured out how to use the CLI to point to a HDd iso file.  So I have to burn a bootable CD each time for a new guest OS.
  Good luck
   Tabo

---

### Post by tripados on 2011-02-09
Does anyone know how to have the Microsoft Win7 & Office 2010 licenses, or any other software licenses, carried over into the new cloned HDD in VirtualBox 4.0.2?  I am running VBox on Ubuntu 10.10 64bit.  Thanks,

---

### Post by CharlesA on 2011-02-10
> **tripados said:**
> Does anyone know how to have the Microsoft Win7 & Office 2010 licenses, or any other software licenses, carried over into the new cloned HDD in VirtualBox 4.0.2?  I am running VBox on Ubuntu 10.10 64bit.  Thanks,
They should be there already. You might have to activate them again.

---

### Post by brangkas on 2011-04-20
> **CharlesA said:**
> Did it actually install? The error means that either:

A) The OS didn't install
B) Grub isn't loaded correctly

My guess is A. Try running the install again.


i am sorry, i don't really understand  of what u r saying..
i am about to install the windows 7 in virtual box tho, but this "fatal: No bootable medium found! system halted" problem appeared so yes the OS didn't install...

now the question is how to solve this problem

thanks..

---

### Post by CharlesA on 2011-04-20
> **brangkas said:**
> i am sorry, i don't really understand  of what u r saying..
i am about to install the windows 7 in virtual box tho, but this "fatal: No bootable medium found! system halted" problem appeared so yes the OS didn't install...

now the question is how to solve this problem

thanks..

Mount the ISO, boot off it and install.

---

