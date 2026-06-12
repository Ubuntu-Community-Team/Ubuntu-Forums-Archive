---
title: "Installation problem, done everything i can think of"
date: 2014-10-01
forum: Ubuntu/Debian BASED
---

### Post by zenon809 on 2014-10-01
I can't get the Elementary OS linux distro to install. I have been trying since 4pm and it is now midnight. 
I always get this error: 

(initramfs) unable to find a medium containing a live file system

I don't understand why. 
I checked the MD5's, I made a live USB MANY times using many utilities. All the same.

Tried changing USB ports and that also didn't work. This laptop only has 2 USB ports on the left hand side and NO cd drive.

the ONLY Linux distro that i was able to get working tonight was "LXLE" and i didn't want that...
The distro's i tried tonight:
-LXLE
-CentOS 7
-Elementary OS (32 and 64 bit) 

The utilities i used:
-Rufus
-iso2usb
-UNetBootin
-Universal USB Installer
-I even manually extracted the ISO and tried

This laptop originally had Windows 8.1 on it and i formatted it and put windows 7 on it. So this laptop now runs in Legacy mode and has since about a week after i got the laptop. I have tried booting Elementary OS in both Legacy BIOS and UEFI BIOS both returned the same error: (initramfs) unable to find a medium containing a live file system

I know the USB is a good USB for live boots because i used it to install Windows 7 many times previous. So it's not the USB and it's not the ISO.

The laptop is a Dell Inspiron 3531
-Intel Celeron N 2830 Processor
-4GB DDR3 Ram
-Intel HD Graphics 3000 series

I don't understand what's wrong, Can anyone help me out? I have the latest drivers as well.
I've tried just about everything i could think of, I even scraped Google trying to find answers and couldn't find any.

If someone can help me get this running i would be grateful. This looks like an amazing OS compared to any other Linux Distro and I'm able to use this distro in a VMWare virtual machine but not on my physical laptop... i don't get it since the virtual machine runs on the laptop as well.

---

### Post by deadflowr on 2014-10-01
Moved to Other Operating Systems and Projects

---

### Post by Stinger on 2014-10-01
did you try booting another PC with your live usb ?
Maybe you need to [Set secure boot to off and set boot list order to legacy]("https://wiki.archlinux.org/index.php/Dell_Inspiron_3531#Installation_in_MBR_mode"), but you seem to have done that already. Taken from [Arch Linux Dell Inspiron 3531]("https://wiki.archlinux.org/index.php/Dell_Inspiron_3531")
Are you using windows or Linux for creating the live usb ?
I make my live usb's using the GNOME-disks tool and before that I used the dd command.
It's actually the same procedure but GNOME-disks provides you with a nice gui.
I just right click my ( iso ) image and select 'restore image' then select the correct usb drive from the dropdown menu and within minutes I have a live usb, never let me down so far.  
Some guides:
[How to make a Live USB stick using GNOME Disks]("http://fedoramagazine.org/how-to-make-a-live-usb-stick-using-gnome-disks/"). The same goes for Ubuntu or any Ubuntu derivative  You have the disk tool there too, or it can be installed from software center.
[Creating bootable media (Korora)]("https://kororaproject.org/support/documentation/creating-bootable-media"). Scroll down to where it says "The dd command".
And here from Arch [dd for Windows]("https://wiki.archlinux.org/index.php/USB_flash_installation_media#dd_for_Windows"). Haven't tried that one ( been running Linux only since 2004 ) but it ought to work too.
[COLOR="#FF0000"]**Be absolutely sure that you are directing dd to the correct drive before executing! **[/COLOR] or you can end up erasing your hard drive instead :shock:

---

### Post by zenon809 on 2014-10-01
I'm using Windows to make my live USB.. In the first post i mentioned i have Windows... Just thought i would point that out.
I just used the same USB that i was using lastnight (That currently has Elementary OS on it) on my grandmothers laptop and it worked great the first run. Didn't even have to change anything.

But it won't work on my laptop... It just gives me that error that i posted in the first post.. But my laptop is newer than hers. Hers is a Toshiba Satellite C650D -026
But i can't use it on her laptop cause it's her laptop & I want to use my laptop.

---

### Post by christopher9 on 2014-10-01
Are there any USB settings in the BIOS to configure ?  Is your BIOS up-to-date ?

---

### Post by zenon809 on 2014-10-01
No, The only USB settings there are are to change the Boot Order.
The BIOS is up to date. Everything is latest.

But i had installed all the Windows 7 64bit drivers / BIOS Update from the Dell site after i installed Windows 7 so i'm gonna try running the Windows 8.1 BIOS update and see if that changes anything.

Update:
Nothing changed, BIOS is latest version.

---

### Post by Stinger on 2014-10-01
did you try dd for windows ?
There is a more comprehensive guide here:
[How to Use DD for Windows to Make a Bootable USB]("http://www.ehow.com/how_7487139_use-windows-make-bootable-usb.html")
But as said before please be careful :)
> The command-line software application "dd" is a "raw write" data manipulation program. It reads and writes data more directly than most other methods.

---

### Post by zenon809 on 2014-10-01
Honestly, I don't understand what DD will do to help me. The Live USB setup is not the problem, The USB works perfectly fine on other computers with Elementary OS booting to the install with no problems on other computers. 

It has nothing to do with the USB so unless DD has some use other than making Bootable USBs then please quit irritating me with DD. The Live USB is not the problem. Obviously, Cause if it was it wouldn't on other computers.

---

### Post by zenon809 on 2014-10-01
[ATTACH=CONFIG]256879[/ATTACH][ATTACH=CONFIG]256880[/ATTACH][ATTACH=CONFIG]256881[/ATTACH][ATTACH=CONFIG]256882[/ATTACH][ATTACH=CONFIG]256883[/ATTACH]

Pictures of my BIOS and the error that pops up upon trying to boot the USB

---

### Post by Stinger on 2014-10-01
> **zenon809 said:**
> Honestly, I don't understand what DD will do to help me. The Live USB setup is not the problem, The USB works perfectly fine on other computers with Elementary OS booting to the install with no problems on other computers. 

It has nothing to do with the USB so unless DD has some use other than making Bootable USBs then please quit irritating me with DD. The Live USB is not the problem. Obviously, Cause if it was it wouldn't on other computers.

I was trying to help you, but you seem to know better, I rest my case ;)

---

### Post by zenon809 on 2014-10-01
> **Stinger said:**
> I was trying to help you, but you seem to know better, I rest my case ;)

Well i still don't get what making a bootable USB with DD is gonna do when it works fine as it is just not on my own computer.....

Update
& I just attempted to use DD. I have no clue wtf im doing, All i was able to achieve with it was a 1GB useless file named D.

---

### Post by christopher9 on 2014-10-01
Any BIOS settings that mention SATA, IDE, or AHCI ?  Any other USB devices plugged in at the same time ?
Any way to burn the iso to DVD and install from that ?

---

### Post by zenon809 on 2014-10-01
> **christopher9 said:**
> Any BIOS settings that mention SATA, IDE, or AHCI ?  Any other USB devices plugged in at the same time ?
Any way to burn the iso to DVD and install from that ?

No. 
The only bios settings that mention SATA, IDE or AHCI there are 2, AHCI and i cant remember the other option.
By defaut the BIOS is AHCI.

As stated in the first post there is no DVD drive so that's not even an option.
Otherwise i would of just burned a disc.

And no, No other USB devices are plugged in at the same time

---

### Post by zenon809 on 2014-10-02
Can somebody help me out here?

---

### Post by oldfred on 2014-10-02
If system was UEFI that has gpt partitioning.
And if you did a typical Windows 7 install with BIOS and MBR, it converted drive from gpt to MBR partitioning. (You can install Windows 7 in UEFI mode but have to copy to flash drive and do some updates first).

Post this from a live installer.

sudo fdisk -lu

If that mentions gpt then you have the error that Windows does not correctly convert from gpt to MBR. Then Linux tools see both MBR and gpt and fail.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by zenon809 on 2014-10-03
> **oldfred said:**
> If system was UEFI that has gpt partitioning.
And if you did a typical Windows 7 install with BIOS and MBR, it converted drive from gpt to MBR partitioning. (You can install Windows 7 in UEFI mode but have to copy to flash drive and do some updates first).

Post this from a live installer.

sudo fdisk -lu

If that mentions gpt then you have the error that Windows does not correctly convert from gpt to MBR. Then Linux tools see both MBR and gpt and fail.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Yes it was a Windows 8 UEFI installation.
When i put windows 7 onto it i changed the BIOS to Legacy and formatted all the partitions then installed Windows 7.

I'll post the results when i can run a distro.. Gonna have to make a bootable LXLE USB now so i can run the query. Since LXLE is the only one that works....

---

### Post by zenon809 on 2014-10-03
[ATTACH=CONFIG]256915[/ATTACH]

The output of sudo fdisk -lu

---

### Post by oldfred on 2014-10-03
Better just to copy text from terminal to reply. If longer use Code tags which are easy to add with Advanced editor and # icon.

It seems to mention gpt at top? If so then you need to run fixparts to clear backup partition table.

---

### Post by zenon809 on 2014-10-03
[ATTACH=CONFIG]256918[/ATTACH]

Ok there's the full output.
I'm not copying and pasting because i don't have LXLE setup for anything. It's on a USB key.

The only reason it's even on my USB Key is so i can run the queries you may need me to run..

---

### Post by oldfred on 2014-10-03
Have not use LXLE as live installer, but you should be able to install and run fixparts. Link above to download it and it has instructions. You just run it and it should reset partitions, if you confirm they are correct with the w command.

---

### Post by zenon809 on 2014-10-03
> **oldfred said:**
> Have not use LXLE as live installer, but you should be able to install and run fixparts. Link above to download it and it has instructions. You just run it and it should reset partitions, if you confirm they are correct with the w command.

w command? I don't know what that command is nor do i know what it does...
First time i've ever heard of this command.

Update:
I will need exact commands to run IN ORDER please, I don't want to screw anything up.
I have installed FixParts.

---

### Post by oldfred on 2014-10-03
I have just loaded fixparts once. Never have had to use it.
The link has the detailed instructions.

First you backup current partition table if it lets you:

Change example sdc to your drive:
        sudo sfdisk -d /dev/sdc > parts.txt
    Then you load it using your drive, again change from sdc if not corrrect:
 sudo fixparts /dev/sdc
say yes
Then do  a p to review partitions, should be your standard MBR partitions.
If not correct use q to quit or if correct use w to write updates.

Please read thru all the details in the Tutorial.

---

### Post by zenon809 on 2014-10-03
> **oldfred said:**
> I have just loaded fixparts once. Never have had to use it.
The link has the detailed instructions.

First you backup current partition table if it lets you:

Change example sdc to your drive:
        sudo sfdisk -d /dev/sdc > parts.txt
    Then you load it using your drive, again change from sdc if not corrrect:
 sudo fixparts /dev/sdc
say yes
Then do  a p to review partitions, should be your standard MBR partitions.
If not correct use q to quit or if correct use w to write updates.

Please read thru all the details in the Tutorial.

uhmmm yup... makes me really wanna use this... I can use Windows and Linux with no problem but i don't mess with important stuff that can screw over my computer or my windows installation and since i need my windows installation for both school and my home usage. I don't really wanna play with that.

On top of that, Even you don't know how to use it and that documentation is not really straight forward to me nor do i wanna read through a wall of text. 
I don't really understand how to properly use a utility that can screw everything up and i don't want to play with something that can really mess things up with 1 wrong letter when the person telling me to do this doesn't even really know how to use it.

And for me, That's a big deal. Normally I'll do something if someone can provide me 100% proper accurate instructions on how to do something where i feel it'll be ok, but you have no idea how to use it is what your basically saying and therefore you haven't tried it, Since you know, you said you didn't use it ever. 

I'm not comfortable playing with such a dangerous utility without instructions on every line to run and such to fix this... Cause i may learn fast, but my experience with dangerous utilities and no proper step by step instructions by someone whose actually used the utility didn't end well.... any of the times.

---

### Post by oldfred on 2014-10-03
You converted a UEFI install to BIOS with proprietary software that does the conversion incorrectly and do not want to run a simple fix?  While I have not run it, many users have run it and say it works to solve exactly your issue.

If Windows is that vital you absolutely must create backups and a Windows repair CD or flash drive.

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by zenon809 on 2014-10-04
> **oldfred said:**
> You converted a UEFI install to BIOS with proprietary software that does the conversion incorrectly and do not want to run a simple fix?  While I have not run it, many users have run it and say it works to solve exactly your issue.

If Windows is that vital you absolutely must create backups and a Windows repair CD or flash drive.

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I didn't mean to sound like an ass if i did. I was in a rough mood earlier. 
Uhmm Ok but i don't feel comfortable trying to figure out exactly what commands to run or what does what.. For all i know i could accidentally run a command that i think will do one thing and it'll do another and be catastrophic.
Hence the reason i like to have commands that i can run exactly where i know they aren't just guesses.. I'm very cautious to such matters.

I don't have any device large enough to backup to. My laptop has a 500GB hard drive and out of that i have a bit less than half that free.
But, I guess if it has worked for some people then im sure it will work for me, Im just not comfortable trying to guess the commands and hope they're right..  I personally prefer to have exact commands to run. I am still learning Linux and don't really understand most of it, Especially things that have to do with the labeling scheme of sda

Do you have commands for this program? I would feel much better about this if i had all the commands in order to run in order to be successful. 

Another reason i prefer Linux for general use is simply because this Dell on any Windows installation uses max resources and that's just absurd since it shouldn't be, But it doesnt have a CPU fan so that may be a good reason to why but i found windows to always be a resource hog. Just not this bad. I found LXLE on Live USB didn't even use 10% of my resources ( 1% RAM 99% of the time, 3% hard drive, and just overall very non resource intensive and fast).

---

### Post by oldfred on 2014-10-04
The exact commands are in post #22. The only question is what drive is it sdb, sdc or something else.
Just change to correct drive. Drives can change device labels. Best to check with fdisk.
sudo fdisk -lu

Then run the commands. If at all concerned you use q to quit and nothing will change or w to write fix which should not change any partitions, just remove the hidden data that Windows should have removed.

Best to buy another drive, or at least a larger flash drive and copy most important data to backups. With Ubuntu I know I can easily reinstall system and restore my settings from /home and backup my data. But Windows integrates everything that you just about have to do a full image backup. And hard drives, systems and user errors (even just in Windows) may mean you need that backup.

---

### Post by zenon809 on 2014-10-04
> **oldfred said:**
> The exact commands are in post #22. The only question is what drive is it sdb, sdc or something else.
Just change to correct drive. Drives can change device labels. Best to check with fdisk.
sudo fdisk -lu

Then run the commands. If at all concerned you use q to quit and nothing will change or w to write fix which should not change any partitions, just remove the hidden data that Windows should have removed.

Best to buy another drive, or at least a larger flash drive and copy most important data to backups. With Ubuntu I know I can easily reinstall system and restore my settings from /home and backup my data. But Windows integrates everything that you just about have to do a full image backup. And hard drives, systems and user errors (even just in Windows) may mean you need that backup.

It didn't work.
sudo fixparts /dev/sda2
then it gave some stuff about oversized data (Didn't take a picture, Thought of that AFTER it was booting windows) so i wrote the changes
booted into windows
updated the windows time to be correct (Cause somehow it messed with my time)
tried to boot Elementary OS and got the same error i posted in post #1

---

### Post by oldfred on 2014-10-04
the command is not for a partition like sda2, but a drive like sda. Please review examples, both the one I posted and the linked site.

---

### Post by buzzingrobot on 2014-10-04
> **zenon809 said:**
> 
updated the windows time to be correct (Cause somehow it messed with my time)


Windows uses local time and Linux use UTC time.

---

### Post by zenon809 on 2014-10-04
> **oldfred said:**
> the command is not for a partition like sda2, but a drive like sda. Please review examples, both the one I posted and the linked site.

I'm confused, Like i said, I don't have the knowledge to screw around with commands like this. Which was the whole point of asking for the commands to run.
I read the docs and i thought i needed to run /dev/sda2 since sda2 is my hard drive. 

but obviously i didn't see that right, I don't see you really explaining what the difference is nor have you given me the commands to use to run this properly. 
Obviously im getting frustrated and pissed off, you keep telling me im not doing it right and things like it but yet still don't provide me any commands to run to get to fixing the darn thing. You never said there was a difference between sda / sdc or whatever it is. 

I don't understand wtf that documentation is trying to say. It's only confusing me & i don't feel like nor do i want to read a damn wall of text.

just give me the damn commands so i can get this fixed and get off the damn forums. Sick of trying to run different commands whatever and getting nowhere. It really isn't that hard to tell me what utility to use and the commands to run with it.


> **buzzingrobot said:**
> Windows uses local time and Linux use UTC time.

Huh, I wasn't worried about it anyway just made me somewhat wonder why it changed but it's no biggy.

---

### Post by oldfred on 2014-10-05
Same as post #22.

Change example sdc to your drive:
        sudo sfdisk -d /dev/sdc > parts.txt
    Then you load it using your drive, again change from sdc if not corrrect:
 sudo fixparts /dev/sdc
say yes
Then do  a p to review partitions, should be your standard MBR partitions.
If not correct use q to quit or if correct use w to write updates.

Please read thru all the details in the Tutorial.

Note that Windows uses "drives" like c: drive and d: drive. But the d: drive could be a second partition on the first physical drive or a second drive.
To avoid confusion Linux labels drives as sda, sdb, sdc etc for each physical drive. 
Then for any partitions on a drive each partition has a number like sda1 is first partition on physical drive sda. 
Some commands require drives and others require partitions. Example above has no numbers and it is a repair of a drive not a repair of a partition.

---

### Post by zenon809 on 2014-10-05
> **oldfred said:**
> Same as post #22.

Change example sdc to your drive:
        sudo sfdisk -d /dev/sdc > parts.txt
    Then you load it using your drive, again change from sdc if not corrrect:
 sudo fixparts /dev/sdc
say yes
Then do  a p to review partitions, should be your standard MBR partitions.
If not correct use q to quit or if correct use w to write updates.

Please read thru all the details in the Tutorial.

Note that Windows uses "drives" like c: drive and d: drive. But the d: drive could be a second partition on the first physical drive or a second drive.
To avoid confusion Linux labels drives as sda, sdb, sdc etc for each physical drive. 
Then for any partitions on a drive each partition has a number like sda1 is first partition on physical drive sda. 
Some commands require drives and others require partitions. Example above has no numbers and it is a repair of a drive not a repair of a partition.

Ok, So what im getting out of this is sda is supposed to be my hard drive then since sda2 is my hard drive and sda1 is my USB ?
Cause according to Linux my USB is sda1 and my hard drive is sda2....
because when i booted with Linux live USB that drive was labeled sda1 and it had an asterisk under boot where sda2 was the size of my hard drive **without **an asterisk under boot.

---

### Post by oldfred on 2014-10-05
Not possible that two different drives would be sda1 & sda2. In Windows that could be c: & d:

Your screen shot from before showed sda as a 500GB drive with sda1 & sda2 partitions both formatted NTFS. Your sda1 was the Windows boot partition and sda2 was the main install. And you showed a sdb drive which was about 8GB which would be normally your live installer. It only has one FAT32 formatted partition.

Windows typically does not show the boot partition so you main install in sda2 is the size you see as your c: "drive".

You want to run the fixparts on sda, or your entire 500GB drive.

---

### Post by zenon809 on 2014-10-05
> **oldfred said:**
> Not possible that two different drives would be sda1 & sda2. In Windows that could be c: & d:

Your screen shot from before showed sda as a 500GB drive with sda1 & sda2 partitions both formatted NTFS. Your sda1 was the Windows boot partition and sda2 was the main install. And you showed a sdb drive which was about 8GB which would be normally your live installer. It only has one FAT32 formatted partition.

Windows typically does not show the boot partition so you main install in sda2 is the size you see as your c: "drive".

You want to run the fixparts on sda, or your entire 500GB drive.

Oh ok
I think i'm just gonna wait a couple months.. 

I'm supposed to be getting a different new laptop for christmas (Cause this one is crap.. damn dell) and see if that one works, and if i don't get one for Christmas fine but then ill just wait until i finish school in January. I'm starting to think what if's about running this utility and i don't want to lose all my data with no backup space anywhere so this might just be a wiser choice to wait a few months.

---

### Post by oldfred on 2014-10-05
From what I have seen Dell's are better at working with dual booting. Many others particularly HP & Sony require significant work arounds to get them to work. But only one or two models from several years ago would not boot Ubuntu at all. But like you Windows has made it so complicated that some users do give up.

But you should invest you money in backup solutions before thinking of a new system if your data is at all valuable. We regularly get users with failing hard drives and have lost important data. In some cases we have gotten data back, but at the cost of many days of work and they still had to buy a back up drive to restore data to.

---

### Post by buzzingrobot on 2014-10-05
> **zenon809 said:**
> Oh ok
I think i'm just gonna wait a couple months.. 

I'm supposed to be getting a different new laptop for christmas (Cause this one is crap.. damn dell) and see if that one works, and if i don't get one for Christmas fine but then ill just wait until i finish school in January. I'm starting to think what if's about running this utility and i don't want to lose all my data with no backup space anywhere so this might just be a wiser choice to wait a few months.

Well, backing up is certainly a sensible precaution before adjusting partitions in any OS.

For reference, just in case, drives in Linux are identified as "/dev/sda", "/dev/sdb", etc.  Partitions on drives are identified as "/dev/sda1", /dev/sdb1", etc. Different things.

So, the first partition on the first, or only, drive would be "/dev/sda1".  Commands that work on drives will fail when pointed at partitions, and vice versa.

On Windows, a drive designation -- C:, for example -- can be mapped to one partition that uses an entire physical drive, or to a partition on a physical drive.  E.g., a single physical drive could contain two partitions, which Windows could map so that the user would see a C: drive and a D: drive.

The two different approaches takes some getting used to, but the Unix/Linux approach predates Windows by some time.  Windows picked up its approach from the days of DOS.

---

### Post by zenon809 on 2014-10-05
> **oldfred said:**
> From what I have seen Dell's are better at working with dual booting. Many others particularly HP & Sony require significant work arounds to get them to work. But only one or two models from several years ago would not boot Ubuntu at all. But like you Windows has made it so complicated that some users do give up.


this is a brand new laptop from Dell, One of there new inspiron 15 models.
I had an Acer laptop last, i dual booted that with ubuntu no problem but yeah...

I'll come back to it eventually lol

---

