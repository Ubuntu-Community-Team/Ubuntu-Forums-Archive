---
title: "[Solved]Can't install Ubuntu from pen/dvd - small size and breaks...."
date: 2017-11-22
forum: System76 Support
---

### Post by narayami on 2017-11-22
[[IMG]https://preview.ibb.co/iig3L6/23848114_1944895912392106_818974461_o.jpg[/IMG]]("https://ibb.co/ezv8nm")

I cant install ubuntu...as you can see in the image i can move the mouse and i can select but i cant see anything because the size is too small and its all bugged. i tried all options, in the "try ubuntu before install its the same..."
i have windows and created a partition, it should work fine, i used both rufus and universal usb to create the iso boot. 
i even tried the LTS and the most recent ubuntu version, i tried using a DVD and it doesnt work, my graphic card is integrated, i did the update, i changed some files from the usb and nothing works... i think i tried almos anything as i said and it wont work...
help please?

---

### Post by oldfred on 2017-11-22
What brand/model system?
What video card/chip?
UEFI or BIOS hardware & UEFI or BIOS install?

Have you tried nomodeset?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by narayami on 2017-11-23
Thank you for your fast reply.
I'm new to ubuntu so i don't understand somethigs... i know that grub menu is the boot menu right?
I have windows 10, and my video card is AMD Radeon HD 7660D.
In the menu i tried to use E but nothing happened, i realised it sais there to press tab for edit and sent me to the line to edit, i writted nomodeset and that codeline seem to work because it booted the setup but happened the same as the image...
i dont know what grub2 is... should i just writte "[COLOR=#000000][FONT=&amp]acpi_osi="?? [/FONT][/COLOR]as for the [COLOR=#000000]UEFI or BIOS hardware & UEFI or BIOS install question i just used rufus standar MBR for BIOS or UEFI (dont know if is that what are u asking).
i just wanted to start coding again, learn java on android studio and as i researched ubuntu is better for that, much faster than windows and less problems. 
im gonna try those codes you gave me.
thank you a lot.

edit: well i guess its just to edit, because it seem if i write anything and press enter boots to installation anyway, the thing is in the memory code i can edit there is no quiet splash... :(
i think im gonna give up and install android studio on windows. -.-[/COLOR]

---

### Post by oldfred on 2017-11-23
Grub2 is the Linux boot loader. Windows boot loader does not have a name.

With UEFI you have UEFI as a boot loader & its menu & grub2 with its menu. If you install a second copy of Windows its BCD becomes a boot menu also, but it will not boot Linux directly. With UEFI you can add a BCD entry to one time reboot into UEFI and boot the Ubuntu entry.

I suggested the nomodeset boot parameter. The first link was just about boot parameters
The second link shows a typical grub boot stanza and the linux line with quiet splash.

Some more examples:
[https://ubuntuforums.org/showthread.php?t=2184839&page=2&p=12871710#post12871710](https://ubuntuforums.org/showthread.php?t=2184839&page=2&p=12871710#post12871710)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by narayami on 2017-11-25
It worked! i got confused but it was pretty easy, just used the nomodeset as you said nad worked fine.
Thank you a lot!!!!

---

### Post by oldfred on 2017-11-25
Now if you have nVidia card/chip in system you should install the nVidia proprietary driver from system settings, software & updates, & tab for additional drivers.

---

