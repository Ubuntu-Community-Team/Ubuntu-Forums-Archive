---
title: "Secure Boot and Xenial Xerus"
date: 2016-02-22
forum: Ubuntu Development Version
---

### Post by irvine_himself2 on 2016-02-22
At the moment, I am running Ubuntu Studio Wily Werewolf off an external hard disk to test for compatibility with my new laptop and expect to do a full install to replace the Windows 10 operating system sometime this week. Given the ever increasing level of security threats, I am very interested in secure boot options. Since the LTS release of Xenial Xerus is scheduled for April, I am considering  whether it would be worthwhile skipping Wily Werewolf and installing a beta of the LTS. To this end, I have a number of questions:

 
[LIST=1]
[*][COLOR=#000000]Noting that the current secure boot options are neither functional nor user friendly, how difficult is it going to be to enable secure boot using the basic EFI firmware supplied with the ISO?[/COLOR] 
[*][COLOR=#000000]I will probably want to install proprietary drivers for Intel and Nvidia, how will this complicate enabling secure boot?[/COLOR] 
[*][COLOR=#000000]Noting that I am hobbyist and can afford to put up with minor irritations, how stable are the latest Xenial Xerus betas?[/COLOR] 
[*][COLOR=#000000]Am I being overly paranoid and better off leaving things as is until all the kinks of Ubuntu secure boot are worked out?[/COLOR] 
[*][COLOR=#000000]Are there other issues or complications I may have missed?[/COLOR] 
[/LIST]
 
 [COLOR=#000000]Thanks in advance[/COLOR]
 
 [COLOR=#000000]Irvine[/COLOR]

---

### Post by kurt18947 on 2016-02-22
I cannot answer questions about secure boot but I am using gnome-shell & Xubuntu 'flavors' of 16.04. I find them quite stable but wouldn't use them in a 'gotta work' environment. There are sizeable updates most days and one bad update could break things. It might be helpful if you mention what make/model machine you're working with. Not every manufacturer's UEFI implementation is equally polished.

---

### Post by Bucky Ball on 2016-02-22
*Thread moved to **Ubuntu Development Version**.*

Any and all threads regarding unreleased and development Ubuntus go here.

Please use default size/colour/font when posting. Using large text for no reason for a whole post is considered shouting and decreases your chances of getting support. 

Good luck.

---

### Post by irvine_himself2 on 2016-02-22
It's a Toshiba Satellite P50-C, and, running as a live installation from an external hard disk, the machine doesn't seem to have any problems with the Wily Werewolf EFI firmware. I should also make clear that when I finally do a full install, I intend to make an image of the current Windows 10 installation before installing Ubuntu Studio as a single boot.

---

### Post by Bucky Ball on 2016-02-22
How do you mean a 'live installation from a hard drive'. :-k

A 'live' session is had from 'Try Ubuntu' from install media. Do you mean you have installed Ubuntu to an external hard drive and are booting from that?

---

### Post by irvine_himself2 on 2016-02-22
It's installed to a 1 TB SSD using the USB PenDrive utility and is technicaly a live session. At the moment, all I am doing is testing for basic compatibility, but I seriously wish to permanently dump Windows 10!

In essence, from the boot options splash screen, I redirect to the grub on the USB device without ever touching the Toshiba UEFI firmware, (I think?)

Edit
Note, by changing the boot order, I have also booted directly into the USB hard drive without going near the splash screen.

---

### Post by kurt18947 on 2016-02-22
I'm not certain because I don't have a UEFI machine but I'd think a Live USB would still have to pass Secure Boot muster. It'd seem like a huge security hole otherwise. I don't know your situation but it can be useful to have a Windows install at your disposal even if you seldom boot it. There are a few tasks - updating my GPS is one, updating firmware on a printer is another - where there is no practical alternative and you already paid for the Windows license.

---

### Post by irvine_himself2 on 2016-02-22
I don't use GPS and when I need a printer I connect to a friends network. In all honestly, while there are a few Windows only utilities that are nice to have, there is virtually nothing I do where having a working Windows system is essential. So, in that respect, for me personally, am image of the primary disc drive would be quite sufficient. After using Windows 10 for three weeks, from the point of view of respecting basic privacy, Windows 10 is a monster that I am very anxious to get rid of, and yes, I am familiar with the controversy over Unity Dash.

With respect to UEFI and secure boot: Currently, Microsoft provides a recommended key to alternative operating systems, but leaves the implementation up to the OEM. Since many OEM's do not fully implement the UEFI standard, dual booting an alternative operating system under secure boot can be problematic. At the moment, in order to boot from the external drive, I have secure boot turned OFF.

Similarly, while current Ubuntu distros appear to have a secure boot option,  it is not actually implemented, thus leaving the gaping security hole you mentioned. Hence my interest in Xenial Xerus. 

Additionally, as it stands at the moment, to get even the fake secure boot option working for Ubuntu is quite involved, with the user, among other things, having to create fake certificates and keys. Since this will be the first Ubuntu distro to have a working secure boot option, I am wondering if this is still going to be the case , or will the process be more or less invisible to the casual user?

Irvine

---

### Post by mc4man on 2016-02-22
If you (or anyone else) has such concerns it doesn't appear in place yet, tracking bug - 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1401532](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1401532)
Otherwise use your own keys, ect., *lightly* mentioned here, seems a bit complicated - [https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)
relevant quote - 
> IMPORTANT: Canonical's Secure Boot implementation in Ubuntu 15.10 and early is primarily about hardware-enablement and this page focuses on how to test Secure Boot for common hardware-enablement configurations, not for enabling Secure Boot to harden your system. If you want to use Secure Boot as a security mechanism, an appropriate solution would be to use your own keys (optionally enrolling additional keys, see above) and update the bootloader to prohibit booting an unsigned kernel. Ubuntu 16.04 LTS is planned to enable enforcing secure boot (see LP: #1401532 for details).  

---

### Post by grahammechanical on 2016-02-22
As I understand it Ubuntu has met the secure boot requirements since Ubuntu 12.10. Ubuntu was the first Linux distribution to do so.

As far as I can see, some people recommend turning secure boot off for 2 reasons (a) it has become a habit to recommend turning secure boot off; (b) it is sometimes necessary depending on the implementation of the UEFI specification by the manufacturer and the need to dual boot with Windows 10.

So, I do not agree with these statement:

> 
Similarly, while current Ubuntu distros appear to have a secure boot  option,  it is not actually implemented, thus leaving the gaping  security hole you mentioned. Hence my interest in Xenial Xerus. 

Since this will be the first Ubuntu distro to have a working secure boot option,
> 
In order to boot on the widest range of systems, Ubuntu uses the following chain of trust: 


[LIST=1]
[*]Microsoft  signs Canonical's 'shim' 1st stage bootloader with their 'Microsoft  Corporation UEFI CA'. When the system boots and Secure Boot is enabled,  firmware verifies that this 1st stage bootloader (from the 'shim-signed'  package) is signed with a key in DB (in this case 'Microsoft  Corporation UEFI CA') 
[*]The  second stage bootloader (grub-efi-amd64-signed) is signed with  Canonical's 'Canonical Ltd. Secure Boot Signing' key. The shim 1st stage  bootloader verifies that the 2nd stage grub2 bootloader is properly  signed. 
[*]The  2nd stage grub2 bootloader boots an Ubuntu kernel (as of 2012/11, if  the kernel (linux-signed) is signed with the 'Canonical Ltd. Secure Boot  Signing' key, then grub2 will boot the kernel which will in turn apply  quirks and call ExitBootServices. If the kernel is unsigned, grub2 will  call ExitBootServices before booting the unsigned kernel) 
[/LIST]


That has been the situation since the release of Ubuntu 12.10. And Canonical got a lot of insults from the Linux community for providing Ubuntu users with secure boot by getting a Microsoft signed key. 

[https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)

This is how far back the implementation of secure boot in Ubuntu goes.

[https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-June/035445.html)

> Use a supported version of Ubuntu. Support for UEFI appeared in 11.10,  but has become more reliable in next versions. Support for UEFI [SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

See bug report.

> Our SecureBoot support is only to allow installation on computers that have it enabled by default.

User choice. 

> Re-assigning to grub; this "simply" needs modifying one of the linuxefi  patches to not fallback to linux when linuxefi fails; but depends on  having the installer, mokutil and some minimal infrastructure (new shim  keys) in place to handle making this easy for users to "disable" first  if they use DKMS modules.

> If SecureBoot is disabled, validation would succeed anyway in both the signed kernels and unsigned kernels.

Ubuntu 16.04 will not change the way UEFI has been implemented by the manufacture. So, if turning secure boot off is the only way to get Ubuntu working on your machine, then that will not change with 16.04. 

I have been using Xenial Xerus since the first day its 26 week development period started. I have found it to be stable every day I have used it. And I use it every day.

Regards.

---

### Post by cariboo on 2016-02-22
I've been using UEFI on both my laptop and desktop systems. The laptop is dual boot with Windows 10 and Xenial, during the 4.2 kernel cycle, one of the kernels was released without linux-signed-image-generic, which wouldn't allow my laptop to boot giving me a security error (using proposed at the time). My desktop is dual boot, wily and xenial, I haven't run into any problems with it yet. :)

---

### Post by oldfred on 2016-02-22
The concern by Linux is the use of Microsoft's own key for secure boot as Ubuntu and many Linux distributions do. That is/was as some UEFI only supported that key and made it impossible or difficult to add or change keys.
But at any point Microsoft can revoke their keys, so not in control of user. So that is why the suggestion for creating your own keys.

But I am of the opinion that the entire secure boot is Microsoft marketing. If your company is in the headlines every day about lack of security what better way to change perception than have in the title "Secure Boot". 

It just is almost all the issues of Microsoft security are virus which have nothing to do with boot. Then main BIOS boot sector virus was actually released by Sony to control DRM for its music and video.

BIOS installs also have no secure boot.

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

If you want UEFI Secure Boot, some discussion:
[http://mjg59.dreamwidth.org/39339.html](http://mjg59.dreamwidth.org/39339.html)

I assume eventually I will have to turn on Secure boot, but by then the tools to do it will be a bit easier.

---

### Post by irvine_himself2 on 2016-02-22
With regard to **grahammechanical's** comments on a working version of secure boot: 
 

[LIST=1]
[*]This bug report details how a couple of months ago,  some students got Ubuntu to load an unsigned Linux kernel [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1401532](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1401532) 
[*]And thiis PcWorld article details how Ubuntu's current boot loader happily boots unsigned code [http://www.pcworld.com/article/3026346/linux/ubuntus-secure-boot-support-isnt-secure-and-threatens-even-windows-pcs.html](http://www.pcworld.com/article/3026346/linux/ubuntus-secure-boot-support-isnt-secure-and-threatens-even-windows-pcs.html) 
[/LIST]
  
As far as the OEM's UEFI implementation is concerned, **grahammechanical** is totally correct, and I should thank him since his comments caused me to check exactly what is happening when I try to boot onto the external HD. Basically, I had been having problems with creating a working USB drive, and, since turning off secure boot is the first thing everybody suggests, I blithely assumed this was part of the problem. It wasn't!

**cariboo's** comments are very re-assuring, 

In regard to **oldfred's** comments, with the greatest respect, when you compare the modern EFI firmware to  the old BIOS ROM, I think you are seriously underestimating the potential for OS independent malicious code to take control of your baby. While, to-date, such infections are primarily of academic interest, I get surprisingly frequent requests from friends and acquaintances to dig out old fashioned rootkits from infected windows machines. 

On the other hand, I do agree that Microsoft is using security as a marketing ploy to disguise the fact that, by using Windows 10, you have given up any right to privacy.

Thanks for your comments, they have given me a lot to think about and have been generally re-assuring.

Irvine

---

