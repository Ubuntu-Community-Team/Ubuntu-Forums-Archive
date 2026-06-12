---
title: "reboot after reboot after reboot"
date: 2006-08-14
forum: Server Platforms
---

### Post by chipyoung on 2006-08-14
I just installed the lamp server on my AMD K6 233 machine.  When I booted up the box after the install it would go through the bios then it would get to GRUB  , execute Grub then the screen would flash and the PC would reboot again.

I have reviewed GRUB and everything looks fine.  I am pulling my hair out over this one....someone please hurry, I am running out of hair.  

I have also checked out my bios settings, but I don't see anything that jumps out at me.  I have also tried to load Damn Ssmall Linux from a CD and it does the same thing.  I can run unbutu 5.10 live from CD and I can also run version 6.06 live from CD.

I have also Googled this issue with no results.

Any thoughts would be appreciated.

Thank you,
Chip

---

### Post by lamego on 2006-08-15
Are you trying to boot from the "Server" installed version ? The kernel installed by the server version is optimizted for newer processors, it will not run on older systems.
The best solution is to install from the "Alternate CD" and using the "server" option.

---

### Post by chipyoung on 2006-08-15
Thank you so much for the advise.  I installed the server version off of the Ubuntu 6.06.1-alternate - i386 iso.  It seems to load ok but I do receive a message when it first boots (acpi: unable to locate rsdp).  like I said I do get through this message but it has come up a number of times on other linux discs also.  It just creates about a 8 second delay.  It is annoying.  Since you sound like your the master of the older PC's, do you have any idea what this means? I have tried Googleing it but nothing difinitive comes up.

I have been running knoppix and ubuntu for about 9 months now on my other machine, In fact I have a triple boot.  I am new at the command line, but now having a server will give me plenty of practice.

Thanks again,
Chip

---

