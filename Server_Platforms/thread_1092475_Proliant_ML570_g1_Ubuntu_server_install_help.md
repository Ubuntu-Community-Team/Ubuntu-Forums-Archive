---
title: "Proliant ML570 g1 Ubuntu server install help"
date: 2009-03-10
forum: Server Platforms
---

### Post by tomarcom on 2009-03-10
I am having trouble loading Ubuntu server 8.10 on a proliant ML570g1.  It looks like there is a problem with the compaq raid controller,  durring installation I do not get any errors and the raid does show up.  Has anyone ever loaded Ubuntu on this server?, Does anyone know of or have any links to documentation for howto do this?

---

### Post by Nxion on 2009-03-10
I don't quite get what you are asking. Are you looking for a guide on how to install Ubuntu for your specific server or are you having issues with the RAID controller?

---

### Post by tomarcom on 2009-03-10
yes specific to ml570g1  Install completes without error, however it will not boot.  I was able to get it to boot using super grub, but lots of errors during boot. Anyway now I can login at least.

---

### Post by Nxion on 2009-03-10
Can you remember the errors you were getting?

---

### Post by delalom on 2009-03-10
It has been 2 days I'have been trying to find a fix for this issue. I also have a Compaq Proliant ML570 G1 xeon and the install went fine with ubuntu server 8.10. After reboot the server displays something like "no boot device error ... strike a key.." I event found this : [http://ubuntuforums.org/showthread.php?t=82466](http://ubuntuforums.org/showthread.php?t=82466) and applied it without succes. how did you install supergrub tomarcom? What are the error you are having on boot?

---

### Post by tomarcom on 2009-03-12
delalom- There is something not working with the default setup of grub for us.  I was able to get it to boot up by, durring install, manualy set up the disk partition to have 50mb /boot, 800mb for swap and what ever for /.  be sure that you create the boot patition at the begining of the disk. "AUTO PARTITIONING MAY ALSO WORK I JUST DID NOT TRY IT". Complete the install, then you can try to boot it up and get your error "Non-system boot disk".  Download and burn a supergrub cd, boot with it and then run the FIX EXISTING GRUB BOOTLOADER.  Super Grub did it's thing rebooted and my ML570 spits out that some stuff Failed at boot up but it does come up to a logon screen at least.

---

### Post by delalom on 2009-03-12
Tomarcom yes I figured it out. The auto partitioning did not work as well.
I have to create my own partition and tell Grub where the boot partition is.

I also have these error when I boot my server and to resolve them I added in /boot/grub/menu.lst line defoptions = noapic noapci and then run update-grub.

Thanks.

---

