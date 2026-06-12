---
title: "secure boot ubuntu"
date: 2013-02-25
forum: Security
---

### Post by ggankhuy on 2013-02-25
Recently found the following article saying Ubuntu 12.10 supports now the secure boot and comes with a bootloader with CA signed by MSFT. It does not give much detail on deployment on a system with secure boot enabled. I also not sure whether server or desktop version or both supprots secure boot. On ubuntu website itself, I am not finding any information. Has anyone explored this avenue? I would specifically like to try isntalling it in secure boot mode enabled system. 
Thanks!

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)

---

### Post by oldfred on 2013-02-25
There is controversy with Secure Boot as that is a Microsoft requirement with new computers pre-installed with Windows 8. These computers are all UEFI with gpt partitioning. There is no secure boot in BIOS and most older UEFI installs do not have a way to turn secure boot on. 

If you have a new Windows 8 system you need the new version of Ubuntu to be able to install with secure boot. But many hardware vendors have not implemented UEFI correctly and even with the grub shim file that has the Microsoft key you may have issues installing Ubuntu.

Some say secure boot does not add to security and is just a way for Microsoft to make it more difficult to install other systems. But it seems to be more that many UEFI systems are not created per the UEFI standard.

       Protection against Samsung UEFI bug merged into Linux kernel
[http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html](http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html)
Since these patches have not yet been integrated into the installation media for these distributions, users should always use the UEFI firmware's Compatibility Support Module (CSM), which emulates a BIOS mode, when booting on affected laptops. 
The current state of UEFI and Linux = Feb 1, 2013 - Matthew Garrett
Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)
New Linux UEFI boot loader
[http://mjg59.dreamwidth.org/23113.html](http://mjg59.dreamwidth.org/23113.html)
Matthew Garrett
[http://www.zdnet.com/linux-developers-working-on-uniting-windows-8-secure-boot-fixes-7000011094/](http://www.zdnet.com/linux-developers-working-on-uniting-windows-8-secure-boot-fixes-7000011094/)
James Bottomley's random Pages - Linux Foundation Secure Boot System Released
[http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/](http://blog.hansenpartnership.com/linux-foundation-secure-boot-system-released/)

---

### Post by ggankhuy on 2013-03-05
thanks it looks pretty messy now. Articles says users shold stay away from shim as they are for advanced users. I am test environment, need to be able to try this. I found the svn lhttp link containins shims I see bunch of tgz and tar file. I wonder if there is any instruction somewhere to integrate the keys into firmware UEFI BIOS and successfully deploy linux O/S-s. Thanks!

---

### Post by oldfred on 2013-03-05
I think one of the blog's I linked to above, discuss the issue of compiling your own key is very complex. You have to buy your own key for about $100 with what every documentation that you are valid to buy a key. And then compiling it requires a lot of special software.

With Ubuntu you just install in UEFI mode and if  a secure boot system it will install shim so it has the Microsoft key to boot with. 

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by ggankhuy on 2013-03-13
OLDFREd, I actually have a sony with secure boot enabled. I purchased it around new year 2013. Tried both fedora 18 and ubuntu 12 both installed fine. Meaning the KEK must have contained the signed hash or signature of these two ubuntus. Other ubuntu distro-s would not isntall saying "installation fails due to unsigned" etc.

I wonder how it also plays out in PXE boot environment. Meanining if we try installing from PXE boot server how the secure boot will handle this.
I tried this in qa environment using wireshark and noticed for Windows Deployment Server first file uploaded through tftp is boot\x64\wdsmgfw.efi next file is boot.vim and for Linux PXE server it is BOOTX64.efi (RHEL). After that vmlinuz and initrd.img loads. In this case which file would need to be signed I wonder.

---

### Post by oldfred on 2013-03-13
I thought I saw somewhere that PXE does not currently boot with secure boot on.

The new signed kernel on the installer is now vmlinuz.efi so the installer knows it is a signed kernel. That kernel will also install to BIOS mode systems.

---

### Post by mathias j sagartz on 2013-03-13
I just installed 12.04.2 on my 5 month old HP desktop using a LiveCD.  The install was done with secure boot enabled and it went pretty smoothly.  Rebooting after the install was something else.  During the install I enabled updating and so when all was over I had 3 kernels and naturally Grub set the menu  to boot the newest one.  

Problem was that only the oldest kernel, the one that came with the LiveCD disk, was signed -- I assumed this was the case because only that kernel's image had an ".efi.signed" in it's file extension.  When I tried to reboot the system using a newer (presumably unsigned) kernel the machine froze and needed to powered off to be rebooted.  Using the Grub menu I was able to boot Windows 8 or the oldest linux kernel.  

After I figured out how to disable secure boot I was able to boot Windows 8 or any of the linux kernels.  

So is this the way it's going to be, i.e. each new kernel needs to be signed to be usable with a secure boot enabled system?  Should we just disable secure boot and forget about it?

---

### Post by oldfred on 2013-03-13
@mathias j sagartz

Very interesting & maybe why some others are having issues. 

I think you should report the bug.
       bug reports info on how to do:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

    
Not sure if it is UEFI, updating or the kernel where it should be reported.
Somewhat related but both are incomplete so not sure what they are:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1098952](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1098952)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1130834](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1130834)

---

### Post by mathias j sagartz on 2013-03-14
I need to modify my last post slightly after looking carefully at the files on the LiveCD I used to install 12.4.2 and also on my installation.  

After completing my install I said that I had 3 kernels, but in looking at the files in my /boot folder I had 4.

vmlinuz-3.5.0-17-generic        File type is shown as unknown
vmlinuz-3.5.0-17.efi.signed     File type is DOS/Windows (application/x-ms-dos-executable)
vmlinuz-3.5.0-23-generic        File type is DOS/Windows (application/x-ms-dos-executable)
vmlinuz-3.5.0-25-generic        File type is shown as unknown

The grub menu after installation had about 12 entries, but the top two are "Ubuntu" and  "Advanced Options for Ubuntu".
Looking at the grub.cfg file shows that the Ubuntu option tries to boot the 3.5.0-25-generic kernel.

Selecting the "Advanced Options for Ubuntu" bring up a new menu with 6 options to use either the ....-17 or the -23 or the -25 kernels
or each of these in recovery mode.  Fortunately, of the two ....-17 kernels grub chose to use the vmlinuz-3.5.0-17.efi.signed kernel as 
I was able to verify by looking at the grub.cft file. I think that was why I could boot that option with secure boot enabled while the other 
options that used the -23 and -25 kernels froze the computer.

---

