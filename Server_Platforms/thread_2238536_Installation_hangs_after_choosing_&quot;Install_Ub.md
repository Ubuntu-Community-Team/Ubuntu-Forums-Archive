---
title: "Installation hangs after choosing &quot;Install Ubuntu Server&quot;"
date: 2014-08-08
forum: Server Platforms
---

### Post by casper7 on 2014-08-08
Hello,
I recently bought a secondhand Supermicro Server with the following specs
 - P4SCI motherboard
 - Pentium 4 3.06 GHz CPU
 - 2x 160gb IDE Harddrive
 - 2x 1gb ECC RAM
I am co-organiser of a smaller LAN party, where we will use this server as a Radius server. We have a existing system, i just want to reinstall and reconfigure everything on this machine.

Well,
The CPU is of the architecture i386, so ofcourse i downloaded the Ubuntu Server 12.04 i386 iso file and extracted it to a USB Flash Drive with "Universal USB Installer".
It booted up, I chose my language, and I chose "Install Ubuntu Server". There, it froze. Simply dead, nothing happened.
I have tried booting with acpi=off and nomodeset. I have tried a newer ISO 14.04 x64 (I did not expect it to work, and it did not.) Same problem.
I tried booting up from a Debian netinstall image (Same usb device, also Universal USB Installer), and the exact same error occured - Well, the menu entry is just called "Install", but it hanged there.

Therefore, I suspect a hardware problem. Do any of you have a suggestion?

Thanks in advance.

Best Regards,
Casper Bladt

---

### Post by casper7 on 2014-08-09
I am still not able to install any operating system with USB thumb drives, but i succeeded to install Ubuntu Server with PXE.

---

### Post by mastablasta on 2014-08-10
since you are doing a new install it migh tbe better to use 14.04 and as it's next upgrade is due in about 5 years.

hard to say what went wrong but perhaps there is an issue with the way porgram burned the USB. so you could try again with different program such as Unebootin or if oyu have windows Lili. Yumi multiboot also seems to work well with Ubuntu

---

