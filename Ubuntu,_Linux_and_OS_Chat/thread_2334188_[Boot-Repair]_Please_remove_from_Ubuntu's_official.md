---
title: "[Boot-Repair] Please remove from Ubuntu's official documentation"
date: 2016-08-17
forum: Ubuntu, Linux and OS Chat
---

### Post by shersk on 2016-08-17
I propose that boot-repair be removed from the official documentation, or that there is included some stronger warnings with the package. From experience, the program is presented as if it is able to automatically fix a broken boot setup, but this is not the case. Booting with grub is very complicated, and modifying your setup requires that you understand what you are doing. I trusted this program to fix my system, but it didn't. It just made it worse. I have written an email to the developer, as is offered in one of the last screens after the program has finished, and let's see if I get any answer.

For example, in [this post]("https://ubuntuforums.org/showthread.php?t=1581099"), can some please change the text, so it does not recommend people to run boot-repair first?

I also want to point out that on the [page about boot-repair]("https://help.ubuntu.com/community/Boot-Repair"), it directs the reader to a certain forum thread "[COLOR=#333333][FONT=Ubuntu]for any questions/comments", but the thread it links to is closed. [/FONT][/COLOR]

---

### Post by ajgreeny on 2016-08-17
*Thread moved to **Ubuntu, Linux and OS Chat**.* which is more appropriate for the situation as this is not a support request.

---

### Post by RichardET on 2016-08-17
> **shersk said:**
> I propose that boot-repair be removed from the official documentation, or that there is included some stronger warnings with the package. From experience, the program is presented as if it is able to automatically fix a broken boot setup, but this is not the case. Booting with grub is very complicated, and modifying your setup requires that you understand what you are doing. I trusted this program to fix my system, but it didn't. It just made it worse. I have written an email to the developer, as is offered in one of the last screens after the program has finished, and let's see if I get any answer.

For example, in [this post]("https://ubuntuforums.org/showthread.php?t=1581099"), can some please change the text, so it does not recommend people to run boot-repair first?

I also want to point out that on the [page about boot-repair]("https://help.ubuntu.com/community/Boot-Repair"), it directs the reader to a certain forum thread "[COLOR=#333333][FONT=Ubuntu]for any questions/comments", but the thread it links to is closed. [/FONT][/COLOR]

Multi-boot systems are tricky in today's world of secure-boot, uefi, gpt, etc.  I stay away from this and run Linux natively, and use Windows VM's;  back-ups are a cinch and grub2 issues never exist, especially if one picks the installer defaults.  In my view, serious Windows users should consider the reverse option, with use of Linux VM's, not a multi-boot scenario, which is prone to errors.

---

### Post by mastablasta on 2016-08-17
rather than removing the app how about resolving the app? you should have posted here or use the bug report app: [SIZE=2]https://bugs.launchpad.net/boot-repair
[/SIZE]
i am sure the app works well on MBR computer as well as on many UEFI machines. if it doesn't (didn't) work for oyu it owul dbe better to troubelshoot it & solve the bug rather then removing it.

> Easy-to-use (repair in 1 click ! )
Free (GPL open-source license)
Helpful (Boot-Info summary to get help by email or on your favorite forum)
Safe (automatic backups)
Reliable (300.000 users per year)
Can recover access to Windows (XP, Vista, Windows7, Windows8, Windows10).
Can recover access to Debian, Ubuntu, Mint, Fedora, OpenSuse, ArchLinux...
Can recover access to any OS (Windows, MacOS, Linux..) if your PC contains Debian, Ubuntu, Mint, Fedora, OpenSuse, ArchLinux, or derivative.
Can repair MBR-locked OEM computer boot if the original bootsector has been saved by [Clean-Ubiquity]("https://launchpad.net/clean-ubiquity")
Can repair the boot when you have the "GRUB Recovery" error message
Options to reinstall GRUB2/GRUB1 bootloader easily (OS by default, purge, unhide, kernel options..)
and much more ! (UEFI, SecureBoot, RAID, LVM, Wubi, filesystem repair...)




i am not sure what is complicated about GRUB.

i also second the idea of RichardET - to have dualboot it might be better to use one OS in VM. PC's these days are strong enough to run them without any issues.

---

### Post by grahammechanical on 2016-08-17
Many people for one reason and another mess up installing Ubuntu as a duel boot with Windows 8/10. The number of help requests testify to that. Very few of these posts contain any useful information. So, the Boot Info Summary report of Boot Repair is most useful to those of us who are trying to help.

What is the alternative to using the Boot Repair recommended repair? Is anybody here willing to explain step by step to a completely new user how to fix the problem using the command line? If we think that Grub is complicated, then just try to explain how to fix a Grub boot problem to someone who does not even know what a command line is or how to get access to one, or how to access the motherboard boot system utility, or whether it is BIOS or UEFI.

Regards.

---

### Post by oldfred on 2016-08-17
It does have a warning:
> Warning: the default settings are the ones used by the "Recommended  Repair". Changing them may worsen your problem. Don't modify them before  creating a [BootInfo URL]("https://help.ubuntu.com/community/Boot-Info"), and asking for advice on Ubuntu Forums [Absolute Beginners Section]("http://ubuntuforums.org/newthread.php?do=newthread&f=326") or in [Installation and Upgrades]("http://ubuntuforums.org/newthread.php?do=newthread&f=333").


The links I see in the Boot-Info page lead directly to new posts in forum, Beginners or Installation.

But the issues with new UEFI systems are that vendors have violated UEFI spec by using descriptio and only valid description is "Windows Boot Manager" and installing Ubuntu/grub just does not work the way it should. 
Major work arounds often required.

 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

Also as with any open source software, please file a bug report on any specific issue. I have filed several on Boot-Repair and response has always been good.

[https://bugs.launchpad.net/boot-repair](https://bugs.launchpad.net/boot-repair)

---

### Post by shersk on 2016-08-17
Thanks for the responses. The reason I got into this was that I was forced to use an older laptop for some time while my newer laptop is being repaired, and I am trying out many distros on the old one to find out what suits it best according to my requirements. Thus multi-boot. When I installed Lubuntu, it did something to the boot setup so that I could no longer boot Linux Lite. I ran boot-repair, but it didn't fix my problem. Afterward, it had added one boot option for Windows 7, so now there are two Windows 7 lines. I could still boot all the other OSes, except Linux Lite.

About my particular problems, it didn't take too long time searching the ubuntu documentation and studying my laptop's behavior to find out how to make it boot into Linux Lite. I quickly found [this page]("https://help.ubuntu.com/community/Grub2/Troubleshooting"), which walked me through the troubleshooting process for grub2. From some prior experience tinkering with linux boot setups and just studying the other boot command lines in grub (which were working), I could see that some text was missing. The 'linux /boot/vmlinuz-....' and the next one 'initrd /boot/initrd-...'. Those lines must have been deleted during the installation of Lubuntu for some reason. I wrote in the correct commands, ran the two commands ```
[COLOR=#333333][FONT=UbuntuMono]sudo update-grub [/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuMono]sudo grub-install /dev/sdX[/FONT][/COLOR]
``` and now Linux Lite is booting normally. I can post debug info about this to help find out what caused it (probably due to Lubuntu's installer), but where can I find these logs?

About boot-repair, I appreciate the work done by the developers of this program, and I'm sure it is useful in a lot of situations, but in my case I felt kind of misled when it seemed to promise to fix my boot setup. There could be more warnings and caveats, or options to get detailed diagnostic info  (more 'Advanced...' buttons), for those who are interested in understanding what's going on. 

Of course when something is not working it should go through a debugging process, but not all people are ready to dive into the coding world whenever a problem arises. It can be a terrible time hog and distraction.

---

### Post by mastablasta on 2016-08-18
Lubuntu and boot repair in your case then worked as expected and made Lubuntu to boot. Thi sis then not an issue with boto repair but rather with Linux lite. Boot repair fixes the boot so that users can boto into Ubuntu or that they can boot in dualboot systems (Ubuntu, Windows). it may work with other distros as well, but you are getting into advanced settings here and then you should understand what you set up. in that case it is best to first post results of boot info script, get help with propper settings, and then do the repair.

Windows 7 - 2 lines is correct. one is bnormla boot the other one i think it uses for"repair mode" - but you can also boot from it normally i think.

---

### Post by shersk on 2016-08-19
I don't agree with this last comment. It's something about not promising more in the advertisement than you can keep. After you wrote this, I went back and re-read the introduction to boot-repair, and I think I was right to criticize. And it doesn't say what you write here. It just says that it is able to repair various boot set-ups. 

The problem was, as far as I can understand, Lubuntu's installer, and I have read that when setting up a multi-boot maching (i.e. more than two OSes), and if using grub, then it's better to not reinstall grub each time, but go back and boot the first Linux installation and run update-grub from there (for each new system). 

I'm planning to have five or six different Linuxes on my laptop, lightweight distros, to see what works best. 

I don't believe the second Windows 7 boot option is for repair mode. Both are normal boot, but one is from /dev/sda1 and the other /dev/sda2. I used to have only one Windows boot option.

---

### Post by oldfred on 2016-08-19
Because so many users did not know the Windows boot partition was essential as it normally is hidden, Boot-Repair now copies bootmgr & /boot/BCD. Then main (c: ) partition can be directly booted. Windows uses boot flag to know which partition has boot files, but grub searches for bootmgr & BCD files to know which partition is bootable, so then you get two entries in grub.

If planning multiple installs best to learn to manage grub manally. I turn off os-prober and add my own entries to 40_custom.
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays) 

Not sure if all distributions create links to newest kernel in / like Debian, but you can always copy a boot stanza into 40_custom to boot a specific install, but may then have to update with new kernel later.

---

