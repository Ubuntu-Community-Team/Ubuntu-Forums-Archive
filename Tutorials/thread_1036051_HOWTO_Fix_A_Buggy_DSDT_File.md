---
title: "HOWTO Fix A Buggy DSDT File"
date: 2009-01-10
forum: Tutorials
---

### Post by 67GTA on 2009-01-10
This guide will help you fix your DSDT file to fix common ACPI problems on any Debian based OS. With Mint 6/Ubuntu 8.10, I started having a lot of problems with my laptop thermal temps, and not wanting to boot without holding down a keyboard key. This was in my case because of a buggy DSDT file. To read more about ACPI/DSDT go here: [http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html](http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html) It is the catalyst behind this how to. The process is a little different for Debian based operating systems. This how to will show you how to do it with Mint/Ubuntu. 

[COLOR=#ff0000]WARNING: This might mess up your operating system. Even if you have zero errors after fixing the DSDT, it may still cause you to not be able to boot your OS. It will not harm your PC or hardware.[/COLOR]

Before trying this tutorial, try updating your BIOS to fix bugs first. This is a last resort to try and manually fix DSDT related bugs.

The first thing we need to do is install the Intel DSDT compiler. Open a terminal and run ```
sudo apt-get install iasl
```Then we need to get a copy of your current DSDT and save it in your home folder with this command ```
sudo cat /proc/acpi/dsdt > dsdt.dat
```Then we will disassemble it with iasl with this command ```
iasl -d dsdt.dat
``` You should now have a file called dsdt.dsl in your home folder. This is the file you will be editing. Once you are done making changes, we will use it to make a new DSDT file. The next step is to use iasl to recompile the dsdt.dsl file to see any errors/warnings/optimizations with this command. Replace <yourusername> with your username.
```
iasl -tc /home/<yourusername>/dsdt.dsl
``` This will show you the output of the recompiling process. At this point, you can use the output to find errors in the DSDT and attempt to fix them by editing the dsdt.dsl file with your favorite text editor. Go into the preferences for your text editor and turn on "line numbering". Then open dsdt.dsl with your text editor. You can use the output of the last command to find the errors by their line number. The following is an example of a common error. "dsdt.dsl 349" means the error is on line 349 of the dsdt.dsl file. Go to that line in your dsdt.dsl file with the text editor to fix it and save.

```
dsdt.dsl   349:     Method (\_WAK, 1, NotSerialized)
Warning  1079 -                 ^ Reserved method must return a value (_WAK)
```Each time you make a change in the dsdt.dsl file, be sure to save it, and then recompile to see the new output with ```
iasl -tc /home/<yourusername>/dsdt.dsl
``` This will recompile it with the new changes and give you a new output to see if things look better :D Below are several links with common DSDT errors and their fixes. 

[http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html](http://forums.opensuse.org/how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html)
[https://wiki.edubuntu.org/LaptopTestingTeam/HPdv5z](https://wiki.edubuntu.org/LaptopTestingTeam/HPdv5z)
[http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/320199-howto-fix-your-buggy-dsdt.html](http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/320199-howto-fix-your-buggy-dsdt.html)
[http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)

You might get lucky and find one already fixed for your make/model here: [http://acpi.sourceforge.net/dsdt/view.php](http://acpi.sourceforge.net/dsdt/view.php) If so then you can skip to the last two commands. 

Once you have successfully edited the dsdt.dsl file, we should have a dsdt.aml in your home folder. This was the goal of the how to. 

[COLOR=#ff0000]WARNING: The commands up till this point have not made any changes to your system. You can simply delete the files that have been created. After the last two commands, you will be using a custom DSDT at boot. This is the point of no return.[/COLOR]

These commands will rename the dsdt.aml file and copy it to your /etc/initramfs-tools folder. Then we will update the initrd image to include the DSDT override at boot. The very last command will update the initrd image. You need to replace "kernel version" with your kernel version. You can see it by running ```
uname -r
``` in a terminal.

```
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
``````
sudo update-initramfs -u -k kernel-version
```Now cross your fingers and reboot  :wink: To see if it stuck, you can look in your dmesg output. Open a terminal and run ```
dmesg > /home/yourusername/Desktop/dmesg
``` This will put your dmesg output into a text file on your desktop. You should see a line similar to this:

```
[    0.020495] ACPI: Checking initramfs for custom DSDT
[    0.353464] ACPI: Found DSDT in DSDT.aml.
[    0.353470] ACPI: Override [DSDT-   MCP67], this is unsafe: tainting kernel
[    0.353478] ACPI: Table DSDT replaced by host OS
[    0.353482] ACPI: DSDT 00000000, 7CB3 (r1 NVIDIA    MCP67  6040000 INTL 20061109)
[    0.353487] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"

```Places to check before and after are: dmesg output and /proc/acpi. I would especially check /proc/acpi/fan and /proc/acpi/thermal_zone to see if they are populated after this tutorial if they weren't before. Another trick I've learned during this process is to specify the operating system at boot. More about this is explained in the links I provided. I found that by adding ```
acpi_osi="Linux"
``` to the boot options, the operating system even saw my hardware differently at boot. This seems to be very affective on HP laptops with Vista preinstalled. I outlined these steps here: [http://www.linuxmint.com/forum/viewtopic.php?f=60&t=18222](http://www.linuxmint.com/forum/viewtopic.php?f=60&t=18222) The DSDT code is very hard to read, and I myself don't understand all of it. I left my HP desktop with 0 errors, and 4 warnings. Everything works, so I left the warnings. My laptop DSDT is perfect. It is a HP dv6815nr if someone with the same model wants to use my custom DSDT file. DSDT files are PC specific. Do not try using a DSDT from another PC unless it has the same hardware as yours.

[COLOR=Red]EDIT:[/COLOR] To remove a custom DSDT, delete the DSDT.aml file with ```
sudo rm /etc/initramfs-tools/DSDT.aml
```[COLOR=Red][COLOR=Black] and reupdate the init image with [/COLOR][/COLOR]```
sudo update-initramfs -u -k kernel-version
``` This will revert your system back to the original state after a reboot.[COLOR=Red]

EDIT:[/COLOR] This will not work with kernels that are still in development. The patches that allow the custom DSDT are not included until the kernel is released as "stable".

[COLOR=Red]UPDATE:[/COLOR] The kernel dev's will no longer use the patch to enable custom DSDT files for Karmic 9.10 and beyond. Jaunty 9.04 is the last version this will work on. You are urged to file a bug report for DSDT errors.

---

### Post by CylnZ on 2009-05-07
:confused:
```
john@john-laptop2:~$ sudo update-initramfs -u -k kernel-version
[sudo] password for john: 
update-initramfs: Generating /boot/initrd.img-kernel-version
Cannot find /lib/modules/kernel-version
update-initramfs: failed for /boot/initrd.img-kernel-version
john@john-laptop2:~$ 
```Duh, got it figured, replace "kernel-version" where appropriate; sheesh. :oops:

```
john@john-laptop2:~$ sudo update-initramfs -u -k 2.6.28-12-generic
update-initramfs: Generating /boot/initrd.img-2.6.28-12-generic
john@john-laptop2:~$
```:P

  ```
0.004000] ACPI: Core revision 20080926
[    0.006886] ACPI: Checking initramfs for custom DSDT
[    0.443822] ACPI: Found DSDT in DSDT.aml.
[    0.443828] ACPI: Override [DSDT-CRESTLNE], this is unsafe: tainting kernel
[    0.443834] ACPI: Table DSDT replaced by host OS
[    0.443838] ACPI: DSDT 00000000, 887E (r2 INTEL  CRESTLNE  6040000 INTL 20081204)
[    0.443843] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"
[    0.452055] Setting APIC routing to flat
```

:popcorn::popcorn:

I'll move on to the add os to startup tip, Thanks so much:KS

---

### Post by CylnZ on 2009-05-08
```
   Scope (\_SB)
    {
        Method (_INI, 0, NotSerialized)
        {
            If (DTSE)
            {
                TRAP (0x47)
            }

            Store (0x07D0, OSYS)
            If (CondRefOf (_OSI, Local0))
            {
                If (_OSI ("Linux"))
                {
                    Store (0x01, LINX)
                }

                If (_OSI ("Windows 2001"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP1"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP2"))
                {
                    Store (0x07D2, OSYS)
                }

                If (_OSI ("Windows 2006"))
                {
                    Store (0x07D6, OSYS)
                }
            }
```Those dirty SoBs.

I'm going to try an experiment; changing :

 ```
If (_OSI ("Linux"))
                {
                    Store (0x01, LINX)
```to:

 ```
If (_OSI ("Linux"))
                {
                    Store (0x07D2, OSYS)

```which would be telling the bios we are running xp sp2 wouldnt it?

I'll post the results in a bit. Its gonna be real interesting to see if the things cool off.

I picked up the 965 whitepaper from intel and I may grab the compiler from m$ to compare dsdt.dsl output. Strangely, many of intels and some of acpi.info calls arnt there where acpi says they should be. 

will let you know.

---

### Post by CalderCoalson on 2009-05-08
Thank you, thank you thank you!!!  My laptop can finally suspend again!

---

### Post by mm0204 on 2009-05-10
I really appreciate that someone has figured out how to fix this problem.  I am really miffed that i can't get simple things to work on my laptop but I think this is the issue.

my question is: has anybody submitted a bug report to Ubuntu about this problem?  Because, I am not a programer.  I don't speak machine language.  I have googled for the corrections to make to my dsdt.dsl file and I can't find any of the errors that I'm getting.  So, I'm going to have to go back to Hardy Heron because everything (except for sound capture which still doesn't work on this laptop) worked in Hardy.  Just finding a work around doesn't help the community.  this needs to be fixed by someone who knows what they're doing at the source code level... right?

or am i missing something?

Grace and Peace,
Matt
matty (at) the strange land (dot) net {just put it all together :) }
:guitar:

---

### Post by 67GTA on 2009-05-10
> **mm0204 said:**
> I really appreciate that someone has figured out how to fix this problem.  I am really miffed that i can't get simple things to work on my laptop but I think this is the issue.

my question is: has anybody submitted a bug report to Ubuntu about this problem?  Because, I am not a programer.  I don't speak machine language.  I have googled for the corrections to make to my dsdt.dsl file and I can't find any of the errors that I'm getting.  So, I'm going to have to go back to Hardy Heron because everything (except for sound capture which still doesn't work on this laptop) worked in Hardy.  Just finding a work around doesn't help the community.  this needs to be fixed by someone who knows what they're doing at the source code level... right?

or am i missing something?

Grace and Peace,
Matt
matty (at) the strange land (dot) net {just put it all together :) }
:guitar:


This is not a Ubuntu problem to fix. The hardware vendors are causing the trouble. The DSDT is hard coded into your BIOS when it is programed. There is nothing Ubuntu or any other OS can do except find workarounds. Even then, your hardware might not work correctly, you just don't see it as a bug within the OS. Some hardware/PC makers use the Microsoft AML compiler, and causes breakage for Linux/Mac. Follow my how to to the point of getting your dsdt.dsl file and send it to me. I will see if I can fix the errors.

---

### Post by 67GTA on 2009-05-10
> **CylnZ said:**
> ```
   Scope (\_SB)
    {
        Method (_INI, 0, NotSerialized)
        {
            If (DTSE)
            {
                TRAP (0x47)
            }

            Store (0x07D0, OSYS)
            If (CondRefOf (_OSI, Local0))
            {
                If (_OSI ("Linux"))
                {
                    Store (0x01, LINX)
                }

                If (_OSI ("Windows 2001"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP1"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP2"))
                {
                    Store (0x07D2, OSYS)
                }

                If (_OSI ("Windows 2006"))
                {
                    Store (0x07D6, OSYS)
                }
            }
```Those dirty SoBs.

I'm going to try an experiment; changing :

 ```
If (_OSI ("Linux"))
                {
                    Store (0x01, LINX)
```to:

 ```
If (_OSI ("Linux"))
                {
                    Store (0x07D2, OSYS)

```which would be telling the bios we are running xp sp2 wouldnt it?

I'll post the results in a bit. Its gonna be real interesting to see if the things cool off.

I picked up the 965 whitepaper from intel and I may grab the compiler from m$ to compare dsdt.dsl output. Strangely, many of intels and some of acpi.info calls arnt there where acpi says they should be. 

will let you know.

An easier way to do this would be to add the corresponding boot argument to /boot/grub/menu.lst as I laid out at the end of my how to. Instead of ```
acpi_osi="Linux"
```, you would add ```
acpi_osi="Windows 2001 SP2"
``` This will tell Ubuntu to load the acpi tables for XP to use in Ubuntu.

---

### Post by mgolobay on 2009-05-14
> **67GTA said:**
> This is not a Ubuntu problem to fix. 

Unfortunately that is not true.  While the Microsoft AML compiler may be just as buggy as all the rest of their products, the end result is that many of us have dual boot machines where a Microsoft OS is able to work around the DSDT bugs to yield a running system and Linux is not.  

Ubuntu is a distribution of Linux that is well positioned to be an upgrade from Windows.  But as long as so many have had experiences like mine where I set a friend's laptop up for dual boot Vista/Ubuntu and only the Vista system works, Microsoft will continue to win.  The vast majority who try Ubuntu with a buggy DSDT will do no research whatsoever, decide Ubuntu is sort of pretty but not ready for real work, delete it and go on never to look back.

People want to experience this:
[http://www.youtube.com/watch?v=EwL0G9wK8j4]("http://www.youtube.com/watch?v=EwL0G9wK8j4")

But end up with a lot of this:
[http://failblog.files.wordpress.com/2009/03/fail-owned-roadpaint-fail.jpg?w=362&h=500]("http://failblog.files.wordpress.com/2009/03/fail-owned-roadpaint-fail.jpg?w=362&h=500")

---

### Post by 67GTA on 2009-05-14
> Unfortunately that is not true. While the Microsoft AML compiler may be just as buggy as all the rest of their products, the end result is that many of us have dual boot machines where a Microsoft OS is able to work around the DSDT bugs to yield a running system and Linux is not.

You unfortunately don't understand what you are talking about. Do you know what a DSDT is and how operating systems interact with them? The Microsoft ACPI tables in the 71 DSDT's I've fixed so far have had zero errors. All the errors have been in the Linux tables. MS and Linux don't use the same sectiuons of a DSDT. The MS sections have no errors to work around when the MS compiler is used. The Microsoft AML compiler is intentionally breaking Linux/Mac compatibility. If you send me your DSDT, I can break a few things in the Microsoft ACPI tables, the MS AML compiler won't catch the errors, and MS won't run correctly. Would it then be MS's job to fix it? When the open industry standard Intel AML compiler is used, "ALL" operating systems work as they should.

> Ubuntu is a distribution of Linux that is well positioned to be an upgrade from Windows. But as long as so many have had experiences like mine where I set a friend's laptop up for dual boot Vista/Ubuntu and only the Vista system works, Microsoft will continue to win. The vast majority who try Ubuntu with a buggy DSDT will do no research whatsoever, decide Ubuntu is sort of pretty but not ready for real work, delete it and go on never to look back.

Your point here is not valid either. Any PC with Windows preinstalled is supposed to work correctly. The fact that you installed Ubuntu on a PC that has thousands of possible hardware combinations, and it didn't work as expected, is not a "fail". Try picking a PC at random that wasn't designed for Vista and try installing it. You will have just as many bad experiences. If you get a PC designed for Linux with Linux preinstalled, it will run just as perfect as Vista preinstalled on a Vista supported PC. If Vista failed to work on "said PC", would that mean Vista is not ready for work?

> The vast majority who try Ubuntu with a buggy DSDT will do no research whatsoever, decide Ubuntu is sort of pretty but not ready for real work, delete it and go on never to look back.

This is the only point I agree with you on. The vast majority of people have no idea what a DSDT is, or that it even exists. I for one know Linux is a superior OS to Windows, and if something doesn't work right, I will try to find out why. Most people don't think this way. They try Linux out of curiosity, it doesn't work exactly right, and then go back to Windows where they should stay. The other small percentage of free thinkers stick with it, find out "who" is causing them trouble, and liberate themselves.

---

### Post by CalderCoalson on 2009-05-14
> **67GTA said:**
> The other small percentage of free thinkers stick with it, find out "who" is causing them trouble, and liberate themselves.
:D
Windows = The Matrix

---

### Post by tdietz87 on 2009-05-14
> **67GTA said:**
> The other small percentage of free thinkers stick with it, find out "who" is causing them trouble, and liberate themselves.
hell yea!

---

### Post by mgolobay on 2009-05-15
> **67GTA said:**
> Do you know what a DSDT is and how operating systems interact with them? 

Thank you for helping to make my point more clear while still missing it entirely.  Should I need to know what a DSDT is and what it does in order to use Linux?  No.  Does anyone need to know such things when running a Windows OS on any hardware currently available.  No.

If Linux is going to ever be a viable replacement for Windows the developers are going to need to be a lot more creative about solutions rather than excuses.

---

### Post by CalderCoalson on 2009-05-15
OR hardware companies could simply begin standing behind the quality of their products...  just a thought...

---

### Post by chavanak on 2009-05-16
> **mgolobay said:**
> Thank you for helping to make my point more clear while still missing it entirely.  Should I need to know what a DSDT is and what it does in order to use Linux?  No.  Does anyone need to know such things when running a Windows OS on any hardware currently available.  No.

If Linux is going to ever be a viable replacement for Windows the developers are going to need to be a lot more creative about solutions rather than excuses.

You again seem to miss the point that this is not a OS specific problem. It has nothing to do with linux/vista/or sorts. It's because your hardware manufacturer faulted and used a crappy compiler. If you take a linux pre-installed pc, then you hardly face these problems. If you are not ready to spend sometime to get your OS running then you can by all means use windows.  

P.S: I am not trying to be harsh but get your points straight, it is NOT a linux problem and no one is giving excuses here instead of fixing it. According to me its only because of the hardware manufacturer (In my case HP screwed up :( and I had lot of errors in dsdt which i fixed. Now my laptop rocks)

---

### Post by CylnZ on 2009-05-24
Gateway 6860fx
Bios v. 94.29

```
CylnZ@CylnZ-laptop1:~$ iasl -tc /home/CylnZ/dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

ASL Input:  /home/CylnZ/dsdt.dsl - 7427 lines, 258581 bytes, 2928 keywords
AML Output: /home/CylnZ/dsdt.aml - 27724 bytes, 715 named objects, 2213 executable opcodes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 872 Optimizations
CylnZ@CylnZ-laptop1:~$ 
```

Yippee-Skippee :KS:KS:KS:KS:KS

If you want/need the file:

---

### Post by totoxa on 2009-05-27
I got these errors:

> /home/user/dsdt.dsl   104:     Method (\_WAK, 1, NotSerialized)
Warning  1080 -   Reserved method must return a value ^  (_WAK)

/home/user/dsdt.dsl  3540:                 Method (_Q16, 0, NotSerialized)
Warning  1087 -             Not all control paths return a value ^  (_Q16)

/home/users/dsdt.dsl  7714:                 Method (_HOT, 0, Serialized)
Warning  1087 -             Not all control paths return a value ^  (_HOT)

/home/users/dsdt.dsl  7714:                 Method (_HOT, 0, Serialized)
Warning  1080 -              Reserved method must return a value ^  (_HOT)

/home/users/dsdt.dsl  7716:                     Zero
Error    4095 -        syntax error, unexpected PARSEOP_ZERO ^ 

/home/users/dsdt.dsl  7723:                 Method (_CRT, 0, Serialized)
Warning  1087 -             Not all control paths return a value ^  (_CRT)

/home/users/dsdt.dsl  7723:                 Method (_CRT, 0, Serialized)
Warning  1080 -              Reserved method must return a value ^  (_CRT)

/home/users/dsdt.dsl  7725:                     Zero
Error    4095 -        syntax error, unexpected PARSEOP_ZERO ^ Can you help me with mi dsdt.dsl file?, i dont know how to fix it.

I have an HP DV6620LA and the only problem that i have detected is:

when the notebook boots only with battery i have to press any key to successful boot the os.

Sorry my english

---

### Post by 67GTA on 2009-05-27
Yours isn't that bad. I will fix it and get it back to you tomorrow. A custom DSDT for your PC will fix:

Suspend/Hibernate
Heat/Fan(will run cooler, your temp limits aren't being read)
Fix hanging at boot

First I need a copy of the output of ```
sudo dmesg
``` The output exceeds the terminal cache, so open a terminal, click "Edit" and then "Profile Preferences". Click on the "Scrolling" tab and change 512 to 3000. Then run ```
sudo dmesg
``` and post a copy of it. I will need to compare it to the output of dmesg afterwards to make sure everything is okay.

---

### Post by totoxa on 2009-05-27
Here is it

---

### Post by 67GTA on 2009-05-27
I went ahead and fixed it before bed:D You can copy/paste from the how to now that you have the fixed dsdt.aml file. The results from iasl: Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 1130 Optimizations. Be sure to add "acpi_osi="Linux" to /boot/grub/menu.lst per the how to. After you get it implemented, run "sudo dmesg" after rebooting and post a copy. I will look tomorrow to make sure there are no errors left in your dmesg output and post the changes for you. [ATTACH]115398[/ATTACH]

---

### Post by pormogo on 2009-05-27
Hi, I was directed here by way of the following post I made in the dell user support forums. 

[http://ubuntuforums.org/showthread.php?t=1149898](http://ubuntuforums.org/showthread.php?t=1149898)

Since updating to Ubuntu 9.04 (32bit) on my Dell m1330n when returning from suspend occasionally (every second suspend really) my computer seems to myteriously "lose" my gnome session, and all of my work with it. It's pretty annoying and I have gotten into the habit of just shutting down my machine when moving from place to place. I posted my pm-suspend.log file in the other thead above and it seemed to indicate it returned from suspend correctly. However my session is gone :_| 

I tried flashing my BIOS from version A8 to the current version A15 on the advice of another user. This did not fix my issue. I read through this thead and it seems unlikely to me that dell would compile a linux incompatible/buggy version of their DSDT in a laptop model that was actually sold with Ubuntu preinstalled on it. 

I've taken a dump of my DSDT file and I could provide it if someone would be so kind as to take a look or tell me is the DSDT could potentially even be responsible fro my problem.

I'm a little lost as to where to look next. No log files are showing any errors or anything. 

The only thing I see is an error with GDM indicating MTRR issues. 

from /var/log/gmd/:0.log
*error setting MTRR (base = 0xe0000000, size = 0x10000000, type = 1) Invalid argument (22)*

---

### Post by totoxa on 2009-05-27
> **67GTA said:**
> I went ahead and fixed it before bed:D You can copy/paste from the how to now that you have the fixed dsdt.aml file. The results from iasl: Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 1130 Optimizations. Be sure to add "acpi_osi="Linux" to /boot/grub/menu.lst per the how to. After you get it implemented, run "sudo dmesg" after rebooting and post a copy. I will look tomorrow to make sure there are no errors left in your dmesg output and post the changes for you. [ATTACH]115398[/ATTACH]

So many thanks

---

### Post by 67GTA on 2009-05-28
> **pormogo said:**
> Hi, I was directed here by way of the following post I made in the dell user support forums. 

[http://ubuntuforums.org/showthread.php?t=1149898](http://ubuntuforums.org/showthread.php?t=1149898)

Since updating to Ubuntu 9.04 (32bit) on my Dell m1330n when returning from suspend occasionally (every second suspend really) my computer seems to myteriously "lose" my gnome session, and all of my work with it. It's pretty annoying and I have gotten into the habit of just shutting down my machine when moving from place to place. I posted my pm-suspend.log file in the other thead above and it seemed to indicate it returned from suspend correctly. However my session is gone :_| 

I tried flashing my BIOS from version A8 to the current version A15 on the advice of another user. This did not fix my issue. I read through this thead and it seems unlikely to me that dell would compile a linux incompatible/buggy version of their DSDT in a laptop model that was actually sold with Ubuntu preinstalled on it. 

I've taken a dump of my DSDT file and I could provide it if someone would be so kind as to take a look or tell me is the DSDT could potentially even be responsible fro my problem.

I'm a little lost as to where to look next. No log files are showing any errors or anything. 

The only thing I see is an error with GDM indicating MTRR issues. 

from /var/log/gmd/:0.log
*error setting MTRR (base = 0xe0000000, size = 0x10000000, type = 1) Invalid argument (22)*

It is probably some leftover link in some obscure config file left after upgrade. I've never had much luck with upgrading, and keep a second /home partition. I have not found any errors on any Dell PC yet, but it is possible. Extract it using the how to, zip it up, and post it here as an attachment. I will be glad to have a look.

---

### Post by 67GTA on 2009-05-28
What does 
```
cat /proc/mtrr
``` return? The gdm error says you have 256MB of RAM.

---

### Post by pormogo on 2009-05-28
my laptop seems to allocate 256Mb of RAM to my onboard intel GM965 graphics chip. I am assuming this is the 256Mb of RAM that it is referring to 

```

$ cat /proc/mtrr 
reg00: base=0x000000000 (    0MB), size= 2048MB, count=1: write-back
reg01: base=0x080000000 ( 2048MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  512MB, count=1: write-back
reg03: base=0x100000000 ( 4096MB), size=  512MB, count=1: write-back
reg04: base=0x0df800000 ( 3576MB), size=    8MB, count=1: uncachable
reg05: base=0x0df700000 ( 3575MB), size=    1MB, count=1: uncachable

```

Is what /proc/mtrr looks like on this system.

On a side note it seems like my system is allocating 512Mb to my video card. There is 4G of RAM in this system however only 3520M seems usable by the syste

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          **3520**       3005        514          0        171       2249
-/+ buffers/cache:        585       2935
Swap:         2933          0       2932

```

Is there any way for me to check the amount of RAM being used by my GM965? Looking back through those gdm logs I think that error might actually be the root cause of my issue as it pops up every second log file which would indicate that it is happening in concordance with when I am forced to use a fresh gdm login...

On a side note I've actually had pretty good luck upgrading this laptop. It's gone from 7.04 to 9.04 without any kind of serious issues (until now).

---

### Post by totoxa on 2009-05-28
Hello, here is my new dmesg file, Now i can see a folder in /proc/acpi/thermal_zone and Computer Temperature Monitor only show one temperature, before it show four

I didnt use the acpi_osi="Linux" option. i will try it and will compare the results.

 i have a question: How can i restore the old DSDT file or make the os load it from bios?

thanks

---

### Post by 67GTA on 2009-05-28
Looks good. It should run like a new laptop now;) The only error now is: ```
ACPI: BIOS _OSI(Linux) query ignored
``` If you add the osi definition to the grub menu, that will go away, and your hardware will be initialized when Ubuntu boots according to the Linux acpi tables only. Your temp is being seen, so it should run cooler/quieter instead of being guessed at ```
thermal LNXTHERM:01: registered as thermal_zone0 ACPI: Thermal Zone [THRM] (37 C)
``` Suspend/hibernate should work now since your sleep states are recognized ```
ACPI: (supports S0 S3 S4 S5)
``` I would make a copy of the DSDT.aml file and keep it in a safe place. You will have to use it anytime you reinstall, or install any other Mac/Linux OS. The DSDT in your BIOS is broken and won't change. To remove it and boot with the original DSDT in the BIOS, just delete DSDT.aml in /etc/initramfs-tools, and update the initramfs again. This will remove the link to the custom DSDT.

---

### Post by 67GTA on 2009-05-28
pormogo: The system isn't reporting 4GB. The first line is saying you have 256. You might try this method to see if it fixes the error: [http://ubuntuforums.org/showthread.php?t=115104](http://ubuntuforums.org/showthread.php?t=115104)

---

### Post by totoxa on 2009-05-28
> **67GTA said:**
> Looks good. It should run like a new laptop now;) The only error now is: ```
ACPI: BIOS _OSI(Linux) query ignored
``` If you add the osi definition to the grub menu, that will go away, and your hardware will be initialized when Ubuntu boots according to the Linux acpi tables only. Your temp is being seen, so it should run cooler/quieter instead of being guessed at ```
thermal LNXTHERM:01: registered as thermal_zone0 ACPI: Thermal Zone [THRM] (37 C)
``` Suspend/hibernate should work now since your sleep states are recognized ```
ACPI: (supports S0 S3 S4 S5)
``` I would make a copy of the DSDT.aml file and keep it in a safe place. You will have to use it anytime you reinstall, or install any other Mac/Linux OS. The DSDT in your BIOS is broken and won't change. To remove it and boot with the original DSDT in the BIOS, just delete DSDT.aml in /etc/initramfs-tools, and update the initramfs again. This will remove the link to the custom DSDT.

many thanks :D, i will add acpi.. to the grub list :D

---

### Post by ryanrudolf on 2009-05-28
Hello 67gta,

Hope everything is well in your end. I would like to request for assistance regarding my dsdt file. I think I belong to one of those who acquired a laptop with buggy implementation of dsdt. My /proc/acpi/fan is empty, and my fan does not turn on. Even if my laptop is idle, I am getting 58C and it goes as high as 65C when transferring huge amounts of data (in GBs). Appreciate if you could help me out as I am fairly new to the dsdt stuff. Thanks in advance.

> ryanrudolf@linux-laptop:~$ iasl -d dsdt.dat 

Intel ACPI Component Architecture
AML Disassembler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

Loading Acpi table from file dsdt.dat
Acpi table [DSDT] successfully installed and loaded
Pass 1 parse of [DSDT]
Pass 2 parse of [DSDT]
Parsing Deferred Opcodes (Methods/Buffers/Packages/Regions)
..........................................................................................................................................................................................................................................................................................................................................................................................................................
Parsing completed
Disassembly completed, written to "dsdt.dsl"
ryanrudolf@linux-laptop:~$ 


> ryanrudolf@linux-laptop:~$ iasl -tc dsdt.dsl
Maximum error count (200) exceeded
ASL Input:  dsdt.dsl - 7228 lines, 247531 bytes, 2835 keywords
Compilation complete. 201 Errors, 0 Warnings, 0 Remarks, 4 Optimizations

Maximum error count (200) exceeded
Segmentation fault
ryanrudolf@linux-laptop:~$


Thank you for your time.

---

### Post by pormogo on 2009-05-29
> **67GTA said:**
> pormogo: The system isn't reporting 4GB. The first line is saying you have 256. You might try this method to see if it fixes the error: [http://ubuntuforums.org/showthread.php?t=115104](http://ubuntuforums.org/showthread.php?t=115104)

Stay with me for a second, I'm not really getting what you're saying here. The first line, as in register00 there?

*reg00: base=0x000000000 (    0MB), size= **2048**MB, count=1: write-back*

While that does not equate to the correct available amount of main system memory it doesn't look like 256Mb to me it looks like 2GB. 

I also don't have poor glx gears performance. However I do see how it could create a problem so I'll give it a shot.

---

### Post by 67GTA on 2009-05-29
The part you quoted is correct. I was referring to the info in your error message. [QUOTE]error setting MTRR (base = 0xe0000000, size = 0x10000000, type = 1) Invalid argument (22) If you could manually set the value according to the script in the post I linked to, it might fix the problem.

---

### Post by 67GTA on 2009-05-29
> **ryanrudolf said:**
> Hello 67gta,

Hope everything is well in your end. I would like to request for assistance regarding my dsdt file. I think I belong to one of those who acquired a laptop with buggy implementation of dsdt. My /proc/acpi/fan is empty, and my fan does not turn on. Even if my laptop is idle, I am getting 58C and it goes as high as 65C when transferring huge amounts of data (in GBs). Appreciate if you could help me out as I am fairly new to the dsdt stuff. Thanks in advance.





Thank you for your time.

It now has zero errors and 44 optimizations. I hope it will help with your trouble. If your fan still doesn't work, try looking in your BIOS to see if it is controlling your fan. Follow the how to to implement the dsdt.aml. After rebooting, post a copy of ```
sudo dmesg
``` from a terminal. Be sure to add the osi="Linux" definition per the how to. [ATTACH]115634[/ATTACH]

---

### Post by ryanrudolf on 2009-05-29
Thank you 67gta! That was quick. Followed the howto and here are the result of my dmesg before and after. Still not getting /proc/acpi/fan . . . but the temp reading now is lower. It now reads 46C at idle compared to as before. Thank you.

---

### Post by 67GTA on 2009-05-29
> **ryanrudolf said:**
> Thank you 67gta! That was quick. Followed the howto and here are the result of my dmesg before and after. Still not getting /proc/acpi/fan . . . but the temp reading now is lower. It now reads 46C at idle compared to as before. Thank you.

Everything looks fine. Your fan is probably controlled by the BIOS. As long as it comes on when the PC gets hot;) It sucks that we have to do this, and don't really own something we paid for. Now you are truly free. Keep a copy of the DSDT.aml in a safe place. You will need it if you ever reinstall another Linux/Mac OS. The DSDT in your BIOS will always be broken, and will need to be overridden.

---

### Post by peterwil on 2009-05-30
Hello 67GTA,

I have a toshiba Satellite L305D-S5881 with Vista running fine. After repartitioning I have installed Ubuntu (hardy heron) with
wireless (Atheros card) working alright. The only problem is the fan doesn't switch on. Vista runs at around 44 C while Ubuntu consistenly runs at > 66 C. Reading your posts, mine looks like a dsdt problem.
Could you please take a look at my dsdt.dsl file and possibly suggest the sections to change to get the fan to switch on. 
Thanks a great deal for your time.

Peter William

---

### Post by ryanrudolf on 2009-05-30
> **67GTA said:**
> Everything looks fine. Your fan is probably controlled by the BIOS. As long as it comes on when the PC gets hot;) It sucks that we have to do this, and don't really own something we paid for. Now you are truly free. Keep a copy of the DSDT.aml in a safe place. You will need it if you ever reinstall another Linux/Mac OS. The DSDT in your BIOS will always be broken, and will need to be overridden.

Thanks again for the help. Just need some clarification for my peace of mind. :) Is the dsdt in my BIOS very broken? Based on my dmesg's, are there any indications that the new dsdt fixed a  lot of stuff? One more question, if I use a new distro, I can still use the fixed dsdt you created? Thanks again.

---

### Post by 67GTA on 2009-05-30
ryanrudolf:

> Is the dsdt in my BIOS very broken?Only the Linux tables. The Microsoft AML compiler makes Windows run fine, but breaks Linux/Mac compatibility. The Intel AML compiler isn't OS specific. It tries to fix errors for all OS's, and doesn't break things.

> Based on my dmesg's, are there any indications that the new dsdt fixed a  lot of stuff?The biggest were temp readings and suspend/hibernate. There were several tweaks to things like CPU, etc that you won't really notice.

> One more question, if I use a new distro, I can still use the fixed dsdt you created?It will work on any Linux/Mac OS. A a matter of fact, even if the developers find workarounds for your specific problems, the problems still exist, but are not seen. The ACPI developers are constantly working to add new hardware/functionality to their code, but if your BIOS is broken, anything short of fixing it will just be a bandage. Not every Linux/Mac OS does things the same. If you use another OS, you will have to find out how to implement the DSDT. The how to here is for any Debian based OS.

---

### Post by 67GTA on 2009-05-30
> **peterwil said:**
> Hello 67GTA,

I have a toshiba Satellite L305D-S5881 with Vista running fine. After repartitioning I have installed Ubuntu (hardy heron) with
wireless (Atheros card) working alright. The only problem is the fan doesn't switch on. Vista runs at around 44 C while Ubuntu consistenly runs at > 66 C. Reading your posts, mine looks like a dsdt problem.
Could you please take a look at my dsdt.dsl file and possibly suggest the sections to change to get the fan to switch on. 
Thanks a great deal for your time.

Peter William

I don't see any fan related tables. Is it controlled by the bios? Look for fan settings there.

---

### Post by moose2 on 2009-05-30
```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

ASL Input:  dsdt.dsl - 8075 lines, 285872 bytes, 3173 keywords
AML Output: dsdt.aml - 30379 bytes, 737 named objects, 2436 executable opcodes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 929 Optimizations
```

Why are there 929 Optimizations? Are those Optimizations done automaticly or can I improve it? For this dsdt.dsl I fixed a lot of errors, warnings and remarks...

Here is my dsdt.dsl
```
/*
 * Intel ACPI Component Architecture
 * AML Disassembler version 20081204
 *
 * Disassembly of dsdt.dat, Thu May 21 17:54:01 2009
 *
 *
 * Original Table Header:
 *     Signature        "DSDT"
 *     Length           0x00007E20 (32288)
 *     Revision         0x02
 *     Checksum         0x64
 *     OEM ID           "WS    "
 *     OEM Table ID     "C46_____"
 *     OEM Revision     0x06040000 (100925440)
 *     Compiler ID      "MSFT"
 *     Compiler Version 0x03000000 (50331648)
 */
DefinitionBlock ("dsdt.aml", "DSDT", 2, "WS    ", "C46_____", 0x06040000)
{
    External (PDC1)
    External (PDC0)
    External (CFGD)
    External (\_PR_.CPU0._PPC)

    Mutex (MSMI, 0x07)
    Method (PHSR, 2, NotSerialized)
    {
        Acquire (MSMI, 0xFFFF)
        Store (Arg1, PRM0)
        Store (Arg0, SMIF)
        Store (Zero, TRP0)
        Store (PRM0, Local0)
        Release (MSMI)
        Return (Local0)
    }

    Method (HKEY, 1, NotSerialized)
    {
        PHSR (0x1E, Arg0)
    }

    Method (LAMN, 1, NotSerialized)
    {
        If (\_SB.AMW0.WLMP)
        {
            Store (Arg0, \_SB.AMW0.WLID)
            Notify (\_SB.AMW0, 0xB0)
        }
        Else
        {
            PHSR (0x1F, Arg0)
        }
    }

    Method (RBEC, 1, NotSerialized)
    {
        Return (PHSR (0x20, Arg0))
    }

    Method (WBEC, 2, NotSerialized)
    {
        Acquire (MSMI, 0xFFFF)
        Store (Arg1, PRM1)
        Store (Arg0, PRM0)
        Store (0x21, SMIF)
        Store (Zero, TRP0)
        Release (MSMI)
    }

    Method (MBEC, 3, NotSerialized)
    {
        Acquire (MSMI, 0xFFFF)
        Store (Arg2, PRM2)
        Store (Arg1, PRM1)
        Store (Arg0, PRM0)
        Store (0x22, SMIF)
        Store (Zero, TRP0)
        Release (MSMI)
    }

    Name (B2ED, Buffer (0x1C)
    {
        /* 0000 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
        /* 0008 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
        /* 0010 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
        /* 0018 */    0x00, 0x00, 0x00, 0x00
    })
    Method (WH15, 2, NotSerialized)
    {
        Acquire (MSMI, 0xFFFF)
        CreateDWordField (Arg1, 0x00, DEAX)
        CreateDWordField (Arg1, 0x04, DEBX)
        CreateDWordField (Arg1, 0x08, DECX)
        CreateDWordField (Arg1, 0x0C, DEDX)
        CreateDWordField (B2ED, 0x00, OEAX)
        CreateDWordField (B2ED, 0x04, OEBX)
        CreateDWordField (B2ED, 0x08, OECX)
        CreateDWordField (B2ED, 0x0C, OEDX)
        CreateDWordField (B2ED, 0x10, OFLG)
        If (LEqual (\_SB.AMW0.WMID, 0x01))
        {
            CreateDWordField (Arg1, 0x10, DESI)
            CreateDWordField (Arg1, 0x14, DEDI)
            CreateDWordField (B2ED, 0x14, OESI)
            CreateDWordField (B2ED, 0x18, OEDI)
        }

        If (LAnd (LEqual (DEAX, 0x9630), LEqual (DEBX, 0x01)))
        {
            Store (\_SB.AMW0.WCOD (), Local0)
            Store (Local0, OECX)
            If (LEqual (Local0, 0x00))
            {
                Store (0x01, OFLG)
            }
            Else
            {
                Store (Zero, OFLG)
            }

            Return (B2ED)
        }

        Store (DEAX, WNVA)
        Store (DEBX, WNVB)
        Store (DECX, WNVC)
        Store (DEDX, WNVD)
        If (LEqual (\_SB.AMW0.WMID, 0x01))
        {
            Store (DESI, WNVS)
            Store (DEDI, WNVI)
        }

        Store (0x23, SMIF)
        Store (Zero, TRP0)
        Store (WNVA, OEAX)
        Store (WNVB, OEBX)
        Store (WNVC, OECX)
        Store (WNVD, OEDX)
        Store (WFLG, OFLG)
        If (LEqual (\_SB.AMW0.WMID, 0x01))
        {
            Store (WNVS, OESI)
            Store (WNVI, OEDI)
        }

        Release (MSMI)
        Return (B2ED)
    }

    Name (\BCLP, Package (0x12)
    {
        0x64, 
        0x3C, 
        0x19, 
        0x1E, 
        0x23, 
        0x28, 
        0x2D, 
        0x32, 
        0x37, 
        0x3C, 
        0x41, 
        0x46, 
        0x4B, 
        0x50, 
        0x55, 
        0x5A, 
        0x5F, 
        0x64
    })
    Name (\MAXL, 0x11)
    Method (BIAN, 1, NotSerialized)
    {
        If (LEqual (And (DID1, 0x0F00), 0x0400))
        {
            Notify (\_SB.PCI0.GFX0.DD01, Arg0)
        }

        If (LEqual (And (DID2, 0x0F00), 0x0400))
        {
            Notify (\_SB.PCI0.GFX0.DD02, Arg0)
        }

        If (LEqual (And (DID3, 0x0F00), 0x0400))
        {
            Notify (\_SB.PCI0.GFX0.DD03, Arg0)
        }

        If (LEqual (And (DID4, 0x0F00), 0x0400))
        {
            Notify (\_SB.PCI0.GFX0.DD04, Arg0)
        }

        If (LEqual (And (DID5, 0x0F00), 0x0400))
        {
            Notify (\_SB.PCI0.GFX0.DD05, Arg0)
        }
    }

    Mutex (MUTX, 0x00)
    OperationRegion (PORT, SystemIO, 0x80, 0x01)
    Field (PORT, ByteAcc, NoLock, Preserve)
    {
        P80H,   8
    }

    Method (P8XH, 2, Serialized)
    {
        If (LEqual (Arg0, 0x00))
        {
            Store (Or (And (P80D, 0xFFFFFF00), Arg1), P80D)
        }

        If (LEqual (Arg0, 0x01))
        {
            Store (Or (And (P80D, 0xFFFF00FF), ShiftLeft (Arg1, 0x08)
                ), P80D)
        }

        If (LEqual (Arg0, 0x02))
        {
            Store (Or (And (P80D, 0xFF00FFFF), ShiftLeft (Arg1, 0x10)
                ), P80D)
        }

        If (LEqual (Arg0, 0x03))
        {
            Store (Or (And (P80D, 0x00FFFFFF), ShiftLeft (Arg1, 0x18)
                ), P80D)
        }

        Store (P80D, P80H)
    }

    Method (\_PIC, 1, NotSerialized)
    {
        Store (Arg0, GPIC)
    }

    Method (_PTS, 1, NotSerialized)
    {
        Store (0x00, P80D)
        P8XH (0x00, Arg0)
        Store (Arg0, \_SB.PCI0.LPCB.EC0.SYSC)
        Store (0x01, \_SB.PCI0.LPCB.EC0.MUTE)
        If (LEqual (Arg0, 0x04))
        {
            Store (\_SB.PCI0.LPCB.EC0.BNEN, \_SB.PCI0.LPCB.EC0.EBNE)
        }
    }

    Method (_WAK, 1, NotSerialized)
    {
        P8XH (0x00, Arg0)
        If (LOr (LEqual (Arg0, 0x03), LEqual (Arg0, 0x04)))
        {
            If (And (CFGD, 0x01000000))
            {
                If (LAnd (And (CFGD, 0xF0), LEqual (OSYS, 0x07D1)))
                {
                    TRAP (0x3D)
                }
            }
        }

        Notify (\_SB.PCI0, 0x08)
        If (NEXP)
        {
            If (And (OSCC, 0x02))
            {
                \_SB.PCI0.NHPG ()
            }

            If (And (OSCC, 0x04))
            {
                \_SB.PCI0.NPME ()
            }
        }

        Store (Arg0, \_SB.PCI0.LPCB.EC0.SYSO)
        Store (0x00, \_SB.PCI0.LPCB.EC0.MUTE)
        \_SB.PCI0.LPCB.EC0.TINI ()
        Notify (\_SB.PCI0.LPCB.EC0.BAT0, 0x81)
        If (LEqual (RP1D, 0x00)) {}
        If (LEqual (RP2D, 0x00))
        {
            Notify (\_SB.PCI0.RP02, 0x00)
        }

        If (LEqual (RP3D, 0x00))
        {
            Notify (\_SB.PCI0.RP03, 0x00)
        }

        If (LEqual (RP4D, 0x00))
        {
            Notify (\_SB.PCI0.RP04, 0x00)
        }

        If (LEqual (RP5D, 0x00))
        {
            Notify (\_SB.PCI0.RP05, 0x00)
        }

        If (LEqual (RP6D, 0x00))
        {
            Notify (\_SB.PCI0.RP06, 0x00)
        }

        If (LEqual (Arg0, 0x04))
        {
            Store (\_SB.PCI0.LPCB.EC0.EBNE, \_SB.PCI0.LPCB.EC0.BNEN)
            \_SB.PCI0.LPCB.EC0.MCEB.HRSM ()
        }

        If (LEqual (Arg0, 0x03))
        {
            \_SB.PCI0.LPCB.EC0.MCEB.HRSM ()
        }

        \_PR.RPPC ()
        P8XH (0x00, 0xCD)
        Return (Package (0x02)
        {
            0x00, 
            0x00
        })
    }

    Method (GETB, 3, Serialized)
    {
        Multiply (Arg0, 0x08, Local0)
        Multiply (Arg1, 0x08, Local1)
        CreateField (Arg2, Local0, Local1, TBF3)
        Return (TBF3)
    }

    Method (PNOT, 0, Serialized)
    {
        If (MPEN)
        {
            If (And (PDC0, 0x08))
            {
                Notify (\_PR.CPU0, 0x80)
                If (And (PDC0, 0x10))
                {
                    Sleep (0x64)
                    Notify (\_PR.CPU0, 0x81)
                }
            }

            If (And (PDC1, 0x08))
            {
                Notify (\_PR.CPU1, 0x80)
                If (And (PDC1, 0x10))
                {
                    Sleep (0x64)
                    Notify (\_PR.CPU1, 0x81)
                }
            }
        }
        Else
        {
            Notify (\_PR.CPU0, 0x80)
            Sleep (0x64)
            Notify (\_PR.CPU0, 0x81)
        }
    }

    Method (TRAP, 1, Serialized)
    {
        Store (Arg0, SMIF)
        Store (0x00, TRP0)
        Return (SMIF)
    }

    Scope (\_SB)
    {
        Device (AMW0)
        {
            Name (_HID, "pnp0c14")
            Name (_UID, 0x00)
            Name (WLMP, 0x00)
            Name (WMID, 0x00)
            Name (B0ED, Buffer (0x04)
            {
                0x00, 0x00, 0x00, 0x00
            })
            CreateDWordField (B0ED, 0x00, WLID)
            Name (B1ED, Buffer (0x04)
            {
                0x00, 0x00, 0x00, 0x00
            })
            Name (_WDG, Buffer (0x64)
            {
                /* 0000 */    0x81, 0x17, 0xF4, 0xD9, 0x33, 0xF6, 0x00, 0x44, 
                /* 0008 */    0x93, 0x55, 0x60, 0x17, 0x70, 0xBE, 0xC5, 0x10, 
                /* 0010 */    0x41, 0x41, 0x01, 0x00, 0x1D, 0x37, 0xC3, 0x67, 
                /* 0018 */    0xA3, 0x95, 0x37, 0x4C, 0xBB, 0x61, 0xDD, 0x47, 
                /* 0020 */    0xB4, 0x91, 0xDA, 0xAB, 0x41, 0x42, 0x01, 0x02, 
                /* 0028 */    0xED, 0x16, 0x1F, 0x43, 0x2B, 0x0C, 0x4C, 0x44, 
                /* 0030 */    0xB2, 0x67, 0x27, 0xDE, 0xB1, 0x40, 0xCF, 0x9C, 
                /* 0038 */    0x41, 0x43, 0x01, 0x02, 0x71, 0xBF, 0xD1, 0x40, 
                /* 0040 */    0x2D, 0xA8, 0x59, 0x4E, 0xA1, 0x68, 0x39, 0x85, 
                /* 0048 */    0xE0, 0x3B, 0x2E, 0x87, 0xB0, 0x00, 0x01, 0x08, 
                /* 0050 */    0x21, 0x12, 0x90, 0x05, 0x66, 0xD5, 0xD1, 0x11, 
                /* 0058 */    0xB2, 0xF0, 0x00, 0xA0, 0xC9, 0x06, 0x29, 0x10, 
                /* 0060 */    0x44, 0x44, 0x01, 0x00
            })
            Method (_WED, 1, NotSerialized)
            {
                Store (Arg0, P80H)
                If (LEqual (Arg0, 0xB0))
                {
                    Return (B0ED)
                }
		Return(Package(0x02){0x00, 0x00}) 
            }

            Method (WQAA, 1, NotSerialized)
            {
                Store (0xAA, P80H)
                Return (B1ED)
            }

            Method (WSAA, 2, NotSerialized)
            {
                Store (0xA1, P80H)
                CreateDWordField (Arg1, 0x00, DDD0)
                If (LEqual (DDD0, 0x01))
                {
                    Add (DDD0, 0x02, DDD0)
                    Store (DDD0, Index (B1ED, 0x00))
                }
            }

            Method (WMAB, 3, NotSerialized)
            {
                Store (0xAB, P80H)
                Store (0x01, WLMP)
                Store (0x00, WMID)
                Return (WH15 (Arg1, Arg2))
            }

            Method (WMAC, 3, NotSerialized)
            {
                Store (0xAC, P80H)
                Store (0x01, WLMP)
                Store (0x01, WMID)
                Return (WH15 (Arg1, Arg2))
            }

            Name (WQDD, Buffer (0x0560)
            {
                /* 0000 */    0x46, 0x4F, 0x4D, 0x42, 0x01, 0x00, 0x00, 0x00, 
                /* 0008 */    0x50, 0x05, 0x00, 0x00, 0x70, 0x1D, 0x00, 0x00, 
                /* 0010 */    0x44, 0x53, 0x00, 0x01, 0x1A, 0x7D, 0xDA, 0x54, 
                /* 0018 */    0x18, 0xCB, 0x8D, 0x00, 0x01, 0x06, 0x18, 0x42, 
                /* 0020 */    0x10, 0x09, 0x10, 0x8A, 0xE7, 0x80, 0x42, 0x04, 
                /* 0028 */    0x0A, 0x0D, 0xA1, 0x40, 0x30, 0x28, 0x38, 0x4B, 
                /* 0030 */    0x82, 0x90, 0x0B, 0x26, 0x26, 0x40, 0x08, 0x84, 
                /* 0038 */    0x24, 0x0A, 0x30, 0x2F, 0x40, 0xB7, 0x00, 0xC3, 
                /* 0040 */    0x02, 0x6C, 0x0B, 0x30, 0x2D, 0xC0, 0x31, 0x90, 
                /* 0048 */    0xFA, 0xF7, 0x87, 0x28, 0x0D, 0x44, 0x22, 0x20, 
                /* 0050 */    0xA9, 0x14, 0x08, 0x09, 0x15, 0xA0, 0x5C, 0x80, 
                /* 0058 */    0x6F, 0x01, 0xDA, 0x11, 0x25, 0x59, 0x80, 0x65, 
                /* 0060 */    0x18, 0x11, 0xD8, 0x2B, 0x32, 0x41, 0xE3, 0x04, 
                /* 0068 */    0xE5, 0x0C, 0x03, 0x05, 0x6F, 0xC0, 0x36, 0x05, 
                /* 0070 */    0x98, 0x1C, 0x04, 0x95, 0x3D, 0x08, 0x94, 0x0C, 
                /* 0078 */    0x08, 0x79, 0x14, 0x60, 0x15, 0x4E, 0xD3, 0x49, 
                /* 0080 */    0x60, 0xF7, 0x73, 0x91, 0x30, 0x18, 0x19, 0x13, 
                /* 0088 */    0xA0, 0x50, 0x80, 0x46, 0x01, 0xDE, 0x40, 0x64, 
                /* 0090 */    0x4B, 0x80, 0x41, 0x01, 0xE2, 0x04, 0x28, 0x83, 
                /* 0098 */    0x12, 0x4A, 0xB8, 0x83, 0x69, 0x4D, 0x80, 0x39, 
                /* 00A0 */    0x28, 0x82, 0x56, 0x1B, 0x98, 0x50, 0x3A, 0x03, 
                /* 00A8 */    0x12, 0x48, 0xAC, 0x16, 0xC1, 0x05, 0x13, 0x3B, 
                /* 00B0 */    0x6A, 0x94, 0x40, 0xD1, 0xDB, 0x1F, 0x04, 0x09, 
                /* 00B8 */    0xA7, 0x00, 0xA2, 0x06, 0x10, 0x45, 0x1A, 0x0D, 
                /* 00C0 */    0x6A, 0x44, 0x09, 0x0E, 0xCC, 0xA3, 0x39, 0xD5, 
                /* 00C8 */    0xCE, 0x05, 0x48, 0x9F, 0xAB, 0x40, 0x8E, 0xF5, 
                /* 00D0 */    0x34, 0xEA, 0x1C, 0x2E, 0x01, 0x49, 0x60, 0xAC, 
                /* 00D8 */    0x04, 0xB7, 0xEE, 0x21, 0xE2, 0x5D, 0x03, 0x6A, 
                /* 00E0 */    0xE2, 0x87, 0xC8, 0x04, 0xC1, 0xA1, 0x86, 0xE8, 
                /* 00E8 */    0xF1, 0x86, 0x3B, 0x81, 0xA3, 0x3E, 0x12, 0x06, 
                /* 00F0 */    0x71, 0x50, 0x47, 0x83, 0x39, 0x07, 0xD8, 0xE1, 
                /* 00F8 */    0x64, 0x34, 0xE3, 0x52, 0x05, 0x98, 0x1D, 0xBA, 
                /* 0100 */    0x46, 0x96, 0xE0, 0x78, 0x0C, 0x7D, 0xF6, 0xE7, 
                /* 0108 */    0xD3, 0x33, 0x24, 0x91, 0x3F, 0x08, 0xD4, 0xC8, 
                /* 0110 */    0x0C, 0xED, 0xA1, 0x9E, 0x56, 0xCC, 0x90, 0x4F, 
                /* 0118 */    0x01, 0x87, 0xC5, 0xC4, 0x42, 0x68, 0x93, 0x1A, 
                /* 0120 */    0x0F, 0xC4, 0xFF, 0xFF, 0x78, 0xC0, 0xA3, 0xF8, 
                /* 0128 */    0x68, 0x20, 0x84, 0x57, 0x82, 0xD8, 0x1E, 0x50, 
                /* 0130 */    0x82, 0x01, 0x21, 0xE4, 0x64, 0x3C, 0xA8, 0x51, 
                /* 0138 */    0x18, 0x35, 0xDC, 0x61, 0x1C, 0xB5, 0x8F, 0x0F, 
                /* 0140 */    0x3A, 0x3C, 0x50, 0x51, 0xC3, 0xA6, 0x67, 0x06, 
                /* 0148 */    0x7E, 0x5C, 0x60, 0xE7, 0x82, 0x98, 0x8F, 0x00, 
                /* 0150 */    0x1E, 0xC9, 0x09, 0xF9, 0x38, 0xE1, 0x81, 0xC1, 
                /* 0158 */    0x07, 0xC4, 0x7B, 0x9F, 0x32, 0x19, 0xC1, 0x99, 
                /* 0160 */    0x7A, 0x80, 0xE0, 0xB0, 0x3E, 0x7C, 0x02, 0xFC, 
                /* 0168 */    0xB2, 0xF0, 0xB0, 0x90, 0xC0, 0xF7, 0x07, 0x03, 
                /* 0170 */    0xE3, 0x46, 0x68, 0xBF, 0x02, 0x10, 0x82, 0x97, 
                /* 0178 */    0x79, 0x02, 0x90, 0x53, 0x04, 0x8D, 0xCD, 0xD0, 
                /* 0180 */    0x4F, 0x03, 0x2F, 0x0E, 0xE1, 0x83, 0x47, 0x38, 
                /* 0188 */    0xDF, 0x03, 0x38, 0x85, 0xC7, 0x00, 0x0F, 0xC1, 
                /* 0190 */    0x04, 0x16, 0x39, 0x02, 0x94, 0x98, 0x11, 0xA0, 
                /* 0198 */    0x8E, 0x0D, 0x27, 0x70, 0x3C, 0x61, 0x8F, 0xE0, 
                /* 01A0 */    0x78, 0xA2, 0x9C, 0xC4, 0x01, 0xF9, 0xA8, 0x61, 
                /* 01A8 */    0x84, 0xE0, 0xE5, 0x9E, 0x38, 0x88, 0xE6, 0x71, 
                /* 01B0 */    0x6A, 0x16, 0xEF, 0x00, 0x87, 0xC0, 0xC6, 0x84, 
                /* 01B8 */    0x3B, 0x40, 0x78, 0x08, 0x7C, 0x00, 0x8F, 0x1A, 
                /* 01C0 */    0xE7, 0x67, 0xA5, 0xB3, 0x42, 0x9E, 0x3B, 0xF8, 
                /* 01C8 */    0x98, 0xB0, 0x03, 0xE0, 0xD2, 0x0F, 0x27, 0x28, 
                /* 01D0 */    0xB1, 0xE7, 0x13, 0x50, 0xFC, 0xFF, 0xCF, 0x27, 
                /* 01D8 */    0xC0, 0x1E, 0xE4, 0x99, 0xE4, 0xED, 0xE4, 0x68, 
                /* 01E0 */    0x9E, 0x4B, 0x1E, 0x48, 0x9E, 0x48, 0x9E, 0x4F, 
                /* 01E8 */    0x8C, 0xF3, 0x66, 0xF2, 0x64, 0x10, 0xE1, 0xF9, 
                /* 01F0 */    0xC4, 0xD7, 0x14, 0x23, 0x44, 0x09, 0x19, 0xE8, 
                /* 01F8 */    0xE1, 0x24, 0x42, 0x94, 0x70, 0x81, 0xC2, 0x1A, 
                /* 0200 */    0x21, 0xC8, 0x63, 0xC1, 0x09, 0x1F, 0x76, 0xAC, 
                /* 0208 */    0x40, 0x61, 0x9E, 0x4F, 0x98, 0xF0, 0xA7, 0x86, 
                /* 0210 */    0x2C, 0x9C, 0x4F, 0x00, 0xBA, 0xFC, 0xFF, 0xCF, 
                /* 0218 */    0x27, 0x80, 0x33, 0x81, 0xE7, 0x13, 0x90, 0x0E, 
                /* 0220 */    0x8F, 0x1F, 0x4F, 0x80, 0xC9, 0x08, 0xB8, 0x16, 
                /* 0228 */    0x13, 0x87, 0x2F, 0xD4, 0xE3, 0xC0, 0xA7, 0x11, 
                /* 0230 */    0x40, 0xCE, 0x09, 0xE4, 0xFD, 0xE3, 0x38, 0x9F, 
                /* 0238 */    0x44, 0x7C, 0xF7, 0xF2, 0xFF, 0xFF, 0xE6, 0xE5, 
                /* 0240 */    0x83, 0xC8, 0x1B, 0xC8, 0xC1, 0x3E, 0x8D, 0xB0, 
                /* 0248 */    0x51, 0x05, 0x33, 0xCA, 0xE9, 0x47, 0x88, 0xFA, 
                /* 0250 */    0x52, 0x62, 0xC4, 0x08, 0xC1, 0x42, 0x05, 0x8A, 
                /* 0258 */    0x11, 0x35, 0xB2, 0x61, 0x23, 0xC4, 0x79, 0xF8, 
                /* 0260 */    0xA2, 0x0F, 0x06, 0x0D, 0xD5, 0xA7, 0x11, 0x80, 
                /* 0268 */    0x1F, 0xA7, 0x09, 0xDC, 0xE9, 0x02, 0x4C, 0x93, 
                /* 0270 */    0x38, 0x80, 0x28, 0x45, 0xC3, 0x68, 0x3A, 0x8F, 
                /* 0278 */    0x03, 0x01, 0x9F, 0x2F, 0x80, 0x89, 0xE2, 0x97, 
                /* 0280 */    0x9E, 0xCE, 0x27, 0xFE, 0xFF, 0xAB, 0x05, 0x91, 
                /* 0288 */    0x8D, 0xB5, 0x7A, 0x58, 0x34, 0xF3, 0x03, 0x48, 
                /* 0290 */    0xF0, 0xC5, 0x03, 0x6B, 0xD8, 0x27, 0x79, 0x16, 
                /* 0298 */    0x27, 0x99, 0x60, 0x56, 0x28, 0xC1, 0x7A, 0xD8, 
                /* 02A0 */    0x4E, 0x09, 0xA3, 0x04, 0x24, 0x1A, 0x8E, 0xA1, 
                /* 02A8 */    0xAD, 0x19, 0x46, 0x70, 0x06, 0xF1, 0x79, 0xC8, 
                /* 02B0 */    0x21, 0xCE, 0x31, 0x50, 0x8E, 0x0C, 0x1E, 0xC5, 
                /* 02B8 */    0x59, 0x3D, 0x07, 0x78, 0x8C, 0x8F, 0x0B, 0x6C, 
                /* 02C0 */    0x7C, 0x3E, 0x08, 0xF0, 0xC3, 0xA0, 0x6F, 0x06, 
                /* 02C8 */    0x46, 0xB6, 0x9A, 0xD3, 0x0C, 0x0A, 0xCC, 0xC7, 
                /* 02D0 */    0x0B, 0x4E, 0x50, 0xD7, 0xCD, 0x05, 0x64, 0x43, 
                /* 02D8 */    0x82, 0x79, 0x10, 0x38, 0x24, 0x30, 0x4F, 0xD5, 
                /* 02E0 */    0x43, 0x02, 0x1E, 0xE0, 0x87, 0x04, 0xE6, 0x2B, 
                /* 02E8 */    0x81, 0x87, 0x04, 0x2C, 0xFE, 0xFF, 0xA8, 0x07, 
                /* 02F0 */    0x71, 0x48, 0x60, 0x46, 0xF2, 0x90, 0xC0, 0xA6, 
                /* 02F8 */    0xEF, 0xC8, 0x01, 0x0A, 0x20, 0xDF, 0x30, 0x7C, 
                /* 0300 */    0xDC, 0x7B, 0xCA, 0x60, 0x63, 0x78, 0xE2, 0x33, 
                /* 0308 */    0x9A, 0xD1, 0xB9, 0xC4, 0xE5, 0xE8, 0x42, 0xC1, 
                /* 0310 */    0x45, 0xC1, 0xE8, 0x58, 0x60, 0x10, 0x4F, 0xCB, 
                /* 0318 */    0x51, 0xA6, 0x8A, 0x9E, 0x89, 0x7D, 0x9E, 0x42, 
                /* 0320 */    0xC8, 0x89, 0x82, 0x5F, 0xDD, 0x74, 0x9F, 0x81, 
                /* 0328 */    0x76, 0xF7, 0x08, 0xEA, 0x8B, 0x0A, 0x83, 0xF3, 
                /* 0330 */    0x64, 0x39, 0x9C, 0xAF, 0x14, 0xFC, 0xAE, 0xE3, 
                /* 0338 */    0xCB, 0x15, 0xF8, 0x46, 0x05, 0xF7, 0x50, 0xC1, 
                /* 0340 */    0x46, 0x05, 0xF6, 0xEB, 0x88, 0x47, 0x05, 0xD6, 
                /* 0348 */    0xFF, 0xFF, 0xA8, 0x60, 0x9D, 0x2B, 0xD8, 0xA8, 
                /* 0350 */    0xC0, 0x7E, 0x26, 0xF0, 0xA8, 0x80, 0xCB, 0xD1, 
                /* 0358 */    0x82, 0x8D, 0x0A, 0xEC, 0x1E, 0x46, 0x05, 0xCA, 
                /* 0360 */    0x20, 0xD7, 0x0F, 0x28, 0xD0, 0x8F, 0x96, 0xAF, 
                /* 0368 */    0x40, 0x0F, 0x41, 0x8F, 0x51, 0x1E, 0x14, 0xB8, 
                /* 0370 */    0x61, 0x7C, 0xDF, 0x03, 0x4E, 0x17, 0x10, 0x98, 
                /* 0378 */    0xF0, 0x18, 0xC1, 0x47, 0x18, 0xF2, 0xFF, 0x27, 
                /* 0380 */    0x28, 0x6B, 0x5C, 0xA8, 0xFB, 0x8A, 0xAF, 0x72, 
                /* 0388 */    0xEC, 0x3A, 0x85, 0xBB, 0x2A, 0x62, 0x60, 0x3D, 
                /* 0390 */    0x52, 0x0E, 0x6B, 0xB4, 0xB0, 0x07, 0xFC, 0xA6, 
                /* 0398 */    0xE5, 0x63, 0x9A, 0x67, 0x66, 0x8C, 0xB0, 0x1E, 
                /* 03A0 */    0xAD, 0x95, 0x92, 0xD2, 0x2B, 0x9F, 0x23, 0xDD, 
                /* 03A8 */    0xFA, 0x00, 0x41, 0x73, 0x79, 0x10, 0x78, 0xCE, 
                /* 03B0 */    0x7B, 0x4B, 0x78, 0x73, 0xF7, 0x59, 0xC2, 0xC7, 
                /* 03B8 */    0xBD, 0xC7, 0x82, 0x97, 0x80, 0x97, 0x81, 0xF7, 
                /* 03C0 */    0x92, 0x57, 0x5A, 0x76, 0xED, 0xF3, 0xAD, 0xCF, 
                /* 03C8 */    0x48, 0x0F, 0x80, 0x46, 0x09, 0x12, 0x23, 0xE6, 
                /* 03D0 */    0xFB, 0x89, 0x91, 0x1F, 0x6D, 0x7D, 0x69, 0xF0, 
                /* 03D8 */    0xBD, 0x2F, 0xC6, 0x5B, 0x1F, 0x8B, 0x77, 0xEB, 
                /* 03E0 */    0x03, 0x44, 0xFD, 0xFF, 0x6F, 0x7D, 0xC0, 0xFE, 
                /* 03E8 */    0x72, 0xF1, 0xD6, 0x07, 0x1C, 0x30, 0x23, 0xBE, 
                /* 03F0 */    0xF6, 0x01, 0x93, 0x34, 0x2B, 0xD0, 0x59, 0xC3, 
                /* 03F8 */    0x49, 0x40, 0x74, 0xED, 0xC3, 0xE9, 0x01, 0xD2, 
                /* 0400 */    0xB5, 0x0F, 0xAF, 0x03, 0x96, 0x8E, 0xDB, 0x0A, 
                /* 0408 */    0x60, 0x94, 0xE4, 0x58, 0x85, 0xD2, 0x7E, 0xAC, 
                /* 0410 */    0xA2, 0x20, 0x3E, 0xCE, 0xF8, 0xDA, 0x07, 0x58, 
                /* 0418 */    0xF9, 0xFF, 0x5F, 0xFB, 0x00, 0x26, 0x0E, 0x09, 
                /* 0420 */    0xE6, 0xF5, 0xE2, 0x09, 0xC7, 0x43, 0x02, 0xEB, 
                /* 0428 */    0x8D, 0xC6, 0x43, 0x82, 0xFB, 0xFF, 0x1F, 0x34, 
                /* 0430 */    0xD8, 0x86, 0x04, 0xE6, 0x8B, 0x9D, 0xAF, 0x8E, 
                /* 0438 */    0xC0, 0x59, 0xF6, 0x82, 0x75, 0x29, 0xE1, 0x42, 
                /* 0440 */    0x61, 0x74, 0xB4, 0x30, 0x88, 0x01, 0x7D, 0x75, 
                /* 0448 */    0x04, 0x7E, 0x17, 0x3E, 0xE0, 0x73, 0x75, 0x04, 
                /* 0450 */    0x0E, 0x17, 0x3E, 0xFC, 0xFF, 0xFF, 0xEA, 0x08, 
                /* 0458 */    0x38, 0xB8, 0xF1, 0x81, 0xF3, 0xEA, 0x08, 0xFC, 
                /* 0460 */    0x4C, 0x5C, 0x1D, 0x01, 0x1D, 0x2A, 0x46, 0x0E, 
                /* 0468 */    0x74, 0x4E, 0x31, 0x8C, 0xE0, 0xFF, 0x7F, 0x54, 
                /* 0470 */    0xE0, 0x06, 0xF6, 0xF1, 0x00, 0xD8, 0x8C, 0x0A, 
                /* 0478 */    0x18, 0x9C, 0x06, 0x7C, 0x09, 0x05, 0xBC, 0x2A, 
                /* 0480 */    0xB4, 0xE9, 0x53, 0xA3, 0x51, 0xAB, 0x06, 0x65, 
                /* 0488 */    0x6A, 0x94, 0x69, 0x50, 0xAB, 0x4F, 0xA5, 0xC6, 
                /* 0490 */    0x8C, 0x5D, 0x29, 0x13, 0x8C, 0xB1, 0x02, 0x8D, 
                /* 0498 */    0xC5, 0x22, 0x96, 0x23, 0x10, 0x87, 0x04, 0xA1, 
                /* 04A0 */    0x22, 0x1F, 0x43, 0x02, 0x71, 0x44, 0x10, 0x1A, 
                /* 04A8 */    0xE1, 0x4D, 0x23, 0x10, 0xC7, 0x5B, 0x9B, 0x40, 
                /* 04B0 */    0x2C, 0xEE, 0xA1, 0x21, 0x10, 0xFF, 0xFF, 0x83, 
                /* 04B8 */    0x3C, 0x23, 0x64, 0x04, 0x44, 0xA9, 0x40, 0x74, 
                /* 04C0 */    0x4B, 0x22, 0x6B, 0x12, 0x90, 0x95, 0x81, 0x08, 
                /* 04C8 */    0xC8, 0x81, 0x80, 0x68, 0x3A, 0x20, 0x2A, 0xEA, 
                /* 04D0 */    0x21, 0x20, 0x20, 0x2B, 0x04, 0x11, 0x90, 0xD5, 
                /* 04D8 */    0xD8, 0x00, 0x62, 0xDA, 0x40, 0x04, 0xE4, 0x5C, 
                /* 04E0 */    0x40, 0x34, 0x25, 0x10, 0x55, 0xA8, 0x03, 0x88, 
                /* 04E8 */    0xE9, 0x05, 0x11, 0x90, 0xB3, 0x02, 0xD1, 0xE4, 
                /* 04F0 */    0x40, 0x54, 0xB3, 0x0F, 0x20, 0x96, 0x00, 0x44, 
                /* 04F8 */    0x40, 0x4E, 0x4A, 0x23, 0x10, 0xEB, 0x54, 0x02, 
                /* 0500 */    0xC2, 0x52, 0xBD, 0x1D, 0x04, 0xE8, 0x88, 0x20, 
                /* 0508 */    0x02, 0xB2, 0xB2, 0x2F, 0xAB, 0x80, 0x2C, 0x13, 
                /* 0510 */    0x44, 0x40, 0x4E, 0x07, 0x44, 0xA3, 0x02, 0x51, 
                /* 0518 */    0x85, 0x56, 0x80, 0x98, 0x5C, 0x10, 0x01, 0x39, 
                /* 0520 */    0x25, 0x10, 0x8D, 0x0C, 0x44, 0x95, 0x6A, 0x01, 
                /* 0528 */    0x62, 0xB2, 0x41, 0x04, 0x64, 0x89, 0x5E, 0x80, 
                /* 0530 */    0x98, 0x60, 0x10, 0x01, 0x39, 0x2C, 0x10, 0x8D, 
                /* 0538 */    0x0E, 0x44, 0x65, 0xBF, 0x0A, 0x04, 0xE4, 0x10, 
                /* 0540 */    0x20, 0x3A, 0x25, 0x10, 0x33, 0x40, 0x4C, 0x0E, 
                /* 0548 */    0x88, 0x0E, 0x00, 0x04, 0x88, 0xC6, 0x02, 0xA2, 
                /* 0550 */    0x92, 0xFE, 0x5B, 0x02, 0xB2, 0x40, 0x10, 0x01, 
                /* 0558 */    0x39, 0x1C, 0x10, 0x8D, 0x0A, 0x44, 0xFF, 0xFF
            })
            OperationRegion (KBIO, SystemIO, 0x6C, 0x01)
            Field (KBIO, ByteAcc, Lock, Preserve)
            {
                    ,   5, 
                ECEP,   1
            }

            OperationRegion (RAMS, EmbeddedControl, 0x00, 0xFF)
            Field (RAMS, ByteAcc, Lock, Preserve)
            {
                CMD1,   8, 
                        Offset (0x08), 
                DAT2,   8, 
                DAT3,   8, 
                        Offset (0x4E), 
                SDID,   8
            }

            Method (WCOD, 0, NotSerialized)
            {
                Store (0x00, Local0)
                If (ECEP)
                {
                    If (\ECON)
                    {
                        Store (SDID, Local0)
                    }
                }

                If (LEqual (Local0, 0x00))
                {
                    Return (0x00)
                }

                If (LLess (Local0, 0x20))
                {
                    While (One)
                    {
                        Name (dit0, 0x00)
                        Store (And (Local0, 0xFF), dit0)
                        If (LEqual (dit0, 0x10))
                        {
                            \_SB.PCI0.LPCB.EC0._Q10 ()
                        }
                        Else
                        {
                            If (LEqual (dit0, 0x11))
                            {
                                \_SB.PCI0.LPCB.EC0._Q11 ()
                            }
                            Else
                            {
                                If (LEqual (dit0, 0x12))
                                {
                                    \_SB.PCI0.LPCB.EC0._Q12 ()
                                }
                                Else
                                {
                                    If (LEqual (dit0, 0x13))
                                    {
                                        \_SB.PCI0.LPCB.EC0._Q13 ()
                                    }
                                    Else
                                    {
                                        If (LEqual (dit0, 0x14))
                                        {
                                            \_SB.PCI0.LPCB.EC0._Q14 ()
                                        }
                                        Else
                                        {
                                            If (LEqual (dit0, 0x15))
                                            {
                                                \_SB.PCI0.LPCB.EC0._Q15 ()
                                            }
                                            Else
                                            {
                                                If (LEqual (dit0, 0x16))
                                                {
                                                    \_SB.PCI0.LPCB.EC0._Q16 ()
                                                }
                                                Else
                                                {
                                                    If (LEqual (dit0, 0x17))
                                                    {
                                                        \_SB.PCI0.LPCB.EC0._Q17 ()
                                                    }
                                                    Else
                                                    {
                                                        If (LEqual (dit0, 0x19))
                                                        {
                                                            \_SB.PCI0.LPCB.EC0._Q19 ()
                                                        }
                                                        Else
                                                        {
                                                            If (LEqual (dit0, 0x1A))
                                                            {
                                                                \_SB.PCI0.LPCB.EC0._Q1A ()
                                                            }
                                                            Else
                                                            {
                                                                If (LEqual (dit0, 0x1B))
                                                                {
                                                                    \_SB.PCI0.LPCB.EC0._Q1B ()
                                                                }
                                                                Else
                                                                {
                                                                    If (LEqual (dit0, 0x1C))
                                                                    {
                                                                        \_SB.PCI0.LPCB.EC0._Q1C ()
                                                                    }
                                                                    Else
                                                                    {
                                                                        If (LEqual (dit0, 0x1D))
                                                                        {
                                                                            \_SB.PCI0.LPCB.EC0._Q1D ()
                                                                        }
                                                                        Else
                                                                        {
                                                                            If (LEqual (dit0, 0x1E))
                                                                            {
                                                                                \_SB.PCI0.LPCB.EC0._Q1E ()
                                                                            }
                                                                            Else
                                                                            {
                                                                                If (LEqual (dit0, 0x1F))
                                                                                {
                                                                                    \_SB.PCI0.LPCB.EC0._Q1F ()
                                                                                }
                                                                            }
                                                                        }
                                                                    }
                                                                }
                                                            }
                                                        }
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }
                            }
                        }

                        Break
                    }
                }
                Else
                {
                    If (LLess (Local0, 0x30))
                    {
                        While (One)
                        {
                            Name (dit1, 0x00)
                            Store (And (Local0, 0xFF), dit1)
                            If (LEqual (dit1, 0x22))
                            {
                                \_SB.PCI0.LPCB.EC0._Q22 ()
                            }
                            Else
                            {
                                If (LEqual (dit1, 0x23))
                                {
                                    \_SB.PCI0.LPCB.EC0._Q23 ()
                                }
                                Else
                                {
                                    If (LEqual (dit1, 0x24))
                                    {
                                        \_SB.PCI0.LPCB.EC0._Q24 ()
                                    }
                                    Else
                                    {
                                        If (LEqual (dit1, 0x25))
                                        {
                                            \_SB.PCI0.LPCB.EC0._Q25 ()
                                        }
                                        Else
                                        {
                                            If (LEqual (dit1, 0x28))
                                            {
                                                \_SB.PCI0.LPCB.EC0._Q28 ()
                                            }
                                        }
                                    }
                                }
                            }

                            Break
                        }
                    }
                    Else
                    {
                        If (LLess (Local0, 0x40))
                        {
                            While (One)
                            {
                                Name (dit2, 0x00)
                                Store (And (Local0, 0xFF), dit2)
                                If (LEqual (dit2, 0x32))
                                {
                                    \_SB.PCI0.LPCB.EC0._Q32 ()
                                }
                                Else
                                {
                                    If (LEqual (dit2, 0x33))
                                    {
                                        \_SB.PCI0.LPCB.EC0._Q33 ()
                                    }
                                    Else
                                    {
                                        If (LEqual (dit2, 0x34))
                                        {
                                            \_SB.PCI0.LPCB.EC0._Q34 ()
                                        }
                                        Else
                                        {
                                            If (LEqual (dit2, 0x35))
                                            {
                                                \_SB.PCI0.LPCB.EC0._Q35 ()
                                            }
                                            Else
                                            {
                                                If (LEqual (dit2, 0x36))
                                                {
                                                    \_SB.PCI0.LPCB.EC0._Q36 ()
                                                }
                                                Else
                                                {
                                                    If (LEqual (dit2, 0x3F))
                                                    {
                                                        \_SB.PCI0.LPCB.EC0._Q3F ()
                                                    }
                                                }
                                            }
                                        }
                                    }
                                }

                                Break
                            }
                        }
                        Else
                        {
                            If (LLess (Local0, 0x50))
                            {
                                While (One)
                                {
                                    Name (dit3, 0x00)
                                    Store (And (Local0, 0xFF), dit3)
                                    If (LEqual (dit3, 0x40))
                                    {
                                        \_SB.PCI0.LPCB.EC0._Q40 ()
                                    }
                                    Else
                                    {
                                        If (LEqual (dit3, 0x41))
                                        {
                                            \_SB.PCI0.LPCB.EC0._Q41 ()
                                        }
                                        Else
                                        {
                                            If (LEqual (dit3, 0x48))
                                            {
                                                \_SB.PCI0.LPCB.EC0._Q48 ()
                                            }
                                            Else
                                            {
                                                If (LEqual (dit3, 0x4C))
                                                {
                                                    \_SB.PCI0.LPCB.EC0._Q4C ()
                                                }
                                            }
                                        }
                                    }

                                    Break
                                }
                            }
                            Else
                            {
                                If (LLess (Local0, 0x60))
                                {
                                    While (One)
                                    {
                                        Name (dit4, 0x00)
                                        Store (And (Local0, 0xFF), dit4)
                                        If (LEqual (dit4, 0x50))
                                        {
                                            \_SB.PCI0.LPCB.EC0._Q50 ()
                                        }
                                        Else
                                        {
                                            If (LEqual (dit4, 0x51))
                                            {
                                                \_SB.PCI0.LPCB.EC0._Q51 ()
                                            }
                                            Else
                                            {
                                                If (LEqual (dit4, 0x52))
                                                {
                                                    \_SB.PCI0.LPCB.EC0._Q52 ()
                                                }
                                                Else
                                                {
                                                    If (LEqual (dit4, 0x53))
                                                    {
                                                        \_SB.PCI0.LPCB.EC0._Q53 ()
                                                    }
                                                    Else
                                                    {
                                                        If (LEqual (dit4, 0x5C))
                                                        {
                                                            \_SB.PCI0.LPCB.EC0._Q5C ()
                                                        }
                                                    }
                                                }
                                            }
                                        }

                                        Break
                                    }
                                }
                                Else
                                {
                                    While (One)
                                    {
                                        Name (dit5, 0x00)
                                        Store (And (Local0, 0xFF), dit5)
                                        If (LEqual (dit5, 0x80))
                                        {
                                            \_SB.PCI0.LPCB.EC0._Q80 ()
                                        }
                                        Else
                                        {
                                            If (LEqual (dit5, 0x81))
                                            {
                                                \_SB.PCI0.LPCB.EC0._Q81 ()
                                            }
                                            Else
                                            {
                                                If (LEqual (dit5, 0x82))
                                                {
                                                    \_SB.PCI0.LPCB.EC0._Q82 ()
                                                }
                                                Else
                                                {
                                                    If (LEqual (dit5, 0x83))
                                                    {
                                                        \_SB.PCI0.LPCB.EC0._Q83 ()
                                                    }
                                                    Else
                                                    {
                                                        If (LEqual (dit5, 0x84))
                                                        {
                                                            \_SB.PCI0.LPCB.EC0._Q84 ()
                                                        }
                                                        Else
                                                        {
                                                            If (LEqual (dit5, 0x85))
                                                            {
                                                                \_SB.PCI0.LPCB.EC0._Q85 ()
                                                            }
                                                            Else
                                                            {
                                                                If (LEqual (dit5, 0x86))
                                                                {
                                                                    \_SB.PCI0.LPCB.EC0._Q86 ()
                                                                }
                                                            }
                                                        }
                                                    }
                                                }
                                            }
                                        }

                                        Break
                                    }
                                }
                            }
                        }
                    }
                }

                Return (Local0)
            }
        }

        Method (_INI, 0, NotSerialized)
        {
            If (DTSE)
            {
                TRAP (0x47)
            }

            Store (0x07D0, OSYS)
            If (CondRefOf (_OSI, Local0))
            {
                If (_OSI ("Linux"))
                {
                    Store (0x01, LINX)
                }

                If (_OSI ("Windows 2001"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP1"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP2"))
                {
                    Store (0x07D2, OSYS)
                }

                If (_OSI ("Windows 2006"))
                {
                    Store (0x07D6, OSYS)
                }
            }

            If (LAnd (MPEN, LEqual (OSYS, 0x07D1)))
            {
                TRAP (0x3D)
            }

            TRAP (0x2B)
            TRAP (0x32)
        }
    }

    OperationRegion (GNVS, SystemMemory, 0xBFEDEDBC, 0x0100)
    Field (GNVS, AnyAcc, Lock, Preserve)
    {
        OSYS,   16, 
        SMIF,   8, 
        PRM0,   8, 
        PRM1,   8, 
        SCIF,   8, 
        PRM2,   8, 
        PRM3,   8, 
        LCKF,   8, 
        PRM4,   8, 
        PRM5,   8, 
        P80D,   32, 
        LIDS,   8, 
        PWRS,   8, 
        DBGS,   8, 
        LINX,   8, 
                Offset (0x14), 
        ACT1,   8, 
        ACTT,   8, 
        PSVT,   8, 
        TC1V,   8, 
        TC2V,   8, 
        TSPV,   8, 
        CRTT,   8, 
        DTSE,   8, 
        DTS1,   8, 
        DTS2,   8, 
                Offset (0x25), 
        HSTE,   8, 
                Offset (0x28), 
        APIC,   8, 
        MPEN,   8, 
        PCP0,   8, 
        PCP1,   8, 
        PPCM,   8, 
                Offset (0x32), 
                Offset (0x39), 
        PEGD,   8, 
                Offset (0x3C), 
        IGDS,   8, 
        TLST,   8, 
        CADL,   8, 
        PADL,   8, 
        CSTE,   16, 
        NSTE,   16, 
        SSTE,   16, 
        NDID,   8, 
        DID1,   32, 
        DID2,   32, 
        DID3,   32, 
        DID4,   32, 
        DID5,   32, 
                Offset (0x64), 
        WNVA,   32, 
        WNVB,   32, 
        WNVC,   32, 
        WNVD,   32, 
        WFLG,   32, 
        WNVS,   32, 
        WNVI,   32, 
                Offset (0x82), 
        GTF0,   56, 
        GTF2,   56, 
        IDEM,   8, 
        GTF1,   56, 
                Offset (0xAA), 
        ASLB,   32, 
        IBTT,   8, 
        IPAT,   8, 
        ITVF,   8, 
        ITVM,   8, 
        IPSC,   8, 
        IBLC,   8, 
        IBIA,   8, 
        ISSC,   8, 
        I409,   8, 
        I509,   8, 
        I609,   8, 
        I709,   8, 
        IDMM,   8, 
        IDMS,   8, 
        IF1E,   8, 
        HVCO,   8, 
        NXD1,   32, 
        NXD2,   32, 
        NXD3,   32, 
        NXD4,   32, 
        NXD5,   32, 
        NXD6,   32, 
        NXD7,   32, 
        NXD8,   32, 
        OSCC,   8, 
        OSCS,   8, 
        NEXP,   8
    }

    Name (\DSEN, 0x01)
    Name (\ECON, 0x00)
    Name (\GPIC, 0x00)
    Name (\CTYP, 0x00)
    Name (\L01C, 0x00)
    Name (\VFN0, 0x00)
    Name (\VFN1, 0x00)
    Scope (\_GPE)
    {
        Method (_L01, 0, NotSerialized)
        {
            Add (L01C, 0x01, L01C)
            P8XH (0x00, 0x01)
            P8XH (0x01, L01C)
            If (LAnd (LEqual (RP1D, 0x00), \_SB.PCI0.RP01.HPSX))
            {
                Sleep (0x64)
                If (\_SB.PCI0.RP01.PDCX)
                {
                    Store (0x01, \_SB.PCI0.RP01.PDCX)
                    Store (0x01, \_SB.PCI0.RP01.HPSX)
                    Notify (\_SB.PCI0.RP01, 0x00)
                }
                Else
                {
                    Store (0x01, \_SB.PCI0.RP01.HPSX)
                }
            }

            If (LAnd (LEqual (RP2D, 0x00), \_SB.PCI0.RP02.HPSX))
            {
                Sleep (0x64)
                If (\_SB.PCI0.RP02.PDCX)
                {
                    Store (0x01, \_SB.PCI0.RP02.PDCX)
                    Store (0x01, \_SB.PCI0.RP02.HPSX)
                    Notify (\_SB.PCI0.RP02, 0x00)
                }
                Else
                {
                    Store (0x01, \_SB.PCI0.RP02.HPSX)
                }
            }

            If (LAnd (LEqual (RP3D, 0x00), \_SB.PCI0.RP03.HPSX))
            {
                Sleep (0x64)
                If (\_SB.PCI0.RP03.PDCX)
                {
                    Store (0x01, \_SB.PCI0.RP03.PDCX)
                    Store (0x01, \_SB.PCI0.RP03.HPSX)
                    Notify (\_SB.PCI0.RP03, 0x00)
                }
                Else
                {
                    Store (0x01, \_SB.PCI0.RP03.HPSX)
                }
            }

            If (LAnd (LEqual (RP4D, 0x00), \_SB.PCI0.RP04.HPSX))
            {
                Sleep (0x64)
                If (\_SB.PCI0.RP04.PDCX)
                {
                    Store (0x01, \_SB.PCI0.RP04.PDCX)
                    Store (0x01, \_SB.PCI0.RP04.HPSX)
                    Notify (\_SB.PCI0.RP04, 0x00)
                }
                Else
                {
                    Store (0x01, \_SB.PCI0.RP04.HPSX)
                }
            }

            If (LAnd (LEqual (RP5D, 0x00), \_SB.PCI0.RP05.HPSX))
            {
                Sleep (0x64)
                If (\_SB.PCI0.RP05.PDCX)
                {
                    Store (0x01, \_SB.PCI0.RP05.PDCX)
                    Store (0x01, \_SB.PCI0.RP05.HPSX)
                    Notify (\_SB.PCI0.RP05, 0x00)
                }
                Else
                {
                    Store (0x01, \_SB.PCI0.RP05.HPSX)
                }
            }

            If (LAnd (LEqual (RP6D, 0x00), \_SB.PCI0.RP06.HPSX))
            {
                Sleep (0x64)
                If (\_SB.PCI0.RP06.PDCX)
                {
                    Store (0x01, \_SB.PCI0.RP06.PDCX)
                    Store (0x01, \_SB.PCI0.RP06.HPSX)
                    Notify (\_SB.PCI0.RP06, 0x00)
                }
                Else
                {
                    Store (0x01, \_SB.PCI0.RP06.HPSX)
                }
            }
        }

        Method (_L03, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB1, 0x02)
        }

        Method (_L04, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB2, 0x02)
        }

        Method (_L05, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB5, 0x02)
        }

        Method (_L06, 0, NotSerialized)
        {
            If (\_SB.PCI0.GFX0.GSSE)
            {
                \_SB.PCI0.GFX0.GSCI ()
            }
            Else
            {
                Store (0x01, SCIS)
            }
        }

        Method (_L07, 0, NotSerialized)
        {
            Store (0x20, \_SB.PCI0.SBUS.HSTS)
        }

        Method (_L09, 0, NotSerialized)
        {
            If (\_SB.PCI0.RP01.PSPX)
            {
                Store (0x01, \_SB.PCI0.RP01.PSPX)
                Store (0x01, \_SB.PCI0.RP01.PMSX)
                Notify (\_SB.PCI0.RP01, 0x02)
            }

            If (\_SB.PCI0.RP02.PSPX)
            {
                Store (0x01, \_SB.PCI0.RP02.PSPX)
                Store (0x01, \_SB.PCI0.RP02.PMSX)
                Notify (\_SB.PCI0.RP02, 0x02)
            }

            If (\_SB.PCI0.RP03.PSPX)
            {
                Store (0x01, \_SB.PCI0.RP03.PSPX)
                Store (0x01, \_SB.PCI0.RP03.PMSX)
                Notify (\_SB.PCI0.RP03, 0x02)
            }

            If (\_SB.PCI0.RP04.PSPX)
            {
                Store (0x01, \_SB.PCI0.RP04.PSPX)
                Store (0x01, \_SB.PCI0.RP04.PMSX)
                Notify (\_SB.PCI0.RP04, 0x02)
            }

            If (\_SB.PCI0.RP05.PSPX)
            {
                Store (0x01, \_SB.PCI0.RP05.PSPX)
                Store (0x01, \_SB.PCI0.RP05.PMSX)
                Notify (\_SB.PCI0.RP05, 0x02)
            }

            If (\_SB.PCI0.RP06.PSPX)
            {
                Store (0x01, \_SB.PCI0.RP06.PSPX)
                Store (0x01, \_SB.PCI0.RP06.PMSX)
                Notify (\_SB.PCI0.RP06, 0x02)
            }
        }

        Method (_L0B, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.PCIB, 0x02)
        }

        Method (_L0C, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB3, 0x02)
            Notify (\_SB.SLPB, 0x02)
        }

        Method (_L0D, 0, NotSerialized)
        {
            If (\_SB.PCI0.EHC1.PMES)
            {
                Store (0x01, \_SB.PCI0.EHC1.PMES)
                Notify (\_SB.PCI0.EHC1, 0x02)
            }

            If (\_SB.PCI0.EHC2.PMES)
            {
                Store (0x01, \_SB.PCI0.EHC2.PMES)
                Notify (\_SB.PCI0.EHC2, 0x02)
            }

            If (\_SB.PCI0.HDEF.PMES)
            {
                Store (0x01, \_SB.PCI0.HDEF.PMES)
                Notify (\_SB.PCI0.HDEF, 0x02)
            }

            If (\_SB.PCI0.LANC.PMES)
            {
                Store (0x01, \_SB.PCI0.LANC.PMES)
                Notify (\_SB.PCI0.LANC, 0x02)
            }
        }

        Method (_L0E, 0, NotSerialized)
        {
            Notify (\_SB.PCI0.USB4, 0x02)
        }

        Method (_L1C, 0, NotSerialized)
        {
            Store (0x1D, P80H)
            Notify (\_SB.SLPB, 0x02)
        }
    }

    Scope (\_PR)
    {
        Processor (CPU0, 0x00, 0x00001010, 0x06) {}
        Processor (CPU1, 0x01, 0x00001010, 0x06) {}
        Method (RPPC, 0, NotSerialized)
        {
            If (LEqual (OSYS, 0x07D2))
            {
                If (And (CFGD, 0x01))
                {
                    If (LGreater (\_PR.CPU0._PPC, 0x00))
                    {
                        Subtract (\_PR.CPU0._PPC, 0x01, \_PR.CPU0._PPC)
                        PNOT ()
                        Add (\_PR.CPU0._PPC, 0x01, \_PR.CPU0._PPC)
                        PNOT ()
                    }
                    Else
                    {
                        Add (\_PR.CPU0._PPC, 0x01, \_PR.CPU0._PPC)
                        PNOT ()
                        Subtract (\_PR.CPU0._PPC, 0x01, \_PR.CPU0._PPC)
                        PNOT ()
                    }
                }
            }
        }
    }

    Scope (\_TZ)
    {
        Name (TBSE, 0x0AAC)
        Name (CRT0, 0x00)
        Name (PSV0, 0x00)
        Name (PSVA, 0x00)
        ThermalZone (TZS0)
        {
            Method (_TMP, 0, NotSerialized)
            {
                If (\ECON)
                {
                    Store (\_SB.PCI0.LPCB.EC0.THS0, Local0)
                    Store (\_SB.PCI0.LPCB.EC0.KCSS, Local1)
                    Store (\_SB.PCI0.LPCB.EC0.KOSD, Local2)
                }
                Else
                {
                    Store (RBEC (0x92), Local0)
                    And (Local0, 0x01, Local1)
                    And (Local0, 0x08, Local2)
                    Store (RBEC (0xA8), Local0)
                }

                If (LOr (Local1, PSVA))
                {
                    If (LGreaterEqual (PSVA, 0x01))
                    {
                        Subtract (CRT0, 0x02, Local0)
                    }
                    Else
                    {
                        If (LLessEqual (Local0, PSV0))
                        {
                            Add (PSV0, 0x02, Local0)
                        }
                    }
                }

                If (Local2)
                {
                    If (LLessEqual (Local0, CRT0))
                    {
                        Add (CRT0, 0x02, Local0)
                    }
                }

                Return (C2K (Local0))
            }

            Method (_CRT, 0, NotSerialized)
            {
                If (\ECON)
                {
                    Store (0x20, \_SB.PCI0.LPCB.EC0.TIID)
                    Store (\_SB.PCI0.LPCB.EC0.TSC0, Local0)
                }
                Else
                {
                    WBEC (0x01, 0x20)
                    Store (RBEC (0xD1), Local0)
                }

                If (LOr (LGreaterEqual (Local0, 0x80), LLess (Local0, 0x1E)))
                {
                    Store (0x78, Local0)
                }

                Store (Local0, CRT0)
                Return (C2K (Local0))
            }

            Method (_PSL, 0, Serialized)
            {
                If (MPEN)
                {
                    Return (Package (0x02)
                    {
                        \_PR.CPU0, 
                        \_PR.CPU1
                    })
                }

                Return (Package (0x01)
                {
                    \_PR.CPU0
                })
            }

            Method (_PSV, 0, NotSerialized)
            {
                If (\ECON)
                {
                    Store (0x20, \_SB.PCI0.LPCB.EC0.TIID)
                    Store (\_SB.PCI0.LPCB.EC0.TSP0, Local0)
                }
                Else
                {
                    WBEC (0x01, 0x20)
                    Store (RBEC (0xD0), Local0)
                }

                If (LOr (LGreaterEqual (Local0, 0x80), LLess (Local0, 0x1E)))
                {
                    Store (0x5A, Local0)
                }

                Store (Local0, PSV0)
                Return (C2K (Local0))
            }

            Name (_TC1, 0x04)
            Name (_TC2, 0x03)
            Name (_TSP, 0x96)
        }

        ThermalZone (TZS1)
        {
            Method (_TMP, 0, NotSerialized)
            {
                If (\ECON)
                {
                    Store (\_SB.PCI0.LPCB.EC0.THS1, Local0)
                }
                Else
                {
                    Store (RBEC (0xA9), Local0)
                }

                Return (C2K (Local0))
            }

            Method (_CRT, 0, NotSerialized)
            {
                If (\ECON)
                {
                    Store (0x20, \_SB.PCI0.LPCB.EC0.TIID)
                    Store (\_SB.PCI0.LPCB.EC0.TSC1, Local0)
                }
                Else
                {
                    WBEC (0x01, 0x20)
                    Store (RBEC (0xD3), Local0)
                }

                If (LOr (LGreaterEqual (Local0, 0x80), LLess (Local0, 0x1E)))
                {
                    Store (0x78, Local0)
                }

                Return (C2K (Local0))
            }
        }

        Method (C2K, 1, NotSerialized)
        {
            Store (Arg0, Local0)
            If (LLessEqual (Local0, 0x10))
            {
                Store (0x1E, Local0)
            }

            If (LGreaterEqual (Local0, 0x7F))
            {
                Store (0x1E, Local0)
            }

            Add (Multiply (Local0, 0x0A), TBSE, Local0)
            Return (Local0)
        }

        Method (SPSV, 2, NotSerialized)
        {
            ShiftLeft (0x01, Arg0, Local0)
            If (Arg1)
            {
                Or (PSVA, Local0, PSVA)
            }
            Else
            {
                And (PSVA, Not (Local0), PSVA)
            }
        }
    }

    Scope (\_SB)
    {
        Device (LID0)
        {
            Name (_HID, EisaId ("PNP0C0D"))
            Method (_LID, 0, NotSerialized)
            {
                If (\ECON)
                {
                    Store (\_SB.PCI0.LPCB.EC0.KLID, Local0)
                }
                Else
                {
                    And (\RBEC (0x70), 0x02, Local0)
                    ShiftRight (Local0, 0x01, Local0)
                }

                Store (Local0, LIDS)
                Return (Local0)
            }

            Method (_PSW, 1, NotSerialized)
            {
                If (\ECON)
                {
                    Store (Arg0, \_SB.PCI0.LPCB.EC0.LIDW)
                }
                Else
                {
                    If (Arg0)
                    {
                        \MBEC (0x72, 0xEF, 0x10)
                    }
                    Else
                    {
                        \MBEC (0x72, 0xEF, 0x00)
                    }
                }
            }

            Name (_PRW, Package (0x02)
            {
                0x1C, 
                0x03
            })
        }

        Device (SLPB)
        {
            Name (_HID, EisaId ("PNP0C0E"))
            Name (_PRW, Package (0x02)
            {
                0x1C, 
                0x03
            })
        }

        Device (PCI0)
        {
            Method (_S3D, 0, NotSerialized)
            {
                Return (0x02)
            }

            Method (_S4D, 0, NotSerialized)
            {
                Return (0x02)
            }

            Name (_HID, EisaId ("PNP0A08"))
            Name (_CID, EisaId ("PNP0A03"))
            Device (MCHC)
            {
                Name (_ADR, 0x00)
                OperationRegion (HBUS, PCI_Config, 0x40, 0xC0)
                Field (HBUS, DWordAcc, NoLock, Preserve)
                {
                    EPEN,   1, 
                        ,   11, 
                    EPBR,   20, 
                            Offset (0x08), 
                    MHEN,   1, 
                        ,   13, 
                    MHBR,   18, 
                            Offset (0x20), 
                    PXEN,   1, 
                    PXSZ,   2, 
                        ,   23, 
                    PXBR,   6, 
                            Offset (0x28), 
                    DIEN,   1, 
                        ,   11, 
                    DIBR,   20, 
                            Offset (0x30), 
                    IPEN,   1, 
                        ,   11, 
                    IPBR,   20, 
                            Offset (0x50), 
                        ,   4, 
                    PM0H,   2, 
                            Offset (0x51), 
                    PM1L,   2, 
                        ,   2, 
                    PM1H,   2, 
                            Offset (0x52), 
                    PM2L,   2, 
                        ,   2, 
                    PM2H,   2, 
                            Offset (0x53), 
                    PM3L,   2, 
                        ,   2, 
                    PM3H,   2, 
                            Offset (0x54), 
                    PM4L,   2, 
                        ,   2, 
                    PM4H,   2, 
                            Offset (0x55), 
                    PM5L,   2, 
                        ,   2, 
                    PM5H,   2, 
                            Offset (0x56), 
                    PM6L,   2, 
                        ,   2, 
                    PM6H,   2, 
                            Offset (0x57), 
                        ,   7, 
                    HENA,   1, 
                            Offset (0x62), 
                    TUUD,   16, 
                            Offset (0x70), 
                        ,   4, 
                    TLUD,   12, 
                            Offset (0xA4), 
                        ,   1, 
                    IGDD,   1
                }
            }

            Name (BUF0, ResourceTemplate ()
            {
                WordBusNumber (ResourceProducer, MinFixed, MaxFixed, PosDecode,
                    0x0000,             // Granularity
                    0x0000,             // Range Minimum
                    0x00FF,             // Range Maximum
                    0x0000,             // Translation Offset
                    0x0100,             // Length
                    ,, )
                DWordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0x00000CF7,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000CF8,         // Length
                    ,, , TypeStatic)
                IO (Decode16,
                    0x0CF8,             // Range Minimum
                    0x0CF8,             // Range Maximum
                    0x01,               // Alignment
                    0x08,               // Length
                    )
                DWordIO (ResourceProducer, MinFixed, MaxFixed, PosDecode, EntireRange,
                    0x00000000,         // Granularity
                    0x00000D00,         // Range Minimum
                    0x0000FFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x0000F300,         // Length
                    ,, , TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000A0000,         // Range Minimum
                    0x000BFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00020000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C0000,         // Range Minimum
                    0x000C3FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y00, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C4000,         // Range Minimum
                    0x000C7FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y01, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000C8000,         // Range Minimum
                    0x000CBFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y02, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000CC000,         // Range Minimum
                    0x000CFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y03, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D0000,         // Range Minimum
                    0x000D3FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y04, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D4000,         // Range Minimum
                    0x000D7FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y05, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000D8000,         // Range Minimum
                    0x000DBFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y06, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000DC000,         // Range Minimum
                    0x000DFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y07, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000E0000,         // Range Minimum
                    0x000E3FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y08, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000E4000,         // Range Minimum
                    0x000E7FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y09, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000E8000,         // Range Minimum
                    0x000EBFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y0A, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000EC000,         // Range Minimum
                    0x000EFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00004000,         // Length
                    ,, _Y0B, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x000F0000,         // Range Minimum
                    0x000FFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00010000,         // Length
                    ,, _Y0C, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0xDFFFFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000000,         // Length
                    ,, _Y0D, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0xF0000000,         // Range Minimum
                    0xFEBFFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x0EC00000,         // Length
                    ,, _Y0E, AddressRangeMemory, TypeStatic)
                DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0xFED40000,         // Range Minimum
                    0xFED44FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)
            })
            Method (_CRS, 0, Serialized)
            {
                If (^MCHC.PM1L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y00._LEN, C0LN)
                    Store (Zero, C0LN)
                }

                If (LEqual (^MCHC.PM1L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y00._RW, C0RW)
                    Store (Zero, C0RW)
                }

                If (^MCHC.PM1H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y01._LEN, C4LN)
                    Store (Zero, C4LN)
                }

                If (LEqual (^MCHC.PM1H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y01._RW, C4RW)
                    Store (Zero, C4RW)
                }

                If (^MCHC.PM2L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y02._LEN, C8LN)
                    Store (Zero, C8LN)
                }

                If (LEqual (^MCHC.PM2L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y02._RW, C8RW)
                    Store (Zero, C8RW)
                }

                If (^MCHC.PM2H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y03._LEN, CCLN)
                    Store (Zero, CCLN)
                }

                If (LEqual (^MCHC.PM2H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y03._RW, CCRW)
                    Store (Zero, CCRW)
                }

                If (^MCHC.PM3L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y04._LEN, D0LN)
                    Store (Zero, D0LN)
                }

                If (LEqual (^MCHC.PM3L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y04._RW, D0RW)
                    Store (Zero, D0RW)
                }

                If (^MCHC.PM3H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y05._LEN, D4LN)
                    Store (Zero, D4LN)
                }

                If (LEqual (^MCHC.PM3H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y05._RW, D4RW)
                    Store (Zero, D4RW)
                }

                If (^MCHC.PM4L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y06._LEN, D8LN)
                    Store (Zero, D8LN)
                }

                If (LEqual (^MCHC.PM4L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y06._RW, D8RW)
                    Store (Zero, D8RW)
                }

                If (^MCHC.PM4H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y07._LEN, DCLN)
                    Store (Zero, DCLN)
                }

                If (LEqual (^MCHC.PM4H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y07._RW, DCRW)
                    Store (Zero, DCRW)
                }

                If (^MCHC.PM5L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y08._LEN, E0LN)
                    Store (Zero, E0LN)
                }

                If (LEqual (^MCHC.PM5L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y08._RW, E0RW)
                    Store (Zero, E0RW)
                }

                If (^MCHC.PM5H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y09._LEN, E4LN)
                    Store (Zero, E4LN)
                }

                If (LEqual (^MCHC.PM5H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y09._RW, E4RW)
                    Store (Zero, E4RW)
                }

                If (^MCHC.PM6L)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y0A._LEN, E8LN)
                    Store (Zero, E8LN)
                }

                If (LEqual (^MCHC.PM6L, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y0A._RW, E8RW)
                    Store (Zero, E8RW)
                }

                If (^MCHC.PM6H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y0B._LEN, ECLN)
                    Store (Zero, ECLN)
                }

                If (LEqual (^MCHC.PM6H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y0B._RW, ECRW)
                    Store (Zero, ECRW)
                }

                If (^MCHC.PM0H)
                {
                    CreateDWordField (BUF0, \_SB.PCI0._Y0C._LEN, F0LN)
                    Store (Zero, F0LN)
                }

                If (LEqual (^MCHC.PM0H, 0x01))
                {
                    CreateBitField (BUF0, \_SB.PCI0._Y0C._RW, F0RW)
                    Store (Zero, F0RW)
                }

                CreateDWordField (BUF0, \_SB.PCI0._Y0D._MIN, M1MN)
                CreateDWordField (BUF0, \_SB.PCI0._Y0D._MAX, M1MX)
                CreateDWordField (BUF0, \_SB.PCI0._Y0D._LEN, M1LN)
                CreateDWordField (BUF0, \_SB.PCI0._Y0E._MIN, M2MN)
                CreateDWordField (BUF0, \_SB.PCI0._Y0E._MAX, M2MX)
                CreateDWordField (BUF0, \_SB.PCI0._Y0E._LEN, M2LN)
                ShiftLeft (^MCHC.PXBR, 0x1A, M1MX)
                ShiftRight (0x10000000, ^MCHC.PXSZ, Local0)
                Add (M1MX, Local0, M2MN)
                Add (Subtract (M2MX, M2MN), 0x01, M2LN)
                Subtract (M1MX, 0x01, M1MX)
                ShiftLeft (^MCHC.TLUD, 0x14, M1MN)
                Add (Subtract (M1MX, M1MN), 0x01, M1LN)
                Return (BUF0)
            }

            Method (_PRT, 0, NotSerialized)
            {
                If (GPIC)
                {
                    Return (Package (0x17)
                    {
                        Package (0x04)
                        {
                            0x0001FFFF, 
                            0x00, 
                            0x00, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x0002FFFF, 
                            0x00, 
                            0x00, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x0003FFFF, 
                            0x00, 
                            0x00, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x0003FFFF, 
                            0x01, 
                            0x00, 
                            0x11
                        }, 

                        Package (0x04)
                        {
                            0x0003FFFF, 
                            0x02, 
                            0x00, 
                            0x12
                        }, 

                        Package (0x04)
                        {
                            0x0003FFFF, 
                            0x03, 
                            0x00, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x0007FFFF, 
                            0x00, 
                            0x00, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x0019FFFF, 
                            0x00, 
                            0x00, 
                            0x14
                        }, 

                        Package (0x04)
                        {
                            0x001AFFFF, 
                            0x00, 
                            0x00, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x001AFFFF, 
                            0x01, 
                            0x00, 
                            0x15
                        }, 

                        Package (0x04)
                        {
                            0x001AFFFF, 
                            0x02, 
                            0x00, 
                            0x12
                        }, 

                        Package (0x04)
                        {
                            0x001BFFFF, 
                            0x00, 
                            0x00, 
                            0x16
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x00, 
                            0x00, 
                            0x11
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x01, 
                            0x00, 
                            0x10
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x02, 
                            0x00, 
                            0x12
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x03, 
                            0x00, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x00, 
                            0x00, 
                            0x17
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x01, 
                            0x00, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x02, 
                            0x00, 
                            0x12
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x00, 
                            0x00, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x01, 
                            0x00, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x02, 
                            0x00, 
                            0x13
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x03, 
                            0x00, 
                            0x10
                        }
                    })
                }
                Else
                {
                    Return (Package (0x17)
                    {
                        Package (0x04)
                        {
                            0x0001FFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKA, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x0002FFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKA, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x0003FFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKA, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x0003FFFF, 
                            0x01, 
                            \_SB.PCI0.LPCB.LNKB, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x0003FFFF, 
                            0x02, 
                            \_SB.PCI0.LPCB.LNKC, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x0003FFFF, 
                            0x03, 
                            \_SB.PCI0.LPCB.LNKD, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x0007FFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKA, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x0019FFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKE, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001AFFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKA, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001AFFFF, 
                            0x01, 
                            \_SB.PCI0.LPCB.LNKF, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001AFFFF, 
                            0x02, 
                            \_SB.PCI0.LPCB.LNKC, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001BFFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKG, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKB, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x01, 
                            \_SB.PCI0.LPCB.LNKA, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x02, 
                            \_SB.PCI0.LPCB.LNKC, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001CFFFF, 
                            0x03, 
                            \_SB.PCI0.LPCB.LNKD, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKH, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x01, 
                            \_SB.PCI0.LPCB.LNKD, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001DFFFF, 
                            0x02, 
                            \_SB.PCI0.LPCB.LNKC, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x00, 
                            \_SB.PCI0.LPCB.LNKD, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x01, 
                            \_SB.PCI0.LPCB.LNKD, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x02, 
                            \_SB.PCI0.LPCB.LNKD, 
                            0x00
                        }, 

                        Package (0x04)
                        {
                            0x001FFFFF, 
                            0x03, 
                            \_SB.PCI0.LPCB.LNKA, 
                            0x00
                        }
                    })
                }
            }

            Device (PDRC)
            {
                Name (_HID, EisaId ("PNP0C02"))
                Name (_UID, 0x01)
                Name (BUF0, ResourceTemplate ()
                {
                    Memory32Fixed (ReadWrite,
                        0x00000000,         // Address Base
                        0x00004000,         // Address Length
                        _Y0F)
                    Memory32Fixed (ReadWrite,
                        0x00000000,         // Address Base
                        0x00004000,         // Address Length
                        _Y10)
                    Memory32Fixed (ReadWrite,
                        0x00000000,         // Address Base
                        0x00001000,         // Address Length
                        _Y11)
                    Memory32Fixed (ReadWrite,
                        0x00000000,         // Address Base
                        0x00001000,         // Address Length
                        _Y12)
                    Memory32Fixed (ReadWrite,
                        0x00000000,         // Address Base
                        0x00000000,         // Address Length
                        _Y13)
                    Memory32Fixed (ReadWrite,
                        0xFED20000,         // Address Base
                        0x00020000,         // Address Length
                        )
                    Memory32Fixed (ReadWrite,
                        0xFED45000,         // Address Base
                        0x0004B000,         // Address Length
                        )
                })
                Method (_CRS, 0, Serialized)
                {
                    CreateDWordField (BUF0, \_SB.PCI0.PDRC._Y0F._BAS, RBR0)
                    ShiftLeft (\_SB.PCI0.LPCB.RCBA, 0x0E, RBR0)
                    CreateDWordField (BUF0, \_SB.PCI0.PDRC._Y10._BAS, MBR0)
                    ShiftLeft (\_SB.PCI0.MCHC.MHBR, 0x0E, MBR0)
                    CreateDWordField (BUF0, \_SB.PCI0.PDRC._Y11._BAS, DBR0)
                    ShiftLeft (\_SB.PCI0.MCHC.DIBR, 0x0C, DBR0)
                    CreateDWordField (BUF0, \_SB.PCI0.PDRC._Y12._BAS, EBR0)
                    ShiftLeft (\_SB.PCI0.MCHC.EPBR, 0x0C, EBR0)
                    CreateDWordField (BUF0, \_SB.PCI0.PDRC._Y13._BAS, XBR0)
                    ShiftLeft (\_SB.PCI0.MCHC.PXBR, 0x1A, XBR0)
                    CreateDWordField (BUF0, \_SB.PCI0.PDRC._Y13._LEN, XSZ0)
                    ShiftRight (0x10000000, \_SB.PCI0.MCHC.PXSZ, XSZ0)
                    Return (BUF0)
                }
            }

            Device (PEGP)
            {
                Name (_ADR, 0x00010000)
                Method (_STA, 0, NotSerialized)
                {
                    If (LEqual (PHSR (0x2D, 0x00), 0x00))
                    {
                        Return (0x00)
                    }
                    Else
                    {
                        Return (0x0F)
                    }
                }

                Device (VGA)
                {
                    Name (_ADR, 0x00)
                    Method (_DOS, 1, NotSerialized)
                    {
                        Store (And (Arg0, 0x03), DSEN)
                    }

                    Method (_DOD, 0, NotSerialized)
                    {
                        If (LEqual (PEGD, 0x03))
                        {
                            Return (Package (0x04)
                            {
                                0x00010100, 
                                0x00010200, 
                                0x00010118, 
                                0x00010120
                            })
                        }
                        Else
                        {
                            Return (Package (0x04)
                            {
                                0x00010100, 
                                0x00010200, 
                                0x00010110, 
                                0x00010210
                            })
                        }
                    }

                    Device (CRT)
                    {
                        Name (_ADR, 0x0100)
                        Method (_DCS, 0, NotSerialized)
                        {
                            PHSR (0x25, 0x00)
                            If (And (CSTE, 0x0101))
                            {
                                Return (0x1F)
                            }

                            Return (0x1D)
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (And (NSTE, 0x0101))
                            {
                                Return (0x01)
                            }

                            Return (0x00)
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                            If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                            {
                                Store (NSTE, CSTE)
                            }
                        }
                    }

                    Device (LCD)
                    {
                        Method (_ADR, 0, NotSerialized)
                        {
                            If (LEqual (PEGD, 0x03))
                            {
                                Return (0x0118)
                            }
                            Else
                            {
                                Return (0x0110)
                            }
                        }

                        Method (_DCS, 0, NotSerialized)
                        {
                            PHSR (0x25, 0x00)
                            If (And (CSTE, 0x0808))
                            {
                                Return (0x1F)
                            }

                            Return (0x1D)
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (And (NSTE, 0x0808))
                            {
                                Return (0x01)
                            }

                            Return (0x00)
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                            If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                            {
                                Store (NSTE, CSTE)
                            }
                        }

                        Method (_DDC, 1, NotSerialized)
                        {
                            If (LEqual (Arg0, 0x01))
                            {
                                Return (\_SB.PCI0.PEGP.VGA.DDC4)
                            }

                            If (LEqual (Arg0, 0x02))
                            {
                                Concatenate (\_SB.PCI0.PEGP.VGA.DDC4, \_SB.PCI0.PEGP.VGA.DDC0, Local0)
                                Return (Local0)
                            }

                            Return (0x00)
                        }

                        Method (_BCL, 0, NotSerialized)
                        {
                            Return (BCLP)
                        }

                        Method (_BCM, 1, NotSerialized)
                        {
                            Store (0x01, Local0)
                            Store (0x02, Local1)
                            While (Local0)
                            {
                                If (LEqual (Arg0, DerefOf (Index (BCLP, Local1))))
                                {
                                    Store (0x00, Local0)
                                }
                                Else
                                {
                                    Increment (Local1)
                                    If (LEqual (0x11, Local1))
                                    {
                                        Store (0x00, Local0)
                                    }
                                }
                            }

                            Decrement (Local1)
                            Decrement (Local1)
                            If (\_SB.PCI0.LPCB.EC0.BNCM)
                            {
                                If (\_SB.PCI0.LPCB.EC0.ACST)
                                {
                                    Store (Local1, \_SB.PCI0.LPCB.EC0.BNAC)
                                }
                                Else
                                {
                                    Store (Local1, \_SB.PCI0.LPCB.EC0.BNDC)
                                }
                            }
                            Else
                            {
                                Store (Local1, \_SB.PCI0.LPCB.EC0.BNAC)
                            }
                        }

                        Method (_BQC, 0, NotSerialized)
                        {
                            If (\_SB.PCI0.LPCB.EC0.BNCM)
                            {
                                If (\_SB.PCI0.LPCB.EC0.ACST)
                                {
                                    Store (\_SB.PCI0.LPCB.EC0.BNAC, Local1)
                                }
                                Else
                                {
                                    Store (\_SB.PCI0.LPCB.EC0.BNDC, Local1)
                                }
                            }
                            Else
                            {
                                Store (\_SB.PCI0.LPCB.EC0.BNAC, Local1)
                            }

                            Increment (Local1)
                            Increment (Local1)
                            Store (DerefOf (Index (BCLP, Local1)), Local0)
                            Return (Local0)
                        }
                    }

                    Device (TV0)
                    {
                        Name (_ADR, 0x0200)
                        Method (_DCS, 0, NotSerialized)
                        {
                            PHSR (0x25, 0x00)
                            If (And (CSTE, 0x0202))
                            {
                                Return (0x1F)
                            }

                            Return (0x1D)
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (And (NSTE, 0x0202))
                            {
                                Return (0x01)
                            }

                            Return (0x00)
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                            If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                            {
                                Store (NSTE, CSTE)
                            }
                        }

                        Method (_DDC, 1, NotSerialized)
                        {
                            If (LEqual (Arg0, 0x01))
                            {
                                Return (\_SB.PCI0.PEGP.VGA.DDC3)
                            }

                            If (LEqual (Arg0, 0x02))
                            {
                                Concatenate (\_SB.PCI0.PEGP.VGA.DDC3, \_SB.PCI0.PEGP.VGA.DDC0, Local0)
                                Return (Local0)
                            }

                            Return (0x00)
                        }
                    }

                    Device (DVI)
                    {
                        Method (_ADR, 0, NotSerialized)
                        {
                            If (LEqual (PEGD, 0x03))
                            {
                                Return (0x0120)
                            }
                            Else
                            {
                                Return (0x0210)
                            }
                        }

                        Method (_DCS, 0, NotSerialized)
                        {
                            PHSR (0x25, 0x00)
                            If (And (CSTE, 0x0404))
                            {
                                Return (0x1F)
                            }

                            Return (0x1D)
                        }

                        Method (_DGS, 0, NotSerialized)
                        {
                            If (And (NSTE, 0x0404))
                            {
                                Return (0x01)
                            }

                            Return (0x00)
                        }

                        Method (_DSS, 1, NotSerialized)
                        {
                            If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                            {
                                Store (NSTE, CSTE)
                            }
                        }
                    }

                    Name (DDC0, Buffer (0x80)
                    {
                        /* 0000 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0008 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0010 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0018 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0020 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0028 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0030 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0038 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0040 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0048 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0050 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0058 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0060 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0068 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0070 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0078 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00
                    })
                    Name (DDC3, Buffer (0x80)
                    {
                        /* 0000 */    0x00, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0x00, 
                        /* 0008 */    0x41, 0xD0, 0xFE, 0x09, 0x00, 0x00, 0x00, 0x00, 
                        /* 0010 */    0x00, 0x00, 0x02, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0018 */    0xF0, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0020 */    0x00, 0x00, 0x00, 0x21, 0x08, 0x00, 0x00, 0x00, 
                        /* 0028 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0030 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0038 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0040 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0048 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0050 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0058 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0060 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0068 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0070 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0078 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xD3
                    })
                    Name (DDC4, Buffer (0x80)
                    {
                        /* 0000 */    0x00, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0xFF, 0x00, 
                        /* 0008 */    0x36, 0x7F, 0x03, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0010 */    0x00, 0x00, 0x02, 0x00, 0x01, 0x28, 0x1E, 0x00, 
                        /* 0018 */    0xF0, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0020 */    0x00, 0x00, 0x00, 0x21, 0x08, 0x00, 0x00, 0x00, 
                        /* 0028 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0030 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0038 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0040 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0048 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0050 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0058 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0060 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0068 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0070 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                        /* 0078 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0xEC
                    })
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (GPIC)
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                0x00, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                0x00, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                0x00, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                0x00, 
                                0x13
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKA, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                \_SB.PCI0.LPCB.LNKB, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                \_SB.PCI0.LPCB.LNKC, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                \_SB.PCI0.LPCB.LNKD, 
                                0x00
                            }
                        })
                    }
                }
            }

            Device (GFX0)
            {
                Name (_ADR, 0x00020000)
                Method (_DOS, 1, NotSerialized)
                {
                    Store (And (Arg0, 0x03), DSEN)
                }

                Method (_DOD, 0, NotSerialized)
                {
                    Store (NDID, Local0)
                    Store (0x00, NDID)
                    If (LNotEqual (DIDL, Zero))
                    {
                        Store (SDDL (DID1), DID1)
                    }

                    If (LNotEqual (DDL2, Zero))
                    {
                        Store (SDDL (DID2), DID2)
                    }

                    If (LNotEqual (DDL3, Zero))
                    {
                        Store (SDDL (DID3), DID3)
                    }

                    If (LNotEqual (DDL4, Zero))
                    {
                        Store (SDDL (DID4), DID4)
                    }

                    If (LNotEqual (DDL5, Zero))
                    {
                        Store (SDDL (DID5), DID5)
                    }

                    If (LEqual (NDID, 0x00))
                    {
                        Store (Local0, NDID)
                    }

                    If (LEqual (NDID, 0x01))
                    {
                        Name (TMP1, Package (0x01)
                        {
                            0xFFFFFFFF
                        })
                        Store (Or (0x00010000, DID1), Index (TMP1, 0x00))
                        Return (TMP1)
                    }

                    If (LEqual (NDID, 0x02))
                    {
                        Name (TMP2, Package (0x02)
                        {
                            0xFFFFFFFF, 
                            0xFFFFFFFF
                        })
                        Store (Or (0x00010000, DID1), Index (TMP2, 0x00))
                        Store (Or (0x00010000, DID2), Index (TMP2, 0x01))
                        Return (TMP2)
                    }

                    If (LEqual (NDID, 0x03))
                    {
                        Name (TMP3, Package (0x03)
                        {
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF
                        })
                        Store (Or (0x00010000, DID1), Index (TMP3, 0x00))
                        Store (Or (0x00010000, DID2), Index (TMP3, 0x01))
                        Store (Or (0x00010000, DID3), Index (TMP3, 0x02))
                        Return (TMP3)
                    }

                    If (LEqual (NDID, 0x04))
                    {
                        Name (TMP4, Package (0x04)
                        {
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF
                        })
                        Store (Or (0x00010000, DID1), Index (TMP4, 0x00))
                        Store (Or (0x00010000, DID2), Index (TMP4, 0x01))
                        Store (Or (0x00010000, DID3), Index (TMP4, 0x02))
                        Store (Or (0x00010000, DID4), Index (TMP4, 0x03))
                        Return (TMP4)
                    }

                    If (LGreater (NDID, 0x04))
                    {
                        Name (TMP5, Package (0x05)
                        {
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF
                        })
                        Store (Or (0x00010000, DID1), Index (TMP5, 0x00))
                        Store (Or (0x00010000, DID2), Index (TMP5, 0x01))
                        Store (Or (0x00010000, DID3), Index (TMP5, 0x02))
                        Store (Or (0x00010000, DID4), Index (TMP5, 0x03))
                        Store (Or (0x00010000, DID4), Index (TMP5, 0x04))
                        Return (TMP5)
                    }

                    Return (Package (0x01)
                    {
                        0x0400
                    })
                }

                Device (DD01)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        If (LEqual (DID1, 0x00))
                        {
                            Return (0x01)
                        }
                        Else
                        {
                            Return (And (0xFFFF, DID1))
                        }
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        Return (CDDS (DID1))
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        Return (NDDS (DID1))
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }
                }

                Device (DD02)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        If (LEqual (DID2, 0x00))
                        {
                            Return (0x02)
                        }
                        Else
                        {
                            Return (And (0xFFFF, DID2))
                        }
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        Return (CDDS (DID2))
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        Return (NDDS (DID2))
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }
                }

                Device (DD03)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        If (LEqual (DID3, 0x00))
                        {
                            Return (0x03)
                        }
                        Else
                        {
                            Return (And (0xFFFF, DID3))
                        }
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        If (LEqual (DID3, 0x00))
                        {
                            Return (0x0B)
                        }
                        Else
                        {
                            Return (CDDS (DID3))
                        }
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        Return (NDDS (DID3))
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }
                }

                Device (DD04)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        If (LEqual (DID4, 0x00))
                        {
                            Return (0x04)
                        }
                        Else
                        {
                            Return (And (0xFFFF, DID4))
                        }
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        If (LEqual (DID4, 0x00))
                        {
                            Return (0x0B)
                        }
                        Else
                        {
                            Return (CDDS (DID4))
                        }
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        Return (NDDS (DID4))
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }
                }

                Device (DD05)
                {
                    Method (_ADR, 0, Serialized)
                    {
                        If (LEqual (DID5, 0x00))
                        {
                            Return (0x05)
                        }
                        Else
                        {
                            Return (And (0xFFFF, DID5))
                        }
                    }

                    Method (_DCS, 0, NotSerialized)
                    {
                        If (LEqual (DID5, 0x00))
                        {
                            Return (0x0B)
                        }
                        Else
                        {
                            Return (CDDS (DID5))
                        }
                    }

                    Method (_DGS, 0, NotSerialized)
                    {
                        Return (NDDS (DID5))
                    }

                    Method (_DSS, 1, NotSerialized)
                    {
                        If (LEqual (And (Arg0, 0xC0000000), 0xC0000000))
                        {
                            Store (NSTE, CSTE)
                        }
                    }
                }

                Method (SDDL, 1, NotSerialized)
                {
                    Increment (NDID)
                    Store (And (Arg0, 0x0F0F), Local0)
                    Or (0x80000000, Local0, Local1)
                    If (LEqual (DIDL, Local0))
                    {
                        Return (Local1)
                    }

                    If (LEqual (DDL2, Local0))
                    {
                        Return (Local1)
                    }

                    If (LEqual (DDL3, Local0))
                    {
                        Return (Local1)
                    }

                    If (LEqual (DDL4, Local0))
                    {
                        Return (Local1)
                    }

                    If (LEqual (DDL5, Local0))
                    {
                        Return (Local1)
                    }

                    If (LEqual (DDL6, Local0))
                    {
                        Return (Local1)
                    }

                    If (LEqual (DDL7, Local0))
                    {
                        Return (Local1)
                    }

                    If (LEqual (DDL8, Local0))
                    {
                        Return (Local1)
                    }

                    Return (0x00)
                }

                Method (CDDS, 1, NotSerialized)
                {
                    If (LEqual (CADL, And (Arg0, 0x0F0F)))
                    {
                        Return (0x1F)
                    }

                    If (LEqual (CAL2, And (Arg0, 0x0F0F)))
                    {
                        Return (0x1F)
                    }

                    If (LEqual (CAL3, And (Arg0, 0x0F0F)))
                    {
                        Return (0x1F)
                    }

                    If (LEqual (CAL4, And (Arg0, 0x0F0F)))
                    {
                        Return (0x1F)
                    }

                    If (LEqual (CAL5, And (Arg0, 0x0F0F)))
                    {
                        Return (0x1F)
                    }

                    If (LEqual (CAL6, And (Arg0, 0x0F0F)))
                    {
                        Return (0x1F)
                    }

                    If (LEqual (CAL7, And (Arg0, 0x0F0F)))
                    {
                        Return (0x1F)
                    }

                    If (LEqual (CAL8, And (Arg0, 0x0F0F)))
                    {
                        Return (0x1F)
                    }

                    If (LEqual (CADL, 0x00))
                    {
                        If (LEqual (And (Arg0, 0x0F0F), 0x0400))
                        {
                            Return (0x1F)
                        }
                    }

                    Return (0x1D)
                }

                Method (NDDS, 1, NotSerialized)
                {
                    If (LEqual (NADL, And (Arg0, 0x0F0F)))
                    {
                        Return (0x01)
                    }

                    If (LEqual (NDL2, And (Arg0, 0x0F0F)))
                    {
                        Return (0x01)
                    }

                    If (LEqual (NDL3, And (Arg0, 0x0F0F)))
                    {
                        Return (0x01)
                    }

                    If (LEqual (NDL4, And (Arg0, 0x0F0F)))
                    {
                        Return (0x01)
                    }

                    If (LEqual (NDL5, And (Arg0, 0x0F0F)))
                    {
                        Return (0x01)
                    }

                    If (LEqual (NDL6, And (Arg0, 0x0F0F)))
                    {
                        Return (0x01)
                    }

                    If (LEqual (NDL7, And (Arg0, 0x0F0F)))
                    {
                        Return (0x01)
                    }

                    If (LEqual (NDL8, And (Arg0, 0x0F0F)))
                    {
                        Return (0x01)
                    }

                    If (LEqual (NADL, 0x00))
                    {
                        If (LEqual (And (Arg0, 0x0F0F), 0x0400))
                        {
                            Return (0x01)
                        }
                    }

                    Return (0x00)
                }

                Scope (\_SB.PCI0)
                {
                    OperationRegion (MCHP, PCI_Config, 0x40, 0xC0)
                    Field (MCHP, AnyAcc, NoLock, Preserve)
                    {
                                Offset (0x60), 
                        TASM,   10, 
                                Offset (0x62)
                    }
                }

                OperationRegion (IGDP, PCI_Config, 0x40, 0xC0)
                Field (IGDP, AnyAcc, NoLock, Preserve)
                {
                            Offset (0x12), 
                        ,   1, 
                    GIVD,   1, 
                        ,   2, 
                    GUMA,   3, 
                            Offset (0x14), 
                        ,   4, 
                    GMFN,   1, 
                            Offset (0x18), 
                            Offset (0xA4), 
                    ASLE,   8, 
                            Offset (0xA8), 
                    GSSE,   1, 
                    GSSB,   14, 
                    GSES,   1, 
                            Offset (0xB0), 
                            Offset (0xB1), 
                    CDVL,   5, 
                            Offset (0xB2), 
                            Offset (0xB5), 
                    LBPC,   8, 
                            Offset (0xBC), 
                    ASLS,   32
                }

                OperationRegion (IGDM, SystemMemory, ASLB, 0x2000)
                Field (IGDM, AnyAcc, NoLock, Preserve)
                {
                    SIGN,   128, 
                    SIZE,   32, 
                    OVER,   32, 
                    SVER,   256, 
                    VVER,   128, 
                    GVER,   128, 
                    MBOX,   32, 
                            Offset (0x100), 
                    DRDY,   32, 
                    CSTS,   32, 
                    CEVT,   32, 
                            Offset (0x120), 
                    DIDL,   32, 
                    DDL2,   32, 
                    DDL3,   32, 
                    DDL4,   32, 
                    DDL5,   32, 
                    DDL6,   32, 
                    DDL7,   32, 
                    DDL8,   32, 
                    CPDL,   32, 
                    CPL2,   32, 
                    CPL3,   32, 
                    CPL4,   32, 
                    CPL5,   32, 
                    CPL6,   32, 
                    CPL7,   32, 
                    CPL8,   32, 
                    CADL,   32, 
                    CAL2,   32, 
                    CAL3,   32, 
                    CAL4,   32, 
                    CAL5,   32, 
                    CAL6,   32, 
                    CAL7,   32, 
                    CAL8,   32, 
                    NADL,   32, 
                    NDL2,   32, 
                    NDL3,   32, 
                    NDL4,   32, 
                    NDL5,   32, 
                    NDL6,   32, 
                    NDL7,   32, 
                    NDL8,   32, 
                    ASLP,   32, 
                    TIDX,   32, 
                    CHPD,   32, 
                    CLID,   32, 
                    CDCK,   32, 
                    SXSW,   32, 
                    EVTS,   32, 
                    CNOT,   32, 
                    NRDY,   32, 
                            Offset (0x200), 
                    SCIE,   1, 
                    GEFC,   4, 
                    GXFC,   3, 
                    GESF,   8, 
                            Offset (0x204), 
                    PARM,   32, 
                    DSLP,   32, 
                            Offset (0x300), 
                    ARDY,   32, 
                    ASLC,   32, 
                    TCHE,   32, 
                    ALSI,   32, 
                    BCLP,   32, 
                    PFIT,   32, 
                    CBLV,   32, 
                    BCLM,   320, 
                    CPFM,   32, 
                    EPFM,   32, 
                            Offset (0x400), 
                    GVD1,   57344
                }

                Name (DBTB, Package (0x15)
                {
                    0x00, 
                    0x07, 
                    0x38, 
                    0x01C0, 
                    0x0E00, 
                    0x3F, 
                    0x01C7, 
                    0x0E07, 
                    0x01F8, 
                    0x0E38, 
                    0x0FC0, 
                    0x00, 
                    0x00, 
                    0x00, 
                    0x00, 
                    0x00, 
                    0x7000, 
                    0x7007, 
                    0x7038, 
                    0x71C0, 
                    0x7E00
                })
                Name (CDCT, Package (0x03)
                {
                    Package (0x03)
                    {
                        0xC8, 
                        0x0140, 
                        0x0190
                    }, 

                    Package (0x03)
                    {
                        0xC8, 
                        0x014D, 
                        0x0190
                    }, 

                    Package (0x03)
                    {
                        0xDE, 
                        0x014D, 
                        0x017D
                    }
                })
                Name (SUCC, 0x01)
                Name (NVLD, 0x02)
                Name (CRIT, 0x04)
                Name (NCRT, 0x06)
                Method (GSCI, 0, Serialized)
                {
                    Method (GBDA, 0, Serialized)
                    {
                        If (LEqual (GESF, 0x00))
                        {
                            Store (0x0279, PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x01))
                        {
                            Store (0x0240, PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x04))
                        {
                            And (PARM, 0xEFFF0000, PARM)
                            And (PARM, ShiftLeft (DerefOf (Index (DBTB, IBTT)), 0x10), 
                                PARM)
                            Or (IBTT, PARM, PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x05))
                        {
                            Store (IPSC, PARM)
                            Or (PARM, ShiftLeft (IPAT, 0x08), PARM)
                            Add (PARM, 0x0100, PARM)
                            Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
                            Add (PARM, 0x00010000, PARM)
                            Or (PARM, ShiftLeft (IBIA, 0x14), PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x06))
                        {
                            Store (ITVF, PARM)
                            Or (PARM, ShiftLeft (ITVM, 0x04), PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x07))
                        {
                            Store (GIVD, PARM)
                            XOr (PARM, 0x01, PARM)
                            Or (PARM, ShiftLeft (GMFN, 0x01), PARM)
                            Or (PARM, ShiftLeft (0x02, 0x0B), PARM)
                            If (IDMM)
                            {
                                Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
                            }
                            Else
                            {
                                Or (PARM, ShiftLeft (IDMS, 0x0D), PARM)
                            }

                            Or (ShiftLeft (DerefOf (Index (DerefOf (Index (CDCT, HVCO)), Subtract (
                                CDVL, 0x01))), 0x15), PARM, PARM)
                            Store (0x01, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x0A))
                        {
                            Store (0x00, PARM)
                            If (ISSC)
                            {
                                Or (PARM, 0x03, PARM)
                            }

                            Store (0x00, GESF)
                            Return (SUCC)
                        }

                        Store (Zero, GESF)
                        Return (CRIT)
                    }

                    Method (SBCB, 0, Serialized)
                    {
                        If (LEqual (GESF, 0x00))
                        {
                            Store (0x40, PARM)
                            Store (0xF7FD, PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x01))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x03))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x04))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x05))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x06))
                        {
                            Store (And (PARM, 0x0F), ITVF)
                            Store (ShiftRight (And (PARM, 0xF0), 0x04), ITVM)
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x07))
                        {
                            If (LEqual (PARM, 0x00))
                            {
                                Store (CLID, Local0)
                                If (And (0x80000000, Local0))
                                {
                                    And (CLID, 0x0F, CLID)
                                    GLID (CLID)
                                }
                            }

                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x08))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x09))
                        {
                            And (PARM, 0xFF, IBTT)
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x0A))
                        {
                            And (PARM, 0xFF, IPSC)
                            If (And (ShiftRight (PARM, 0x08), 0xFF))
                            {
                                And (ShiftRight (PARM, 0x08), 0xFF, IPAT)
                                Decrement (IPAT)
                            }

                            And (ShiftRight (PARM, 0x14), 0x07, IBIA)
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x0B))
                        {
                            And (ShiftRight (PARM, 0x01), 0x01, IF1E)
                            If (And (PARM, ShiftLeft (0x0F, 0x0D)))
                            {
                                And (ShiftRight (PARM, 0x0D), 0x0F, IDMS)
                                Store (0x00, IDMM)
                            }
                            Else
                            {
                                And (ShiftRight (PARM, 0x11), 0x0F, IDMS)
                                Store (0x01, IDMM)
                            }

                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x10))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x11))
                        {
                            Store (ShiftLeft (LIDS, 0x08), PARM)
                            Add (PARM, 0x0100, PARM)
                            Store (Zero, GESF)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x12))
                        {
                            If (And (PARM, 0x01))
                            {
                                If (LEqual (ShiftRight (PARM, 0x01), 0x01))
                                {
                                    Store (0x01, ISSC)
                                }
                                Else
                                {
                                    Store (Zero, GESF)
                                    Return (CRIT)
                                }
                            }
                            Else
                            {
                                Store (0x00, ISSC)
                            }

                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        If (LEqual (GESF, 0x13))
                        {
                            Store (Zero, GESF)
                            Store (Zero, PARM)
                            Return (SUCC)
                        }

                        Store (Zero, GESF)
                        Return (SUCC)
                    }

                    If (LEqual (GEFC, 0x04))
                    {
                        Store (GBDA (), GXFC)
                    }

                    If (LEqual (GEFC, 0x06))
                    {
                        Store (SBCB (), GXFC)
                    }

                    Store (0x00, GEFC)
                    Store (0x01, SCIS)
                    Store (0x00, GSSE)
                    Store (0x00, SCIE)
                    Return (Zero)
                }

                Method (PDRD, 0, NotSerialized)
                {
                    If (LNot (DRDY))
                    {
                        Sleep (ASLP)
                    }

                    Return (LNot (DRDY))
                }

                Method (PSTS, 0, NotSerialized)
                {
                    If (LGreater (CSTS, 0x02))
                    {
                        Sleep (ASLP)
                    }

                    Return (LEqual (CSTS, 0x03))
                }

                Method (GNOT, 2, NotSerialized)
                {
                    If (PDRD ())
                    {
                        Return (0x01)
                    }

                    Store (Arg0, CEVT)
                    Store (0x03, CSTS)
                    If (LAnd (LEqual (CHPD, 0x00), LEqual (Arg1, 0x00)))
                    {
                        If (LOr (LGreater (OSYS, 0x07D0), LLess (OSYS, 0x07D6)))
                        {
                            Notify (\_SB.PCI0, Arg1)
                        }
                        Else
                        {
                            Notify (\_SB.PCI0.GFX0, Arg1)
                        }
                    }

                    Notify (\_SB.PCI0.GFX0, 0x80)
                    Return (0x00)
                }

                Method (GHDS, 1, NotSerialized)
                {
                    Store (Arg0, TIDX)
                    Return (GNOT (0x01, 0x00))
                }

                Method (GLID, 1, NotSerialized)
                {
                    Store (Arg0, CLID)
                    Return (GNOT (0x02, 0x00))
                }

                Method (GDCK, 1, NotSerialized)
                {
                    Store (Arg0, CDCK)
                    Return (GNOT (0x04, 0x00))
                }

                Method (PARD, 0, NotSerialized)
                {
                    If (LNot (ARDY))
                    {
                        Sleep (ASLP)
                    }

                    Return (LNot (ARDY))
                }

                Method (AINT, 2, NotSerialized)
                {
                    If (LNot (And (TCHE, ShiftLeft (0x01, Arg0))))
                    {
                        Return (0x01)
                    }

                    If (PARD ())
                    {
                        Return (0x01)
                    }

                    If (LEqual (Arg0, 0x02))
                    {
                        If (CPFM)
                        {
                            And (CPFM, 0x0F, Local0)
                            And (EPFM, 0x0F, Local1)
                            If (LEqual (Local0, 0x01))
                            {
                                If (And (Local1, 0x06))
                                {
                                    Store (0x06, PFIT)
                                }
                                Else
                                {
                                    If (And (Local1, 0x08))
                                    {
                                        Store (0x08, PFIT)
                                    }
                                    Else
                                    {
                                        Store (0x01, PFIT)
                                    }
                                }
                            }

                            If (LEqual (Local0, 0x06))
                            {
                                If (And (Local1, 0x08))
                                {
                                    Store (0x08, PFIT)
                                }
                                Else
                                {
                                    If (And (Local1, 0x01))
                                    {
                                        Store (0x01, PFIT)
                                    }
                                    Else
                                    {
                                        Store (0x06, PFIT)
                                    }
                                }
                            }

                            If (LEqual (Local0, 0x08))
                            {
                                If (And (Local1, 0x01))
                                {
                                    Store (0x01, PFIT)
                                }
                                Else
                                {
                                    If (And (Local1, 0x06))
                                    {
                                        Store (0x06, PFIT)
                                    }
                                    Else
                                    {
                                        Store (0x08, PFIT)
                                    }
                                }
                            }
                        }
                        Else
                        {
                            XOr (PFIT, 0x07, PFIT)
                        }

                        Or (PFIT, 0x80000000, PFIT)
                        Store (0x04, ASLC)
                    }
                    Else
                    {
                        If (LEqual (Arg0, 0x01))
                        {
                            Store (Divide (Multiply (Arg1, 0xFF), 0x64, ), BCLP)
                            Or (BCLP, 0x80000000, BCLP)
                            Store (0x02, ASLC)
                        }
                        Else
                        {
                            If (LEqual (Arg0, 0x00))
                            {
                                Store (Arg1, ALSI)
                                Store (0x01, ASLC)
                            }
                            Else
                            {
                                Return (0x01)
                            }
                        }
                    }

                    Store (0x00, LBPC)
                    Return (0x00)
                }

                Name (NDLC, 0x00)
                Method (SNDL, 1, NotSerialized)
                {
                    Store (0x00, NDLC)
                    Store (0x00, NADL)
                    Store (0x00, NDL2)
                    Store (0x00, NDL3)
                    Store (0x00, NDL4)
                    Store (0x00, NDL5)
                    If (And (Arg0, 0x08))
                    {
                        S2ND (0x0400)
                    }

                    If (And (Arg0, 0x01))
                    {
                        S2ND (0x0100)
                    }

                    If (And (Arg0, 0x02))
                    {
                        S2ND (0x0200)
                    }

                    If (And (Arg0, 0x04))
                    {
                        S2ND (0x0300)
                    }
                }

                Method (S2ND, 1, NotSerialized)
                {
                    Increment (NDLC)
                    If (LEqual (NDLC, 0x01))
                    {
                        Store (Arg0, NADL)
                    }

                    If (LEqual (NDLC, 0x02))
                    {
                        Store (Arg0, NDL2)
                    }

                    If (LEqual (NDLC, 0x03))
                    {
                        Store (Arg0, NDL3)
                    }

                    If (LEqual (NDLC, 0x04))
                    {
                        Store (Arg0, NDL4)
                    }

                    If (LEqual (NDLC, 0x05))
                    {
                        Store (Arg0, NDL5)
                    }
                }
            }

            Scope (\)
            {
            }

            Scope (\)
            {
                OperationRegion (IO_T, SystemIO, 0x0800, 0x10)
                Field (IO_T, ByteAcc, NoLock, Preserve)
                {
                            Offset (0x08), 
                    TRP0,   8
                }

                OperationRegion (PMIO, SystemIO, 0x1000, 0x80)
                Field (PMIO, ByteAcc, NoLock, Preserve)
                {
                            Offset (0x42), 
                        ,   1, 
                    GPEC,   1, 
                            Offset (0x64), 
                        ,   9, 
                    SCIS,   1, 
                            Offset (0x66)
                }

                OperationRegion (GPIO, SystemIO, 0x1180, 0x3C)
                Field (GPIO, ByteAcc, NoLock, Preserve)
                {
                    GU00,   8, 
                    GU01,   8, 
                    GU02,   8, 
                    GU03,   8, 
                    GIO0,   8, 
                    GIO1,   8, 
                    GIO2,   8, 
                    GIO3,   8, 
                            Offset (0x0C), 
                    GL00,   8, 
                    GL01,   8, 
                    GL02,   8, 
                        ,   3, 
                    GP27,   1, 
                    GP28,   1, 
                            Offset (0x10), 
                            Offset (0x18), 
                    GB00,   8, 
                    GB01,   8, 
                    GB02,   8, 
                    GB03,   8, 
                            Offset (0x2C), 
                    GIV0,   8, 
                    GIV1,   8, 
                    GIV2,   8, 
                    GIV3,   8, 
                    GU04,   8, 
                    GU05,   8, 
                    GU06,   8, 
                    GU07,   8, 
                    GIO4,   8, 
                    GIO5,   8, 
                    GIO6,   8, 
                    GIO7,   8, 
                        ,   5, 
                    GP37,   1, 
                            Offset (0x39), 
                    GL05,   8, 
                    GL06,   8, 
                    GL07,   8
                }

                OperationRegion (RCRB, SystemMemory, 0xFED1C000, 0x4000)
                Field (RCRB, DWordAcc, Lock, Preserve)
                {
                            Offset (0x1000), 
                            Offset (0x3000), 
                            Offset (0x3404), 
                    HPAS,   2, 
                        ,   5, 
                    HPAE,   1, 
                            Offset (0x3418), 
                        ,   1, 
                    PATD,   1, 
                    SATD,   1, 
                    SMBD,   1, 
                    HDAD,   1, 
                            Offset (0x341A), 
                    RP1D,   1, 
                    RP2D,   1, 
                    RP3D,   1, 
                    RP4D,   1, 
                    RP5D,   1, 
                    RP6D,   1
                }

                Name (_S0, Package (0x03)
                {
                    0x00, 
                    0x00, 
                    0x00
                })
                Name (_S3, Package (0x03)
                {
                    0x05, 
                    0x05, 
                    0x00
                })
                Name (_S4, Package (0x03)
                {
                    0x06, 
                    0x06, 
                    0x00
                })
                Name (_S5, Package (0x03)
                {
                    0x07, 
                    0x07, 
                    0x00
                })
                Method (GETP, 1, Serialized)
                {
                    If (LEqual (And (Arg0, 0x09), 0x00))
                    {
                        Return (0xFFFFFFFF)
                    }

                    If (LEqual (And (Arg0, 0x09), 0x08))
                    {
                        Return (0x0384)
                    }

                    ShiftRight (And (Arg0, 0x0300), 0x08, Local0)
                    ShiftRight (And (Arg0, 0x3000), 0x0C, Local1)
                    Return (Multiply (0x1E, Subtract (0x09, Add (Local0, Local1))
                        ))
                }

                Method (GDMA, 5, Serialized)
                {
                    If (Arg0)
                    {
                        If (LAnd (Arg1, Arg4))
                        {
                            Return (0x14)
                        }

                        If (LAnd (Arg2, Arg4))
                        {
                            Return (Multiply (Subtract (0x04, Arg3), 0x0F))
                        }

                        Return (Multiply (Subtract (0x04, Arg3), 0x1E))
                    }

                    Return (0xFFFFFFFF)
                }

                Method (GETT, 1, Serialized)
                {
                    Return (Multiply (0x1E, Subtract (0x09, Add (And (ShiftRight (Arg0, 0x02
                        ), 0x03), And (Arg0, 0x03)))))
                }

                Method (GETF, 3, Serialized)
                {
                    Name (TMPF, 0x00)
                    If (Arg0)
                    {
                        Or (TMPF, 0x01, TMPF)
                    }

                    If (And (Arg2, 0x02))
                    {
                        Or (TMPF, 0x02, TMPF)
                    }

                    If (Arg1)
                    {
                        Or (TMPF, 0x04, TMPF)
                    }

                    If (And (Arg2, 0x20))
                    {
                        Or (TMPF, 0x08, TMPF)
                    }

                    If (And (Arg2, 0x4000))
                    {
                        Or (TMPF, 0x10, TMPF)
                    }

                    Return (TMPF)
                }

                Method (SETP, 3, Serialized)
                {
                    If (LGreater (Arg0, 0xF0))
                    {
                        Return (0x08)
                    }
                    Else
                    {
                        If (And (Arg1, 0x02))
                        {
                            If (LAnd (LLessEqual (Arg0, 0x78), And (Arg2, 0x02)))
                            {
                                Return (0x2301)
                            }

                            If (LAnd (LLessEqual (Arg0, 0xB4), And (Arg2, 0x01)))
                            {
                                Return (0x2101)
                            }
                        }

                        Return (0x1001)
                    }
                }

                Method (SDMA, 1, Serialized)
                {
                    If (LLessEqual (Arg0, 0x14))
                    {
                        Return (0x01)
                    }

                    If (LLessEqual (Arg0, 0x1E))
                    {
                        Return (0x02)
                    }

                    If (LLessEqual (Arg0, 0x2D))
                    {
                        Return (0x01)
                    }

                    If (LLessEqual (Arg0, 0x3C))
                    {
                        Return (0x02)
                    }

                    If (LLessEqual (Arg0, 0x5A))
                    {
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Method (SETT, 3, Serialized)
                {
                    If (And (Arg1, 0x02))
                    {
                        If (LAnd (LLessEqual (Arg0, 0x78), And (Arg2, 0x02)))
                        {
                            Return (0x0B)
                        }

                        If (LAnd (LLessEqual (Arg0, 0xB4), And (Arg2, 0x01)))
                        {
                            Return (0x09)
                        }
                    }

                    Return (0x04)
                }
            }

            Device (LANC)
            {
                Name (_ADR, 0x00190000)
                OperationRegion (LANF, PCI_Config, 0xCC, 0x04)
                Field (LANF, DWordAcc, NoLock, Preserve)
                {
                        ,   15, 
                    PMES,   1
                }

                Name (_PRW, Package (0x02)
                {
                    0x0D, 
                    0x04
                })
            }

            Device (HDEF)
            {
                Name (_ADR, 0x001B0000)
                OperationRegion (HDAR, PCI_Config, 0x4C, 0x10)
                Field (HDAR, WordAcc, NoLock, Preserve)
                {
                    DCKA,   1, 
                            Offset (0x01), 
                    DCKM,   1, 
                        ,   6, 
                    DCKS,   1, 
                            Offset (0x08), 
                        ,   15, 
                    PMES,   1
                }

                Name (_PRW, Package (0x02)
                {
                    0x0D, 
                    0x04
                })
            }

            Device (RP01)
            {
                Name (_ADR, 0x001C0000)
                OperationRegion (PXCS, PCI_Config, 0x40, 0xC0)
                Field (PXCS, AnyAcc, NoLock, WriteAsZeros)
                {
                            Offset (0x12), 
                        ,   13, 
                    LASX,   1, 
                            Offset (0x1A), 
                    ABPX,   1, 
                        ,   2, 
                    PDCX,   1, 
                        ,   2, 
                    PDSX,   1, 
                            Offset (0x1B), 
                    LSCX,   1, 
                            Offset (0x20), 
                            Offset (0x22), 
                    PSPX,   1, 
                            Offset (0x98), 
                        ,   30, 
                    HPEX,   1, 
                    PMEX,   1, 
                        ,   30, 
                    HPSX,   1, 
                    PMSX,   1
                }

                Device (PXSX)
                {
                    Name (_ADR, 0x00)
                    Name (_PRW, Package (0x02)
                    {
                        0x09, 
                        0x04
                    })
                }

                Method (PXSX._RMV, 0, NotSerialized)
                {
                    Return (XOr (PHSR (0x2D, 0x00), 0x01))
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (\GPIC)
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                0x00, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                0x00, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                0x00, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                0x00, 
                                0x13
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKA, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                \_SB.PCI0.LPCB.LNKB, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                \_SB.PCI0.LPCB.LNKC, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                \_SB.PCI0.LPCB.LNKD, 
                                0x00
                            }
                        })
                    }
                }
            }

            Device (RP02)
            {
                Name (_ADR, 0x001C0001)
                OperationRegion (PXCS, PCI_Config, 0x40, 0xC0)
                Field (PXCS, AnyAcc, NoLock, WriteAsZeros)
                {
                            Offset (0x12), 
                        ,   13, 
                    LASX,   1, 
                            Offset (0x1A), 
                    ABPX,   1, 
                        ,   2, 
                    PDCX,   1, 
                        ,   2, 
                    PDSX,   1, 
                            Offset (0x1B), 
                    LSCX,   1, 
                            Offset (0x20), 
                            Offset (0x22), 
                    PSPX,   1, 
                            Offset (0x98), 
                        ,   30, 
                    HPEX,   1, 
                    PMEX,   1, 
                        ,   30, 
                    HPSX,   1, 
                    PMSX,   1
                }

                Device (PXSX)
                {
                    Name (_ADR, 0x00)
                    Name (_PRW, Package (0x02)
                    {
                        0x09, 
                        0x04
                    })
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (\GPIC)
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                0x00, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                0x00, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                0x00, 
                                0x13
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                0x00, 
                                0x10
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKB, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                \_SB.PCI0.LPCB.LNKC, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                \_SB.PCI0.LPCB.LNKD, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                \_SB.PCI0.LPCB.LNKA, 
                                0x00
                            }
                        })
                    }
                }
            }

            Device (RP03)
            {
                Name (_ADR, 0x001C0002)
                OperationRegion (PXCS, PCI_Config, 0x40, 0xC0)
                Field (PXCS, AnyAcc, NoLock, WriteAsZeros)
                {
                            Offset (0x12), 
                        ,   13, 
                    LASX,   1, 
                            Offset (0x1A), 
                    ABPX,   1, 
                        ,   2, 
                    PDCX,   1, 
                        ,   2, 
                    PDSX,   1, 
                            Offset (0x1B), 
                    LSCX,   1, 
                            Offset (0x20), 
                            Offset (0x22), 
                    PSPX,   1, 
                            Offset (0x98), 
                        ,   30, 
                    HPEX,   1, 
                    PMEX,   1, 
                        ,   30, 
                    HPSX,   1, 
                    PMSX,   1
                }

                Device (PXSX)
                {
                    Name (_ADR, 0x00)
                    Name (_PRW, Package (0x02)
                    {
                        0x09, 
                        0x04
                    })
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (\GPIC)
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                0x00, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                0x00, 
                                0x13
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                0x00, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                0x00, 
                                0x11
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKC, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                \_SB.PCI0.LPCB.LNKD, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                \_SB.PCI0.LPCB.LNKA, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                \_SB.PCI0.LPCB.LNKB, 
                                0x00
                            }
                        })
                    }
                }
            }

            Device (RP04)
            {
                Name (_ADR, 0x001C0003)
                OperationRegion (PXCS, PCI_Config, 0x40, 0xC0)
                Field (PXCS, AnyAcc, NoLock, WriteAsZeros)
                {
                            Offset (0x12), 
                        ,   13, 
                    LASX,   1, 
                            Offset (0x1A), 
                    ABPX,   1, 
                        ,   2, 
                    PDCX,   1, 
                        ,   2, 
                    PDSX,   1, 
                            Offset (0x1B), 
                    LSCX,   1, 
                            Offset (0x20), 
                            Offset (0x22), 
                    PSPX,   1, 
                            Offset (0x98), 
                        ,   30, 
                    HPEX,   1, 
                    PMEX,   1, 
                        ,   30, 
                    HPSX,   1, 
                    PMSX,   1
                }

                Device (PXSX)
                {
                    Name (_ADR, 0x00)
                    Name (_PRW, Package (0x02)
                    {
                        0x09, 
                        0x04
                    })
                }

                Method (_PRT, 0, NotSerialized)
                {
                    If (\GPIC)
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                0x00, 
                                0x13
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                0x00, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                0x00, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                0x00, 
                                0x12
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKD, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                \_SB.PCI0.LPCB.LNKA, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                \_SB.PCI0.LPCB.LNKB, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                \_SB.PCI0.LPCB.LNKC, 
                                0x00
                            }
                        })
                    }
                }
            }

            Device (RP05)
            {
                Name (_ADR, 0x001C0004)
                OperationRegion (PXCS, PCI_Config, 0x40, 0xC0)
                Field (PXCS, AnyAcc, NoLock, WriteAsZeros)
                {
                            Offset (0x12), 
                        ,   13, 
                    LASX,   1, 
                            Offset (0x1A), 
                    ABPX,   1, 
                        ,   2, 
                    PDCX,   1, 
                        ,   2, 
                    PDSX,   1, 
                            Offset (0x1B), 
                    LSCX,   1, 
                            Offset (0x20), 
                            Offset (0x22), 
                    PSPX,   1, 
                            Offset (0x98), 
                        ,   30, 
                    HPEX,   1, 
                    PMEX,   1, 
                        ,   30, 
                    HPSX,   1, 
                    PMSX,   1
                }

                Device (PXSX)
                {
                    Name (_ADR, 0x00)
                    Name (_PRW, Package (0x02)
                    {
                        0x09, 
                        0x04
                    })
                }

                Name (PXSX._RMV, 0x01)
                Method (_PRT, 0, NotSerialized)
                {
                    If (\GPIC)
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                0x00, 
                                0x10
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                0x00, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                0x00, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                0x00, 
                                0x13
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKA, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                \_SB.PCI0.LPCB.LNKB, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                \_SB.PCI0.LPCB.LNKC, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                \_SB.PCI0.LPCB.LNKD, 
                                0x00
                            }
                        })
                    }
                }
            }

            Device (RP06)
            {
                Name (_ADR, 0x001C0005)
                OperationRegion (PXCS, PCI_Config, 0x40, 0xC0)
                Field (PXCS, AnyAcc, NoLock, WriteAsZeros)
                {
                            Offset (0x12), 
                        ,   13, 
                    LASX,   1, 
                            Offset (0x1A), 
                    ABPX,   1, 
                        ,   2, 
                    PDCX,   1, 
                        ,   2, 
                    PDSX,   1, 
                            Offset (0x1B), 
                    LSCX,   1, 
                            Offset (0x20), 
                            Offset (0x22), 
                    PSPX,   1, 
                            Offset (0x98), 
                        ,   30, 
                    HPEX,   1, 
                    PMEX,   1, 
                        ,   30, 
                    HPSX,   1, 
                    PMSX,   1
                }

                Device (PXSX)
                {
                    Name (_ADR, 0x00)
                    Name (_PRW, Package (0x02)
                    {
                        0x09, 
                        0x04
                    })
                }

                Name (PXSX._RMV, 0x01)
                Method (_PRT, 0, NotSerialized)
                {
                    If (\GPIC)
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                0x00, 
                                0x11
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                0x00, 
                                0x12
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                0x00, 
                                0x13
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                0x00, 
                                0x10
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x04)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKB, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                \_SB.PCI0.LPCB.LNKC, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                \_SB.PCI0.LPCB.LNKD, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                \_SB.PCI0.LPCB.LNKA, 
                                0x00
                            }
                        })
                    }
                }
            }

            Method (NHPG, 0, Serialized)
            {
                Store (0x00, ^RP01.HPEX)
                Store (0x00, ^RP02.HPEX)
                Store (0x00, ^RP03.HPEX)
                Store (0x00, ^RP04.HPEX)
                Store (0x01, ^RP01.HPSX)
                Store (0x01, ^RP02.HPSX)
                Store (0x01, ^RP03.HPSX)
                Store (0x01, ^RP04.HPSX)
            }

            Method (NPME, 0, Serialized)
            {
                Store (0x00, ^RP01.PMEX)
                Store (0x00, ^RP02.PMEX)
                Store (0x00, ^RP03.PMEX)
                Store (0x00, ^RP04.PMEX)
                Store (0x00, ^RP05.PMEX)
                Store (0x00, ^RP06.PMEX)
                Store (0x01, ^RP01.PMSX)
                Store (0x01, ^RP02.PMSX)
                Store (0x01, ^RP03.PMSX)
                Store (0x01, ^RP04.PMSX)
                Store (0x01, ^RP05.PMSX)
                Store (0x01, ^RP06.PMSX)
            }

            Device (USB1)
            {
                Name (_ADR, 0x001D0000)
                OperationRegion (U1CS, PCI_Config, 0xC4, 0x04)
                Field (U1CS, DWordAcc, NoLock, Preserve)
                {
                    U1EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x03, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U1EN)
                    }
                    Else
                    {
                        Store (0x00, U1EN)
                    }
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB2)
            {
                Name (_ADR, 0x001D0001)
                OperationRegion (U2CS, PCI_Config, 0xC4, 0x04)
                Field (U2CS, DWordAcc, NoLock, Preserve)
                {
                    U2EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x04, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U2EN)
                    }
                    Else
                    {
                        Store (0x00, U2EN)
                    }
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB3)
            {
                Name (_ADR, 0x001D0002)
                OperationRegion (U2CS, PCI_Config, 0xC4, 0x04)
                Field (U2CS, DWordAcc, NoLock, Preserve)
                {
                    U3EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x0C, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U3EN)
                    }
                    Else
                    {
                        Store (0x00, U3EN)
                    }
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB4)
            {
                Name (_ADR, 0x001A0000)
                OperationRegion (U4CS, PCI_Config, 0xC4, 0x04)
                Field (U4CS, DWordAcc, NoLock, Preserve)
                {
                    U4EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x0E, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U4EN)
                    }
                    Else
                    {
                        Store (0x00, U4EN)
                    }
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (USB5)
            {
                Name (_ADR, 0x001A0001)
                OperationRegion (U5CS, PCI_Config, 0xC4, 0x04)
                Field (U5CS, DWordAcc, NoLock, Preserve)
                {
                    U5EN,   2
                }

                Name (_PRW, Package (0x02)
                {
                    0x05, 
                    0x03
                })
                Method (_PSW, 1, NotSerialized)
                {
                    If (Arg0)
                    {
                        Store (0x03, U5EN)
                    }
                    Else
                    {
                        Store (0x00, U5EN)
                    }
                }

                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (EHC1)
            {
                Name (_ADR, 0x001D0007)
                OperationRegion (U7CS, PCI_Config, 0x54, 0x04)
                Field (U7CS, DWordAcc, NoLock, Preserve)
                {
                        ,   15, 
                    PMES,   1
                }

                Device (HUB7)
                {
                    Name (_ADR, 0x00)
                    Device (PRT1)
                    {
                        Name (_ADR, 0x01)
                    }

                    Device (PRT2)
                    {
                        Name (_ADR, 0x02)
                    }

                    Device (PRT3)
                    {
                        Name (_ADR, 0x03)
                    }

                    Device (PRT4)
                    {
                        Name (_ADR, 0x04)
                    }

                    Device (PRT5)
                    {
                        Name (_ADR, 0x05)
                    }

                    Device (PRT6)
                    {
                        Name (_ADR, 0x06)
                    }
                }

                Name (_PRW, Package (0x02)
                {
                    0x0D, 
                    0x03
                })
                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (EHC2)
            {
                Name (_ADR, 0x001A0007)
                OperationRegion (UFCS, PCI_Config, 0x54, 0x04)
                Field (UFCS, DWordAcc, NoLock, Preserve)
                {
                        ,   15, 
                    PMES,   1
                }

                Device (HUB7)
                {
                    Name (_ADR, 0x00)
                    Device (PRT1)
                    {
                        Name (_ADR, 0x01)
                    }

                    Device (PRT2)
                    {
                        Name (_ADR, 0x02)
                    }

                    Device (PRT3)
                    {
                        Name (_ADR, 0x03)
                    }

                    Device (PRT4)
                    {
                        Name (_ADR, 0x04)
                    }
                }

                Name (_PRW, Package (0x02)
                {
                    0x0D, 
                    0x03
                })
                Method (_S3D, 0, NotSerialized)
                {
                    Return (0x02)
                }

                Method (_S4D, 0, NotSerialized)
                {
                    Return (0x02)
                }
            }

            Device (PCIB)
            {
                Name (_ADR, 0x001E0000)
                Method (_PRT, 0, NotSerialized)
                {
                    If (GPIC)
                    {
                        Return (Package (0x02)
                        {
                            Package (0x04)
                            {
                                0x0004FFFF, 
                                0x00, 
                                0x00, 
                                0x16
                            }, 

                            Package (0x04)
                            {
                                0x0004FFFF, 
                                0x01, 
                                0x00, 
                                0x15
                            }
                        })
                    }
                    Else
                    {
                        Return (Package (0x06)
                        {
                            Package (0x04)
                            {
                                0xFFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKF, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x01, 
                                \_SB.PCI0.LPCB.LNKG, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x02, 
                                \_SB.PCI0.LPCB.LNKH, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0xFFFF, 
                                0x03, 
                                \_SB.PCI0.LPCB.LNKE, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0x0004FFFF, 
                                0x00, 
                                \_SB.PCI0.LPCB.LNKG, 
                                0x00
                            }, 

                            Package (0x04)
                            {
                                0x0004FFFF, 
                                0x01, 
                                \_SB.PCI0.LPCB.LNKF, 
                                0x00
                            }
                        })
                    }
                }

                Device (CBS0)
                {
                    Name (_ADR, 0x00040000)
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }

                    Method (_S3D, 0, NotSerialized)
                    {
                        Return (0x03)
                    }

                    Method (_S4D, 0, NotSerialized)
                    {
                        Return (0x03)
                    }
                }
            }

            Device (LPCB)
            {
                Name (_ADR, 0x001F0000)
                OperationRegion (LPC0, PCI_Config, 0x40, 0xC0)
                Field (LPC0, AnyAcc, NoLock, Preserve)
                {
                            Offset (0x20), 
                    PARC,   8, 
                    PBRC,   8, 
                    PCRC,   8, 
                    PDRC,   8, 
                            Offset (0x28), 
                    PERC,   8, 
                    PFRC,   8, 
                    PGRC,   8, 
                    PHRC,   8, 
                            Offset (0x40), 
                    IOD0,   8, 
                    IOD1,   8, 
                            Offset (0xB0), 
                    RAEN,   1, 
                        ,   13, 
                    RCBA,   18
                }

                Device (LNKA)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x01)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PARC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,10,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLA, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y14)
                                {}
                        })
                        CreateWordField (RTLA, \_SB.PCI0.LPCB.LNKA._CRS._Y14._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PARC, 0x0F), IRQ0)
                        Return (RTLA)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PARC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PARC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKB)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x02)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PBRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,11,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLB, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y15)
                                {}
                        })
                        CreateWordField (RTLB, \_SB.PCI0.LPCB.LNKB._CRS._Y15._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PBRC, 0x0F), IRQ0)
                        Return (RTLB)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PBRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PBRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKC)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x03)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PCRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,10,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLC, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y16)
                                {}
                        })
                        CreateWordField (RTLC, \_SB.PCI0.LPCB.LNKC._CRS._Y16._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PCRC, 0x0F), IRQ0)
                        Return (RTLC)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PCRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PCRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKD)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x04)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PDRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,11,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLD, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y17)
                                {}
                        })
                        CreateWordField (RTLD, \_SB.PCI0.LPCB.LNKD._CRS._Y17._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PDRC, 0x0F), IRQ0)
                        Return (RTLD)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PDRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PDRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKE)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x05)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PERC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,10,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLE, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y18)
                                {}
                        })
                        CreateWordField (RTLE, \_SB.PCI0.LPCB.LNKE._CRS._Y18._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PERC, 0x0F), IRQ0)
                        Return (RTLE)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PERC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PERC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKF)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x06)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PFRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,11,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLF, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y19)
                                {}
                        })
                        CreateWordField (RTLF, \_SB.PCI0.LPCB.LNKF._CRS._Y19._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PFRC, 0x0F), IRQ0)
                        Return (RTLF)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PFRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PFRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKG)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x07)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PGRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,10,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLG, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y1A)
                                {}
                        })
                        CreateWordField (RTLG, \_SB.PCI0.LPCB.LNKG._CRS._Y1A._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PGRC, 0x0F), IRQ0)
                        Return (RTLG)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PGRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PGRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (LNKH)
                {
                    Name (_HID, EisaId ("PNP0C0F"))
                    Name (_UID, 0x08)
                    Method (_DIS, 0, Serialized)
                    {
                        Store (0x80, PHRC)
                    }

                    Name (_PRS, ResourceTemplate ()
                    {
                        IRQ (Level, ActiveLow, Shared, )
                            {1,3,4,5,6,7,11,12,14,15}
                    })
                    Method (_CRS, 0, Serialized)
                    {
                        Name (RTLH, ResourceTemplate ()
                        {
                            IRQ (Level, ActiveLow, Shared, _Y1B)
                                {}
                        })
                        CreateWordField (RTLH, \_SB.PCI0.LPCB.LNKH._CRS._Y1B._INT, IRQ0)
                        Store (Zero, IRQ0)
                        ShiftLeft (0x01, And (PHRC, 0x0F), IRQ0)
                        Return (RTLH)
                    }

                    Method (_SRS, 1, Serialized)
                    {
                        CreateWordField (Arg0, 0x01, IRQ0)
                        FindSetRightBit (IRQ0, Local0)
                        Decrement (Local0)
                        Store (Local0, PHRC)
                    }

                    Method (_STA, 0, Serialized)
                    {
                        If (And (PHRC, 0x80))
                        {
                            Return (0x09)
                        }
                        Else
                        {
                            Return (0x0B)
                        }
                    }
                }

                Device (DMAC)
                {
                    Name (_HID, EisaId ("PNP0200"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0000,             // Range Minimum
                            0x0000,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            )
                        IO (Decode16,
                            0x0081,             // Range Minimum
                            0x0081,             // Range Maximum
                            0x01,               // Alignment
                            0x11,               // Length
                            )
                        IO (Decode16,
                            0x0093,             // Range Minimum
                            0x0093,             // Range Maximum
                            0x01,               // Alignment
                            0x0D,               // Length
                            )
                        IO (Decode16,
                            0x00C0,             // Range Minimum
                            0x00C0,             // Range Maximum
                            0x01,               // Alignment
                            0x20,               // Length
                            )
                        DMA (Compatibility, NotBusMaster, Transfer8_16, )
                            {4}
                    })
                }

                Device (FWHD)
                {
                    Name (_HID, EisaId ("INT0800"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        Memory32Fixed (ReadOnly,
                            0xFF000000,         // Address Base
                            0x01000000,         // Address Length
                            )
                    })
                }

                Device (HPET)
                {
                    Name (_HID, EisaId ("PNP0103"))
                    Name (_CID, EisaId ("PNP0C01"))
                    Name (BUF0, ResourceTemplate ()
                    {
                        Memory32Fixed (ReadOnly,
                            0xFED00000,         // Address Base
                            0x00000400,         // Address Length
                            _Y1C)
                    })
                    Method (_STA, 0, NotSerialized)
                    {
                        If (LGreaterEqual (OSYS, 0x07D1))
                        {
                            If (HPAE)
                            {
                                Return (0x0F)
                            }
                        }
                        Else
                        {
                            If (HPAE)
                            {
                                Return (0x0B)
                            }
                        }

                        Return (0x00)
                    }

                    Method (_CRS, 0, Serialized)
                    {
                        If (HPAE)
                        {
                            CreateDWordField (BUF0, \_SB.PCI0.LPCB.HPET._Y1C._BAS, HPT0)
                            If (LEqual (HPAS, 0x01))
                            {
                                Store (0xFED01000, HPT0)
                            }

                            If (LEqual (HPAS, 0x02))
                            {
                                Store (0xFED02000, HPT0)
                            }

                            If (LEqual (HPAS, 0x03))
                            {
                                Store (0xFED03000, HPT0)
                            }
                        }

                        Return (BUF0)
                    }
                }

                Device (IPIC)
                {
                    Name (_HID, EisaId ("PNP0000"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0020,             // Range Minimum
                            0x0020,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0024,             // Range Minimum
                            0x0024,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0028,             // Range Minimum
                            0x0028,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x002C,             // Range Minimum
                            0x002C,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0030,             // Range Minimum
                            0x0030,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0034,             // Range Minimum
                            0x0034,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0038,             // Range Minimum
                            0x0038,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x003C,             // Range Minimum
                            0x003C,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A0,             // Range Minimum
                            0x00A0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A4,             // Range Minimum
                            0x00A4,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00A8,             // Range Minimum
                            0x00A8,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00AC,             // Range Minimum
                            0x00AC,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00B0,             // Range Minimum
                            0x00B0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00B4,             // Range Minimum
                            0x00B4,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00B8,             // Range Minimum
                            0x00B8,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x00BC,             // Range Minimum
                            0x00BC,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x04D0,             // Range Minimum
                            0x04D0,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IRQNoFlags ()
                            {2}
                    })
                }

                Device (MATH)
                {
                    Name (_HID, EisaId ("PNP0C04"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x00F0,             // Range Minimum
                            0x00F0,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IRQNoFlags ()
                            {13}
                    })
                }

                Device (LDRC)
                {
                    Name (_HID, EisaId ("PNP0C02"))
                    Name (_UID, 0x02)
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x002E,             // Range Minimum
                            0x002E,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x004E,             // Range Minimum
                            0x004E,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0061,             // Range Minimum
                            0x0061,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0063,             // Range Minimum
                            0x0063,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0065,             // Range Minimum
                            0x0065,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0067,             // Range Minimum
                            0x0067,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0080,             // Range Minimum
                            0x0080,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0092,             // Range Minimum
                            0x0092,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x00B2,             // Range Minimum
                            0x00B2,             // Range Maximum
                            0x01,               // Alignment
                            0x02,               // Length
                            )
                        IO (Decode16,
                            0x0068,             // Range Minimum
                            0x0068,             // Range Maximum
                            0x01,               // Alignment
                            0x08,               // Length
                            )
                        IO (Decode16,
                            0x0800,             // Range Minimum
                            0x0800,             // Range Maximum
                            0x01,               // Alignment
                            0x10,               // Length
                            )
                        IO (Decode16,
                            0x1000,             // Range Minimum
                            0x1000,             // Range Maximum
                            0x01,               // Alignment
                            0x80,               // Length
                            )
                        IO (Decode16,
                            0x1180,             // Range Minimum
                            0x1180,             // Range Maximum
                            0x01,               // Alignment
                            0x40,               // Length
                            )
                        IO (Decode16,
                            0xFE00,             // Range Minimum
                            0xFE00,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        Memory32Fixed (ReadWrite,
                            0xFF800000,         // Address Base
                            0x00001000,         // Address Length
                            )
                    })
                }

                Device (RTC)
                {
                    Name (_HID, EisaId ("PNP0B00"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0070,             // Range Minimum
                            0x0070,             // Range Maximum
                            0x01,               // Alignment
                            0x08,               // Length
                            )
                        IRQNoFlags ()
                            {8}
                    })
                }

                Device (TIMR)
                {
                    Name (_HID, EisaId ("PNP0100"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0040,             // Range Minimum
                            0x0040,             // Range Maximum
                            0x01,               // Alignment
                            0x04,               // Length
                            )
                        IO (Decode16,
                            0x0050,             // Range Minimum
                            0x0050,             // Range Maximum
                            0x10,               // Alignment
                            0x04,               // Length
                            )
                        IRQNoFlags ()
                            {0}
                    })
                }

                Device (EC0)
                {
                    Name (_HID, EisaId ("PNP0C09"))
                    Name (_GPE, 0x17)
                    Name (EBNE, 0x00)
                    Method (_STA, 0, NotSerialized)
                    {
                        Return (0x0F)
                    }

                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0062,             // Range Minimum
                            0x0062,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0066,             // Range Minimum
                            0x0066,             // Range Maximum
                            0x00,               // Alignment
                            0x01,               // Length
                            )
                    })
                    OperationRegion (ECO1, SystemIO, 0x62, 0x01)
                    Field (ECO1, ByteAcc, Lock, Preserve)
                    {
                        PX62,   8
                    }

                    OperationRegion (ECO2, SystemIO, 0x66, 0x01)
                    Field (ECO2, ByteAcc, Lock, Preserve)
                    {
                        PX66,   8
                    }

                    OperationRegion (RAM, EmbeddedControl, 0x00, 0xFF)
                    Field (RAM, ByteAcc, Lock, Preserve)
                    {
                                Offset (0x0A), 
                            ,   1, 
                        BLNK,   1, 
                        WLLD,   2, 
                        BTLD,   2, 
                                Offset (0x13), 
                        URTB,   8, 
                                Offset (0x70), 
                            ,   1, 
                        KLID,   1, 
                            ,   3, 
                        KACS,   1, 
                                Offset (0x71), 
                        WLEN,   1, 
                        BTEN,   1, 
                        DCKS,   1, 
                        MUTE,   1, 
                        KBID,   3, 
                                Offset (0x72), 
                            ,   2, 
                        KEYW,   1, 
                        RTCW,   1, 
                        LIDW,   1, 
                        BL2W,   1, 
                        TPDW,   1, 
                                Offset (0x75), 
                        SWBL,   1, 
                        KLMA,   1, 
                                Offset (0x76), 
                        SYSC,   4, 
                        SYSO,   4
                    }

                    Field (RAM, ByteAcc, Lock, Preserve)
                    {
                                Offset (0x7F), 
                        BNEN,   1, 
                        BNCM,   1, 
                        BNDM,   1, 
                        BNVE,   1, 
                                Offset (0x83), 
                        BNAC,   4, 
                        BNDC,   4
                    }

                    Field (RAM, ByteAcc, Lock, Preserve)
                    {
                                Offset (0x01), 
                        TIID,   8, 
                                Offset (0x10), 
                            ,   1, 
                        KTEE,   1, 
                                Offset (0x11), 
                        KPPS,   1, 
                                Offset (0x91), 
                        TTID,   8, 
                        KCSS,   1, 
                        KCTT,   1, 
                        KDTT,   1, 
                        KOSD,   1, 
                        KVTP,   1, 
                                Offset (0xA8), 
                        THS0,   8, 
                        THS1,   8, 
                        THS2,   8, 
                        THS3,   8, 
                        THS4,   8, 
                        THS5,   8, 
                        THS6,   8, 
                        THS7,   8
                    }

                    Field (RAM, ByteAcc, Lock, Preserve)
                    {
                                Offset (0x92), 
                        KTAF,   8
                    }

                    Field (RAM, ByteAcc, Lock, Preserve)
                    {
                                Offset (0x92), 
                        THSL,   4
                    }

                    Field (RAM, ByteAcc, Lock, Preserve)
                    {
                                Offset (0xD0), 
                        TSP0,   8, 
                        TSC0,   8, 
                        TSP1,   8, 
                        TSC1,   8, 
                        TSP2,   8, 
                        TSC2,   8, 
                        TSP3,   8, 
                        TSC3,   8, 
                        TSP4,   8, 
                        TSC4,   8, 
                        TSP5,   8, 
                        TSC5,   8, 
                        TSP6,   8, 
                        TSC6,   8, 
                        TSP7,   8, 
                        TSC7,   8
                    }

                    Method (_REG, 2, NotSerialized)
                    {
                        If (LEqual (Arg0, 0x03))
                        {
                            Store (Arg1, ECON)
                            TINI ()
                            Store (0x05, SYSO)
                            If (LEqual (OSYS, 0x07D6))
                            {
                                Store (0x00, BNEN)
                            }
                        }

                        Store (0x01, \_SB.PCI0.GFX0.CLID)
                    }

                    Method (TINI, 0, NotSerialized)
                    {
                        If (\ECON)
                        {
                            Store (0x00, KTAF)
                            Store (0x01, KTEE)
                        }
                        Else
                        {
                            WBEC (0x92, 0x00)
                            MBEC (0x10, 0xFD, 0x02)
                        }
                    }

                    Method (_Q16, 0, NotSerialized)
                    {
                        Store (0x16, P80H)
                        LAMN (0x01)
                    }

                    Method (_Q24, 0, NotSerialized)
                    {
                        Store (0x24, P80H)
                        LAMN (0x6A)
                    }

                    Method (_Q25, 0, NotSerialized)
                    {
                        Store (0x25, P80H)
                        LAMN (0x6D)
                    }

                    Method (_Q17, 0, NotSerialized)
                    {
                        Store (0x17, P80H)
                        Notify (\_SB.SLPB, 0x80)
                    }

                    Method (HKDS, 1, NotSerialized)
                    {
                        If (LEqual (0x00, DSEN))
                        {
                            If (LEqual (Arg0, 0x10))
                            {
                                If (IGDS)
                                {
                                    If (\ASLB)
                                    {
                                        \_SB.PCI0.GFX0.GHDS (0x00)
                                        Return (0x00)
                                    }
                                }

                                Store (PHSR (0x27, 0x00), Local0)
                                Increment (Local0)
                                If (LGreaterEqual (Local0, 0x03))
                                {
                                    Store (0x00, Local0)
                                }
                            }
                            Else
                            {
                                Store (Arg0, Local0)
                            }

                            If (LEqual (Local0, 0x00))
                            {
                                Store (0x0101, NSTE)
                            }

                            If (LEqual (Local0, 0x01))
                            {
                                Store (0x0808, NSTE)
                            }

                            If (LEqual (Local0, 0x02))
                            {
                                Store (0x0909, NSTE)
                            }

                            If (LEqual (Local0, 0x03))
                            {
                                Store (0x0404, NSTE)
                            }

                            If (LEqual (Local0, 0x04))
                            {
                                Store (0x0202, NSTE)
                            }

                            If (LEqual (Local0, 0x05))
                            {
                                Store (0x0C0C, NSTE)
                            }

                            If (LEqual (Local0, 0x06))
                            {
                                Store (0x0A0A, NSTE)
                            }

                            If (IGDS)
                            {
                                If (\ASLB)
                                {
                                    \_SB.PCI0.GFX0.SNDL (NSTE)
                                    \_SB.PCI0.GFX0.GHDS (0x04)
                                }
                                Else
                                {
                                    Notify (\_SB.PCI0.GFX0, 0x80)
                                }
                            }
                            Else
                            {
                                Notify (\_SB.PCI0.PEGP.VGA, 0x80)
                            }
                        }

                        If (LEqual (0x01, DSEN))
                        {
                            If (LEqual (Arg0, 0x10))
                            {
                                PHSR (0x26, 0x00)
                            }
                            Else
                            {
                                PHSR (0x28, Arg0)
                            }
                        }
			    Return(Package(0x02){0x00, 0x00})
                    }

                    Method (_Q19, 0, NotSerialized)
                    {
                        Store (0x19, P80H)
                        If (\_SB.PCI0.LPCB.EC0.KLMA)
                        {
                            LAMN (0x05)
                        }
                        Else
                        {
                            HKDS (0x10)
                        }
                    }

                    Method (_Q80, 0, NotSerialized)
                    {
                        Store (0x80, P80H)
                        HKDS (0x00)
                    }

                    Method (_Q81, 0, NotSerialized)
                    {
                        Store (0x81, P80H)
                        HKDS (0x01)
                    }

                    Method (_Q82, 0, NotSerialized)
                    {
                        Store (0x82, P80H)
                        HKDS (0x02)
                    }

                    Method (_Q83, 0, NotSerialized)
                    {
                        Store (0x83, P80H)
                        HKDS (0x03)
                    }

                    Method (_Q84, 0, NotSerialized)
                    {
                        Store (0x84, P80H)
                        HKDS (0x04)
                    }

                    Method (_Q85, 0, NotSerialized)
                    {
                        Store (0x85, P80H)
                        HKDS (0x05)
                    }

                    Method (_Q86, 0, NotSerialized)
                    {
                        Store (0x86, P80H)
                        HKDS (0x06)
                    }

                    Method (_Q1A, 0, NotSerialized)
                    {
                        Store (0x1A, P80H)
                        LAMN (0x06)
                    }

                    Method (_Q5C, 0, NotSerialized)
                    {
                        Store (0x5C, P80H)
                        HKEY (0x5C)
                    }

                    Method (_Q1E, 0, NotSerialized)
                    {
                        Store (0x1E, P80H)
                        LAMN (0x20)
                    }

                    Method (_Q1F, 0, NotSerialized)
                    {
                        Store (0x1F, P80H)
                        LAMN (0x21)
                    }

                    Method (_Q22, 0, NotSerialized)
                    {
                        Store (0x22, P80H)
                        LAMN (0x07)
                    }

                    Method (_Q10, 0, NotSerialized)
                    {
                        Store (0x10, P80H)
                        LAMN (0x30)
                    }

                    Method (_Q11, 0, NotSerialized)
                    {
                        Store (0x11, P80H)
                        LAMN (0x36)
                    }

                    Method (_Q12, 0, NotSerialized)
                    {
                        Store (0x12, P80H)
                        LAMN (0x31)
                    }

                    Method (_Q13, 0, NotSerialized)
                    {
                        Store (0x13, P80H)
                        LAMN (0x11)
                    }

                    Method (_Q14, 0, NotSerialized)
                    {
                        Store (0x14, P80H)
                        LAMN (0x12)
                    }

                    Method (_Q15, 0, NotSerialized)
                    {
                        Store (0x15, P80H)
                        LAMN (0x13)
                    }

                    Method (_Q1B, 0, NotSerialized)
                    {
                        Store (0x1B, P80H)
                        LAMN (0x08)
                    }

                    Method (_Q1C, 0, NotSerialized)
                    {
                        Store (0x1C, P80H)
                        LAMN (0x73)
                        If (BNEN) {}
                        Else
                        {
                            If (IGDS)
                            {
                                \BIAN (0x86)
                            }
                            Else
                            {
                                Notify (\_SB.PCI0.PEGP.VGA.LCD, 0x86)
                            }
                        }
                    }

                    Method (_Q1D, 0, NotSerialized)
                    {
                        Store (0x1D, P80H)
                        LAMN (0x74)
                        If (BNEN) {}
                        Else
                        {
                            If (IGDS)
                            {
                                \BIAN (0x87)
                            }
                            Else
                            {
                                Notify (\_SB.PCI0.PEGP.VGA.LCD, 0x87)
                            }
                        }
                    }

                    Method (_Q23, 0, NotSerialized)
                    {
                        Store (0x23, P80H)
                        LAMN (0x44)
                    }

                    Method (_Q28, 0, NotSerialized)
                    {
                        Store (0x28, P80H)
                        \_SB.PCI0.LPCB.EC0.MCEB.HQ28 ()
                    }

                    Method (_Q32, 0, NotSerialized)
                    {
                        Store (0x32, P80H)
                        HKEY (0x32)
                        Store (0x00, KCTT)
                    }

                    Method (_Q33, 0, NotSerialized)
                    {
                        Store (0x33, P80H)
                        Store (0x00, KCSS)
                        NGV3 (0x00, 0x00)
                    }

                    Method (_Q34, 0, NotSerialized)
                    {
                        Store (0x34, P80H)
                        Store (0x01, KCSS)
                        NGV3 (0x00, 0x01)
                    }

                    Method (_Q35, 0, NotSerialized)
                    {
                        Store (0x35, P80H)
                        HKEY (0x35)
                        Store (0x01, KCTT)
                    }

                    Method (_Q36, 0, NotSerialized)
                    {
                        Store (0x36, P80H)
                        Store (0x01, KOSD)
                        Sleep (0x01F4)
                        NTMR ()
                    }

                    Method (_Q3F, 0, NotSerialized)
                    {
                        Store (0x3F, P80H)
                        HKEY (0x3F)
                    }

                    Method (_Q40, 0, NotSerialized)
                    {
                        Store (0x40, P80H)
                        Notify (\_SB.PCI0.LPCB.EC0.BAT0, 0x81)
                    }

                    Method (_Q41, 0, NotSerialized)
                    {
                        Store (0x41, P80H)
                        Notify (\_SB.PCI0.LPCB.EC0.BAT0, 0x81)
                    }

                    Method (_Q48, 0, NotSerialized)
                    {
                        Store (0x48, P80H)
                        Notify (\_SB.PCI0.LPCB.EC0.BAT0, 0x80)
                    }

                    Method (_Q4C, 0, NotSerialized)
                    {
                        Store (0x4C, P80H)
                        If (B0ST)
                        {
                            Notify (\_SB.PCI0.LPCB.EC0.BAT0, 0x80)
                        }
                    }

                    Method (_Q50, 0, NotSerialized)
                    {
                        Store (0x50, P80H)
                        Notify (\_SB.PCI0.LPCB.EC0.ADP1, 0x80)
                    }

                    Method (_Q51, 0, NotSerialized)
                    {
                        Store (0x51, P80H)
                        Notify (\_SB.PCI0.LPCB.EC0.ADP1, 0x80)
                    }

                    Method (_Q52, 0, NotSerialized)
                    {
                        Store (0x52, P80H)
                        Notify (\_SB.LID0, 0x80)
                    }

                    Method (_Q53, 0, NotSerialized)
                    {
                        Store (0x53, P80H)
                        Notify (\_SB.LID0, 0x80)
                    }

                    Method (NTMR, 0, NotSerialized)
                    {
                        Notify (\_TZ.TZS0, 0x80)
                        Notify (\_TZ.TZS1, 0x80)
                    }

                    Method (NGV3, 2, NotSerialized)
                    {
                        \_TZ.SPSV (Arg0, Arg1)
                        NTMR ()
                    }

                    Field (RAM, ByteAcc, Lock, Preserve)
                    {
                                Offset (0x02), 
                        NBID,   8, 
                                Offset (0x17), 
                            ,   5, 
                        SM0F,   1, 
                            ,   1, 
                        SM1F,   1, 
                                Offset (0x88), 
                        NB0A,   1, 
                            ,   2, 
                        NB0R,   1, 
                        NB0L,   1, 
                        NB0F,   1, 
                        NB0N,   1, 
                                Offset (0x89), 
                        NB1A,   1, 
                            ,   2, 
                        NB1R,   1, 
                        NB1L,   1, 
                        NB1F,   1, 
                        NB1N,   1
                    }

                    Field (RAM, ByteAcc, Lock, Preserve)
                    {
                                Offset (0x88), 
                        NB0S,   8, 
                        NB1S,   8
                    }

                    Field (RAM, ByteAcc, Lock, Preserve)
                    {
                                Offset (0xE0), 
                        BSRC,   16, 
                        BSFC,   16, 
                        BSPE,   16, 
                        BSAC,   16, 
                        BSVO,   16, 
                            ,   15, 
                        BSCM,   1, 
                        BSCU,   16, 
                        BSTV,   16
                    }

                    Field (RAM, ByteAcc, Lock, Preserve)
                    {
                                Offset (0xE0), 
                        BSDC,   16, 
                        BSDV,   16, 
                        BSSN,   16
                    }

                    Field (RAM, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0xE0), 
                        BSMN,   128
                    }

                    Field (RAM, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0xE0), 
                        BSDN,   128
                    }

                    Field (RAM, ByteAcc, NoLock, Preserve)
                    {
                                Offset (0xE0), 
                        BSCH,   128
                    }

                    Mutex (BATM, 0x07)
                    Method (GBIF, 3, NotSerialized)
                    {
                        Acquire (BATM, 0xFFFF)
                        If (Arg2)
                        {
                            Store (0xFFFFFFFF, Index (Arg1, 0x01))
                            Store (0xFFFFFFFF, Index (Arg1, 0x02))
                            Store (0xFFFFFFFF, Index (Arg1, 0x04))
                            Store (0x00, Index (Arg1, 0x05))
                            Store (0x00, Index (Arg1, 0x06))
                        }
                        Else
                        {
                            And (Arg0, 0xF0, NBID)
                            Store (BSCM, Local0)
                            XOr (Local0, 0x01, Index (Arg1, 0x00))
                            Or (Arg0, 0x01, NBID)
                            If (Local0)
                            {
                                Multiply (BSDC, 0x0A, Local1)
                            }
                            Else
                            {
                                Store (BSDC, Local1)
                            }

                            Store (Local1, Index (Arg1, 0x01))
                            And (Arg0, 0xF0, NBID)
                            If (Local0)
                            {
                                Multiply (BSFC, 0x0A, Local2)
                            }
                            Else
                            {
                                Store (BSFC, Local2)
                            }

                            Store (Local2, Index (Arg1, 0x02))
                            Or (Arg0, 0x01, NBID)
                            Store (BSDV, Index (Arg1, 0x04))
                            Divide (Local2, 0x64, Local7, Local6)
                            Multiply (Local6, 0x05, Local3)
                            Store (Local3, Index (Arg1, 0x05))
                            Multiply (0x03, 0x02, Local4)
                            Add (Local4, 0x01, Local4)
                            Multiply (Local6, Local4, Local4)
                            Divide (Local4, 0x02, Local7, Local4)
                            Store (Local4, Index (Arg1, 0x06))
                            Subtract (Local3, Local4, Index (Arg1, 0x07))
                            Subtract (Local2, Local3, Index (Arg1, 0x08))
                            Store (BSSN, Local7)
                            Name (SERN, Buffer (0x06)
                            {
                                "     "
                            })
                            Store (0x04, Local6)
                            While (Local7)
                            {
                                Divide (Local7, 0x0A, Local5, Local7)
                                Add (Local5, 0x30, Index (SERN, Local6))
                                Decrement (Local6)
                            }

                            Store (SERN, Index (Arg1, 0x0A))
                            Or (Arg0, 0x03, NBID)
                            Store (BSDN, Index (Arg1, 0x09))
                            Or (Arg0, 0x04, NBID)
                            Store (BSCH, Index (Arg1, 0x0B))
                            Or (Arg0, 0x02, NBID)
                            Store (BSMN, Index (Arg1, 0x0C))
                        }

                        Release (BATM)
                        Return (Arg1)
                    }

                    Method (GBST, 4, NotSerialized)
                    {
                        If (Arg0)
                        {
                            Store (SM1F, Local0)
                        }
                        Else
                        {
                            Store (SM0F, Local0)
                        }

                        If (Local0)
                        {
                            And (Arg1, ShiftLeft (0x01, 0x03), Local0)
                            If (LEqual (Local0, 0x00))
                            {
                                Return (Arg3)
                            }
                        }

                        Acquire (BATM, 0xFFFF)
                        If (And (Arg1, 0x02))
                        {
                            Store (0x02, Local0)
                            If (And (Arg1, 0x20))
                            {
                                Store (0x00, Local0)
                            }
                        }
                        Else
                        {
                            If (And (Arg1, 0x04))
                            {
                                Store (0x01, Local0)
                            }
                            Else
                            {
                                Store (0x00, Local0)
                            }
                        }

                        If (And (Arg1, 0x10))
                        {
                            Or (Local0, 0x04, Local0)
                        }

                        If (And (Arg1, 0x01))
                        {
                            And (Arg0, 0xF0, NBID)
                            Store (BSAC, Local1)
                            Store (BSRC, Local2)
                            If (ACST)
                            {
                                If (And (Arg1, 0x20))
                                {
                                    Store (BSFC, Local2)
                                }
                            }

                            If (Arg2)
                            {
                                Multiply (Local2, 0x0A, Local2)
                            }

                            Store (BSVO, Local3)
                            If (LGreaterEqual (Local1, 0x8000))
                            {
                                If (And (Local0, 0x01))
                                {
                                    Subtract (0x00010000, Local1, Local1)
                                }
                                Else
                                {
                                    Store (0x00, Local1)
                                }
                            }
                            Else
                            {
                                If (LEqual (And (Local0, 0x02), 0x00))
                                {
                                    Store (0x00, Local1)
                                }
                            }

                            If (Arg2)
                            {
                                Multiply (Local3, Local1, Local1)
                                Divide (Local1, 0x03E8, Local7, Local1)
                            }
                        }
                        Else
                        {
                            Store (0x00, Local0)
                            Store (0xFFFFFFFF, Local1)
                            Store (0xFFFFFFFF, Local2)
                            Store (0xFFFFFFFF, Local3)
                        }

                        Store (Local0, Index (Arg3, 0x00))
                        Store (Local1, Index (Arg3, 0x01))
                        Store (Local2, Index (Arg3, 0x02))
                        Store (Local3, Index (Arg3, 0x03))
                        Release (BATM)
                        Return (Arg3)
                    }

                    Name (B0ST, 0x00)
                    Device (BAT0)
                    {
                        Name (_HID, EisaId ("PNP0C0A"))
                        Name (_UID, 0x01)
                        Method (_PCL, 0, NotSerialized)
                        {
                            Return (\_SB)
                        }

                        Name (B0IP, Package (0x0D)
                        {
                            0x01, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0x01, 
                            0xFFFFFFFF, 
                            0x00, 
                            0x00, 
                            0x5A, 
                            0x5A, 
                            "", 
                            "100", 
                            "Lion", 
                            0x00
                        })
                        Name (B0SP, Package (0x04)
                        {
                            0x00, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF, 
                            0xFFFFFFFF
                        })
                        Method (_STA, 0, NotSerialized)
                        {
                            If (\ECON)
                            {
                                Store (NB0A, Local1)
                                If (NB0N)
                                {
                                    Store (0x00, Local1)
                                }
                            }
                            Else
                            {
                                Store (RBEC (0x88), Local0)
                                ShiftRight (Local0, 0x00, Local1)
                                And (Local1, 0x01, Local1)
                                If (And (Local0, 0x40))
                                {
                                    Store (0x00, Local1)
                                }
                            }

                            Store (Local1, B0ST)
                            If (Local1)
                            {
                                Return (0x1F)
                            }
                            Else
                            {
                                Return (0x0F)
                            }
                        }

                        Method (_BIF, 0, NotSerialized)
                        {
                            Store (B0ST, Local6)
                            Store (0x14, Local7)
                            While (LAnd (Local6, Local7))
                            {
                                If (\ECON)
                                {
                                    Store (NB0S, Local1)
                                }
                                Else
                                {
                                    Store (RBEC (0x88), Local1)
                                }

                                If (And (Local1, 0x08))
                                {
                                    Store (0x00, Local6)
                                }
                                Else
                                {
                                    Sleep (0x01F4)
                                    Decrement (Local7)
                                }
                            }

                            Return (GBIF (0x00, B0IP, Local6))
                        }

                        Method (_BST, 0, NotSerialized)
                        {
                            XOr (DerefOf (Index (B0IP, 0x00)), 0x01, Local0)
                            If (\ECON)
                            {
                                Store (NB0S, Local1)
                            }
                            Else
                            {
                                Store (RBEC (0x88), Local1)
                            }

                            Return (GBST (0x00, Local1, Local0, B0SP))
                        }
                    }

                    Name (ACST, 0x01)
                    Device (ADP1)
                    {
                        Name (_HID, "ACPI0003")
                        Method (_PSR, 0, NotSerialized)
                        {
                            If (ECON)
                            {
                                Store (KACS, Local1)
                            }
                            Else
                            {
                                Store (RBEC (0x70), Local0)
                                And (Local0, 0x20, Local1)
                            }

                            If (Local1)
                            {
                                Store (0x01, ACST)
                            }
                            Else
                            {
                                Store (0x00, ACST)
                            }

                            Return (ACST)
                        }

                        Method (_PCL, 0, NotSerialized)
                        {
                            Return (\_SB)
                        }

                        Method (_STA, 0, NotSerialized)
                        {
                            Return (0x0F)
                        }
                    }

                    OperationRegion (RAMH, EmbeddedControl, 0x00, 0xFF)
                    Field (RAMH, ByteAcc, Lock, Preserve)
                    {
                                Offset (0x4B), 
                        HID3,   8, 
                        HID0,   8
                    }

                    Device (MCEB)
                    {
                        Name (_HID, EisaId ("PNP0C32"))
                        Name (_UID, 0x02)
                        Method (_STA, 0, NotSerialized)
                        {
                            If (LEqual (OSYS, 0x07D6))
                            {
                                Store (0x0F, Local0)
                            }
                            Else
                            {
                                Store (0x00, Local0)
                            }

                            Return (Local0)
                        }

                        Method (GHID, 0, NotSerialized)
                        {
                            If (HSTE)
                            {
                                If (LEqual (HID0, 0x09))
                                {
                                    Notify (\_SB.PCI0.LPCB.EC0.MCEB, 0x02)
                                }
                            }

                            Return (Buffer (0x01)
                            {
                                0x02
                            })
                        }

                        Method (HRSM, 0, NotSerialized)
                        {
                            If (HSTE)
                            {
                                If (LOr (LEqual (HID0, 0x09), LEqual (HID3, 0x09)))
                                {
                                    Notify (\_SB.PCI0.LPCB.EC0.MCEB, 0x02)
                                }
                            }
                        }

                        Method (HQ28, 0, NotSerialized)
                        {
                            If (HSTE)
                            {
                                Notify (\_SB.PCI0.LPCB.EC0.MCEB, 0x80)
                            }
                        }
                    }
                }

                Device (KBD0)
                {
                    Name (_HID, EisaId ("PNP0303"))
                    Name (_CRS, ResourceTemplate ()
                    {
                        IO (Decode16,
                            0x0060,             // Range Minimum
                            0x0060,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IO (Decode16,
                            0x0064,             // Range Minimum
                            0x0064,             // Range Maximum
                            0x01,               // Alignment
                            0x01,               // Length
                            )
                        IRQ (Edge, ActiveHigh, Exclusive, )
                            {1}
                    })
                }

                Device (PS2M)
                {
                    Name (_HID, EisaId ("SYN030F"))
                    Name (_CID, Package (0x03)
                    {
                        EisaId ("SYN0300"), 
                        EisaId ("SYN0002"), 
                        EisaId ("PNP0F13")
                    })
                    Name (_CRS, ResourceTemplate ()
                    {
                        IRQ (Edge, ActiveHigh, Exclusive, )
                            {12}
                    })
                }
            }

            Device (PATA)
            {
                Name (_ADR, 0x001F0001)
                OperationRegion (PACS, PCI_Config, 0x40, 0xC0)
                Field (PACS, DWordAcc, NoLock, Preserve)
                {
                    PRIT,   16, 
                            Offset (0x04), 
                    PSIT,   4, 
                            Offset (0x08), 
                    SYNC,   4, 
                            Offset (0x0A), 
                    SDT0,   2, 
                        ,   2, 
                    SDT1,   2, 
                            Offset (0x14), 
                    ICR0,   4, 
                    ICR1,   4, 
                    ICR2,   4, 
                    ICR3,   4, 
                    ICRP,   2, 
                    ICRS,   2, 
                    ICR5,   4
                }

                Device (PRID)
                {
                    Name (_ADR, 0x00)
                    Method (_GTM, 0, NotSerialized)
                    {
                        Name (PBUF, Buffer (0x14)
                        {
                            /* 0000 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                            /* 0008 */    0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 
                            /* 0010 */    0x00, 0x00, 0x00, 0x00
                        })
                        CreateDWordField (PBUF, 0x00, PIO0)
                        CreateDWordField (PBUF, 0x04, DMA0)
                        CreateDWordField (PBUF, 0x08, PIO1)
                        CreateDWordField (PBUF, 0x0C, DMA1)
                        CreateDWordField (PBUF, 0x10, FLAG)
                        Store (GETP (PRIT), PIO0)
                        Store (GDMA (And (SYNC, 0x01), And (ICR3, 0x01), 
                            And (ICR0, 0x01), SDT0, And (ICR1, 0x01)), DMA0)
                        If (LEqual (DMA0, 0xFFFFFFFF))
                        {
                            Store (PIO0, DMA0)
                        }

                        If (And (PRIT, 0x4000))
                        {
                            If (LEqual (And (PRIT, 0x90), 0x80))
                            {
                                Store (0x0384, PIO1)
                            }
                            Else
                            {
                                Store (GETT (PSIT), PIO1)
                            }
                        }
                        Else
                        {
                            Store (0xFFFFFFFF, PIO1)
                        }

                        Store (GDMA (And (SYNC, 0x02), And (ICR3, 0x02), 
                            And (ICR0, 0x02), SDT1, And (ICR1, 0x02)), DMA1)
                        If (LEqual (DMA1, 0xFFFFFFFF))
                        {
                            Store (PIO1, DMA1)
                        }

                        Store (GETF (And (SYNC, 0x01), And (SYNC, 0x02), 
                            PRIT), FLAG)
                        If (And (LEqual (PIO0, 0xFFFFFFFF), LEqual (DMA0, 0xFFFFFFFF)))
                        {
                            Store (0x78, PIO0)
                            Store (0x14, DMA0)
                            Store (0x03, FLAG)
                        }

                        Return (PBUF)
                    }

                    Method (_STM, 3, NotSerialized)
                    {
                        CreateDWordField (Arg0, 0x00, PIO0)
                        CreateDWordField (Arg0, 0x04, DMA0)
                        CreateDWordField (Arg0, 0x08, PIO1)
                        CreateDWordField (Arg0, 0x0C, DMA1)
                        CreateDWordField (Arg0, 0x10, FLAG)
                        If (LEqual (SizeOf (Arg1), 0x0200))
                        {
                            And (PRIT, 0xC0F0, PRIT)
                            And (SYNC, 0x02, SYNC)
                            Store (0x00, SDT0)
                            And (ICR0, 0x02, ICR0)
                            And (ICR1, 0x02, ICR1)
                            And (ICR3, 0x02, ICR3)
                            And (ICR5, 0x02, ICR5)
                            CreateWordField (Arg1, 0x62, W490)
                            CreateWordField (Arg1, 0x6A, W530)
                            CreateWordField (Arg1, 0x7E, W630)
                            CreateWordField (Arg1, 0x80, W640)
                            CreateWordField (Arg1, 0xB0, W880)
                            CreateWordField (Arg1, 0xBA, W930)
                            Or (PRIT, 0x8004, PRIT)
                            If (LAnd (And (FLAG, 0x02), And (W490, 0x0800)))
                            {
                                Or (PRIT, 0x02, PRIT)
                            }

                            Or (PRIT, SETP (PIO0, W530, W640), PRIT)
                            If (And (FLAG, 0x01))
                            {
                                Or (SYNC, 0x01, SYNC)
                                Store (SDMA (DMA0), SDT0)
                                If (LLess (DMA0, 0x1E))
                                {
                                    Or (ICR3, 0x01, ICR3)
                                }

                                If (LLess (DMA0, 0x3C))
                                {
                                    Or (ICR0, 0x01, ICR0)
                                }

                                If (And (W930, 0x2000))
                                {
                                    Or (ICR1, 0x01, ICR1)
                                }
                            }
                        }

                        If (LEqual (SizeOf (Arg2), 0x0200))
                        {
                            And (PRIT, 0xBF0F, PRIT)
                            Store (0x00, PSIT)
                            And (SYNC, 0x01, SYNC)
                            Store (0x00, SDT1)
                            And (ICR0, 0x01, ICR0)
                            And (ICR1, 0x01, ICR1)
                            And (ICR3, 0x01, ICR3)
                            And (ICR5, 0x01, ICR5)
                            CreateWordField (Arg2, 0x62, W491)
                            CreateWordField (Arg2, 0x6A, W531)
                            CreateWordField (Arg2, 0x7E, W631)
                            CreateWordField (Arg2, 0x80, W641)
                            CreateWordField (Arg2, 0xB0, W881)
                            CreateWordField (Arg2, 0xBA, W931)
                            Or (PRIT, 0x8040, PRIT)
                            If (LAnd (And (FLAG, 0x08), And (W491, 0x0800)))
                            {
                                Or (PRIT, 0x20, PRIT)
                            }

                            If (And (FLAG, 0x10))
                            {
                                Or (PRIT, 0x4000, PRIT)
                                If (LGreater (PIO1, 0xF0))
                                {
                                    Or (PRIT, 0x80, PRIT)
                                }
                                Else
                                {
                                    Or (PRIT, 0x10, PRIT)
                                    Store (SETT (PIO1, W531, W641), PSIT)
                                }
                            }

                            If (And (FLAG, 0x04))
                            {
                                Or (SYNC, 0x02, SYNC)
                                Store (SDMA (DMA1), SDT1)
                                If (LLess (DMA1, 0x1E))
                                {
                                    Or (ICR3, 0x02, ICR3)
                                }

                                If (LLess (DMA1, 0x3C))
                                {
                                    Or (ICR0, 0x02, ICR0)
                                }

                                If (And (W931, 0x2000))
                                {
                                    Or (ICR1, 0x02, ICR1)
                                }
                            }
                        }
                    }

                    Device (P_D0)
                    {
                        Name (_ADR, 0x00)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Name (PIB0, Buffer (0x0E)
                            {
                                /* 0000 */    0x03, 0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF, 0x03, 
                                /* 0008 */    0x00, 0x00, 0x00, 0x00, 0xA0, 0xEF
                            })
                            CreateByteField (PIB0, 0x01, PMD0)
                            CreateByteField (PIB0, 0x08, DMD0)
                            If (And (PRIT, 0x02))
                            {
                                If (LEqual (And (PRIT, 0x09), 0x08))
                                {
                                    Store (0x08, PMD0)
                                }
                                Else
                                {
                                    Store (0x0A, PMD0)
                                    ShiftRight (And (PRIT, 0x0300), 0x08, Local0)
                                    ShiftRight (And (PRIT, 0x3000), 0x0C, Local1)
                                    Add (Local0, Local1, Local2)
                                    If (LEqual (0x03, Local2))
                                    {
                                        Store (0x0B, PMD0)
                                    }

                                    If (LEqual (0x05, Local2))
                                    {
                                        Store (0x0C, PMD0)
                                    }
                                }
                            }
                            Else
                            {
                                Store (0x01, PMD0)
                            }

                            If (And (SYNC, 0x01))
                            {
                                Store (Or (SDT0, 0x40), DMD0)
                                If (And (ICR1, 0x01))
                                {
                                    If (And (ICR0, 0x01))
                                    {
                                        Add (DMD0, 0x02, DMD0)
                                    }

                                    If (And (ICR3, 0x01))
                                    {
                                        Store (0x45, DMD0)
                                    }
                                }
                            }
                            Else
                            {
                                Or (Subtract (And (PMD0, 0x07), 0x02), 0x20, DMD0)
                            }

                            Return (PIB0)
                        }
                    }

                    Device (P_D1)
                    {
                        Name (_ADR, 0x01)
                        Method (_GTF, 0, NotSerialized)
                        {
                            Name (PIB1, Buffer (0x0E)
                            {
                                /* 0000 */    0x03, 0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF, 0x03, 
                                /* 0008 */    0x00, 0x00, 0x00, 0x00, 0xB0, 0xEF
                            })
                            CreateByteField (PIB1, 0x01, PMD1)
                            CreateByteField (PIB1, 0x08, DMD1)
                            If (And (PRIT, 0x20))
                            {
                                If (LEqual (And (PRIT, 0x90), 0x80))
                                {
                                    Store (0x08, PMD1)
                                }
                                Else
                                {
                                    Add (And (PSIT, 0x03), ShiftRight (And (PSIT, 0x0C), 
                                        0x02), Local0)
                                    If (LEqual (0x05, Local0))
                                    {
                                        Store (0x0C, PMD1)
                                    }
                                    Else
                                    {
                                        If (LEqual (0x03, Local0))
                                        {
                                            Store (0x0B, PMD1)
                                        }
                                        Else
                                        {
                                            Store (0x0A, PMD1)
                                        }
                                    }
                                }
                            }
                            Else
                            {
                                Store (0x01, PMD1)
                            }

                            If (And (SYNC, 0x02))
                            {
                                Store (Or (SDT1, 0x40), DMD1)
                                If (And (ICR1, 0x02))
                                {
                                    If (And (ICR0, 0x02))
                                    {
                                        Add (DMD1, 0x02, DMD1)
                                    }

                                    If (And (ICR3, 0x02))
                                    {
                                        Store (0x45, DMD1)
                                    }
                                }
                            }
                            Else
                            {
                                Or (Subtract (And (PMD1, 0x07), 0x02), 0x20, DMD1)
                            }

                            Return (PIB1)
                        }
                    }
                }
            }

            Device (SATA)
            {
                Name (_ADR, 0x001F0002)
                OperationRegion (SACS, PCI_Config, 0x40, 0xC0)
                Field (SACS, DWordAcc, NoLock, Preserve)
                {
                    PRIT,   16, 
                    SECT,   16, 
                    PSIT,   4, 
                    SSIT,   4, 
                            Offset (0x08), 
                    SYNC,   4, 
                            Offset (0x0A), 
                    SDT0,   2, 
                        ,   2, 
                    SDT1,   2, 
                            Offset (0x0B), 
                    SDT2,   2, 
                        ,   2, 
                    SDT3,   2, 
                            Offset (0x14), 
                    ICR0,   4, 
                    ICR1,   4, 
                    ICR2,   4, 
                    ICR3,   4, 
                    ICR4,   4, 
                    ICR5,   4, 
                            Offset (0x50), 
                    MAPV,   2
                }
            }

            Device (SBUS)
            {
                Name (_ADR, 0x001F0003)
                OperationRegion (SMBP, PCI_Config, 0x40, 0xC0)
                Field (SMBP, DWordAcc, NoLock, Preserve)
                {
                        ,   2, 
                    I2CE,   1
                }

                OperationRegion (SMBI, SystemIO, 0x1C00, 0x10)
                Field (SMBI, ByteAcc, NoLock, Preserve)
                {
                    HSTS,   8, 
                            Offset (0x02), 
                    HCON,   8, 
                    HCOM,   8, 
                    TXSA,   8, 
                    DAT0,   8, 
                    DAT1,   8, 
                    HBDR,   8, 
                    PECR,   8, 
                    RXSA,   8, 
                    SDAT,   16
                }

                Method (SSXB, 2, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0x00)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Arg0, TXSA)
                    Store (Arg1, HCOM)
                    Store (0x48, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Method (SRXB, 1, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0xFFFF)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Or (Arg0, 0x01), TXSA)
                    Store (0x44, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (DAT0)
                    }

                    Return (0xFFFF)
                }

                Method (SWRB, 3, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0x00)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Arg0, TXSA)
                    Store (Arg1, HCOM)
                    Store (Arg2, DAT0)
                    Store (0x48, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Method (SRDB, 2, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0xFFFF)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Or (Arg0, 0x01), TXSA)
                    Store (Arg1, HCOM)
                    Store (0x48, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (DAT0)
                    }

                    Return (0xFFFF)
                }

                Method (SWRW, 3, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0x00)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Arg0, TXSA)
                    Store (Arg1, HCOM)
                    And (Arg2, 0xFF, DAT0)
                    And (ShiftRight (Arg2, 0x08), 0xFF, DAT1)
                    Store (0x4C, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Method (SRDW, 2, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0xFFFF)
                    }

                    Store (0x00, I2CE)
                    Store (0xBF, HSTS)
                    Store (Or (Arg0, 0x01), TXSA)
                    Store (Arg1, HCOM)
                    Store (0x4C, HCON)
                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (Or (ShiftLeft (DAT1, 0x08), DAT0))
                    }

                    Return (0xFFFFFFFF)
                }

                Method (SBLW, 4, Serialized)
                {
                    If (STRT ())
                    {
                        Return (0x00)
                    }

                    Store (Arg3, I2CE)
                    Store (0xBF, HSTS)
                    Store (Arg0, TXSA)
                    Store (Arg1, HCOM)
                    Store (SizeOf (Arg2), DAT0)
                    Store (0x00, Local1)
                    Store (DerefOf (Index (Arg2, 0x00)), HBDR)
                    Store (0x54, HCON)
                    While (LGreater (SizeOf (Arg2), Local1))
                    {
                        Store (0x0FA0, Local0)
                        While (LAnd (LNot (And (HSTS, 0x80)), Local0))
                        {
                            Decrement (Local0)
                            Stall (0x32)
                        }

                        If (LNot (Local0))
                        {
                            KILL ()
                            Return (0x00)
                        }

                        Store (0x80, HSTS)
                        Increment (Local1)
                        If (LGreater (SizeOf (Arg2), Local1))
                        {
                            Store (DerefOf (Index (Arg2, Local1)), HBDR)
                        }
                    }

                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (0x01)
                    }

                    Return (0x00)
                }

                Method (SBLR, 3, Serialized)
                {
                    Name (TBUF, Buffer (0x0100) {})
                    If (STRT ())
                    {
                        Return (0x00)
                    }

                    Store (Arg2, I2CE)
                    Store (0xBF, HSTS)
                    Store (Or (Arg0, 0x01), TXSA)
                    Store (Arg1, HCOM)
                    Store (0x54, HCON)
                    Store (0x0FA0, Local0)
                    While (LAnd (LNot (And (HSTS, 0x80)), Local0))
                    {
                        Decrement (Local0)
                        Stall (0x32)
                    }

                    If (LNot (Local0))
                    {
                        KILL ()
                        Return (0x00)
                    }

                    Store (DAT0, Index (TBUF, 0x00))
                    Store (0x80, HSTS)
                    Store (0x01, Local1)
                    While (LLess (Local1, DerefOf (Index (TBUF, 0x00))))
                    {
                        Store (0x0FA0, Local0)
                        While (LAnd (LNot (And (HSTS, 0x80)), Local0))
                        {
                            Decrement (Local0)
                            Stall (0x32)
                        }

                        If (LNot (Local0))
                        {
                            KILL ()
                            Return (0x00)
                        }

                        Store (HBDR, Index (TBUF, Local1))
                        Store (0x80, HSTS)
                        Increment (Local1)
                    }

                    If (COMP ())
                    {
                        Or (HSTS, 0xFF, HSTS)
                        Return (TBUF)
                    }

                    Return (0x00)
                }

                Method (STRT, 0, Serialized)
                {
                    Store (0xC8, Local0)
                    While (Local0)
                    {
                        If (And (HSTS, 0x40))
                        {
                            Decrement (Local0)
                            Sleep (0x01)
                            If (LEqual (Local0, 0x00))
                            {
                                Return (0x01)
                            }
                        }
                        Else
                        {
                            Store (0x00, Local0)
                        }
                    }

                    Store (0x0FA0, Local0)
                    While (Local0)
                    {
                        If (And (HSTS, 0x01))
                        {
                            Decrement (Local0)
                            Stall (0x32)
                            If (LEqual (Local0, 0x00))
                            {
                                KILL ()
                            }
                        }
                        Else
                        {
                            Return (0x00)
                        }
                    }

                    Return (0x01)
                }

                Method (COMP, 0, Serialized)
                {
                    Store (0x0FA0, Local0)
                    While (Local0)
                    {
                        If (And (HSTS, 0x02))
                        {
                            Return (0x01)
                        }
                        Else
                        {
                            Decrement (Local0)
                            Stall (0x32)
                            If (LEqual (Local0, 0x00))
                            {
                                KILL ()
                            }
                        }
                    }

                    Return (0x00)
                }

                Method (KILL, 0, Serialized)
                {
                    Or (HCON, 0x02, HCON)
                    Or (HSTS, 0xFF, HSTS)
                }
            }
        }
    }
}
```

---

### Post by 67GTA on 2009-05-30
Those are small syntax fixes, and tweaks that the iasl compiler automatically knows how to fix. You can see them if you use ```
iasl -tc -vo path_to_dsdt.dsl
``` They are just done in the background. The Microsoft AML compiler is lazy with errors. The Intel compiler won't let any errors get by wether they are serious or not. You can't improve anything except errors or warnings that the compiler can't fix.

---

### Post by moose2 on 2009-05-30
Thank you very much. I tried it now and it works.

Can I fix this:
```
moose@pc07:~$ dmesg | grep Warning
[    2.396636] ACPI Warning (nspredef-0852): \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer [20080926]
```

---

### Post by 67GTA on 2009-05-30
You can ignore that. It is basically saying that the kernel isn't issuing a BIOS compatible command to your hard drive (ATA). The kernel controls the hard drive re-initialization at boot, so the BIOS is just complaining about nothing. ;)

---

### Post by moose2 on 2009-05-31
I have a special error at the start. The notebook starts, shuts down and starts again: [http://www.youtube.com/watch?v=HqNmHgjNKjQ](http://www.youtube.com/watch?v=HqNmHgjNKjQ)
Perhaps its related to this error-message?

---

### Post by peterwil on 2009-05-31
> **67GTA said:**
> I don't see any fan related tables. Is it controlled by the bios? Look for fan settings there.

There seems to be multiple references to FAN1 in the dsdt. 
I checked on the vista side with a utility (SPEED FAN) which shows temp < 46 C.. On booting Ubuntu the temp is already at 66C and rising steadily. If I have multiple apps ( IDE's , server processes ) running the temp is already 75 C.. Hence my concern and on looking through the fora for a bit came across your posting.  
> /proc/acpi/fan/FAN1/state : *off*  and never seems to be *on *while running Ubuntu. 
I tried inserting the line acpi_osi="Windows 2001 SP2" into making it think that the OS is win as mentioned in one of your threads.. but even that didn't seem to switch the FAN on to cool
the CPU down a bit. Interestingly the menu.lst file didn't even have an entry for acpi_osi="Linux".
I will check the BIOS settings to check if the fan is controlled from there...However one question that comes up 
How does Vista figure that out while Ubuntu is not able.. ? Clearly from reading your posts this would have to be dsdt problem.. since the iasl complier fails to compile the dsdt.dsl..and reports errors.  I am new to assembler , have coded a ton in java and 6 other langs.. but it would take me a week or more to figure this assembler listing and mapping it to the ACPI spec doc.( 700 odd pages ). So any help you can suggest would be greatly appreciated... Cheers...

---

### Post by 67GTA on 2009-05-31
peterwill:

What is under:

cat /proc/acpi/thermal_zone/THRM/cooling_mode

cat /proc/acpi/thermal_zone/THRM/trip_points

cat /proc/acpi/thermal_zone/THRM/polling_frequency

cat /proc/acpi/thermal_zone/THRM/state

cat /proc/acpi/thermal_zone/THRM/temperature

---

### Post by 67GTA on 2009-05-31
> **moose2 said:**
> I have a special error at the start. The notebook starts, shuts down and starts again: [http://www.youtube.com/watch?v=HqNmHgjNKjQ](http://www.youtube.com/watch?v=HqNmHgjNKjQ)
Perhaps its related to this error-message?

According to your dmesg output, the hard drive is booting fine. That is weird. Did this happen before the custom DSDT?

---

### Post by Perpetual on 2009-05-31
The thing that confuses me the most about this is that it wasn't an issue until the 2.6.27 kernel.  Why?  If the DSDT is buggy...why did pre-2.6.27 kernels work fine?

---

### Post by peterwil on 2009-05-31
> **67GTA said:**
> peterwill:

What is under:

cat /proc/acpi/thermal_zone/THRM/cooling_mode

cat /proc/acpi/thermal_zone/THRM/trip_points

cat /proc/acpi/thermal_zone/THRM/polling_frequency

cat /proc/acpi/thermal_zone/THRM/state

cat /proc/acpi/thermal_zone/THRM/temperature

67GTA -- Thanks for your note. Here are the results..

cat /proc/acpi/thermal_zone/THZN$ cat /proc/acpi/thermal_zone/THZN/cooling_mode
0 - Active; 1 - Passive

cat /proc/acpi/thermal_zone/THZN$ cat /proc/acpi/thermal_zone/THZN/trip_points
critical (S5):           105 C

cat /proc/acpi/thermal_zone/THZN$ cat /proc/acpi/thermal_zone/THZN/polling_frequency
<polling disabled>

cat /proc/acpi/thermal_zone/THZN/state
state:                   ok

 cat /proc/acpi/thermal_zone/THZN/temperature
temperature:             64 C
---

Not sure why the polling frequency is set to disabled.. It may possibly mean that the temps are not being read at all and hence the fans don't switch on and as result the temperature keeps rising.. ?

The dsdt has errors on compiling with iasl.. perhaps this section is not being read in by Ubuntu at all due to the errors?...

Cheers..

---

### Post by peterwil on 2009-05-31
> **peterwil said:**
> 67GTA -- Thanks for your note. Here are the results..

cat /proc/acpi/thermal_zone/THZN$ cat /proc/acpi/thermal_zone/THZN/cooling_mode
0 - Active; 1 - Passive

cat /proc/acpi/thermal_zone/THZN$ cat /proc/acpi/thermal_zone/THZN/trip_points
critical (S5):           105 C

cat /proc/acpi/thermal_zone/THZN$ cat /proc/acpi/thermal_zone/THZN/polling_frequency
<polling disabled>

cat /proc/acpi/thermal_zone/THZN/state
state:                   ok

 cat /proc/acpi/thermal_zone/THZN/temperature
temperature:             64 C
---

Not sure why the polling frequency is set to disabled.. It may possibly mean that the temps are not being read at all and hence the fans don't switch on and as result the temperature keeps rising.. ?

The dsdt has errors on compiling with iasl.. perhaps this section is not being read in by Ubuntu at all due to the errors?...

Cheers..

Also here is the compliation output ( error) from the disassembled code

 iasl -tc ./dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20061109 [May 16 2007]
Copyright (C) 2000 - 2006 Intel Corporation
Supports ACPI Specification Revision 3.0a

./dsdt.dsl     1: ACPI
Error    4094 -      ^ syntax error, unexpected PARSEOP_NAMESEG, expecting PARSEOP_DEFINITIONBLOCK

ASL Input:  ./dsdt.dsl - 7578 lines, 268931 bytes, 0 keywords
Compilation complete. 1 Errors, 0 Warnings, 0 Remarks, 0 Optimizations
----

---

### Post by chavanak on 2009-05-31
Can someone help me with my dsdt.dsl? I have 6 warnings which I would like to solve. My laptop is a hp dv6602au. Here is the output of iasl

```
 Intel ACPI Component Architecture
AML Disassembler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

Loading Acpi table from file dsdt.dat
Acpi table [DSDT] successfully installed and loaded
Pass 1 parse of [DSDT]
Pass 2 parse of [DSDT]
Parsing Deferred Opcodes (Methods/Buffers/Packages/Regions)
..................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
Parsing completed
Disassembly completed, written to "dsdt.dsl"
vivek@alwayzgame:~$ iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl   104:     Method (_WAK, 1, NotSerialized)
Warning  1080 -                ^ Reserved method must return a value (_WAK)

dsdt.dsl  3540:                 Method (_Q16, 0, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (_Q16)

dsdt.dsl  7714:                 Method (_HOT, 0, Serialized)
Warning  1087 -                            ^ Not all control paths return a value (_HOT)

dsdt.dsl  7714:                 Method (_HOT, 0, Serialized)
Warning  1080 -                            ^ Reserved method must return a value (_HOT)

dsdt.dsl  7722:                 Method (_CRT, 0, Serialized)
Warning  1087 -                            ^ Not all control paths return a value (_CRT)

dsdt.dsl  7722:                 Method (_CRT, 0, Serialized)
Warning  1080 -                            ^ Reserved method must return a value (_CRT)

ASL Input:  dsdt.dsl - 8135 lines, 276412 bytes, 4173 keywords
AML Output: dsdt.aml - 31936 bytes, 821 named objects, 3352 executable opcodes

Compilation complete. 0 Errors, 6 Warnings, 0 Remarks, 26 Optimizations

```

---

### Post by 67GTA on 2009-05-31
peterwill:

First lets see if you can control your fan before we get dirty. Open a terminal and become root with ```
sudo su
``` Then run this command to see if we can turn it on:

```
echo 0 > /proc/acpi/fan/FAN1/state
```

Then check to see what the state is with ```
cat /proc/acpi/fan/FAN1/state
``` If that shows it on, then I can probably write an init script for you that will switch it on at boot and tell ACPI to poll the BIOS so it knows when to kick it on.

---

### Post by 67GTA on 2009-05-31
chavanak: 

```
Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 29 Optimizations
```

I fixed _WAK error and temp readings. You should be able to hibernate/suspend, and it should run cooler/quieter. Keep the dsdt.aml in a safe place for future use. Follow the rest of the how to and add acpi_osi="Linux" as stated. Post a copy of your dmesg output afterwards.

[ATTACH]115938[/ATTACH]

---

### Post by peterwil on 2009-05-31
> **67GTA said:**
> peterwill:

First lets see if you can control your fan before we get dirty. Open a terminal and become root with ```
sudo su
``` Then run this command to see if we can turn it on:

```
echo 0 > /proc/acpi/fan/FAN1/state
```

Then check to see what the state is with ```
cat /proc/acpi/fan/FAN1/state
``` If that shows it on, then I can probably write an init script for you that will switch it on at boot and tell ACPI to poll the BIOS so it knows when to kick it on.

Thanks!.. The fan switched on alright.. ie state returned ON. However did a quick check on the temperature and it still showed as rising from 66 -- 69 in about 3 mins... Any thoughts on why this is so ?

---

### Post by 67GTA on 2009-05-31
Do you have lm-sensors installed? Install them, and run ```
sudo sensors-detect
``` in a terminal. Hit enter for each question except the last. You want the sensors written to /etc/modules and the default is no. Type in "yes" and hit enter for the last one. Go to Menu>System>Administration>Services and check the box for the sensors. Reboot to activate them and see if the temp is any lower while the fan is on. The fact that the fan can be controlled means the BIOS is not controlling it. There is a bug with ACPI because it is disabled by default. You might want to file a bug on launchpad even if we get it working.

---

### Post by chavanak on 2009-06-01
Hi,
Thanks a lot 67GTA as you mentioned it is much better now!!! I will keep it in a safe place. Thanks once again!!!!
Cheers,
Chav

---

### Post by peterwil on 2009-06-01
> **67GTA said:**
> Do you have lm-sensors installed? Install them, and run ```
sudo sensors-detect
``` in a terminal. Hit enter for each question except the last. You want the sensors written to /etc/modules and the default is no. Type in "yes" and hit enter for the last one. Go to Menu>System>Administration>Services and check the box for the sensors. Reboot to activate them and see if the temp is any lower while the fan is on. The fact that the fan can be controlled means the BIOS is not controlling it. There is a bug with ACPI because it is disabled by default. You might want to file a bug on launchpad even if we get it working.

Thanks 67GTA!.. I installed lm-sensors.. The output showed it was not able to detect the sensors.
-----
Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or [http://www.lm-sensors.org/wiki/FAQ](http://www.lm-sensors.org/wiki/FAQ)
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.
----

On rebooting with the system-Admin-services-hardware monitor(lm-sensors) checked it is still showing rising temp.. 

This looks like a serious issue for me.. As I am concerned that the rising temps would fry the computer.. 

Does this happen with versions of Ubuntu (after Hardy Heron ) as well. ?
I am just about to wipe out this distro and try Red Hat... 
As this is clearly unworkable for sustained development use ...

Thanks again for helping with the understanding of this issue.

Cheers 
Peter

---

### Post by 67GTA on 2009-06-01
peterwill:

While I was researching your problem, I ran across toshset. It is in the repos. It is made just for Toshiba laptops and controls fan/temp and a couple of other things. From what I have seen, Toshibas seem to have a lot of trouble with fans/heat and Linux. You might want to check it out. If that doesn't help, I would suggest trying Opensuse. Their acpi implementation always seemed to be a little better to me.

---

### Post by CylnZ on 2009-06-02
Hi 67GTA, I am still reading :) 
Found some instances of "acpi_osi="Linux" that have syntax of acpi_osi="**[COLOR=Red]![/COLOR]**Linux"

From what I've been reading, adding that bang seems to help in some cases. Do you happen to know why?

Here's a post from Len [EMAIL="Brown@intel.com"][/EMAIL]Brown at Intel mentioning that particular command.

[http://forum.soft32.com/linux/PATCH-22-ACPI-fix-acpi_osi-Linux-ftopict346586.html](http://forum.soft32.com/linux/PATCH-22-ACPI-fix-acpi_osi-Linux-ftopict346586.html)

Thoughts?

---

### Post by peterwil on 2009-06-02
> **67GTA said:**
> peterwill:

While I was researching your problem, I ran across toshset. It is in the repos. It is made just for Toshiba laptops and controls fan/temp and a couple of other things. From what I have seen, Toshibas seem to have a lot of trouble with fans/heat and Linux. You might want to check it out. If that doesn't help, I would suggest trying Opensuse. Their acpi implementation always seemed to be a little better to me.

Are you suggesting that even fixing the DSDT errors won't get the fan to cool the laptop ? I thought if there was an error free DSDT, then it could be complied and at boot time the dsdt supplied ( by the BIOS) could be overridden and hence we could get the ACPI interface working ok( as this controls the fans, thermal zones etc ). So now it appears to be that we have to fix the DSDT , recompile so that the OS could load it at boot time.
Any possibilities of fixing the DSDT src  to recompile without errors ? 

Thanks 
Peter

---

### Post by peterwil on 2009-06-02
> **67GTA said:**
> peterwill:

While I was researching your problem, I ran across toshset. It is in the repos. It is made just for Toshiba laptops and controls fan/temp and a couple of other things. From what I have seen, Toshibas seem to have a lot of trouble with fans/heat and Linux. You might want to check it out. If that doesn't help, I would suggest trying Opensuse. Their acpi implementation always seemed to be a little better to me.

I downloaded toshset and ran make but it failed to produce an executable( 
not a 64bit version ). But came across this post
[http://ubuntuforums.org/showthread.php?t=1043248](http://ubuntuforums.org/showthread.php?t=1043248)
where acpitool is mentioned. So downloaded and installed that tool.
and interestingly this tool is supposed to support Toshiba laptops for fan control ( Forced mode )
ie , acpitool -F 1 ( 1 is the on state )
but I get the following response. 
     Forcing the fan of/off is only supported on Toshiba laptops. 
     No Toshiba ACPI extensions were found. 

Somehow it thinks I am not running a Toshiba Laptop.. Possibly due to a missing Toshiba Extensions package ?

Cheers
Peter

---

### Post by 67GTA on 2009-06-02
> **CylnZ said:**
> Hi 67GTA, I am still reading :) 
Found some instances of "acpi_osi="Linux" that have syntax of acpi_osi="**[COLOR=Red]![/COLOR]**Linux"

From what I've been reading, adding that bang seems to help in some cases. Do you happen to know why?

Here's a post from Len Brown at Intel mentioning that particular command.

[http://forum.soft32.com/linux/PATCH-22-ACPI-fix-acpi_osi-Linux-ftopict346586.html](http://forum.soft32.com/linux/PATCH-22-ACPI-fix-acpi_osi-Linux-ftopict346586.html)

Thoughts?

Passing the "!" argument actually disables osi detection. I'm not sure why that was ever suggested. It may have had some functionality in earlier kernels. When "!Linux" is used ```
ACPI: BIOS _OSI(Linux) query ignored via cmdline
``` When "Linux" is used  ```
ACPI: BIOS _OSI(Linux) query honored via cmdline
```

---

### Post by peterwil on 2009-06-02
> **peterwil said:**
> I downloaded toshset and ran make but it failed to produce an executable( 
not a 64bit version ). But came across this post
[http://ubuntuforums.org/showthread.php?t=1043248](http://ubuntuforums.org/showthread.php?t=1043248)
where acpitool is mentioned. So downloaded and installed that tool.
and interestingly this tool is supposed to support Toshiba laptops for fan control ( Forced mode )
ie , acpitool -F 1 ( 1 is the on state )
but I get the following response. 
     Forcing the fan of/off is only supported on Toshiba laptops. 
     No Toshiba ACPI extensions were found. 

Somehow it thinks I am not running a Toshiba Laptop.. Possibly due to a missing Toshiba Extensions package ?

Cheers
Peter


I have opened bug report on launchpad the id is #382806

---

### Post by 67GTA on 2009-06-02
peterwill:

You can't get the DSDT source. It is hard coded in the BIOS. The only way that would work is if your BIOS vendor made an error free DSDT and packaged it in a BIOS update. We are simply grabbing a copy of it from the BIOS and trying to patch it. Then we tell the OS to use it instead of the original. After a lot of reading, I found Toshiba laptops have a lot of trouble with Linux. That's why I suggested trying toshset. It doesn't seem the fan issue is linked to your DSDT errors, and it is disabled by default. I was starting to wonder if we were chasing our tails in your case. You can get a 64bit source package of toshset here: [http://schwieters.org/toshset/toshset64.gz](http://schwieters.org/toshset/toshset64.gz)

---

### Post by peterwil on 2009-06-02
> **67GTA said:**
> peterwill:

You can't get the DSDT source. It is hard coded in the BIOS. The only way that would work is if your BIOS vendor made an error free DSDT and packaged it in a BIOS update. We are simply grabbing a copy of it from the BIOS and trying to patch it. Then we tell the OS to use it instead of the original. After a lot of reading, I found Toshiba laptops have a lot of trouble with Linux. That's why I suggested trying toshset. It doesn't seem the fan issue is linked to your DSDT errors, and it is disabled by default. I was starting to wonder if we were chasing our tails in your case. You can get a 64bit source package of toshset here: [http://schwieters.org/toshset/toshset64.gz](http://schwieters.org/toshset/toshset64.gz)
]
Yes I think I understood as much. My BIOS vendor is Insyde..v 1.2. They have a newer bios version which I read about on Toshiba's site. I was hoping that BIOS version would have a correct dsdt as
per Intel's iasl compiler.  Also from your note you mention that the DSDT errors are unrelated to the fan as it is disabled by default( which is possibly a kernel bug.. maybe ? ). Ok I have included a ref. to the link above where instead of toshset I used acpitool ( a tool specifically written for Toshibas to begin with. ) This tool has a specific option to switch the fan on ( acpitool -F 1 .. option only for toshibas )but it still doesn't do so . Hence perhaps it is a bug in the implementation of the ACPI interface in Hardy .. On searching on launchpad I do so similar bugs being filed and tracked.. I have filed a bug report.. awaiting response and advise from the team. 

I will also try ( configure, make, install ) on the 64bit toshset to see if it can switch the fan on... 

Cheers
Peter
Thanks and best regards..

---

### Post by CylnZ on 2009-06-02
Hi Peter, have you tried:

sudo apt-get install toshutils ?

Supposedly it has toshiba acpi fan controls. I found it in a round about way from this:
[http://www.linuxquestions.org/hcl/showproduct.php/product/4080/sl/d](http://www.linuxquestions.org/hcl/showproduct.php/product/4080/sl/d)

I was reading the acpi section and found toshutils by  typing "fan" into a terminal. Toshutils doesnt help me a lick since I have a pm965 but hopefully it'll help you.

---

### Post by CylnZ on 2009-06-02
@ 67GTA,

I get the same "ignored" with bang in place. Oh Well, you gotta try them all to find one diamond.

You know, sadly enough, notebook forums all over the net whether linux, windows or mac have intel pm965 overheating. Theres an entire linux project that has apparently died for 965 because Intel wont release the danged code for it. It,s almost enough to make a guy buy a tiny rheostat and some 20 gauge wire.

---

### Post by peterwil on 2009-06-02
> **CylnZ said:**
> Hi Peter, have you tried:

sudo apt-get install toshutils ?

Supposedly it has toshiba acpi fan controls. I found it in a round about way from this:
[http://www.linuxquestions.org/hcl/showproduct.php/product/4080/sl/d](http://www.linuxquestions.org/hcl/showproduct.php/product/4080/sl/d)

I was reading the acpi section and found toshutils by  typing "fan" into a terminal. Toshutils doesnt help me a lick since I have a pm965 but hopefully it'll help you.

Hi CylnZ,
Thanks for your note.. Is toshutils a 64bit exec..?
My machine is Toshiba Sat.. L305D-S5881 ( AMD Turion X2 Dual core RM 70) running in 64bit mode on Ubuntu 8.0.4...

Cheers
Peter

---

### Post by CylnZ on 2009-06-02
[http://linuxappfinder.com/package/toshset](http://linuxappfinder.com/package/toshset)

I'd sure give it a try. Ubuntu-Intrepid-64 bit...Hard to argue with that one. Apparently toshset/toshutils are related, one gui one cmd line.

---

### Post by PatrickVogeli on 2009-06-02
Hi there! I've come across this and this way I've realized my DSDT has 2 warnings. Could you have a look into it please? I have some problems with ACPI and so, maybe this could fix them?

Do you know what those 2 warnings are?

I attach all dsdt files, as well as dmesg output file.

Thank you so much!!

---

### Post by 67GTA on 2009-06-03
moz_21:

[ATTACH]116326[/ATTACH]

---

### Post by 67GTA on 2009-06-03
> **PatrickVogeli said:**
> Hi there! I've come across this and this way I've realized my DSDT has 2 warnings. Could you have a look into it please? I have some problems with ACPI and so, maybe this could fix them?

Do you know what those 2 warnings are?

I attach all dsdt files, as well as dmesg output file.

Thank you so much!!

I fixed the warnings. I had to put a return value for the PSR method. 

[ATTACH]116328[/ATTACH]

---

### Post by PatrickVogeli on 2009-06-04
thanks a lot. Later today I'll try your DSDT and report back.

Do you know if that should make any effect to how stuff works? Or was is just a simple and no harmful warning?

---

### Post by 67GTA on 2009-06-04
> **PatrickVogeli said:**
> thanks a lot. Later today I'll try your DSDT and report back.

Do you know if that should make any effect to how stuff works? Or was is just a simple and no harmful warning?

(_PSR) has to do with your power source. I would check to see if the battery shows charge/discharge correctly. The method already had the values 0x00(off) and 0x01(on), but needed a null value in case no value was returned. You really shouldn't notice any difference.

---

### Post by peterwil on 2009-06-04
> **CylnZ said:**
> [http://linuxappfinder.com/package/toshset](http://linuxappfinder.com/package/toshset)

I'd sure give it a try. Ubuntu-Intrepid-64 bit...Hard to argue with that one. Apparently toshset/toshutils are related, one gui one cmd line.

Ok my problem seems to be resolved.. :-)

The above post and 67GTA's previous post mentioning that Toshiba's seem to have trouble with linux got me thinking... whether it was simply related to a bad (ie buggy ) acpi implementation in Hardy.. Toshset wouldn't run complaining that it was an unsupported Kernel extension...

So this morning I decide to can the entire distro and downloaded 9.0.4 (jaunty jackaloupe) and had it installed in about an hour or so.
The install went pretty smoothly and the temps were distinctly lower.
So the laptop doesn't seem to be overheating as of now ie 6 hours later..

Here is the output from acpi..

peter@neutrino:acpi -V
     Battery 0: Charging, 35%, 00:57:48 until charged
     Battery 0: design capacity 4000 mAh, last full capacity 4254 mAh = 100%
  AC Adapter 0: off-line
     Thermal 0: ok, 49.0 degrees C
     Cooling 0: LCD 3 of 7
     Cooling 1: Processor 0 of 3
     Cooling 2: Processor 0 of 10
     Cooling 3: Fan 1 of 1
peter@neutrino:~$ acpi -t
     Battery 0: Charging, 36%, 00:56:54 until charged
     Thermal 0: ok, 49.0 degrees C

  
With Hardy on this laptop the temps start at about 60 C and keeps rising to 75 or so.. I stop the machine at that point.. No point frying eggs with the laptop..:-).

Thanks for all the understanding regarding DSDT's and ACPI ( both are totally new areas for me... )

_________
Toshiba L305D S5881 - AMD Turion RM-70  running 64bit Jaunty..

Cheers

Peter William

---

### Post by jijin on 2009-06-05
67GTA, you look like a god send to amny people so thanks in advance :D

Anyway, I have an Acer Aspire 5520 and I'm having heating issues.. I have fixed as much as I can with the dsdt file, but I'm right at the edge of what I know about linux here and there are still more warnings that I want gone when I try to compile.

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/jijin/dsdt.dsl   825:             Method (Z004, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (Z004)

/home/jijin/dsdt.dsl  1498:             Method (_WED, 1, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_WED)

/home/jijin/dsdt.dsl  1498:             Method (_WED, 1, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_WED)

/home/jijin/dsdt.dsl  1504:                         Return (Z004 ())
Warning  1092 -    Called method may not always return a value ^ 

/home/jijin/dsdt.dsl  1542:             Method (WMBD, 3, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (WMBD)

/home/jijin/dsdt.dsl  2215:                 Method (WMNV, 3, NotSerialized)
Warning  1087 -   Not all control paths return a value ^  (WMNV)

ASL Input:  /home/jijin/dsdt.dsl - 6854 lines, 235103 bytes, 2960 keywords
AML Output: /home/jijin/dsdt.aml - 24159 bytes, 868 named objects, 2092 executable opcodes

Compilation complete. 0 Errors, 6 Warnings, 0 Remarks, 711 Optimizations

```

And attached is the file itself, let me know if you need anymore info from me thanks, you really are awesome for helping with this issue.

As an aside, I do NOT have anything listed in proc/acpi/fan/ folder. I did the thing you had told peterwill to do with the command:

```
sudo sensors-detect
```

Output of sensors:

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +66.0°C  (crit = +100.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +63.0°C                                    
Core0 Temp:  +64.0°C                                    
Core1 Temp:  +64.0°C                                    
Core1 Temp:  +63.0°C   
```

It gets really hot and the fan doesn't kick on as fast (or as loud) as it does in windows playing the same game. I'm looking at 85°C+ temps during gaming and I would like the fan to kick on sooner and be able to spin faster as it does in windows.

Thanks again :)

---

### Post by MakotoTheKnight on 2009-06-05
Hey there!  I was recently fascinated by this post about two weeks ago, when I wanted to figure out the issues behind a misplaced IRQ, and why my laptop wasn't idling cool enough (54C idle is NOT cool, man).

I did some digging (after reading your and everyone else's post), and I managed to find some documentation for ASL here:  [http://acpi.info/spec.htm](http://acpi.info/spec.htm) .  Be forewarned - those without any programming experience or assembly experience will be lost in some places.

I've learned a handful from debugging the DSDT file, including how it controls certain resources (hence my wireless card dying sometimes).  So far, with your guide, I was able to knock my laptop's idle down to about 41-47C w/o AC and about 36-43C w/AC.

I hope that the documentation (I'd use the PDF) will help you and everyone else looking to disect their DSDT, and hopefully it will ultimately lead to an improved experience with fan control, thermals, and hibernation.

---

### Post by jijin on 2009-06-06
Bump for 67GTA or another person good with DSDT files

---

### Post by Schugy on 2009-06-07
I have a Raon Digital Everun Note D60H with a factory underclocked Turion X2-TL56 @ 1200MHz. I have a DSDT bug (error 4095) and powernow-k8 doesn't work (see dmesg).
Thanks a lot for a fixed file.

Stupid Microsoft Compiler. If we don't use any of their crappy OSes they just f*** up the BIOS.
 
 * Original Table Header:
 *     Signature        "DSDT"
 *     Length           0x0000621D (25117)
 *     Revision         0x01 **** ACPI 1.0, no 64-bit math support
 *     Checksum         0x14
 *     OEM ID           "ATI"
 *     OEM Table ID     "SB600"
 *     OEM Revision     0x06040000 (100925440)
 *     Compiler ID      "MSFT"
 *     Compiler Version 0x03000000 (50331648)
 */
DefinitionBlock ("dsdt-everun-note.aml", "DSDT", 1, "ATI", "SB600", 0x06040000)

---

### Post by ubunxpm on 2009-06-07
Hello,

Seems like some of you have really screwed up dsdt s . Mine is not that bad, just 1 warning. Having said that I haven`t got a clue about how to fix it. I googled, read some other threads and found other people with similar problems but no solution.

Some help would be greatly appreciated.

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/tempered/dsdt.dsl 12682:             Method (_Q15, 0, NotSerialized)
Warning  1087 -  Not all control paths return a value ^  (_Q15)

ASL Input:  /home/tempered/dsdt.dsl - 14751 lines, 489458 bytes, 6269 keywords
AML Output: /home/tempered/dsdt.aml - 52499 bytes, 1275 named objects, 4994 executable opcodes

Compilation complete. 0 Errors, 1 Warnings, 0 Remarks, 2938 Optimizations

```

dmesg|grep Warning
```
[    0.000000] ACPI Warning (tbfadt-0460): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20080926]

```

---

### Post by 67GTA on 2009-06-08
Sorry, I've been busy with work. I haven't checked my email for several days. 

jijin: I have dealt with several Acer Aspire's and can not effect the temp through the BIOS. I have advised everyone to file bugs against acpi, pm-utils, or maybe kernel (not sure) for their laptop model. I have fixed the errors for yours. 

[ATTACH]116904[/ATTACH] 


Schugy: I didn't see any errors pertaining to your problems. Hopefully the Intel compiler automatically fixed them. It made around 1400 optimizations by it's self. If not, we can investigate.

[ATTACH]116905[/ATTACH]


ubunxpm: Yours was hiding. I fixed the 1 error, and 8 more showed up(LOL). I fixed them, and the Intel compiler still made about 2500 optimizations. 

[ATTACH]116906[/ATTACH]


Be sure to add the acpi_osi="Linux" description per the how to. Send me your dmesg outputs afterwards, and I will check to see what is happening.

---

### Post by ubunxpm on 2009-06-08
Hat`s off to you 67GTA,

I don`t know what those errors you fixed were but the new dsdt made a big difference. My hdd head used to hit the far end stopper every now end then and it sounded like a ball bearing bouncing on a hard surface. No more of that annoyance. Now the kernel and ubuntu actually works well with my hardware. `Cause it used to work around it`s quirks due to a buggy dsdt.

You should have "The Dsdt Debugger" written under your nick.
Applause to 67GTA =D>

---

### Post by jijin on 2009-06-08
> **67gta said:**
> sorry, i've been busy with work. I haven't checked my email for several days. 

Jijin: I have dealt with several acer aspire's and can not effect the temp through the bios. I have advised everyone to file bugs against acpi, pm-utils, or maybe kernel (not sure) for their laptop model. I have fixed the errors for yours. 


thank you :d

---

### Post by peterwil on 2009-06-10
> **MakotoTheKnight said:**
> Hey there!  I was recently fascinated by this post about two weeks ago, when I wanted to figure out the issues behind a misplaced IRQ, and why my laptop wasn't idling cool enough (54C idle is NOT cool, man).

I did some digging (after reading your and everyone else's post), and I managed to find some documentation for ASL here:  [http://acpi.info/spec.htm](http://acpi.info/spec.htm) .  Be forewarned - those without any programming experience or assembly experience will be lost in some places.

I've learned a handful from debugging the DSDT file, including how it controls certain resources (hence my wireless card dying sometimes).  So far, with your guide, I was able to knock my laptop's idle down to about 41-47C w/o AC and about 36-43C w/AC.

I hope that the documentation (I'd use the PDF) will help you and everyone else looking to disect their DSDT, and hopefully it will ultimately lead to an improved experience with fan control, thermals, and hibernation.

Hello MakototheKnight,
Thanks for your note.. I had an overheating problem with Hardy on my Toshiba. Temps would start at 59 C and rise to 75 in about 10 mins.It 
seems to be doing a lot better after Jaunty ..don't see it go beyond 55C.
But still 55C seems a bit high considering your post and I would be very interested in knocking it down to your temps 36-43 A/C ... Could you please post your dsdt.dsl before and after your changes.? I have seen the spec -it is  a bit daunting ( 673 pages ) but maybe possible to map the assembler code at least for FAN , default start status and thermal zone settings. 
After reinstalling I went through 67GTA's procedure to check the compilation of the disassembled DSDT and it shows the same error as before. So it might be worth while trying to get that error out of the way
to see if it helps any...

Thanks in advance..

Peter

---

### Post by chavanak on 2009-06-10
> **67GTA said:**
> chavanak: 

```
Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 29 Optimizations
```I fixed _WAK error and temp readings. You should be able to hibernate/suspend, and it should run cooler/quieter. Keep the dsdt.aml in a safe place for future use. Follow the rest of the how to and add acpi_osi="Linux" as stated. Post a copy of your dmesg output afterwards.

[ATTACH]115938[/ATTACH]
Hi,
Here is my dmesg copy, can you please let me know if everything is going on well with my system? 
Cheers
Chav
P.S: Was on vacation, so took time to reply ;)

---

### Post by 67GTA on 2009-06-10
chavanak: Looks fine. No errors :D

---

### Post by chavanak on 2009-06-10
> **67GTA said:**
> chavanak: Looks fine. No errors :D
Bingo! Thanks a lot 67GTA, my laptop is back to normal. Btw one question how about mac's running ubuntu? Does the DSDT problem apply to mac also?

---

### Post by 67GTA on 2009-06-10
Yes, this affects Mac also. For that matter, it affects any OS other than Windows. You can use this how to for Ubuntu running on a Mac. There is also someone who made a DSDT patcher program for Mac OS's because of the same problem. I remember seeing it on a Mac forum somewhere.

---

### Post by chavanak on 2009-06-10
> **67GTA said:**
> Yes, this affects Mac also. For that matter, it affects any OS other than Windows. You can use this how to for Ubuntu running on a Mac. There is also someone who made a DSDT patcher program for Mac OS's because of the same problem. I remember seeing it on a Mac forum somewhere.

Hmmm how much I hate winnie :( I will be purchasing a mac tomorrow so just though of clarifying it with you, the DSDT Master!!!!!

---

### Post by Trebaruna on 2009-06-11
@67GTA:
Like peterwil I've got a Toshiba L305D-S5881. Today I found out something somewhere is quite buggy: I tried to compile a vanilla kernel, but during the process the system decided it was getting too hot and turned off.

DSDT has one warning, pertaining to an AND operation that doesn't store its result. It's the same as the ACPI reference implementation, which on page 206 says this in sample code:

```
// Only allow native hot plug control if OS supports:
// * ASPM
// * Clock PM
// * MSI/MSI-X
If(LNotEqual(And(SUPP, 0x16), 0x16))
{
    And(CTRL,0x1E) // Mask bit 0 (and undefined bits)
}

```Is it me, or does that masking not actually mask anything, because CTRL isn't being updated?
Would this change anything?

Also, it seems that the rather dramatic shut off wasn't really due to temperatures reaching 105C: the laptop felt pretty warm, but not nearly that hot. Do you (or anyone) know of anything that could alleviate this problem? I trust the preinstalled Windows doesn't have this problem, but I've never used it long enough to find out.

Lastly: I tried using toshset, but it complains of missing Toshiba functionality in the kernel. Enabling the module toshiba_acpi fails with the following message:

"FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.28-11-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device"

Hope I didn't veer too much off topic...

---

### Post by MakotoTheKnight on 2009-06-11
> **peterwil said:**
> Hello MakototheKnight,
Thanks for your note.. I had an overheating problem with Hardy on my Toshiba. Temps would start at 59 C and rise to 75 in about 10 mins.It 
seems to be doing a lot better after Jaunty ..don't see it go beyond 55C.
But still 55C seems a bit high considering your post and I would be very interested in knocking it down to your temps 36-43 A/C ... Could you please post your dsdt.dsl before and after your changes.? I have seen the spec -it is  a bit daunting ( 673 pages ) but maybe possible to map the assembler code at least for FAN , default start status and thermal zone settings. 
After reinstalling I went through 67GTA's procedure to check the compilation of the disassembled DSDT and it shows the same error as before. So it might be worth while trying to get that error out of the way
to see if it helps any...

Thanks in advance..


Peter

Well...I don't know if mine would help (I'm guessing that mine was a special case), but I can attach it here.  I'm still tinkering with it, looking and making sure that the IRQs get set properly.

I do NOT want you to use this for your own DSDT file since our two machines are different.  You can look at this to simply gather an understanding though, which is absolutely fine.  :D

---

### Post by peterwil on 2009-06-12
> **Trebaruna said:**
> @67GTA:
Like peterwil I've got a Toshiba L305D-S5881. Today I found out something somewhere is quite buggy: I tried to compile a vanilla kernel, but during the process the system decided it was getting too hot and turned off.

DSDT has one warning, pertaining to an AND operation that doesn't store its result. It's the same as the ACPI reference implementation, which on page 206 says this in sample code:

```
// Only allow native hot plug control if OS supports:
// * ASPM
// * Clock PM
// * MSI/MSI-X
If(LNotEqual(And(SUPP, 0x16), 0x16))
{
    And(CTRL,0x1E) // Mask bit 0 (and undefined bits)
}

```Is it me, or does that masking not actually mask anything, because CTRL isn't being updated?
Would this change anything?

Also, it seems that the rather dramatic shut off wasn't really due to temperatures reaching 105C: the laptop felt pretty warm, but not nearly that hot. Do you (or anyone) know of anything that could alleviate this problem? I trust the preinstalled Windows doesn't have this problem, but I've never used it long enough to find out.

Lastly: I tried using toshset, but it complains of missing Toshiba functionality in the kernel. Enabling the module toshiba_acpi fails with the following message:

"FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.28-11-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device"

Hope I didn't veer too much off topic...

Trebaruna,
Glad to know you have the same machine (Toshiba L305D-S5881) with Ubuntu Jaunty. My DSDT has a very similar warning on compilation with iasl..There are no errors.. Previously 67GTA concluded that getting rid of that warning may not help much with
fan overheating.. The good thing for me is that on jaunty so far
I haven't seen it go much higher than 55C unlike Hardy where it would jump to 75C within minutes.. Having said that I don't think my problem is fully resolved since the dmesg output does not seem to indicate 
i) The fan default state to be ON 
ii) Thermal zone temp. settings to be lower than what I have seen in this thread from the output of others where 67GTA has fixed the dsdt. Most of the postings have the AML binaries. It might be more useful to have the before and after DSDT's to get a deeper understanding. Assembler code is not my expertise :-).
One thing that comes to mind right away is my BIOS is Insyde v1.2. I think there is an update to this v1.5. Have you tried this update yet?

Comparing the dmesg output in hardy and jaunty seems like they are very similar. There is the usual line about acpi_os (linux) query ignored which seems to suggest that the linux tables are not being read right. Haven't tried sticking this as a boot option in Jaunty to see if it goes away.

On filing a bug in Launchpad I got a response from the kernel team that "Toshiba extensions are not enabled by default and you would have to create a custom distribution..." Also I came across numerous posts complaining of overheating laptops in Jaunty. It doesn't seem to be only Toshiba's.. 

I have a good mind to try Fedora 11 on the remaining free space partition on my laptop to see how it behaves..But that is for another day... ( Factory installed Vista takes up 2 ! )..

If you do end up resolving this completely pl. post as I am very interested in this as well.

Thanks
Peter

---

### Post by peterwil on 2009-06-12
> **MakotoTheKnight said:**
> Well...I don't know if mine would help (I'm guessing that mine was a special case), but I can attach it here.  I'm still tinkering with it, looking and making sure that the IRQs get set properly.

I do NOT want you to use this for your own DSDT file since our two machines are different.  You can look at this to simply gather an understanding though, which is absolutely fine.  :D

Thanks Makoto.. I won't use your DSDT ( they are machine specific :-) ) .. But will get some pointers from  looking at similarities if there are any..I am particularly interested in the thermal zone settings .. which seem to have brought your temps down by 10C....

---

### Post by kahukiloia on 2009-06-13
67GTA,

First of all, thanks for the very informative howto. I have followed your instructions and got the output file without a hitch. The hitch popped up a when I got to this:

Maximum error count (200) exceeded
ASL Input:  /home/kahu/dsdt.dsl - 7375 lines, 254663 bytes, 3490 keywords
Compilation complete. 201 Errors, 0 Warnings, 0 Remarks, 570 Optimizations

Maximum error count (200) exceeded
Segmentation fault

I am slightly over my head with this and stuck. I hate to do this to you or anyone, but..... If you could give me some idea how to proceed with making this file usable, I would be very grateful. I am on newest version of Linux-Mint (Gloria - 7) and since I have upgraded from Elissa, I have been experiencing issues with booting up (have to hold any key), and sleep (mainly waking up), additionally, it would seem that my fan is on an unauthorized overtime. Any help would be greatly appreciated.

---

### Post by 67GTA on 2009-06-13
kahukiloia:

You now have zero errors. I fixed errors for suspend/hibernate, so with the nvidia drivers installed, you should be able to wake properly. The hanging at boot should stop. I also fixed errors with the temp readings. It should run cooler/quieter. Follow the rest of the how to with the dsdt.aml file. Be sure to add the acpi_osi="Linux" line to /boot/grub/menu.lst. It is asking for it in your dmesg output. After a reboot, send me your dmesg output again.

[ATTACH]117527[/ATTACH]

---

### Post by Trebaruna on 2009-06-13
I've just checked my fiancee's laptop. Her machine's DSDT is completely screwed up, it makes iasl segfault! (though it seems that's the default at > 200 errors).
Most (all?) of the errors seem to be "object does not exist" though, so I've a feeling there's a pretty simple fix. Would anyone know what to do with this file? (see attachment).

Also, gta, did you get a chance to look at my question about the AND operation not storing its results? Is it significant at all, you think?

---

### Post by 67GTA on 2009-06-13
Trebaruna: 

I changed all instances of (^CPU0) to (\CPU0), and there are zero errors. Sorry, I missed your question. Can you post the error message?

[ATTACH]117530[/ATTACH]

---

### Post by Trebaruna on 2009-06-13
> **67GTA said:**
> 
I changed all instances of (^CPU0) to (\CPU0), and there are zero errors.

Thanks! I guess that means there's nothing wrong with it (syntactically anyway)?

> **67GTA said:**
> 
Sorry, I missed your question. Can you post the error message?

It's a warning, actually:
```

dsdt.dsl  2783:                         And (CTRL, 0x1E)
Warning  1105 -                                 ^ Result is not used, operator has no effect

```
The ACPI spec mentions exactly this piece of code on page 186, claiming it is to mask bit 0. Indeed, that's what this statement *would* do, if it stored the result back into CTRL. As it stands, though, only the AND is taking place, without the storing. Is the spec (and by extension this piece of code, which is taken directly from the reference) wrong?

---

### Post by 67GTA on 2009-06-13
You can try adding CRTL back into the method to shut the error up, but it won't affect your system in any way since the control method isn't used. Try this:

```
And (CTRL, 0x1E, CTRL)
```

---

### Post by peterwil on 2009-06-13
> **Trebaruna said:**
> Thanks! I guess that means there's nothing wrong with it (syntactically anyway)?


It's a warning, actually:
```

dsdt.dsl  2783:                         And (CTRL, 0x1E)
Warning  1105 -                                 ^ Result is not used, operator has no effect

```
The ACPI spec mentions exactly this piece of code on page 186, claiming it is to mask bit 0. Indeed, that's what this statement *would* do, if it stored the result back into CTRL. As it stands, though, only the AND is taking place, without the storing. Is the spec (and by extension this piece of code, which is taken directly from the reference) wrong?
Mine has exactly the same warning...
```

peter@neutrino:~/pw_acpi_issues/pw_modified$ iasl -tc ./dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

./dsdt.dsl  2803:                         And (CTRL, 0x1E)
Warning  1105 -                                   ^ Result is not used, operator has no effect

ASL Input:  ./dsdt.dsl - 7962 lines, 277321 bytes, 3515 keywords
AML Output: ./dsdt.aml - 30381 bytes, 838 named objects, 2677 executable opcodes

Compilation complete. 0 Errors, 1 Warnings, 0 Remarks, 18 Optimizations

```
--- No errors.. 
I haven't seen it shut down.. But today under slightly heavy processing..
(portal + servers ) I saw the temps spike to 75C and then drop down back again to around 56C..

---

### Post by kahukiloia on 2009-06-14
67GTA,

You are amazing, works just as advertised. Quiet, fast, does not hang up on boot while on the batteries; only thing I did not have a chance to fully test is the waking up from suspend, however, quick test already worked really well. 

Thank you very much for your help, I was really stuck. Attached is the post update dmesg output. Once again, thank you.

kahukiloia

---

### Post by ceejay on 2009-06-16
OK, here comes another one looking for help!! Not having found this thread, I started my own at [http://ubuntuforums.org/showthread.php?t=1184364](http://ubuntuforums.org/showthread.php?t=1184364) and have followed a few red herrings. Basically my Intel DG965WH-based system has been running very hot since I upgraded from 8.04 to 9.04. I find that the fans are not picking up speed even when it gets hot. I am monitoring CPU and disc temps with sensor-applet.

/proc/acpi/fans and .../thermal_zone are both empty.

acpi -V returns just

```
     Cooling 0: Processor 0 of 10
     Cooling 1: Processor 0 of 10

```

I've looked at the how-to at the beginning of this thread and like many others am petrified at what I see! But so far I have followed it as far as installing the iasl compiler and running it. I get just one warning:

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/xxx/dsdt.dsl  2187:                     Acquire (MUT0, 0x0FFF)
Warning  1104 -                  Possible operator timeout is ignored ^ 

ASL Input:  /home/xxx/dsdt.dsl - 5186 lines, 178431 bytes, 1615 keywords
AML Output: /home/xxx/dsdt.aml - 15771 bytes, 546 named objects, 1069 executable opcodes

Compilation complete. 0 Errors, 1 Warnings, 0 Remarks, 597 Optimizations

```

which doesn't sound serious in itself, but I guess there may be other incorrect things in here that aren't errors.

In the hope that someone might be able to help I'll attach a copy of the dsdt.dsl file ....

Any pointers, clues or other assistance much appreciated!

TIA
Ceejay

---

### Post by 67GTA on 2009-06-16
ceejay:

I fixed the warning, and 597 optimizations were made. I didn't see any errors in the temp sections, but as I have seen several times so far, fixes in the CPU area often automatically fixes temp problems. The iasl compiler made several optimizations to your CPU area. Hopefully we inadvertantely fixed the fan/temp problem. Follow the rest of my how to, and be sure to add the acpi_osi="Linux" definition.

EDIT: I forgot the file;) [ATTACH]117860[/ATTACH]

---

### Post by ceejay on 2009-06-16
> **67GTA said:**
> ceejay:

I fixed the warning, and 597 optimizations were made. I didn't see any errors in the temp sections, but as I have seen several times so far, fixes in the CPU area often automatically fixes temp problems. The iasl compiler made several optimizations to your CPU area. Hopefully we inadvertantely fixed the fan/temp problem. Follow the rest of my how to, and be sure to add the acpi_osi="Linux" definition.



Thanks! I've tried that and not much has changed, except that acpi -V now reports "... Processor 0 of 3" instead of "0 of 10" (which I suppose at least demonstrates that the modified file has been read!).

The only thing I'm not sure about is exactly what to do with "acpi-osi="Linux" ... add it to /boot/grub/menu.lst where exactly? On the end of the "kernel ..." line?

The sections in this file look something like
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f88d4134-8382-438a-8ce6-915c301fc8e2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
```

Thanks again
Ceejay

---

### Post by 67GTA on 2009-06-16
It needs to look like this: 

```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=f88d4134-8382-438a-8ce6-915c301fc8e2 ro acpi_osi="Linux" quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
```
This might actually be a kernel bug. I googled your mobo, and came up with your other thread(LOL). I would file a bug on launchpad if you haven't already.

---

### Post by ubunxpm on 2009-06-16
Hello 67GTA,

Thank you for the new dsdt. It`s working much better than the old one. I`m about to merge it into my new kernel. But I`m curious about the 1 error I have. a short clarification would be great.
Thanks

> Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/tempered/dsdt.dsl     1: [*** iASL: Read error on source code temp file /home/tempered/dsdt.src ***]
Error    4095 -               ^ syntax error, unexpected $end, expecting PARSEOP_DEFINITIONBLOCK

ASL Input:  /home/tempered/dsdt.dsl - 2 lines, 0 bytes, 0 keywords
Compilation complete. 1 Errors, 0 Warnings, 0 Remarks, 0 Optimizations


---

### Post by 67GTA on 2009-06-16
The dsdt you posted is corrupt. It won't open. From the error, it sounds like the definition block is wrong. Look at the line around #20 that starts with "Definitionblock". Make sure the line starts with "dsdt.aml" and not "/home/username/..../dsdt.aml".

---

### Post by ceejay on 2009-06-16
> **67GTA said:**
> 
This might actually be a kernel bug. I googled your mobo, and came up with your other thread(LOL). I would file a bug on launchpad if you haven't already.

Many thanks for the help - I guess I'm not much further forward at the moment, although I have certainly learned something!

I may file a bug but tbh I need to get a usable system and I'm not sure how to do that without doing something drastic.  It certainly feels like something is not working properly here...

Thanks again

Ceejay

---

### Post by ceejay on 2009-06-17
> **ceejay said:**
> 
I may file a bug but tbh I need to get a usable system and I'm not sure how to do that without doing something drastic.  It certainly feels like something is not working properly here...


Somebody beat me to it!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264290](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/264290)

Reverting to a Hardy kernel (but still running Jaunty otherwise) drops the reported temperature by about 15C. The bug report suggests that the temp isn't really higher: there seems to be some debate about whether the old or the new way is the more accurate.

Thanks for the help anyway!

---

### Post by tedrampart on 2009-06-19
Thanks for this guide,  I think it can help me out as well on my dell latitude D620. 

I received 1 error, 9 warnings, and 7 remarks.  

this seems a bit out of my realm.  Here's my dsdt.dsl file, I really hope its not too much for you to look at it.  Thanks either way!

ted

---

### Post by 67GTA on 2009-06-20
tedrampart:


Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 675 Optimizations

[ATTACH]118386[/ATTACH]

---

### Post by tedrampart on 2009-06-20
Thanks a lot.

what did these errors fix?  anything I should notice?

---

### Post by Hated On Mostly on 2009-06-21
Hi 67GTA,

Can you work your magic on mine?

Thanks

7 Errors, 9 Warnings, 1 Remarks, 831 Optimizations

For a Dell D830

---

### Post by 67GTA on 2009-06-21
> **tedrampart said:**
> Thanks a lot.

what did these errors fix?  anything I should notice?

You shouldn't notice much difference. The one error was actually a syntax error that the kernel is able to work around. I didn't go through the full 675 optimizations, so not sure what was automatically tweaked. You can tell iasl to be verbose with ```
iasl -tc -vo /path_to_dsdt.dsl
``` This will show info for each optimization that the compiler knows how to fix.

---

### Post by 67GTA on 2009-06-21
[Hated On Mostly]("http://ubuntuforums.org/member.php?u=705393"):

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 828 Optimizations

[ATTACH]118410[/ATTACH]

---

### Post by sergiom99 on 2009-06-23
> **67GTA said:**
>  Another trick I've learned during this process is to specify the operating system at boot. More about this is explained in the links I provided. I found that by adding ```
acpi_osi="Linux"
``` to the boot options, the operating system even saw my hardware differently at boot. This seems to be very affective on HP laptops with Vista preinstalled. I outlined these steps here: [http://www.linuxmint.com/forum/viewtopic.php?f=60&t=18222](http://www.linuxmint.com/forum/viewtopic.php?f=60&t=18222) 
Hey 67GTA, great work you're doing here!

I saw in that link that, after all, adding this parameter to the GRUB was not needed in Ubuntu. Is that right?
Regards- Sergio

---

### Post by 67GTA on 2009-06-24
It really depends on your DSDT. Search through it for "OSI". If there are no instances of split methods, then you won't have to worry about adding the osi definition. Most of the newer HP laptops require the osi to be defined for the temperature to stay within the limits because there are two seperate methods for temps. One for Windows, and one for Linux. The kernel won't read either unless it's osi is defined and just make a guess.

---

### Post by Hated On Mostly on 2009-06-24
> **67GTA said:**
> [Hated On Mostly]("http://ubuntuforums.org/member.php?u=705393"):

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 828 Optimizations

[ATTACH]118410[/ATTACH]

Thanks 67GTA,

No more errors, but it appears all of the optimizations got wiped out.

0 Errors, 0 Warnings, 0 Remarks, 5 Optimizations

---

### Post by sergiom99 on 2009-06-24
> **67GTA said:**
> It really depends on your DSDT. Search through it for "OSI". If there are no instances of split methods, then you won't have to worry about adding the osi definition. Most of the newer HP laptops require the osi to be defined for the temperature to stay within the limits because there are two seperate methods for temps. One for Windows, and one for Linux. The kernel won't read either unless it's osi is defined and just make a guess.
I do have an OSI instance.
When trying to compile I got 2 Errors, 6 Warnings, 0 Remarks, 1127 Optimizations
```
 $ iasl -tc /home/sergio/dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation           
Supports ACPI Specification Revision 3.0a

/home/sergio/dsdt.dsl   104:     Method (\_WAK, 1, NotSerialized)
Warning  1080 -                              ^ Reserved method must return a value (_WAK)

/home/sergio/dsdt.dsl  3540:                 Method (_Q16, 0, NotSerialized)
Warning  1087 -    Not all control paths return a value ^  (_Q16)

/home/sergio/dsdt.dsl  7714:                 Method (_HOT, 0, Serialized)
Warning  1087 -    Not all control paths return a value ^  (_HOT)

/home/sergio/dsdt.dsl  7714:                 Method (_HOT, 0, Serialized)
Warning  1080 -     Reserved method must return a value ^  (_HOT)

/home/sergio/dsdt.dsl  7716:                     Zero
Error    4095 -                                     ^ syntax error, unexpected PARSEOP_ZERO

/home/sergio/dsdt.dsl  7723:                 Method (_CRT, 0, Serialized)
Warning  1087 -    Not all control paths return a value ^  (_CRT)

/home/sergio/dsdt.dsl  7723:                 Method (_CRT, 0, Serialized)
Warning  1080 -     Reserved method must return a value ^  (_CRT)

/home/sergio/dsdt.dsl  7725:                     Zero
Error    4095 -                                     ^ syntax error, unexpected PARSEOP_ZERO

ASL Input:  /home/sergio/dsdt.dsl - 8137 lines, 278758 bytes, 4173 keywords
Compilation complete. 2 Errors, 6 Warnings, 0 Remarks, 1127 Optimizations
sergio@kubuntu:~$
```

Could you please take a look at my file?
thanks!

---

### Post by 67GTA on 2009-06-25
sergiom99: 

```
Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 1130 Optimizations
```

Yours was exactly like mine. I fixed errors for wake from suspend/hibernate and temp readings. It will run cooler/quieter with the custom DSDT. You will definitely want to add the acpi_osi="Linux" definition for yours. Keep a copy of your dmesg output from before and after. You will be able to see the difference, escpecially with your temp being read correctly instead of being guessed at.

[ATTACH]118958[/ATTACH]

---

### Post by sergiom99 on 2009-06-25
wow dude! Thanks a lot!!

I already added the osi definition in my GRUB line before starting the whole DSDT process.
Will be loading your file right now.

Do I need to do this everytime I update the kernel from the repos?

---

### Post by 67GTA on 2009-06-25
No. Keep a copy of the DSDT in a safe place for future use though. You will have to use it again if you ever do a clean install or install a new kernel version. A kernel update/upgrade will trigger the update-initramfs command and recreate the link to the custom DSDT again.

---

### Post by sergiom99 on 2009-06-25
Awesome! It worked just great and it fixed the problem when booting on battery. (holding a key and such)

It hibernated and resumed OK. (even though the first time it resumed it started Kubuntu and powered off. Then I started again and loaded fine.)

Thanks 67GTA!

---

### Post by Roby64 on 2009-06-26
Thanks a lot.

---

### Post by stephen.mann on 2009-06-27
67GTA,

Would you mind looking at mine?

Errors:

> /home/steve/dsdt.dsl   104:     Method (\_WAK, 1, NotSerialized)
Warning  1080 -                             ^ Reserved method must return a value (_WAK)

/home/steve/dsdt.dsl  3540:                 Method (_Q16, 0, NotSerialized)
Warning  1087 -   Not all control paths return a value ^  (_Q16)

/home/steve/dsdt.dsl  7714:                 Method (_HOT, 0, Serialized)
Warning  1087 -   Not all control paths return a value ^  (_HOT)

/home/steve/dsdt.dsl  7714:                 Method (_HOT, 0, Serialized)
Warning  1080 -    Reserved method must return a value ^  (_HOT)

/home/steve/dsdt.dsl  7716:                     Zero
Error    4095 -                                    ^ syntax error, unexpected PARSEOP_ZERO

/home/steve/dsdt.dsl  7723:                 Method (_CRT, 0, Serialized)
Warning  1087 -   Not all control paths return a value ^  (_CRT)

/home/steve/dsdt.dsl  7723:                 Method (_CRT, 0, Serialized)
Warning  1080 -    Reserved method must return a value ^  (_CRT)

/home/steve/dsdt.dsl  7725:                     Zero
Error    4095 -                                    ^ syntax error, unexpected PARSEOP_ZERO
Thanks in advance!

---

### Post by 67GTA on 2009-06-27
stephen.mann:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 1130 Optimizations

Your was exactly like sergiom99's. Fixed wake from sleep/hibernate, temp readings, and CPU tweaks. Should run quieter/cooler.


[ATTACH]119111[/ATTACH]

---

### Post by stephen.mann on 2009-06-27
Thanks!:d

---

### Post by staticanime on 2009-06-27
@67GTA,

Would you mind looking at mine as well? Been driving me crazy trying to find info on the warnings I have

Output:
```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  4565:                 Method (WQAA, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAA)

dsdt.dsl  4772:                 Method (WQAB, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAB)

dsdt.dsl  4787:                 Method (WQAC, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAC)

dsdt.dsl  4796:                 Method (WQAD, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAD)

dsdt.dsl  4889:                 Method (WQAE, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAE)

dsdt.dsl  4970:                 Method (WQAF, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAF)

dsdt.dsl  5087:                 Method (WQAG, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAG)

dsdt.dsl  5198:                 Method (WQAH, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAH)

dsdt.dsl  5327:                 Method (WQAI, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAI)

dsdt.dsl  5379:                 Method (WSAA, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAA)

dsdt.dsl  5586:                 Method (WSAB, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAB)

dsdt.dsl  5601:                 Method (WSAC, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAC)

dsdt.dsl  5610:                 Method (WSAD, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAD)

dsdt.dsl  5703:                 Method (WSAE, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAE)

dsdt.dsl  5784:                 Method (WSAF, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAF)

dsdt.dsl  5901:                 Method (WSAG, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAG)

dsdt.dsl  6012:                 Method (WSAH, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAH)

dsdt.dsl  6141:                 Method (WSAI, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAI)

dsdt.dsl  6192:                 Method (_WED, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (_WED)

dsdt.dsl  6192:                 Method (_WED, 1, NotSerialized)
Warning  1080 -                            ^ Reserved method must return a value (_WED)

ASL Input:  dsdt.dsl - 6270 lines, 186266 bytes, 2915 keywords
AML Output: dsdt.aml - 20275 bytes, 624 named objects, 2291 executable opcodes

Compilation complete. 0 Errors, 20 Warnings, 0 Remarks, 644 Optimizations
```

---

### Post by 67GTA on 2009-06-27
> **staticanime said:**
> @67GTA,

Would you mind looking at mine as well? Been driving me crazy trying to find info on the warnings I have

Output:
```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  4565:                 Method (WQAA, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAA)

dsdt.dsl  4772:                 Method (WQAB, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAB)

dsdt.dsl  4787:                 Method (WQAC, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAC)

dsdt.dsl  4796:                 Method (WQAD, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAD)

dsdt.dsl  4889:                 Method (WQAE, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAE)

dsdt.dsl  4970:                 Method (WQAF, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAF)

dsdt.dsl  5087:                 Method (WQAG, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAG)

dsdt.dsl  5198:                 Method (WQAH, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAH)

dsdt.dsl  5327:                 Method (WQAI, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WQAI)

dsdt.dsl  5379:                 Method (WSAA, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAA)

dsdt.dsl  5586:                 Method (WSAB, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAB)

dsdt.dsl  5601:                 Method (WSAC, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAC)

dsdt.dsl  5610:                 Method (WSAD, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAD)

dsdt.dsl  5703:                 Method (WSAE, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAE)

dsdt.dsl  5784:                 Method (WSAF, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAF)

dsdt.dsl  5901:                 Method (WSAG, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAG)

dsdt.dsl  6012:                 Method (WSAH, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAH)

dsdt.dsl  6141:                 Method (WSAI, 2, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WSAI)

dsdt.dsl  6192:                 Method (_WED, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (_WED)

dsdt.dsl  6192:                 Method (_WED, 1, NotSerialized)
Warning  1080 -                            ^ Reserved method must return a value (_WED)

ASL Input:  dsdt.dsl - 6270 lines, 186266 bytes, 2915 keywords
AML Output: dsdt.aml - 20275 bytes, 624 named objects, 2291 executable opcodes

Compilation complete. 0 Errors, 20 Warnings, 0 Remarks, 644 Optimizations
```

You forgot to attach your dsdt

---

### Post by lukamar on 2009-06-27
Hi 67GTA,
can you help me, plz?
I see you are very able with dsdt.

I've a new HP laptop, dv5-1070el.

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20080926 [Oct  4 2008]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

./dsdt_fixed.txt  1407:             Method (_HOT, 0, Serialized)
Warning  1087 -                                ^ Not all control paths return a value (_HOT)

./dsdt_fixed.txt  1407:             Method (_HOT, 0, Serialized)
Warning  1080 -                                ^ Reserved method must return a value (_HOT)

./dsdt_fixed.txt  1433:             Method (_CRT, 0, Serialized)
Warning  1087 -                                ^ Not all control paths return a value (_CRT)

./dsdt_fixed.txt  1433:             Method (_CRT, 0, Serialized)
Warning  1080 -                                ^ Reserved method must return a value (_CRT)

./dsdt_fixed.txt  1491:             Method (_PSV, 0, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (_PSV)

./dsdt_fixed.txt  1491:             Method (_PSV, 0, NotSerialized)
Warning  1080 -                                ^ Reserved method must return a value (_PSV)

./dsdt_fixed.txt  8188:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -   Not all control paths return a value ^  (_GTM)

./dsdt_fixed.txt  8188:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -    Reserved method must return a value ^  (_GTM)

./dsdt_fixed.txt  8348:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -       Not all control paths return a value ^  (_GTF)

./dsdt_fixed.txt  8348:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -        Reserved method must return a value ^  (_GTF)

./dsdt_fixed.txt  8416:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -       Not all control paths return a value ^  (_GTF)

./dsdt_fixed.txt  8416:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -        Reserved method must return a value ^  (_GTF)

./dsdt_fixed.txt  8489:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -   Not all control paths return a value ^  (_GTM)

./dsdt_fixed.txt  8489:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -    Reserved method must return a value ^  (_GTM)

./dsdt_fixed.txt  8649:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -       Not all control paths return a value ^  (_GTF)

./dsdt_fixed.txt  8649:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -        Reserved method must return a value ^  (_GTF)

./dsdt_fixed.txt  8717:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -       Not all control paths return a value ^  (_GTF)

./dsdt_fixed.txt  8717:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -        Reserved method must return a value ^  (_GTF)

./dsdt_fixed.txt  8822:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -   Not all control paths return a value ^  (_GTM)

./dsdt_fixed.txt  8822:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -    Reserved method must return a value ^  (_GTM)

./dsdt_fixed.txt  8982:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -       Not all control paths return a value ^  (_GTF)

./dsdt_fixed.txt  8982:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -        Reserved method must return a value ^  (_GTF)

./dsdt_fixed.txt  9050:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -       Not all control paths return a value ^  (_GTF)

./dsdt_fixed.txt  9050:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -        Reserved method must return a value ^  (_GTF)

./dsdt_fixed.txt  9123:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -   Not all control paths return a value ^  (_GTM)

./dsdt_fixed.txt  9123:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -    Reserved method must return a value ^  (_GTM)

./dsdt_fixed.txt  9283:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -       Not all control paths return a value ^  (_GTF)

./dsdt_fixed.txt  9283:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -        Reserved method must return a value ^  (_GTF)

./dsdt_fixed.txt  9351:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -       Not all control paths return a value ^  (_GTF)

./dsdt_fixed.txt  9351:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -        Reserved method must return a value ^  (_GTF)

./dsdt_fixed.txt 10233:                 Store (Package (0x02)
Warning  1099 -             Statement is unreachable ^ 

ASL Input:  ./dsdt_fixed.txt - 11811 lines, 414637 bytes, 5701 keywords
AML Output: ././dsdt.aml - 47970 bytes, 995 named objects, 4706 executable opcodes

Compilation complete. 0 Errors, 31 Warnings, 0 Remarks, 40 Optimizations
```

Tnx in advantage, regards.

---

### Post by staticanime on 2009-06-28
> **67GTA said:**
> You forgot to attach your dsdt

Doh, here it is:

---

### Post by 67GTA on 2009-06-28
[lukamar]("http://ubuntuforums.org/member.php?u=861956"): 

```
Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 56 Optimizations
```

I had to do some custom work on yours. After implementing the dsdt and rebooting, post a copy of ```
sudo dmesg
``` from a terminal so I can see if there are any ACPI errors. First open a terminal, click on  "edit" and then "profile preferences". Then click on the "scrolling" tab and change scrollback from 512 to about 3000. Then run sudo dmesg. If you don't do this, the terminal will run out of space (memory) to store all of the output.

[ATTACH]119266[/ATTACH]

---

### Post by 67GTA on 2009-06-28
staticanime:

```
Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 663 Optimizations
```

[ATTACH]119268[/ATTACH]

---

### Post by lukamar on 2009-06-28
Wow wow!! 67GTA

Very good solutions you've found for me. You're a geek!!

Tnx! Tnx! Tnx!

I'm running leopard, and leo as ubuntu need dsdt fix for better performance.

This is dmesg by leopard.

---

### Post by 67GTA on 2009-06-28
The dmesg output is from Apple. I need to see one from Ubuntu. I don't see any errors though;)

---

### Post by lukamar on 2009-06-28
Omg sorry, I'm going to download ubuntu 64 bit. At next time! (sorry for my bad english)

I renew, a big tnx for your work!

---

### Post by 67GTA on 2009-06-28
No big deal. I misunderstood. The custom DSDT should also work on your Mac. If you look on the insanely mac forums, someone was creating a tool to do this for Mac PC's. I don't know if it will do any more than what I've done. You might want to check it out.

---

### Post by staticanime on 2009-06-29
> **67GTA said:**
> staticanime:

```
Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 663 Optimizations
```

[ATTACH]119268[/ATTACH]

Legendary, gonna copy this to my Ubuntu partition and see how it goes, thanks very much :D

---

### Post by lukamar on 2009-06-29
> **67GTA said:**
> No big deal. I misunderstood. The custom DSDT should also work on your Mac. If you look on the insanely mac forums, someone was creating a tool to do this for Mac PC's. I don't know if it will do any more than what I've done. You might want to check it out.

Yes, the dsdt patcher (from insanelymac) remove hpet issues and fix "_T_0" > "T0_0" (your solution "T_0") issues; but your work was very usefull anyway, the patcher don't correct warnings. Tnx again 67GTA.
I'm posting 2 versions of dmesg from ubuntu (i'm loving it), with and without - acpi_osi="Linux" - boot option, as you wrote in first post. 
But I haven't found any difference between the two dmesg.
I've checked the folders in /proc/acpi, but fan and thermal_zone are not populated, in any case.

Tnx for your time 67GTA.

---

### Post by lukamar on 2009-06-30
NB: I'haven't a real mac, but I'm using Leopard on HP dv5-1070el.

---

### Post by 67GTA on 2009-06-30
lukamar: There isn't alot of difference between them. There are no errors, but the kernel still isn't able to see your temps. I would post a bug on launchpad. This might be something the ACPI devs need to look at. I don't think it is DSDT related. Is it actually over heating, or just not reorting temps? Try installing lm-sensors. Open a terminal and run ```
sudo sensors-detect
``` Answer yes (hit enter) for every question except the last. You need to answer yes for it. Then reboot and see if your temps are seen.

---

### Post by scaine on 2009-07-06
Do you think it would be feasible to create a python/gui program that would run iasl, generate your DSDT file, then check its contents against a web respository of such DSDT files, then give you the option to download/install a "fixed" version?

Otherwise, surely, this will potentially affect every future version of linux?

I mean, such a tool would have to be run with huge warnings regarding the potential for complete breakage, but all I'm asking is if such a tool is feasible?

---

### Post by 67GTA on 2009-07-06
I'm sure it could be done. I actually envisioned something like this when I started this thread, but don't know how to write code, and don't have any web space to host anything. If you know of someone interested then tell them to contact me.

---

### Post by kevin butler on 2009-07-08
Well, congratulations 67GTA on creating the most productive thread I've seen in a long, long time. Kudos to you! In following your howto, I've eliminated all but one pesky error 
```

 dsdt.dsl   776:                 Return (^C08F (Arg0, Arg1, Arg2))
 Error    4059 -                                     ^ Called method returns no value 

```Damn it, but I can't sort this last issue correctly. 'Tis beyond me. If you could point me in the right direction, you'd make an old compaq armada m300 very happy indeed!

---

### Post by 67GTA on 2009-07-08
kevin butler:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 1179 Optimizations

I added a null value to fix the last error. The method seemed to be complete. The two remarks were harmless. I changed the values from 0 to 1 to make iasl happy. After you get it done and reboot, open a terminal and edit the scrollback in the terminal preferences to 3000 instead of 512. Then post a copy of ```
sudo dmesg
``` so I can see if there are any acpi errors.

[ATTACH]120400[/ATTACH]

EDIT: Be sure to add acpi_osi="Linux" to your grub list as shown in my first post.

---

### Post by kevin butler on 2009-07-10
[LEFT]Excellent! She boots, reboots, suspends and powers off! All this, without a paragraph of kernel parameters nor any elephants raised, skinny or otherwise. This old curmudgeon of a laptop is transformed to an obedient pup with a single file. How fantastic is that. Huge thanks to you 67GTA for your time!

[/LEFT]
```

sudo dmesg | grep ACPI > dmesg-acpi

```

---

### Post by 67GTA on 2009-07-10
No ACPI errors. Glad to help!

---

### Post by enomis on 2009-07-11
Hi, I have a Toshiba Satellite L300D-22L and I read in several forums that, generally speaking, Satellite L300Ds (and L300) may have buggy DSDT that prevent Linux from correctly managing the fan and the ACPI. In my case, the fan seems to work fine (i.e. it is on and the cpu temperature never gets warmer than 50-52C). However, I was not able to hibernate (system crashes on wake up). Therefore, I tried to fix my DSDT. I write below what I did, in case it might be useful for someone else.

When trying to recompile my dsdt.dsl, I got the following error

dsdt_old.dsl     1: ACPI    LIMF,   8, 
Error    4095 -        ^ syntax error, unexpected PARSEOP_NAMESEG, expecting PARSEOP_DEFINITIONBLOCK

Openining my dsdt.dsl, I saw that the first two lines were:

ACPI Warning (nsaccess-0733): NsLookup: Type mismatch on INFO (RegionField), searching for (Buffer) [20081204]
ACPI Warning (nsaccess-0733): NsLookup: Type mismatch on INFO (RegionField), searching for (Buffer) [20081204]

I deleted both of them and tried to recompile dsdt.dsl. This time I got the following error:

dsdt_old.dsl  2785:                         And (CTRL, 0x1E)
Warning  1105 -                                     ^ Result is not used, operator has no effect

This time I changed And (CTRL, 0x1E) to And (CTRL, 0x1E, CTRL) at line 2785. I was then able to recompile without warning and without errors. While recompiling, iasl made 18 optimizations.
My notebook is now able to hibernate and wakes up without problems. I do not know if the problem was solved by eliminating the warning of by the optimizations, but what matters is that now evereything seems to work :)

I decided to post this just in case someone has my same laptop or is experiencing the same problem.
However, I have one question: what do I have to do if I want to get back to my old dsdt (of which I made a back up copy of course)? To install the new one I followed the howto in the first post of this thread. How do I "uninstall" it?

I hope that my post can help someone and thanks for the answer! :)

---

### Post by RD1 on 2009-07-12
How do I fix these errors?

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  1234:             Method (_WED, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (_WED)

dsdt.dsl  1234:             Method (_WED, 1, NotSerialized)
Warning  1080 -                        ^ Reserved method must return a value (_WED)

dsdt.dsl  1575:             Method (WMCA, 3, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (WMCA)

dsdt.dsl  1673:             Method (WMCB, 3, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (WMCB)

dsdt.dsl  1717:             Method (WMCD, 3, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (WMCD)

dsdt.dsl  1809:             Method (WMCE, 3, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (WMCE)

dsdt.dsl  2190:             Method (WMCF, 3, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (WMCF)

ASL Input:  dsdt.dsl - 7550 lines, 265365 bytes, 2721 keywords
AML Output: dsdt.aml - 26843 bytes, 697 named objects, 2024 executable opcodes

Compilation complete. 0 Errors, 7 Warnings, 0 Remarks, 844 Optimizations

```

Thanks

---

### Post by RD1 on 2009-07-12
Sorry ... flubbed attachment

---

### Post by 67GTA on 2009-07-12
> **RD1 said:**
> Sorry ... flubbed attachment

I was just going to ask for it (LOL)

---

### Post by RD1 on 2009-07-12
...also, the laptop came with 1GB ram. I've since upgraded to 2GB. Does anything in DSDT need to be changed to reflect this?

---

### Post by 67GTA on 2009-07-12
> **RD1 said:**
> ...also, the laptop came with 1GB ram. I've since upgraded to 2GB. Does anything in DSDT need to be changed to reflect this?

Sometimes the BIOS settings have to be changed, but as long as the operating system shows the correct amount of ram, you are good to go. I have your dsdt down to 1 warning. I will have to do some custom work to get the brackets to match. I should have it by tonight.

---

### Post by 67GTA on 2009-07-12
RD1:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 850 Optimizations

It just had a missing bracket, so not bad to fix. Be sure to add the acpi_osi="Linux" definition per my first post and send me a copy of ```
sudo dmesg
``` after a reboot.

[ATTACH]120845[/ATTACH]

---

### Post by jvijayv on 2009-07-12
Thanks for all the help guys. I was having this startup problem where I had to press some key to boot and that is gone after updating the dsdt file...

I have a compaq F700. I used the dsdt file from the following thread - [http://ubuntuforums.org/showthread.php?p=7581849](http://ubuntuforums.org/showthread.php?p=7581849) [page 2] and it works fine and I can boot up without issues.

Thanks to all!

---

### Post by RD1 on 2009-07-12
> Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 850 Optimizations

It just had a missing bracket, so not bad to fix. Be sure to add the acpi_osi="Linux" definition per my first post and send me a copy of
Code:

sudo dmesg

after a reboot.


dmesg after reboot...

---

### Post by rubax on 2009-07-25
Thanks for the HOWTO - it is very enlightening. I have a question that may be off topic. I have a IBM ThinkPad R51 and if I turn off the power supply (so I run on battery) Ubuntu starts rebooting over and over till I put power back on. There is plenty of power on the battery. Basically it just looks like it is booting normally every time and then at some point it just shuts down and starts over. It never makes it to the login screen. Does anybody know if this can be related to a faulty acpi or something? (I don't know anything about this stuff).

The EXTREMELY weird part is that the problem does not occur when I have my mobil broadband usb modem (Huwaei) plugged in! When I pull out the power cord the led showing it's connected to power stays on, however Ubuntu does figure out that I'm not connected, and the battery icon appears in the panel, and I can keep running on battery power.

I noticed the problem about a week ago, but I have no idea when or why it started because I have the modem in and the power connected most of the time.

I tried upgrading from Intrepid to Jaunty, but the problem persists.

I followed the first steps of this HOWTO, and there are no errors or warnings when I compile:
```
Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 2522 Optimizations
```

Any ideas what I could do next? What are the relevant logs to look at and how do I grep the proper places in them? Do you think my hardware is faulty?

I'll probably try to do a clean install of Jaunty, but I doubt it will help.

Thanks a lot for any help on this. (Let me know if I should post this in some other thread - I don't have a lot of experience with these forums).

---

### Post by 67GTA on 2009-07-25
This might be a tough problem to crack. Attach a copy of your dsdt.dsl file, and I will take a look. Is this only with Ubuntu, or can you test it with another OS? It definatley sounds like an ACPI problem since it doesn't happen when a USB device is connected. Have you tried using the DSDT you created yet to see if it still happens?

---

### Post by rubax on 2009-07-25
Thanks for the quick reply. I really have a feeling some hardware is faulty. The problem persists on clean installs of both Intrepid and Jaunty. And you are right it is definitely acpi related. If I include the option acpi=off in /boot/grub/menu.lst the problem disappears (along with all power management - I can't even see the battery in Sys. > Pref. > Power Man.).

I have loaded my own compiled DSDT and it doesn't help. I've attached the dsdt.dsl file. I haven't changed anything since it compiled without errors. I.e. I haven't done: acpi_osi="Linux". Should I do that?

I don't have access to Windows or any other OS, so I haven't tested it on anything other than Ubuntu, but I'll see if I can get one somehow. Will it be sufficient for the test just to make a Windows partition for dual boot or does it have to be installed on it's own in case the problem is in GRUB? (Again, I really don't know what I'm talking about :confused:)

Thanks again for all the help. That's what the Linux/Ubuntu community is all about :)

---

### Post by 67GTA on 2009-07-25
I don't see anything in the dsdt. I wouldn't bother installing Windows. I was just curious if you were dual booting already to see if the same thing happened in Windows. That way we would know if it is hardware or software related. It would have to be installed to the hard drive to check. First, remove the DSDT ```
sudo rm /etc/initramfs-tools/DSDT.aml
``` then update the initramfs ```
sudo update-initramfs -u -k <kernel-version>
``` Reboot. Open a terminal, click on Edit>Profile Preferences>Scrolling tab and change 512 to about 3000. We have to do this so the terminal won't run out of space before the next command spits everything out. Now post a copy of ```
sudo dmesg
``` This will show any ACPI errors. Maybe we can find a clue about what is happening.

---

### Post by rubax on 2009-07-25
Here's the dmesg.

Is there any way to compile a new DSDT file, with parts of the ACPI functionality commented out to figure out what part of the ACPI is causing the problem? As I mentioned previously the problem disappears with acpi=off in GRUB...

---

### Post by 67GTA on 2009-07-25
There were a couple of lines that caught my attention. 

```
Line 92: Local APIC disabled by BIOS -- you can enable it with "lapic"
Line 148: weird, boot CPU (#0) not listed by the BIOS
Line 150: Local APIC not detected. Using dummy APIC emulation
Line 180: HPET not enabled in BIOS. You might try hpet=force boot option

``` Try booting with hpet=force and lapic separately and together to see if it makes a difference. I would also poke around in your BIOS settings to see if it has any ACPI options you can enable/disable. Maybe enable/diable ACPI or SMP (dual cores).

---

### Post by 67GTA on 2009-07-25
Sorry, you need to add the boot options hpet=force and lapic to /boot/grub/menu.lst and reboot.

---

### Post by rubax on 2009-07-26
Attached are the three dmesg files where I have enabled lapic, hpet=force, and both.

The problem still persists...

---

### Post by 67GTA on 2009-07-26
With both options, there are no errors. Maybe try those together with the DSDT. I'm about out of ideas. Is the battery calibrated? When was is calibrated last?

---

### Post by 67GTA on 2009-07-26
I just ran across this: [http://forums.lenovo.com/lnv/board/message?board.id=R_Series_Thinkpads&thread.id=4373 ]("http://forums.lenovo.com/lnv/board/message?board.id=R_Series_Thinkpads&thread.id=4373")

At least you know your not alone. This makes me wonder if it is a random defective battery or something. I would also consider doing a clean install to see if the problem persists. I'm still not sure if this is a bad install/upgrade, ACPI bug, or hardware/battery failure.

---

### Post by rubax on 2009-07-26
Well, thanks a lot for your help anyway. Somehow it helps knowing that I'm not alone (I especially like the fact that Windows has the same problem according to that link you posted ;)).

Exactly what did you mean by doing it with the DSDT? Should I add both hpet=force and lapic to /boot/grub/menu.lst, and compile my own dsdt again following the guide and then reboot? I'll try that very soon and post the results.

I have no idea how I calibrate the battery and if it was ever done, but I'll try to google it and see what I can find out...

---

### Post by rubax on 2009-07-26
Here's the dmesg when using dsdt and hpet=force and lapic. It didn't solve the problem. My laptop battery is lithium-ion and doing okay (I can use it for 1.5-2 hours with the usb-modem in), so from what I understand recalibration wont work. Btw. I tested plugging in a standard 2GB usb flash drive instead of the usb-modem and then disconnecting the power, but the computer starts to reboot. It's only the usb-modem that lets me run on battery - I still think that's a bit weird...

Thanks for all your help and time! Is there a place to give users an official thumbs up on this forum?

---

### Post by NarsilAnduril on 2009-07-27
Hi,

Weired. Found my old Evo'dsdt in in the [sourceforge project hompage]("http://acpi.sourceforge.net/dsdt/index.php") but the [downloaded file]("http://acpi.sourceforge.net/dsdt/dl.php?id=5") isn't in valid gzip format.

Is something wrong with me ?

---

### Post by 67GTA on 2009-07-27
> **rubax said:**
> Here's the dmesg when using dsdt and hpet=force and lapic. It didn't solve the problem. My laptop battery is lithium-ion and doing okay (I can use it for 1.5-2 hours with the usb-modem in), so from what I understand recalibration wont work. Btw. I tested plugging in a standard 2GB usb flash drive instead of the usb-modem and then disconnecting the power, but the computer starts to reboot. It's only the usb-modem that lets me run on battery - I still think that's a bit weird...

Thanks for all your help and time! Is there a place to give users an official thumbs up on this forum?

I would post a bug on launchpad. Maybe the devs will see something I don't.

---

### Post by 67GTA on 2009-07-27
> **NarsilAnduril said:**
> Hi,

Weired. Found my old Evo'dsdt in in the [sourceforge project hompage]("http://acpi.sourceforge.net/dsdt/index.php") but the [downloaded file]("http://acpi.sourceforge.net/dsdt/dl.php?id=5") isn't in valid gzip format.

Is something wrong with me ?

I have had this happen several times with downloads from there. It has to do with the program used to compress the data. A lot of them are .asl which is not human readable. It is most likely in ASCII format. I don't understand why people do this. That is why I tell everyone to use iasl to decode their .asl to .dsl which is human readable text before they send it to me. You can use the file command to tell you what is inside. Open a terminal and run ```
file name_of_file.gz
``` If you follow the first post in this thread and get your dsdt.dsl, post it and I will fix it for you.

---

### Post by NarsilAnduril on 2009-07-27
```
diego@laptop:~/Bureau$ file Compaq*
Compaq-Evo_N160-unknown-custom.asl.gz: ASCII C program text, with very long lines

```

In fact, gzipping a text file is ... strange.

Anyway, that's what I did with my files ;-))

Diego

---

### Post by 67GTA on 2009-07-27
> Acronym for the ***A**merican **S**tandard **C**ode for **I**nformation **I**nterchange*. Pronounced *ask-ee*, ASCII is a code for representing English [characters]("http://www.webopedia.com/TERM/A/character.html") as numbers, with each letter assigned a number from 0 to 127. For example, the ASCII code for [uppercase]("http://www.webopedia.com/TERM/A/uppercase.html") *M* is 77. Most [computers]("http://www.webopedia.com/TERM/A/computer.html") use ASCII codes to represent [text]("http://www.webopedia.com/TERM/A/text.html"), which makes it possible to transfer [data]("http://www.webopedia.com/TERM/A/data.html") from one computer to another.  

In other words the archived file is in ASCII format and is not human readable. The archive manager is expecting a regular gzipped text file. It thinks the file is corrupt.

---

### Post by 67GTA on 2009-07-27
[NarsilAnduril]("http://ubuntuforums.org/member.php?u=238986"): 

0 Errors, 0 Warnings, 0 Remarks, 775 Optimizations

I fixed wake from sleep/suspend error. I also fixed a couple of other errors that probably won't affect your day to day stuff. Send me a copy of ```
sudo dmesg
``` afterwards.

[ATTACH]122658[/ATTACH]

---

### Post by NarsilAnduril on 2009-07-28
Thanks !

Here is the file.

I don't know if this changed something ... I was expecting gnome power manager to find my battery, but it still doesn't.

---

### Post by 67GTA on 2009-07-28
I don't see any errors in your dmesg output. What does ```
lshal | grep battery
``` say?

---

### Post by NarsilAnduril on 2009-07-28
Looks good :

```
diego@laptop:~$ lshal | grep battery
udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_CMB0'
  battery.charge_level.current = 0  (0x0)  (int)
  battery.charge_level.design = 0  (0x0)  (int)
  battery.charge_level.last_full = 0  (0x0)  (int)
  battery.charge_level.percentage = 0  (0x0)  (int)
  battery.charge_level.rate = 1620  (0x654)  (int)
  battery.is_rechargeable = true  (bool)
  battery.model = 'BAT1'  (string)
  battery.present = true  (bool)
  battery.rechargeable.is_charging = false  (bool)
  battery.rechargeable.is_discharging = true  (bool)
  battery.reporting.current = 1903  (0x76f)  (int)
  battery.reporting.design = -1  (0xffffffff)  (int)
  battery.reporting.last_full = -1  (0xffffffff)  (int)
  battery.reporting.rate = 1620  (0x654)  (int)
  battery.reporting.technology = 'Li-ion'  (string)
  battery.reporting.unit = 'mWh'  (string)
  battery.serial = '0000'  (string)
  battery.technology = 'lithium-ion'  (string)
  battery.type = 'primary'  (string)
  battery.vendor = 'COMPAQ'  (string)
  battery.voltage.current = 13544  (0x34e8)  (int)
  battery.voltage.design = -1  (0xffffffff)  (int)
  battery.voltage.unit = 'mV'  (string)
  info.capabilities = {'battery'} (string list)
  info.category = 'battery'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_CMB0'
```

---

### Post by 67GTA on 2009-07-28
According to that your battery is recognized, but can't read it's capacity info. I took another look at your battery section and made some changes. Try this dsdt along with the acpi, hpet, and acpi_osi arguments we tried earlier. Reboot and send me another sudo dmesg output. Hopefully the changes I made will let the kernel see your battery info.

[ATTACH]122738[/ATTACH]

---

### Post by NarsilAnduril on 2009-07-28
That's it, thank you very very much !

Diego

---

### Post by litspliff on 2009-07-28
hey.
i've got an F700 presario that doesn't boot unless AC is connected....it progresses somewhat through the boot if i repeatedly press the power button, but never totally boots until plugged into the wall. same with shutting down.

all the threads i read led here. 


here is my output from [iasl -tc /home/(user)/dsdt.dsl

repeated over and over again...."Object does not exist ^"
then eventually:
Maximum error count (200) exceeded
ASL Input:  /home/(user)/dsdt.dsl - 7375 lines, 254663 bytes, 3490 keywords
Compilation complete. 201 Errors, 0 Warnings, 0 Remarks, 570 Optimizations

what the hell does this mean?

---

### Post by 67GTA on 2009-07-28
> **NarsilAnduril said:**
> That's it, thank you very very much !

Diego

Cool. :guitar: My advice is to keep a copy of the fixed DSDT.aml in a safe place. The DSDT shipped with your BIOS is broken and will never change. If you ever do a clean install of any Linux/Mac OS, then you will have to reuse the custom DSDT. You can use it for any distro.

---

### Post by 67GTA on 2009-07-28
> **litspliff said:**
> hey.
i've got an F700 presario that doesn't boot unless AC is connected....it progresses somewhat through the boot if i repeatedly press the power button, but never totally boots until plugged into the wall. same with shutting down.

all the threads i read led here. 


here is my output from [iasl -tc /home/(user)/dsdt.dsl

repeated over and over again...."Object does not exist ^"
then eventually:
Maximum error count (200) exceeded
ASL Input:  /home/(user)/dsdt.dsl - 7375 lines, 254663 bytes, 3490 keywords
Compilation complete. 201 Errors, 0 Warnings, 0 Remarks, 570 Optimizations

what the hell does this mean?

Iasl has an error limit of 200 before it just gives up. If there was an error on the 3rd line out of a possible of 10,000-11,000 lines, then everything below that 3rd line would also show up as an error. Crazy isn't it? What is the first error in the list?

---

### Post by NarsilAnduril on 2009-07-28
> My advice is to keep a copy of the fixed DSDT.aml in a safe place. The DSDT shipped with your BIOS is broken and will never change. If you ever do a clean install of any Linux/Mac OS, then you will have to reuse the custom DSDT. You can use it for any distro.

Of course, the file is already in my dropbox and all of my computers :D

I'll also try to understand what you did ...

Diego

---

### Post by 67GTA on 2009-07-28
The _GLK and _WAK errors are well documented. The _DOD section on line 1122 is where I did the custom work. You can compare it with the original.

---

### Post by litspliff on 2009-07-29
this is the first page when i
.... | less


```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

ACPI Error (nsaccess-0528): ACPI path has too many parent prefixes (^) - reached
 beyond root node [20081204]

Maximum error count (200) exceeded
/home/-user-/dsdt.dsl    21:     External (^Z00G, IntObj)
Error    4014 -                         From ACPI CA Subsystem ^  (AE_NOT_FOUND 
Failure from lookup %s
)

/home/-user-/dsdt.dsl    24:     Name (RBRF, 0x01)
Error    4063 -            Object does not exist ^  (RBRF)

/home/-user-/dsdt.dsl    25:     Name (L10F, 0x00)
Error    4063 -            Object does not exist ^  (L10F)

/home/-user-/dsdt.dsl    26:     Name (SCIC, 0x00)
Error    4063 -            Object does not exist ^  (SCIC)
:

```

---

### Post by 67GTA on 2009-07-29
> **litspliff said:**
> this is the first page when i
.... | less


```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

ACPI Error (nsaccess-0528): ACPI path has too many parent prefixes (^) - reached
 beyond root node [20081204]

Maximum error count (200) exceeded
/home/-user-/dsdt.dsl    21:     External (^Z00G, IntObj)
Error    4014 -                         From ACPI CA Subsystem ^  (AE_NOT_FOUND 
Failure from lookup %s
)

/home/-user-/dsdt.dsl    24:     Name (RBRF, 0x01)
Error    4063 -            Object does not exist ^  (RBRF)

/home/-user-/dsdt.dsl    25:     Name (L10F, 0x00)
Error    4063 -            Object does not exist ^  (L10F)

/home/-user-/dsdt.dsl    26:     Name (SCIC, 0x00)
Error    4063 -            Object does not exist ^  (SCIC)
:

```

Delete the first two lines in your dsdt.dsl file, save and try it again.

---

### Post by litspliff on 2009-07-29
more specific please (the first two lines are commented, after the comments, the first two lines seem important)....
```
DefinitionBlock ("dsdt.aml", "DSDT", 1, "NVIDIA", "MCP67", 0x06040000)
{
    External (^Z00G, IntObj)
    External (\_PR_.CPU0._PPC, IntObj)

    Name (RBRF, 0x01)
    Name (L10F, 0x00)
    Name (SCIC, 0x00)
    Name (SCID, 0x00)
```are you refering to the definition block, the External, or the name lines?

---

### Post by litspliff on 2009-07-29
not sure if this is worth mentioning, but i'm running 64-bit ubuntu jaunty on my laptop. (F700 presario)

---

### Post by 67GTA on 2009-07-29
It is hard to say without seeing the file. Send me a copy of the dsdt.dsl file and I can either fix it, or help walk you through it if you would rather do it. 32bit vs 64bit doesn't matter with the DSDT.

---

### Post by Scotty Bones on 2009-07-30
67GTA,

I found mine to be interesting.
It does not have any errors, but it does have some warnings and optimizations. Where the surprise came for me, is that my system is from a linux OEM. They have atleast branded the BIOS, I would have thought they would not let something like this slip bye. Since you seem to be the resident expert: If you see something in there that concerns you, I will pass it along to them. 

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/scotty/dsdt.dsl  2033:                         Method (_BQC, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_BQC)

/home/scotty/dsdt.dsl  2033:                         Method (_BQC, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_BQC)

/home/scotty/dsdt.dsl  2581:                                         Or (TMOR, TMPV)
Warning  1105 -                  Result is not used, operator has no effect ^ 

/home/scotty/dsdt.dsl  5259:                                 Or (TMOR, TMPV)
Warning  1105 -          Result is not used, operator has no effect ^ 

ASL Input:  /home/scotty/dsdt.dsl - 6599 lines, 209268 bytes, 2418 keywords
AML Output: /home/scotty/dsdt.aml - 22137 bytes, 686 named objects, 1732 executable opcodes

Compilation complete. 0 Errors, 4 Warnings, 0 Remarks, 41 Optimizations

```

---

### Post by 67GTA on 2009-07-30
> **Scotty Bones said:**
> 67GTA,

I found mine to be interesting.
It does not have any errors, but it does have some warnings and optimizations. Where the surprise came for me, is that my system is from a linux OEM. They have atleast branded the BIOS, I would have thought they would not let something like this slip bye. Since you seem to be the resident expert: If you see something in there that concerns you, I will pass it along to them. 

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/scotty/dsdt.dsl  2033:                         Method (_BQC, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_BQC)

/home/scotty/dsdt.dsl  2033:                         Method (_BQC, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_BQC)

/home/scotty/dsdt.dsl  2581:                                         Or (TMOR, TMPV)
Warning  1105 -                  Result is not used, operator has no effect ^ 

/home/scotty/dsdt.dsl  5259:                                 Or (TMOR, TMPV)
Warning  1105 -          Result is not used, operator has no effect ^ 

ASL Input:  /home/scotty/dsdt.dsl - 6599 lines, 209268 bytes, 2418 keywords
AML Output: /home/scotty/dsdt.aml - 22137 bytes, 686 named objects, 1732 executable opcodes

Compilation complete. 0 Errors, 4 Warnings, 0 Remarks, 41 Optimizations

```

Most people don't dig this deep(LOL) You actually have two warnings. The first two are related. Fix the first and the second fixes it's self. 

```
From the ACPI manual... _BQC Brightness Query Current &#8211; returns the current display brightness level.
``` Yours is fine. IASL is open source and an industry standard. It doesn't let anything get by it. It is just complaining because there is not a "null" value. That means there is not a value to tell the kernel what to do if there is no brightness level returned. I know that seems silly, but the IASL compiler is that precise. The third and fourth warnings are also meaningless. The two lines it is referencing has extra values pertaining to Windows that are not usable to Linux, but won't hurt anything by being there. The kernel just ignores them. In your case there would not be any ACPI errors for anyone to follow. I fixed them, but it's probably not worth the trouble to keep a custom DSDT on this machine. We are just simply are making IASL happy:D You can see the optimizations made by using ```
iasl -tc -vo
```[ATTACH]123001[/ATTACH]

---

### Post by 67GTA on 2009-07-30
[litspliff]("http://ubuntuforums.org/member.php?u=875489"):

The _WAK error is well documented. The method is missing a return value when the kernel tries to wake from sleep. We have to finish the method with the standard return value from the ACPI specs manual. Follow the line numbers and be sure to keep the indentation where it is originally at.

```
183 Release (\_SB.PCI0.PSMX)
184         }
185    Return(Package(0x02){0x00, 0x00})
186   }

```Save and rerun iasl -tc. You should have 0 Errors, 4 Warnings, 0 Remarks, 958 Optimizations. Now we need to fix the _HOT and _CRT methods. They affect your fans and cpu heat settings. The problem is the way it is written tells the kernel that the temps can't be read. That is false. The kernel can see the temps just fine. We have to comment // out the lines that are misleading the temp readings so they are ignored. Make yours look like this and rerun iasl -tc again.

```
7178                Method (_HOT, 0, Serialized)
7179                {
7180//                    If (LEqual (OSYS, 0x07D6))
7181//                    {
7182                        Return (Add (0x0AAC, Multiply (TPC, 0x0A)))
7183//                    }
7184                }
7185
7186                Method (_CRT, 0, Serialized)
7187                {
7188//                    If (LLess (OSYS, 0x07D6))
7189//                    {
7190                        Return (Add (0x0AAC, Multiply (TPC, 0x0A)))
7191//                    }
7192                }
```Now you should have 0 Errors, 0 Warnings, 0 Remarks, 958 Optimizations. Follow the rest of the how to with the dsdt.aml file you produced. You will want to add the acpi_osi="Linux" definition to boot/grub/menu.lst on your machine. After you get it done and reboot, send me a copy of ```
sudo dmesg
``` from a terminal so I can double check for ACPI errors. You should now be able to resume from sleep without hanging, and the machine should run quieter/cooler since your temp/fan relationship will be correct instead of guessed at. You can save a copy of ```
sudo dmesg
``` before this and after to see the differences. Open a terminal, click "Edit" and then "Profile Preferences". Then click the Scrolling tab and change 512 to 3000. The terminal will run out of memory before it spits out all of the data if you don't do this and cut part of it off. I have an error free copy with me if you run in to trouble;)

---

### Post by Scotty Bones on 2009-07-31
> **67GTA said:**
> Most people don't dig this deep(LOL) You actually have two warnings. The first two are related. Fix the first and the second fixes it's self.

Too true. When I saw it hadn't found "errors", I considered forgetting about it, but none of it makes sense to me. We are having a strange issue with the system reporting as being on AC power when it is in fact on battery. As well as not being able to provide discharge times and obviously incorrect recharge times. This just seemed like a tangent worth exploring. I thank you for your time and input.

---

### Post by litspliff on 2009-07-31
doesn't seem right.....

```

[    0.004339] ACPI: Checking initramfs for custom DSDT
[    0.308057] Setting APIC routing to flat
[    0.308611] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.348678] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[    0.352001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3800.36 BogoMIPS (lpj=7600739)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] System has AMD C1E enabled
[    0.004000] Switch to broadcast mode on CPU1
[    0.436204] CPU1: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[    0.436217] Brought up 2 CPUs
[    0.436219] Total of 2 processors activated (7600.31 BogoMIPS).

```


> 

Places to check before and after are: dmesg output and /proc/acpi. I would especially check /proc/acpi/fan and /proc/acpi/thermal_zone to see if they are populated after this tutorial if they weren't before. Another trick I've learned during this process is to specify the operating system at boot. More about this is explained in the links I provided. I found that by adding  	

....not populated....

---

### Post by biodiesel-bri on 2009-07-31
67GTA, thank you ten thousand times.  Your HOWTO completely solved my problem, and also quite a few problems I didn't even know my laptop had.  You sir are the epitome of the open source movement.  It is people like you that make our community so great.

I'm attaching my fixed working dsdt in case anyone else has an hp dv9610 / dv9610us and doesn't want to make the changes I did.  Nothing special; all the fixes were found in the HOWTO.

```

iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

ASL Input:  dsdt.dsl - 7832 lines, 268231 bytes, 3863 keywords
AML Output: dsdt.aml - 30658 bytes, 812 named objects, 3051 executable opcodes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 1069 Optimizations

```

---

### Post by Polygon on 2009-07-31
Hi 67GTA,

you fixed my laptops dsdt file, and i was wondering if you could do the same again for a different computer of mine =P

i tried to fix as much as i could but the only thing i could get from google is the _T_0 renaming to T_0 thingy, the rest i really have no clue about. Can you at least summarize what you did? i am going to write this up on my blog so google indexes it and at least helps some poor soul out there try and fix their broken dsdt files.

dsdt file:  [www.kramidnarg.com/stuff/asus_p5q_pro.dsl.tar.gz](www.kramidnarg.com/stuff/asus_p5q_pro.dsl.tar.gz)

console output: 

```

[mark@Patagonicus dsdt 2102]$ iasl -tc dsdt.dsl 

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090625 [Jun 27 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  8602:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8616:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8631:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8646:             Acquire (MUTE, 0x0FFF)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8660:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8675:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8690:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  9650:         Method (VGET, 1, NotSerialized)
Warning  1087 -                    ^ Not all control paths return a value (VGET)

dsdt.dsl  9695:         Method (TGET, 1, NotSerialized)
Warning  1087 -                    ^ Not all control paths return a value (TGET)

dsdt.dsl  9748:         Method (FGET, 1, NotSerialized)
Warning  1087 -                    ^ Not all control paths return a value (FGET)

dsdt.dsl  9779:             Store (VGET (Local0), Local1)
Warning  1092 -                       ^ Called method may not always return a value

dsdt.dsl  9821:             Store (TGET (Local0), Local1)
Warning  1092 -                       ^ Called method may not always return a value

dsdt.dsl  9854:             Store (FGET (Local0), Local1)
Warning  1092 -                       ^ Called method may not always return a value

dsdt.dsl 10171:                                         ShiftRight (BUF2, 0x04)
Warning  1105 -             Result is not used, operator has no effect ^ 

ASL Input:  dsdt.dsl - 10343 lines, 334155 bytes, 4854 keywords
AML Output: dsdt.aml - 38692 bytes, 1002 named objects, 3852 executable opcodes

Compilation complete. 0 Errors, 14 Warnings, 0 Remarks, 70 Optimizations
[mark@Patagonicus dsdt 2102]$ 

```

also, is there a website besides that crappy old sourceforge page where people post their fixed DSDT files? if not, someone should create one....

---

### Post by 67GTA on 2009-07-31
> **Scotty Bones said:**
> Too true. When I saw it hadn't found "errors", I considered forgetting about it, but none of it makes sense to me. We are having a strange issue with the system reporting as being on AC power when it is in fact on battery. As well as not being able to provide discharge times and obviously incorrect recharge times. This just seemed like a tangent worth exploring. I thank you for your time and input.

I'll take a look at your DSDT again to see if there is anything I can tweak in the battery section.

---

### Post by 67GTA on 2009-07-31
> **litspliff said:**
> doesn't seem right.....

```

[    0.004339] ACPI: Checking initramfs for custom DSDT
[    0.308057] Setting APIC routing to flat
[    0.308611] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.348678] CPU0: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[    0.352001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3800.36 BogoMIPS (lpj=7600739)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 256K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] System has AMD C1E enabled
[    0.004000] Switch to broadcast mode on CPU1
[    0.436204] CPU1: AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 stepping 02
[    0.436217] Brought up 2 CPUs
[    0.436219] Total of 2 processors activated (7600.31 BogoMIPS).

```


....not populated....

Check to make sure you have DSDT.aml (case is sensitive) in /etc/initramfs-tools. Make sure you ran the update-initramfs command with your kernel version. If you are running a development kernel version such as in 9.10, the custom patches won't be compiled until it is considered stable. You have to be running a stable kernel release for the DSDT patch to work.

---

### Post by litspliff on 2009-07-31
yes....stable kernel
> administrator@904:~$ uname -r
2.6.28-14-generic
administrator@904:~$ ls /etc/initramfs-tools/DSDT.aml
/etc/initramfs-tools/DSDT.aml
administrator@904:~$ 



tried again....here's what i got this time....almost 2000 lines of it.

```
 enumerate USB device on port 2
[ 5832.200054] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5832.584071] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5832.968091] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5833.352064] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5833.736057] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5834.120053] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5834.504054] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5834.888055] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5835.301154] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5835.685289] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5836.069130] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5836.452058] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5836.836058] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5837.220055] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5837.604067] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5837.988081] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5838.372066] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5838.756063] hub 4-0:1.0: unable to enumerate USB device on port 2
```
no coincidence that when i shut down....it repeats this over and over and over and over.....

---

### Post by 67GTA on 2009-07-31
> **Polygon said:**
> Hi 67GTA,

you fixed my laptops dsdt file, and i was wondering if you could do the same again for a different computer of mine =P

i tried to fix as much as i could but the only thing i could get from google is the _T_0 renaming to T_0 thingy, the rest i really have no clue about. Can you at least summarize what you did? i am going to write this up on my blog so google indexes it and at least helps some poor soul out there try and fix their broken dsdt files.

dsdt file:  [www.kramidnarg.com/stuff/asus_p5q_pro.dsl.tar.gz]("http://www.kramidnarg.com/stuff/asus_p5q_pro.dsl.tar.gz")

console output: 

```

[mark@Patagonicus dsdt 2102]$ iasl -tc dsdt.dsl 

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090625 [Jun 27 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  8602:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8616:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8631:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8646:             Acquire (MUTE, 0x0FFF)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8660:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8675:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  8690:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  9650:         Method (VGET, 1, NotSerialized)
Warning  1087 -                    ^ Not all control paths return a value (VGET)

dsdt.dsl  9695:         Method (TGET, 1, NotSerialized)
Warning  1087 -                    ^ Not all control paths return a value (TGET)

dsdt.dsl  9748:         Method (FGET, 1, NotSerialized)
Warning  1087 -                    ^ Not all control paths return a value (FGET)

dsdt.dsl  9779:             Store (VGET (Local0), Local1)
Warning  1092 -                       ^ Called method may not always return a value

dsdt.dsl  9821:             Store (TGET (Local0), Local1)
Warning  1092 -                       ^ Called method may not always return a value

dsdt.dsl  9854:             Store (FGET (Local0), Local1)
Warning  1092 -                       ^ Called method may not always return a value

dsdt.dsl 10171:                                         ShiftRight (BUF2, 0x04)
Warning  1105 -             Result is not used, operator has no effect ^ 

ASL Input:  dsdt.dsl - 10343 lines, 334155 bytes, 4854 keywords
AML Output: dsdt.aml - 38692 bytes, 1002 named objects, 3852 executable opcodes

Compilation complete. 0 Errors, 14 Warnings, 0 Remarks, 70 Optimizations
[mark@Patagonicus dsdt 2102]$ 

```also, is there a website besides that crappy old sourceforge page where people post their fixed DSDT files? if not, someone should create one....

I will take a look and try to send you something to explain what I did. The old sourceforge page is really outdated. No one uploads to it anymore. Unfortunately, this thread and here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247) are the only places I know of that has fixed DSDT's posted. I've urged everyone to post there PC make/model along with them. If I knew how to edit the wiki, I would start listing the fixed ones on a wiki page. I would love to get this info out to more people. A lot of newer PC's are having ACPI troubles with Linux because the DSDT's are being compiled with Microsoft's homebrewed AML compiler (MSFT) instead of the industry standard IASL. New users think Linux is crap when MS is breaking stuff. I personally think this deserves another antitrust lawsiut:evil: Microsoft is now basically controlling what you put on your computer.

---

### Post by 67GTA on 2009-07-31
> **litspliff said:**
> yes....stable kernel




tried again....here's what i got this time....almost 2000 lines of it.

```
 enumerate USB device on port 2
[ 5832.200054] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5832.584071] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5832.968091] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5833.352064] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5833.736057] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5834.120053] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5834.504054] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5834.888055] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5835.301154] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5835.685289] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5836.069130] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5836.452058] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5836.836058] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5837.220055] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5837.604067] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5837.988081] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5838.372066] hub 4-0:1.0: unable to enumerate USB device on port 2
[ 5838.756063] hub 4-0:1.0: unable to enumerate USB device on port 2
```no coincidence that when i shut down....it repeats this over and over and over and over.....

Zip up the output of ```
sudo dmesg
``` and attach it here.

---

### Post by litspliff on 2009-07-31
```
administrator@904:~$ dmesg > ./Desktop/dmesg
administrator@904:~$ zip ./Desktop/dmesg.zip ./Desktop/dmesg
  adding: Desktop/dmesg (deflated 92%)

```
i'm afraid of rebooting at this point.....

---

### Post by 67GTA on 2009-07-31
Don't freak out:D You can delete the custom DSDT and update the initramfs to revert it back to before we started.

```
sudo rm /etc/initramfs-tools/DSDT.aml
```
```
sudo update-initramfs -u -k 2.6.28-14-generic
```

Just to be sure you didn't mess up somewhere in the DSDT file, try the one I fixed. This file is read by the kernel at boot to know how to interact with your hardware. One tiny error, and it will choke on something.

[ATTACH]123085[/ATTACH]

---

### Post by litspliff on 2009-07-31
i've got my past 3 kernels in my /boot/grub/menu.lst, so i'm not that worried.

rebooting.....now

---

### Post by litspliff on 2009-07-31
holy f'n sht
amazing!

i can boot on battery power now!!
also boots quicker!!!
uses the fan at more appropriate times!!

also, no longer do i get the USB enumeration message over and over and over and over ......you get the point...



my next inquiry.....is canonical on top of this problem in the development process, or does this duty get passed on to you for yet another version of "stable" ubuntu releases?

---

### Post by 67GTA on 2009-07-31
The Ubuntu devs and Linux devs in general are not able to fix this. For decades the major PC and BIOS companies used the IASL AML compiler to generate DSDT files. It is jointly developed by Intel, HP, Toshiba, Phoenix, and... Microsoft. It was an industry standard, and worked with every operating system. It also conformed to the ACPI standards for all OS's. The IASL is what I'm using to fix the buggy DSDT's. The reason this has become a big problem in the last 2-3 years is that Microsoft has decided to create their own AML compiler (MSFT) that breaks the ACPI standards and breaks ACPI compatability for evry OS except for Windows. Sometimes it is the BIOS manufacturer that uses it, and sometimes hardware manufacturers like Nvidia use it to recompile the DSDT when their chipset is put in the PC. I don't know if any of these people are aware of the problem it causes. The only way to fix this once it is done, is to manually fix the screwed up DSDT and tell the OS to use the custom one. It is sad to say, but like I've told countless others, even when you purchase a PC.....Microsoft still owns it. My HP dv6815nr came with Vista preinstalled. It worked perfectly. Ubuntu had over heating problems because of the _HOT and _CRT errors. At first I thought what most people did and blamed Ubuntu, but was determined to find out why and fix it. That's when I came across this info. After fixing my DSDT for Linux, I used the MSFT compiler in Vista and it said there were zero errors in the DSDT. Then I ran across this: [http://digg.com/linux_unix/Newly_leaked_Antitrust_Memo_Bill_Gates_on_Making_ACPI_Not_Work_with_Linux ]("http://digg.com/linux_unix/Newly_leaked_Antitrust_Memo_Bill_Gates_on_Making_ACPI_Not_Work_with_Linux")
Click on the link to download the PDF email.

---

### Post by litspliff on 2009-07-31
"The only thing necessary for the triumph of evil is for good men to do nothing." Edmund Burke

so what became of mr. comes?
[http://iowa.gotthefacts.org/](http://iowa.gotthefacts.org/)
[http://www.iowamicrosoftcase.com/](http://www.iowamicrosoftcase.com/)


i'll be reading this all day.....found it on BING!

---

### Post by 67GTA on 2009-07-31
I'm not sure about Mr. Comes. For Microsoft lawsuits look here: [http://www.groklaw.net/articlebasic.php?story=20041228040645419](http://www.groklaw.net/articlebasic.php?story=20041228040645419)

---

### Post by 67GTA on 2009-08-01
polygon: 

[ATTACH]123222[/ATTACH]

---

### Post by 67GTA on 2009-08-01
scottybones:

What is in /proc/acpi/battery?

---

### Post by 67GTA on 2009-08-01
scottybones:

I made a small tweak to the battery section. Try this DSDT and keep your fingers crossed. Run ```
sudo dmseg > dmesg
``` and post a copy.

[ATTACH]123257[/ATTACH]

---

### Post by hawthornso23 on 2009-08-02
Thanks for this Tutorial. Using it I was able to solve the  DSDT error responsible for Bug #379940 which was afflicting my machine.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/379940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/379940)

---

### Post by loomsen on 2009-08-02
Hello.

I'm trying for quite some time now, but I just don't seem to be able to find the bug.

> 
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090730 [Aug  2 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 4.0

DSDT.dsl     9:       Sign    ASLB,   32, 
Error    4095 -          ^ syntax error, unexpected PARSEOP_NAMESEG, expecting PARSEOP_DEFINITIONBLOCK

ASL Input:  DSDT.dsl - 6269 lines, 223716 bytes, 0 keywords
Compilation complete. 1 Errors, 0 Warnings, 0 Remarks, 0 Optimizations


No matter what I do, I get this error. 
I hope you can help me, this is slightly drivin me nutz :) 

Here's my DSDT 
[http://omploader.org/vMjJ6aw](http://omploader.org/vMjJ6aw)

Thx

---

### Post by 67GTA on 2009-08-02
> **loomsen said:**
> Hello.

I'm trying for quite some time now, but I just don't seem to be able to find the bug.



No matter what I do, I get this error. 
I hope you can help me, this is slightly drivin me nutz :) 

Here's my DSDT 
[http://omploader.org/vMjJ6aw](http://omploader.org/vMjJ6aw)

Thx

There is an earlier error somewhere in the file. I would probably have to see the original. I'm just chasing syntax errors. This one is no good.

---

### Post by loomsen on 2009-08-02
Yeah, that's what stopped me too, there's only the default comment in the header. Nothing else.

Sigh, thx tho.

Here's my initial dump...

[http://omploader.org/vMjMxYQ](http://omploader.org/vMjMxYQ)

---

### Post by 67GTA on 2009-08-02
> **loomsen said:**
> Yeah, that's what stopped me too, there's only the default comment in the header. Nothing else.

Sigh, thx tho.

Here's my initial dump...

[http://omploader.org/vMjMxYQ](http://omploader.org/vMjMxYQ)

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 45 Optimizations

Line 24 had the wrong syntax. That was causing the whole file to show errors. The Microsoft compiler loves to do this. The original line was (^CPU0._PPC). The "^" symbol doesn't belong here. I changed it to the ACPI compliant (\_PR_.CPU0._PPC) method, and you have zero errors/warnings. It was actually a good dsdt with some monkey buisness at the begining.

[ATTACH]123337[/ATTACH]

---

### Post by Polygon on 2009-08-02
> **67GTA said:**
> polygon: 

[ATTACH]123222[/ATTACH]

thanks!

also, since i use arch linux i wondered if you knew anything about this: [http://bugs.archlinux.org/task/15112](http://bugs.archlinux.org/task/15112)

> 
removed the patch, bye bye dsdt patch ...
please compile now custom kernels for custom dsdt as kernel developers want it.


as in, whenever the next ubuntu version uses a 2.6.30 kernel, are people going to be able to use the sudo "update-initramfs -u -k kernel-version" command anymore? or is this issue a arch linux specific thing only.

---

### Post by 67GTA on 2009-08-02
I'm guessing it is just the Arch kernel developers that are removing the patch. I guess they are having problems, and just decided to remove it instead of fix it. Most distros add/remove their own kernel patches. The channel log for 2.6.30 still mentions the initrd-dsdt hook for Ubuntu.

---

### Post by 67GTA on 2009-08-02
The pacth has been updated for 2.6.30. It is available. I would file a bug for Arch and link to it. The kernel devs just aren't compiling it in for some reason. You can also download the patch and try recompiling the kernel yourself if you feel energetic (LOL). [http://gaugusch.at/acpi-dsdt-initrd-patches/acpi-dsdt-initrd-v0.9d-2.6.30-20090730+log.patch](http://gaugusch.at/acpi-dsdt-initrd-patches/acpi-dsdt-initrd-v0.9d-2.6.30-20090730+log.patch)

---

### Post by loomsen on 2009-08-02
> **67GTA said:**
> 
Line 24 had the wrong syntax. That was causing the whole file to show errors. The Microsoft compiler loves to do this. The original line was (^CPU0._PPC). The "^" symbol doesn't belong here. I changed it to the ACPI compliant (\_PR_.CPU0._PPC) method, and you have zero errors/warnings. It was actually a good dsdt with some monkey buisness at the begining.


Thank you very much, Sir!
Much appreciated.

---

### Post by WMarin288 on 2009-08-02
I only got as far as the fourth step
```
iasl -tc /home/<yourusername>/dsdt.dsl 
```Afterwards, this is what came up.

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/adminwalter/dsdt.dsl     1: [*** iASL: Read error on source code temp file /home/adminwalter/dsdt.src ***]
Error    4095 -                  ^ syntax error, unexpected $end, expecting PARSEOP_DEFINITIONBLOCK

Error    4010 - Could not close file "/home/adminwalter/dsdt.hex" (No space left on device)

Segmentation fault

```I'm not sure how to proceed from here.

---

### Post by 67GTA on 2009-08-03
> **WMarin288 said:**
> I only got as far as the fourth step
```
iasl -tc /home/<yourusername>/dsdt.dsl 
```Afterwards, this is what came up.

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/adminwalter/dsdt.dsl     1: [*** iASL: Read error on source code temp file /home/adminwalter/dsdt.src ***]
Error    4095 -                  ^ syntax error, unexpected $end, expecting PARSEOP_DEFINITIONBLOCK

Error    4010 - Could not close file "/home/adminwalter/dsdt.hex" (No space left on device)

Segmentation fault

```I'm not sure how to proceed from here.

From the error message, it looks like you have some text that shouldn't be there at the top of the file. I would have to look at it. Zip up a copy of the original dsdt.dsl file and attach it here.

---

### Post by WMarin288 on 2009-08-03
> **67GTA said:**
> From the error message, it looks like you have some text that shouldn't be there at the top of the file. I would have to look at it. Zip up a copy of the original dsdt.dsl file and attach it here.

Here it is. Sorry that I didn't zip and upload the file through Ubuntu, but Just recently, I couldn't open Firefox at all on Ubuntu.

---

### Post by scaine on 2009-08-07
Hi 67GTA, would you mind helping me with this dsl file?


```
$ iasl -tc dsdt.dsl 

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  2716:                             Name (_T_0, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_0)

dsdt.dsl  2782:                             Name (_T_0, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_0)

dsdt.dsl  3036:                     Method (DRUL, 1, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (DRUL)

dsdt.dsl  3529:                         Name (_T_0, Zero)
Remark   5110 -    Use of compiler reserved name ^  (_T_0)

dsdt.dsl  3595:                         Name (_T_0, Zero)
Remark   5110 -    Use of compiler reserved name ^  (_T_0)

dsdt.dsl  5714:                         Name (_T_0, Zero)
Remark   5110 -    Use of compiler reserved name ^  (_T_0)

dsdt.dsl  9335:             Method (BTST, 0, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (BTST)

dsdt.dsl  9389:             Method (EVNT, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (EVNT)

dsdt.dsl 10173:                 Name (_T_0, Zero)
Remark   5110 -                          ^ Use of compiler reserved name (_T_0)

ASL Input:  dsdt.dsl - 10940 lines, 367766 bytes, 4539 keywords
AML Output: dsdt.aml - 40523 bytes, 962 named objects, 3577 executable opcodes

Compilation complete. 0 Errors, 3 Warnings, 6 Remarks, 41 Optimizations

```

It's a Toshiba U400-130 and I reckon that it runs a little hot.  Otherwise, everything seems to be working though...

---

### Post by 67GTA on 2009-08-07
scaine:

[ATTACH]123969[/ATTACH]

---

### Post by s0undt3ch on 2009-08-08
I think I'm screwed!

Here's the output when trying to re-compile my unchanged DSDT:
  [http://paste.pocoo.org/show/133250/](http://paste.pocoo.org/show/133250/)

Here's the DSDT:
  [http://paste.pocoo.org/show/133251/](http://paste.pocoo.org/show/133251/)

Where do I even start!?

---

### Post by 67GTA on 2009-08-08
> **s0undt3ch said:**
> I think I'm screwed!

Here's the output when trying to re-compile my unchanged DSDT:
  [http://paste.pocoo.org/show/133250/](http://paste.pocoo.org/show/133250/)

Here's the DSDT:
  [http://paste.pocoo.org/show/133251/](http://paste.pocoo.org/show/133251/)

Where do I even start!?

That may or may not be too bad. One small error can throw everything into a tailspin. The compiler gives up after 200 errors. Zip up a copy of your dsdt.dsl file and attach it here. I will take a look at it.

---

### Post by s0undt3ch on 2009-08-08
> **67GTA said:**
> That may or may not be too bad. One small error can throw everything into a tailspin. The compiler gives up after 200 errors. Zip up a copy of your dsdt.dsl file and attach it here. I will take a look at it.

Here it is. Thank You!

---

### Post by 67GTA on 2009-08-09
s0undt3ch:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 61 Optimizations

This will probably not work with the 2.6.31 kernel. I don't think the custom dsdt patch has been compiled in to it yet. 2.6.28 is the latest version (Jaunty) I'm sure it will work with. All of the custom patches like this aren't included until the final release. 

[ATTACH]124095[/ATTACH]

---

### Post by s0undt3ch on 2009-08-09
> **67GTA said:**
> s0undt3ch:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 61 Optimizations

This will probably not work with the 2.6.31 kernel. I don't think the custom dsdt patch has been compiled in to it yet. 2.6.28 is the latest version (Jaunty) I'm sure it will work with. All of the custom patches like this aren't included until the final release. 

[ATTACH]124095[/ATTACH]

I won't be using .31 since I got some segfaults on the logs.

As you suggest I found the line referring to the custom DSDT.
Here's the ACPI messages from dmesg: [http://paste.pocoo.org/show/133255/](http://paste.pocoo.org/show/133255/)

Thank You! However, temperatures are the same they were before I tried the .31 kernel. Still too high.
```

Battery 0: Discharging, 100%, discharging at zero rate - will never fully discharge.
     Thermal 0: ok, 40.0 degrees C
     Thermal 1: ok, 55.0 degrees C
     Thermal 2: ok, 62.0 degrees C
     Cooling 0: LCD 0 of 8
     Cooling 1: Processor 0 of 10
     Cooling 2: Processor 0 of 10
     Cooling 3: Fan 0 of 1

```

---

### Post by 67GTA on 2009-08-09
s0undt3ch:

Do you have a link to the laptop product page? I was trying to run down the specs, but LG doesn't list laptops on their site.

---

### Post by 67GTA on 2009-08-09
s0undt3ch:

The limit for your CPU is 100C. 64C isn't that bad if there is a load such as booting or video/games. Is your's shutting down too? Just for giggles, try booting with acpi=off in your /boot/grub/menu.lst to see if it helps anything.

---

### Post by s0undt3ch on 2009-08-09
> **67GTA said:**
> s0undt3ch:

Do you have a link to the laptop product page? I was trying to run down the specs, but LG doesn't list laptops on their site.

Here's the spec, in Portuguese, sorry, but you can understand the specs:
  [http://pt.lge.com/download/product/040316/P1-J331P/P1-J331P.pdf](http://pt.lge.com/download/product/040316/P1-J331P/P1-J331P.pdf)

---

### Post by s0undt3ch on 2009-08-09
> **67GTA said:**
> s0undt3ch:

The limit for your CPU is 100C. 64C isn't that bad if there is a load such as booting or video/games. Is your's shutting down too? Just for giggles, try booting with acpi=off in your /boot/grub/menu.lst to see if it helps anything.

I'll try that giggle in a while, though my laptop only shut down once because it did reach 100C, then I limited it's velocity.

Whats really weird is the discrepancy between the 2 cpu's, 10ºC's

---

### Post by scaine on 2009-08-09
> **67GTA said:**
> scaine:

[ATTACH]123969[/ATTACH]

Awesome - thanks very much.  Tried it tonight and it worked perfectly.  My dmesg output shows that it's using the new aml file.  The laptop is running slightly cooler, subjectively (since I couldn't get LMsensors working before) at around 30 degrees core and 40 for the chassis (LMsensors now reports three ACPI values).

I don't think this aml file would have affected LMsensors, would it?  My guess is that because I had to downgrade to 2.6.28 to use this, everything is detecting normally again.  Including my bluetooth.

---

### Post by s0undt3ch on 2009-08-09
> **67GTA said:**
> s0undt3ch:

The limit for your CPU is 100C. 64C isn't that bad if there is a load such as booting or video/games. Is your's shutting down too? Just for giggles, try booting with acpi=off in your /boot/grub/menu.lst to see if it helps anything.

Like this I can't know the temperature, now that I'm posting, I don't think I ran sensors. This is based on the non-working plasma in my KDE 4.2

---

### Post by kidalive on 2009-08-10
How about this DSDT file? I have problems compiling it into DSDT.AML. If you can help me, then p.l.s help me.
```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20080926 [Oct  4 2008]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

ACPI Error (nsaccess-0530): ACPI path has too many parent prefixes (^) - reached beyond root node [20080926]

Maximum error count (200) exceeded
./dsdt_fixed.txt    24:     External (^CPU0._PPC)
Error    4014 -          From ACPI CA Subsystem ^  (AE_NOT_FOUND Failure from lookup %s
)

./dsdt_fixed.txt    27:     Mutex (MUTX, 0x00)
Error    4063 - Object does not exist ^  (MUTX)

./dsdt_fixed.txt    28:     OperationRegion (CMS2, SystemIO, 0x72, 0x02)
Error    4063 -           Object does not exist ^  (CMS2)

./dsdt_fixed.txt    29:     Field (CMS2, ByteAcc, NoLock, Preserve)
Error    4063 - Object does not exist ^  (CMS2)

./dsdt_fixed.txt    31:         INDX,   8, 
Error    4063 -                    ^ Object does not exist (INDX)

./dsdt_fixed.txt    32:         DATA,   8
Error    4063 -                    ^ Object does not exist (DATA)

./dsdt_fixed.txt    35:     IndexField (INDX, DATA, ByteAcc, NoLock, Preserve)
Error    4063 -      Object does not exist ^  (INDX)

./dsdt_fixed.txt    35:     IndexField (INDX, DATA, ByteAcc, NoLock, Preserve)
Error    4063 -            Object does not exist ^  (DATA)

./dsdt_fixed.txt    38:         LBLM,   1, 
Error    4063 -                    ^ Object does not exist (LBLM)

./dsdt_fixed.txt    40:         USWU,   1, 
Error    4063 -                    ^ Object does not exist (USWU)

./dsdt_fixed.txt    42:         LCDL,   3, 
Error    4063 -                    ^ Object does not exist (LCDL)

./dsdt_fixed.txt    44:         S4FG,   1
Error    4063 -                    ^ Object does not exist (S4FG)

./dsdt_fixed.txt    47:     OperationRegion (PRT0, SystemIO, 0x80, 0x04)
Error    4063 -           Object does not exist ^  (PRT0)

./dsdt_fixed.txt    48:     Field (PRT0, DWordAcc, Lock, Preserve)
Error    4063 - Object does not exist ^  (PRT0)

./dsdt_fixed.txt    50:         P80H,   32
Error    4063 -                    ^ Object does not exist (P80H)

./dsdt_fixed.txt    53:     Method (P8XH, 2, Serialized)
Error    4063 -  Object does not exist ^  (P8XH)

./dsdt_fixed.txt    57:             Store (Or (And (P80D, 0xFFFFFF00), Arg1), P80D)
Error    4063 -                  Object does not exist ^  (P80D)

./dsdt_fixed.txt    57:             Store (Or (And (P80D, 0xFFFFFF00), Arg1), P80D)
Error    4063 -                                            Object does not exist ^  (P80D)

./dsdt_fixed.txt    62:             Store (Or (And (P80D, 0xFFFF00FF), ShiftLeft (Arg1, 0x08)
Error    4063 -                  Object does not exist ^  (P80D)

./dsdt_fixed.txt    63:                 ), P80D)
Error    4063 -         Object does not exist ^  (P80D)

./dsdt_fixed.txt    68:             Store (Or (And (P80D, 0xFF00FFFF), ShiftLeft (Arg1, 0x10)
Error    4063 -                  Object does not exist ^  (P80D)

./dsdt_fixed.txt    69:                 ), P80D)
Error    4063 -         Object does not exist ^  (P80D)

./dsdt_fixed.txt    74:             Store (Or (And (P80D, 0x00FFFFFF), ShiftLeft (Arg1, 0x18)
Error    4063 -                  Object does not exist ^  (P80D)

./dsdt_fixed.txt    75:                 ), P80D)
Error    4063 -         Object does not exist ^  (P80D)

./dsdt_fixed.txt    78:         Store (P80D, P80H)
Error    4063 -     Object does not exist ^  (P80D)

./dsdt_fixed.txt    78:         Store (P80D, P80H)
Error    4063 -           Object does not exist ^  (P80H)

./dsdt_fixed.txt    81:     Method (_PIC, 1, NotSerialized)
Error    4063 -  Object does not exist ^  (_PIC)

./dsdt_fixed.txt    83:         Store (Arg0, GPIC)
Error    4063 -           Object does not exist ^  (GPIC)

./dsdt_fixed.txt    86:     Method (_PTS, 1, NotSerialized)
Error    4063 -  Object does not exist ^  (_PTS)

./dsdt_fixed.txt    88:         Store (Zero, P80D)
Error    4063 -           Object does not exist ^  (P80D)

./dsdt_fixed.txt    89:         P8XH (Zero, Arg0)
Error    4063 -                    ^ Object does not exist (P8XH)

./dsdt_fixed.txt    92:             Store (Zero, \_SB.PCI0.LPCB.EC0.XSEC)
Error    4063 -                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.XSEC)

./dsdt_fixed.txt    93:             Store (Zero, \_SB.PCI0.LPCB.EC0.SLMS)
Error    4063 -                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.SLMS)

./dsdt_fixed.txt    94:             Store (One, S4FG)
Error    4063 -              Object does not exist ^  (S4FG)

./dsdt_fixed.txt    99:             Store (Zero, \_SB.PCI0.LPCB.EC0.XSEC)
Error    4063 -                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.XSEC)

./dsdt_fixed.txt   104:             Store (One, \_SB.PCI0.LPCB.EC0.S3FG)
Error    4063 -                                 Object does not exist ^  (\_SB.PCI0.LPCB.EC0.S3FG)

./dsdt_fixed.txt   108:     Method (_WAK, 1, NotSerialized)
Error    4063 -  Object does not exist ^  (_WAK)

./dsdt_fixed.txt   110:         P8XH (One, 0xAB)
Error    4063 -                    ^ Object does not exist (P8XH)

./dsdt_fixed.txt   115:                 If (LAnd (And (CFGD, 0xF0), LEqual (OSYS, 0x07D1)))
Error    4063 -                                          Object does not exist ^  (OSYS)

./dsdt_fixed.txt   117:                     TRAP (0x3D)
Error    4063 -          Object does not exist ^  (TRAP)

./dsdt_fixed.txt   122:         If (LEqual (RP1D, Zero))
Error    4063 -          Object does not exist ^  (RP1D)

./dsdt_fixed.txt   124:             Notify (\_SB.PCI0.RP01, Zero)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.RP01)

./dsdt_fixed.txt   127:         If (LEqual (RP2D, Zero))
Error    4063 -          Object does not exist ^  (RP2D)

./dsdt_fixed.txt   129:             Notify (\_SB.PCI0.RP02, Zero)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.RP02)

./dsdt_fixed.txt   132:         If (LEqual (RP3D, Zero))
Error    4063 -          Object does not exist ^  (RP3D)

./dsdt_fixed.txt   134:             Notify (\_SB.PCI0.RP03, Zero)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.RP03)

./dsdt_fixed.txt   137:         If (LEqual (RP4D, Zero))
Error    4063 -          Object does not exist ^  (RP4D)

./dsdt_fixed.txt   139:             Notify (\_SB.PCI0.RP04, Zero)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.RP04)

./dsdt_fixed.txt   142:         If (LEqual (RP5D, Zero))
Error    4063 -          Object does not exist ^  (RP5D)

./dsdt_fixed.txt   144:             Notify (\_SB.PCI0.RP05, Zero)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.RP05)

./dsdt_fixed.txt   147:         If (LEqual (RP6D, Zero))
Error    4063 -          Object does not exist ^  (RP6D)

./dsdt_fixed.txt   149:             Notify (\_SB.PCI0.RP06, Zero)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.RP06)

./dsdt_fixed.txt   152:         \_SB.PCI0.LPCB.EC0._REG (0x03, One)
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.LPCB.EC0._REG)

./dsdt_fixed.txt   155:             If (PCIW)
Error    4063 -      Object does not exist ^  (PCIW)

./dsdt_fixed.txt   157:                 Notify (\_SB.PWRB, 0x02)
Error    4063 -                   Object does not exist ^  (\_SB.PWRB)

./dsdt_fixed.txt   163:             Notify (\_SB.PWRB, 0x02)
Error    4063 -               Object does not exist ^  (\_SB.PWRB)

./dsdt_fixed.txt   166:         \_PR.RPPC ()
Error    4063 -   Object does not exist ^  (\_PR.RPPC)

./dsdt_fixed.txt   167:         Store (Zero, \_SB.PCI0.LPCB.EC0.APST)
Error    4063 -                              Object does not exist ^  (\_SB.PCI0.LPCB.EC0.APST)

./dsdt_fixed.txt   168:         Store (Zero, \_SB.PCI0.LPCB.EC0.APTH)
Error    4063 -                              Object does not exist ^  (\_SB.PCI0.LPCB.EC0.APTH)

./dsdt_fixed.txt   169:         \_SB.PCI0.LPCB.EC0._Q07 ()
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.LPCB.EC0._Q07)

./dsdt_fixed.txt   170:         P8XH (Zero, 0xCD)
Error    4063 -                    ^ Object does not exist (P8XH)

./dsdt_fixed.txt   178:     Method (GETB, 3, Serialized)
Error    4063 -  Object does not exist ^  (GETB)

./dsdt_fixed.txt   182:         CreateField (Arg2, Local0, Local1, TBF3)
Error    4063 -           Object does not exist ^  (TBF3)

./dsdt_fixed.txt   183:         Return (TBF3)
Error    4063 -      Object does not exist ^  (TBF3)

./dsdt_fixed.txt   186:     Method (PNOT, 0, Serialized)
Error    4063 -  Object does not exist ^  (PNOT)

./dsdt_fixed.txt   188:         If (MPEN)
Error    4063 -  Object does not exist ^  (MPEN)

./dsdt_fixed.txt   192:                 Notify (\_PR.CPU0, 0x80)
Error    4063 -                   Object does not exist ^  (\_PR.CPU0)

./dsdt_fixed.txt   196:                     Notify (\_PR.CPU0, 0x81)
Error    4063 -                       Object does not exist ^  (\_PR.CPU0)

./dsdt_fixed.txt   202:                 Notify (\_PR.CPU1, 0x80)
Error    4063 -                   Object does not exist ^  (\_PR.CPU1)

./dsdt_fixed.txt   206:                     Notify (\_PR.CPU1, 0x81)
Error    4063 -                       Object does not exist ^  (\_PR.CPU1)

./dsdt_fixed.txt   212:             Notify (\_PR.CPU0, 0x80)
Error    4063 -               Object does not exist ^  (\_PR.CPU0)

./dsdt_fixed.txt   214:             Notify (\_PR.CPU0, 0x81)
Error    4063 -               Object does not exist ^  (\_PR.CPU0)

./dsdt_fixed.txt   218:     Method (TRAP, 1, Serialized)
Error    4063 -  Object does not exist ^  (TRAP)

./dsdt_fixed.txt   220:         Store (Arg0, SMIF)
Error    4063 -           Object does not exist ^  (SMIF)

./dsdt_fixed.txt   221:         Store (Zero, TRP0)
Error    4063 -           Object does not exist ^  (TRP0)

./dsdt_fixed.txt   222:         Return (SMIF)
Error    4063 -      Object does not exist ^  (SMIF)

./dsdt_fixed.txt   227:         Method (_INI, 0, NotSerialized)
Error    4063 -      Object does not exist ^  (_INI)

./dsdt_fixed.txt   229:             Store (0x07D0, OSYS)
Error    4063 -                 Object does not exist ^  (OSYS)

./dsdt_fixed.txt   234:                     Store (One, LINX)
Error    4063 -                      Object does not exist ^  (LINX)

./dsdt_fixed.txt   239:                     Store (0x07D1, OSYS)
Error    4063 -                         Object does not exist ^  (OSYS)

./dsdt_fixed.txt   244:                     Store (0x07D1, OSYS)
Error    4063 -                         Object does not exist ^  (OSYS)

./dsdt_fixed.txt   249:                     Store (0x07D2, OSYS)
Error    4063 -                         Object does not exist ^  (OSYS)

./dsdt_fixed.txt   254:                     Store (0x07D6, OSYS)
Error    4063 -                         Object does not exist ^  (OSYS)

./dsdt_fixed.txt   260:     OperationRegion (GNVS, SystemMemory, 0x7F6DEDBC, 0x0100)
Error    4063 -           Object does not exist ^  (GNVS)

./dsdt_fixed.txt   261:     Field (GNVS, AnyAcc, Lock, Preserve)
Error    4063 - Object does not exist ^  (GNVS)

./dsdt_fixed.txt   263:         OSYS,   16, 
Error    4063 -                    ^ Object does not exist (OSYS)

./dsdt_fixed.txt   264:         SMIF,   8, 
Error    4063 -                    ^ Object does not exist (SMIF)

./dsdt_fixed.txt   265:         PRM0,   8, 
Error    4063 -                    ^ Object does not exist (PRM0)

./dsdt_fixed.txt   266:         PRM1,   8, 
Error    4063 -                    ^ Object does not exist (PRM1)

./dsdt_fixed.txt   267:         SCIF,   8, 
Error    4063 -                    ^ Object does not exist (SCIF)

./dsdt_fixed.txt   268:         PRM2,   8, 
Error    4063 -                    ^ Object does not exist (PRM2)

./dsdt_fixed.txt   269:         PRM3,   8, 
Error    4063 -                    ^ Object does not exist (PRM3)

./dsdt_fixed.txt   270:         LCKF,   8, 
Error    4063 -                    ^ Object does not exist (LCKF)

./dsdt_fixed.txt   271:         PRM4,   8, 
Error    4063 -                    ^ Object does not exist (PRM4)

./dsdt_fixed.txt   272:         PRM5,   8, 
Error    4063 -                    ^ Object does not exist (PRM5)

./dsdt_fixed.txt   273:         P80D,   32, 
Error    4063 -                    ^ Object does not exist (P80D)

./dsdt_fixed.txt   274:         LIDS,   8, 
Error    4063 -                    ^ Object does not exist (LIDS)

./dsdt_fixed.txt   275:         PWRS,   8, 
Error    4063 -                    ^ Object does not exist (PWRS)

./dsdt_fixed.txt   276:         DBGS,   8, 
Error    4063 -                    ^ Object does not exist (DBGS)

./dsdt_fixed.txt   277:         LINX,   8, 
Error    4063 -                    ^ Object does not exist (LINX)

./dsdt_fixed.txt   279:         ACT1,   8, 
Error    4063 -                    ^ Object does not exist (ACT1)

./dsdt_fixed.txt   280:         ACTT,   8, 
Error    4063 -                    ^ Object does not exist (ACTT)

./dsdt_fixed.txt   281:         PSVT,   8, 
Error    4063 -                    ^ Object does not exist (PSVT)

./dsdt_fixed.txt   282:         TC1V,   8, 
Error    4063 -                    ^ Object does not exist (TC1V)

./dsdt_fixed.txt   283:         TC2V,   8, 
Error    4063 -                    ^ Object does not exist (TC2V)

./dsdt_fixed.txt   284:         TSPV,   8, 
Error    4063 -                    ^ Object does not exist (TSPV)

./dsdt_fixed.txt   285:         CRTT,   8, 
Error    4063 -                    ^ Object does not exist (CRTT)

./dsdt_fixed.txt   286:         DTSE,   8, 
Error    4063 -                    ^ Object does not exist (DTSE)

./dsdt_fixed.txt   287:         DTS1,   8, 
Error    4063 -                    ^ Object does not exist (DTS1)

./dsdt_fixed.txt   288:         DTS2,   8, 
Error    4063 -                    ^ Object does not exist (DTS2)

./dsdt_fixed.txt   290:         APIC,   8, 
Error    4063 -                    ^ Object does not exist (APIC)

./dsdt_fixed.txt   291:         MPEN,   8, 
Error    4063 -                    ^ Object does not exist (MPEN)

./dsdt_fixed.txt   292:         PCP0,   8, 
Error    4063 -                    ^ Object does not exist (PCP0)

./dsdt_fixed.txt   293:         PCP1,   8, 
Error    4063 -                    ^ Object does not exist (PCP1)

./dsdt_fixed.txt   294:         PPCM,   8, 
Error    4063 -                    ^ Object does not exist (PPCM)

./dsdt_fixed.txt   297:         IGDS,   8, 
Error    4063 -                    ^ Object does not exist (IGDS)

./dsdt_fixed.txt   298:         TLST,   8, 
Error    4063 -                    ^ Object does not exist (TLST)

./dsdt_fixed.txt   299:         CADL,   8, 
Error    4063 -                    ^ Object does not exist (CADL)

./dsdt_fixed.txt   300:         PADL,   8, 
Error    4063 -                    ^ Object does not exist (PADL)

./dsdt_fixed.txt   301:         CSTE,   16, 
Error    4063 -                    ^ Object does not exist (CSTE)

./dsdt_fixed.txt   302:         NSTE,   16, 
Error    4063 -                    ^ Object does not exist (NSTE)

./dsdt_fixed.txt   303:         SSTE,   16, 
Error    4063 -                    ^ Object does not exist (SSTE)

./dsdt_fixed.txt   304:         NDID,   8, 
Error    4063 -                    ^ Object does not exist (NDID)

./dsdt_fixed.txt   305:         DID1,   32, 
Error    4063 -                    ^ Object does not exist (DID1)

./dsdt_fixed.txt   306:         DID2,   32, 
Error    4063 -                    ^ Object does not exist (DID2)

./dsdt_fixed.txt   307:         DID3,   32, 
Error    4063 -                    ^ Object does not exist (DID3)

./dsdt_fixed.txt   308:         DID4,   32, 
Error    4063 -                    ^ Object does not exist (DID4)

./dsdt_fixed.txt   309:         DID5,   32, 
Error    4063 -                    ^ Object does not exist (DID5)

./dsdt_fixed.txt   311:         BLCS,   8, 
Error    4063 -                    ^ Object does not exist (BLCS)

./dsdt_fixed.txt   312:         BRTL,   8, 
Error    4063 -                    ^ Object does not exist (BRTL)

./dsdt_fixed.txt   313:         ALSE,   8, 
Error    4063 -                    ^ Object does not exist (ALSE)

./dsdt_fixed.txt   314:         ALAF,   8, 
Error    4063 -                    ^ Object does not exist (ALAF)

./dsdt_fixed.txt   315:         LLOW,   8, 
Error    4063 -                    ^ Object does not exist (LLOW)

./dsdt_fixed.txt   316:         LHIH,   8, 
Error    4063 -                    ^ Object does not exist (LHIH)

./dsdt_fixed.txt   318:         EMAE,   8, 
Error    4063 -                    ^ Object does not exist (EMAE)

./dsdt_fixed.txt   319:         EMAP,   16, 
Error    4063 -                    ^ Object does not exist (EMAP)

./dsdt_fixed.txt   320:         EMAL,   16, 
Error    4063 -                    ^ Object does not exist (EMAL)

./dsdt_fixed.txt   322:         MEFE,   8, 
Error    4063 -                    ^ Object does not exist (MEFE)

./dsdt_fixed.txt   324:         TPMP,   8, 
Error    4063 -                    ^ Object does not exist (TPMP)

./dsdt_fixed.txt   325:         TPME,   8, 
Error    4063 -                    ^ Object does not exist (TPME)

./dsdt_fixed.txt   327:         GTF0,   56, 
Error    4063 -                    ^ Object does not exist (GTF0)

./dsdt_fixed.txt   328:         GTF2,   56, 
Error    4063 -                    ^ Object does not exist (GTF2)

./dsdt_fixed.txt   329:         IDEM,   8, 
Error    4063 -                    ^ Object does not exist (IDEM)

./dsdt_fixed.txt   330:         GTF1,   56, 
Error    4063 -                    ^ Object does not exist (GTF1)

./dsdt_fixed.txt   332:         ASLB,   32, 
Error    4063 -                    ^ Object does not exist (ASLB)

./dsdt_fixed.txt   333:         IBTT,   8, 
Error    4063 -                    ^ Object does not exist (IBTT)

./dsdt_fixed.txt   334:         IPAT,   8, 
Error    4063 -                    ^ Object does not exist (IPAT)

./dsdt_fixed.txt   335:         ITVF,   8, 
Error    4063 -                    ^ Object does not exist (ITVF)

./dsdt_fixed.txt   336:         ITVM,   8, 
Error    4063 -                    ^ Object does not exist (ITVM)

./dsdt_fixed.txt   337:         IPSC,   8, 
Error    4063 -                    ^ Object does not exist (IPSC)

./dsdt_fixed.txt   338:         IBLC,   8, 
Error    4063 -                    ^ Object does not exist (IBLC)

./dsdt_fixed.txt   339:         IBIA,   8, 
Error    4063 -                    ^ Object does not exist (IBIA)

./dsdt_fixed.txt   340:         ISSC,   8, 
Error    4063 -                    ^ Object does not exist (ISSC)

./dsdt_fixed.txt   341:         I409,   8, 
Error    4063 -                    ^ Object does not exist (I409)

./dsdt_fixed.txt   342:         I509,   8, 
Error    4063 -                    ^ Object does not exist (I509)

./dsdt_fixed.txt   343:         I609,   8, 
Error    4063 -                    ^ Object does not exist (I609)

./dsdt_fixed.txt   344:         I709,   8, 
Error    4063 -                    ^ Object does not exist (I709)

./dsdt_fixed.txt   345:         IDMM,   8, 
Error    4063 -                    ^ Object does not exist (IDMM)

./dsdt_fixed.txt   346:         IDMS,   8, 
Error    4063 -                    ^ Object does not exist (IDMS)

./dsdt_fixed.txt   347:         IF1E,   8, 
Error    4063 -                    ^ Object does not exist (IF1E)

./dsdt_fixed.txt   348:         HVCO,   8, 
Error    4063 -                    ^ Object does not exist (HVCO)

./dsdt_fixed.txt   349:         NXD1,   32, 
Error    4063 -                    ^ Object does not exist (NXD1)

./dsdt_fixed.txt   350:         NXD2,   32, 
Error    4063 -                    ^ Object does not exist (NXD2)

./dsdt_fixed.txt   351:         NXD3,   32, 
Error    4063 -                    ^ Object does not exist (NXD3)

./dsdt_fixed.txt   352:         NXD4,   32, 
Error    4063 -                    ^ Object does not exist (NXD4)

./dsdt_fixed.txt   353:         NXD5,   32, 
Error    4063 -                    ^ Object does not exist (NXD5)

./dsdt_fixed.txt   354:         NXD6,   32, 
Error    4063 -                    ^ Object does not exist (NXD6)

./dsdt_fixed.txt   355:         NXD7,   32, 
Error    4063 -                    ^ Object does not exist (NXD7)

./dsdt_fixed.txt   356:         NXD8,   32
Error    4063 -                    ^ Object does not exist (NXD8)

./dsdt_fixed.txt   359:     Name (DSEN, One)
Error    4063 -                      ^ Object does not exist (DSEN)

./dsdt_fixed.txt   360:     Name (ECON, Zero)
Error    4063 -                      ^ Object does not exist (ECON)

./dsdt_fixed.txt   361:     Name (GPIC, Zero)
Error    4063 -                      ^ Object does not exist (GPIC)

./dsdt_fixed.txt   362:     Name (CTYP, Zero)
Error    4063 -                      ^ Object does not exist (CTYP)

./dsdt_fixed.txt   363:     Name (L01C, Zero)
Error    4063 -                      ^ Object does not exist (L01C)

./dsdt_fixed.txt   364:     Name (VFN0, Zero)
Error    4063 -                      ^ Object does not exist (VFN0)

./dsdt_fixed.txt   365:     Name (VFN1, Zero)
Error    4063 -                      ^ Object does not exist (VFN1)

./dsdt_fixed.txt   368:         Method (_L01, 0, NotSerialized)
Error    4063 -      Object does not exist ^  (_L01)

./dsdt_fixed.txt   370:             Add (L01C, One, L01C)
Error    4063 -       Object does not exist ^  (L01C)

./dsdt_fixed.txt   370:             Add (L01C, One, L01C)
Error    4063 -                  Object does not exist ^  (L01C)

./dsdt_fixed.txt   371:             P8XH (Zero, One)
Error    4063 -  Object does not exist ^  (P8XH)

./dsdt_fixed.txt   372:             P8XH (One, L01C)
Error    4063 -  Object does not exist ^  (P8XH)

./dsdt_fixed.txt   372:             P8XH (One, L01C)
Error    4063 -             Object does not exist ^  (L01C)

./dsdt_fixed.txt   373:             If (LAnd (LEqual (RP1D, Zero), \_SB.PCI0.RP01.HPSX))
Error    4063 -                    Object does not exist ^  (RP1D)

./dsdt_fixed.txt   373:             If (LAnd (LEqual (RP1D, Zero), \_SB.PCI0.RP01.HPSX))
Error    4063 -                                                Object does not exist ^  (\_SB.PCI0.RP01.HPSX)

./dsdt_fixed.txt   376:                 If (\_SB.PCI0.RP01.PDCX)
Error    4063 -                         Object does not exist ^  (\_SB.PCI0.RP01.PDCX)

./dsdt_fixed.txt   378:                     Store (One, \_SB.PCI0.RP01.PDCX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP01.PDCX)

./dsdt_fixed.txt   379:                     Store (One, \_SB.PCI0.RP01.HPSX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP01.HPSX)

./dsdt_fixed.txt   380:                     Notify (\_SB.PCI0.RP01, Zero)
Error    4063 -                            Object does not exist ^  (\_SB.PCI0.RP01)

./dsdt_fixed.txt   384:                     Store (One, \_SB.PCI0.RP01.HPSX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP01.HPSX)

./dsdt_fixed.txt   388:             If (LAnd (LEqual (RP2D, Zero), \_SB.PCI0.RP02.HPSX))
Error    4063 -                    Object does not exist ^  (RP2D)

./dsdt_fixed.txt   388:             If (LAnd (LEqual (RP2D, Zero), \_SB.PCI0.RP02.HPSX))
Error    4063 -                                                Object does not exist ^  (\_SB.PCI0.RP02.HPSX)

./dsdt_fixed.txt   391:                 If (\_SB.PCI0.RP02.PDCX)
Error    4063 -                         Object does not exist ^  (\_SB.PCI0.RP02.PDCX)

./dsdt_fixed.txt   393:                     Store (One, \_SB.PCI0.RP02.PDCX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP02.PDCX)

./dsdt_fixed.txt   394:                     Store (One, \_SB.PCI0.RP02.HPSX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP02.HPSX)

./dsdt_fixed.txt   395:                     Notify (\_SB.PCI0.RP02, Zero)
Error    4063 -                            Object does not exist ^  (\_SB.PCI0.RP02)

./dsdt_fixed.txt   399:                     Store (One, \_SB.PCI0.RP02.HPSX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP02.HPSX)

./dsdt_fixed.txt   403:             If (LAnd (LEqual (RP3D, Zero), \_SB.PCI0.RP03.HPSX))
Error    4063 -                    Object does not exist ^  (RP3D)

./dsdt_fixed.txt   403:             If (LAnd (LEqual (RP3D, Zero), \_SB.PCI0.RP03.HPSX))
Error    4063 -                                                Object does not exist ^  (\_SB.PCI0.RP03.HPSX)

./dsdt_fixed.txt   406:                 If (\_SB.PCI0.RP03.PDCX)
Error    4063 -                         Object does not exist ^  (\_SB.PCI0.RP03.PDCX)

./dsdt_fixed.txt   408:                     Store (One, \_SB.PCI0.RP03.PDCX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP03.PDCX)

./dsdt_fixed.txt   409:                     Store (One, \_SB.PCI0.RP03.HPSX)
Error    4063 -                                     Object does not exist ^  (\_SB.PCI0.RP03.HPSX)

./dsdt_fixed.txt  4008:                         Return (Package (0x00) {})
Remark   5071 -                Effective AML package length is zero ^ 


Maximum error count (200) exceeded
ASL Input:  ./dsdt_fixed.txt - 6346 lines, 212590 bytes, 2447 keywords
Compilation complete. 201 Errors, 0 Warnings, 1 Remarks, 4 Optimizations

```

---

### Post by 67GTA on 2009-08-10
I just got word from the kernel team that the DSDT patch will no longer be used. This is not good. I guess I will have to rewrite the how to so a custom kernel can be compiled with the patch. That is assuming someone continues to update the patch. I am going to voice my opinion. You are welcome to chime in on the mailing list if you want. My laptop won't run Linux without a custom DSDT. My desktop won't wake from suspend without a custom DSDT. I might be S.O.L.

[kernel-team@lists.ubuntu.com]("http://ubuntuforums.org/kernel-team@lists.ubuntu.com")

---

### Post by s0undt3ch on 2009-08-10
> **67GTA said:**
> I just got word from the kernel team that the DSDT patch will no longer be used. This is not good. I guess I will have to rewrite the how to so a custom kernel can be compiled with the patch. That is assuming someone continues to update the patch. I am going to voice my opinion. You are welcome to chime in on the mailing list if you want. My laptop won't run Linux without a custom DSDT. My desktop won't wake from suspend without a custom DSDT. I might be S.O.L.

[kernel-team@lists.ubuntu.com]("http://ubuntuforums.org/kernel-team@lists.ubuntu.com")

What's the thread on [https://lists.ubuntu.com/archives/kernel-team/](https://lists.ubuntu.com/archives/kernel-team/)

---

### Post by 67GTA on 2009-08-10
That's just the channel log for the mailing list discussions.

---

### Post by s0undt3ch on 2009-08-10
> **67GTA said:**
> That's just the channel log for the mailing list discussions.

Yes I know, but instead of creating a new thread(new mail), maybe I could try to respond to the one where you learned that the support for custom DSDT is being dropped.

---

### Post by 67GTA on 2009-08-10
That was a personal email I sent to one of the dev's. I just sent a mail to the mailing list. It will be a couple of days before it shows up. Since I'm not a member of the kernel team, a moderator has to approve the message before it will be seen.

---

### Post by sergiom99 on 2009-08-10
Can we file a bug or something @ launchpad?

---

### Post by Red_Lion on 2009-08-11
Hello! Need help with parsing DSDT.

Some errors was fownd, and we know how fix this. Now need to search 2 buttons and remoute (after starn vista, hibernate it and back it's dead. Not know where search - in i8042 or acpi).

Please see line 4338 - when ECON is == One?
Also - _Q16 on line 4586 and GBBV on 7929 - if i not mistake all events listed in _Q16 missed in GBBV and first can run only if ECON not true (if true GBBV save it to internal and blank)?

Also see please line 8681 QBTN device - how it work?

P.S. it's for tx2* tablets - we missing some buttons and think what they work via acpi - in i8042 in debug empty. DSDT decompiled on link:

[http://ubuntuforums.org/attachment.php?attachmentid=122955&d=1248966592](http://ubuntuforums.org/attachment.php?attachmentid=122955&d=1248966592)

---

### Post by 67GTA on 2009-08-11
I have filed a bug report on launchpad for my machines that are affected. The kernel devs are removing the dsdt patch in order to get more kernel bug reports. The idea is to try and fix the problems we are dealing with in this thread. With 9.10 and on, you will have to compile a custom kernel to use a custom dsdt. I will see if my bugs can be fixed by 9.10. If you want to try the same, create an account here: [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) Once that is done, open a terminal and run ```
ubuntu-bug -p linux
  
``` This will gather all of the needed reports for you and post them after you finish the report. All of the bugs fixed by editing the dsdt are considered kernel bugs. The "linux" package is the kernel. I will still fix dsdt's if you ask or help you figure out what to put in the bug report.

---

### Post by 67GTA on 2009-08-11
Red_Lion:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 18 Optimizations

I fixed a warning that kept the kernel from reading your CPU temps. It should run quieter/cooler. 

[ATTACH]124485[/ATTACH]

---

### Post by sergiom99 on 2009-08-11
OK, submitted bug #412253

---

### Post by Red_Lion on 2009-08-12
About you fixes we know :) We search for buttons...

---

### Post by bela83 on 2009-08-12
Hi 67GTA !
Could you help me fix my dsdt.dsl ? I've begun the work but I don't know what to do with the warnings...
Thanks

---

### Post by 67GTA on 2009-08-12
bela83:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 748 Optimizations

[ATTACH]124657[/ATTACH]

---

### Post by cespinal on 2009-08-13
Hello to everyone (specially to our savior) 

I am having the exact same problems. I need help with my dsdt file getting fixed :(. 

I also have a question, Laptop fan is off, will a new dsdt fix that? im running Ubuntu on a HP dv9000

thank very much 67gta!

---

### Post by alex.pancescu on 2009-08-13
hello all,
could you help me please with a recompiled dsdt file?
here is the original...
thank you

---

### Post by 67GTA on 2009-08-13
> **cespinal said:**
> Hello to everyone (specially to our savior) 

I am having the exact same problems. I need help with my dsdt file getting fixed :(. 

I also have a question, Laptop fan is off, will a new dsdt fix that? im running Ubuntu on a HP dv9000

thank very much 67gta!

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 1130 Optimizations

I fixed errors in the temp section. This should help with temp/fan. I also fixed error in the section that controls waking from sleep/hibernate. 

[ATTACH]124754[/ATTACH]

---

### Post by 67GTA on 2009-08-13
> **alex.pancescu said:**
> hello all,
could you help me please with a recompiled dsdt file?
here is the original...
thank you

The one you attached here is the original? It says every piece of hardware in you PC doesn't exist.

---

### Post by cespinal on 2009-08-13
Whoa!, for the first time since I got hooked with linux, my laptop is 99% functional!! thank you very much!

next (and last) issue to resolve: sound capture!

---

### Post by 67GTA on 2009-08-13
> **cespinal said:**
> Whoa!, for the first time since I got hooked with linux, my laptop is 99% functional!! thank you very much!

next (and last) issue to resolve: sound capture!

Good luck with that! I've owned two HP dv laptops, and have not gotten sound capture to work yet. The alsa drivers just doesn't support them yet.

---

### Post by alex.pancescu on 2009-08-14
> **67GTA said:**
> The one you attached here is the original? It says every piece of hardware in you PC doesn't exist.
yes, it is the original file, will try later to send it again
my pc is a custom built rig, amd athlon x2 5600, mb asus m3a-h/hdmi, ati radeon 3870
it works fairly well, but it is very loud, all coolers are spinning like crazy
/proc/acpi/fan and /proc/acpi/thermal_zone are not populated

---

### Post by bela83 on 2009-08-14
It works like a charm now ! Thanks !
Hope the community will find a solution for Karmic though...

---

### Post by kage52124 on 2009-08-14
Hello 67GTA, I was wondering if I too could receive some assistance...  for anyone doing a search my laptop is a hp pavilion dv5 1235dx.

```
 Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/kage52124/dsdt.dsl  1379:             Method (_HOT, 0, Serialized)
Warning  1087 -   Not all control paths return a value ^  (_HOT)

/home/kage52124/dsdt.dsl  1379:             Method (_HOT, 0, Serialized)
Warning  1080 -    Reserved method must return a value ^  (_HOT)

/home/kage52124/dsdt.dsl  1405:             Method (_CRT, 0, Serialized)
Warning  1087 -   Not all control paths return a value ^  (_CRT)

/home/kage52124/dsdt.dsl  1405:             Method (_CRT, 0, Serialized)
Warning  1080 -    Reserved method must return a value ^  (_CRT)

/home/kage52124/dsdt.dsl  1463:             Method (_PSV, 0, NotSerialized)
Warning  1087 -   Not all control paths return a value ^  (_PSV)

/home/kage52124/dsdt.dsl  1463:             Method (_PSV, 0, NotSerialized)
Warning  1080 -    Reserved method must return a value ^  (_PSV)

/home/kage52124/dsdt.dsl  6554:                         Name (_T_0, Zero)
Remark   5110 -                    Use of compiler reserved name ^  (_T_0)

/home/kage52124/dsdt.dsl  6596:                         Name (_T_0, Zero)
Remark   5110 -                    Use of compiler reserved name ^  (_T_0)

/home/kage52124/dsdt.dsl  8027:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -           Not all control paths return a value ^  (_GTM)

/home/kage52124/dsdt.dsl  8027:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -            Reserved method must return a value ^  (_GTM)

/home/kage52124/dsdt.dsl  8187:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -               Not all control paths return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  8187:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                Reserved method must return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  8255:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -               Not all control paths return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  8255:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                Reserved method must return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  8328:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -           Not all control paths return a value ^  (_GTM)

/home/kage52124/dsdt.dsl  8328:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -            Reserved method must return a value ^  (_GTM)

/home/kage52124/dsdt.dsl  8488:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -               Not all control paths return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  8488:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                Reserved method must return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  8556:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -               Not all control paths return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  8556:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                Reserved method must return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  8661:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -           Not all control paths return a value ^  (_GTM)

/home/kage52124/dsdt.dsl  8661:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -            Reserved method must return a value ^  (_GTM)

/home/kage52124/dsdt.dsl  8821:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -               Not all control paths return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  8821:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                Reserved method must return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  8889:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -               Not all control paths return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  8889:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                Reserved method must return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  8962:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -           Not all control paths return a value ^  (_GTM)

/home/kage52124/dsdt.dsl  8962:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -            Reserved method must return a value ^  (_GTM)

/home/kage52124/dsdt.dsl  9122:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -               Not all control paths return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  9122:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                Reserved method must return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  9190:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -               Not all control paths return a value ^  (_GTF)

/home/kage52124/dsdt.dsl  9190:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                Reserved method must return a value ^  (_GTF)

/home/kage52124/dsdt.dsl 10072:                 Store (Package (0x02)
Warning  1099 -                     Statement is unreachable ^ 

ASL Input:  /home/kage52124/dsdt.dsl - 11650 lines, 409530 bytes, 5631 keywords
AML Output: /home/kage52124/dsdt.aml - 47460 bytes, 968 named objects, 4663 executable opcodes

Compilation complete. 0 Errors, 31 Warnings, 2 Remarks, 40 Optimizations 
```My apologies for there being so MANY errors :-(

Thank you so much for your time everyone!

EDIT: Uploaded correct zip file....whoops :-P

---

### Post by 67GTA on 2009-08-14
kage52124:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 56 Optimizations

[ATTACH]124907[/ATTACH]

---

### Post by kage52124 on 2009-08-14
Well after following the howto after putting the dsdt.aml in the home directory and running all the commands, finding the similar lines in the dmesg and adding ```
 acpi_osi="Linux" 
``` into menu.lst, I still am unable to find anything in the /proc/acpi/fan and /proc/acpi/thermal_zone directories.  I'm rather bummed, standby still does not function and my fans still don't run.  Would y'all happen to have any other ideas?

Also, thank you for the dsdt.aml compilation, I was quite giddy when I saw you had done it so soon.

Kage

---

### Post by nickf1195 on 2009-08-16
Surprise, 67GTA (or anyone else that knows this stuff)!

Another buggy DSDT for you! I've been having some of the same issues and am hoping the DSDT is what's causing them so I can fix it soon. If you could take a quick look at it, I'd really appreciate it. There are only 2 errors and 3 warnings, so it shouldn't be too bad.

Thanks for your time.

---

### Post by kage52124 on 2009-08-16
Update! Looks like my google searching wasn't very good, I've found out what was wrong with my standby/resume feature.  Go here: ```
 [http://h30434.www3.hp.com/psg/board/message?board.id=Hardware&thread.id=9394&view=by_date_ascendingpage=1]("http://h30434.www3.hp.com/psg/board/message?board.id=Hardware&thread.id=9394&view=by_date_ascending&page=1") 
``` to read a thread on the HP forums about the bad BIOS that affects HP dv5 and other similar models.  There was a BIOS update that will fix the standby/resume issues in Ubuntu and other Linux OS.

If you own a DV5 or similar laptop, do _**NOT **_use this procedure first!  After I flashed my BIOS and returned to Ubuntu (I flashed it from Vista), it still did not resume properly, but the computer would fall into standby much easier.  If you already have done the procedure listed here and haven't deleted your original dsdt.aml like I did, then use the old one in the same process to put your old settings back in place, then try and see if standby/resume works properly.  In my case, I had to reformat the partition and reinstall :-(.

I hope this is helpful to anyone and a big thanks to 67GTA for the help!

-Kage

---

### Post by 67GTA on 2009-08-16
You don't have to go to that extreme. You can simply delete the custom dsdt.aml in /etc/initramfs-tools and update the initrd image again with the update-initramfs command this will revert everything back to before the steps you took in the how to. Your original dsdt is hard coded in to your bios and can not be removed. We were simply bypassing it and telling the OS to use the custom one.

---

### Post by Harper45 on 2009-08-16
here is code;
   	Code:
 	0.004000] ACPI: Core revision 20080926
[    0.006886] ACPI: Checking initramfs for custom DSDT
[    0.443822] ACPI: Found DSDT in DSDT.aml.
[    0.443828] ACPI: Override [DSDT-CRESTLNE], this is unsafe: tainting kernel
[    0.443834] ACPI: Table DSDT replaced by host OS
[    0.443838] ACPI: DSDT 00000000, 887E (r2 INTEL  CRESTLNE  6040000 INTL 20081204)
[    0.443843] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"
[    0.452055] Setting APIC routing to flat

---

### Post by 67GTA on 2009-08-16
> **Harper45 said:**
> here is code;
       Code:
     0.004000] ACPI: Core revision 20080926
[    0.006886] ACPI: Checking initramfs for custom DSDT
[    0.443822] ACPI: Found DSDT in DSDT.aml.
[    0.443828] ACPI: Override [DSDT-CRESTLNE], this is unsafe: tainting kernel
[    0.443834] ACPI: Table DSDT replaced by host OS
[    0.443838] ACPI: DSDT 00000000, 887E (r2 INTEL  CRESTLNE  6040000 INTL 20081204)
[    0.443843] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"
[    0.452055] Setting APIC routing to flat

That means the custom DSDT is being used.

---

### Post by walterav on 2009-08-17
Hi 67GTA,

I have a "Asus p5ke wifi ap bios 1202", and I'm unable to suspend to ram in ubuntu 9.04 i386/64, the system stays powered on and the monitor goes black when going to suspend. So I have to HARD reset to continue working.

When I'm in ubuntu 9.10 alpha 3 i386/64, the system suspends and wakes! But just one strange bug, It will not restart after sleep, It just hangs at a black screen. 
So restart after sleep is an issue with 9.10 alpha 3.

Strange thing is, running osx86 on my machine "which is ofcourse out of the scope of this forum" is also able to suspend to ram on this machine and wake succesfully, but also the same bug. 
It will not restart after sleep it also hangs at the same black screen "as ubuntu 9.10alpa 3", just before the pc speaker beep has to arrive and show the bios and post screen. It never restarts after sleep.

Sleep after sleep works and it wakes to...

Do you have any hint where it can be found in the dsdt? I will attach the following.

attachments:
dsdt / dmesg / lsusb / lspci / lshw

---

### Post by Fox McCloud on 2009-08-17
Hey 67GTA! I'm so glad someone knows what causes this problem. I followed the how-to the point where I disasemble the DSDT file. At that point you say I can edit it...but I don't know exactly what I'm doing at that point. 

I did the next step and got this:```
/home/alex/dsdt.dsl  1170:             Method (FRSP, 0, NotSerialized)
Warning  1087 -                                   ^ Not all control paths return a value (FRSP)

/home/alex/dsdt.dsl  1206:             Method (_PSV, 0, Serialized)
Warning  1087 -                                   ^ Not all control paths return a value (_PSV)

/home/alex/dsdt.dsl  1206:             Method (_PSV, 0, Serialized)
Warning  1080 -                                   ^ Reserved method must return a value (_PSV)

/home/alex/dsdt.dsl  4213:                             Method (WMAB, 3, NotSerialized)
Warning  1087 -              Not all control paths return a value ^  (WMAB)

ASL Input:  /home/<user>/dsdt.dsl - 9696 lines, 378733 bytes, 3618 keywords
AML Output: /home/<user>/dsdt.aml - 42129 bytes, 780 named objects, 2838 executable opcodes

Compilation complete. 0 Errors, 4 Warnings, 0 Remarks, 37 Optimizations
```

I'm not sure what to do with these warnings. :(

A quick rundown of the issues I have is the fan will not increase speed when the temps rise.
The laptop will sometimes will not come out of sleep, and will not always shutdown correctly.

I attached the DSDT.dsl file. I thank you for sticking around and helping us with this issue. ^-^

---

### Post by 67GTA on 2009-08-18
[walterav]("http://ubuntuforums.org/member.php?u=450091"):

Try this one. Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 50 Optimizations. It will also work with Mac. 

[ATTACH]125405[/ATTACH]

---

### Post by 67GTA on 2009-08-18
Fox McCloud:

[ATTACH]125406[/ATTACH]

---

### Post by 67GTA on 2009-08-18
nickf1195:

I can't get yours to compile. It exceeds 200 errors. You might try posting it again. This one is no good.

---

### Post by for.i.am.root on 2009-08-19
> **67GTA said:**
> stephen.mann:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 1130 Optimizations

Your was exactly like sergiom99's. Fixed wake from sleep/hibernate, temp readings, and CPU tweaks. Should run quieter/cooler.


[ATTACH]119111[/ATTACH]

Just wanted to let everyone know that this one also worked for my HP DV6700z.

I have been struggling with my suspend and hibernate for about 6 months now.

Huge lifesaver 67GTA!!

By the way , coupe or fastback?

---

### Post by 67GTA on 2009-08-19
Fastback:guitar:

---

### Post by Fox McCloud on 2009-08-20
> **67GTA said:**
> Fox McCloud:

[ATTACH]125406[/ATTACH]
Sorry, been a little busy. >.>

Just want to that it worked! Thanks so much for the help! :)

---

### Post by walterav on 2009-08-21
> **67GTA said:**
> [walterav]("http://ubuntuforums.org/member.php?u=450091"):

Try this one. Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 50 Optimizations. It will also work with Mac. 

[ATTACH]125405[/ATTACH]

67GTA thanks for patching the dsdt.aml

I tried it in ubuntu 9.04 amd64, and did the following to install:
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
sudo update-initramfs -u -k kernel-version
After reboot I checked dmesg and it said it has been replaced.

Problem:
When pressing suspend, the system still hangs at a black screen with a small white blinking cursor and the power stays on.

Any suggestions? I will try it later at osx today

Do I have to look for a specific thing you fixed so I can test it? Sleep/restart after sleep?

---

### Post by 67GTA on 2009-08-21
> **walterav said:**
> 67GTA thanks for patching the dsdt.aml

I tried it in ubuntu 9.04 amd64, and did the following to install:
sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml
sudo update-initramfs -u -k kernel-version
After reboot I checked dmesg and it said it has been replaced.

Problem:
When pressing suspend, the system still hangs at a black screen with a small white blinking cursor and the power stays on.

Any suggestions? I will try it later at osx today

Do I have to look for a specific thing you fixed so I can test it? Sleep/restart after sleep?

You probably need to file a bug.

---

### Post by nickf1195 on 2009-08-24
[COLOR=#000000]?Ä[/COLOR]

---

### Post by nickf1195 on 2009-08-24
?Ä

---

### Post by cehjohnson on 2009-08-27
This is a fascinating issue and one that i wasn't aware of before. I was expecting to get the normal bugs when running this under Debian, but instead got a one line message: 'Segmentation fault'. What's all that about?

---

### Post by 67GTA on 2009-08-27
> **nickf1195 said:**
> I'd really appreciate it if you gave it one more try. Here's another one straight from /proc/acpi/dsdt.

Thanks for your time.

Nick

There is still some stuff missing at the top of the file. Send me the dsdt.dat instead of dsdt.dsl, and I will try to decode it to see if I get the same errors.

---

### Post by 67GTA on 2009-08-27
> **cehjohnson said:**
> This is a fascinating issue and one that i wasn't aware of before. I was expecting to get the normal bugs when running this under Debian, but instead got a one line message: 'Segmentation fault'. What's all that about?

There were a couple of iasl versions that had this bug. You might try installing a newer version.

---

### Post by Squirrel E. Doom on 2009-08-31
I have read this thread as closely as I could with a damaged brain from reading this thread as closely as I could. From what I gather, I have no idea what's going on. I have a Toshiba Satellite L305-S5909 and "iasl -d dsdt.dat" gives me "Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 39 Optimizations".

From what I gather this should be a good thing? However no fan or at least insufficient CPU fan activity as this thing keeps shutting down due to heat when I do things that make it think. Is this just a sign that the computer has become so aware of me that it can mimic my physical behaviour?. It seems like since noticing this problem and trying to find a solution to it I have been doing the same thing. However both my PC and myself have been awake long enough now to write this so I would like to take the opportunity before one of us passes out again to plead for help. *


* Please help me I am dying. Thank you.

P.S.
I am ubernoob. 

Also tried the toshutils and toshset. Seems they are installed but I can't do anything with them. 

OOOOOH OOOOOH OOOOH OOOOOH! and while I'm at it the computer wont stay on unless it's plugged into the wall....... Other than that its great.

---

### Post by 67GTA on 2009-09-01
Toshiba's are notorious for ACPI problems with Linux. That's why the toshet scripts were written. Try booting with "acpi=force" for example, or one of the other options here one at a time:

force -- enable ACPI if default was off
off -- disable ACPI if default was on (same as noacpi)
noirq -- do not use ACPI for IRQ routing
ht -- run only enough ACPI to enable Hyper Threading
strict -- Be less tolerant of platforms that are not strictly ACPI specification compliant.

If none of these help, I would file a bug against the kernel.

---

### Post by cespinal on 2009-09-02
Hey guys!! I am having a couple of small issues here, just want to check put if the have something to do with DSDT file

First: when system is resuming from suspend, the system shows the desktop and all applications, takes some seconds to boot, some more seconds to get online, and AFTER all that, the login windows appears, asking for the password as usual!!. Shoulndt this window show up first before everything? how could I fix that?

Second: sometimes I turn off the computer, and when I turn it on again and the system boots, all the windows and applications I left open are back again!... looks like the RAM is not being emptied when I shut down the system.

thanks again for your time and patience :D 
cheers.

---

### Post by scaine on 2009-09-03
> **cespinal said:**
>  First: when system is resuming from suspend, the system shows the desktop and all applications, takes some seconds to boot, some more seconds to get online, and AFTER all that, the login windows appears, asking for the password as usual!!. Shoulndt this window show up first before everything? how could I fix that?

I'm no expert, but this doesn't sound DSDT related.  And yes, when you resume, unless you have modified your settings via gconf-editor for gnome-power-manager, you should be prompted for a password on resume.  First thing I turn off, personally.

> **cespinal said:**
>  Second: sometimes I turn off the computer, and when I turn it on again and the system boots, all the windows and applications I left open are back again!... looks like the RAM is not being emptied when I shut down the system.

This is a gnome feature in System/Preferences/Startup Applications.  Click on the options tab, then untick "Automatically remember running applications when logging out".

---

### Post by nicholasblock on 2009-09-08
I have spent a long time trying to fix my dsdt and I thought I would stop here for help. I started with over 200 errors and I now have it down to 55 I would really really appreciate some help please.

Also if anymore information is needed please let me know and I will get it up asap
Thanks

---

### Post by 67GTA on 2009-09-08
> **nicholasblock said:**
> I have spent a long time trying to fix my dsdt and I thought I would stop here for help. I started with over 200 errors and I now have it down to 55 I would really really appreciate some help please.

Also if anymore information is needed please let me know and I will get it up asap
Thanks

Send me a fresh copy of your dsdt.dsl file without any changes, and I will take a look.

---

### Post by nicholasblock on 2009-09-08
Thank you very much for taking the time to look at it. It originally returns over 200 errors but I got it down to 55 and now there is just so much and I do not understand dsdt that well. My board is a Asus M3A79-T Deluxe with an AMD Phenom II 940 CPU. If you need more info please let me know.

---

### Post by 67GTA on 2009-09-09
> **nicholasblock said:**
> Thank you very much for taking the time to look at it. It originally returns over 200 errors but I got it down to 55 and now there is just so much and I do not understand dsdt that well. My board is a Asus M3A79-T Deluxe with an AMD Phenom II 940 CPU. If you need more info please let me know.

Is this a custom system? There are a lot of objects that don't exist. I had it down to 2 errors, took out the last "}", and had 178 errors. This one might be a lost cause. I'll keep working on it.

---

### Post by nicholasblock on 2009-09-09
Yeah this is custom here's my specs:
Motherboard- Asus M3A79-t Deluxe
CPU- AMD Phenom II 940
Memory- Kingston HyperX T1 2x2 gigs 1066Mhz
Hard drives- 2 500 gig seagate 1 160 gig Excellstore
CD/DVD Burner- Lit-on
PSU- Corsair 750 watt
Video Cards- 2 XFX 4850's

I really appreciate you taking your time to look at this. I hope its not a lost cause. If you can not get it could you please send me the one wit two errors? Thank you so much.

---

### Post by 67GTA on 2009-09-09
The reason there are so many errors, is because the original dsdt is pointing to hardware that is no longer there. Are you having any problems that you think may be related? If the operating system is finding and configuring the current hardware okay, then fixing the dsdt errors won't do anything. Post the output of ```
sudo lspci
``` and ```
sudo dmesg
```

---

### Post by nicholasblock on 2009-09-09
I have been having a lot of problems like shutdown freezes, graphics problems, and a few others. I dont understand cause I just updated my BIOS a few days ago and nothing has changed since then. I messed up my ubuntu install so I am forced to use windows til I get this mess figured out. I booted into an old slax I had laying around to get you this info but if you need any thing else please dont hasitate to ask.
Thanks



lspci
```
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9442
01:00.1 Audio device: ATI Technologies Inc Unknown device aa30
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:08.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)


```
dmesg
```
Linux version 2.6.24.4 (root@slax) (gcc version 4.2.3) #1 SMP Mon Mar 31 08:38:11 GMT 2008
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 00000000cffb0000 (usable)
 BIOS-e820: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
 BIOS-e820: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
 BIOS-e820: 00000000cffe0000 - 00000000d0000000 (reserved)
 BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
 BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
Warning only 4GB will be used.
Use a HIGHMEM64G enabled kernel.
3200MB HIGHMEM available.
896MB LOWMEM available.
found SMP MP-table at 000ff780
Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
Zone PFN ranges:
  DMA             0 ->     4096
  Normal       4096 ->   229376
  HighMem    229376 ->  1048576
Movable zone start PFN for each node
early_node_map[1] active PFN ranges
    0:        0 ->  1048576
On node 0 totalpages: 1048576
  DMA zone: 32 pages used for memmap
  DMA zone: 0 pages reserved
  DMA zone: 4064 pages, LIFO batch:0
  Normal zone: 1760 pages used for memmap
  Normal zone: 223520 pages, LIFO batch:31
  HighMem zone: 6400 pages used for memmap
  HighMem zone: 812800 pages, LIFO batch:31
  Movable zone: 0 pages used for memmap
DMI present.
ACPI: RSDP 000F9F00, 0024 (r2 ACPIAM)
ACPI: XSDT CFFB0100, 004C (r1 082009 OEMXSDT  20090820 MSFT       97)
ACPI: FACP CFFB0290, 00F4 (r3 082009 OEMFACP  20090820 MSFT       97)
ACPI: DSDT CFFB0440, B322 (r1  P0024 P0024000        0 INTL 20051117)
ACPI: FACS CFFBE000, 0040
ACPI: APIC CFFB0390, 006C (r1 082009 OEMAPIC  20090820 MSFT       97)
ACPI: MCFG CFFB0400, 003C (r1 082009 OEMMCFG  20090820 MSFT       97)
ACPI: OEMB CFFBE040, 0071 (r1 082009 AMI_OEM  20090820 MSFT       97)
ACPI: HPET CFFBB770, 0038 (r1 082009 OEMHPET  20090820 MSFT       97)
ATI board detected. Disabling timer routing over 8254.
ACPI: PM-Timer IO Port: 0x808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Processor #0 0:4 APIC version 16
ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Processor #1 0:4 APIC version 16
ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Processor #2 0:4 APIC version 16
ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Processor #3 0:4 APIC version 16
ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
ACPI: HPET id: 0x8300 base: 0xfed00000
Using ACPI (MADT) for SMP configuration information
Allocating PCI resources starting at d4000000 (gap: d0000000:2ff00000)
swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1040384
Kernel command line: initrd=/boot/initrd.gz ramdisk_size=6666 root=/dev/ram0 rw autoexec=xconf;telinit~4 changes=/slax/ BOOT_IMAGE=/boot/vmlinuz
mapped APIC to ffffb000 (fee00000)
mapped IOAPIC to ffffa000 (fec00000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 16384 bytes)
Detected 3010.260 MHz processor.
Console: colour VGA+ 80x25
console [tty0] enabled
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 3361440k/4194304k available (6267k kernel code, 45016k reserved, 2011k data, 384k init, 2490048k highmem)
virtual kernel memory layout:
    fixmap  : 0xffe14000 - 0xfffff000   (1964 kB)
    pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
    vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
    lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
      .init : 0xc091f000 - 0xc097f000   ( 384 kB)
      .data : 0xc071edca - 0xc0915d5c   (2011 kB)
      .text : 0xc0100000 - 0xc071edca   (6267 kB)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
hpet clockevent registered
Calibrating delay using timer specific routine.. 6024.82 BogoMIPS (lpj=12049648)
Security Framework initialized
Capability LSM initialized
Mount-cache hash table entries: 512
CPU: After generic identify, caps: 178bfbff efd3fbff 00000000 00000000 00802009 00000000 000037ff 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU 0(4) -> Core 0
CPU: After all inits, caps: 178bfbff efd3fbff 00000000 00000510 00802001 00000000 000037ff 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
Compat vDSO mapped to ffffe000.
Checking 'hlt' instruction... OK.
SMP alternatives: switching to UP code
ACPI: Core revision 20070126
CPU0: AMD Phenom(tm) II X4 940 Processor stepping 02
SMP alternatives: switching to SMP code
Booting processor 1/1 eip 3000
Initializing CPU#1
Calibrating delay using timer specific routine.. 6020.62 BogoMIPS (lpj=12041240)
CPU: After generic identify, caps: 178bfbff efd3fbff 00000000 00000000 00802009 00000000 000037ff 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU 1(4) -> Core 1
CPU: After all inits, caps: 178bfbff efd3fbff 00000000 00000510 00802001 00000000 000037ff 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#1.
CPU1: AMD Phenom(tm) II X4 940 Processor stepping 02
SMP alternatives: switching to SMP code
Booting processor 2/2 eip 3000
Initializing CPU#2
Calibrating delay using timer specific routine.. 6020.59 BogoMIPS (lpj=12041183)
CPU: After generic identify, caps: 178bfbff efd3fbff 00000000 00000000 00802009 00000000 000037ff 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU 2(4) -> Core 2
CPU: After all inits, caps: 178bfbff efd3fbff 00000000 00000510 00802001 00000000 000037ff 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#2.
CPU2: AMD Phenom(tm) II X4 940 Processor stepping 02
SMP alternatives: switching to SMP code
Booting processor 3/3 eip 3000
Initializing CPU#3
Calibrating delay using timer specific routine.. 6020.65 BogoMIPS (lpj=12041312)
CPU: After generic identify, caps: 178bfbff efd3fbff 00000000 00000000 00802009 00000000 000037ff 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU 3(4) -> Core 3
CPU: After all inits, caps: 178bfbff efd3fbff 00000000 00000510 00802001 00000000 000037ff 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#3.
CPU3: AMD Phenom(tm) II X4 940 Processor stepping 02
Total of 4 processors activated (24086.69 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Brought up 4 CPUs
net_namespace: 64 bytes
xor: automatically using best checksumming function: pIII_sse
   pIII_sse  : 12197.000 MB/sec
xor: using function: pIII_sse (12197.000 MB/sec)
NET: Registered protocol family 16
No dock devices found.
ACPI: bus type pci registered
PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
PCI: Not using MMCONFIG.
PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
PCI: Using configuration type 1
Setting up standard PCI resources
mtrr: your CPUs had inconsistent fixed MTRR settings
mtrr: probably your BIOS does not setup all CPUs.
mtrr: corrected configuration.
ACPI: EC: Look up EC in DSDT
ACPI: Interpreter enabled
ACPI: (supports S0 S1 S3 S4 S5)
ACPI: Using IOAPIC for interrupt routing
Error attaching device data
Error attaching device data
Error attaching device data
Error attaching device data
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: Transparent bridge - 0000:00:14.4
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 4 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  AB, should be A2 [20070126]
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
ACPI: bus type pnp registered
pnp: PnP ACPI: found 15 devices
ACPI: ACPI bus type pnp unregistered
SCSI subsystem initialized
libata version 3.00 loaded.
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
PCI: Cannot allocate resource region 3 of device 0000:00:00.0
Time: hpet clocksource has been installed.
system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
system 00:0a: ioport range 0x40b-0x40b has been reserved
system 00:0a: ioport range 0x4d6-0x4d6 has been reserved
system 00:0a: ioport range 0xc00-0xc01 has been reserved
system 00:0a: ioport range 0xc14-0xc14 has been reserved
system 00:0a: ioport range 0xc50-0xc51 has been reserved
system 00:0a: ioport range 0xc52-0xc52 has been reserved
system 00:0a: ioport range 0xc6c-0xc6c has been reserved
system 00:0a: ioport range 0xc6f-0xc6f has been reserved
system 00:0a: ioport range 0xcd0-0xcd1 has been reserved
system 00:0a: ioport range 0xcd2-0xcd3 has been reserved
system 00:0a: ioport range 0xcd4-0xcd5 has been reserved
system 00:0a: ioport range 0xcd6-0xcd7 has been reserved
system 00:0a: ioport range 0xcd8-0xcdf has been reserved
system 00:0a: ioport range 0x800-0x89f has been reserved
system 00:0a: ioport range 0xb00-0xb3f has been reserved
system 00:0a: ioport range 0x900-0x90f has been reserved
system 00:0a: ioport range 0x910-0x91f has been reserved
system 00:0a: ioport range 0xfe00-0xfefe has been reserved
system 00:0a: iomem range 0xffb80000-0xffbfffff has been reserved
system 00:0a: iomem range 0xfec10000-0xfec1001f has been reserved
system 00:0c: ioport range 0xe00-0xe0f has been reserved
system 00:0c: ioport range 0xe80-0xe8f has been reserved
system 00:0c: ioport range 0xf40-0xf4f has been reserved
system 00:0c: ioport range 0xa30-0xa3f has been reserved
system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
system 00:0e: iomem range 0x0-0x9ffff could not be reserved
system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
system 00:0e: iomem range 0x100000-0xcfffffff could not be reserved
system 00:0e: iomem range 0xfec00000-0xffffffff could not be reserved
PCI: Bridge: 0000:00:02.0
  IO window: d000-dfff
  MEM window: fe900000-fe9fffff
  PREFETCH window: d0000000-dfffffff
PCI: Bridge: 0000:00:06.0
  IO window: e000-efff
  MEM window: fea00000-feafffff
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:14.4
  IO window: disabled.
  MEM window: feb00000-febfffff
  PREFETCH window: disabled.
ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 18 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:02.0 to 64
ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 18 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:06.0 to 64
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
checking if image is initramfs...it isn't (no cpio magic); looks like an initrd
Freeing initrd memory: 1918k freed
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: disabled - APM is not SMP safe.
highmem bounce pool size: 64 pages
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
NTFS driver 2.1.29 [Flags: R/O].
JFS: nTxBlock = 8192, nTxLock = 65536
SGI XFS with ACLs, security attributes, large block numbers, no debug enabled
SGI XFS Quota Management subsystem
OCFS2 1.3.3
OCFS2 Node Manager 1.3.3
OCFS2 DLM 1.3.3
OCFS2 DLMFS 1.3.3
OCFS2 User DLM kernel interface loaded
GFS2 (built Mar 31 2008 08:35:14) installed
async_tx: api initialized (sync-only)
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
Boot video device is 0000:01:00.0
PCI: Setting latency timer of device 0000:00:02.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:02.0:pcie00]
PCI: Setting latency timer of device 0000:00:06.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:06.0:pcie00]
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
input: Power Button (FF) as /devices/virtual/input/input0
ACPI: Power Button (FF) [PWRF]
input: Power Button (CM) as /devices/virtual/input/input1
ACPI: Power Button (CM) [PWRB]
ACPI: Processor [P001] (supports 8 throttling states)
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Real Time Clock Driver v1.12ac
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
RAMDISK driver initialized: 16 RAM disks of 6666K size 1024 blocksize
loop: module loaded
Compaq SMART2 Driver (v 2.6.0)
HP CISS Driver (v 3.6.14)
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ATIIXP: IDE controller (0x1002:0x439c rev 0x00) at  PCI slot 0000:00:14.1
ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
ATIIXP: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:pio
ATIIXP: simplex device: DMA disabled
ide1: ATIIXP Bus-Master DMA disabled (BIOS)
Probing IDE interface ide0...
hda: ATAPI DVD A DH20A4P, ATAPI CD/DVD-ROM drive
hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
hda: UDMA/66 mode selected
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
Probing IDE interface ide1...
hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
ide-floppy driver 0.99.newide
Loading iSCSI transport class v2.0-724.
iscsi: registered transport (tcp)
Loading Adaptec I2O RAID: Version 2.4 Build 5go
Detecting Adaptec I2O RAID controllers...
Adaptec aacraid driver 1.1-5[2449]-ms
aic94xx: Adaptec aic94xx SAS/SATA driver version 1.0.3 loaded
scsi: <fdomain> Detection failed (no card)
sym53c416.c: Version 1.0.0-ac
qlogicfas: no cards were found, please specify I/O address and IRQ using iobase= and irq= options<6>QLogic Fibre Channel HBA Driver
iscsi: registered transport (qla4xxx)
QLogic iSCSI HBA Driver
Emulex LightPulse Fibre Channel SCSI driver 8.2.2
Copyright(c) 2004-2007 Emulex.  All rights reserved.
seagate: ST0x/TMC-8xx not detected.
Failed initialization of WD-7000 SCSI card!
DC390: clustering now enabled by default. If you get problems load
        with "disable_clustering=1" and report to maintainers
megaraid cmm: 2.20.2.7 (Release Date: Sun Jul 16 00:01:03 EST 2006)
megaraid: 2.20.5.1 (Release Date: Thu Nov 16 15:32:35 EST 2006)
megasas: 00.00.03.10-rc5 Thu May 17 10:09:32 PDT 2007
GDT-HA: Storage RAID Controller Driver. Version: 3.05
GDT-HA: Found 0 PCI Storage RAID Controllers
3ware Storage Controller device driver for Linux v1.26.02.002.
3ware 9000 Storage Controller device driver for Linux v2.26.02.010.
nsp32: loading...
ipr: IBM Power RAID SCSI Device Driver version: 2.4.1 (April 24, 2007)
RocketRAID 3xxx SATA Controller driver v1.2 (070830)
st: Version 20070203, fixed bufsize 32768, s/g segs 256
Driver 'st' needs updating - please use bus_type methods
Driver 'sd' needs updating - please use bus_type methods
Driver 'sr' needs updating - please use bus_type methods
ahci 0000:00:11.0: version 3.0
ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 18
ahci 0000:00:11.0: controller can't do 64bit DMA, forcing 32bit
ahci 0000:00:11.0: controller can't do PMP, turning off CAP_PMP
ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
ahci 0000:00:11.0: flags: ncq sntf ilck pm led clo pio slum part
scsi2 : ahci
scsi3 : ahci
scsi4 : ahci
scsi5 : ahci
scsi6 : ahci
scsi7 : ahci
ata1: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff900 irq 18
ata2: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff980 irq 18
ata3: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa00 irq 18
ata4: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa80 irq 18
ata5: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffb00 irq 18
ata6: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffb80 irq 18
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata1.00: HPA detected: current 976771055, native 976773168
ata1.00: ATA-7: ST3500630AS, 3.AFM, max UDMA/133
ata1.00: 976771055 sectors, multi 16: LBA48 NCQ (depth 31/32)
ata1.00: configured for UDMA/133
ata2: SATA link down (SStatus 0 SControl 300)
ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata3.00: HPA detected: current 312579695, native 312581808
ata3.00: ATA-7: ExcelStor Technology J8160S, P22OABEA, max UDMA/133
ata3.00: 312579695 sectors, multi 16: LBA48 NCQ (depth 31/32)
ata3.00: configured for UDMA/133
ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata4.00: HPA detected: current 976771055, native 976773168
ata4.00: ATA-8: ST3500820AS, SD81, max UDMA/133
ata4.00: 976771055 sectors, multi 16: LBA48 NCQ (depth 31/32)
ata4.00: configured for UDMA/133
ata5: SATA link down (SStatus 0 SControl 300)
ata6: SATA link down (SStatus 0 SControl 300)
scsi 2:0:0:0: Direct-Access     ATA      ST3500630AS      3.AF PQ: 0 ANSI: 5
sd 2:0:0:0: [sda] 976771055 512-byte hardware sectors (500107 MB)
sd 2:0:0:0: [sda] Write Protect is off
sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 2:0:0:0: [sda] 976771055 512-byte hardware sectors (500107 MB)
sd 2:0:0:0: [sda] Write Protect is off
sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sda: sda1 sda2
sd 2:0:0:0: [sda] Attached SCSI disk
scsi 4:0:0:0: Direct-Access     ATA      ExcelStor Techno P22O PQ: 0 ANSI: 5
sd 4:0:0:0: [sdb] 312579695 512-byte hardware sectors (160041 MB)
sd 4:0:0:0: [sdb] Write Protect is off
sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 4:0:0:0: [sdb] 312579695 512-byte hardware sectors (160041 MB)
sd 4:0:0:0: [sdb] Write Protect is off
sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdb: sdb1 sdb2
sd 4:0:0:0: [sdb] Attached SCSI disk
scsi 5:0:0:0: Direct-Access     ATA      ST3500820AS      SD81 PQ: 0 ANSI: 5
sd 5:0:0:0: [sdc] 976771055 512-byte hardware sectors (500107 MB)
sd 5:0:0:0: [sdc] Write Protect is off
sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 5:0:0:0: [sdc] 976771055 512-byte hardware sectors (500107 MB)
sd 5:0:0:0: [sdc] Write Protect is off
sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdc: sdc1
sd 5:0:0:0: [sdc] Attached SCSI disk
I2O subsystem v1.325
i2o: max drivers = 8
I2O Configuration OSM v1.323
I2O Bus Adapter OSM v1.317
I2O Block Device OSM v1.325
I2O SCSI Peripheral OSM v1.316
I2O ProcFS OSM v1.316
Fusion MPT base driver 3.04.06
Copyright (c) 1999-2007 LSI Corporation
Fusion MPT SPI Host driver 3.04.06
Fusion MPT FC Host driver 3.04.06
Fusion MPT SAS Host driver 3.04.06
ACPI: PCI Interrupt 0000:03:08.0[A] -> GSI 22 (level, low) -> IRQ 18
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
usbmon: debugfs is not available
ACPI: PCI Interrupt 0000:00:12.2[B] -> GSI 17 (level, low) -> IRQ 19
ehci_hcd 0000:00:12.2: EHCI Host Controller
ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
ehci_hcd 0000:00:12.2: debug port 1
ehci_hcd 0000:00:12.2: irq 19, io mem 0xfe8ff000
ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 6 ports detected
ACPI: PCI Interrupt 0000:00:13.2[B] -> GSI 19 (level, low) -> IRQ 20
ehci_hcd 0000:00:13.2: EHCI Host Controller
ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
ehci_hcd 0000:00:13.2: debug port 1
ehci_hcd 0000:00:13.2: irq 20, io mem 0xfe8fa800
ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 6 ports detected
116x: driver isp116x-hcd, 03 Nov 2005
ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 17
ohci_hcd 0000:00:12.0: OHCI Host Controller
ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
ohci_hcd 0000:00:12.0: irq 17, io mem 0xfe8fe000
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 3 ports detected
ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 17
ohci_hcd 0000:00:12.1: OHCI Host Controller
ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
ohci_hcd 0000:00:12.1: irq 17, io mem 0xfe8fd000
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 3 ports detected
usb 2-4: new high speed USB device using ehci_hcd and address 2
ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 16
ohci_hcd 0000:00:13.0: OHCI Host Controller
ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe8fc000
usb usb5: configuration #1 chosen from 1 choice
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 3 ports detected
usb 2-4: configuration #1 chosen from 1 choice
ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 16
ohci_hcd 0000:00:13.1: OHCI Host Controller
ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe8fb000
usb usb6: configuration #1 chosen from 1 choice
hub 6-0:1.0: USB hub found
hub 6-0:1.0: 3 ports detected
ACPI: PCI Interrupt 0000:00:14.5[C] -> GSI 18 (level, low) -> IRQ 16
ohci_hcd 0000:00:14.5: OHCI Host Controller
ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
ohci_hcd 0000:00:14.5: irq 16, io mem 0xfe8f9000
usb 4-3: new low speed USB device using ohci_hcd and address 2
usb usb7: configuration #1 chosen from 1 choice
hub 7-0:1.0: USB hub found
hub 7-0:1.0: 2 ports detected
USB Universal Host Controller Interface driver v3.0
sl811: driver sl811-hcd, 19 May 2005
Initializing USB Mass Storage driver...
usb 4-3: configuration #1 chosen from 1 choice
scsi8 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
PNP: PS/2 Controller [PNP0303:PSKE,PNP0f03:PSMS] at 0x60,0x64 irq 1,12
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
md: linear personality registered for level -1
md: raid0 personality registered for level 0
md: raid1 personality registered for level 1
md: raid10 personality registered for level 10
raid6: int32x1    980 MB/s
raid6: int32x2   1050 MB/s
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001b9ff38]
raid6: int32x4   1123 MB/s
raid6: int32x8    661 MB/s
raid6: mmxx1     2102 MB/s
raid6: mmxx2     3797 MB/s
raid6: sse1x1    2163 MB/s
raid6: sse1x2    3689 MB/s
raid6: sse2x1    4083 MB/s
raid6: sse2x2    7048 MB/s
raid6: using algorithm sse2x2 (7048 MB/s)
md: raid6 personality registered for level 6
md: raid5 personality registered for level 5
md: raid4 personality registered for level 4
md: multipath personality registered for level -4
device-mapper: uevent: version 1.0.3
device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
usbcore: registered new interface driver hiddev
input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.0/input/input2
input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:12.1-3
Fixing up Logitech keyboard report descriptor
input: Logitech USB Receiver as /devices/pci0000:00/0000:00:12.1/usb4/4-3/4-3:1.1/input/input3
input,hiddev96: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:12.1-3
usbcore: registered new interface driver usbhid
drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
TCP cubic registered
Initializing XFRM netlink socket
NET: Registered protocol family 1
NET: Registered protocol family 17
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
Starting balanced_irq
Using IPI No-Shortcut mode
md: Autodetecting RAID arrays.
md: Scanned 0 and added 0 devices.
md: autorun ...
md: ... autorun DONE.
RAMDISK: Compressed image found at block 0
VFS: Mounted root (ext2 filesystem).
Freeing unused kernel memory: 384k freed
squashfs: version 3.3 (2007/10/31) Phillip Lougher
squashfs: LZMA suppport for slax.org by jro
aufs 20080317
fuse init (API version 7.9)
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
scsi 8:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
fuse exit
sd 8:0:0:0: [sdd] 3862528 512-byte hardware sectors (1978 MB)
sd 8:0:0:0: [sdd] Write Protect is off
sd 8:0:0:0: [sdd] Mode Sense: 03 00 00 00
sd 8:0:0:0: [sdd] Assuming drive cache: write through
sd 8:0:0:0: [sdd] 3862528 512-byte hardware sectors (1978 MB)
sd 8:0:0:0: [sdd] Write Protect is off
sd 8:0:0:0: [sdd] Mode Sense: 03 00 00 00
sd 8:0:0:0: [sdd] Assuming drive cache: write through
 sdd: sdd1
sd 8:0:0:0: [sdd] Attached SCSI removable disk
scsi 8:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
sd 8:0:0:1: [sde] Attached SCSI removable disk
scsi 8:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
sd 8:0:0:2: [sdf] Attached SCSI removable disk
scsi 8:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
sd 8:0:0:3: [sdg] Attached SCSI removable disk
usb-storage: device scan complete
sd 2:0:0:0: Attached scsi generic sg0 type 0
sd 4:0:0:0: Attached scsi generic sg1 type 0
sd 5:0:0:0: Attached scsi generic sg2 type 0
sd 8:0:0:0: Attached scsi generic sg3 type 0
sd 8:0:0:1: Attached scsi generic sg4 type 0
sd 8:0:0:2: Attached scsi generic sg5 type 0
sd 8:0:0:3: Attached scsi generic sg6 type 0
ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:02:00.0 to 64
sky2 0000:02:00.0: v1.20 addr 0xfeafc000 irq 16 Yukon-EC Ultra (0xb4) rev 3
sky2 eth0: addr 00:24:8c:0f:03:f6
piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
Linux agpgart interface v0.102
ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0
end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0
input: PC Speaker as /devices/platform/pcspkr/input/input4
lp: driver loaded but no devices found
fuse init (API version 7.9)
Intel ISA PCIC probe: not found.
Databook TCIC-2 PCMCIA probe: not found.
sky2 eth0: enabling interface
sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
hda-intel: Invalid position buffer, using LPIB read method instead.
```

---

### Post by 67GTA on 2009-09-09
It says that your BIOS is probably not seeing all 4 CPU's. Check your BIOS settings to make sure everything is detected and set up. There are a few errors at boot, but the kernel is working around them like it should. It would be better to get the outputs from the newest kernel version you can.

---

### Post by nicholasblock on 2009-09-09
ok ill reinstall ubuntu tonight and ill get back to you. On my BIOS I have a few options I dont understand ill get those and get back to you

---

### Post by ronaldrand on 2009-09-13
Sorry for not reading the whole thread to see if my question was answered. I have a Compaq Presario F700. On Intrepid it ran horribly. I had the "press keys while booting" problem you mentioned. My laptop overheated severely shutting off every 10 minutes or so unless I set my CPU to 800 MHz. It would get hot enough to burn my leg. Even at 800 MHz the fan ran non-stop at high speed making lots of noise and probably wearing out the parts. It worked much better in Vista than it did in Ubuntu for some reason. I tried to upgrade to Jaunty a few months ago but had mega errors with all my programs so I decided to wait a while while the bugs got worked out. Last week I upgraded to Jaunty and it's just been fantastic. CPU doesn't max out, fan stays low, laptop cool. Bootup problem went away. I only just came across your thread as I was curious about what the problem was and how it got worked out in Jaunty.

My question is, do I still need to fix my dsdt file? I ran the compilation and got over 200 errors. I don't know if I'll be able to fix all these errors, as I don't understand the language. Is it something I need to worry about? Thanks in advance.

Oh yeah, one thing I forgot. With Intrepid I couldn't play any streaming video files either, like on YouTube. They stuttered so bad, and sometimes I had to drag my mouse over the video continuously in circles just to get it to play. (Yeah, that was weird!) On Jaunty it is a lot better, but doesn't seem perfect. It is clearly much better than before but now and then it still makes random pauses. Could this have something to do with the dsdt?

---

### Post by 67GTA on 2009-09-14
[ronaldrand]("http://ubuntuforums.org/member.php?u=754806"): It is hard to say about these things. Attach a copy of your dsdt.dsl file, and I can look to see what sections the errors are affecting. I can tell you more then.

---

### Post by ronaldrand on 2009-09-14
Okay, thanks a lot for looking!

---

### Post by 67GTA on 2009-09-14
ronaldrand:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 958 Optimizations

I fixed errors in the temp section. It should run cooler/quieter now. I also fixed an error with waking from suspend/hibernate. You can copy/paste for the rest of the how to with the fixed dsdt.aml I attached. FYI, 9.04 will be the last version to use custom DSDT support. 9.10 and beyond will still have these bugs because of your buggy DSDT. The only distro as of now that is planning to keep the custom DSDT kernel patch for the near future is Opensuse. My HP laptop has the same BIOS bug. I filed a kernel bug for the heat problem, and it was marked "WON'T FIX". The only real solution would be to get HP/Compaq to fix the BIOS. 

[ATTACH]128607[/ATTACH]

---

### Post by ronaldrand on 2009-09-15
Thanks for that. Unforunately after installing it I overheated just surfing the web. It seems that it's worse using it than not using it. Is that even possible?

---

### Post by 67GTA on 2009-09-15
That doesn't seem right. Post the output of ```
sudo dmesg
```

---

### Post by buellman on 2009-09-20
> **67GTA said:**
> The one you attached here is the original? It says every piece of hardware in you PC doesn't exist.

Hi
I have the same "problem" as alex.pancescu. My dsdt.dsl shows 200 errors about not existing objects. Is there anything that can be done?
The dsdt.dsl of my Asus M3A-H/HDMI is attached. Newest BIOS (1702) installed.

Greets. Buellman

---

### Post by 67GTA on 2009-09-20
If it is a custom rig, then it won't help to try fixing errors in the dsdt. Take a look in /var/log to see if there are any errors at boot. Or look at the output of ```
sudo dmesg
``` for a quick look.

---

### Post by buellman on 2009-09-20
Thank you!
I don't see anything problematic :-) Just thought it might be a good idea to fix those erorrs. But as it just works... why fix something that is not broken :-)

Greets. Grimsrud

---

### Post by buellman on 2009-09-20
Hmmm...
I checked my IBM X31 and my HP Omnibook vt6200 and as my X31 does not show any warning or errors I wouldlike to know if you could have a look at the dsdt.dsl of my HP as it shows warnings.
I tried it myself but well... I can't find the fixes I need.

Would be pretty cool if you could help.

Greets. Buellman

Ps: is there a page where fixed dsdt's could be uploaded so they could be of use for others?

---

### Post by HolyShnikes on 2009-09-20
I cant seem to find anything to fix my errors and warnings.  I don't know if I am searching in the right places or not, but I can't find anything.  I just updated my bios and I still get the following:

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/nathan/dsdt.dsl   104:     Method (\_WAK, 1, NotSerialized)
Warning  1080 -                              ^ Reserved method must return a value (_WAK)

/home/nathan/dsdt.dsl  3535:                 Method (_Q16, 0, NotSerialized)
Warning  1087 -    Not all control paths return a value ^  (_Q16)

/home/nathan/dsdt.dsl  7709:                 Method (_HOT, 0, Serialized)
Warning  1087 -    Not all control paths return a value ^  (_HOT)

/home/nathan/dsdt.dsl  7709:                 Method (_HOT, 0, Serialized)
Warning  1080 -     Reserved method must return a value ^  (_HOT)

/home/nathan/dsdt.dsl  7711:                     Zero
Error    4095 -                                     ^ syntax error, unexpected PARSEOP_ZERO

/home/nathan/dsdt.dsl  7718:                 Method (_CRT, 0, Serialized)
Warning  1087 -    Not all control paths return a value ^  (_CRT)

/home/nathan/dsdt.dsl  7718:                 Method (_CRT, 0, Serialized)
Warning  1080 -     Reserved method must return a value ^  (_CRT)

/home/nathan/dsdt.dsl  7720:                     Zero
Error    4095 -                                     ^ syntax error, unexpected PARSEOP_ZERO

ASL Input:  /home/nathan/dsdt.dsl - 8126 lines, 278510 bytes, 4166 keywords
Compilation complete. 2 Errors, 6 Warnings, 0 Remarks, 1126 Optimizations

```

Can someone help please?

---

### Post by 67GTA on 2009-09-20
[HolyShnikes]("http://ubuntuforums.org/member.php?u=38116"):

I can fix heat/loud fan problems and wake from suspend/hibernate. Attach a copy of your original dsdt.dsl file and I will fix it. Remember, this will no longer work with 9.10 and beyond. 9.04 is the last version to have custom dsdt support in the kernel.

---

### Post by HolyShnikes on 2009-09-20
Thanks so much.

**Edit** I uploaded the wrong file.  Fixed now.  Thanks again.

---

### Post by gnychis on 2009-09-21
hi all, I generally run Ubuntu machines, but I have recently tried to build a Hackintosh.  For graphics card support, I need to modify my DSDL and recompile it.  However, I keep getting an error that a user "litspliff" had in this thread, that you guys (e.g., 67GTA) were able to help him with.  

This error is: "ACPI path has too many parent prefixes."  I am basically trying to overcome this error.  Following this thread, it seems to have been fixed for litspiff somehow, but I didn't see details of how.

I've attached my DSDL, but from a comment in this thread, I believe the culprit line is this:
```
    External (^^^SATA.SCND.MSTR)
```

I think that the "^^^" cause the "too many prefixes" error.  How do you modify this line, and the resulting related lines in the DSDT to fix this?

I understand that this is not directly related to booting Ubuntu, but I would sincerely appreciate any help.  

Thanks!
George

---

### Post by HolyShnikes on 2009-09-21
> **67GTA said:**
> [HolyShnikes]("http://ubuntuforums.org/member.php?u=38116"):

I can fix heat/loud fan problems and wake from suspend/hibernate. Attach a copy of your original dsdt.dsl file and I will fix it. Remember, this will no longer work with 9.10 and beyond. 9.04 is the last version to have custom dsdt support in the kernel.

Do you know if these problems going to be fixed in Karmic Koala?

---

### Post by 67GTA on 2009-09-21
> **HolyShnikes said:**
> Do you know if these problems going to be fixed in Karmic Koala?

No, they won't be fixed unless HP fixes the BIOS. HP says that the machine wasn't certified for Linux, so it isn't their problem. This how to simply bypasses the original dsdt in your bios, and tells the kernel to use the fixed version. As of right now, Opensuse is the only distro trying to get the custom DSDT patch to work for future versions. I just received an email from the Suse devs that a pacth was committed to fix the problems with the custom dsdt patch for 2.6.31.  Everyone else is just dropping it. I am moving to Opensuse when 11.2 goes final. It doesn't run as hot as 9.10 without a custom dsdt, and suspend/hibernate work also. I've got you fixed up. 

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 1130 Optimizations

[ATTACH]129304[/ATTACH]

---

### Post by 67GTA on 2009-09-21
> **gnychis said:**
> hi all, I generally run Ubuntu machines, but I have recently tried to build a Hackintosh.  For graphics card support, I need to modify my DSDL and recompile it.  However, I keep getting an error that a user "litspliff" had in this thread, that you guys (e.g., 67GTA) were able to help him with.  

This error is: "ACPI path has too many parent prefixes."  I am basically trying to overcome this error.  Following this thread, it seems to have been fixed for litspiff somehow, but I didn't see details of how.

I've attached my DSDL, but from a comment in this thread, I believe the culprit line is this:
```
    External (^^^SATA.SCND.MSTR)
```I think that the "^^^" cause the "too many prefixes" error.  How do you modify this line, and the resulting related lines in the DSDT to fix this?

I understand that this is not directly related to booting Ubuntu, but I would sincerely appreciate any help.  

Thanks!
George


DSDT's aren't OS specific, so it should work with Mac also. I changed the language for the first error. "^^^" is not compatible acpi code. I replaced it with \_SB_PCI0. This caused the other errors to go away. See what this does:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 70 Optimizations

[ATTACH]129307[/ATTACH]

---

### Post by HolyShnikes on 2009-09-21
I followed the steps from "sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml" 

to "dmesg > /home/yourusername/Desktop/dmesg"

I am adding a copy of my dmesg.  I typed in iasl -tc /home/nathan/dsdt.dsl and still got the same errors.  I am not sure if I am doing it right.  If you get the time, cause I know your busy, could you help?

---

### Post by spanakorizo on 2009-09-22
hello all i have 6 errors (3+3) and i think that they are common to fix
can someone plz help?
here is the warnings:
> Intel ACPI Component Architecture
ASL Optimizing Compiler version 20080926 [Oct  4 2008]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

./dsdt_fixed.txt  9473:         Method (VGET, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (VGET)

./dsdt_fixed.txt  9518:         Method (TGET, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (TGET)

./dsdt_fixed.txt  9571:         Method (FGET, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (FGET)

./dsdt_fixed.txt  9602:             Store (VGET (Local0), Local1)
Warning  1092 -                               ^ Called method may not always return a value

./dsdt_fixed.txt  9644:             Store (TGET (Local0), Local1)
Warning  1092 -                               ^ Called method may not always return a value

./dsdt_fixed.txt  9677:             Store (FGET (Local0), Local1)
Warning  1092 -                               ^ Called method may not always return a value

ASL Input:  ./dsdt_fixed.txt - 9911 lines, 331416 bytes, 4808 keywords
AML Output: ./dsdt.aml - 37577 bytes, 1061 named objects, 3747 executable opcodes

Compilation complete. 0 Errors, 6 Warnings, 0 Remarks, 47 Optimizationsand here is the dsdt.dsl

[ATTACH]129374[/ATTACH]

if this helps:
MY MOBO is is P5K PREMIUM WIFI and the CPU=Q6600 2.4 (OC at 3.0GHZ) ---4GB Ram

---

### Post by 67GTA on 2009-09-22
> **HolyShnikes said:**
> I followed the steps from "sudo cp dsdt.aml /etc/initramfs-tools/DSDT.aml" 

to "dmesg > /home/yourusername/Desktop/dmesg"

I am adding a copy of my dmesg.  I typed in iasl -tc /home/nathan/dsdt.dsl and still got the same errors.  I am not sure if I am doing it right.  If you get the time, cause I know your busy, could you help?


You got it. There is no need to decompile the dsdt again with "iasl -tc". The custom dsdt I sent you has zero errors, and is being loaded per your dmesg output::

```
ACPI: Checking initramfs for custom DSDT
ACPI: Found DSDT in DSDT.aml.
ACPI: Override [DSDT-   MCP67], this is unsafe: tainting kernel
ACPI: Table DSDT replaced by host OS
ACPI: DSDT 00000000, 7C8A (r1 NVIDIA    MCP67  6040000 INTL 20090320)

```And your CPU temp is being read where it wasn't before:

```
thermal LNXTHERM:01: registered as thermal_zone0
ACPI: Thermal Zone [THRM] (49 C)
```

You should notice it runs a little cooler with a quieter fan, and it should wake from sleep with no problems.

---

### Post by 67GTA on 2009-09-22
> **spanakorizo said:**
> hello all i have 6 errors (3+3) and i think that they are common to fix
can someone plz help?
here is the warnings:
and here is the dsdt.dsl

[ATTACH]129374[/ATTACH]

if this helps:
MY MOBO is is P5K PREMIUM WIFI and the CPU=Q6600 2.4 (OC at 3.0GHZ) ---4GB Ram

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 50 Optimizations

I'm not sure if this will fix any bugs for you, but it is error free. Check your dmesg output before and after to see if anything changes.

[ATTACH]129413[/ATTACH]

---

### Post by gnychis on 2009-09-23
> **67GTA said:**
> DSDT's aren't OS specific, so it should work with Mac also. I changed the language for the first error. "^^^" is not compatible acpi code. I replaced it with \_SB_PCI0. This caused the other errors to go away. See what this does:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 70 Optimizations

[ATTACH]129307[/ATTACH]

Would you be willing to attach the .DSL you made to fix this?  For some reason, I'm trying to replicate your change but I'm failing.

---

### Post by spanakorizo on 2009-09-23
> **67GTA said:**
> Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 50 Optimizations

I'm not sure if this will fix any bugs for you, but it is error free. Check your dmesg output before and after to see if anything changes.

[ATTACH]129413[/ATTACH]
thank u! :)
but i need to ask u something..
did u try to fix those errors (mentioned in the lines) or u gave me a diferent .aml?
cause i see even the cpus are written by other method than the one patched by me
this results in CPU kernel panic (testing in leopard, forgot to mention)

anyway thanks again, i fixed the 6 errors with a lot help from this thread :)

---

### Post by spanakorizo on 2009-09-23
> **gnychis said:**
> Would you be willing to attach the .DSL you made to fix this?  For some reason, I'm trying to replicate your change but I'm failing.

u can decompile this aml to .dsl with iaslMe very easily

---

### Post by gnychis on 2009-09-23
> **spanakorizo said:**
> u can decompile this aml to .dsl with iaslMe very easily

if I decompile it, it has the same errors as before

---

### Post by HolyShnikes on 2009-09-23
Suspend isnt working still.  When I bring it back from suspend I hold in the power button for 3 seconds, then again for 2 seconds, and then again for another 2 seconds before the screen will turn on.  This is what I had to do before though.  I thought fixing the bug would fix the problem.  Is there something else that you know of that would fix this?  I am sure I noticed the fan running cooler.

Thanks, you are amazing.

---

### Post by 67GTA on 2009-09-23
> **gnychis said:**
> Would you be willing to attach the .DSL you made to fix this?  For some reason, I'm trying to replicate your change but I'm failing.

Here is the fixed dsdt.dsl [ATTACH]129500[/ATTACH]

---

### Post by 67GTA on 2009-09-23
> **spanakorizo said:**
> thank u! :)
but i need to ask u something..
did u try to fix those errors (mentioned in the lines) or u gave me a diferent .aml?
cause i see even the cpus are written by other method than the one patched by me
this results in CPU kernel panic (testing in leopard, forgot to mention)

anyway thanks again, i fixed the 6 errors with a lot help from this thread :)

I only fixed the errors reported by the iasl compiler.

---

### Post by 67GTA on 2009-09-23
> **HolyShnikes said:**
> Suspend isnt working still.  When I bring it back from suspend I hold in the power button for 3 seconds, then again for 2 seconds, and then again for another 2 seconds before the screen will turn on.  This is what I had to do before though.  I thought fixing the bug would fix the problem.  Is there something else that you know of that would fix this?  I am sure I noticed the fan running cooler.

Thanks, you are amazing.

That is a weird bug. I would probably file a bug report on that one. It might be something specific to your hardware. Most of the Nvidia MCP67 chipsets return to a black screen. I guess it is good that yours actually wakes up:-)

---

### Post by gnychis on 2009-09-23
> **67GTA said:**
> Here is the fixed dsdt.dsl [ATTACH]129500[/ATTACH]

Thanks bud! I really appreciate your help.

I have two bugs I am trying to figure out.  One is that, after my computer re-wakes from sleeping (Thinkpad X300 w/ Intel GMA3100) the screen becomes stretched, cut in half, and distorted:

[IMG]http://farm3.static.flickr.com/2620/3946048497_4acddcd9cb_o.jpg[/IMG]

Do you know of anything incorrect in my DSDL that might cause this, or something that could fix it?

The second problem is that I have no brightness control over the screen.

I understand if you are not sure on these problems, but I figured I would at least ask!

Thanks!
George

---

### Post by 67GTA on 2009-09-23
> **gnychis said:**
> Thanks bud! I really appreciate your help.

I have two bugs I am trying to figure out.  One is that, after my computer re-wakes from sleeping (Thinkpad X300 w/ Intel GMA3100) the screen becomes stretched, cut in half, and distorted:

[IMG]http://farm3.static.flickr.com/2620/3946048497_4acddcd9cb_o.jpg[/IMG]

Do you know of anything incorrect in my DSDL that might cause this, or something that could fix it?

The second problem is that I have no brightness control over the screen.

I understand if you are not sure on these problems, but I figured I would at least ask!

Thanks!
George


There isn't any way to fix these through the dsdt. I would file bug reports on these two bugs.

---

### Post by mtnova on 2009-09-23
HEllo,

I have the following warnings.Please help if you can.

[I]Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/doma/dsdt.dsl  5016:             Acquire (MUTE, 0x03E8)
Warning  1104 -       Possible operator timeout is ignored ^ 

/home/doma/dsdt.dsl  5030:             Acquire (MUTE, 0x03E8)
Warning  1104 -       Possible operator timeout is ignored ^ 

/home/doma/dsdt.dsl  5045:             Acquire (MUTE, 0x03E8)
Warning  1104 -       Possible operator timeout is ignored ^ 

/home/doma/dsdt.dsl  5060:             Acquire (MUTE, 0x0FFF)
Warning  1104 -       Possible operator timeout is ignored ^ 

/home/doma/dsdt.dsl  5074:             Acquire (MUTE, 0x03E8)
Warning  1104 -       Possible operator timeout is ignored ^ 

/home/doma/dsdt.dsl  5089:             Acquire (MUTE, 0x03E8)
Warning  1104 -       Possible operator timeout is ignored ^ 

/home/doma/dsdt.dsl  5104:             Acquire (MUTE, 0x03E8)
Warning  1104 -       Possible operator timeout is ignored ^ 

/home/doma/dsdt.dsl  5509:         Method (VGET, 1, NotSerialized)
Warning  1087 -                               ^ Not all control paths return a value (VGET)

/home/doma/dsdt.dsl  5554:         Method (TGET, 1, NotSerialized)
Warning  1087 -                               ^ Not all control paths return a value (TGET)

/home/doma/dsdt.dsl  5589:         Method (FGET, 1, NotSerialized)
Warning  1087 -                               ^ Not all control paths return a value (FGET)

/home/doma/dsdt.dsl  5624:             Store (VGET (Local0), Local1)
Warning  1092 -                                  ^ Called method may not always return a value

/home/doma/dsdt.dsl  5666:             Store (TGET (Local0), Local1)
Warning  1092 -                                  ^ Called method may not always return a value

/home/doma/dsdt.dsl  5699:             Store (FGET (Local0), Local1)
Warning  1092 -                                  ^ Called method may not always return a value

ASL Input:  /home/doma/dsdt.dsl - 5960 lines, 185348 bytes, 2496 keywords
AML Output: /home/doma/dsdt.aml - 19947 bytes, 632 named objects, 1864 executable opcodes

Compilation complete. 0 Errors, 13 Warnings, 0 Remarks, 552 Optimizations
[/I]

And of course:

---

### Post by 67GTA on 2009-09-23
mtnova:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 555 Optimizations

[ATTACH]129528[/ATTACH]

---

### Post by nicholasblock on 2009-09-24
67GTA, 

     Hey, you had worked on my dsdt a while ago but had lots of problems. I was wondering if you still have the on you compiled that only had the two errors? If you do I would really appreciate it if you could post it for me to look over. I am attaching a fresh one if you do not have it still.

Thanks,
Nic

---

### Post by Magnesium on 2009-09-24
Howdy 67GTA!

First of all, let me thank you for sticking with this thread for so long and helping so many people individually with their DSDT problems. Don't know if you really expected that to happen :eek:, but you did it anyway, and it's people like you that are the reason open-source can be successful...so thank you.

I'd also like to offer a suggestion for your how-to of the first post, if I may. I followed your steps, and actually found a DSDT for my laptop model on acpi.sourceforge.net. But somehow, there was a little difference between his laptop and mine (amount of RAM, I think), and it rendered my Kubuntu unbootable. I managed to get my system back, but I couldn't help but think of a better way: Just before we execute

```
sudo update-initramfs -u -k kernel-version
```

I would propose adding the command

```
sudo cp /boot/initrd.img-kernel-version ~/init.img-kernel-version
```

For example, ```
sudo cp /boot/initrd.img-2.6.28-15-generic ~/init.img-2.6.28-15-generic
```

This will back up their initial RAM image, since that's all that is modified by this procedure. Then, if something goes wrong, and their computer won't boot, they can just boot into a Live CD, and execute in a terminal

```
sudo cp ~/init.img-kernel-version /boot/initrd.img-kernel-version
```

and their computer will boot again. These commands essentially eliminate the risk encapsulated in your [COLOR="Red"]WARNING[/COLOR].

Now that I've "done my duty" by offering a suggestion...could you fix my DSDT? :redface: Actually, if you've got time, I would be very appreciative if you could look at the DSDT for both my laptop and my desktop. I believe I've attached all the relevant files in the tgz. I'm not noticing any problems with thermal sensors, etc., but both of these machines completely hang upon resuming from suspend...even Alt+SysRq+R,E,I,S,U,B doesn't do anything. I'm hoping that you can solve it!

Thanks again for everything.

Mg

---

### Post by mtnova on 2009-09-24
Hey 67GTA!

Great staff!!!!!!

I want to THANK YOU very much for helping me and people around the forum, and for your effort:)

Will try the file later one and update on the progress.

Thanks again!!!!

Cheers,
mtnova

---

### Post by HolyShnikes on 2009-09-24
> **67GTA said:**
> That is a weird bug. I would probably file a bug report on that one. It might be something specific to your hardware. Most of the Nvidia MCP67 chipsets return to a black screen. I guess it is good that yours actually wakes up:-)

Thanks for the help.  I really appreciate it.

---

### Post by BionicSeahorse on 2009-09-26
Hello,

I'm trying to fix all the warnings in the attached DSDT.dsl, but I have been unsuccessful in finding a solution so far... Here is my current output:

```
$ iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20081204 [Jan 10 2009]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  6307:                             If (LOr (MP0P (Local6), MP1P (Local6)))
Warning  1092 -                                         ^ Called method may not always return a value

dsdt.dsl  6307:                             If (LOr (MP0P (Local6), MP1P (Local6)))
Warning  1092 -                                         ^ Called method may not always return a value

dsdt.dsl  6309:                                 Multiply (MCRS (Local6), 0x08000000, BF0F)
Warning  1092 -  Called method may not always return a value ^ 

dsdt.dsl  6311:                                 If (MPCR (Local6))
Warning  1092 -                                        ^ Called method may not always return a value

dsdt.dsl  6313:                                     If (MP0P (Local6))
Warning  1092 -                                            ^ Called method may not always return a value

dsdt.dsl  6315:                                         If (MP1P (Local6))
Warning  1092 -    Called method may not always return a value ^ 

dsdt.dsl  6326:                                 If (MP0P (Local6))
Warning  1092 -                                        ^ Called method may not always return a value

dsdt.dsl  6328:                                     Store (MP0N (Local6), Local5)
Warning  1092 -   Called method may not always return a value ^ 

dsdt.dsl  6332:                                     If (MP1P (Local6))
Warning  1092 -                                            ^ Called method may not always return a value

dsdt.dsl  6334:                                         Store (MP1N (Local6), Local5)
Warning  1092 -       Called method may not always return a value ^ 

dsdt.dsl  6338:                                 If (LGreater (BNKN, MCDB (Local5)))
Warning  1092 -      Called method may not always return a value ^ 

dsdt.dsl  6340:                                     Store (MCDB (Local5), BNKN)
Warning  1092 -   Called method may not always return a value ^ 

dsdt.dsl  6343:                                 If (LLess (BNKX, MCDB (Local5)))
Warning  1092 -   Called method may not always return a value ^ 

dsdt.dsl  6345:                                     Store (MCDB (Local5), BNKX)
Warning  1092 -   Called method may not always return a value ^ 

dsdt.dsl  6348:                                 If (LGreater (COLN, MCDC (Local5)))
Warning  1092 -      Called method may not always return a value ^ 

dsdt.dsl  6350:                                     Store (MCDC (Local5), COLN)
Warning  1092 -   Called method may not always return a value ^ 

dsdt.dsl  6353:                                 If (LLess (COLX, MCDC (Local5)))
Warning  1092 -   Called method may not always return a value ^ 

dsdt.dsl  6355:                                     Store (MCDC (Local5), COLX)
Warning  1092 -   Called method may not always return a value ^ 

dsdt.dsl  6396:             Method (MP0P, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MP0P)

dsdt.dsl  6424:             Method (MP1P, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MP1P)

dsdt.dsl  6452:             Method (MPCR, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MPCR)

dsdt.dsl  6480:             Method (MP0N, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MP0N)

dsdt.dsl  6508:             Method (MP1N, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MP1N)

dsdt.dsl  6536:             Method (MCRB, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MCRB)

dsdt.dsl  6564:             Method (MCRS, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MCRS)

dsdt.dsl  6592:             Method (MCDB, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MCDB)

dsdt.dsl  6615:             Method (MCDC, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MCDC)

dsdt.dsl  6893:             Method (WMNV, 3, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (WMNV)

ASL Input:  dsdt.dsl - 7567 lines, 231342 bytes, 2929 keywords
AML Output: dsdt.aml - 28905 bytes, 1157 named objects, 1772 executable opcodes

Compilation complete. 0 Errors, 28 Warnings, 0 Remarks, 83 Optimizations

```

I've been googling for warnings 1087 and 1092 for days now, but I haven't found a definitive answer on how to fix them yet.
Any help would be appreciated. Thanks in advance!

---

### Post by 67GTA on 2009-09-28
BionicSeahorse:

[ATTACH]130111[/ATTACH]

---

### Post by 67GTA on 2009-09-28
Magnesium:

[ATTACH]130112[/ATTACH]

---

### Post by 67GTA on 2009-09-28
nicholasblock:

I'm afraid yours is a lost cause. I didn't keep the one you are talking about because it was so hacked up, I would have been afraid to boot a computer with it. I literally deleted whole sections just to get rid of some errors. Is this a custom system? There were a lot of errors about devices not existing. Does ```
sudo dmesg
``` report any errors?

---

### Post by nicholasblock on 2009-09-28
67GTA,

     Thanks for your time. This is a custom system and the dsdt posted was taken after I installed the newest bios and cleared cMOS so I don't know why hardware that is not there is showing up. I am actually needing the dsdt for my hackintosh as I having lots of problems that only a dsdt will fix. I dual boot with ubuntu and I also have problems with sleep/shutdown and I get random system freezes. I was hoping to get a dsdt with minimal errors so I can enable features that I need on my hack. Do you have any other suggestions that might help me?

---

### Post by BionicSeahorse on 2009-09-29
> **67GTA said:**
> BionicSeahorse:

[ATTACH]130111[/ATTACH]

Thanks a bunch! Looks like this aml file worked perfectly. :guitar:

---

### Post by Magnesium on 2009-10-02
> **67GTA said:**
> Magnesium:

[ATTACH]130112[/ATTACH]

Hello 67GTA!

Thanks so much for your time...0 errors or warnings on either computer! Unfortunately, this didn't fix my "resume from sleep" problems; both hang completely upon resume (not even "raising elephants" works).:cry: I'll experiment a little more, but do you have any ideas I can try? Maybe I'll start a new thread to get some input.

Sometimes I feel like I'm  ](*,)

Thanks,
Mg

EDIT: Forgot to ask...does the backup operation I described in my last post sound reasonable to you? I thought it might be a good addition to your how-to...

---

### Post by 67GTA on 2009-10-06
You will probably have to file a bug at this point. It is probably something hardware specific. I probably won't change the dsdt removal part of the how to. The method I currently have is needed to remove the link to the custom dsdt.

---

### Post by mtnova on 2009-10-10
Hi 67GTA


You have already helped me with my desktop dsdt and i'm really gratefull.

Can i ask you if you can take a look at my laptop dsdt please?

In the attachment i'm sending the dmesg output as well with many errors in it and dsdt of course

Thank you very,very much

mtnova

---

### Post by 67GTA on 2009-10-10
mtnova:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 7 Optimizations

Not too serious. May have caused an occasional freeze or bottleneck.

[ATTACH]131529[/ATTACH]

---

### Post by mtnova on 2009-10-11
Hi 67GTA,

Great staff.

I wish to thank you for all your help.

Cheers,
mtnova

---

### Post by scaine on 2009-10-12
Any news on the Karmic situation?  Is it still a "custom DSDT no-go"?

And did you get any update on your launchpad bugs, other than "won't fix"?

I'll be updating my main laptop to Karmic shortly, but I'm fairly sure that it won't be running at 31 degrees on the CPU and 45 degrees on the chassis after the upgrade...  :-(

---

### Post by 67GTA on 2009-10-12
Karmic and beyond will be a NO GO for custom DSDT's. You will have to compile your own kernel. I've been testing Karmic, and the heat isn't as bad as Jaunty. It is still making the fan run constantly on low. I had a discussion with the kernel devs about this, and they said no. I also filed a bug for Opensuse, and despite the problems, they are still trying to get it to work. [https://bugzilla.novell.com/show_bug.cgi?id=533555](https://bugzilla.novell.com/show_bug.cgi?id=533555) I'm going to download the test kernel now to see if it works.

---

### Post by monthana on 2009-10-13
Here is my output from running "iasl -tc dsdt.dsl" : [http://pastebin.ubuntu.com/292478/](http://pastebin.ubuntu.com/292478/)

Here is my output from the file dsdt.dsl :
[http://pastebin.ubuntu.com/292481/](http://pastebin.ubuntu.com/292481/)

Can anyone help me fix these errors?
I have a HP Pavilion DV6653eo running Ubuntu 9.04 64-bit, 
with 2.6.28-15-generic kernel

---

### Post by 67GTA on 2009-10-13
monthana:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 1162 Optimizations

Fixed temp reading errors and wake from suspend error. Should run quieter/cooler. Run this command before and after to see the difference.

```
dmesg | grep THRM
```

[ATTACH]131804[/ATTACH]

---

### Post by scaine on 2009-10-13
> **67GTA said:**
> Karmic and beyond will be a NO GO for custom DSDT's. You will have to compile your own kernel. I've been testing Karmic, and the heat isn't as bad as Jaunty. It is still making the fan run constantly on low. I had a discussion with the kernel devs about this, and they said no. I also filed a bug for Opensuse, and despite the problems, they are still trying to get it to work. [https://bugzilla.novell.com/show_bug.cgi?id=533555](https://bugzilla.novell.com/show_bug.cgi?id=533555) I'm going to download the test kernel now to see if it works.

And judging from that, they got it working for you!  Magic news.  Fingers crossed for their help in getting a custom ubuntu kernel going.  That would be awesome, but a little unexpected, I imagine...

---

### Post by agats on 2009-10-21
Could someone please help me with my dsdt file?

I've been getting to class five minutes early to press my arrow-down key to boot up into Ubuntu. :(

[ATTACH]132589[/ATTACH]

[ATTACH]132590[/ATTACH]

---

### Post by 67GTA on 2009-10-21
agats:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 1130 Optimizations

Should run cooler/quieter. 

[ATTACH]132669[/ATTACH]

---

### Post by krantix on 2009-10-24
I have a perfectly patched DSDT and no way to load it with karmic. Any news on the supposed patch? thanks!

---

### Post by 67GTA on 2009-10-24
It will not be supported. See post #343.

---

### Post by snoopy33 on 2009-10-24
Hi to all,

I m trying to patch myself the dsdt, I m not sure to understand how to do...

I use the how to from [http://forums.opensuse.org/new-user-how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html](http://forums.opensuse.org/new-user-how-faq-read-only/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html)

I ve decompiled the dsdt, go to the buggy line, and after, i try to look for Method (_HOT, 0, NotSerialized), but not so much response... don t know what to do !

Can anyone help me ???

Thanks in advance.

---

### Post by snoopy33 on 2009-10-24
I fix myself most of the errors by adding return(zero) but i don t find any help for _HOT, 0, NotSerialized, google has only 3 answers...

Have an idea ?

---

### Post by krantix on 2009-10-24
> **67GTA said:**
> It will not be supported. See post #343.

I've seen that, but toshiba will never fix the DSDT.

I can't use my laptop without the DSDT fix. I've tried [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml) but it does not work with 2.6.31-14.

---

### Post by 67GTA on 2009-10-24
> **snoopy33 said:**
> I fix myself most of the errors by adding return(zero) but i don t find any help for _HOT, 0, NotSerialized, google has only 3 answers...

Have an idea ?

Change the _HOT method at the end from:

```
Release (\_SB.PCI0.LPC.EC.ECMX)
                    Multiply (Local0, 0x0A, Local0)
                    Add (Local0, 0x0AAC, Local0)
                    Return (Local0)
                }
            }
```to
```

Release (\_SB.PCI0.LPC.EC.ECMX)
                    Multiply (Local0, 0x0A, Local0)
                    Add (Local0, 0x0AAC, Local0)
                    Return (Local0)
                }
             Return (0x00)
            }
```The _T_X remarks are usually harmless, but to get rid of them, replace with any three letter combo plus the number. For example, I'll use "cat". _T_0 will become cat0, _T_1 will become cat1, etc. The rest are just complaints that can be gotten rid of by adding a null value to shut iasl up as you have already seen. You didn't have any errors, so the kernel can probably work around all of these without a custom DSDT. Look for kernel/ACPI errors by running "dmesg" in a terminal.

---

### Post by 67GTA on 2009-10-24
> **krantix said:**
> I've seen that, but toshiba will never fix the DSDT.

I can't use my laptop without the DSDT fix. I've tried [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml) but it does not work with 2.6.31-14.

You have to recompile the kernel to apply this patch. Once you do that, it is YOUR kernel, and no longer get updates or patches from Debian/Ubuntu. You have to manually download and apply these and recompile again each time a security/driver update comes out.

---

### Post by deslos on 2009-10-25
hello there,

I have a nx7400 notebook, and my DSDT file is the one attached, is it fixable ?
do you have any hints for me?

thanx in advance

./deslos

when I compile it, I get 
```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20080926 [Oct  4 2008]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  2829:                     Method (_BCQ, 0, Serialized)
Warning  1098 -          Unknown reserved name ^  (_BCQ)

dsdt.dsl  9988:                         If (LEqual (C2C6 (0x00), 0x01))
Warning  1092 -                                        ^ Called method may not always return a value

dsdt.dsl 10012:                         If (LEqual (C2C6 (0x01), 0x01))
Warning  1092 -                                        ^ Called method may not always return a value

dsdt.dsl 10889:             Method (C2C6, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (C2C6)

ASL Input:  dsdt.dsl - 13745 lines, 503959 bytes, 6381 keywords
AML Output: ./dsdt.aml - 60653 bytes, 1080 named objects, 5301 executable opcodes

Compilation complete. 0 Errors, 4 Warnings, 0 Remarks, 2154 Optimizations

```

---

### Post by 67GTA on 2009-10-26
deslos:

Compilation complete. 0 Errors, 1 Warnings, 0 Remarks, 2156 Optimizations

I left the one warning. It is a Vista entry to control the backlight. It will not cause the Linux kernel any problems. There is no way to get rid of it except removing it all together which screws up the rest of the dsdt.

[ATTACH]133220[/ATTACH]

---

### Post by lui777 on 2009-10-27
Hi 67GTA, please would you tell me which correction you made in the dsdt.dsl a user send you in a past post to avoid these warnings?



> lu@lu-laptop:~$ iasl -tc dsdt.dsl                                           

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation           
Supports ACPI Specification Revision 3.0a             

dsdt.dsl  2934:                     Acquire (MUT0, 0x0FFF)
Warning  1104 -    Possible operator timeout is ignored ^

dsdt.dsl  5651:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5665:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5680:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5695:             Acquire (MUTE, 0x0FFF)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5709:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5724:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5739:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

ASL Input:  dsdt.dsl - 9617 lines, 292742 bytes, 4433 keywords
AML Output: dsdt.aml - 33391 bytes, 1068 named objects, 3365 executable opcodes

Compilation complete. 0 Errors, 8 Warnings, 0 Remarks, 1139 Optimizations


Thank you in advance!

Luigi

---

### Post by VXxed on 2009-10-27
Hey, I'm getting one warning on line 2098.  I fixed the other error there was by simply deleting the line.  Originally, I got this: ```
ronen@vxtablet:~$ iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl    23:     External (\DC1S)
Error    4056 -                    ^ Name already exists in scope (\DC1S)

dsdt.dsl  2098:                     Method (SBLL, 1, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (SBLL)

ASL Input:  dsdt.dsl - 5888 lines, 210890 bytes, 2615 keywords
Compilation complete. 1 Errors, 1 Warnings, 0 Remarks, 473 Optimizations

```

If at all possible, could you take a look and see if there's any fan control in there?  I'm having issues with my fan actually turning on on this laptop.  Thanks a lot!

---

### Post by 67GTA on 2009-10-28
> **lui777 said:**
> Hi 67GTA, please would you tell me which correction you made in the dsdt.dsl a user send you in a past post to avoid these warnings?





Thank you in advance!

Luigi

>                     Acquire (MUT0, 0x0FFF) Replace  and > Acquire (MUTE, 0x03E8 ) with > Acquire (MUT0, 0xFFFF)

---

### Post by glitchbit on 2009-10-28
Hi 67GTA,
     I am desperate need of your assistance and expertise in this dsdt matter. I have an issue with my Asus G2S laptop not waking up properly after going to sleep. The laptop turns on but the screen is blank and it is non-responsive (I do not believe the OS resumes).

I read this may be a common issue with _WAK? Here is what that section looks like and I have attached a dump of my dsdt.

```

    Method (_WAK, 1, NotSerialized)
    {
        ShiftLeft (Arg0, 0x04, DBG8)
        WAK (Arg0)
        If (ASSB)
        {
            Store (WSSB, ASSB)
            Store (WOTB, AOTB)
            Store (WAXB, AAXB)
        }

        If (DerefOf (Index (WAKP, Zero)))
        {
            Store (Zero, Index (WAKP, One))
        }
        Else
        {
            Store (Arg0, Index (WAKP, One))
        }

        Return (WAKP)
    }

```Also here is a line from the build log (I forgot to include it in the zip file, let me know if you need/want it)

Compilation complete. 0 Errors, 1 Warnings, 0 Remarks, 53 Optimizations

Going off of some code written for another Asus laptop and they fixed the sleep issue, so I tried modifying these two parts just now (and it still did not fix my sleep issue)

Original PRW directly before _WAK
```

    Scope (_SB)
    {
        Device (SLPB)
        {
            Name (_HID, EisaId ("PNP0C0E"))
            Method (_PRW, 0, NotSerialized)
            {
                Return (Package (0x02)
                {
                    0x0B, 
                    0x04
                })
            }
        }
    }

```Modified PRW (after reading more elsewhere I think this was some sort of power button fix..)
```

    Scope (_SB)
    {
        Device (PWRB)
        {
            Name (_HID, EisaId ("PNP0C0C"))
        }

        Device (SLPB)
        {
            Name (_HID, EisaId ("PNP0C0E"))
            Method (_PRW, 0, NotSerialized)
            {
                Return (Package (0x02)
                {
                    0x0B, 
                    0x04
                })
            }
        }
    }
 
```Original _WAK
```

    Method (_WAK, 1, NotSerialized)
    {
        ShiftLeft (Arg0, 0x04, DBG8)
        WAK (Arg0)
        If (ASSB)
        {
            Store (WSSB, ASSB)
            Store (WOTB, AOTB)
            Store (WAXB, AAXB)
        }

        If (DerefOf (Index (WAKP, Zero)))
        {
            Store (Zero, Index (WAKP, One))
        }
        Else
        {
            Store (Arg0, Index (WAKP, One))
        }

        Return (WAKP)
    }
 
```Modified _WAK
```

    Method (_WAK, 1, NotSerialized)
    {
        ShiftLeft (Arg0, 0x04, DBG8)
        WAK (Arg0)
        If (ASSB)
        {
            Store (WSSB, ASSB)
            Store (WOTB, AOTB)
            Store (WAXB, AAXB)
        }

        If (DerefOf (Index (WAKP, Zero)))
        {
            Store (Zero, Index (WAKP, One))
        }
        Else
        {
            Store (Arg0, Index (WAKP, One))
        }

        Return (Package (0x02)
        {
            Zero, 
            Zero
        })
    }
 
```

---

### Post by 67GTA on 2009-10-28
[VXxed]("http://ubuntuforums.org/member.php?u=937253"):

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 474 Optimizations I don't see any fan controls. Check your bios to see if it has any fan control. If not, you should file a bug.

[ATTACH]133436[/ATTACH]

---

### Post by 67GTA on 2009-10-28
glitchbit:

Compilation complete. 0 Errors, 8 Warnings, 0 Remarks, 53 Optimizations I really didn't see any suspend problems. It is more likely a hardware problem. I would file a bug for suspend failing.

[ATTACH]133437[/ATTACH]

---

### Post by 67GTA on 2009-10-28
ignore

---

### Post by glitchbit on 2009-10-28
> **67GTA said:**
> glitchbit:

Compilation complete. 0 Errors, 8 Warnings, 0 Remarks, 53 Optimizations I really didn't see any suspend problems. It is more likely a hardware problem. I would file a bug for suspend failing.

[ATTACH]133437[/ATTACH]

Thanks for taking a look, it appears like it was actually just an OSX problem and I got it fixed. Between collaborating with someone in an irc chat room and comparing my dsdt to "The King" from insanelymac I found my problems. It appears it had to do _WAK (Package, zero, zero), _GPE's PRW related methods? (nawcom fixed them), but I still could not wake back up out of sleep, so I then found that USB names were missing from King's dsdt so I renamed mine to match his (UCHx). Now everything appears to be working just fine, it wakes up very well.

Also I don't know how but when I compile I do not get any more warnings..

---

### Post by VXxed on 2009-10-28
Thanks a lot, 67GTA.  I've been working on this issue for a while now, and I'm glad an expert was able to take a look at the second-most-core piece of software in this situation.  I'm pretty sure, it's a phoenix bios from 2005...version 1.05.  Any chance you know anything specific about it?

---

### Post by scaine on 2009-10-29
Just found this thread :
[http://ubuntuforums.org/showthread.php?t=871311](http://ubuntuforums.org/showthread.php?t=871311)
which is fairly closely related to the work that 67GTA has been doing on this thread.

I'm pretty gutted about the DSDT situation on Karmic.  I upgraded my Tosh U-400 from my DSDT fixed Jaunty build last night.  Core idle temp shot up from 32C to 42C instantly.  Any kind of CPU activity will likely see it hitting 45C where the fan comes on and then the fan will likely stay on indefinitely until I stop using the lappy for an extended period.

Shame.

---

### Post by krantix on 2009-10-29
same problem here. without custom dsdt, GPU temperatures are crazy.

---

### Post by spillin_dylan on 2009-10-29
67GTA is cool and sexy!  Thanks for the super-helpful thread.

Toshiba A300 Special Edition, 58 optimizations!  You da man!

---

### Post by sergiom99 on 2009-10-30
How are your laptops working with KK and the no-DSDT-support?

---

### Post by calimancer on 2009-11-03
Hi 67GTA!

I read in that you can do magic with DSDT.
I need your help. I have these four errors and don´t know how to fix them:


   /home/cali/DSDT.dsl  9164:                 Alias (^AGP.VGA.UDCS, UDSC)
  Error    4064 - Object not found or not accessible from scope ^  (UDSC)
   
  /home/cali/DSDT.dsl  9165:                 Alias (^AGP.VGA.LCD, PLCD)
  Error    4064 - ^ Object not found or not accessible from scope (PLCD)
   
  /home/cali/DSDT.dsl  9166:                 Alias (^PB2.VGA.UDCS, UDS1)
  Error    4064 - Object not found or not accessible from scope ^  (UDS1)
   
  /home/cali/DSDT.dsl  9167:                 Alias (^PB2.VGA.LCD, PLC1)
  Error    4064 - ^ Object not found or not accessible from scope (PLC1)
   
  
 
My laptop is a Toshiba L505D-S5992.
Here is my dsdt.dsl file:



;)

---

### Post by 67GTA on 2009-11-03
Calimancer:

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 23 Optimizations

[ATTACH]134584[/ATTACH]

---

### Post by calimancer on 2009-11-03
Thanks 67GTA!!!
Now, I'm going to try it.
Why Toshiba has this kind of problems if they are one of the precursors of ACPI?

---

### Post by 67GTA on 2009-11-04
> **calimancer said:**
> Thanks 67GTA!!!
Now, I'm going to try it.
Why Toshiba has this kind of problems if they are one of the precursors of ACPI?

Most of the time, the hardware vendors use the Microsoft compiler to recompile the DSDT against their hardware. The PC manufacturers as a whole usually are not aware of the difference between MSFT and IASL, just developers and programmers.

---

### Post by BionicSeahorse on 2009-11-11
I just tried fixing this under an updated 9.10 installation before I saw the warning on the OP... Is there no longer a way to fix it by myself?

BTW, where should I file a bug report?

---

### Post by 67GTA on 2009-11-11
The only way is to compile your own kernel with the DSDT patch included. I wouldn't recommend this method. You need to register and file a bug on launchpad.

---

### Post by kruemelchen26 on 2009-11-11
Hello Friends,
 
can anyone fix my dsdt. I'm newbie and my english is bad.
 
```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation           
Supports ACPI Specification Revision 3.0a             
 
dsdt.dsl  5696:                             If (LOr (MP0P (Local6), MP1P (Local6)))
Warning  1092 -                                         ^ Called method may not always return a value
 
dsdt.dsl  5696:                             If (LOr (MP0P (Local6), MP1P (Local6)))
Warning  1092 -                                         ^ Called method may not always return a value
 
dsdt.dsl  5698:                                 Multiply (MCRS (Local6), 0x08000000, BF0F)
Warning  1092 -  Called method may not always return a value ^                            
 
dsdt.dsl  5700:                                 If (MPCR (Local6))
Warning  1092 -                                        ^ Called method may not always return a value
 
dsdt.dsl  5702:                                     If (MP0P (Local6))
Warning  1092 -                                            ^ Called method may not always return a value
 
dsdt.dsl  5704:                                         If (MP1P (Local6))
Warning  1092 -    Called method may not always return a value ^          
 
dsdt.dsl  5715:                                 If (MP0P (Local6))
Warning  1092 -                                        ^ Called method may not always return a value
 
dsdt.dsl  5717:                                     Store (MP0N (Local6), Local5)
Warning  1092 -   Called method may not always return a value ^                  
 
dsdt.dsl  5721:                                     If (MP1P (Local6))
Warning  1092 -                                            ^ Called method may not always return a value
 
dsdt.dsl  5723:                                         Store (MP1N (Local6), Local5)
Warning  1092 -       Called method may not always return a value ^                  
 
dsdt.dsl  5727:                                 If (LGreater (BNKN, MCDB (Local5)))
Warning  1092 -      Called method may not always return a value ^                 
 
dsdt.dsl  5729:                                     Store (MCDB (Local5), BNKN)
Warning  1092 -   Called method may not always return a value ^                
 
dsdt.dsl  5732:                                 If (LLess (BNKX, MCDB (Local5)))
Warning  1092 -   Called method may not always return a value ^                 
 
dsdt.dsl  5734:                                     Store (MCDB (Local5), BNKX)
Warning  1092 -   Called method may not always return a value ^                
 
dsdt.dsl  5737:                                 If (LGreater (COLN, MCDC (Local5)))
Warning  1092 -      Called method may not always return a value ^                 
 
dsdt.dsl  5739:                                     Store (MCDC (Local5), COLN)
Warning  1092 -   Called method may not always return a value ^                
 
dsdt.dsl  5742:                                 If (LLess (COLX, MCDC (Local5)))
Warning  1092 -   Called method may not always return a value ^                 
 
dsdt.dsl  5744:                                     Store (MCDC (Local5), COLX)
Warning  1092 -   Called method may not always return a value ^                
 
dsdt.dsl  5785:             Method (MP0P, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MP0P)
 
dsdt.dsl  5813:             Method (MP1P, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MP1P)
 
dsdt.dsl  5841:             Method (MPCR, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MPCR)
 
dsdt.dsl  5869:             Method (MP0N, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MP0N)
 
dsdt.dsl  5897:             Method (MP1N, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MP1N)
 
dsdt.dsl  5925:             Method (MCRB, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MCRB)
 
dsdt.dsl  5953:             Method (MCRS, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MCRS)
 
dsdt.dsl  5981:             Method (MCDB, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MCDB)
 
dsdt.dsl  6004:             Method (MCDC, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (MCDC)
 
dsdt.dsl  6353:             Method (_DSM, 4, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (_DSM)
 
dsdt.dsl  6353:             Method (_DSM, 4, NotSerialized)
Warning  1080 -                        ^ Reserved method must return a value (_DSM)
 
dsdt.dsl  6532:             Method (GAPR, 0, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (GAPR)
 
dsdt.dsl  6552:                     Store (ROPO (Local0), Local1)
Warning  1092 -                               ^ Called method may not always return a value
 
dsdt.dsl  6577:             Method (ROPO, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (ROPO)
 
dsdt.dsl  6917:             Method (_DSM, 4, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (_DSM)
 
dsdt.dsl  6917:             Method (_DSM, 4, NotSerialized)
Warning  1080 -                        ^ Reserved method must return a value (_DSM)
 
dsdt.dsl  7365:             Method (WMNV, 3, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (WMNV)
 
dsdt.dsl  7593:                                 Return (^^IXVE.IGPU._DSM (MUID, REVI, SFNC, ARGD))
Warning  1092 -            Called method may not always return a value ^
 
dsdt.dsl  7598:                                 Return (^^XVR0.VGA._DSM (MUID, REVI, SFNC, ARGD))
Warning  1092 -           Called method may not always return a value ^
 
dsdt.dsl  7605:                                 Return (^^IXVE.IGPU._DSM (MUID, REVI, SFNC, ARGD))
Warning  1092 -            Called method may not always return a value ^
 
dsdt.dsl  7610:                                 Return (^^XVR0.VGA._DSM (MUID, REVI, SFNC, ARGD))
Warning  1092 -           Called method may not always return a value ^
 
dsdt.dsl  8002:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored
 
dsdt.dsl  8016:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored
 
dsdt.dsl  8031:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored
 
dsdt.dsl  8046:             Acquire (MUTE, 0x0FFF)
Warning  1104 -                                 ^ Possible operator timeout is ignored
 
dsdt.dsl  8060:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored
 
dsdt.dsl  8075:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored
 
dsdt.dsl  8090:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored
 
dsdt.dsl 11324:             Method (GMLE, 1, Serialized)
Warning  1087 -                        ^ Not all control paths return a value (GMLE)
 
dsdt.dsl 11337:             Method (SMLE, 1, Serialized)
Warning  1087 -                        ^ Not all control paths return a value (SMLE)
 
dsdt.dsl 11357:             Method (WLLC, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (WLLC)
 
ASL Input:  dsdt.dsl - 15439 lines, 454389 bytes, 7331 keywords
AML Output: dsdt.aml - 58399 bytes, 1839 named objects, 5492 executable opcodes
 
Compilation complete. 0 Errors, 49 Warnings, 0 Remarks, 63 Optimizations

```
 
My Laptop is a Asus k70I0

---

### Post by k0smik0 on 2009-11-12
hi ;D

obviously, i also have a problem with dsdt... so, here partial dmesg:

[   18.962087] ACPI Error (psargs-0359): [^CKDY] Namespace lookup failure, AE_NOT_FOUND
[   18.962100] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.BASM] (Node ffff880037a653b0), AE_NOT_FOUND
[   18.962175] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.CIMP] (Node ffff880037a65590), AE_NOT_FOUND
[   18.962252] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IXVE.IGPU.NVIF] (Node ffff880037a65c70), AE_NOT_FOUND



hardware is:

fujitsu-siemens v6555, core2duo t5870, chipset nvidia mcp79 - buyed without os (;D)

i suppose this dsdt is not working correctly, because fans not work at all; here the output by sensors (by thermal and coretemp modules):

acpitz-virtual-0
Adapter: Virtual device
temp1:       +72.8 C  (crit = +199.8 C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +73.0 C  (high = +100.0 C, crit = +100.0 C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +73.0 C  (high = +100.0 C, crit = +100.0 C)



finally, i tried to fix dsdt, but i'm not so able ;D - here first output:


iasl -d dsdt.dat

[...]
Loading Acpi table from file dsdt.dat
Acpi table [DSDT] successfully installed and loaded
Pass 1 parse of [DSDT]
Pass 2 parse of [DSDT]
Parsing Deferred Opcodes (Methods/Buffers/Packages/Regions)
........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
Parsing completed

Found 3 external control methods, reparsing with new information
Pass 1 parse of [DSDT]
Pass 2 parse of [DSDT]
Parsing Deferred Opcodes (Methods/Buffers/Packages/Regions)
........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
Parsing completed
Disassembly completed, written to "dsdt.dsl"



and again: 

iasl -tc dsdt.dsl

[...]
dsdt.dsl     1: ACPI  // Address Base
Error    4095 -    ^ syntax error, unexpected PARSEOP_NAMESEG, expecting PARSEOP_DEFINITIONBLOCK

ASL Input:  dsdt.dsl - 7495 lines, 251808 bytes, 0 keywords
Compilation complete. 1 Errors, 0 Warnings, 0 Remarks, 0 Optimizations



i tried to search for some fix about "4095 error" and i found that is first row to delete:
first row in dsdt.dsl is
"ACPI Error: ACPI path has too many parent prefixes (^) - reached beyond root node 20090521 nsaccess-526"

and finally, if i delete this row and try to recompile with -tc, i have 201 errors ;D


ok, i have to stop ;D



in attach, there are dsdt.dat (same /proc/acpi/dsdt), dsdt.dsl and dsdt.hex


ah! searching for "linux + fujitsu amilo v6555" in google... obtain 0 (ZERO) results ;D
too, too young :/


pardon for my english, but i'm italian ;)

p.s.: i'm using debian (testing) - i think it's not so different fro *ubuntu, but in doubt i preferred to specify

thanks in advance,
Max

---

### Post by k0smik0 on 2009-11-12
hi ;D

another box

this time is for Lenovo 3000 N200 (celeron64, 82801H / ICH8 chipset, vga GM965)

here the output of iasl -tc

[http://pastebin.com/f7083a7a4](http://pastebin.com/f7083a7a4)

dsdt files in attach

tnx ;D,
Max

---

### Post by iantdude on 2009-11-13
67GTA and other community members,

I have been finding great difficulty in trying to locate any information on the following error/warning messages when I compile dsdt.dsl to dsdt.aml using iasl version 20090903:

```

bash-3.2# ./iasl -ta dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090903 [Sep  3 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 4.0

dsdt.dsl  9624:         Method (VGET, 1, NotSerialized)
Warning  1087 -                    ^ Not all control paths return a value (VGET)

dsdt.dsl  9669:         Method (TGET, 1, NotSerialized)
Warning  1087 -                    ^ Not all control paths return a value (TGET)

dsdt.dsl  9722:         Method (FGET, 1, NotSerialized)
Warning  1087 -                    ^ Not all control paths return a value (FGET)

dsdt.dsl  9753:             Store (VGET (Local0), Local1)
Warning  1092 -                       ^ Called method may not always return a value

dsdt.dsl  9795:             Store (TGET (Local0), Local1)
Warning  1092 -                       ^ Called method may not always return a value

dsdt.dsl  9828:             Store (FGET (Local0), Local1)
Warning  1092 -                       ^ Called method may not always return a value

dsdt.dsl 10145:                                         ShiftRight (BUF2, 0x04)
Warning  1105 -             Result is not used, operator has no effect ^

ASL Input:  dsdt.dsl - 10317 lines, 333408 bytes, 4839 keywords
AML Output: dsdt.aml - 38570 bytes, 996 named objects, 3843 executable opcodes

Compilation complete. 0 Errors, 7 Warnings, 0 Remarks, 69 Optimizations

```Perhaps my search terms aren't exacting enough when trying to find an explanation for any of the 7 warning messages listed above.  I apologize if it has already been mentioned under this topic.

In closing, I am kindly requesting anyone's assistance in trying to resolve or remove the error/warning messages listed above.

I am not sure if it matters, but the attached dsdt.dsl is from an ASUS P5Q.

Thank you very much for your time!


Best regards,

IanT


PS.  Is it best practice to extract **dsdt** from an original, unmodified, bios?  The reason why I ask this, especially as a post-script message, is because I wonder if some of my problems are attributed to a modified bios, and hence dsdt might have been altered somehow...?

---

### Post by sinus0 on 2009-11-19
Hello 67GTA and All,

For las t couple of days I was fighting DTST problems of my brand new HP Pavilion dv7-3090er. Under linux it's unable to get to ANY thermal attributes. As a result fan is minimal and system gets over heated easily. I'm unfortunate to get quite rare errors (at least no solution I came across in the internet)

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20091112 [Nov 12 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 4.0

Error    4069 - Could not open file "C:\ACPI\C:\ACPI\dsdt_orig.aml" (Invalid argument)

C:\ACPI\dsdt_orig.dsl  3704:                 If (CondRefOf (FPED))
Error    4096 -                     parse error ^

C:\ACPI\dsdt_orig.dsl  7753:                 If (IGDS)
Error    4096 -                      parse error ^

C:\ACPI\dsdt_orig.dsl  7785:                 Else
Error    4096 -                         parse error ^

C:\ACPI\dsdt_orig.dsl  7934:             Device  {
Error    4096 -     parse error, expecting `$' ^

```67GTA could you take a look at this stuff please, I suspect it is a scope issue or code is placed where it shouldn't be. My knowledge of AML is too limited to get it resolved fast.

Thanks,
Alex

P.S. Pity Ubuntu will no longer support custom DTSTs, it makes me move to OpenSUSE. Wrong decision IMHO.

---

### Post by cyberey66 on 2009-11-20
Is it possible to recompile the current karmic kernel with DSDT file support?

---

### Post by mamato on 2009-11-22
Hi 67GTA and others,

Would you take a look at my DSDT file? My laptop, HP Pavilion DV5162 suddenly start to act weird since I upgraded to the latest kernel. :-(. 
The CPU fan is running at its full speed and sometimes, my processor reach
its critical temperature limit. I googled for the solution and found that it was caused by a buggy DSDT :-(

I have followed the How To, and there was no error and warning. For the sake of curiousity, would you like to take a look at it? :-D Thanks a lot before.

And, I am using openSUSE 11.2 for trying this custom DSDT.

---

### Post by bronzika on 2009-11-30
Hi,

I've been trying to fix DSDT file from my HP 6910p but couldn't. I can get down to some 35 errors from 45 and then I'm stuck!
Installed latest BIOS f17. 

67GTA do your magic!!![U]
[/U]  Please!!! Help!!! :-)

---

### Post by seish on 2009-12-03
how do I add 
acpi_osi="Linux"

Into grub2?

---

### Post by n2sins on 2009-12-04
hello.. i have a toshiba a305-s6848. amd turion x2. i have the phoenix bios. i have been having temp problems. so i have spent a while researching this.. especially at this thread. i have 0 errors , 0 warnings and it made 15 optimization. i never installed the custom dsdt. should i? since it has no errors. i checked /proc/acpi/fan. this is in the off state. i can turn on but it does not cool it down  . i looked at several of peterwills posts as his was giving some of the same problems. my only problem is heat. i can suspend , hibernate and control lcd brightness. the only custom part on my machine is i put a 500gb wd hd in instead of the 200gb wd hd. my temp at 800mhz right now idoling at 54c. i have checked proc/acpi/ have many populated folders.. i checked ibex on live cd and temps were idol 35c. i am grub dual boot vista preinstall and ubuntu 9.04. i can play simple game like moonlander.. or more graphically sophisticated  frets on fire and actually shut my pc off when i run it at 2ghz performance level or on demand.. then have to go to manual fsck and fix.. took me 3 times to realize it was heat related. if i get to 75c it shuts down. i will include my dsdt file. if u could look at it i would appreciate. this is my first post.. sorry for so long. i just wanted to make sure i covered everything. i did try to install toshutils and the other one that peterwill discussed. one was already installed but said kernel had no support.. the  other one i found out will not run on phoenix bios.. as its not really 100% toshiba.. anyone have any ideas. i have ran 9.04 since it came out and until i started trying to play games i just left it on demand and had no clue of any bug.. even usb huawei broadband dongleworked except after hibernate just unplug my usb dongle plug back in and it would run my internet.

---

### Post by n2sins on 2009-12-04
one last thing.. i have the ati x1250 integrated graphics on this toshiba a305 . and im using open drivers. as this is now considered legacy. ( 1 yr old laptop is legacy now...)  can the open drivers for the video be causing this headache?

---

### Post by n2sins on 2009-12-04
i sent the wrong file should be the dsl file? anyways here it is

---

### Post by n2sins on 2009-12-06
> **CylnZ said:**
> Hi Peter, have you tried:

sudo apt-get install toshutils ?

Supposedly it has toshiba acpi fan controls. I found it in a round about way from this:
[http://www.linuxquestions.org/hcl/showproduct.php/product/4080/sl/d](http://www.linuxquestions.org/hcl/showproduct.php/product/4080/sl/d)

I was reading the acpi section and found toshutils by  typing "fan" into a terminal. Toshutils doesnt help me a lick since I have a pm965 but hopefully it'll help you.

[SIZE=2]i read this and it seems i may be right to a degree.. according to this the acpi interacts with the video card and since the x1250 is legacy and unsupported it might indicate a reason i have alot of heat being generated. i did try  the acpi_osi="Linux" at grub options and i do get a more detailed dmesg.. but under my /proc/acpi/ no new functions or fan on appeared . so i am still looking for a good answer[/SIZE]

---

### Post by n2sins on 2009-12-06
[SIZE=3]i know this may not be of any help.. but i am tryi[COLOR=black]ng to ge this issue solved.. i decided to run dmesg with a little twist.. to see the differences between how 9.04 and 8.10 saw my hardware. i am a newbie.. windows convert with little knowledge , but how do you learn if u dont investigate. so my system is dual boot vista 9.04. so i downloaded 8.10 and done the live disc. it showed some differences. i didnt think that 8.10 would catch more then 9.04 but in a few cases described hardware better.
also found where linux is reporting a bios bug. i will include the 2 dmesg's if anyone wants to help. that would be great. cant learn to speak linux.  if u dont understand linux.
[/COLOR][/SIZE]

---

### Post by n2sins on 2009-12-06
just a little difference.. ,but why different?

 12.673234] ACPI: Thermal Zone [THZN] (62 C)  in 8.10
 11.733877] ACPI: Thermal Zone [THZN] (65 C)  in 9.04

is the bios not being read by linux correctly?

look at the 2 attached dmesg from previous post.. if the opsys is reading wrong and not adjusting temp correctly.. is their a way to change thermal zones temp settings.. then fan may start functining at proper speed? maybe its a calculated temp. if its a calculated temp then maybe whatever the multiplier is, is incorrect or can be adjusted? anyone ?

---

### Post by sergiom99 on 2009-12-09
Hey Shawn, are you already gone to OpenSUSE?

Did you try KK? 
Is the lack of DSDT support a final decision?

Regards- Sergio

---

### Post by TheLostThinker on 2009-12-11
Can someone help me fix my file.. I'm a real noob and do not know what I would change. Here is my dsdt. And the error message I am getting is ```
  Error    4095 -                ^ syntax error, unexpected PARSEOP_NAMESEG, expecting PARSEOP_DEFINITIONBLOCK

``` Im running a sattelite l305d and having major overheating problems...

---

### Post by ibuclaw on 2009-12-11
> **TheLostThinker said:**
> Can someone help me fix my file.. I'm a real noob and do not know what I would change. Here is my dsdt. And the error message I am getting is ```
  Error    4095 -                ^ syntax error, unexpected PARSEOP_NAMESEG, expecting PARSEOP_DEFINITIONBLOCK

``` Im running a sattelite l305d and having major overheating problems...

The first two lines seem to have made it's way into the file somehow ... they shouldn't be there.

Also - dsdt patch is no longer used, not sure how you intend to use it. And if your Laptop is overheating - I doubt DSDT will solve your problem.

---

### Post by Bluesbird on 2009-12-16
Hi,
@67GTA and any other
I have a 13 inch ULV Notebook and the Vendor is CZC. I have still fixed 28 of 30 errors
in the DSDT but I need a little bit help to fix the last two :) 

                                 dsdt.dsl  7271:             Method (_TMP, 0, NotSerialized) 
 Warning  1087 -                        ^ Not all control paths return a value (_TMP) 
  
 dsdt.dsl  7271:             Method (_TMP, 0, NotSerialized) 
 Warning  1080 -                        ^ Reserved method must return a value (_TMP) 
 
```
 

Method (_TMP, 0, NotSerialized)
            {
                If (DTSE)
                {
                    If (LGreaterEqual (DTS1, DTS2))
                    {
                        Return (Add (0x0AAC, Multiply (DTS1, 0x0A)))
                    }
                    Else
                    {
                        Return (Add (0x0AAC, Multiply (DTS2, 0x0A)))
                    }
                }
            }

            Method (_AC0, 0, NotSerialized)
            {
                Return (Add (0x0AAC, Multiply (TAL0, 0x0A)))
            }

            Method (_CRT, 0, NotSerialized)
            {
                Return (0x0E62)
            }
```

I'm not really a Programmer ;) What must I do to fix this ?

Greetings 
Bluesbird

---

### Post by luigi6699 on 2009-12-16
This thread is far and away one of the best resources on the net for DSDT repair/hacking.  Thank you to everyone who has participated thus far!

With all your advice, I've fixed my DSDT errors and many of the warnings.  I'm down to just 13 warnings left... I would love any help, especially if the helper wouldn't mind explaining what they did.  I've learned a lot about DSDT already and I'm always hungry for more... :)

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20091112 [Nov 13 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 4.0

/Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl  7342:                         Method (_GTF, 0, NotSerialized)
Warning  1081 -                                                                       Reserved method must return a value ^  (_GTF)

/Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl  7405:                         Method (_GTF, 0, NotSerialized)
Warning  1088 -                                                                      Not all control paths return a value ^  (_GTF)

/Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl  7405:                         Method (_GTF, 0, NotSerialized)
Warning  1081 -                                                                       Reserved method must return a value ^  (_GTF)

/Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl  7477:                     Method (_GTM, 0, NotSerialized)
Warning  1088 -                                                                  Not all control paths return a value ^  (_GTM)

/Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl  7477:                     Method (_GTM, 0, NotSerialized)
Warning  1081 -                                                                   Reserved method must return a value ^  (_GTM)

/Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl  7650:                         Method (_GTF, 0, NotSerialized)
Warning  1088 -                                                                      Not all control paths return a value ^  (_GTF)

/Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl  7650:                         Method (_GTF, 0, NotSerialized)
Warning  1081 -                                                                       Reserved method must return a value ^  (_GTF)

/Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl  7718:                         Method (_GTF, 0, NotSerialized)
Warning  1088 -                                                                      Not all control paths return a value ^  (_GTF)

/Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl  7718:                         Method (_GTF, 0, NotSerialized)
Warning  1081 -                                                                       Reserved method must return a value ^  (_GTF)

/Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl  7825:                     Method (_GTF, 0, NotSerialized)
Warning  1088 -                                                                  Not all control paths return a value ^  (_GTF)

/Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl  7825:                     Method (_GTF, 0, NotSerialized)
Warning  1081 -                                                                   Reserved method must return a value ^  (_GTF)

/Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl  7871:                     Method (_GTF, 0, NotSerialized)
Warning  1088 -                                                                  Not all control paths return a value ^  (_GTF)

/Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl  7871:                     Method (_GTF, 0, NotSerialized)
Warning  1081 -                                                                   Reserved method must return a value ^  (_GTF)

ASL Input:  /Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl - 7885 lines, 301109 bytes, 3352 keywords
AML Output: /Users/campbell/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/./dsdt.aml - 32813 bytes, 676 named objects, 2676 executable opcodes

Compilation complete. 0 Errors, 13 Warnings, 0 Remarks, 36 Optimizations
```

DSDT attached.  Thanks in advance for the help!

---

### Post by n2sins on 2009-12-18
i have had the same overheating problems since i got ubuntu 9.04 on this pc.. i checked the dsdt data.. 0 errors 0 warnings 15 optimizations.. after puting the dsdt file in and verifying it was correctly installed  and putting in the acp_osi="Linux" still no love.. still the same.. except now no cpu throttling is listed in acpi.. ughhh.. and no fan on.. so still no colling.. however i did stumble on something that lowered my temps 10c.. i dont know if it will help but its real simple.. just try to hibernate.. on mine i have the ata1: softreset failed (device not ready) .. so even though it did successfully hibernate.. it went throught grub to start back up.. then i tried suspend and upon waking.. i tried to play moonlander.. normally it stated on grellm that im using up to 99% of both cpus alternating.. this time.. it was only using about 10% alternating. so i looked at the temp.. instead of 80c to 82c it was 68c to 70c.. so i looked at the acpi.. and it stated the fan was on.. the first time i have seen it on.. so it seems i have a workaround.. i hope this helps someone

---

### Post by _loof_ on 2009-12-28
hey all

my thinkpad t500 2089-2kg is extremly overheating under ubuntu. under windows xp everything is fine. I have been playing around with all sorts of fan and cpu tools for about a half a year now, but nothing helped...

would be really cool if you could take a look at my dsdt. I think its not such a big deal, because there are only warnings and no errors:

```
/home/yves/dsdt.dsl  3251:                                     If (LFLS ())
Warning  1092 -           Called method may not always return a value ^ 

/home/yves/dsdt.dsl  3354:                                 If (LFLS ())
Warning  1092 -       Called method may not always return a value ^ 

/home/yves/dsdt.dsl  3377:                                 If (LFLS ())
Warning  1092 -       Called method may not always return a value ^ 

/home/yves/dsdt.dsl  3442:                                     If (LFLS ())
Warning  1092 -           Called method may not always return a value ^ 

/home/yves/dsdt.dsl  3454:                                     If (LFLS ())
Warning  1092 -           Called method may not always return a value ^ 

/home/yves/dsdt.dsl  3474:                     Method (LFLS, 0, NotSerialized)
Warning  1087 -      Not all control paths return a value ^  (LFLS)

/home/yves/dsdt.dsl  8002:                 Method (ATPX, 2, NotSerialized)
Warning  1087 -  Not all control paths return a value ^  (ATPX)

/home/yves/dsdt.dsl  8103:                 Method (ATIF, 2, NotSerialized)
Warning  1087 -  Not all control paths return a value ^  (ATIF)

/home/yves/dsdt.dsl 11642:             Method (_Q15, 0, NotSerialized)
Warning  1087 -                                   ^ Not all control paths return a value (_Q15)

ASL Input:  /home/yves/dsdt.dsl - 15810 lines, 521341 bytes, 6428 keywords
AML Output: /home/yves/dsdt.aml - 57498 bytes, 1254 named objects, 5174 executable opcodes

Compilation complete. 0 Errors, 9 Warnings, 0 Remarks, 3090 Optimizations

```[ATTACH]141538[/ATTACH]

thanks 1024!

_loof_

---

### Post by arcasys on 2010-01-11
Hi 67GTA,

Sorry to bother you with another potential DSDT problem.
I'm not new to Linux and using Debian servers for years which run 24/7 with no need to suspend or hibernate.
Now I decided to install Ubuntu on my laptop and I'm running into suspend/hibernate problems.

I first installed 8.04 (Hardy Heron) and suspend seemed to work.
Then I decided to try 9.10 (Karmic) and suspend finishes without errors according to the log but returns with a black screen and absolutely no reaction to any keystroke.
The funny thing is that now the 8.04 installation which I kept on a different partition also ceased to return from suspend and shows the same effect as 9.10.
This brought me to the conclusion that something must have been changed in the BIOS during the installation process.

Is this possible? 

I can reproduce it by subsequently re-installing 8.04 (suspend works but not in 9.10) and 9.10 - suspend doesn't work in both installations.

I found a fixed DSDT in the DSDT repository, but this does only say fix a thermal problem and I didn't try it yet.
There was a note somewhere saying Ubuntu 9.10 doesn't provide the kernel patch to replace the DSDT anymore, so what can I do except filing a bug?

I've attached a tar with both my original DSDT (dsdt.dsl) and the fixed one.

I'd appreciate any advice and help. 

Regards
Hans

---

### Post by 00oo00 on 2010-01-19
Hi,67GTA.
 I tried 3 versions of Ubuntu and got a brightness issue with it which linked to my ACPI. I know this can be fixed via the DSDT Override but I failed to get rid of the annoying errors each time I compile. And tried the menu.lst way not working for me. Maybe you can have a check of my DSDT and ACPI info then get a clue. I did what you demonstrated of this thread and got all the ACPI info I could. Hope you can guide me through this mess. I also got the SSDTs of my BOard and need to inject it into the DSDT to get the SpeedStep function.
Here is my ACPI stuff pls take a look.;)
 
Regards

---

### Post by jmhdj on 2010-02-08
Hello guys. I am really impressed to see how much you can about dsdt repairing. I have problems with my dsdt file, and if anyone can see and help me here please do so. here sre warnigs i get and  dsdt file. Thanks forward


Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100121 [Feb  8 2010]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0

DSDT.dsl  2752:             Method (WMBA, 3, NotSerialized)
Warning  1088 -                        ^ Not all control paths return a value (WMBA)

DSDT.dsl  2840:             Method (_WED, 1, NotSerialized)
Warning  1081 -                        ^ Reserved method must return a value (_WED)

DSDT.dsl  3150:             Method (WMBE, 3, NotSerialized)
Warning  1088 -                        ^ Not all control paths return a value (WMBE)

DSDT.dsl  4367:                             P8XH (Zero, 0x0F)
Warning  1100 -       Statement is unreachable ^ 

DSDT.dsl  4430:                         Method (_BQC, 0, NotSerialized)
Warning  1088 -                                    ^ Not all control paths return a value (_BQC)

DSDT.dsl  4430:                         Method (_BQC, 0, NotSerialized)
Warning  1081 -                                    ^ Reserved method must return a value (_BQC)

DSDT.dsl  4616:                         Method (_BQC, 0, NotSerialized)
Warning  1088 -                                    ^ Not all control paths return a value (_BQC)

DSDT.dsl  4616:                         Method (_BQC, 0, NotSerialized)
Warning  1081 -                                    ^ Reserved method must return a value (_BQC)

DSDT.dsl  4851:                         P8XH (Zero, 0x1F)
Warning  1100 -   Statement is unreachable ^ 

DSDT.dsl  4895:                         P8XH (Zero, 0xF9)
Warning  1100 -   Statement is unreachable ^ 

DSDT.dsl  4908:                         P8XH (Zero, 0xFC)
Warning  1100 -   Statement is unreachable ^ 

DSDT.dsl  8352:                     Method (_GTM, 0, NotSerialized)
Warning  1088 -                                ^ Not all control paths return a value (_GTM)

DSDT.dsl  8352:                     Method (_GTM, 0, NotSerialized)
Warning  1081 -                                ^ Reserved method must return a value (_GTM)

DSDT.dsl  8513:                         Method (_GTF, 0, NotSerialized)
Warning  1088 -                                    ^ Not all control paths return a value (_GTF)

DSDT.dsl  8513:                         Method (_GTF, 0, NotSerialized)
Warning  1081 -                                    ^ Reserved method must return a value (_GTF)

DSDT.dsl  8581:                         Method (_GTF, 0, NotSerialized)
Warning  1088 -                                    ^ Not all control paths return a value (_GTF)

DSDT.dsl  8581:                         Method (_GTF, 0, NotSerialized)
Warning  1081 -                                    ^ Reserved method must return a value (_GTF)

DSDT.dsl  8654:                     Method (_GTM, 0, NotSerialized)
Warning  1088 -                                ^ Not all control paths return a value (_GTM)

DSDT.dsl  8654:                     Method (_GTM, 0, NotSerialized)
Warning  1081 -                                ^ Reserved method must return a value (_GTM)

DSDT.dsl  8815:                         Method (_GTF, 0, NotSerialized)
Warning  1088 -                                    ^ Not all control paths return a value (_GTF)

DSDT.dsl  8815:                         Method (_GTF, 0, NotSerialized)
Warning  1081 -                                    ^ Reserved method must return a value (_GTF)

DSDT.dsl  8883:                         Method (_GTF, 0, NotSerialized)
Warning  1088 -                                    ^ Not all control paths return a value (_GTF)

DSDT.dsl  8883:                         Method (_GTF, 0, NotSerialized)
Warning  1081 -                                    ^ Reserved method must return a value (_GTF)

DSDT.dsl  8988:                     Method (_GTM, 0, NotSerialized)
Warning  1088 -                                ^ Not all control paths return a value (_GTM)

DSDT.dsl  8988:                     Method (_GTM, 0, NotSerialized)
Warning  1081 -                                ^ Reserved method must return a value (_GTM)

DSDT.dsl  9148:                         Method (_GTF, 0, NotSerialized)
Warning  1088 -                                    ^ Not all control paths return a value (_GTF)

DSDT.dsl  9148:                         Method (_GTF, 0, NotSerialized)
Warning  1081 -                                    ^ Reserved method must return a value (_GTF)

DSDT.dsl  9216:                         Method (_GTF, 0, NotSerialized)
Warning  1088 -                                    ^ Not all control paths return a value (_GTF)

DSDT.dsl  9216:                         Method (_GTF, 0, NotSerialized)
Warning  1081 -                                    ^ Reserved method must return a value (_GTF)

DSDT.dsl  9289:                     Method (_GTM, 0, NotSerialized)
Warning  1088 -                                ^ Not all control paths return a value (_GTM)

DSDT.dsl  9289:                     Method (_GTM, 0, NotSerialized)
Warning  1081 -                                ^ Reserved method must return a value (_GTM)

DSDT.dsl  9449:                         Method (_GTF, 0, NotSerialized)
Warning  1088 -                                    ^ Not all control paths return a value (_GTF)

DSDT.dsl  9449:                         Method (_GTF, 0, NotSerialized)
Warning  1081 -                                    ^ Reserved method must return a value (_GTF)

DSDT.dsl  9517:                         Method (_GTF, 0, NotSerialized)
Warning  1088 -                                    ^ Not all control paths return a value (_GTF)

DSDT.dsl  9517:                         Method (_GTF, 0, NotSerialized)
Warning  1081 -                                    ^ Reserved method must return a value (_GTF)

ASL Input:  DSDT.dsl - 9592 lines, 326219 bytes, 4071 keywords
AML Output: dat.aml - 37175 bytes, 1024 named objects, 3047 executable opcodes

Compilation complete. 0 Errors, 35 Warnings, 0 Remarks, 36 Optimizations

---

### Post by 67GTA on 2010-02-08
I just looked at this post again after a long absence. I guess I didn't visit the thread after the last email notification. The forums won't notify you again until you visit the thread. I didn't realize all of the activity here. I have moved to Opensuse. The Novell devs fixed the dsdt patch that allows you to use a custom dsdt and apply it. EVERY other distro has just dropped it per Linus's wishes including Ubuntu. With 9.10 and beyond, you can no longer apply a custom dsdt without compiling your own kernel.  The idea was to make people file bugs against the kernel instead of fixing them through the dsdt. This is fine in most cases and is what I recommend you do first. If at that point you are one of the lucky people like me that has an ACPI bug due to a buggy dsdt that the kernel devs won't fix, then I will try to help you fix your dsdt, but do not want to try and help walk everyone through compiling a custom kernel to be able to apply the dsdt. I'm not trying to be a butt, but this can be very tricky with hundreds of pitfalls, and would be impossible to help you from here if you make a mistake and your OS won't boot. Anyone using 9.04 and older can still use this how to without problems. My ultimate suggestion would be to give Opensuse a try. I use KDE, so I can't vouch for the Gnome version. If anyone still wants help with their dsdt after reading this, and I haven't answered you, then you can reach me by email from my profile.

---

### Post by 67GTA on 2010-02-16
[COLOR=Red]Update:[/COLOR] There is now an argument going on over the inclusion of the dsdt patch in the Opensuse kernel. Version 2.6.31.8 had the patch. Another kernel dev removed it with the 2.6.31.12 update. So, as of right now, no distro supports a custom dsdt without rolling your own kernel. I guess the best avenue now is just to file a bug against the kernel and hope they can fix it.

---

### Post by cyberey66 on 2010-02-16
> **67GTA said:**
> [COLOR=Red]Update:[/COLOR] There is now an argument going on over the inclusion of the dsdt patch in the Opensuse kernel. Version 2.6.31.8 had the patch. Another kernel dev removed it with the 2.6.31.12 update. So, as of right now, no distro supports a custom dsdt without rolling your own kernel. I guess the best avenue now is just to file a bug against the kernel and hope they can fix it.

I was wondering about suse and that's a shame to hear since many laptops ship with DSDTs compiled by the MS compiler.

Do you happen to know if the latest patch suse used is posted anywhere?  It would be interesting to try and get it to work on an Ubuntu kernel.  It would only take one person to get it to work and many will benefit.

---

### Post by 67GTA on 2010-02-17
It was a private patch supplied by one of the Novell kernel devs and not officially supported (hence the removal by a higher rank). I actually asked if I could get the patch to use with Ubuntu, but never got a reply. I don't think they liked the request:-s

---

### Post by Favux on 2010-02-17
Hi 67GTA,

Thank you for your HOW TO and the associated thread!

I've been following it for about a year now, ever since I used your HOW TO to fix my DSDT (which I'm using right now).

I am sorry about losing the DSDT patch in OpenSUSE.  I followed that and it seemed like it only took the dev. a few days to fix the memory issue with it.  Sort of set to rest some of the arguments you were getting, didn't it?

I understand the argument about the community needing the error(s) in the DSDT submitted so that everyone benefits.  Rather than folks having 'private' patched DSDT's.

What really irritates me is that not once did anyone give you a time-line.  Or did I miss it?  I follow the kernel news a little so here is my guess.  I'm sure you have a more accurate idea.

1 month - avg. time for user to discover bug, trace it to bios, decompile DSDT, recompile and discover error(s), and find where to submit the DSDT.
1 month - time for review of the buggy DSDT, develop quirk and submission to kernel
1 month - time for kernel to review quirk and accept it.
3 months - minimum time for distro. to pick up kernel with quirk.  (I suppose quicker with a rolling distribution or if you import the kernel)

6 months - total elapsed time.  That would seem close to the minimum.  It wouldn't surprise me if the typical scenario is double that.

Does that sound close?

---

### Post by cyberey66 on 2010-02-18
> **Favux said:**
> Hi 67GTA,

Thank you for your HOW TO and the associated thread!

I've been following it for about a year now, ever since I used your HOW TO to fix my DSDT (which I'm using right now).

I am sorry about losing the DSDT patch in OpenSUSE.  I followed that and it seemed like it only took the dev. a few days to fix the memory issue with it.  Sort of set to rest some of the arguments you were getting, didn't it?

I understand the argument about the community needing the error(s) in the DSDT submitted so that everyone benefits.  Rather than folks having 'private' patched DSDT's.

What really irritates me is that not once did anyone give you a time-line.  Or did I miss it?  I follow the kernel news a little so here is my guess.  I'm sure you have a more accurate idea.

1 month - avg. time for user to discover bug, trace it to bios, decompile DSDT, recompile and discover error(s), and find where to submit the DSDT.
1 month - time for review of the buggy DSDT, develop quirk and submission to kernel
1 month - time for kernel to review quirk and accept it.
3 months - minimum time for distro. to pick up kernel with quirk.  (I suppose quicker with a rolling distribution or if you import the kernel)

6 months - total elapsed time.  That would seem close to the minimum.  It wouldn't surprise me if the typical scenario is double that.

Does that sound close?

If it's a common laptop, the correct DSDT is likely available as it is probable at least one person out of all the linux using owners fixed it.  Total time to locate and download DSDT, 1 day.  It still takes that long now, but you have to compile the kernel.

So for the bug reporting, what happens in the case of DSDT compiled with the microsoft compiler?

---

### Post by bruderjakob on 2010-02-25
Hey,

there is a problem in the dsdt of various acer timeline/travelmate notebooks as you can see there:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120")

it would be great when someone can help us out, if there is a patched dsdt i can test it.
what do you think where i should submit a patched dsdt that it can be build in the upcoming kernel releases?

thanks in advance! (and sorry for bad english)

jakob

---

### Post by 67GTA on 2010-02-25
Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 50 Optimizations

That was a buggy dsdt. This will only work with 9.04 and earlier. 9.10 and after will no longer allow you to use a custom dsdt. A dsdt file can not be put in the kernel. Hopefully the devs can see what I've fixed (assuming it helps you) and create a kernel fix. You can test this dsdt with 9.04 to see if your trouble is dsdt specific. If it is, then add the old and new dsdt's to your bug report. You might also want to go over the Ubuntu kernel devs head and also file one at the source: [http://www.kernel.org/pub/linux/docs/lkml/reporting-bugs.html](http://www.kernel.org/pub/linux/docs/lkml/reporting-bugs.html)

[http://bugzilla.kernel.org/](http://bugzilla.kernel.org/)

[ATTACH]148227[/ATTACH]

---

### Post by bruderjakob on 2010-02-26
Can't say how thankful i am!

I will start testing now and report later.

I think i try to compile own kernel with dsdt patch (i think i saw a 'how to' in my researches about dsdt); isn't it possible to take the same kernel in 9.04 from mainline kernels? otherwise i have to test with 9.04.

---

### Post by 67GTA on 2010-02-26
If you want to experiment, you can compile the dsdt into the 9.10 kernel. This seems to be the simplest method I've found. [http://ubuntuforums.org/showthread.php?t=1341580](http://ubuntuforums.org/showthread.php?t=1341580)
If your not sure about what a setting does while reconfiguring the kernel, just don't touch it, and you should be fine.

---

### Post by bruderjakob on 2010-02-26
i'm experimenting the whole day ;) learned a lot about things i hadn't done before, exactly the right timewasting for holidays :)

i've tried to compile latest kernel from mainline ppa in lucid -> doesn't work for suspend but one error message in /var/log/messages disappeared!

now i'm on 9.04 jaunty and have tried to follow up your how to, but seems it doesn't recognize the dsdt, but i will try it further the next hours.

for my surprising the hibernate works out of the box in jaunty, but maybe it's because i've set from ahci to ide mode in bios, not sure if i tested hibernate with this setting in karmic or lucid.

there was a few trouble about the version of iasl i'd used. takes me a lot time. but from now i think there are only a few steps to success ;)

---

### Post by 67GTA on 2010-02-26
Punctuation is essential. Make sure the dsdt is named DSDT.aml, and it is in the right folder.

---

### Post by bruderjakob on 2010-02-26
thanks, i've already recognized, that was the issue. but suspend doesn't work, tried also acpi_osi="linux" and various other acpi related bootflags.

i've figured out that suspend doesn't work from live cd or live usb either, further i can't do partitioning before cli or live cd install without triggered ahci in the bios, otherwise the installer crashes.
but when i boot after install with ahci i got something like this:
```

[   15.720046] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   16.540846] ata1.00: ACPI _SDD failed (AE 0x5)
[   16.553907] ata1.00: ACPI: failed the second time, disabled
```


which disappears in ide mode, but without any advantage.

any suggestions?

thanks for the help with this!

---

### Post by equin00x on 2010-02-27
67GTA help please, save me..

I got asus K52F laptop, and its have broken dsdt... unable to sleep | hibernate etc..

I am use ubuntu 10.04 alpha 3... 

Thank you very much!

---

### Post by arium84 on 2010-03-14
I only get warning when I compile mine which is ok right? only thing that worries me is laptop running hot?
When I scroll down to THERMAL ZONE there are FMIN and FMAX values which are presume are fan minimum and maximum speeds. 
Changing the FMIN to higher value didnt make any difference, 
wonder what I am doing wrong? 
perhaps temp sensor is not read correctly? :o

Laptop Compaq C793VU

---

### Post by macky_reddy on 2010-03-20
Hi gta67,
 
Even i am using dv6815nr laptop with F.32 bios and here am attaching my dsl and i want use this dsdt on snow leo. can u just help me out fixing & optimizing my dsdt. 
 
Well as u said even u use dv6815nr so it might be easier for u to optimize it.
 
Cheers in advance

---

### Post by popat007 on 2010-03-21
hi 67GTA,

 Grt.howto my lap. is sony and i use interpid 64bit. i compiled and got 200+ errors, could you please fix my dsdt.

Thank you

Here is my DSDT :

---

### Post by bruderjakob on 2010-03-25
> **bruderjakob said:**
> thanks, i've already recognized, that was the issue. but suspend doesn't work, tried also acpi_osi="linux" and various other acpi related bootflags.

i've figured out that suspend doesn't work from live cd or live usb either, further i can't do partitioning before cli or live cd install without triggered ahci in the bios, otherwise the installer crashes.
but when i boot after install with ahci i got something like this:
```

[   15.720046] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   16.540846] ata1.00: ACPI _SDD failed (AE 0x5)
[   16.553907] ata1.00: ACPI: failed the second time, disabled
```
which disappears in ide mode, but without any advantage.

any suggestions?

thanks for the help with this!



Ok, fixed then [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405120), it wasn't the DSDT, but thanks for fixing it. ;)

---

### Post by athena2284 on 2010-03-25
Hi 67GTA, let me join your dsdt party :)

Please help me fix mine, inspiron1464:
- dsdt recompile w/out error & warning
- can not resume from suspend
- overheat,  /sys/class/thermal/thermal_zone0/temp showing constant value, keep at 26800
- /sys/class/thermal/thermal_zone1/temp showing constant  value, keep at 0

Thank you

---

### Post by ivanmmj on 2010-03-25
I've got a Toshiba L505D with a severely broken DSDT table.
It has the bug outlined [here]("http://bugzilla.kernel.org/show_bug.cgi?id=14679").

(ACPI table overridden after boot)
The DSDT that overrides it is completely broken. The DSDT that we pull using the patch posted on that thread is slightly broken, too. It works, though. Unfortunately, the patch doesn't work on the Ubuntu kernel from git. I was hoping you guys could help us fix our DSDT table. (I'm running 10.04 right now, btw. But the problem is there on all Ubuntu versions (and every other non-windows OS, unfortunately...) 


Thanks guys!

---

### Post by jaci87 on 2010-04-01
Hi,
I have a similar issue described in post [#184]("http://ubuntuforums.org/showpost.php?p=7696584&postcount=184")...

```
Maximum error count (200) exceeded
dsdt.dsl    24:     External (^CPU0._PPC)
Error    4014 -  From ACPI CA Subsystem ^  (AE_NOT_FOUND Failure from lookup %s
)
```

and I see different behaviour with different kernels (interesting lines highlighted): 
- 2.6.31 (Karmic) 
```
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000f8480 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 7fed5bdd 0007C (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7fedfc6c 000F4 (v03 HP     30CC     06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 7fed703c 08BBC (v01 HP     30D2     06040000 INTL 20061109)
[    0.000000] ACPI: FACS 7fee2fc0 00040
[    0.000000] ACPI: HPET 7fedfd60 00038 (v01 HP     30D2     06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7fedfd98 0003C (v01 HP     30D2     06040000 LOHR 0000005A)
[    0.000000] ACPI: TMOR 7fedfdd4 00026 (v01 HP     30CC     06040000 PTL  00000003)
[    0.000000] ACPI: APIC 7fedfdfa 00068 (v01 HP     30D2     06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7fedfe62 00028 (v01 HP     30D2     06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 7fedfe8a 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 7fed6d5f 002DD (v01 HP     30D2     00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 7fed61e5 0025F (v01  HP    30D2     00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 7fed613f 000A6 (v01  HP    30D2     00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 7fed5c59 004E6 (v01  HP     30D2    00003000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.018987] ACPI: Core revision 20090521
[    0.164257] ACPI: bus type pci registered
[    0.169172] ACPI: EC: Enabling special treatment for EC from MSI.
[    0.169175] ACPI: EC: Look up EC in DSDT
[    0.173050] ACPI: BIOS _OSI(Linux) query ignored
[    0.174441] ACPI: Interpreter enabled
[    0.174451] ACPI: (supports S0 S3 S4 S5)
[    0.174475] ACPI: Using IOAPIC for interrupt routing
[    0.176308] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.200667] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.200671] ACPI: EC: driver started in interrupt mode
[    0.201078] ACPI: No dock devices found.
[    0.201743] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.204983] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.207486] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.207741] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.207851] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.207950] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.208052] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.208178] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.218415] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.218542] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.218666] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.218789] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.218911] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.219034] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.219156] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.219278] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.219508] ACPI: WMI: Mapper loaded
[    0.219508] PCI: Using ACPI for IRQ routing
[    0.248010] pnp: PnP ACPI init
[    0.248023] ACPI: bus type pnp registered
[    0.254295] pnp: PnP ACPI: found 11 devices
[    0.254297] ACPI: ACPI bus type pnp unregistered
[    0.254301] PnPBIOS: Disabled by ACPI PNP
[    0.544179] ACPI: AC Adapter [ACAD] (on-line)
[    0.544273] ACPI: Power Button [PWRF]
[    0.544338] ACPI: Power Button [PWRB]
[    0.544392] ACPI: Sleep Button [SLPB]
[    0.547297] ACPI: Lid Switch [LID]
[    0.548058] ACPI: SSDT 7fed6aa1 001F6 (v01  HP    30D2     00003000 INTL 20061109)
[    0.548683] ACPI: SSDT 7fed6444 005D8 (v01  HP    30D2     00003001 INTL 20061109)
[B][    0.551391] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.551425] ACPI: Processor [CPU0] (supports 8 throttling states)[/B]
[    0.551840] ACPI: SSDT 7fed6c97 000C8 (v01  HP    30D2     00003000 INTL 20061109)
[    0.552307] ACPI: SSDT 7fed6a1c 00085 (v01  HP    30D2     00003000 INTL 20061109)
[B][    0.553449] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.553483] ACPI: Processor [CPU1] (supports 8 throttling states)[/B]
**[    0.561126] ACPI Exception: AE_OK, No or invalid critical threshold 20090521 thermal-384**
[    0.722184] ACPI: Battery Slot [BAT0] (battery present)
[    1.241219] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.242690] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    1.561311] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   15.682025] nvidia 0000:01:00.0: power state changed by ACPI to D0

```

- 2.6.32 (Lucid)
```
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000f8480 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 7fed5bdd 0007C (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7fedfc6c 000F4 (v03 HP     30CC     06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 7fed703c 08BBC (v01 HP     30D2     06040000 INTL 20061109)
[    0.000000] ACPI: FACS 7fee2fc0 00040
[    0.000000] ACPI: HPET 7fedfd60 00038 (v01 HP     30D2     06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7fedfd98 0003C (v01 HP     30D2     06040000 LOHR 0000005A)
[    0.000000] ACPI: TMOR 7fedfdd4 00026 (v01 HP     30CC     06040000 PTL  00000003)
[    0.000000] ACPI: APIC 7fedfdfa 00068 (v01 HP     30D2     06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7fedfe62 00028 (v01 HP     30D2     06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 7fedfe8a 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 7fed6d5f 002DD (v01 HP     30D2     00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 7fed61e5 0025F (v01  HP    30D2     00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 7fed613f 000A6 (v01  HP    30D2     00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 7fed5c59 004E6 (v01  HP     30D2    00003000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.023195] ACPI: Core revision 20090903
[    0.177420] ACPI: bus type pci registered
[    0.209457] ACPI: EC: Look up EC in DSDT
[B][    0.210916] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.210924] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_._OSC] (Node f700f648), AE_NOT_FOUND[/B]
[    0.213385] ACPI: BIOS _OSI(Linux) query ignored
[    0.214790] ACPI: Interpreter enabled
[    0.214807] ACPI: (supports S0 S3 S4 S5)
[    0.214833] ACPI: Using IOAPIC for interrupt routing
[    0.224177] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.224609] ACPI: No dock devices found.
[    0.225293] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.226933] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.229476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.229734] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.229849] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.229950] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.230041] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.230173] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.241506] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.241635] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.241764] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.241889] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.242014] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.242138] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.242262] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.242385] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.243129] ACPI: WMI: Mapper loaded
[    0.243131] PCI: Using ACPI for IRQ routing
[    0.250606] pnp: PnP ACPI init
[    0.250623] ACPI: bus type pnp registered
[    0.253927] pnp: PnP ACPI: found 11 devices
[    0.253930] ACPI: ACPI bus type pnp unregistered
[    0.253935] PnPBIOS: Disabled by ACPI PNP
[    0.308201] ACPI: AC Adapter [ACAD] (on-line)
[    0.308301] ACPI: Power Button [PWRB]
[    0.308358] ACPI: Sleep Button [SLPB]
[    0.308749] ACPI: Lid Switch [LID]
[    0.308827] ACPI: Power Button [PWRF]
[    0.309600] ACPI: SSDT 7fed6aa1 001F6 (v01  HP    30D2     00003000 INTL 20061109)
[    0.310229] ACPI: SSDT 7fed6444 005D8 (v01  HP    30D2     00003001 INTL 20061109)
[    0.313443] ACPI: SSDT 7fed6c97 000C8 (v01  HP    30D2     00003000 INTL 20061109)
[    0.313882] ACPI: SSDT 7fed6a1c 00085 (v01  HP    30D2     00003000 INTL 20061109)
**[    0.324756] ACPI Exception: AE_OK, No or invalid critical threshold (20090903/thermal-386)**
[    0.526266] ACPI: Battery Slot [BAT0] (battery present)
[    1.213397] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.215068] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    4.441526] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    6.326842] nouveau 0000:01:00.0: power state changed by ACPI to D0

```


What's the matter ?

---

### Post by 67GTA on 2010-04-01
jaci87:

Change ```
(^CPU0._PPC)
``` to ```
(\_PR.CPU0._PPC)
``` rerun iasl -tc to get your error count down to a manageable number.

---

### Post by jaci87 on 2010-04-02
Much better now, this is the report:
```
dsdt.dsl  3252:             Method (_HOT, 0, Serialized)
Warning  1087 -                        ^ Not all control paths return a value (_HOT)

dsdt.dsl  3252:             Method (_HOT, 0, Serialized)
Warning  1080 -                        ^ Reserved method must return a value (_HOT)

dsdt.dsl  3267:             Method (_CRT, 0, Serialized)
Warning  1087 -                        ^ Not all control paths return a value (_CRT)

dsdt.dsl  3267:             Method (_CRT, 0, Serialized)
Warning  1080 -                        ^ Reserved method must return a value (_CRT)

dsdt.dsl  7275:                     Method (_Q16, 0, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (_Q16)

```

Look at the methods:
```
Method (_HOT, 0, Serialized)
            {
                If (LEqual (OSYS, 0x07D6))
                {
                    If (LEqual (\_SB.TJ85, Zero))
                    {
                        Return (Add (0x0AAC, Multiply (TPC, 0x0A)))
                    }
                    Else
                    {
                        Return (Add (0x0AAC, Multiply (TP85, 0x0A)))
                    }
                }
            }

Method (_CRT, 0, Serialized)
            {
                If (LLess (OSYS, 0x07D6))
                {
                    If (LEqual (\_SB.TJ85, Zero))
                    {
                        Return (Add (0x0AAC, Multiply (TPC, 0x0A)))
                    }
                    Else
                    {
                        Return (Add (0x0AAC, Multiply (TP85, 0x0A)))
                    }
                }
            }
```

```
Method (_Q16, 0, NotSerialized)
                    {
                        Store ("!!! DVD/Music Button pressed !!!", Debug)
                        Store (QBBB, Local0)
                        If (LEqual (Local0, 0x03))
                        {
                            Notify (MBTN, 0x02)
                            Return (Zero)
                        }

                        If (LEqual (Local0, 0x06))
                        {
                            Notify (PBTN, 0x02)
                            Return (Zero)
                        }

                        If (LEqual (Local0, 0x12))
                        {
                            Notify (VBTN, 0x02)
                            Return (Zero)
                        }

                        If (LEqual (Local0, 0x11))
                        {
                            Notify (TBTN, 0x02)
                            Return (Zero)
                        }

                        Store (0x04, ^^^^WMID.Z014)
                        Store (Zero, ^^^^WMID.Z015)
                        Notify (WMID, 0x80)
                    }
```

Does the first warnings refer to "does not return anything if first if is not entered" ?
OSYS variable can store the following:
```
                If (_OSI ("Windows 2001"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP1"))
                {
                    Store (0x07D1, OSYS)
                }

                If (_OSI ("Windows 2001 SP2"))
                {
                    Store (0x07D2, OSYS)
                }

                If (_OSI ("Windows 2006"))
                {
                    Store (0x07D6, OSYS)
                }
            }
```
So could I gain benefits from booting with acpi_osi="Windows 2006" grub2 option ?


Anyway, thanks in advance. :)

---

### Post by 67GTA on 2010-04-02
What is your PC model? You might be able to just use my dsdt. Mine is HP dv6815nr.

---

### Post by jaci87 on 2010-04-02
> **67GTA said:**
> What is your PC model? You might be able to just use my dsdt. Mine is HP dv6815nr.

It's HP dv6635el.

---

### Post by 67GTA on 2010-04-02
That's not close enough. There will be different hardware. I am working on several dsdt's at the moment. If you want to attach a copy of yours here, I will try to fix it. Mine has similar problems with hot and crt. This causes the kernel to not see your cpu temp, and then causes a noisy fan. The q16 error is for windows only, but we can shut it up.

---

### Post by jaci87 on 2010-04-02
> **67GTA said:**
> If you want to attach a copy of yours here, I will try to fix it.

Thank you very much.

---

### Post by 67GTA on 2010-04-02
I've actually moved to Opensuse, and only check this thread occasionally to see if there are any new help requests. I have about 10 dsdt's to fix, so it might take a couple of days.

---

### Post by jaci87 on 2010-04-02
> **67GTA said:**
> I've actually moved to Opensuse, and only check this thread occasionally to see if there are any new help requests. I have about 10 dsdt's to fix, so it might take a couple of days.
Oh no problem, take your time. :)

---

### Post by 67GTA on 2010-04-02
[attach]152222[/attach]

[attach]152223[/attach]

[attach]152224[/attach]

[attach]152225[/attach]

[attach]152226[/attach]

---

### Post by 67GTA on 2010-04-02
ivanmmj: I am stuck on the last four errors for yours. It will take some more investigating.

equin00x: Is this the original without changes, or maybe a custom machine? Send me a fresh dsdt.dsl if you previously made any changes to the one you sent. If this is a custom machine, the dsdt will not matter. You have 201+ errors, and every one says objects don't exist that your bios is telling it to look for.

---

### Post by arium84 on 2010-04-03
Hello 67GTA! Thank you so so much! You just made my day!
[]("http://ubuntuforums.org/member.php?u=231204")Have a Happy Easter! :KS:KS:KS:KS:KS:KS:KS:KS

---

### Post by rock_ksa on 2010-04-05
Hello, I got only 12 warning, no errors , should I correct them ?! I have attched 
the required files ,please if u dont mind to check them 

I got HP TouchSmart tx2z 
Ubutnu 9.10


And sorry for my English

---

### Post by jaci87 on 2010-04-05
Hi 67GTA, thanks for the fixed dsdt.
iasl now gives me 0 Errors, 0 Warnings, 0 Remarks, and 44 Optimizations
However, still the same errors on dmesg:
```
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000f8480 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 7fed5bdd 0007C (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7fedfc6c 000F4 (v03 HP     30CC     06040000 ALAN 00000001)
[    0.000000] ACPI: Override [DSDT-30D2    ], this is unsafe: tainting kernel
[    0.000000] ACPI: DSDT @ 0x7fed703c Table override, replaced with:
[    0.000000] ACPI: DSDT c0768e5c 08BC2 (v01 HP     30D2     06040000 INTL 20090521)
[    0.000000] ACPI: FACS 7fee2fc0 00040
[    0.000000] ACPI: HPET 7fedfd60 00038 (v01 HP     30D2     06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7fedfd98 0003C (v01 HP     30D2     06040000 LOHR 0000005A)
[    0.000000] ACPI: TMOR 7fedfdd4 00026 (v01 HP     30CC     06040000 PTL  00000003)
[    0.000000] ACPI: APIC 7fedfdfa 00068 (v01 HP     30D2     06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7fedfe62 00028 (v01 HP     30D2     06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 7fedfe8a 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 7fed6d5f 002DD (v01 HP     30D2     00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 7fed61e5 0025F (v01  HP    30D2     00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 7fed613f 000A6 (v01  HP    30D2     00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 7fed5c59 004E6 (v01  HP     30D2    00003000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.023195] ACPI: Core revision 20090903
[    0.165419] ACPI: bus type pci registered
[    0.193524] ACPI: EC: Look up EC in DSDT
[B][    0.194913] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.194921] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_._OSC] (Node f700f648), AE_NOT_FOUND[/B]
[    0.197130] ACPI: BIOS _OSI(Linux) query ignored
[    0.198456] ACPI: Interpreter enabled
[    0.198473] ACPI: (supports S0 S3 S4 S5)
[    0.198500] ACPI: Using IOAPIC for interrupt routing
[    0.205279] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.208074] ACPI: No dock devices found.
[    0.208511] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.210151] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.212708] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.212945] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.213051] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.213145] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.213230] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.213352] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.224714] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.224831] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.224946] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.225057] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.225168] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.225280] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.225390] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.225501] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.226246] ACPI: WMI: Mapper loaded
[    0.226249] PCI: Using ACPI for IRQ routing
[    0.234593] pnp: PnP ACPI init
[    0.234611] ACPI: bus type pnp registered
[    0.237524] pnp: PnP ACPI: found 11 devices
[    0.237528] ACPI: ACPI bus type pnp unregistered
[    0.237533] PnPBIOS: Disabled by ACPI PNP
[    0.291456] ACPI: AC Adapter [ACAD] (on-line)
[    0.291556] ACPI: Power Button [PWRB]
[    0.291613] ACPI: Sleep Button [SLPB]
[    0.292016] ACPI: Lid Switch [LID]
[    0.292093] ACPI: Power Button [PWRF]
[    0.292858] ACPI: SSDT 7fed6aa1 001F6 (v01  HP    30D2     00003000 INTL 20061109)
[    0.293490] ACPI: SSDT 7fed6444 005D8 (v01  HP    30D2     00003001 INTL 20061109)
[    0.296660] ACPI: SSDT 7fed6c97 000C8 (v01  HP    30D2     00003000 INTL 20061109)
[    0.297098] ACPI: SSDT 7fed6a1c 00085 (v01  HP    30D2     00003000 INTL 20061109)
**[    0.308715] ACPI Exception: AE_OK, No or invalid critical threshold (20090903/thermal-386)**
[    0.384555] ACPI: Battery Slot [BAT0] (battery present)
[    1.213212] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.214872] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[   11.414650] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   12.441086] nouveau 0000:01:00.0: power state changed by ACPI to D0
```

I strongly think it's a kernel bug. :mad:

---

### Post by 67GTA on 2010-04-06
> **jaci87 said:**
> Hi 67GTA, thanks for the fixed dsdt.
iasl now gives me 0 Errors, 0 Warnings, 0 Remarks, and 44 Optimizations
However, still the same errors on dmesg:
```
[    0.000000]  BIOS-e820: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fed0000 - 000000007fee3000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000f8480 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 7fed5bdd 0007C (v01 HPQOEM SLIC-MPC 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7fedfc6c 000F4 (v03 HP     30CC     06040000 ALAN 00000001)
[    0.000000] ACPI: Override [DSDT-30D2    ], this is unsafe: tainting kernel
[    0.000000] ACPI: DSDT @ 0x7fed703c Table override, replaced with:
[    0.000000] ACPI: DSDT c0768e5c 08BC2 (v01 HP     30D2     06040000 INTL 20090521)
[    0.000000] ACPI: FACS 7fee2fc0 00040
[    0.000000] ACPI: HPET 7fedfd60 00038 (v01 HP     30D2     06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7fedfd98 0003C (v01 HP     30D2     06040000 LOHR 0000005A)
[    0.000000] ACPI: TMOR 7fedfdd4 00026 (v01 HP     30CC     06040000 PTL  00000003)
[    0.000000] ACPI: APIC 7fedfdfa 00068 (v01 HP     30D2     06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7fedfe62 00028 (v01 HP     30D2     06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 7fedfe8a 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 7fed6d5f 002DD (v01 HP     30D2     00001000 INTL 20061109)
[    0.000000] ACPI: SSDT 7fed61e5 0025F (v01  HP    30D2     00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 7fed613f 000A6 (v01  HP    30D2     00003000 INTL 20061109)
[    0.000000] ACPI: SSDT 7fed5c59 004E6 (v01  HP     30D2    00003000 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.023195] ACPI: Core revision 20090903
[    0.165419] ACPI: bus type pci registered
[    0.193524] ACPI: EC: Look up EC in DSDT
[B][    0.194913] ACPI Error (psargs-0359): [CDW1] Namespace lookup failure, AE_NOT_FOUND
[    0.194921] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_._OSC] (Node f700f648), AE_NOT_FOUND[/B]
[    0.197130] ACPI: BIOS _OSI(Linux) query ignored
[    0.198456] ACPI: Interpreter enabled
[    0.198473] ACPI: (supports S0 S3 S4 S5)
[    0.198500] ACPI: Using IOAPIC for interrupt routing
[    0.205279] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.208074] ACPI: No dock devices found.
[    0.208511] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.210151] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.212708] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.212945] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.213051] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.213145] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.213230] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.213352] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.224714] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.224831] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.224946] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.225057] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.225168] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.225280] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.225390] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.225501] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.226246] ACPI: WMI: Mapper loaded
[    0.226249] PCI: Using ACPI for IRQ routing
[    0.234593] pnp: PnP ACPI init
[    0.234611] ACPI: bus type pnp registered
[    0.237524] pnp: PnP ACPI: found 11 devices
[    0.237528] ACPI: ACPI bus type pnp unregistered
[    0.237533] PnPBIOS: Disabled by ACPI PNP
[    0.291456] ACPI: AC Adapter [ACAD] (on-line)
[    0.291556] ACPI: Power Button [PWRB]
[    0.291613] ACPI: Sleep Button [SLPB]
[    0.292016] ACPI: Lid Switch [LID]
[    0.292093] ACPI: Power Button [PWRF]
[    0.292858] ACPI: SSDT 7fed6aa1 001F6 (v01  HP    30D2     00003000 INTL 20061109)
[    0.293490] ACPI: SSDT 7fed6444 005D8 (v01  HP    30D2     00003001 INTL 20061109)
[    0.296660] ACPI: SSDT 7fed6c97 000C8 (v01  HP    30D2     00003000 INTL 20061109)
[    0.297098] ACPI: SSDT 7fed6a1c 00085 (v01  HP    30D2     00003000 INTL 20061109)
**[    0.308715] ACPI Exception: AE_OK, No or invalid critical threshold (20090903/thermal-386)**
[    0.384555] ACPI: Battery Slot [BAT0] (battery present)
[    1.213212] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.214872] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[   11.414650] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   12.441086] nouveau 0000:01:00.0: power state changed by ACPI to D0
```I strongly think it's a kernel bug. :mad:

Yes, but the kernel is working around the errors. I would file a kernel bug at [https://bugzilla.kernel.org/](https://bugzilla.kernel.org/)

---

### Post by 67GTA on 2010-04-06
> **hosein110 said:**
> hi.......programer. I don't speak machine language. I have googled for the corrections to make to my dsdt.dsl file and I can't find any of the errors that I'm getting. So, I'm going to have to go back to Hardy Heron because everything (except for sound capture which still doesn't work on this laptop) worked in Hardy. Just finding a work around doesn't help the community. this needs to be fixed by someone who knows what they're doing at the source code level... right?

or am i missing something?

Grace and Peace,
Matt

You are mostly right. Ubuntu usually includes newer versions of software that may still have bugs to work out(Debian sid). You have to file bugs with the original authors of the packages your having trouble with such as alsa for sound. The Ubuntu devs mostly rely on bug fixes to float down stream from other projects. Other distros like Debian, Opensuse, Fedora, etc will work to fix bugs and send patches upstream to benefit others. With Ubuntu you are mostly out of luck because bugs usually don't get fixed until the next release when they pull in updated packages from Debian unstable, which in turn, introduces new bugs, and on and on...

---

### Post by 67GTA on 2010-04-06
rock_kas:

[ATTACH]152520[/ATTACH]

---

### Post by popat007 on 2010-04-07
hi 67GTA,

   i applied command > sudo update-initramfs -u -k 2.6.27-17-generic and got the error ```
.: 17: Can't open /etc/default/console-setup
```

I dont know what is wrong i am doing, can you pls. look it.

Thanks

---

### Post by 67GTA on 2010-04-07
This was a bug that was supposed to be fixed. Gzip was missing from the initramfs image, so it wasn't able to uncompress it while updating. Make sure you are up to date. You can try running ```
sudo /etc/init.d/console-setup restart

``` to maybe temporarily work around it. Then try updating the initramfs image.

---

### Post by 67GTA on 2010-04-07
> **ivanmmj said:**
> I've got a Toshiba L505D with a severely broken DSDT table.
It has the bug outlined [here]("http://bugzilla.kernel.org/show_bug.cgi?id=14679").

(ACPI table overridden after boot)
The DSDT that overrides it is completely broken. The DSDT that we pull using the patch posted on that thread is slightly broken, too. It works, though. Unfortunately, the patch doesn't work on the Ubuntu kernel from git. I was hoping you guys could help us fix our DSDT table. (I'm running 10.04 right now, btw. But the problem is there on all Ubuntu versions (and every other non-windows OS, unfortunately...) 


Thanks guys!

I can't get yours to compile. It only gets worse. There is at least one fatal flaw, but with 12,000 lines of code, I will never find it. Have you tried updating your bios? It might help if you could send me a copy of your dmesg output.

---

### Post by popat007 on 2010-04-08
hi 67GTA,
  I reinstall console-setup and the problem is gone, now it did manage the command ```
sudo update-initramfs -u -k 2.6.27-17-generic
```
how do i know i have 0 errors and 0 warnings.

Thank you

---

### Post by 67GTA on 2010-04-08
The dsdt I sent you has no errors or warnings, but that may not mean that you still don't have problems caused by other things other than the dsdt. You can run ```
dmesg
``` in a terminal to see any boot or kernel errors. Just make sure to expand your terminal scroll memory in the terminal profile preferences, because this command spits out a lot of info and will cut some of it off. I would change it to something around 3000. I think the default is 512.

PS If you prefer a text file readout, just run ```
dmesg > dmesg
``` This will put all of the output into a file called dmesg into your home folder.

---

### Post by popat007 on 2010-04-08
i outputed dmesg to dmesg file and i see custom dsdt is in use and ```
BIOS _OSI(Linux) query honored via cmdline
``` is also used.

---

### Post by ericw12 on 2010-04-18
I have quite a lot 'Object does not exist" message....any idea?

./dsdt_fixed.txt    44:         \_SB.ODGW (Or (0x5500, Arg0))
Error    4063 -   Object does not exist ^  (\_SB.ODGW)

./dsdt_fixed.txt    47:             Store (0x00, \_SB.PCI0.LPCB.EC0.HSST)
Error    4063 -                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.HSST)

./dsdt_fixed.txt    48:             Store (\_SB.PCI0.RP03.PDSX, IECP)
Error    4063 -                        Object does not exist ^  (\_SB.PCI0.RP03.PDSX)

./dsdt_fixed.txt    49:             Store (\_SB.PCI0.RP05.PDSX, DECP)
Error    4063 -                        Object does not exist ^  (\_SB.PCI0.RP05.PDSX)

./dsdt_fixed.txt    52:                 \_SB.PCI0.LPCB.EC0.BTDR (0x00)
Error    4063 -                         Object does not exist ^  (\_SB.PCI0.LPCB.EC0.BTDR)

./dsdt_fixed.txt    53:                 Store (0x01, \_SB.NFBS)
Error    4063 -                        Object does not exist ^  (\_SB.NFBS)

./dsdt_fixed.txt    56:                     Store (\_SB.LID._LID (), LSTA)
Error    4063 -                          Object does not exist ^  (\_SB.LID._LID)

./dsdt_fixed.txt    65:         \_SB.ODGW (Or (0x5600, Arg0))
Error    4063 -   Object does not exist ^  (\_SB.ODGW)

./dsdt_fixed.txt    68:             \_SB.SSMI (0xEA80, 0x00, 0x00, 0x00, 0x00)
Error    4063 -       Object does not exist ^  (\_SB.SSMI)

./dsdt_fixed.txt    71:         \_SB.PCI0.LPCB.EC0.ITLB ()
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.LPCB.EC0.ITLB)

./dsdt_fixed.txt    72:         \_SB.PCI0.LPCB.EC0.RPPC ()
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.LPCB.EC0.RPPC)

./dsdt_fixed.txt    73:         If (\_SB.PCI0.LPCB.EC0.ECRG)
Error    4063 -                     Object does not exist ^  (\_SB.PCI0.LPCB.EC0.ECRG)

./dsdt_fixed.txt    75:             Acquire (\_SB.PCI0.LPCB.EC0.ECMX, 0xFFFF)
Error    4063 -                              Object does not exist ^  (\_SB.PCI0.LPCB.EC0.ECMX)

./dsdt_fixed.txt    76:             Store (0x01, \_SB.PCI0.LPCB.EC0.ACPI)
Error    4063 -                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.ACPI)

./dsdt_fixed.txt    77:             Store (0x00, \_SB.PCI0.LPCB.EC0.SLPT)
Error    4063 -                                  Object does not exist ^  (\_SB.PCI0.LPCB.EC0.SLPT)

./dsdt_fixed.txt    78:             Release (\_SB.PCI0.LPCB.EC0.ECMX)
Error    4063 -                              Object does not exist ^  (\_SB.PCI0.LPCB.EC0.ECMX)

./dsdt_fixed.txt    83:             \_TZ.RETD ()
Error    4063 -       Object does not exist ^  (\_TZ.RETD)

./dsdt_fixed.txt    84:             \_TZ.INTM (0x01)
Error    4063 -       Object does not exist ^  (\_TZ.INTM)

./dsdt_fixed.txt    85:             Store (0x01, \_SB.NFBS)
Error    4063 -                    Object does not exist ^  (\_SB.NFBS)

./dsdt_fixed.txt    88:                 If (XOr (\_SB.LID._LID (), LSTA))
Error    4063 -                        Object does not exist ^  (\_SB.LID._LID)

./dsdt_fixed.txt    90:                     XOr (GIV, 0x2000, Local0)
Error    4063 -              Object does not exist ^  (GIV_)

./dsdt_fixed.txt    91:                     Store (Local0, GIV)
Error    4063 -                        Object does not exist ^  (GIV_)

./dsdt_fixed.txt    97:                 \_SB.WMID.WGWE (0x05, 0x00)
Error    4063 -                Object does not exist ^  (\_SB.WMID.WGWE)

./dsdt_fixed.txt   101:         If (LOr (LEqual (Arg0, 0x04), LEqual (\WCOS (), 0x01)))
Error    4063 -                                     Object does not exist ^  (\WCOS)

./dsdt_fixed.txt   103:             Notify (\_SB.SLPB, 0x02)
Error    4063 -               Object does not exist ^  (\_SB.SLPB)

./dsdt_fixed.txt   106:         Store (\_SB.PCI0.LPCB.EC0.GACS (), Local2)
Error    4063 -                        Object does not exist ^  (\_SB.PCI0.LPCB.EC0.GACS)

./dsdt_fixed.txt   107:         \_SB.PCI0.LPCB.EC0.PWUP (0x03, 0xFF)
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.LPCB.EC0.PWUP)

./dsdt_fixed.txt   108:         Store (\_SB.PCI0.LPCB.EC0.GBAP (), Local1)
Error    4063 -                        Object does not exist ^  (\_SB.PCI0.LPCB.EC0.GBAP)

./dsdt_fixed.txt   109:         Store (\_SB.PCI0.LPCB.EC0.GACS (), Local3)
Error    4063 -                        Object does not exist ^  (\_SB.PCI0.LPCB.EC0.GACS)

./dsdt_fixed.txt   113:             Notify (\_SB.AC, 0x80)
Error    4063 -             Object does not exist ^  (\_SB.AC)

./dsdt_fixed.txt   120:                 XOr (Local2, 0x01, \_SB.ACST)
Error    4063 -                              Object does not exist ^  (\_SB.ACST)

./dsdt_fixed.txt   124:         WKET (Arg0)
Error    4063 -                    ^ Object does not exist (WKET)

./dsdt_fixed.txt   125:         \_SB.VWAK (Arg0, \_SB.VWAK (0x01, Store (\_SB.HST1.GHID (), Local0), \_SB.PCI0.ACEL.ITAL ()))
Error    4063 -                                                 Object does not exist ^  (\_SB.HST1.GHID)

./dsdt_fixed.txt   125:         \_SB.VWAK (Arg0, \_SB.VWAK (0x01, Store (\_SB.HST1.GHID (), Local0), \_SB.PCI0.ACEL.ITAL ()))
Error    4063 -                                                                                  Object does not exist ^  (\_SB.PCI0.ACEL.ITAL)

./dsdt_fixed.txt   133:             \_SB.ODBG (Arg1)
Error    4063 -       Object does not exist ^  (\_SB.ODBG)

./dsdt_fixed.txt   139:             \_SB.ODG1 (Arg1)
Error    4063 -       Object does not exist ^  (\_SB.ODG1)

./dsdt_fixed.txt   253:                 Notify (\_PR.CPU1, 0x80)
Error    4063 -                   Object does not exist ^  (\_PR.CPU1)

./dsdt_fixed.txt   257:                     Notify (\_PR.CPU1, 0x81)
Error    4063 -                       Object does not exist ^  (\_PR.CPU1)

./dsdt_fixed.txt   274:             Store (0x00, TRP0)
Error    4063 -               Object does not exist ^  (TRP0)

./dsdt_fixed.txt   280:             Store (0x00, TRPD)
Error    4063 -               Object does not exist ^  (TRPD)

./dsdt_fixed.txt   286:             Store (0x00, TRPH)
Error    4063 -               Object does not exist ^  (TRPH)

./dsdt_fixed.txt   332:             \_TZ.BOTT ()
Error    4063 -       Object does not exist ^  (\_TZ.BOTT)

./dsdt_fixed.txt   333:             \_TZ.RETD ()
Error    4063 -       Object does not exist ^  (\_TZ.RETD)

./dsdt_fixed.txt   581:             \_TZ.THEV ()
Error    4063 -       Object does not exist ^  (\_TZ.THEV)

./dsdt_fixed.txt   587:             \_SB.PCI0.RP01.HPLG ()
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.RP01.HPLG)

./dsdt_fixed.txt   588:             \_SB.PCI0.RP02.HPLG ()
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.RP02.HPLG)

./dsdt_fixed.txt   589:             \_SB.PCI0.RP03.HPLG ()
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.RP03.HPLG)

./dsdt_fixed.txt   590:             \_SB.PCI0.RP04.HPLG ()
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.RP04.HPLG)

./dsdt_fixed.txt   591:             \_SB.PCI0.RP05.HPLG ()
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.RP05.HPLG)

./dsdt_fixed.txt   592:             \_SB.PCI0.RP06.HPLG ()
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.RP06.HPLG)

./dsdt_fixed.txt   597:             Store (0x00, GPEC)
Error    4063 -               Object does not exist ^  (GPEC)

./dsdt_fixed.txt   609:                     \_SB.WMID.WGWE (Local0, 0x00)
Error    4063 -                    Object does not exist ^  (\_SB.WMID.WGWE)

./dsdt_fixed.txt   614:                     Acquire (\_TZ.THER, 0xFFFF)
Error    4063 -                        Object does not exist ^  (\_TZ.THER)

./dsdt_fixed.txt   615:                     Or (\_TZ.THSC, 0x01, \_TZ.THSC)
Error    4063 -                   Object does not exist ^  (\_TZ.THSC)

./dsdt_fixed.txt   615:                     Or (\_TZ.THSC, 0x01, \_TZ.THSC)
Error    4063 -                                    Object does not exist ^  (\_TZ.THSC)

./dsdt_fixed.txt   616:                     Release (\_TZ.THER)
Error    4063 -                        Object does not exist ^  (\_TZ.THER)

./dsdt_fixed.txt   617:                     Notify (\_TZ.DTSZ, 0x80)
Error    4063 -                       Object does not exist ^  (\_TZ.DTSZ)

./dsdt_fixed.txt   622:                     VBRE (0x87, If (LEqual (Local0, 0x02))
Error    4095 -                                          ^ syntax error, unexpected PARSEOP_IF, expecting ',' or ')'

./dsdt_fixed.txt   622:                     VBRE (0x87, If (LEqual (Local0, 0x02))
Error    4095 -                                     syntax error, unexpected ')' ^ 

./dsdt_fixed.txt   622:                     VBRE (0x87, If (LEqual (Local0, 0x02))
Warning  1105 -               Result is not used, operator has no effect ^ 

./dsdt_fixed.txt   625:                         })
Error    4095 -     syntax error, unexpected ')' ^ 

./dsdt_fixed.txt   632:             Notify (\_SB.PCI0.USB1, 0x02)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.USB1)

./dsdt_fixed.txt   637:             Notify (\_SB.PCI0.USB2, 0x02)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.USB2)

./dsdt_fixed.txt   642:             Notify (\_SB.PCI0.USB5, 0x02)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.USB5)

./dsdt_fixed.txt   647:             \_SB.PCI0.RP01.PME ()
Error    4063 -                Object does not exist ^  (\_SB.PCI0.RP01.PME)

./dsdt_fixed.txt   648:             \_SB.PCI0.RP02.PME ()
Error    4063 -                Object does not exist ^  (\_SB.PCI0.RP02.PME)

./dsdt_fixed.txt   649:             \_SB.PCI0.RP03.PME ()
Error    4063 -                Object does not exist ^  (\_SB.PCI0.RP03.PME)

./dsdt_fixed.txt   650:             \_SB.PCI0.RP04.PME ()
Error    4063 -                Object does not exist ^  (\_SB.PCI0.RP04.PME)

./dsdt_fixed.txt   651:             \_SB.PCI0.RP05.PME ()
Error    4063 -                Object does not exist ^  (\_SB.PCI0.RP05.PME)

./dsdt_fixed.txt   652:             \_SB.PCI0.RP06.PME ()
Error    4063 -                Object does not exist ^  (\_SB.PCI0.RP06.PME)

./dsdt_fixed.txt   657:             Notify (\_SB.PCI0.PCIB, 0x02)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.PCIB)

./dsdt_fixed.txt   662:             Notify (\_SB.PCI0.USB3, 0x02)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.USB3)

./dsdt_fixed.txt   667:             If (\_SB.PCI0.EHC1.PMES)
Error    4063 -                     Object does not exist ^  (\_SB.PCI0.EHC1.PMES)

./dsdt_fixed.txt   669:                 Store (0x01, \_SB.PCI0.EHC1.PMES)
Error    4063 -                                  Object does not exist ^  (\_SB.PCI0.EHC1.PMES)

./dsdt_fixed.txt   670:                 Notify (\_SB.PCI0.EHC1, 0x02)
Error    4063 -                        Object does not exist ^  (\_SB.PCI0.EHC1)

./dsdt_fixed.txt   673:             If (\_SB.PCI0.EHC2.PMES)
Error    4063 -                     Object does not exist ^  (\_SB.PCI0.EHC2.PMES)

./dsdt_fixed.txt   675:                 Store (0x01, \_SB.PCI0.EHC2.PMES)
Error    4063 -                                  Object does not exist ^  (\_SB.PCI0.EHC2.PMES)

./dsdt_fixed.txt   676:                 Notify (\_SB.PCI0.EHC2, 0x02)
Error    4063 -                        Object does not exist ^  (\_SB.PCI0.EHC2)

./dsdt_fixed.txt   679:             If (\_SB.PCI0.HDEF.PMES)
Error    4063 -                     Object does not exist ^  (\_SB.PCI0.HDEF.PMES)

./dsdt_fixed.txt   681:                 Store (0x01, \_SB.PCI0.HDEF.PMES)
Error    4063 -                                  Object does not exist ^  (\_SB.PCI0.HDEF.PMES)

./dsdt_fixed.txt   682:                 Notify (\_SB.PCI0.HDEF, 0x02)
Error    4063 -                        Object does not exist ^  (\_SB.PCI0.HDEF)

./dsdt_fixed.txt   685:             Notify (\_SB.PCI0.LANC, 0x02)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.LANC)

./dsdt_fixed.txt   690:             Notify (\_SB.PCI0.USB4, 0x02)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.USB4)

./dsdt_fixed.txt   695:             XOr (GIV, 0x0100, Local0)
Error    4063 -      Object does not exist ^  (GIV_)

./dsdt_fixed.txt   696:             Store (Local0, GIV)
Error    4063 -                Object does not exist ^  (GIV_)

./dsdt_fixed.txt   697:             VDET (\_SB.WMID.WGWE (0x01, 0x00))
Error    4063 -                  Object does not exist ^  (\_SB.WMID.WGWE)

./dsdt_fixed.txt   699:             Notify (\_SB.PCI0.USB5, 0x00)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.USB5)

./dsdt_fixed.txt   700:             Notify (\_SB.PCI0.USB6, 0x00)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.USB6)

./dsdt_fixed.txt   701:             Notify (\_SB.PCI0.EHC2, 0x00)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.EHC2)

./dsdt_fixed.txt   702:             Notify (\_SB.PCI0.SATA, 0x00)
Error    4063 -                    Object does not exist ^  (\_SB.PCI0.SATA)

./dsdt_fixed.txt   703:             DKET ()
Error    4063 -  Object does not exist ^  (DKET)

./dsdt_fixed.txt   708:             XOr (GIV, 0x2000, Local0)
Error    4063 -      Object does not exist ^  (GIV_)

./dsdt_fixed.txt   709:             Store (Local0, GIV)
Error    4063 -                Object does not exist ^  (GIV_)

./dsdt_fixed.txt   713:             And (\_SB.PCI0.LPCB.GPRO, Not (Local3), Local0)
Error    4063 -                      Object does not exist ^  (\_SB.PCI0.LPCB.GPRO)

./dsdt_fixed.txt   714:             Store (Local0, \_SB.PCI0.LPCB.GPRO)
Error    4063 -                                Object does not exist ^  (\_SB.PCI0.LPCB.GPRO)

./dsdt_fixed.txt   715:             If (\_SB.PCI0.LPCB.EC0.ECRG)
Error    4063 -                         Object does not exist ^  (\_SB.PCI0.LPCB.EC0.ECRG)

./dsdt_fixed.txt   717:                 XOr (\_SB.LID._LID (), 0x01, \_SB.PCI0.LPCB.EC0.LIDS)
Error    4063 -                    Object does not exist ^  (\_SB.LID._LID)

./dsdt_fixed.txt   717:                 XOr (\_SB.LID._LID (), 0x01, \_SB.PCI0.LPCB.EC0.LIDS)
Error    4063 -                                                      Object does not exist ^  (\_SB.PCI0.LPCB.EC0.LIDS)

./dsdt_fixed.txt   720:             Notify (\_SB.LID, 0x80)
Error    4063 -              Object does not exist ^  (\_SB.LID)

./dsdt_fixed.txt   723:                 And (\_SB.PCI0.LPCB.GPRO, Not (Local3), Local0)
Error    4063 -                          Object does not exist ^  (\_SB.PCI0.LPCB.GPRO)

./dsdt_fixed.txt   724:                 Or (Local0, Local2, \_SB.PCI0.LPCB.GPRO)
Error    4063 -                                         Object does not exist ^  (\_SB.PCI0.LPCB.GPRO)

./dsdt_fixed.txt   727:             \_SB.PCI0.ACEL.AJAL ()
Error    4063 -                 Object does not exist ^  (\_SB.PCI0.ACEL.AJAL)

./dsdt_fixed.txt   731:     Scopeame (_UID, 0x01)
Error    4095 -                 ^ syntax error, unexpected PARSEOP_SCOPE, expecting $end

ASL Input:  ./dsdt_fixed.txt - 18421 lines, 646183 bytes, 261 keywords
Compilation complete. 102 Errors, 1 Warnings, 0 Remarks, 58 Optimizations



Compiling done, if it worked, you have now a patched DSDT in dsdt.aml
If the compiling went wrong, you could force to build it with ./DSDT\ Patcher -f (try this DSDT at your own risk)


rm: dsdt.dat: No such file or directory
mkdir: ./Debug: File exists
mv: ./dsdt.dsl: No such file or directory
tar: ./Debug/eric.tar: Can't add archive to itself

---

### Post by 67GTA on 2010-04-18
The "object does not exist" error is caused by either a custom built rig where the bios is looking for hardware that is no longer there and is rendered useless, or a fatally flawed dsdt file. Open a terminal and run ```
dmesg > dmesg
``` Then look at the new dmesg file in your home directory. If there are no fatal errors there, and all of your hardware works, then fixing the dsdt won't accomplish anything. The dsdt only tells the bios/OS the recommended config for your original hardware. With most modern OS's, the ability to configure hardware on the fly renders the dsdt almost useless anyway.

---

### Post by ericw12 on 2010-04-18
> **67GTA said:**
> The "object does not exist" error is caused by either a custom built rig where the bios is looking for hardware that is no longer there and is rendered useless, or a fatally flawed dsdt file. Open a terminal and run ```
dmesg > dmesg
``` Then look at the new dmesg file in your home directory. If there are no fatal errors there, and all of your hardware works, then fixing the dsdt won't accomplish anything. The dsdt only tells the bios/OS the recommended config for your original hardware. With most modern OS's, the ability to configure hardware on the fly renders the dsdt almost useless anyway.




The reason I need fix it is because I am testing snow leopard on HP laptop.

---

### Post by ericw12 on 2010-04-18
Here is what I stuck actually now after make External claim for each of the objects that do not exist.  Thanks!




                If (LEqual (Local0, 0x03))
                {
                    VBRE (0x87, If (LEqual (Local0, 0x02))
                        {
                            VBRE (0x86)
                        }
                }



/Users/eric/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl   627:                     VBRE (0x87, If (LEqual (Local0, 0x02))
Error    4096 -                                           syntax error, unexpected PARSEOP_IF, expecting ',' or ')' ^ 

/Users/eric/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl   627:                     VBRE (0x87, If (LEqual (Local0, 0x02))
Error    4096 -                                                                                                syntax error, unexpected ')' ^ 

/Users/eric/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl   627:                     VBRE (0x87, If (LEqual (Local0, 0x02))
Warning  1106 -                                                                          Result is not used, operator has no effect ^

---

### Post by 67GTA on 2010-04-18
Just post your dsdt file here and I will see what I can do.

---

### Post by ericw12 on 2010-04-18
> **67GTA said:**
> Just post your dsdt file here and I will see what I can do.



That would be awesome!!!

After declared all Externals for "object does not exist, I have two syntax errors.

Thanks a lot!

======== current errors =========

eric$ ../Tools/iasl dsdt.dsl 

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20080926 [Oct  4 2008]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl   691:                     VBRE (0x87, If (LEqual (Local0, 0x02))
Error    4095 -                                  ^ syntax error, unexpected PARSEOP_IF, expecting ',' or ')'

dsdt.dsl   691:                     VBRE (0x87, If (LEqual (Local0, 0x02))
Error    4095 -                             syntax error, unexpected ')' ^ 

dsdt.dsl   691:                     VBRE (0x87, If (LEqual (Local0, 0x02))
Warning  1105 -       Result is not used, operator has no effect ^ 

dsdt.dsl   800:     Scope)
Error    4095 -         ^ syntax error, unexpected PARSEOP_SCOPE, expecting $end

ASL Input:  dsdt.dsl - 18585 lines, 651056 bytes, 261 keywords
Compilation complete. 3 Errors, 1 Warnings, 0 Remarks, 59 Optimizations

---

### Post by 67GTA on 2010-04-19
Can I trouble you for a fresh dsdt.dsl without any changes?

---

### Post by ericw12 on 2010-04-19
> **67GTA said:**
> Can I trouble you for a fresh dsdt.dsl without any changes?

Dumb me. Sure thing, here it is!

Thanks a lot!

---

### Post by ericw12 on 2010-04-24
> **ericw12 said:**
> Dumb me. Sure thing, here it is!

Thanks a lot!

Any luck?

---

### Post by 67GTA on 2010-04-24
> **ericw12 said:**
> Any luck?

edit

---

### Post by 67GTA on 2010-04-24
> **ericw12 said:**
> Any luck?

Not yet. I've came up with the same results you did. Most of them seem to be Windows related, and probably not used by Linux anyway. Do you have any errors in your dmesg output? The kernel may still be working around them without any adverse effects.

---

### Post by ericw12 on 2010-04-25
> **67GTA said:**
> Not yet. I've came up with the same results you did. Most of them seem to be Windows related, and probably not used by Linux anyway. Do you have any errors in your dmesg output? The kernel may still be working around them without any adverse effects.

My windows and Linux works just fine. It is the OSX Snow leopard having a lot of problems.  I use Chameleon "simulate" a mac book, so I do not have much errors. However, the sleep and speedstep etc do not work properly, and a proper DSDT suppose to fix them.

Anyway, here is the dmesg:

sudo dmesg
Password:
_table_max_displ = 73
[SleepEnabler] Registering PowerManagement dispatch table...
[SleepEnabler] in the event of a kernel panic, please use pmVersion...
[SleepEnabler] Calling pmInitComplete()...
NullCPUPowerManagement::init: properties=0xffffff8009a292c0
NullCPUPowerManagement::start
AppleACPICPU: ProcessorId=0 LocalApicId=0 Enabled
AppleACPICPU: ProcessorId=1 LocalApicId=1 Enabled
AppleACPICPU: ProcessorId=2 LocalApicId=0 Disabled
AppleACPICPU: ProcessorId=3 LocalApicId=0 Disabled
calling mpo_policy_init for Quarantine
Security policy loaded: Quarantine policy (Quarantine)
calling mpo_policy_init for Sandbox
Security policy loaded: Seatbelt sandbox policy (Sandbox)
calling mpo_policy_init for TMSafetyNet
Security policy loaded: Safety net for Time Machine (TMSafetyNet)
Copyright (c) 1982, 1986, 1989, 1991, 1993
	The Regents of the University of California. All rights reserved.

MAC Framework successfully initialized
using 16384 buffer headers and 4096 cluster IO buffer headers
IOAPIC: Version 0x20 Vectors 64:87
ACPI: System State [S0 S3 S4 S5] (S3)
mbinit: done (64 MB memory set for mbuf pool)
From path: "uuid", 
Waiting for boot volume with UUID B1FE2C55-2955-359D-82D9-8790380FD616
Waiting on <dict ID="0"><key>IOProviderClass</key><string ID="1">IOResources</string><key>IOResourceMatch</key><string ID="2">boot-uuid-media</string></dict>
netkas presents fakesmc, a kext which emulates smc device
com.apple.AppleFSCompressionTypeZlib load succeeded
FireWire runtime power conservation disabled. (2)
FireWire (OHCI) VendorID 1180 ID 832 PCI now active, GUID 5566778811223344; max speed s400.
Got boot device = IOService:/AppleACPIPlatformExpert/PCI0/AppleACPIPCI/SATA@1F,2/AppleAHCI/PRT0@0/IOAHCIDevice@0/AppleAHCIDiskDriver/IOAHCIBlockStorageDevice/IOBlockStorageDriver/ST9320421AS Media/IOFDiskPartitionScheme/Untitled 2@2
BSD root: disk0s2, major 14, minor 1
jnl: unknown-dev: replay_journal: from: 2478592 to: 4247040 (joffset 0x97000)
jnl: unknown-dev: journal replay done.
Kernel is LP64
hfs: Removed 3 orphaned / unlinked files and 0 directories 
systemShutdown false
Waiting for DSMOS...
NVDANV50HAL loaded and registered.
Apple16X50PCI3: Identified 1 Serial channels at PCI Bus=0 Dev=3 Func=3
Apple16X50UARTSync3: Detected 16550AF/C/CF FIFO=16 MaxBaud=115200
Apple16X50ACPI0: Identified Serial Port on ACPI Device=COM1
Apple16X50UARTSync0: Detected 16550AF/C/CF FIFO=16 MaxBaud=115200
Previous Shutdown Cause: 0
venderid: 0x8086 deviceid: 0x10f5.
Intel82566MM: Ethernet address 00:25:b3:4b:a4:7d
ring desc success: size->4096, virtual:5cd74000, phy:1778a000.
ring desc success: size->4096, virtual:5cf79000, phy:1778b000.
configure tx tdlen->4096. 
configure rx rdlen->4096. 
enable success.
DSMOS has arrived
VoodooBattery 1.3 (C) 2009 Superhai, All Rights Reserved. Jan  7 2010 23:18:58 64 bit
NTFS driver 3.2 [Flags: R/W].
NTFS volume name , version 3.1.
NTFS-fs warning (device /dev/disk0s1, pid 60): ntfs_system_inodes_get(): NTFS volume is dirty.  You should unmount it and run chkdsk.
NTFS volume name New Volume, version 3.1.
NTFS-fs warning (device /dev/disk0s3, pid 235): ntfs_system_inodes_get(): NTFS volume is dirty.  You should unmount it and run chkdsk.
FakeSMC: key info not found MSDS, length - 6
Intel82566MM info: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX

kxld[com.google.filesystems.fusefs]: The following symbols are unresolved for this kext:
kxld[com.google.filesystems.fusefs]: 	_OSRuntimeFinalizeCPP
kxld[com.google.filesystems.fusefs]: 	_OSRuntimeInitializeCPP
Can't load kext com.google.filesystems.fusefs - link failed.
Failed to load executable for kext com.google.filesystems.fusefs.
Kext com.google.filesystems.fusefs failed to load (0xdc008016).
Failed to load kext com.google.filesystems.fusefs (error 0xdc008016).
ACPI_SMC_PlatformPlugin::start - waitForService(resourceMatching(AppleIntelCPUPowerManagement) timed out
vboxdrv: fAsync=0 offMin=0x873 offMax=0x5f9c
VBoxDrv: version 3.1.6 r59351; IOCtl version 0x100001; IDC version 0x10000; dev major=18
VBoxFltDrv: version 3.1.6 r59351
VBoxAdpDrv: version 3.1.6 r59351
erics-MacBook-Pro:~

---

### Post by 67GTA on 2010-04-25
I don't see anything except for a ntfs partition that needs a file system check. I doubt this is dsdt related. You might give the OSX forums a try.

---

### Post by Sentello on 2010-04-28
**Hello Fans of Ubuntu.**
I have problem with my Ubuntu. Now I use Ubuntu 9.04 with my own DSDT.
I want update to Ubuntu 10.04, how? How I can apply my DSDT in to Ubntu 10.04.
[B][I]sorry for my BAD English
:lolflag:
[/I][/B]

---

### Post by ericwwheeler on 2010-05-02
Then we need to get a copy of your current DSDT and save it in your home  folder with this command  	Code:
 	sudo cat /proc/acpi/dsdt > dsdt.dat 
I ran this command and it returned:

sudo cat /proc/acpi/dsdt > dsdt.dat
cat: /proc/acpi/dsdt: No such file or directory

I am working on installing 10.4 on a friend's Toshiba Satellite L505D-S5983.  I have to add noacpi and acpi=off just to get it to boot but am unsure how to find this dsdt file.  Any help would be appreciated.  I am not sure what other information is necessary but I can follow explicit instructions if you would be willing to help.
:confused:

---

### Post by macky_reddy on 2010-05-11
> **67GTA said:**
> [attach]152222[/attach]
 
[attach]152223[/attach]
 
[attach]152224[/attach]
 
[attach]152225[/attach]
 
[attach]152226[/attach]
 
 
Thanks for ur support appreciated mate

---

### Post by computer.technician on 2010-05-26
I'm trying to patch my DSDT for a Foxconn A85GM with BIOS version 933F1P05. My submitted DSDT.dsl was disassembled with IASL-20100528. Thanks 67GTA or anyone else that could provide some help with resolving the errors and warnings that I'm receiving with compiling it.

Update: I've finally completed the patch for the DSDT table. I've provided attachments for the original and final compilations for the A85GM. I'll clean up the tables syntax later for further optimizations but it is fully functional with zero errors, warnings, or remarks.

Second Update: I've removed the patched DSDT because of finding a bug after performing some Linux and Windows testing. I will have to debug and then I will upload the newer patched DSDT table.

Third Update: I've attached the patched DSDT with 0 errors, 0 warnings, 0 remarks, and 77 optimizations. I am currently using this patched DSDT compiled/compressed in the BIOS and not patched into the Ubuntu 10.04 and Windows 7 kernels. Both OS appear to be a bit more responsive and have slightly faster boot times to their respective desktops. Also, the S0-S5 states are operational. I have not tested this fully for all available options in the CMOS or potential bugs. I am not responsible for your use of my patched DSDT. I will be testing this patched BIOS with an older Linux kernel later on. Again, use this at your own risk.

Fourth Update: I replaced version 933F1P05 with version 933F1P06 which was released on 20100618. The DSDT was almost the same as in the previous version with the same compilation errors, warnings, and remarks; so it wasn't difficult this time to patch this version. This newer version was an update for 6-Core processor support. Use this patched DSDT at your own risk.

---

### Post by RagieL on 2010-05-26
This is such a great resource that you are providing and you give it away for free. I enjoy seeing thread that understand the value of providing a prime resource for free. I truly loved reading your post. Thanks!

---

### Post by erikmorres on 2010-06-01
Hi,

I'm having some issues with my newly acquired system and was pointed ([http://ubuntuforums.org/showthread.php?p=9393520](http://ubuntuforums.org/showthread.php?p=9393520)) to this thread as you might be able to help and/or provide some hints to resolve my issue.

The frustrating issue Iran into with this system is: the fans (at least  the CPU fan) run constantly at max speed.

*sensor* output:

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +34.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +34.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +40.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +28.0°C  (high = +74.0°C, crit = +100.0°C)  

f8000-isa-0a00
Adapter: ISA adapter
+3.3V:       +3.38 V
3VSB:        +3.39 V
Vbat:        +3.30 V
fan1:       1507 RPM
fan2:        831 RPM
fan3:          0 RPM  ALARM
fan4:          0 RPM
temp1:       +38.0°C  (high = +70.0°C, hyst = +60.0°C)  
temp2:       +34.0°C  (high = +100.0°C, hyst = +85.0°C)  sensor = Intel PECI
temp3:       +36.0°C  (high = +100.0°C, hyst = +85.0°C)
```In an attempt to resolve this I've tried different acpi_osi switches, to no avail however. My latest attempt is to look at the DSDT, as it was suggested that this might be the cause of the issue. However after extracting, disassembling and recompiling I get a couple of warnings and a remark. However I don't know if these are the cause of the issue I'm having and - in case this is the cause - how to amend the DSDT to overcome this issue. Your help is very much appreciated!

The output of *iasl* is as follows:

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl   132:         Name (_T_0, Zero)
Remark   5110 -                  ^ Use of compiler reserved name (_T_0)

dsdt.dsl  5223:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5237:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5252:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5267:             Acquire (MUTE, 0x0FFF)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5281:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5296:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5311:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

ASL Input:  dsdt.dsl - 6150 lines, 190558 bytes, 2724 keywords
AML Output: dsdt.aml - 22355 bytes, 729 named objects, 1995 executable opcodes

Compilation complete. 0 Errors, 7 Warnings, 1 Remarks, 66 Optimizations
```I've included my systems DSDT.dsl file in the hopes somebody notices if there is an issue with this file.

Another related question I have after reading through this thread is: in the case I amend the DSDT file, do I need to redo these steps when I add new components to my PC?

Again, thank you in advance!

Kind regards,

Erik

---

### Post by ashikahamed on 2010-06-01
I get this at the end when i compile the dsdt.dsl file

'ASL Input:  dsdt.dsl - 13621 lines, 471479 bytes, 3634 keywords
Compilation complete. 116 Errors, 2 Warnings, 2 Remarks, 4 Optimizations'

I couldn't figure out how to fix all those error.Can you please fix me those errors.I have attached my dsdt.dsl file.

---

### Post by mekh on 2010-06-04
Hi All,
I have LG E500 notebook with the same ACPI issues. But in my case recompiling of DSDT doesn't help.
I tried to put corrected dsdt in initrd as well as in the new kernel. But in both cases it doesn't work.
The issues are:
- sleep and hibernate don't work;
- wrong battery level;
- CPU overheating (for example - when I try to compile a new kernel);

Maybe I need to install some special soft? Or maybe I did something wrong?
There are original and edited dsdts in attached files. Also, dmesg and dmidecode output.

Dear **67GTA**, please, look at attachments. If you'll be need some more information - just let me know what kind of.
I'll be very grateful for any help.

---

### Post by ashikahamed on 2010-06-04
I think the use of custom dsdt file is not supported in current kernel versions.Please have a look at 'https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246222'

---

### Post by mekh on 2010-06-04
> **ashikahamed said:**
> I think the use of custom dsdt file is not supported in current kernel versions.Please have a look at 'https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246222'
I tried to use 2.6.32-22 (out of box) and 2.6.34 (vanilla) kernels with these options:
```
CONFIG_ACPI_CUSTOM_DSDT_FILE="/usr/src/linux-2.6.34/include/acpi/dsdt_table.h"
CONFIG_ACPI_CUSTOM_DSDT=y
```

Take a look at dmesg output:
```
[    0.000000] ACPI: Override [DSDT-LGPC    ], this is unsafe: tainting kernel
[    0.000000] Disabling lock debugging due to kernel taint
[    0.000000] ACPI: DSDT @ 0x000000007ffb05b0 Table override, replaced with:
[    0.000000] ACPI: DSDT ffffffff81a5f7f0 05100 (v01  M163F M163F000 00000000 INTL 20100428)

```

Also, I tried all combinations of acpi_os_name and acpi_osi. But nothing helps.

And final chek:
```
root@PC:~# cp /proc/acpi/dsdt ~
root@PC:~# iasl -d dsdt 

Intel ACPI Component Architecture
AML Disassembler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

Loading Acpi table from file dsdt
Acpi table [DSDT] successfully installed and loaded
Pass 1 parse of [DSDT]
Pass 2 parse of [DSDT]
Parsing Deferred Opcodes (Methods/Buffers/Packages/Regions)
....................................................................................................................................................................................................................................................................................................................................................................................................
Parsing completed
Disassembly completed, written to "dsdt.dsl"

root@PC:~# iasl -tc dsdt.dsl 

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

ASL Input:  dsdt.dsl - 5577 lines, 178779 bytes, 2518 keywords
AML Output: dsdt.aml - 20736 bytes, 702 named objects, 1816 executable opcodes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 42 Optimizations
root@PC:~#

```

---

### Post by mekh on 2010-06-07
Today attempts:
- Ubuntu 10.04 x86 clean install
- get all updates
- put corrected DSDT into new kernel
- compile kernel
- reboot
....
- power management doesn't work (wrong battery level, no hibernate and sleep functions, etc.) :(

Does anybody have an idea what else should I do?
Detailed information you can find in my posts above.

---

### Post by Sentello on 2010-06-14
I have same problem. 
I try everithing, but still nothing helps me...

---

### Post by Sentello on 2010-06-16
> **ashikahamed said:**
> I think the use of custom dsdt file is not supported in current kernel versions.Please have a look at 'https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246222'

What we can do? Nothing?

---

### Post by k0smik0 on 2010-06-17
ok, 

i red about new solutions with opensuse and bla bla, but i want use my debian...

so, can u have a look at these, all the same ?


from this page:

[http://ubuntuforums.org/showpost.php?p=8300591&postcount=378](http://ubuntuforums.org/showpost.php?p=8300591&postcount=378)

dsdt: [http://ubuntuforums.org/attachment.php?attachmentid=135898&d=1258028416](http://ubuntuforums.org/attachment.php?attachmentid=135898&d=1258028416)



and from this page:

[http://ubuntuforums.org/showpost.php?p=8301939&postcount=379](http://ubuntuforums.org/showpost.php?p=8301939&postcount=379)

and dsdt: [http://ubuntuforums.org/attachment.php?attachmentid=135914&d=1258043819](http://ubuntuforums.org/attachment.php?attachmentid=135914&d=1258043819)

 

tnx, bye ;D

---

### Post by Sentello on 2010-06-17
[B][COLOR=Red]I have the same problem, but today i soved it!!![/COLOR]
[/B]
Here is the tutorial 100% WORKING, I tested it, with my laptop _***Fujitsu-Siemens Amilo L7310GW***_
:guitar:

> LINK: [http://www.computerhok.nl/JSPWiki/Wiki.jsp?page=Installatie%20Ubuntu%20Lucid%20Lynx#section-Installatie+Ubuntu+Lucid+Lynx-KernelCompile](http://www.computerhok.nl/JSPWiki/Wiki.jsp?page=Installatie%20Ubuntu%20Lucid%20Lynx#section-Installatie+Ubuntu+Lucid+Lynx-KernelCompile)

---

### Post by ashikahamed on 2010-06-17
I could boot into ubuntu using the boot option "pci=nobios".Still trying to get my DSDT file fixed.

---

### Post by computer.technician on 2010-06-19
I've recompiled your DSDT with 0 errors, 0 warnings, 0 remarks, and 66 optimizations. Also, I've mended the Linux pointer to use the same table references as Windows. Use this patched DSDT at your own risk.

> **erikmorres said:**
> Hi,

I'm having some issues with my newly acquired system and was pointed ([http://ubuntuforums.org/showthread.php?p=9393520](http://ubuntuforums.org/showthread.php?p=9393520)) to this thread as you might be able to help and/or provide some hints to resolve my issue.

The frustrating issue Iran into with this system is: the fans (at least  the CPU fan) run constantly at max speed.

*sensor* output:

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +34.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +34.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +40.0°C  (high = +74.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +28.0°C  (high = +74.0°C, crit = +100.0°C)  

f8000-isa-0a00
Adapter: ISA adapter
+3.3V:       +3.38 V
3VSB:        +3.39 V
Vbat:        +3.30 V
fan1:       1507 RPM
fan2:        831 RPM
fan3:          0 RPM  ALARM
fan4:          0 RPM
temp1:       +38.0°C  (high = +70.0°C, hyst = +60.0°C)  
temp2:       +34.0°C  (high = +100.0°C, hyst = +85.0°C)  sensor = Intel PECI
temp3:       +36.0°C  (high = +100.0°C, hyst = +85.0°C)
```In an attempt to resolve this I've tried different acpi_osi switches, to no avail however. My latest attempt is to look at the DSDT, as it was suggested that this might be the cause of the issue. However after extracting, disassembling and recompiling I get a couple of warnings and a remark. However I don't know if these are the cause of the issue I'm having and - in case this is the cause - how to amend the DSDT to overcome this issue. Your help is very much appreciated!

The output of *iasl* is as follows:

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl   132:         Name (_T_0, Zero)
Remark   5110 -                  ^ Use of compiler reserved name (_T_0)

dsdt.dsl  5223:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5237:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5252:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5267:             Acquire (MUTE, 0x0FFF)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5281:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5296:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

dsdt.dsl  5311:             Acquire (MUTE, 0x03E8)
Warning  1104 -                                 ^ Possible operator timeout is ignored

ASL Input:  dsdt.dsl - 6150 lines, 190558 bytes, 2724 keywords
AML Output: dsdt.aml - 22355 bytes, 729 named objects, 1995 executable opcodes

Compilation complete. 0 Errors, 7 Warnings, 1 Remarks, 66 Optimizations
```I've included my systems DSDT.dsl file in the hopes somebody notices if there is an issue with this file.

Another related question I have after reading through this thread is: in the case I amend the DSDT file, do I need to redo these steps when I add new components to my PC?

Again, thank you in advance!

Kind regards,

Erik

---

### Post by computer.technician on 2010-06-20
This DSDT has been patched and compiles with zero errors, warnings, and remarks. If you decide to compile this with any IASL version dated from 20091214 then all DSDT tables will compile with errors for Name (_PLD, Buffer()) because of the new ACPI 4.0 implementation of requiring packages to be created. Use this patched DSDT at your own risk.
> **ashikahamed said:**
> I get this at the end when i compile the dsdt.dsl file

'ASL Input:  dsdt.dsl - 13621 lines, 471479 bytes, 3634 keywords
Compilation complete. 116 Errors, 2 Warnings, 2 Remarks, 4 Optimizations'

I couldn't figure out how to fix all those error.Can you please fix me those errors.I have attached my dsdt.dsl file.

---

### Post by computer.technician on 2010-06-20
This DSDT has been patched and compiled with zero errors, warnings, and remarks. Use at your own risk.
> **mekh said:**
> Hi All,
I have LG E500 notebook with the same ACPI issues. But in my case recompiling of DSDT doesn't help.
I tried to put corrected dsdt in initrd as well as in the new kernel. But in both cases it doesn't work.
The issues are:
- sleep and hibernate don't work;
- wrong battery level;
- CPU overheating (for example - when I try to compile a new kernel);

Maybe I need to install some special soft? Or maybe I did something wrong?
There are original and edited dsdts in attached files. Also, dmesg and dmidecode output.

Dear **67GTA**, please, look at attachments. If you'll be need some more information - just let me know what kind of.
I'll be very grateful for any help.

---

### Post by computer.technician on 2010-06-20
This patched DSDT compiled with zero errors, warnings, or remarks. Use at your own risk.
> **ericw12 said:**
> Dumb me. Sure thing, here it is!

Thanks a lot!

---

### Post by computer.technician on 2010-06-20
This patched DSDT compiled with zero errors, warnings, or remarks. If you use IASL version dated from 20091214 then the table will compile with errors for Name (_PLD, Buffer ()) because of the ACPI 4.0 specification of requiring packages. (_PLD) object is just for the physical location of the EHCI/OHCI and its child objects for the user and OSPM. Use this DSDT at your own risk.
> **ivanmmj said:**
> I've got a Toshiba L505D with a severely broken DSDT table.
It has the bug outlined [here]("http://bugzilla.kernel.org/show_bug.cgi?id=14679").

(ACPI table overridden after boot)
The DSDT that overrides it is completely broken. The DSDT that we pull using the patch posted on that thread is slightly broken, too. It works, though. Unfortunately, the patch doesn't work on the Ubuntu kernel from git. I was hoping you guys could help us fix our DSDT table. (I'm running 10.04 right now, btw. But the problem is there on all Ubuntu versions (and every other non-windows OS, unfortunately...) 


Thanks guys!

---

### Post by bymaxe on 2010-06-23
Hey guys,

i bought a Lenovo Ideacentre D400 Homeserver normally running Microsoft Windows Home Server very well, but i am a little geek and want to have ubuntu 10.04 on that pretty little box. Now i have a problem with the suspend and hibernate mode. I think it is a problem with the dsdt table. I look but there were only 13 warnings but i am not able to solve these problems to get this job done. Maybe anybody is a dsdt table geek and can help me.

Thanks and greets from Germany.

I attached my dsdt-table.

[ATTACH]161356[/ATTACH]

---

### Post by computer.technician on 2010-06-24
This DSDT has been patched and compiles with zero errors, warnings, or remarks using the 20100528 IASL. Use at your own risk.
> **bymaxe said:**
> Hey guys,

i bought a Lenovo Ideacentre D400 Homeserver normally running Microsoft Windows Home Server very well, but i am a little geek and want to have ubuntu 10.04 on that pretty little box. Now i have a problem with the suspend and hibernate mode. I think it is a problem with the dsdt table. I look but there were only 13 warnings but i am not able to solve these problems to get this job done. Maybe anybody is a dsdt table geek and can help me.

Thanks and greets from Germany.

I attached my dsdt-table.

[ATTACH]161356[/ATTACH]

---

### Post by bymaxe on 2010-06-26
Thanks for your work, but the problem i still there. 
The machine goes down in the suspend for approximately 2 seconds and than it goes up and you can work. Now i believe that Lenovo did a hack that only Windows Home Server works very well. 

Bye and a nice week-end.

---

### Post by computer.technician on 2010-06-26
The problem could be another ACPI table. Too many people focus solely on the DSDT. If the FACP and SSDT tables are incorrect then these could cause a conflict with power savings implementations. I would disassemble and compile each of the ACPI tables for your specific platform. Try to debug those for any errors.
> **bymaxe said:**
> Thanks for your work, but the problem i still there. 
The machine goes down in the suspend for approximately 2 seconds and than it goes up and you can work. Now i believe that Lenovo did a hack that only Windows Home Server works very well. 

Bye and a nice week-end.

---

### Post by erikmorres on 2010-06-27
> **computer.technician said:**
> I've recompiled your DSDT with 0 errors, 0 warnings, 0 remarks, and 66 optimizations. Also, I've mended the Linux pointer to use the same table references as Windows. Use this patched DSDT at your own risk.

Thanks for the support! I had already moved back to Windows, however I'll give Ubuntu another try with the DSDT supplied by you.

KR, Erik

---

### Post by choodalls on 2010-06-28
Hi,
On my Dell Vostro I am having problems with power management. After dumping all my ACPI tables I see that one of my SSDT tables (attached) is buggy and will not compile.
I'd be very grateful if you'd take a look at it for me please. This SSDT contains the Scope (_PR) info. that more usually appears in DSDTs I think.
Thank you.

---

### Post by computer.technician on 2010-06-28
This SSDT has three declared externals, probably declared in the DSDT, and no defined arguments. If you'll look at the declared external object and the arguments assigned in the definition block then ask yourself, "What is accomplished?" The arguments aren't defined anywhere and if they are then it is external. Also, in order to assign arguments, wouldn't you agree that you would need to create fields for them and be able to store them in a variable. I interpret this SSDT as broken without having the external reference available to correct what is probably duplicated externally so this would mean it is redundant. Another thing, whenever I inspected your header for this table before the first compile, it was pointing to the dsdt.aml, so I would believe that this table must have been extracted from the DSDT, unless you had caused the wrong naming convention. Anyways, nothing can be done without more information or since in the tables current state, it accomplishes nothing, then you could exclude it.

Look up the processor configuration in Section 8 of the latest ACPI 4.0 specification and you would be able to have a reference as to what should be declared for the processor in the _PR scope. BTW, How did you obtain this SSDT table? I hope it wasn't from copying and pasting directly from the ACPI binary module. If you miss one byte or if the table is broken up throughout the ACPI binary then this table is useless.
> **choodalls said:**
> Hi,
On my Dell Vostro I am having problems with power management. After dumping all my ACPI tables I see that one of my SSDT tables (attached) is buggy and will not compile.
I'd be very grateful if you'd take a look at it for me please. This SSDT contains the Scope (_PR) info. that more usually appears in DSDTs I think.
Thank you.

---

### Post by choodalls on 2010-06-28
Hi,
Thanks for the reply. It was extracted in the usual way from Linux.....as  a reference, I have attached the zip file of the original full table extraction. The DSDT as original has a few warnings etc. but nothing radically strange.

---

### Post by computer.technician on 2010-06-28
I'll try to read through the tables whenever I get some free time but I've got quite alot that I'm having to complete for work this week. What troubleshooting have you attempted in debugging the tables?
> **choodalls said:**
> Hi,
Thanks for the reply. It was extracted in the usual way from Linux.....as  a reference, I have attached the zip file of the original full table extraction. The DSDT as original has a few warnings etc. but nothing radically strange.

---

### Post by choodalls on 2010-06-28
It's really the processor declarations I would like to try and sort out. 

I use the laptop in Ubuntu, Windows 7, but also in OSX and for OSX I'd like to be able to have the _PR statements all incorporated into the DSDT.  I don't know how to do that in this specific case because the DSDT Scope (_PR) parts seem to require the use of the SSDT tables - and the SSDT tables from this board and how they interact with the DSDT make no sense to me.

So if you get any time to help, then it is the _PR statement parts  - preferably with a view to integration of ssdt into dsdt - that'd really be helpful for me.

Thank you for your help.

---

### Post by computer.technician on 2010-06-28
I noticed that your submitted SSDT and DSDT were retrieved in a Mac environment; correct? Have you patched your ACPI tables or is this the manufacturer supplied tables? If the firmware contains the manufacturer supplied tables then are you using a patched DSDT for the Mac OS to boot up? I'm only attempting to patch the original tables for any inconsistent AML and not for Darwin. Retrieve the ACPI tables within a Linux environment by using acpidump and acpixtract after reverting the platform firmware to its manufacturers state. There are other forums for hacking firmware to support the Mac OS kernel.

What's the model or service tag # of the Dell Vostro? I'll download the BIOS from the Dell support site and extract the ACPI module.
> **choodalls said:**
> It's really the processor declarations I would like to try and sort out. 

I use the laptop in Ubuntu, Windows 7, but also in OSX and for OSX I'd like to be able to have the _PR statements all incorporated into the DSDT.  I don't know how to do that in this specific case because the DSDT Scope (_PR) parts seem to require the use of the SSDT tables - and the SSDT tables from this board and how they interact with the DSDT make no sense to me.

So if you get any time to help, then it is the _PR statement parts  - preferably with a view to integration of ssdt into dsdt - that'd really be helpful for me.

Thank you for your help.

---

### Post by choodalls on 2010-06-28
> **computer.technician said:**
> I noticed that your submitted SSDT and DSDT were retrieved in a Mac environment; correct? Have you patched your ACPI tables or is this the manufacturer supplied tables? If the firmware contains the manufacturer supplied tables then are you using a patched DSDT for the Mac OS to boot up? I'm only attempting to patch the original tables for any inconsistent AML and not for Darwin. Retrieve the ACPI tables within a Linux environment by using acpidump and acpixtract after reverting the platform firmware to its manufacturers state. There are other forums for hacking firmware to support the Mac OS kernel.

What's the model or service tag # of the Dell Vostro? I'll download the BIOS from the Dell support site and extract the ACPI module.

Hi,
No actually they were taken direct from a linux environment using an acpi-dump python script from a live Opensuse CD (i.e. using the acpidump tool). Yes, I have opened in a mac environment, but what i sent to you were the originals from the linux extraction........they are the manufacturer supplied and unpatched tables,
The Dell Vostro is a 3500 running latest Bios of A04.
Please though if you feel that there is something amiss then feel free to download again. 
I have been doing patching, but not at all to the tables i supplied to you - they are 100% as Dell made them. I would not ask for Darwin patching here, but am grateful for any help that you feel able to give me with what look to me to be slightly odd examples and in particular with the _PR scope issue.
Thanks again.

---

### Post by osxfr33k on 2010-06-29
67GTA or computer.technician,
 
Can you help with this one? I am adding a firewire hack to get rid of the power conservation issue. This is for an XPS M1530 Dell Laptop. running both Linux and OSX86 Snow.
 
 
Here is the error:
 
/Users/osxfr33k/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl 6100: [*** iASL: Read error on source code temp file /Users/osxfr33k/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.src ***]
Error 4096 - syntax error, unexpected $end ^ 
 
ASL Input: /Users/osxfr33k/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl - 6101 lines, 194479 bytes, 2019 keywords
Compilation complete. 1 Errors, 0 Warnings, 0 Remarks, 0 Optimizations
 
 
Here is the Hack I inserted from EVO DSDTSE a nice Gui Application with a ton of fixes like HPET, RTC and the list goes on and on.
 
 
 
 
 
 
Firewire power conservation Hack.
 
It´s a nice idea to change all your firewire names on DSDT to apple´s ones, for example from FIWI to FRWR.
 
 
 
Locate Scope (_GPE), add this on the end.
 
Method (_L1A, 0, NotSerialized) /* <-- Added for firewire */
{
Notify (\_SB.PCI0.PCIB.FRWR, 0x00)
Notify (\_SB.PWRB, 0x02)
}
 
 
Locate your Firewire device (or create it with this code if it doesn´t exist)
 
 
Device (FRWR) /*Add all this code if you don´t have firewire device on DSDT*/
{
Name (_ADR, 0x00070000)
Name (_GPE, 0x1A)
Method (_DSM, 4, NotSerialized) /* Add from here if you already have a firewire device on dsdt*/
{
Store (Package (0x02)
{
"fwhub",
Buffer (0x04)
{
0x00, 0x00, 0x00, 0x00
}
}, Local0)
DTGP (Arg0, Arg1, Arg2, Arg3, RefOf (Local0))
Return (Local0)
} /* End of code if you just add to a existing firewire device */
}
 
 
 
 
 
 
 
 
My DSDT.dsl is attached.
 
Thanks for having a look and trying to help. If you are able to fix it can you post what was wrong and what you did to rectify the error?
 
 
 
 
 
EDITED THE NEXT DAY:
 
I think I can see why this Hack is nto going to work.
 
Notify (\_SB.PCI0.PCIB.FRWR, 0x00)
Notify (\_SB.PWRB, 0x02)
 
I do not have a PCIB nor a PWRB device.  I guess if I add those devices I can assume this script will compile correctly?
 
PWRB is just power button and I see that EVO has a small script for that I can add that easily.  But what is the PCIB device I have no idea?

---

### Post by computer.technician on 2010-07-01
I scanned over the external references that the SSDT-AMICPU-PROC table contains and the arguments are used in the DSDT but I see no use for them in this table. The question that I cannot answer and would appreciate someone answering is; "What does this table operate on the Arguments after calling them?" If in fact this table is able to call the arguments because it does not store them for any use and then returns to the external reference in the DSDT. I'll have to keep my original opinion that this table is useless and you don't need it other than for BIOS byte length padding. I'm not an expert and can in no way say that the original programmer didn't have a use for them but with a parsing error of the arguments then the method will not use them. You could even comment out the references to Arg0-Arg3 for each of the methods because they are not used and then it would compile with IASL. The DSDT had a few warnings and remarks and I corrected those but I'm assuming that you could perform that yourself because they were fairly easy patches so I did not upload them. Hope this information helps and please let me know if you find out that there is a reason for those arguments use in this particular table.

Update: I made a rookie mistake whenever disassembling the SSDT tables which you may have made as well. Whenever there are external references then you must parse the the table with the DSDT. I had included all of the SSDT tables with the -e option but forgot to reference them with the DSDT. I'm either tired because it's 04:00 or getting lazy. Anyways, I've uploaded the corrected and compiled tables. Use at your own risk.
> **choodalls said:**
> Hi,
No actually they were taken direct from a linux environment using an acpi-dump python script from a live Opensuse CD (i.e. using the acpidump tool). Yes, I have opened in a mac environment, but what i sent to you were the originals from the linux extraction........they are the manufacturer supplied and unpatched tables,
The Dell Vostro is a 3500 running latest Bios of A04.
Please though if you feel that there is something amiss then feel free to download again. 
I have been doing patching, but not at all to the tables i supplied to you - they are 100% as Dell made them. I would not ask for Darwin patching here, but am grateful for any help that you feel able to give me with what look to me to be slightly odd examples and in particular with the _PR scope issue.
Thanks again.

---

### Post by computer.technician on 2010-07-01
There are other forums for hacking firmware to support the Darwin kernel.
> **osxfr33k said:**
> 67GTA or computer.technician,
 
Can you help with this one? I am adding a firewire hack to get rid of the power conservation issue. This is for an XPS M1530 Dell Laptop. running both Linux and OSX86 Snow.
 
 
Here is the error:
 
/Users/osxfr33k/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl 6100: [*** iASL: Read error on source code temp file /Users/osxfr33k/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.src ***]
Error 4096 - syntax error, unexpected $end ^ 
 
ASL Input: /Users/osxfr33k/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl - 6101 lines, 194479 bytes, 2019 keywords
Compilation complete. 1 Errors, 0 Warnings, 0 Remarks, 0 Optimizations
 
 
Here is the Hack I inserted from EVO DSDTSE a nice Gui Application with a ton of fixes like HPET, RTC and the list goes on and on.
 
 
 
 
 
 
Firewire power conservation Hack.
 
It´s a nice idea to change all your firewire names on DSDT to apple´s ones, for example from FIWI to FRWR.
 
 
 
Locate Scope (_GPE), add this on the end.
 
Method (_L1A, 0, NotSerialized) /* <-- Added for firewire */
{
Notify (\_SB.PCI0.PCIB.FRWR, 0x00)
Notify (\_SB.PWRB, 0x02)
}
 
 
Locate your Firewire device (or create it with this code if it doesn´t exist)
 
 
Device (FRWR) /*Add all this code if you don´t have firewire device on DSDT*/
{
Name (_ADR, 0x00070000)
Name (_GPE, 0x1A)
Method (_DSM, 4, NotSerialized) /* Add from here if you already have a firewire device on dsdt*/
{
Store (Package (0x02)
{
"fwhub",
Buffer (0x04)
{
0x00, 0x00, 0x00, 0x00
}
}, Local0)
DTGP (Arg0, Arg1, Arg2, Arg3, RefOf (Local0))
Return (Local0)
} /* End of code if you just add to a existing firewire device */
}
 
 
 
 
 
 
 
 
My DSDT.dsl is attached.
 
Thanks for having a look and trying to help. If you are able to fix it can you post what was wrong and what you did to rectify the error?
 
 
 
 
 
EDITED THE NEXT DAY:
 
I think I can see why this Hack is nto going to work.
 
Notify (\_SB.PCI0.PCIB.FRWR, 0x00)
Notify (\_SB.PWRB, 0x02)
 
I do not have a PCIB nor a PWRB device.  I guess if I add those devices I can assume this script will compile correctly?
 
PWRB is just power button and I see that EVO has a small script for that I can add that easily.  But what is the PCIB device I have no idea?

---

### Post by choodalls on 2010-07-02
> **computer.technician said:**
> I scanned over the external references that the SSDT-AMICPU-PROC table contains and the arguments are used in the DSDT but I see no use for them in this table. The question that I cannot answer and would appreciate someone answering is; "What does this table operate on the Arguments after calling them?" If in fact this table is able to call the arguments because it does not store them for any use and then returns to the external reference in the DSDT. I'll have to keep my original opinion that this table is useless and you don't need it other than for BIOS byte length padding. I'm not an expert and can in no way say that the original programmer didn't have a use for them but with a parsing error of the arguments then the method will not use them. You could even comment out the references to Arg0-Arg3 for each of the methods because they are not used and then it would compile with IASL. The DSDT had a few warnings and remarks and I corrected those but I'm assuming that you could perform that yourself because they were fairly easy patches so I did not upload them. Hope this information helps and please let me know if you find out that there is a reason for those arguments use in this particular table.

Thanks for your time. BTW managed to download the attachment fine today - think there was something odd about my log in yesterday that prevented me accessing properly.

---

### Post by computer.technician on 2010-07-02
NP. Yesterday, I had the same problem with logging in and uploading the archive to this forum. Perhaps, these will be helpful to you. Do you plan on replacing your original module in your BIOS with this one?
> **choodalls said:**
> Thanks for your time. BTW managed to download the attachment fine today - think there was something odd about my log in yesterday that prevented me accessing properly.

---

### Post by hornedfiend on 2010-07-10
Hi,

Can you guys please help me with my dsdt file.
Here's the output and the dsdt.dsl file.

/home/ubuntu/dsdt.dsl  8873:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -        Not all control paths return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  8873:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -         Reserved method must return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9033:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9033:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9101:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9101:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9174:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -        Not all control paths return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9174:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -         Reserved method must return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9334:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9334:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9402:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9402:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9507:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -        Not all control paths return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9507:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -         Reserved method must return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9667:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9667:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9735:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9735:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9808:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -        Not all control paths return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9808:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -         Reserved method must return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9968:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9968:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl 10036:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl 10036:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

ASL Input:  /home/ubuntu/dsdt.dsl - 10111 lines, 370896 bytes, 4450 keywords
AML Output: /home/ubuntu/dsdt.aml - 38326 bytes, 939 named objects, 3511 executable opcodes

Compilation complete. 0 Errors, 24 Warnings, 0 Remarks, 37 Optimizations

Many thanks in advance

---

### Post by computer.technician on 2010-07-10
Patched and compiled this DSDT with zero warnings, errors, or remarks using IASL 20091214. Use at your own risk.
> **hornedfiend said:**
> Hi,

Can you guys please help me with my dsdt file.
Here's the output and the dsdt.dsl file.

/home/ubuntu/dsdt.dsl  8873:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -        Not all control paths return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  8873:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -         Reserved method must return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9033:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9033:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9101:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9101:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9174:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -        Not all control paths return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9174:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -         Reserved method must return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9334:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9334:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9402:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9402:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9507:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -        Not all control paths return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9507:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -         Reserved method must return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9667:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9667:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9735:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9735:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9808:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -        Not all control paths return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9808:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -         Reserved method must return a value ^  (_GTM)

/home/ubuntu/dsdt.dsl  9968:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl  9968:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl 10036:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -            Not all control paths return a value ^  (_GTF)

/home/ubuntu/dsdt.dsl 10036:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -             Reserved method must return a value ^  (_GTF)

ASL Input:  /home/ubuntu/dsdt.dsl - 10111 lines, 370896 bytes, 4450 keywords
AML Output: /home/ubuntu/dsdt.aml - 38326 bytes, 939 named objects, 3511 executable opcodes

Compilation complete. 0 Errors, 24 Warnings, 0 Remarks, 37 Optimizations

Many thanks in advance

---

### Post by ceratophyllum on 2010-07-11
Can you patch this DSDT from Lenovo Y730?

Warnings:

```

dsdt.dsl  1606:             Method (_WED, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (_WED)

dsdt.dsl  1606:             Method (_WED, 1, NotSerialized)
Warning  1080 -                        ^ Reserved method must return a value (_WED)

dsdt.dsl  5855:                     Method (HKDS, 1, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (HKDS)

dsdt.dsl  6329:                             Method (_CFG, 0, NotSerialized)
Warning  1098 -                  Unknown reserved name ^  (_CFG)

dsdt.dsl  6379:                             Method (VPCR, 1, Serialized)
Warning  1087 -   Not all control paths return a value ^  (VPCR)

dsdt.dsl  6402:                                     Name (_T_0, Zero)
Remark   5110 -                Use of compiler reserved name ^  (_T_0)

dsdt.dsl  6696:                             Method (_CFG, 0, NotSerialized)
Warning  1098 -                  Unknown reserved name ^  (_CFG)

ASL Input:  dsdt.dsl - 9443 lines, 342961 bytes, 3826 keywords
AML Output: dsdt.aml - 35636 bytes, 899 named objects, 2927 executable opcodes


```

---

### Post by hornedfiend on 2010-07-14
Unfortunately, the DSDT implementation failed. I'm not seeing any lines as stated in the first post (after I compile and update the kernel) after the output file is created.
Why is that? Am I doing something wrong, I followed the instructions exactly. Does it make any difference that I changed the user and installed ubuntu with wubi (I previously used usb installer and had ubuntu installed on an usb stick)?

---

### Post by Ed_Saxman on 2010-07-18
HI !!

Please, someone can help me with my DSDT? It´s from my HP DV3540es.

I´m having all these warnings:


Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090730 [Aug 12 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 4.0

/Library/DSDT/DSDTFiles/dsdt.dsl  3430:             Method (_HOT, 0, NotSerialized)
Warning  1087 -           Not all control paths return a value ^  (_HOT)

/Library/DSDT/DSDTFiles/dsdt.dsl  3430:             Method (_HOT, 0, NotSerialized)
Warning  1080 -            Reserved method must return a value ^  (_HOT)

/Library/DSDT/DSDTFiles/dsdt.dsl  3491:             Method (_HOT, 0, NotSerialized)
Warning  1087 -           Not all control paths return a value ^  (_HOT)

/Library/DSDT/DSDTFiles/dsdt.dsl  3491:             Method (_HOT, 0, NotSerialized)
Warning  1080 -            Reserved method must return a value ^  (_HOT)

ASL Input:  /Library/DSDT/DSDTFiles/dsdt.dsl - 9559 lines, 378314 bytes, 4177 keywords
AML Output: /Library/DSDT/DSDTFiles/./dsdt.aml - 42513 bytes, 864 named objects, 3313 executable opcodes

Compilation complete. 0 Errors, 4 Warnings, 0 Remarks, 35 Optimizations

---

### Post by MartinoM on 2010-07-26
Can someone help me? I have Acer Aspire 7720g

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  6842:                    Method (_GTM, 0, NotSerialized)
Warning  1087 -                               ^ Not all control paths return a value (_GTM)

dsdt.dsl  6842:                    Method (_GTM, 0, NotSerialized)
Warning  1080 -                               ^ Reserved method must return a value (_GTM)

dsdt.dsl  7004:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  7004:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  7072:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  7072:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  7145:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (_GTM)

dsdt.dsl  7145:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -                                ^ Reserved method must return a value (_GTM)

dsdt.dsl  7319:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  7319:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  7387:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  7387:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  7494:                     Method (_GTF, 0, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (_GTF)

dsdt.dsl  7494:                     Method (_GTF, 0, NotSerialized)
Warning  1080 -                                ^ Reserved method must return a value (_GTF)

dsdt.dsl  7540:                     Method (_GTF, 0, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (_GTF)

dsdt.dsl  7540:                     Method (_GTF, 0, NotSerialized)
Warning  1080 -                                ^ Reserved method must return a value (_GTF)

dsdt.dsl  7851:                     Name (_T_0, Zero)
Remark   5110 -                              ^ Use of compiler reserved name (_T_0)

dsdt.dsl  7914:                     Name (_T_0, Zero)
Remark   5110 -                              ^ Use of compiler reserved name (_T_0)

dsdt.dsl  7918:                         Name (_T_1, Zero)
Remark   5110 -    Use of compiler reserved name ^  (_T_1)

dsdt.dsl  7952:                         Name (_T_2, Zero)
Remark   5110 -    Use of compiler reserved name ^  (_T_2)

dsdt.dsl  7986:                 Method (OEMN, 0, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (OEMN)

dsdt.dsl  8016:                     Name (_T_0, Zero)
Remark   5110 -                              ^ Use of compiler reserved name (_T_0)

dsdt.dsl  8196:                     Name (_T_0, Zero)
Remark   5110 -                              ^ Use of compiler reserved name (_T_0)

dsdt.dsl  8208:                             Name (_T_1, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_1)

dsdt.dsl  8353:                         Name (_T_2, Zero)
Remark   5110 -    Use of compiler reserved name ^  (_T_2)

dsdt.dsl  8568:                     Name (_T_0, Zero)
Remark   5110 -                              ^ Use of compiler reserved name (_T_0)

dsdt.dsl  8621:                 Method (_WED, 1, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (_WED)

dsdt.dsl  8621:                 Method (_WED, 1, NotSerialized)
Warning  1080 -                            ^ Reserved method must return a value (_WED)

dsdt.dsl  8627:                             Return (OEMN ())
Warning  1092 -                                        ^ Called method may not always return a value

dsdt.dsl  8665:                 Method (WMBD, 3, NotSerialized)
Warning  1087 -                            ^ Not all control paths return a value (WMBD)

ASL Input:  dsdt.dsl - 8837 lines, 327847 bytes, 3822 keywords
AML Output: dsdt.aml - 32998 bytes, 929 named objects, 2893 executable opcodes

Compilation complete. 0 Errors, 21 Warnings, 9 Remarks, 934 Optimizations

```

---

### Post by loluyemi on 2010-08-02
Help me with this please. Thanks so much.

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/bibby/dsdt.dsl   104:     Method (\_WAK, 1, NotSerialized)
Warning  1080 -                             ^ Reserved method must return a value (_WAK)

/home/bibby/dsdt.dsl  3540:                 Method (_Q16, 0, NotSerialized)
Warning  1087 -   Not all control paths return a value ^  (_Q16)

/home/bibby/dsdt.dsl  7714:                 Method (_HOT, 0, Serialized)
Warning  1087 -   Not all control paths return a value ^  (_HOT)

/home/bibby/dsdt.dsl  7714:                 Method (_HOT, 0, Serialized)
Warning  1080 -    Reserved method must return a value ^  (_HOT)

/home/bibby/dsdt.dsl  7716:                     Zero
Error    4095 -                                    ^ syntax error, unexpected PARSEOP_ZERO

/home/bibby/dsdt.dsl  7723:                 Method (_CRT, 0, Serialized)
Warning  1087 -   Not all control paths return a value ^  (_CRT)

/home/bibby/dsdt.dsl  7723:                 Method (_CRT, 0, Serialized)
Warning  1080 -    Reserved method must return a value ^  (_CRT)

/home/bibby/dsdt.dsl  7725:                     Zero
Error    4095 -                                    ^ syntax error, unexpected PARSEOP_ZERO

ASL Input:  /home/bibby/dsdt.dsl - 8137 lines, 278758 bytes, 4173 keywords
Compilation complete. 2 Errors, 6 Warnings, 0 Remarks, 1127 Optimizations

---

### Post by ari197 on 2010-08-09
Hi .. wondering if you could help me.. I have an Acer Aspire 4745G.. on the ACPI battery state, the present rate and remaining capacity is UNKNOWN, but it detected the battery.

When I tried to decompile the dsdt file (attached) using iasl I got "Segmentation Fault" error.

Many thanks

---

### Post by giorgio.01 on 2010-09-01
toschiba L650-116 DSDT problem recompiling
kernel.

Hello everyone. I had to recompile the kernel
DSDT the right, to enable the suspensions.
I all right until kernel 2.6.33.7, 2.6.34 after getting error, ubuntu does not start, because 'thing' changed?
What's wrong?
sorry but I'm Italian, but Italian forum
nobody and 'managed to explain.
I have ubuntu 10.04 64 bit
because 'I can compile the 2.6.33.7, and I can not compile 2.6.34 and 2.6.35?

---

### Post by fish_sticks on 2010-09-05
I'm having the problem relating to my display.It keeps dimming after about 20 seconds and then blacks out in 5.When I press a key in the keyboard,I get it back.

My dsdt.dsl looks like this

iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  5252:                         Method (_BQC, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_BQC)

dsdt.dsl  8927:                             Name (_T_1, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_1)

dsdt.dsl  8928:                             Name (_T_0, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_0)

dsdt.dsl  8985:                             Name (_T_1, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_1)

dsdt.dsl  8986:                             Name (_T_0, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_0)

dsdt.dsl  9128:                             Name (_T_1, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_1)

dsdt.dsl  9129:                             Name (_T_0, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_0)

dsdt.dsl  9186:                             Name (_T_1, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_1)

dsdt.dsl  9187:                             Name (_T_0, Zero)
Remark   5110 -        Use of compiler reserved name ^  (_T_0)

dsdt.dsl 10634:                 Name (_T_2, Zero)
Remark   5110 -                          ^ Use of compiler reserved name (_T_2)

dsdt.dsl 10635:                 Name (_T_1, Zero)
Remark   5110 -                          ^ Use of compiler reserved name (_T_1)

dsdt.dsl 10636:                 Name (_T_0, Zero)
Remark   5110 -                          ^ Use of compiler reserved name (_T_0)

ASL Input:  dsdt.dsl - 12302 lines, 374787 bytes, 4162 keywords
AML Output: dsdt.aml - 42447 bytes, 971 named objects, 3191 executable opcodes

Compilation complete. 0 Errors, 1 Warnings, 11 Remarks, 10 Optimizations

Please help me out.

---

### Post by fish_sticks on 2010-09-06
can anybody help me out here with this problem?

---

### Post by elian83 on 2010-09-12
Hi guys,

Can you please help me checking my DSDT? /proc/acpi/fan and /proc/acpi/thermal_zone are empty.

```

# iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  1354:             Method (_HOT, 0, Serialized)
Warning  1087 -                        ^ Not all control paths return a value (_HOT)

dsdt.dsl  1354:             Method (_HOT, 0, Serialized)
Warning  1080 -                        ^ Reserved method must return a value (_HOT)

dsdt.dsl  1377:             Method (_CRT, 0, Serialized)
Warning  1087 -                        ^ Not all control paths return a value (_CRT)

dsdt.dsl  1377:             Method (_CRT, 0, Serialized)
Warning  1080 -                        ^ Reserved method must return a value (_CRT)

dsdt.dsl  1430:             Method (_PSV, 0, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (_PSV)

dsdt.dsl  1430:             Method (_PSV, 0, NotSerialized)
Warning  1080 -                        ^ Reserved method must return a value (_PSV)

dsdt.dsl  6495:                         Name (_T_0, Zero)
Remark   5110 -    Use of compiler reserved name ^  (_T_0)

dsdt.dsl  6537:                         Name (_T_0, Zero)
Remark   5110 -    Use of compiler reserved name ^  (_T_0)

dsdt.dsl  7943:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (_GTM)

dsdt.dsl  7943:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -                                ^ Reserved method must return a value (_GTM)

dsdt.dsl  8103:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  8103:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  8171:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  8171:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  8244:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (_GTM)

dsdt.dsl  8244:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -                                ^ Reserved method must return a value (_GTM)

dsdt.dsl  8404:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  8404:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  8472:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  8472:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  8577:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (_GTM)

dsdt.dsl  8577:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -                                ^ Reserved method must return a value (_GTM)

dsdt.dsl  8737:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  8737:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  8805:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  8805:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  8878:                     Method (_GTM, 0, NotSerialized)
Warning  1087 -                                ^ Not all control paths return a value (_GTM)

dsdt.dsl  8878:                     Method (_GTM, 0, NotSerialized)
Warning  1080 -                                ^ Reserved method must return a value (_GTM)

dsdt.dsl  9038:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  9038:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  9106:                         Method (_GTF, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_GTF)

dsdt.dsl  9106:                         Method (_GTF, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_GTF)

dsdt.dsl  9994:                 Store (Package (0x02)
Warning  1099 -     Statement is unreachable ^ 

ASL Input:  dsdt.dsl - 11446 lines, 403928 bytes, 5514 keywords
AML Output: dsdt.aml - 47047 bytes, 980 named objects, 4534 executable opcodes

Compilation complete. 0 Errors, 31 Warnings, 2 Remarks, 40 Optimizations


```My laptop model is HP HDX 16. 

Thanks in advance.
Elian.

---

### Post by elian83 on 2010-09-14
Hi,

I replaced:

```

          Method (_HOT, 0, Serialized)
            {
                If (LGreaterEqual (OSYS, 0x07D6))
                {
                    If (LEqual (\_SB.PCI0.LPC.EC0.QUAD, One))
                    {
                        Return (0x0E94)
                    }
                    Else
                    {
                        If (LEqual (TJMX, 0x64))
                        {
                            Return (0x0EC6)
                        }
                    }

                    If (LEqual (TJMX, 0x55))
                    {
                        Return (0x0E30)
                    }
                }
            }

          Method (_CRT, 0, Serialized)
            {
                If (LGreaterEqual (OSYS, 0x07D6))
                {
                    If (LEqual (\_SB.PCI0.LPC.EC0.QUAD, One))
                    {
                        Return (0x0E94)
                    }
                    Else
                    {
                        If (LEqual (TJMX, 0x64))
                        {
                            Return (0x0EC6)
                        }
                    }

                    If (LEqual (TJMX, 0x55))
                    {
                        Return (0x0E30)
                    }
                }
            }

```to:

```

            Method (_HOT, 0, Serialized)
            {
                    Return (Add (0x0AAC, Multiply (TPC, 0x0A)))
            }

            Method (_CRT, 0, Serialized)
            {
                    Return (Add (0x0AAC, Multiply (TPC, 0x0A)))

            }

```and now I have thermal readings on /proc/acpi/thermal_zone/TZ01/ , but still no /proc/acpi/fan 

What am I missing? 

Thanks for you help!

---

### Post by elian83 on 2010-09-17
I fixed all the problems related to the sh*tty DSDT implementation in HP HDX 16. Attached you can find the file.

```

# iasl -tc dsdt_fixed.dsl 

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

ASL Input:  dsdt_fixed.dsl - 11342 lines, 400660 bytes, 5449 keywords
AML Output: dsdt.aml - 46688 bytes, 981 named objects, 4468 executable opcodes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 40 Optimizations

```Thermal readings are ok:

elian@Elian-PC:~$ sudo cat /proc/acpi/thermal_zone/TZ01/temperature 
temperature:             43 C

Suspend is working too. Fan is BIOS based, so /proc/acpi/fan is empty.

Shame on you HP! 8 months waiting an answer: [http://h30434.www3.hp.com/t5/Hardware/HP-HDX-16-BIOS-bug-suspend-thermal-info/td-p/211300](http://h30434.www3.hp.com/t5/Hardware/HP-HDX-16-BIOS-bug-suspend-thermal-info/td-p/211300)

---

### Post by bulva on 2010-10-08
Hello,
I have succesfully debugged DSDT file on Toshiba Satellite l300-257 running Linux MInt Debian with 2.6.32-5-686 kernel, though it seems that the new dsdt file does not stick (and indeed when I pulled the dsdt file after the reboot it was again the old, buggy one). I attach the output of dmesg command, what could be the cause?

---

### Post by mockingbird on 2010-10-22
For people who are getting a bunch of rubbish, something about more than 200 errors and/or a segmentation fault when running "iasl -tc dsdt.dsl", it's caused by a buggy version of iasl.

Do the following:  (In Konsole)
1)  **[COLOR="Red"]sudo kate /etc/apt/sources.list[/COLOR]** (Keep in mind, replace "kate" with your text editor.  I use Kubuntu :-p.  Use gedit if you use Ubuntu or whatever it is Gnome people use these days)
2)  Go all the way down to the end of the page.  Add the following entry: [COLOR="Red"]**[deb http://us.debian.org/debian squeeze main contrib non-free](deb http://us.debian.org/debian squeeze main contrib non-free)**[/COLOR] (We're going to use Debian's testing repository to download the latest iasl instead of downloading the source or the .deb and trying to resolve all the dependencies ourselves).  Save the changes and exit.
3)  Next we need to add the keyring.  There's two ways to go about this.  We can tell APT to disregard the missing keyring for Debian's repositories or we can add the keyring.  We're going to add it by typing:
[COLOR="Red"]**sudo su**[/COLOR]
[COLOR="Red"]**gpg --keyserver wwwkeys.eu.pgp.net --recv 9AA38DCD55BE302B**[/COLOR]
[COLOR="Red"][B]gpg --export --armor 9AA38DCD55BE302B | apt-key add -
[/B][/COLOR]
4)  Close the Konsole and reopen it to get out of superuser mode.  Sometimes I can add keyrings with just sudo, other times I get errors.  If you can't sudo su, then skip that step and try with just sudo before all the commands.
5)  [COLOR="Red"]**sudo apt-get update**[/COLOR]
6)  [COLOR="Red"]**sudo apt-get remove iasl**[/COLOR] (If it's already installed)
7)  [COLOR="Red"]**sudo apt-get install -t squeeze iasl**[/COLOR]
&#56;&#41;  [COLOR="Red"]**cd /home/<yourusername>**[/COLOR] (If you tried this before, remove any of your previous dsdt files you may have, type [COLOR="Red"]**sudo rm dsdt.***[/COLOR])
9)  [COLOR="Red"]**sudo cat /proc/acpi/dsdt > dsdt.dat**[/COLOR]  (Some people may get a "Permission Denied" error.  If you do use [COLOR="Red"]**sudo cat /proc/acpi/dsdt | sudo tee dsdt.dat**[/COLOR] instead.
10)  Next, [COLOR="Red"]**iasl -d dsdt.dat**[/COLOR] and then [COLOR="Red"]**iasl -tc /home/<yourusername>/dsdt.dsl**[/COLOR], my result:

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100528 [Jul  2 2010]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

/home/moishe/dsdt.dsl  1007:                     0x00000000,         // Length
Error    4122 -                                           ^ Invalid combination of Length and Min/Max fixed flags

/home/moishe/dsdt.dsl  1021:                     0x00000000,         // Length
Error    4122 -                                           ^ Invalid combination of Length and Min/Max fixed flags

ASL Input:  /home/moishe/dsdt.dsl - 7616 lines, 275364 bytes, 3155 keywords
Compilation complete. 2 Errors, 0 Warnings, 0 Remarks, 43 Optimizations
```

---

### Post by mockingbird on 2010-10-22
In my case, the errors are fixed by doing the following (courtesy of [mitch](http://www.insanelymac.com/forum/index.php?showtopic=189272&st=80#) from the insanelymac forums):

Edit the dsdt.dsl file and go to the line where iasl indicated the error.  In my case I go to lines 1007 and and 1021:
```
DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0xDFFFFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00000000,         // Length
                    ,, _Y0D, AddressRangeMemory, TypeStatic)
```
So iasl is complaining about the "Length" line "0x00000000".  This is wrong.  Look at the "Range Minimum" and "Range Maximum".  Open up your Kcalc or whatever you Gnome people use and change it to Numeral System Mode.  Make sure HEX is selected and now we subtract the maximum range from the minimum range and then we add 1.  Since the minimum range is 0 (And you can't subtract 0) I will input DFFFFFFF and then add 1 which gives me E0000000 (Don't get confused, I'm simply omitting "0x", the calculator doesn't need this).  I change 0x00000000 to 0xE0000000 by Length.  So now it looks like this:
```
DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0x00000000,         // Range Minimum
                    0xDFFFFFFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0xE0000000,         // Length
                    ,, _Y0D, AddressRangeMemory, TypeStatic)
```
Good.  One down, one left to go:
```
DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
                    0x00000000,         // Granularity
                    0xFED40000,         // Range Minimum
                    0xFED44FFF,         // Range Maximum
                    0x00000000,         // Translation Offset
                    0x00005000,         // Length
                    ,, , AddressRangeMemory, TypeStatic)<snip>
```

For the line 1021 error, I subtract 0xFED44FFF from 0xFED40000 (Remember, I'm subtracting the MAXIMUM range from the MINIMUM range or else I end up with a negative number - remember your elementary school arithmetic), and then I add 1.The length needs to be changed to 0x00005000.

The result:
```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100528 [Jul  2 2010]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

ASL Input:  /home/moishe/dsdt.dsl - 7616 lines, 275364 bytes, 3155 keywords
AML Output: /home/moishe/dsdt.aml - 27850 bytes, 683 named objects, 2472 executable opcodes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 43 Optimizations
```

For anyone who's curious, I'm using a **Toshiba A200**.

---

### Post by mathieud on 2010-11-11
Hello there,

I have an old (second hand) HP Compaq 6710b. This laptop is known to be noisy. The fan spins almost all the time. Apparently the fan is controlled by the BIOS (not sure what this means)...

I have succeeded to update the BIOS (version F16 from HP) but the fan is still very loud.

I found a script to manually set the fan speed. It basically echo values (3 to turn on, 0 to turn off to /proc/acpi/fan/C3C*).

Here are some info about the trip points setting and temperature sensor:
```

/proc/acpi/thermal_zone/TZ0$ more trip_points 
critical (S5):           256 C
passive (forced):<not set>
active[0]:               82 C: devices=C3C1 
active[1]:               74 C: devices=C3C2 
active[2]:               66 C: devices=C3C3 
active[3]:               45 C: devices=C3C4 
active[4]:               30 C: devices=C3C5 
/proc/acpi/thermal_zone/TZ0$ more temperature 
temperature:             45 C

```

Whatever the computer is doing the temperature of TZ0 is 45°C.

Interestingly if I use sys instead of proc:
```

/sys/class/thermal/thermal_zone0$ more temp 
31000

```

I have de-assembled the DSDT and IASL find several syntax error...

Can anyone help me? There seems to be DSDT experts here...

Thanks in advance.
Mathieu

P.S.: I'm not sure about this but right after the BIOS update a colleague showed a USB bootable windows system. Right after the fan was less noisy (only spinning sometimes) and I believe that trip points were set to higher temperatures... Unfortunately I reset the BIOS settings and then spend the afternoon trying to understand what's going on.

**Edit:**

I shutdown the PC for a few hours and trip points have changed:
```

/proc/acpi/thermal_zone/TZ0$ more trip_points 
critical (S5):           256 C
passive (forced):<not set>
active[0]:               82 C: devices=C3C1 
active[1]:               74 C: devices=C3C2 
active[2]:               66 C: devices=C3C3 
active[3]:               **50 C**: devices=C3C4 
active[4]:               30 C: devices=C3C5 

```
So the noise is ok again...

**Edit:**
Hum... Tonight processors seem stuck at 800Mhz. I have played with cpufreqd. It was working yesterday...

**Edit:**
And this morning CPU frequency scale well (I use "on demand" policy)...

---

### Post by mtnova on 2010-11-26
If by any chance 67GTA is still browsing this thread, Your help will be greatly appreciated with this Aspire 5100 DSDT.


Many thanks

mtnova

---

### Post by VSEAE15O on 2011-01-09
> **67GTA said:**
> peterwill:

You can't get the DSDT source. It is hard coded in the BIOS. The only way that would work is if your BIOS vendor made an error free DSDT and packaged it in a BIOS update. We are simply grabbing a copy of it from the BIOS and trying to patch it. Then we tell the OS to use it instead of the original. After a lot of reading, I found Toshiba laptops have a lot of trouble with Linux. That's why I suggested trying toshset. It doesn't seem the fan issue is linked to your DSDT errors, and it is disabled by default. I was starting to wonder if we were chasing our tails in your case. You can get a 64bit source package of toshset here: [http://schwieters.org/toshset/toshset64.gz](http://schwieters.org/toshset/toshset64.gz)

Model: HP DV6-2190us
Problem: MSFT compiled DSDT

67GTA, i read you posts and it seems very ordinary for Microsoft to break things useful to people.  

Similar to what you said, I also read that by extracting DSDT from any system with a MSFT compiled BIOS, regardless the OS, will always result in an erroneous DSDT.dsl which will not compile into DSDT.aml unless patched.  

The hackintosh camp has been trying to patch DSDT to avoid ACPI issues namely sleep, reboot, power off functions, audio, and multi-core cpus issue here: [http://tonymacx86.com/viewtopic.php?f=14&t=1202 and here ]("http://tonymacx86.com/viewtopic.php?f=14&t=1202")[http://www.insanelymac.com/forum/index.php?showtopic=215033&st=60]("http://www.insanelymac.com/forum/index.php?showtopic=215033&st=60") only Yehia Amer is trying to patch the DSDT.dsl done by a MSFT compiler.  This is the reason why some oem BIOs, namely HP, has faulty DSDT which confused the guy who maintains iasl.  Only when he helped Yehia Amer, he simply commented out the errors.  I am not sure if Yehia's DSDT.aml worked, but if I remember correctly, it gave him a kernel panic during boot--I will ask him of this.

Do you need my dmesg output and dsdt.dsl?  Will you take a look at it and see if you can rid the errors?  I will forward you the patch-in-progress as per the above mentioned site i have followed; however, i have come upon a kink which I have no knowledge of the asm language.  Thanks.

---

### Post by irodlak on 2011-01-11
Hi! 

I would like to ask something! I tried to make my custom dsdt today with DSDTSE. I started with compile-ing but I still have some issues: The error list is the following:

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20091214 [Dec 16 2009]
Copyright © 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 4.0

/Users/kaldoritamas/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl 4744: Arg0
Error 4096 - syntax error, unexpected PARSEOP_ARG0 ^ 

/Users/kaldoritamas/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl 4744: Arg0
Warning 1100 - Statement is unreachable ^ 

/Users/kaldoritamas/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl 5033: Method (_BQC, 0, NotSerialized)
Warning 1088 - Not all control paths return a value ^ (_BQC)

/Users/kaldoritamas/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl 5033: Method (_BQC, 0, NotSerialized)
Warning 1081 - Reserved method must return a value ^ (_BQC)

ASL Input: /Users/kaldoritamas/Library/Application Support/EvOSoftware/DSDT/DSDTFiles/dsdt.dsl - 12385 lines, 374388 bytes, 4048 keywords
Compilation complete. 1 Errors, 3 Warnings, 0 Remarks, 11 Optimizations


Can somebody help me with an advice how to continue?

Thanks!
Tom

ps: my laptop is Dell 501x.

---

### Post by angryelephant on 2011-01-16
I'm working on a Toshiba Satellite T235D. Worked okay on 10.04, but on upgrading to 10.10 I can't even get it to boot unless I pass acpi=off in grub. I tried recompiling the dsdt with the stock version of iasl and using the instructions for the debian testing version of iasl, but both gave me about 176 errors. Looks like scope issues but I'm not good enough in assembly to resolve them. 

DSDT is attached if anyone wants to take a wack at fixing it.

---

### Post by GhaleonX on 2011-02-02
Hello. I've been reading through tons and tons of pages trying to find how I can fix the buggy DSDT on my HP d330 uT. I came across your thread which was somewhat helpful, but the bulk of the problem I'm running into is that the ACPI tables I dumped from this machine look to be rather messy and quite different from other DSDT I've looked at. 

 While I understand this is a linux board, the nature of fixing the problem should be the same (or extremely similar; I compile with -sa instead of -tc)

Anyway, any help is VERY appreciated :)

First off, here's my system:
Pentium 4 Prescott (SSE2/SSE3) 2.4GHz
Intel ICH5
Motherboard is P4SD Rev 1.09, which came from a HP d330 uT
Bios is Hewlett-Packard-786B2v2.44
External graphics: nVidia GeForce FX5200 128MB AGP (QE/CI/Dual-VGA working)
Currently running Leopard 10.5.8 (with CoreGraphics Framework from 10.5.5, as that's the last version to support my 5200)
Voodoo/XNU kernel 9.8
Chameleon RC5 699

Here's my untouched ACPI dump, obtained via chameleon:
[ACPI.rar]("http://www.mediafire.com/?pg8qdwbta6ui1cj")

And here's my dsdt.aml which I obtained via ubuntu 8.10 live CD
[dsdt.aml]("http://www.mediafire.com/?vya82kkyy52mcmq")

 I have tried a couple things with the SSDT-X.aml files - namely SSDT-1  and SSDT-3, which I tried fixing the RTC and power button, but I don't  think I was able to fix either one (although RTC looked just like  everything I've seen for others, so perhaps it did work). I also got  compile errors in dsdt.aml for every _S5D instance, which the fix was  just to remove the _ character (although _S1D through _S4D are all  fine).

 I have all these files in my /Extra folder and all are named in my boot.plist (I also see chameleon load them during startup). **/ If you're unfamiliar with this part due to it being OSX, it just means I have the files where they should be, and that I know they are loaded upon startup.

 My main goals are to get the RTC fix, power button to give option for  sleep/restart/shutdown, and as many 'little things' I can do as I figure  things out. Thanx for any assistance!

---

### Post by Danny182 on 2011-02-06
hello, i can't solve this problem. 
please help me

/home/daniel/dsdt.dsl   372:             Package (0x06)
Error    4047 -            Initializer list too long ^ 



```
 Package (0x06)
            {
                0x0898, 
                0x00015BA8, 
                0x64, 
                0x09, 
                0xE020288E, 
                0x008E
            },
            Package (0x06)
            {
                0x07D0, 
                0x00010D88, 
                0x64, 
                0x09, 
                0xE020298C, 
                0x018C
            }, 
            Package (0x06)
            {
                0x0708, 
                0x0000C350, 
                0x64, 
                0x09, 
                0xE0202A8A, 
                0x028A
            },
            Package (0x06)
            {
                0x03E8, 
                0x000055F0, 
                0x64, 
                0x09, 
                0xE0202C82, 
                0x0482
            },
            Package (0x06)
            {
                0xFFFF, 
                0xFFFFFFFF, 
                0xFF, 
                0xFF, 
                0xFFFFFFFF, 
                0x03FF
            }
        })
    }

    Scope (\_SB)
    {
```






the first line i wrote is 372

---

### Post by GhaleonX on 2011-02-09
Danny, post the whole dsl file

---

### Post by angryelephant on 2011-02-16
> **angryelephant said:**
> I'm working on a Toshiba Satellite T235D. Worked okay on 10.04, but on upgrading to 10.10 I can't even get it to boot unless I pass acpi=off in grub. I tried recompiling the dsdt with the stock version of iasl and using the instructions for the debian testing version of iasl, but both gave me about 176 errors. Looks like scope issues but I'm not good enough in assembly to resolve them. 

DSDT is attached if anyone wants to take a wack at fixing it.
I was able to compile without errors by commenting out generous amounts of code but the problem was not fixed.

---

### Post by keplenk on 2011-03-05
Hi guys, 

I have a Google Netbook CR48 and I need help in fixing my DSDT.  I'm having a bunch of ACPI problems (mostly fan issues) and maybe you could help me.

My dsdt compiles fine but with warnings.  0 Errors 16 Warnings 1 Remarks

Most of the errors are very much the same thing so I'll post the most common one:

```

Name (NBTT, Package (0x08)
Remark   5048 -                              Initializer list shorter than declared package length 


Method (_GTM, 0, NotSerialized)
Warning  1088 -                              Not all control paths return a value ^  (_GTM)


Method (_GTM, 0, NotSerialized)
Warning  1081 -                              Reserved method must return a value ^  (_GTM)


Method (_GTF, 0, NotSerialized)
Warning  1088 -                              Not all control paths return a value ^  (_GTF)


Method (_GTF, 0, NotSerialized)
Warning  1081 -                             Reserved method must return a value ^  (_GTF)



```

I currently have 10.10 right now and maybe someone could give me a tip to fix it. I've been trying to search in google but I'm really out of luck.  I'll just attach my dsdt for reference.

Thanks!

---

### Post by Chamwiz on 2011-03-15
@mockingbird

Hey, I tried running that code, because I also exceed the 200 error cap, and I had a timeout issue where it can't access the site to add it to the keyring. (Note: I also tried [www.keys.eu.pgp.net](www.keys.eu.pgp.net) incase the "wwwkeys" was a typo)

```

$ sudo gpg --keyserver wwwkeys.eu.pgp.net --recv 9AA38DCD55BE302B
gpg: requesting key 55BE302B from hkp server wwwkeys.eu.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```

I wasn't sure if you knew of a site to download the accurate version of iasl at, or if you know a work around to get the repository working.  Any advice is appreciated!

P.S. Running Ubuntu 10.10 Maverick

---

### Post by h_ingmar14 on 2011-03-18
Hi, guys!

Model: HP Pavilion dv6 1123sl
OS: Ubuntu 10.10 x86

Problem: 
Possible BUGGY DSDT. I think I fixed all warnigs and errors that showed the compiler, but "dmesg" still shows them. So I can' t understand whether the DSDT is overrided. Please help to deal with the problem.

===================================================================
[    0.166209] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query honored via cmdline
===================================================================
[    0.349558] ACPI Exception: AE_NOT_FOUND, Evaluating _PRW (20101013/scan-723)
===================================================================
[   14.725817] ACPI Error: [T_1_] Namespace lookup failure, AE_ALREADY_EXISTS (20101013/dswload-802)
[   14.725825] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20101013/psloop-231)
[   14.725830] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEGP.VGA_.LCD_.GBQC] (Node f3822438), AE_ALREADY_EXISTS (20101013/psparse-537)
[   14.725838] ACPI: Marking method GBQC as Serialized because of AE_ALREADY_EXISTS error
[   14.725844] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEGP.VGA_.LCD_._BQC] (Node f3822420), AE_ALREADY_EXISTS (20101013/psparse-537)
[   14.725851] ACPI: Marking method _BQC as Serialized because of AE_ALREADY_EXISTS error
[   14.725857] ACPI Warning: Evaluating _BQC failed (20101013/video-538)
[   14.726877] IR Sony protocol handler initialized
[   14.734912] acpi device:08: registered as cooling_device2
[   14.735689] ACPI Error: [T_1_] Namespace lookup failure, AE_ALREADY_EXISTS (20101013/dswload-802)
[   14.735697] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20101013/psloop-231)
[   14.735702] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEGP.VGA_.LCD1.GBQC] (Node f38225b8), AE_ALREADY_EXISTS (20101013/psparse-537)
[   14.735710] ACPI: Marking method GBQC as Serialized because of AE_ALREADY_EXISTS error
[   14.735716] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEGP.VGA_.LCD1._BQC] (Node f38225a0), AE_ALREADY_EXISTS (20101013/psparse-537)
[   14.735723] ACPI: Marking method _BQC as Serialized because of AE_ALREADY_EXISTS error
[   14.735729] ACPI Warning: Evaluating _BQC failed (20101013/video-538)
==================================================================

Thanks for paying attention!

P.S. Sorry for possible grammar or syntax mistakes. English isn't my native language.

---

### Post by vincentvega_1985 on 2011-03-29
hey guys

i've got a toshiba satellite u500-115, which has issues with acpi under linux. i recently found out about dsdt and decided to try and fix it. i have found a u500 dsdt table, that someone else fixed, but unfortunately, that one only fixed part of the problem. if i start my laptop when it's cold, the fan never kicks in. i need to restart it, so bios starts the fan, then it works fine.

so i decided to try and fix it myself. i have managed to fix most errors, exept one:
Error 4122  ^ Invalid combination of Length and Min/Max fixed flags
the error occured here:

DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, NonCacheable, ReadWrite,
                        0x00000000,         // Granularity
                        0x00000000,         // Range Minimum
                        0xFFFFFFFF,         // Range Maximum
                        0x00000000,         // Translation Offset
                        0x00000000,         // Length
                        ,, _Y09, AddressRangeMemory, TypeStatic)

I have googled this issue, and found that Length should be Max-Min+1
the problem, as you can see, the max value is FFFFFFFF and the min value is 00000000
so the length should be 100000000 (one character too long)
what exactly can i do to fix this?
also, what are remarks? do i need to fix them? can't find anything on google about this...
thanks in advance!
cheers

---

### Post by aflaouras on 2011-04-09
Hello guys,

I have this error:

```
 iasl -tc /home/aflaouras/dsdt.dsl 

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

/home/aflaouras/dsdt.dsl     1: ACPI                  Store (0x40, ^OSTB)
Error    4095 -                    ^ syntax error, unexpected PARSEOP_NAMESEG, expecting PARSEOP_DEFINITIONBLOCK

ASL Input:  /home/aflaouras/dsdt.dsl - 7245 lines, 279590 bytes, 0 keywords
Compilation complete. 1 Errors, 0 Warnings, 0 Remarks, 0 Optimizations

```

Can anyone help me to fix it???

I attach the files

---

### Post by streilu on 2011-04-15
Hi ubuntu-Forums!

Since i have massive Problems with mit dsdt-File i thought i could ask for help here.
My compiling-log looks like this:

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl   389:             Method (_OSC, 5, NotSerialized)
Warning  1076 -                        ^ Reserved method has too many arguments (_OSC requires 4)

dsdt.dsl   403:                         And (CAPB, 0xFFFFFFFC)
Warning  1105 -                                 ^ Result is not used, operator has no effect

dsdt.dsl   404:                         Or (CAPB, 0x00)
Warning  1105 -                                ^ Result is not used, operator has no effect

dsdt.dsl  3160:                             Acquire (Z000, 0xFFFF)
Warning  1099 -                Statement is unreachable ^

dsdt.dsl  3358:                             Acquire (Z000, 0xFFFF)
Warning  1099 -                Statement is unreachable ^

dsdt.dsl  3557:                             Acquire (Z000, 0xFFFF)
Warning  1099 -                Statement is unreachable ^

dsdt.dsl  3756:                             Acquire (Z000, 0xFFFF)
Warning  1099 -                Statement is unreachable ^

dsdt.dsl  3915:                             Acquire (Z000, 0xFFFF)
Warning  1099 -                Statement is unreachable ^

dsdt.dsl  4109:                             Acquire (Z000, 0xFFFF)
Warning  1099 -                Statement is unreachable ^

dsdt.dsl  4302:                             Acquire (Z000, 0xFFFF)
Warning  1099 -                Statement is unreachable ^

dsdt.dsl  4486:                             Acquire (Z000, 0xFFFF)
Warning  1099 -                Statement is unreachable ^

dsdt.dsl  4761:                             Acquire (Z000, 0xFFFF)
Warning  1099 -                Statement is unreachable ^

dsdt.dsl  5626:     Method (_WAK, 1, NotSerialized)
Warning  1080 -                ^ Reserved method must return a value (_WAK)

ASL Input:  dsdt.dsl - 5794 lines, 228900 bytes, 2007 keywords
AML Output: dsdt.aml - 19454 bytes, 689 named objects, 1318 executable opcodes

Compilation complete. 0 Errors, 13 Warnings, 0 Remarks, 602 Optimizations

```

May anyone help me fixing it?

Greets from Austria,
streilu

---

### Post by mockingbird on 2011-05-13
> **Chamwiz said:**
> @mockingbird

Hey, I tried running that code, because I also exceed the 200 error cap, and I had a timeout issue where it can't access the site to add it to the keyring. (Note: I also tried [www.keys.eu.pgp.net](www.keys.eu.pgp.net) incase the "wwwkeys" was a typo)

```

$ sudo gpg --keyserver wwwkeys.eu.pgp.net --recv 9AA38DCD55BE302B
gpg: requesting key 55BE302B from hkp server wwwkeys.eu.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```

I wasn't sure if you knew of a site to download the accurate version of iasl at, or if you know a work around to get the repository working.  Any advice is appreciated!

P.S. Running Ubuntu 10.10 Maverick

I don't know whether or not you still need this, but I found a different keyring server, so try this instead:

sudo gpg --keyserver pgpkeys.mit.edu --recv 9AA38DCD55BE302B

Now I myself have another question:

I upgraded to Kubuntu 11.04, and I can't find my DSDT file.

Did they deprecate something and thus changed the structure?  I do recall reading something about /proc/acpi being deprecated.

Does anyone know how to retrieve the DSDT file with the newer kernels?

Thanks

---

### Post by mockingbird on 2011-05-13
Ok, the new location for this is /sys/firmware/acpi/tables.

Here is my output of iasl -tc:
```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100528 [Oct 15 2010]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

dsdt.dsl   372:     Method (\_WAK, 1, NotSerialized)
Warning  1081 -                 ^ Reserved method must return a value (Integer/Package required for _WAK)

dsdt.dsl   430:             Store (Local0, Local0)
Error    4051 -                         ^ Method local variable is not initialized (Local0)

dsdt.dsl   435:             Store (Local0, Local0)
Error    4051 -                         ^ Method local variable is not initialized (Local0)

dsdt.dsl   617:                         0xFFF00000,         // Length
Error    4117 -                                  ^ Length is larger than Min/Max window

dsdt.dsl  2890:                         Store (Local0, Local0)
Error    4051 -                                     ^ Method local variable is not initialized (Local0)

ASL Input:  dsdt.dsl - 5276 lines, 171319 bytes, 1877 keywords
Compilation complete. 4 Errors, 1 Warnings, 0 Remarks, 568 Optimizations
```

I will browse through this thread for similar problems...

---

### Post by mockingbird on 2011-05-13
```
dsdt.dsl   372:     Method (\_WAK, 1, NotSerialized)
Warning  1081 -                 ^ Reserved method must return a value (Integer/Package required for _WAK)
```
For this error, all we do is find the \_WAK, 1, NotSerialized on line 372, look for the closing bracket "}" of its subcommands, and add "Return(Package(0x02){0x00, 0x00})" (without the quotes) before the end. 
```
dsdt.dsl   430:             Store (Local0, Local0)
Error    4051 -                         ^ Method local variable is not initialized (Local0)
```
For this, all we do is comment out the "Store Local0" line by adding "/*" to the beginning of the line and "*/" to the end (w/o the quotes).
```
dsdt.dsl   435:             Store (Local0, Local0)
Error    4051 -                         ^ Method local variable is not initialized (Local0)
```
Same here.
```
dsdt.dsl   617:                         0xFFF00000,         // Length
Error    4117 -                                  ^ Length is larger than Min/Max window
```
In the DSL file, there's a Minlength here and a Maxlength.  Just subtract the maxlength from the minlength and replace 0xFFF00000 witht he correct result.  I've gone through this in an earlier post.  When you subtract the hex values in Kcalc or whatever you use, don't try and figure out how to put the "0x" part in the calculator.  Only everything hat comes after the "x".
```
dsdt.dsl  2890:                         Store (Local0, Local0)
Error    4051 -                                     ^ Method local variable is not initialized (Local0)
```
Same as before.

...and, our result:
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100528 [Oct 15 2010]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

ASL Input:  dsdt.dsl - 5278 lines, 171386 bytes, 1875 keywords
AML Output: dsdt.aml - 16301 bytes, 620 named objects, 1255 executable opcodes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 570 Optimizations

---

### Post by SH4RK300 on 2011-06-04
Hello,

I have a new Dell M5010 (with newest A10 BIOS, AMD P360), and I have a problem. It's overheating (70 °C at boot, 75 °C at work, the service say's OK, but Dell it's not...).
I want to edit DSDT, but it doesn't have Thermal Zone :( and I got many error during recompline...

Can somebody help me?

---

### Post by YavkatA on 2011-06-08
I've been working on fixing the Compaq Presario CQ61 DSDT since I discovered that the fan spins slow all the time and the laptop overheats. 

I have managed to fix it and now it compiles without any errors. :D

 Everything works as expected, the fan speeds up when the load gets hight, but It is still running a little bit hot. I am willing to trade some noise for a few degrees down, and I am trying to figure out where in the DSDT can I control the fan speed? I have been looking into it for a long time and I still cannot figure it out...

Any help would be greatly appreciated ;)

---

### Post by guandalino on 2011-06-09
** Laptop:** HP Pavilion [dv6 6008el]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c02787040&jumpid=reg_R1002_USEN") (2Ghz Intel Core i7 2630QM, 8Gb DDR3, Radeon HD 6490 1Gb, 500Gb sata 7200rpm).

My laptop doesn't boot - blank screen - if acpi=off is not specified in grub, that way disabling ACPI entirely (unacceptable). Ubuntu 10.04 LTS and 10.10 aren't affected, Natty 11.04 *is*.  I followed debug instructions on LessWatts and discovered DSDT table is broken, please help!

[HTML]
DSDT.dsl    37:     External (\TNOT)
Error    4057 -                   ^ Name already exists in scope (\TNOT)

DSDT.dsl 11050:     Method (PAPR, 0, NotSerialized)
Warning  1088 -                ^ Not all control paths return a value (PAPR)

DSDT.dsl 12566:     Method (_CRS, 0, NotSerialized)
Warning  1088 -                ^ Not all control paths return a value (_CRS)

DSDT.dsl 12566:     Method (_CRS, 0, NotSerialized)
Warning  1081 -                ^ Reserved method must return a value (Buffer required for _CRS)
[/HTML]Thanks

---

### Post by mathfeel on 2011-06-25
For my DSDT file, when recompiling, at first I get a series of error like this:

```
dsdt.dsl  8236:                             Name (_PLD, Buffer (0x10)
Error    4080 -              Invalid object type for reserved name ^  (found BUFFER, requires Package)
```

I changed s/Buffer/Package/ in each line and the Errors are gone.

All that remains are these Warnings:
```
# iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100528 [Jun 23 2011]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

dsdt.dsl  4421:                                     If (LFLS ())
Warning  1093 -                                            ^ Called method may not always return a value

dsdt.dsl  4524:                                 If (LFLS ())
Warning  1093 -                                        ^ Called method may not always return a value

dsdt.dsl  4547:                                 If (LFLS ())
Warning  1093 -                                        ^ Called method may not always return a value

dsdt.dsl  4612:                                     If (LFLS ())
Warning  1093 -                                            ^ Called method may not always return a value

dsdt.dsl  4624:                                     If (LFLS ())
Warning  1093 -                                            ^ Called method may not always return a value

dsdt.dsl  4644:                     Method (LFLS, 0, NotSerialized)
Warning  1088 -                                ^ Not all control paths return a value (LFLS)

dsdt.dsl  9060:                         Store (\_SB.PCI0.LPC.EC.SLBN (), Local0)
Warning  1093 -        Called method may not always return a value ^ 

dsdt.dsl  9385:             Method (SLBN, 0, NotSerialized)
Warning  1088 -                        ^ Not all control paths return a value (SLBN)

dsdt.dsl  9854:             Method (_Q15, 0, NotSerialized)
Warning  1088 -                        ^ Not all control paths return a value (_Q15)

ASL Input:  dsdt.dsl - 13834 lines, 450481 bytes, 5744 keywords
AML Output: dsdt.aml - 50486 bytes, 1110 named objects, 4634 executable opcodes
```

which I am not sure how to fix. Please help!

This is for a Lenovo ThinkPAD x201 Tablet.

---

### Post by GreekRockNRoller on 2011-07-13
Hello i tried to copy the dsdt file to my home folder but there is no such file in /proc/acpi/ do you know what i could do?

EDIT: i think that it is now located in folder /sys/firmware/acpi/tables/ is that correct?

---

### Post by deadite66 on 2011-09-19
i have a Pentium M 760 Dothan C0 2.00 GHz and motherboard has ACPI 1.0

cpu scaling is broken with natty and oneiric likely due to the kernel devs no longer supporting kernel hacks and choosing to go for the safer acpi option.

is it possible to hack the DSDT to get cpufreq working again.
currently i'm stuck with p4-clockmod and 1.5GHz.

---

### Post by eloralon on 2011-09-20
Hello experts,

I have an HP Envy 14T-2000 (Beatsaudio) and have extracted it's dsdt. When I try to compile it I get the following error and warnings: 

19      Error	Name already exists in scope (\TNOT)
2316	Remark	Initializer list shorter than declared package length 
4520	Warning	Not all control paths return a value (_HID)
4520	Warning	Reserved method must return a value (Integer/String required for _HID)
4579	Warning	Not all control paths return a value (_CID)
4579	Warning	Reserved method must return a value (Integer/String/Package required for _CID)
5052	Warning	Not all control paths return a value (_BST)
14218	Warning	Not all control paths return a value (_CRS)
14218	Warning	Reserved method must return a value (Buffer required for _CRS)

Can you please help fix the above errors so I can compile and use it on my Ubuntu 11.04 installation?

I have attached the DSDT file for easy reference.

Thank you.

---

### Post by Dewitts on 2011-09-28
Hi, I'm not a programmer by any means and i'm trying to edit my DSDT.
Any help would be appreciated.
Warning Not all control paths return a value (HKDS)
Warning Not all control paths return a value (_WED)
Reserved method must return a value (Integer/string/buffer required..
Warning Not all control paths return a value (WMC9)
Warning Not all control paths return a value (WRC8 )
Warning Not all control paths return a value (WMCD)
Warning Not all control paths return a value (WMCF)
Warning Not all control paths return a value (WB15)

Can someone point me in the right direction? i've also attached my dsdt for viewing.

Thanks

---

### Post by Dewitts on 2011-09-28
> **SH4RK300 said:**
> Hello,

I have a new Dell M5010 (with newest A10 BIOS, AMD P360), and I have a problem. It's overheating (70 °C at boot, 75 °C at work, the service say's OK, but Dell it's not...).
I want to edit DSDT, but it doesn't have Thermal Zone :( and I got many error during recompline...

Can somebody help me?

Used my dsdt editor to try and automatically repair the 124 errors,

1 Error left 1 or 2 warnings and 1 remark I think... though much improved on the original... Give it a whirl ;)

(that's about my limit)

---

### Post by Zane Chua on 2011-10-05
> **Dewitts said:**
> Hi, I'm not a programmer by any means and i'm trying to edit my DSDT.
Any help would be appreciated.
Warning Not all control paths return a value (HKDS)
Warning Not all control paths return a value (_WED)
Reserved method must return a value (Integer/string/buffer required..
Warning Not all control paths return a value (WMC9)
Warning Not all control paths return a value (WRC8 )
Warning Not all control paths return a value (WMCD)
Warning Not all control paths return a value (WMCF)
Warning Not all control paths return a value (WB15)

Can someone point me in the right direction? i've also attached my dsdt for viewing.

Thanks

[http://www.acpica.org/downloads/binary_tools.php](http://www.acpica.org/downloads/binary_tools.php)

Use iasl.

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20110922-32 [Sep 22 2011]
Copyright (c) 2000 - 2011 Intel Corporation

ASL Input:     dsdt.dsl - 10261 lines, 394545 bytes, 4083 keywords
AML Output:    dsdt.aml - 40492 bytes, 879 named objects, 3204 executable opcode
s
Hex Dump:      dsdt.hex - 385045 bytes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 39 Optimizations
```

---

### Post by Zane Chua on 2011-10-05
> **eloralon said:**
> Hello experts,

I have an HP Envy 14T-2000 (Beatsaudio) and have extracted it's dsdt. When I try to compile it I get the following error and warnings: 

19      Error	Name already exists in scope (\TNOT)
2316	Remark	Initializer list shorter than declared package length 
4520	Warning	Not all control paths return a value (_HID)
4520	Warning	Reserved method must return a value (Integer/String required for _HID)
4579	Warning	Not all control paths return a value (_CID)
4579	Warning	Reserved method must return a value (Integer/String/Package required for _CID)
5052	Warning	Not all control paths return a value (_BST)
14218	Warning	Not all control paths return a value (_CRS)
14218	Warning	Reserved method must return a value (Buffer required for _CRS)

Can you please help fix the above errors so I can compile and use it on my Ubuntu 11.04 installation?

I have attached the DSDT file for easy reference.

Thank you.

Fixed. Should have Provided me with the .aml instead.

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20110922-32 [Sep 22 2011]
Copyright (c) 2000 - 2011 Intel Corporation

ASL Input:     DSDT.dsl - 14398 lines, 576367 bytes, 6723 keywords
AML Output:    dsdt.aml - 62775 bytes, 1191 named objects, 5532 executable opcod
es
Hex Dump:      DSDT.hex - 596705 bytes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 29 Optimizations

```

---

### Post by Zane Chua on 2011-10-05
> **mathfeel said:**
> For my DSDT file, when recompiling, at first I get a series of error like this:

```
dsdt.dsl  8236:                             Name (_PLD, Buffer (0x10)
Error    4080 -              Invalid object type for reserved name ^  (found BUFFER, requires Package)
```

I changed s/Buffer/Package/ in each line and the Errors are gone.

All that remains are these Warnings:
```
# iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100528 [Jun 23 2011]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

dsdt.dsl  4421:                                     If (LFLS ())
Warning  1093 -                                            ^ Called method may not always return a value

dsdt.dsl  4524:                                 If (LFLS ())
Warning  1093 -                                        ^ Called method may not always return a value

dsdt.dsl  4547:                                 If (LFLS ())
Warning  1093 -                                        ^ Called method may not always return a value

dsdt.dsl  4612:                                     If (LFLS ())
Warning  1093 -                                            ^ Called method may not always return a value

dsdt.dsl  4624:                                     If (LFLS ())
Warning  1093 -                                            ^ Called method may not always return a value

dsdt.dsl  4644:                     Method (LFLS, 0, NotSerialized)
Warning  1088 -                                ^ Not all control paths return a value (LFLS)

dsdt.dsl  9060:                         Store (\_SB.PCI0.LPC.EC.SLBN (), Local0)
Warning  1093 -        Called method may not always return a value ^ 

dsdt.dsl  9385:             Method (SLBN, 0, NotSerialized)
Warning  1088 -                        ^ Not all control paths return a value (SLBN)

dsdt.dsl  9854:             Method (_Q15, 0, NotSerialized)
Warning  1088 -                        ^ Not all control paths return a value (_Q15)

ASL Input:  dsdt.dsl - 13834 lines, 450481 bytes, 5744 keywords
AML Output: dsdt.aml - 50486 bytes, 1110 named objects, 4634 executable opcodes
```

which I am not sure how to fix. Please help!

This is for a Lenovo ThinkPAD x201 Tablet.

Fixed.

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20110922-32 [Sep 22 2011]
Copyright (c) 2000 - 2011 Intel Corporation

ASL Input:     dsdt.dsl - 13839 lines, 450520 bytes, 5746 keywords
AML Output:    dsdt.aml - 50490 bytes, 1110 named objects, 4636 executable opcod
es
Hex Dump:      dsdt.hex - 480046 bytes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 2799 Optimizations

```

---

### Post by Zane Chua on 2011-10-05
> **guandalino said:**
> ** Laptop:** HP Pavilion [dv6 6008el]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c02787040&jumpid=reg_R1002_USEN") (2Ghz Intel Core i7 2630QM, 8Gb DDR3, Radeon HD 6490 1Gb, 500Gb sata 7200rpm).

My laptop doesn't boot - blank screen - if acpi=off is not specified in grub, that way disabling ACPI entirely (unacceptable). Ubuntu 10.04 LTS and 10.10 aren't affected, Natty 11.04 *is*.  I followed debug instructions on LessWatts and discovered DSDT table is broken, please help!

[HTML]
DSDT.dsl    37:     External (\TNOT)
Error    4057 -                   ^ Name already exists in scope (\TNOT)

DSDT.dsl 11050:     Method (PAPR, 0, NotSerialized)
Warning  1088 -                ^ Not all control paths return a value (PAPR)

DSDT.dsl 12566:     Method (_CRS, 0, NotSerialized)
Warning  1088 -                ^ Not all control paths return a value (_CRS)

DSDT.dsl 12566:     Method (_CRS, 0, NotSerialized)
Warning  1081 -                ^ Reserved method must return a value (Buffer required for _CRS)
[/HTML]Thanks

Fixed.

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20110922-32 [Sep 22 2011]
Copyright (c) 2000 - 2011 Intel Corporation

ASL Input:     DSDT.dsl - 12753 lines, 424443 bytes, 5911 keywords
AML Output:    DSDT.aml - 50369 bytes, 1037 named objects, 4874 executable opcod
es
Hex Dump:      DSDT.hex - 478905 bytes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 20 Optimizations

```

---

### Post by DiaVad on 2011-10-09
Hi. Asus MB E35M1-M with AMD Zacate APU and + 2 network cards. 10.04.03 server sometimes throw out messages in console "irq 19: nobody cared"_**_[]("http://answers.softpicks.net/answers/topic/irq-19-nobody-cared-1783802-1.htm") and become laggy till reboot it. Even with "irqpoll" option its just happen less frequently. I try a couple of kernels. Last one is 2.6.38-11 lucid. Compiling DSDT cause lot of errors. Help please!

---

### Post by Zane Chua on 2011-10-11
Upload the aml file please.

---

### Post by mikejonesey on 2011-10-14
this is an amazing thread... my gratitude...

I've fixed a couple of bugs in my dsdt, would anyone be able to check my other bugs... (uploading aml)...

many thanks,
mike

---

### Post by mikejonesey on 2011-10-14
almost finished just a couple more to go...

---

### Post by mikejonesey on 2011-10-14
finished... (par one bug, which i found info on [here]("http://lists.acpica.org/pipermail/devel/2010-July/000164.html")), but i'll just leave that one as i don't think it'll affect anything much...

attached is my final dsdt... maybe it will be helpful for anyone with hp g6 to diff... if anyone can give the start to finish a quick diff to check my changes would be appreciated...

cheers,
mike

---

### Post by www.rzr.online.fr on 2011-10-17
> **guandalino said:**
> ** Laptop:** HP Pavilion [dv6 6008el]("http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c02787040&jumpid=reg_R1002_USEN") (2Ghz Intel Core i7 2630QM, 8Gb DDR3, Radeon HD 6490 1Gb, 500Gb sata 7200rpm).

My laptop doesn't boot - blank screen - if acpi=off is not specified in grub, that way disabling ACPI entirely (unacceptable). Ubuntu 10.04 LTS and 10.10 aren't affected, Natty 11.04 *is*.  I followed debug instructions on LessWatts and discovered DSDT table is broken, please help!

[HTML]
DSDT.dsl    37:     External (\TNOT)
Error    4057 -                   ^ Name already exists in scope (\TNOT)



can you tell what brand is your bios ? because I have the same error on lenovo g470 :


```
DSDT.dsl    36:     External (\TNOT)
Error    4057 -  Name already exists in scope ^  (\TNOT)
```

---

### Post by qiou on 2011-10-29
Hi,

Could someone help me fix my DSDT table ? I'm stuck with the warning and remarks, I've fixed the 2 errors (Min/Max error using Max - Min + 1 equation).
I've got an Acer 4820TG with 1.25 bios, maybe someone as already fixed the dsdt table.
Particularities of this model : ATI switchable graphic between Intel GPU and ATI GPU.
System : ArchLinux.

I've attached my dsdt.aml (and .dsl if you need it) to the post.

Thx,
Qiou.

---

### Post by silenx on 2011-11-15
Hello everyone, i need help on this DSDT
OS: Debian and Xubuntu
I need ( if we can ) both the .aml,.dsl, and .hex file ( hex used as override on a recompiled kernel )
Thanks a lot for this work/service.

---

### Post by Zane Chua on 2011-11-28
> **silenx said:**
> Hello everyone, i need help on this DSDT
OS: Debian and Xubuntu
I need ( if we can ) both the .aml,.dsl, and .hex file ( hex used as override on a recompiled kernel )
Thanks a lot for this work/service.

Fixed.

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20111123-32 [Nov 23 2011]
Copyright (c) 2000 - 2011 Intel Corporation

ASL Input:     dsdt.dsl - 10262 lines, 391345 bytes, 4083 keywords
AML Output:    dsdt.aml - 40492 bytes, 879 named objects, 3204 executable opcode
s
Hex Dump:      dsdt.hex - 385045 bytes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 39 Optimizations

```

---

### Post by Zane Chua on 2011-11-28
> **qiou said:**
> Hi,

Could someone help me fix my DSDT table ? I'm stuck with the warning and remarks, I've fixed the 2 errors (Min/Max error using Max - Min + 1 equation).
I've got an Acer 4820TG with 1.25 bios, maybe someone as already fixed the dsdt table.
Particularities of this model : ATI switchable graphic between Intel GPU and ATI GPU.
System : ArchLinux.

I've attached my dsdt.aml (and .dsl if you need it) to the post.

Thx,
Qiou.

Fixed.

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20111123-32 [Nov 23 2011]
Copyright (c) 2000 - 2011 Intel Corporation

ASL Input:     dsdt.dsl - 12305 lines, 399767 bytes, 5230 keywords
AML Output:    dsdt.aml - 48751 bytes, 1117 named objects, 4113 executable opcod
es
Hex Dump:      dsdt.hex - 463477 bytes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 6 Optimizations
```

---

### Post by jjjooonnn on 2011-12-07
I'm trying to compile a buggy DSDT file, The error I got is below. I deleted the line and was able to compile it. Will it work?

dsdt.dsl    35:     External (\TNOT)
Error    4057 -                    ^ Name already exists in scope (\TNOT)

I've attached the DSDT.dsl and the compiled .aml
Couldn't find a way to fix on my own.

---

### Post by lexqqq on 2011-12-08
Hi all

I have buggy DSDT too and I can not compile it. It is Dell N7110 with i5 processor.
Please help

Thank you

---

### Post by Zane Chua on 2011-12-09
> **jjjooonnn said:**
> I'm trying to compile a buggy DSDT file, The error I got is below. I deleted the line and was able to compile it. Will it work?

dsdt.dsl    35:     External (\TNOT)
Error    4057 -                    ^ Name already exists in scope (\TNOT)

I've attached the DSDT.dsl and the compiled .aml
Couldn't find a way to fix on my own.


Fixed.

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20111123-32 [Nov 23 2011]
Copyright (c) 2000 - 2011 Intel Corporation

ASL Input:     DSDT.dsl - 10027 lines, 334778 bytes, 3619 keywords
AML Output:    DSDT.aml - 36690 bytes, 864 named objects, 2755 executable opcode
s
Hex Dump:      DSDT.hex - 348945 bytes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 16 Optimizations

```

---

### Post by Zane Chua on 2011-12-09
> **lexqqq said:**
> Hi all

I have buggy DSDT too and I can not compile it. It is Dell N7110 with i5 processor.
Please help

Thank you

Yawn. There's a reason why your .aml file is required instead of a .dsl

---

### Post by lexqqq on 2011-12-12
> **Zane Chua said:**
> Yawn. There's a reason why your .aml file is required instead of a .dsl

please can u explain me?
I can not get .aml because of compile errors. And I need it because of installing Mac OS X on my PC. I know that this forum is for ubuntu users, but this is the only place I found where forum users fix DSDT.

So please can you explain me? Is it possible to repair this dsl file so I could compile it? Or how can I get .aml file?

---

### Post by Zane Chua on 2011-12-21
> **lexqqq said:**
> please can u explain me?
I can not get .aml because of compile errors. And I need it because of installing Mac OS X on my PC. I know that this forum is for ubuntu users, but this is the only place I found where forum users fix DSDT.

So please can you explain me? Is it possible to repair this dsl file so I could compile it? Or how can I get .aml file?

I am not going to repair a 200 over error DSL file since it's been decompiled with an ancient version of IASL.

Besides, this forum is meant for Ubuntu Users and if you're trying to hackintosh you should have said so from the start.

[http://www.insanelymac.com/forum/index.php?showtopic=215844](http://www.insanelymac.com/forum/index.php?showtopic=215844) 

Boot into Ubuntu and use the python script to extract your .aml file.

DO NOT GIVE ME A 0KB file. Check that it actually has data in it.

---

### Post by devilkin on 2011-12-31
I know this thread is quite ancient, but is anyone still helping with fixing dsdts?

I'm trying to get the dsdt of an Acer Ferrari 200 fixed, but it keeps annoying me with 21 errors.

---

### Post by r07f1 on 2012-01-17
Hi first post x) 

can somebody can help me fix my tolhiba laptop dsdt...


tks in advance

---

### Post by awett on 2012-01-31
Hi there i got no luck fixing my dsdt i am unsing a ibm intellistation a pro with 2 opteron 285 cpu&#347; thank you

---

### Post by Zane Chua on 2012-02-04
> **devilkin said:**
> I know this thread is quite ancient, but is anyone still helping with fixing dsdts?

I'm trying to get the dsdt of an Acer Ferrari 200 fixed, but it keeps annoying me with 21 errors.

I was going to help you but apparently you already helped yourself. Good Job. But just so you know that you might have been able to avoid some errors if you had used an updated version of iasl.

[http://sadevil.org/blog/2012/01/01/fixing-the-acpi-dsdt-of-an-acer-ferrari-one-200/](http://sadevil.org/blog/2012/01/01/fixing-the-acpi-dsdt-of-an-acer-ferrari-one-200/)

EDIT:

Also for the other two posters after devilkin. I have repeatedly said in my previous posts that posting the .aml would be so much better but I guess no one reads posts these days. They all just want help and providing the information specifically not asked for.

---

### Post by vhughes on 2012-02-05
wew. im having a hard time following steps..Good luck!

[Santa Ana In-Home]("http://www.phcsicare.com")

---

### Post by Ravven on 2012-02-06
Hello, ubuntu forums!

I'm strugling with cleaning my ASUS X73SV DSDT. I've found it to be quite troublesome. I've been looking for solutions at few places now, but unfortunately some of my DSDT warrings have never been corrected before (or I just simply can't find a solution). So I'm asking you, experienced users, for help.

Till now I've corrected two errors (pnp0c14 changed to PNP0C14) and few remarks (_T_* changed to T_*).

I'm still getting few warnings:

```


Intel ACPI Component Architecture
ASL Optimizing Compiler version 20120111-32 [Jan 11 2012]
Copyright (c) 2000 - 2012 Intel Corporation

dsdt.dsl   4376:                     Method (_CID, 0, NotSerialized)
Warning  1113 -                                 ^ Not all control paths return a value (_CID)

dsdt.dsl   4376:                     Method (_CID, 0, NotSerialized)
Warning  1105 -                                 ^ Reserved method must return a value (Integer/String/Package required for _CID)

dsdt.dsl   4515:                 Method (_REG, 2, NotSerialized)
Warning  1079 -                             ^ _REG has no corresponding Operation Region

dsdt.dsl   8588:                                     Return (\OPVK ())
Warning  1119 -      Called method may not always return a value ^ 

dsdt.dsl   9230:                     Method (_CRS, 0, NotSerialized)
Warning  1113 -                                 ^ Not all control paths return a value (_CRS)

dsdt.dsl   9230:                     Method (_CRS, 0, NotSerialized)
Warning  1105 -                                 ^ Reserved method must return a value (Buffer required for _CRS)

dsdt.dsl  14798:             Return (Ones)
Warning  1130 -                         ^ Statement is unreachable

dsdt.dsl  14829:             Return (Ones)
Warning  1130 -                         ^ Statement is unreachable

dsdt.dsl  16706:                         Return (One)
Warning  1103 -                                    ^ Reserved method should not return a value (_Q0E)

dsdt.dsl  16742:             Return (One)
Warning  1103 -                        ^ Reserved method should not return a value (_Q0E)

dsdt.dsl  16764:                         Return (One)
Warning  1103 -                                    ^ Reserved method should not return a value (_Q0F)

dsdt.dsl  16798:             Return (One)
Warning  1103 -                        ^ Reserved method should not return a value (_Q0F)

dsdt.dsl  16814:         Method (_Q11, 0, Serialized)
Warning  1113 -                     ^ Not all control paths return a value (_Q11)

dsdt.dsl  16819:                 Return (One)
Warning  1103 -                            ^ Reserved method should not return a value (_Q11)

dsdt.dsl  19164:         Method (OPVK, 0, Serialized)
Warning  1113 -                     ^ Not all control paths return a value (OPVK)

dsdt.dsl  19428:         Method (_ON, 0, NotSerialized)
Warning  1113 -                    ^ Not all control paths return a value (_ON_)

dsdt.dsl  19504:         Method (MXDS, 1, NotSerialized)
Warning  1113 -                     ^ Not all control paths return a value (MXDS)

dsdt.dsl  19534:             If (LNotEqual (SVID, 0xFFFFFFFF))
Warning  1130 -                          ^ Statement is unreachable

ASL Input:     dsdt.dsl - 20191 lines, 600498 bytes, 9029 keywords
AML Output:    DSDT.aml - 71065 bytes, 1944 named objects, 7085 executable opcodes

Compilation complete. 0 Errors, 18 Warnings, 0 Remarks, 2710 Optimizations
[Completed]

```

I've attached the dsdt files (with my corrections applied) and txt file with warnings. To extract and compile I've used Jan 2012 iasl. Quite possibly the solution for my warnings is quite simple and I've just missed it somewhere.

Thanks for the help.

---

### Post by awett on 2012-02-07
Sorry i didn read it so here is my dsdt.aml thank you very much :-)

---

### Post by djjovica on 2012-02-07
Hi to all, 

will i get the same dsdt  extracting it from aida64 from windows, and extracting it from ubutnu ?

Here is my dsdt hp dv7, need help fixing errors and warnings

[ATTACH]212226[/ATTACH]

Tnx for help

---

### Post by awett on 2012-02-08
this is how far i get 

but still :

Feb  9 00:59:18 andre-desktop kernel: powernow-k8: Found 2 Dual Core AMD Opteron(tm) Processor 285 (4 cpu cores) (version 2.20.00)
Feb  9 00:59:18 andre-desktop kernel: powernow-k8: fid 0x12 (2600 MHz), vid 0x8
Feb  9 00:59:18 andre-desktop kernel: powernow-k8: fid 0x10 (2400 MHz), vid 0xa
Feb  9 00:59:18 andre-desktop kernel: powernow-k8: fid 0xe (2200 MHz), vid 0xc
Feb  9 00:59:18 andre-desktop kernel: powernow-k8: fid 0xc (2000 MHz), vid 0xe
Feb  9 00:59:18 andre-desktop kernel: powernow-k8: fid 0xa (1800 MHz), vid 0xe
Feb  9 00:59:18 andre-desktop kernel: powernow-k8: fid 0x2 (1000 MHz), vid 0xe
Feb  9 00:59:18 andre-desktop kernel: [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
Feb  9 00:59:18 andre-desktop kernel: [Firmware Bug]: powernow-k8: Try again with latest BIOS.
Feb  9 00:59:26 andre-desktop kernel: EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Feb  9 00:59:26 andre-desktop kernel: EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
Feb  9 01:00:08 andre-desktop kernel: wlan1: authenticate with bc:05:43:60:c7:d7 (try 1)
Feb  9 01:00:08 andre-desktop kernel: wlan1: authenticated
Feb  9 01:00:08 andre-desktop kernel: wlan1: associate with bc:05:43:60:c7:d7 (try 1)
Feb  9 01:00:08 andre-desktop kernel: wlan1: RX AssocResp from bc:05:43:60:c7:d7 (capab=0x411 status=0 aid=3)
Feb  9 01:00:08 andre-desktop kernel: wlan1: associated
Feb  9 01:00:08 andre-desktop kernel: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Feb  9 01:00:08 andre-desktop kernel: Intel AES-NI instructions are not detected.
Feb  9 01:00:18 andre-desktop kernel: wlan1: no IPv6 routers present
Feb  9 01:02:28 andre-desktop kernel: powernow-k8: Found 2 Dual Core AMD Opteron(tm) Processor 285 (4 cpu cores) (version 2.20.00)
Feb  9 01:02:28 andre-desktop kernel: powernow-k8: fid 0x12 (2600 MHz), vid 0x8
Feb  9 01:02:28 andre-desktop kernel: powernow-k8: fid 0x10 (2400 MHz), vid 0xa
Feb  9 01:02:28 andre-desktop kernel: powernow-k8: fid 0xe (2200 MHz), vid 0xc
Feb  9 01:02:28 andre-desktop kernel: powernow-k8: fid 0xc (2000 MHz), vid 0xe
Feb  9 01:02:28 andre-desktop kernel: powernow-k8: fid 0xa (1800 MHz), vid 0xe
Feb  9 01:02:28 andre-desktop kernel: powernow-k8: fid 0x2 (1000 MHz), vid 0xe
Feb  9 01:02:28 andre-desktop kernel: [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
Feb  9 01:02:28 andre-desktop kernel: [Firmware Bug]: powernow-k8: Try again with latest BIOS.

---

### Post by MrSlaggers on 2012-02-10
For whatever reason the fan on my HP dv6-6183nr laptop runs almost constantly at high speeds even when the laptop is not very hot. When the laptop does cool down, the fan sometimes lowers its RPM, however it never seems to turn off completely. In Windows 7 the fan works well in that it only turns on when needed, however with Ubuntu the problem persists. I ran into this blog post [http://notebookequus.blogspot.com/2008/09/patching-dsdt-table.html](http://notebookequus.blogspot.com/2008/09/patching-dsdt-table.html) that gives a tutorial on how fix some fan issues in Windows and I thought I would follow the tutorial but with Ubuntu.

Unfortunately I ran into a problem at this point: 

sudo cat /proc/acpi/dsdt > dsdt.dat
cat: /proc/acpi/dsdt: No such file or directory

If anyone can help me resolve this fan issue I would be grateful. Thanks.

---

### Post by goodgod43 on 2012-02-26
I tried to fix this myself, but I couldn't find anyone who had the same error. This one actually tells me that the problem is on line 1 of all places. I haven't seen anything like it online. If anyone could help, that would be great.

---

### Post by srinivasakp on 2012-04-20
can someone fix acer aspire 5536 dsdt issue.

root@srinivasa-laptop:/home/srinivasa/Desktop/srinivasa# iasl -sa dsdt.dsl 

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20090521 [Jun 30 2009]
Copyright (C) 2000 - 2009 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl   389:     Method (_WAK, 1, NotSerialized)
Warning  1080 -                ^ Reserved method must return a value (_WAK)

dsdt.dsl   755:             Name (_HID, "*pnp0c14")
Error    4001 -                                  ^ String must be entirely alphanumeric (*pnp0c14)

dsdt.dsl   814:             Method (_WED, 1, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (_WED)

dsdt.dsl   814:             Method (_WED, 1, NotSerialized)
Warning  1080 -                        ^ Reserved method must return a value (_WED)

dsdt.dsl  1200:             Method (WMC9, 3, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (WMC9)

dsdt.dsl  1463:             Method (WRCB, 2, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (WRCB)

dsdt.dsl  1644:             Method (WMCD, 3, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (WMCD)

dsdt.dsl  2242:             Method (WMCF, 3, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (WMCF)

dsdt.dsl  2354:             Method (WB15, 6, NotSerialized)
Warning  1087 -                        ^ Not all control paths return a value (WB15)

dsdt.dsl  3361:                 Method (AFN0, 0, Serialized)
Warning  1087 -                            ^ Not all control paths return a value (AFN0)

dsdt.dsl  3365:                         Return (\_SB.PCI0.AGP.VGA.AFN0 ())
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3370:                         Return (\_SB.PCI0.PB2.VGA.AFN0 ())
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3375:                         Return (\_SB.PCI0.PB3.VGA.AFN0 ())
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3387:                 Method (AFN3, 2, Serialized)
Warning  1087 -                            ^ Not all control paths return a value (AFN3)

dsdt.dsl  3391:                         Return (\_SB.PCI0.AGP.VGA.AFN3 (Arg0, Arg1))
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3396:                         Return (\_SB.PCI0.PB2.VGA.AFN3 (Arg0, Arg1))
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3401:                         Return (\_SB.PCI0.PB3.VGA.AFN3 (Arg0, Arg1))
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3405:                 Method (AFN4, 1, Serialized)
Warning  1087 -                            ^ Not all control paths return a value (AFN4)

dsdt.dsl  3409:                         Return (\_SB.PCI0.AGP.VGA.AFN4 (Arg0))
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3414:                         Return (\_SB.PCI0.PB2.VGA.AFN4 (Arg0))
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3419:                         Return (\_SB.PCI0.PB3.VGA.AFN4 (Arg0))
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3423:                 Method (AFN5, 0, Serialized)
Warning  1087 -                            ^ Not all control paths return a value (AFN5)

dsdt.dsl  3427:                         Return (\_SB.PCI0.AGP.VGA.AFN5 ())
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3432:                         Return (\_SB.PCI0.PB2.VGA.AFN5 ())
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3437:                         Return (\_SB.PCI0.PB3.VGA.AFN5 ())
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3441:                 Method (AFN6, 0, Serialized)
Warning  1087 -                            ^ Not all control paths return a value (AFN6)

dsdt.dsl  3445:                         Return (\_SB.PCI0.AGP.VGA.AFN6 ())
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3450:                         Return (\_SB.PCI0.PB2.VGA.AFN6 ())
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  3455:                         Return (\_SB.PCI0.PB3.VGA.AFN6 ())
Error    4060 -                       Called method returns no value ^ 

dsdt.dsl  9695:                         Return (PX02 (DerefOf (Index (Arg1, 0x02))))
Error    4060 -     Called method returns no value ^ 

dsdt.dsl  9700:                         Return (PX03 (DerefOf (Index (Arg1, 0x02))))
Error    4060 -     Called method returns no value ^ 

ASL Input:  dsdt.dsl - 10223 lines, 367270 bytes, 4604 keywords
Compilation complete. 18 Errors, 13 Warnings, 0 Remarks, 1591 Optimizations
root@srinivasa-laptop:/home/srinivasa/Desktop/srinivasa#

---

### Post by rrll1977 on 2012-07-27
Hello guys,

Wondering whether you've got a fixed DSDT.aml for the Pavilion tx2532la
I'm getting these warnings when I try to compile mine:

```
Intel ACPI Component Architecture
ASL Optimizing Compiler version 20080926 [Oct  4 2008]
Copyright (C) 2000 - 2008 Intel Corporation
Supports ACPI Specification Revision 3.0a

dsdt.dsl  2518:                         Method (_BCL, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_BCL)

dsdt.dsl  2518:                         Method (_BCL, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_BCL)

dsdt.dsl  2532:                         Method (_BQC, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_BQC)

dsdt.dsl  2532:                         Method (_BQC, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_BQC)

dsdt.dsl  2812:                         Method (_BCL, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_BCL)

dsdt.dsl  2812:                         Method (_BCL, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_BCL)

dsdt.dsl  2826:                         Method (_BQC, 0, NotSerialized)
Warning  1087 -                                    ^ Not all control paths return a value (_BQC)

dsdt.dsl  2826:                         Method (_BQC, 0, NotSerialized)
Warning  1080 -                                    ^ Reserved method must return a value (_BQC)

dsdt.dsl  8238:             Method (_HOT, 0, Serialized)
Warning  1087 -                        ^ Not all control paths return a value (_HOT)

dsdt.dsl  8238:             Method (_HOT, 0, Serialized)
Warning  1080 -                        ^ Reserved method must return a value (_HOT)

dsdt.dsl  8245:             Method (_CRT, 0, Serialized)
Warning  1087 -                        ^ Not all control paths return a value (_CRT)

dsdt.dsl  8245:             Method (_CRT, 0, Serialized)
Warning  1080 -                        ^ Reserved method must return a value (_CRT)

ASL Input:  dsdt.dsl - 8307 lines, 301040 bytes, 4052 keywords
AML Output: dsdt.aml - 37533 bytes, 803 named objects, 3249 executable opcodes

Compilation complete. 0 Errors, 12 Warnings, 0 Remarks, 14 Optimizations

```

Any help is appreciated

---

### Post by 20072006 on 2012-08-17
Please Help me!!!I can't fix all error!!!Can you fix it for me please?!!!
Here is my DSDT file:

---

### Post by leonidas300 on 2012-09-10
I also have a buggy DSDT with a lot of errors (>200). My laptop is Dell Inspiron N7110. I attach my **DSDT.dsl** and the results of **lspci, dmidecode and dmesg**. How can I fix those errors? Thank you!

---

### Post by Statia on 2012-10-09
> **67GTA said:**
>  Follow my how to to the point of getting your dsdt.dsl file and send it to me. I will see if I can fix the errors.

Can you also fix a DSDT if lm-sensors gets no output from your motherboard sensors?

---

### Post by bashphoenux on 2012-10-22
can someone help with my dsdt ?
Thanks in advance

---

### Post by marcelpado on 2012-11-29
guys, I have four in my dsdt problem, can you help me?
or tell me how to fix it?
I appreciate any response from now.

```
dsdt.dsl  3186:                         Name (_VPC, 0x0140)
Warning  1099 -            Unknown reserved name ^  (_VPC)

dsdt.dsl  3193:                         Method (_CFG, 0, NotSerialized)
Warning  1099 -              Unknown reserved name ^  (_CFG)

dsdt.dsl  3193:                         Method (_CFG, 0, NotSerialized)
Warning  1099 -              Unknown reserved name ^  (_CFG)

dsdt.dsl  3364:                             P8XH (0x04, 0x17, Zero)
Warning  1100 -       Statement is unreachable ^ 

```

Notebook Lenovo G470 CORE I3

my dsdt:

---

### Post by Hanhbau on 2013-04-10
I have 1 error, 6 warnings, 7 remarks:

 Intel ACPI Component ArchitectureASL Optimizing Compiler version 20100528 [Oct  1 2012]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a


/home/hoang/dsdt.dsl    38:     External (\TNOT)
Error    4057 -   Name already exists in scope ^  (\TNOT)


/home/hoang/dsdt.dsl  5528:                     Acquire (MWMI, 0x0005)
Warning  1105 -                Possible operator timeout is ignored ^ 


/home/hoang/dsdt.dsl  6274:             Method (_Q0C, 0, NotSerialized)
Warning  1088 -                                    ^ Not all control paths return a value (_Q0C)


/home/hoang/dsdt.dsl  6287:             Method (_Q0D, 0, NotSerialized)
Warning  1088 -                                    ^ Not all control paths return a value (_Q0D)


/home/hoang/dsdt.dsl  6320:             Method (_Q12, 0, NotSerialized)
Warning  1088 -                                    ^ Not all control paths return a value (_Q12)


/home/hoang/dsdt.dsl  6600:                 Name (_T_0, Zero)
Remark   5111 -        Use of compiler reserved name ^  (_T_0)


/home/hoang/dsdt.dsl  8383:                             Name (_T_0, Zero)
Remark   5111 -                    Use of compiler reserved name ^  (_T_0)


/home/hoang/dsdt.dsl  8461:                             Name (_T_0, Zero)
Remark   5111 -                    Use of compiler reserved name ^  (_T_0)


/home/hoang/dsdt.dsl  8539:                             Name (_T_0, Zero)
Remark   5111 -                    Use of compiler reserved name ^  (_T_0)


/home/hoang/dsdt.dsl  8617:                             Name (_T_0, Zero)
Remark   5111 -                    Use of compiler reserved name ^  (_T_0)


/home/hoang/dsdt.dsl  8797:                             Name (_T_0, Zero)
Remark   5111 -                    Use of compiler reserved name ^  (_T_0)


/home/hoang/dsdt.dsl  8875:                             Name (_T_0, Zero)
Remark   5111 -                    Use of compiler reserved name ^  (_T_0)


/home/hoang/dsdt.dsl 12881:                 Method (_CRS, 0, NotSerialized)
Warning  1088 -   Not all control paths return a value ^  (_CRS)


/home/hoang/dsdt.dsl 12881:                 Method (_CRS, 0, NotSerialized)
Warning  1081 -    Reserved method must return a value ^  (Buffer required for _CRS)

Can someone help me, please?
My dsdt:[ATTACH]241170[/ATTACH]

---

### Post by goon3 on 2013-08-21
> **Zane Chua said:**
> Fixed. Should have Provided me with the .aml instead.

```

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20110922-32 [Sep 22 2011]
Copyright (c) 2000 - 2011 Intel Corporation

ASL Input:     DSDT.dsl - 14398 lines, 576367 bytes, 6723 keywords
AML Output:    dsdt.aml - 62775 bytes, 1191 named objects, 5532 executable opcod
es
Hex Dump:      DSDT.hex - 596705 bytes

Compilation complete. 0 Errors, 0 Warnings, 0 Remarks, 29 Optimizations

```
Thank you very mach. You help me.
```
Method (_CRS, 0, NotSerialized)  // _CRS: Current Resource Settings
                {
                    If (IGDS)
                    {
                        Return (CRS)
                    }
**                    Return (Buffer (One) -- this drive my crazy -- need add this return in my case**
**                        {**
**                            0x00**
**                        })**
}

```
Now I have 0 errors 0 warnings.
Thank you guru!

---

### Post by aljosa2 on 2013-12-22
Hi all, 
I'm going crazy trying to solve dsdt problems with my notebook Asus N750JV-T4069H (Intel® Core™ i7-4700HQ; Bit 64; Nvidia GeForce GT750M). 
Any help would be greatly appreciated :)
Please see my attached dsdt file

> gedit DSDT.dsl

* Disassembly of DSDT.dat, Sun Dec 22 09:23:04 2013
 *
 * Original Table Header:
 *     Signature        "DSDT"
 *     Length           0x00013CF4 (81140)
 *     Revision         0x02
 *     Checksum         0x1E
 *     OEM ID           "_ASUS_"
 *     OEM Table ID     "Notebook"
 *     OEM Revision     0x00000012 (18)
 *     Compiler ID      "INTL"
 *     Compiler Version 0x20120711 (538052369)
 */
DefinitionBlock ("DSDT.aml", "DSDT", 2, "_ASUS_", "Notebook", 0x00000012)
{
    /*
     * iASL Warning: There were 20 external control methods found during
     * disassembly, but additional ACPI tables to resolve these externals
     * were not specified. This resulting disassembler output file may not
     * compile because the disassembler did not know how many arguments
     * to assign to these methods. To specify the tables needed to resolve
     * external control method references, use the one of the following
     * example iASL invocations:
     *     iasl -e <ssdt1.aml,ssdt2.aml...> -d <dsdt.aml>
     *     iasl -e <dsdt.aml,ssdt2.aml...> -d <ssdt1.aml>
     */
    External (_SB_.PCI0.GFX0.AINT, MethodObj)    // Warning: Unresolved Method, guessing 1 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.GFX0.DWBL, MethodObj)    // Warning: Unresolved Method, guessing 0 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.GFX0.GLID, MethodObj)    // Warning: Unresolved Method, guessing 1 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.GFX0.GSCI, MethodObj)    // Warning: Unresolved Method, guessing 0 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.GFX0.IUEH, MethodObj)    // Warning: Unresolved Method, guessing 1 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.GFX0.OPTS, MethodObj)    // Warning: Unresolved Method, guessing 2 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.GFX0.OWAK, MethodObj)    // Warning: Unresolved Method, guessing 2 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.GFX0.SWHD, MethodObj)    // Warning: Unresolved Method, guessing 1 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.GFX0.UPBL, MethodObj)    // Warning: Unresolved Method, guessing 0 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.PAUD.PUAM, MethodObj)    // Warning: Unresolved Method, guessing 0 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.PEG0.HPME, MethodObj)    // Warning: Unresolved Method, guessing 0 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.PEG0.PEGP.DWBL, MethodObj)    // Warning: Unresolved Method, guessing 0 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.PEG0.PEGP.UPBL, MethodObj)    // Warning: Unresolved Method, guessing 0 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.PEG1.HPME, MethodObj)    // Warning: Unresolved Method, guessing 0 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.PEG2.HPME, MethodObj)    // Warning: Unresolved Method, guessing 0 arguments (may be incorrect, see warning above)
    External (_SB_.PCI0.XHC_.DUAM, MethodObj)    // Warning: Unresolved Method, guessing 0 arguments (may be incorrect, see warning above)
    External (_SB_.TPM_.PTS_, MethodObj)    // Warning: Unresolved Method, guessing 1 arguments (may be incorrect, see warning above)
    External (LIDS, MethodObj)    // Warning: Unresolved Method, guessing 0 arguments (may be incorrect, see warning above)
    External (PS0X, MethodObj)    // Warning: Unresolved Method, guessing 0 arguments (may be incorrect, see warning above)
    External (PS3X, MethodObj)    // Warning: Unresolved Method, guessing 0 arguments (may be incorrect, see warning above)

> line 364:
DISE,   8,

line 232:
EMAL,   16,

> iasl -e SSDT1.aml -d DSDT.aml

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20131115-64 [Dec  9 2013]
Copyright (c) 2000 - 2013 Intel Corporation

Loading Acpi table from file DSDT.aml
Acpi table [DSDT] successfully installed and loaded
Loading Acpi table from file SSDT1.aml
Acpi table [DSDT] successfully installed and loaded
Pass 1 parse of [DSDT]
Pass 2 parse of [DSDT]
Pass 1 parse of [DSDT]
ACPI Error: [SMBS] Namespace lookup failure, AE_ALREADY_EXISTS (20131115/dswload-364)
ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20131115/psobject-232)

> gedit DSDT.dsl

Could not parse ACPI tables, AE_ALREADY_EXISTS

---

### Post by Imamauri on 2014-01-14
Hi I'm having trouble with a Toshiba satellite L775-V13. The laptop overheats and shuts down, has no brightness control
and very little battery-life.
> ima@ima-SATELLITE-L775-13V:~$ iasl -tc /home/ima/dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100528 [Oct  1 2012]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

/home/ima/dsdt.dsl 22927:                                 Add (Local1, 0x01)
Warning  1106 -          Result is not used, operator has no effect ^ 

/home/ima/dsdt.dsl 24933:         Method (BBSF, 5, NotSerialized)
Warning  1088 -                              ^ Not all control paths return a value (BBSF)

/home/ima/dsdt.dsl 24945:         Method (HWID, 5, NotSerialized)
Warning  1088 -                              ^ Not all control paths return a value (HWID)

/home/ima/dsdt.dsl 24960:         Method (XPAP, 4, NotSerialized)
Warning  1088 -                              ^ Not all control paths return a value (XPAP)

ASL Input:  /home/ima/dsdt.dsl - 25685 lines, 795158 bytes, 12647 keywords
AML Output: /home/ima/dsdt.aml - 103127 bytes, 2411 named objects, 10236 executable opcodes

Compilation complete. 0 Errors, 4 Warnings, 0 Remarks, 4206 Optimizations



I have already messed with this bringing the number of warnings down (following the tutorial)
but I can't get around the remaining ones.

I hope someone can help !

---

