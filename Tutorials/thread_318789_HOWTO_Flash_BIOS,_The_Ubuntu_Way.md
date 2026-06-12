---
title: "HOWTO: Flash BIOS, The Ubuntu Way"
date: 2006-12-11
forum: Tutorials
---

### Post by ciscosurfer on 2006-12-11
[SIZE=3]**HOW TO FLASH YOUR BIOS**[/SIZE]
[SIZE=2][COLOR=Sienna][B][COLOR=Black]
WARNING
[/COLOR][/B][/COLOR][/SIZE]BIOS flashing is destructive. If you don't understand what this means, start reading [here]("http://en.wikipedia.org/wiki/BIOS") and [here]("http://www.pcstats.com/articleview.cfm?articleID=1605"). Read these documents and all related documents very carefully.
[SIZE=2][COLOR=Sienna][B]
[COLOR=Black]RELEASE COMPATIBILITY (Ubuntu x86/i386) [/COLOR][/B][/COLOR][/SIZE]
[SIZE=1]All versions of Ubuntu have been tested using the methods listed below (4.10 - 12.04).[/SIZE][SIZE=1]
[/SIZE] 
[COLOR=Navy][B][SIZE=2][COLOR=Black]UPDATE[/COLOR][/SIZE]
[/B][/COLOR]Many vendors now include [COLOR=Red]***native Linux utilities***[/COLOR] to assist in a BIOS flash (or [replacement]("http://www.coreboot.org/Welcome_to_coreboot")). If you fit into this category *then it is recommended to use the method  provided by them.* Another example: Dell has the [biosdisk]("http://linux.dell.com/") project. You can also try your luck with the [flashrom]("http://www.flashrom.org/Flashrom") project (more on flashrom below). If you know what you are doing, are feeling daring, or just want to know a little more about this topic, then continue reading.
[SIZE=2][COLOR=Black][B]
BACKGROUND[/B][/COLOR][/SIZE]
Flashing a [BIOS]("http://en.wikipedia.org/wiki/BIOS") typically serves the following functions: to fix specific bugs, to support newer hardware, or to fix a damaged BIOS. Using Ubuntu Linux as our host OS, we will create a bootable floppy disk or CD using FreeDOS as our OS of choice. On this disk we will place a new BIOS image and any related files used for flashing. Once the disk has been created, reboot the system and allow your newly created disk to load automatically and begin the flashing process. See your particular BIOS vendor's web site for these files and for more information on the commands you will to need to use to begin the flashing process. In other words, [I]read what your BIOS vendor has to say about flashing. READ the README file.
[/I] [SIZE=2][COLOR=Black][B]
BIOS INFORMATION[/B][/COLOR][/SIZE]
Learn more about your BIOS and its features (e.g., make, vendor, release date).
```
sudo biosdecode
sudo hwinfo --bios | less
sudo dmidecode --type bios
sudo lshw
gksudo lshw-gtk
```[SIZE=2][COLOR=Black]**[COLOR=Red]TIPS & WARNINGS[/COLOR] (YOU SHOULD READ THESE)**[/COLOR][/SIZE][B]
[COLOR=Black][I]Note
[/I][/COLOR][/B]Flashing your BIOS is a potentially dangerous activity that can render your motherboard (and computer, for that matter) inoperable. Proceed with caution and fully understand what you are doing before attempting the commands below! The only way to reverse the commands below is to make a copy of your current BIOS configuration and re-flash or by reinstalling the original BIOS to your motherboard.
[I][COLOR=Black]
[B]CMOS Jumpers
[/B][/COLOR][/I]Some motherboards have CMOS Jumpers that need to be cleared to perform a successful BIOS flash. More on this topic [here]("http://www.dewassoc.com/support/bios/bios_password.htm") & [here]("http://www.google.com/#&q=cmos+jumper").

*[COLOR=Black]**ACPI-Related Issues**[/COLOR]*
Sometimes these issues can be fixed by updating your BIOS. If after flashing your BIOS you still encounter power/fan/thermal problems, [this thread]("http://ubuntuforums.org/showthread.php?t=1036051") will describe how to modify your [DSDT]("http://acpi.sourceforge.net/dsdt/index.php") file in an attempt at fixing common ACPI-related issues. More on ACPI [here]("http://www.acpi.info/") and [here]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface").

[COLOR=Black][I][B]GRUB 2
[/B][/I][/COLOR]The third method uses the GRUB bootloader. It's meant to be used with original GRUB ***and not with GRUB 2***.
If you need or want to use [GRUB 2]("http://www.gnu.org/software/grub/grub-2.en.html"), check out [The GRUB 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275") or [the GRUB 2 manual]("http://www.gnu.org/software/grub/manual/") for ideas.  You can also alter GRUB 2 using Daniel Richter's "Grub Customizer" -- read more about it [here]("https://launchpad.net/grub-customizer"), [here]("http://ubuntuforums.org/showthread.php?p=10340183"), and [here]("http://www.howtogeek.com/howto/43471/how-to-configure-the-linux-grub2-boot-menu-the-easy-way/").

[I][COLOR=Black][B]Flashrom
[/B][/COLOR][/I][This method]("http://ubuntuforums.org/showpost.php?p=6816011&postcount=70") utilizes an app called **flashrom** to update your BIOS without having to reboot your system. It is a utility for identifying, reading, writing, verifying, and erasing  flash chips ([http://www.flashrom.org/Flashrom](http://www.flashrom.org/Flashrom)). It's often used to flash BIOS/EFI/coreboot/firmware images. Read the compatibility chart to see whether your BIOS is supported or if proposed workarounds have been suggested. Check the following links for more information. Pádraig Brady offers up [this page]("http://www.pixelbeat.org/docs/bios/") as well. More info can be found at the main project site [here]("http://www.flashrom.org/Flashrom"), on wikipedia [here]("http://en.wikipedia.org/wiki/Flashrom"), on apcmag.com [here]("http://apcmag.com/flashrom-fast-approaching-a-version-10.htm"), and on desktoplinux.com [here]("http://www.desktoplinux.com/news/NS6158241352.html").
[I][COLOR=Black]
[/COLOR][/I] [B][I][COLOR=Black]Unetbootin & USB Flash
[/COLOR][/I][/B]Ideas on using unetbootin and/or USB flash drives, thumb drives, sticks, etc., can be found [here]("http://unetbootin.sourceforge.net/") and [here]("http://0sumgain.blogspot.com/2009/11/updating-motherboard-bios-from-ubuntu.html"). Some comments [here]("http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html") discuss making bootable USB flash drives as well.

[B]*Size Contraints*
[/B]In cases where the new BIOS image and related files are larger than 1.44MB, you can go [here]("http://www.fdos.org/bootdisks/") or [here]("http://sites.google.com/site/rugxulo/") to learn about creating or using customized boot disks of larger sizes to help in flashing your BIOS. As an alternative, you can try the third method listed below that uses GRUB to update your BIOS. See above for ideas on modifying config files if using GRUB 2 as your boot loader.

[B]*Still Not Sure?*
[/B]If you don't know what you are doing or feel unsafe at this point, it is ***highly recommended*** to ask for help or consult a professional.


[SIZE=4][COLOR=Navy][B][COLOR=DarkRed] [COLOR=Black]METHODS
Carefully read through all methods.
Pick a method that best suits your situation.
Understand what you are doing before you begin.
Read the [/COLOR][/COLOR][/B][/COLOR][/SIZE][SIZE=2][COLOR=Red]**TIPS & WARNINGS**[/COLOR][/SIZE] [SIZE=4][COLOR=Navy]**[COLOR=DarkRed][COLOR=Black]section above for additional insight.[/COLOR][/COLOR]**[/COLOR][/SIZE]

[SIZE=2][COLOR=Black]**YOU WILL NEED THE FOLLOWING:**[/COLOR][/SIZE]
1a) [FreeDOS]("http://www.fdos.org/"),  specifically, this image:  [http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz](http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz) 
1b) Alternate download location: [http://www.mediafire.com/file/26md8hs5aablqke/FDOEM.144.gz](http://www.mediafire.com/file/26md8hs5aablqke/FDOEM.144.gz)
2) New BIOS image + flashing tool to be found at the web site of your  motherboard/BIOS/OEM vendor.

[SIZE=2][COLOR=Black][B] 
M1: FLOPPY[/B][/COLOR][/SIZE]
[SIZE=1]*Unpack FreeDOS image &#8594; copy image to floppy disk *[/SIZE][SIZE=1]*&#8594; create temp floppy dir *[/SIZE][SIZE=1]*&#8594; mount floppy *[/SIZE][SIZE=1]*&#8594; *[/SIZE][SIZE=1]*copy flashing tool *[/SIZE][SIZE=1]*and new BIOS image to /tmp/floppy *[/SIZE][SIZE=1]*(see footnotes below) &#8594; *[/SIZE][SIZE=1][I]reboot following vendor instructions

Note: "NewBiosFiles" listed below is pseudocode for the extracted location of the new BIOS image + related files that you just downloaded[/I][/SIZE]```
wget http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz
gunzip FDOEM.144.gz
dd if=FDOEM.144 of=/dev/fd0
mkdir /tmp/floppy
sudo mount /dev/fd0 /tmp/floppy
sudo cp ~/NewBiosFiles/* /tmp/floppy
```Once the command has finished executing, mount the floppy and copy the new BIOS image + flashing tool onto it. That's all there is to it. Reboot, flash BIOS with commands provided by the BIOS vendor. Check the **README **file for exact syntax.[COLOR=RoyalBlue][B]
[SIZE=2][COLOR=Sienna][COLOR=Blue]END OF METHOD[/COLOR]
[/COLOR][/SIZE][/B][/COLOR] [B]

[SIZE=2][COLOR=Black] M2: CD[/COLOR][/SIZE]
[/B][SIZE=1]*Unpack FreeDOS image &#8594; create temp dir &#8594; mount FreeDOS image to /tmp/cdr &#8594; copy flashing tool*[/SIZE][SIZE=1]* and new BIOS image to /tmp/cdr *[/SIZE][SIZE=1]*(see footnotes below) &#8594; unmount image &#8594; install mkisofs &#8594; create ISO &#8594; burn ISO to disc *[/SIZE][SIZE=1][I]&#8594; reboot following vendor instructions

[/I][/SIZE][SIZE=1]*Note: "NewBiosFiles" listed below is pseudocode for the extracted location of the new BIOS image + related files that you just downloaded*[/SIZE]```
wget http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz
gunzip FDOEM.144.gz
mkdir /tmp/cdr
sudo mount -t vfat -o loop FDOEM.144 /tmp/cdr
sudo cp ~/NewBiosFiles/* /tmp/cdr
sudo umount /tmp/cdr
sudo apt-get install mkisofs
mkisofs -o newBIOS.iso -b FDOEM.144 FDOEM.144
cdrecord -v newBIOS.iso

```[note: in later releases, /usr/bin/mkisofs symlinks to /usr/bin/genisoimage]
[note: in later releases, /usr/bin/cdrecord symlinks to /usr/bin/wodim]

Reboot from the CD and flash your BIOS with the commands provided by the BIOS vendor. Check the **README** file for exact syntax.[COLOR=Navy][SIZE=2][B]
[COLOR=Blue]END OF METHOD[/COLOR]
[/B][/SIZE][/COLOR] 

[SIZE=2][COLOR=Black]**M3: GRUB (GRUB 2 users, read GRUB 2 links under [COLOR=Red]TIPS & WARNINGS[/COLOR] above)**[/COLOR][/SIZE]
[SIZE=1]*Download FreeDOS image and unpack &#8594; *[/SIZE][SIZE=1]* create temp dir *[/SIZE][SIZE=1]*&#8594; mount image to temp dir *[/SIZE][SIZE=1]*&#8594; *[/SIZE][SIZE=1]*extract flashing utility and new BIOS image to temp dir*[/SIZE][SIZE=1]* &#8594; unmount image, remove temp dir *[/SIZE][SIZE=1]*&#8594; move image to new file to be used by GRUB *[/SIZE][SIZE=1]*&#8594; install syslinux to provide memdisk for booting *[/SIZE][SIZE=1]*&#8594; copy memdisk to /boot dir *[/SIZE][SIZE=1]*&#8594; *[/SIZE][SIZE=1]*reboot choosing biosupdate.img option from GRUB menu *[/SIZE]
[COLOR=maroon][COLOR=Black]```
wget http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz
gunzip FDOEM.144.gz
mkdir /tmp/floppy
sudo mount -t vfat -o loop,quiet,umask=000 FDOEM.144 /tmp/floppy
unzip newBIOS.zip -d /tmp/floppy
sudo umount /tmp/floppy
rmdir /tmp/floppy
sudo mv FDOEM.144 /boot/biosupdate.img
sudo apt-get install syslinux
sudo cp /usr/lib/syslinux/memdisk /boot/

```[/COLOR][/COLOR]```
[COLOR=maroon][COLOR=Black]sudo vim /boot/grub/menu.lst[/COLOR][/COLOR]
```[COLOR=maroon][COLOR=Black]Now add the following to your GRUB menu```

title       BIOS upgrade
kernel      /boot/memdisk
initrd      /boot/biosupdate.img
```[/COLOR][/COLOR][COLOR=Black][COLOR=Blue]**[SIZE=2]END OF METHOD[/SIZE]**[/COLOR]
[/COLOR] [COLOR=Navy][B][COLOR=DarkOliveGreen] [COLOR=DarkOliveGreen]
[SIZE=2][COLOR=Black]INSPIRATION[/COLOR][/SIZE][/COLOR][/COLOR][/B][/COLOR]
[HOWTO:Flash Your Bios...]("http://ubuntuforums.org/showthread.php?t=190615&highlight=flash+bios")
[No DOS/Windows, No floppy...]("http://linux.inet.hr/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html")

[SIZE=2][COLOR=Black]** FOOTNOTES**[/COLOR][/SIZE]
*[COLOR=maroon][COLOR=Black]You've likely downloaded an executable file (an .exe file) containing your new BIOS image and flashing utility. [/COLOR][/COLOR][COLOR=Black]There may be other files that you wish to copy over, such as an AUTOEXEC.BAT file to automate the process. [/COLOR][COLOR=maroon][COLOR=Black]In addition, you'll probably find a README file of some sort that will describe the appropriate syntax to use when flashing. To get at these files, use [/COLOR][COLOR=Black]**unzip **[/COLOR][COLOR=Black]to de-archive the executable file. Install [/COLOR][/COLOR]*[COLOR=maroon]*[COLOR=Black]**unzip** via your favorite package manager.[/COLOR]*[I][COLOR=Black]
[/COLOR][/I][/COLOR]

---

### Post by John.Michael.Kane on 2006-12-14
test

---

### Post by John.Michael.Kane on 2006-12-14
test

---

### Post by John.Michael.Kane on 2006-12-14
Test

---

### Post by bodhi.zazen on 2006-12-17
Nice How-to

This thread has been added to the UDSF wiki.

[Flash_Bios](http://doc.gwos.org/index.php/Flash_Bios)

[color=blue]Thanks Crane[/color]

---

### Post by dannyboy79 on 2006-12-19
i used this to flash my foxconn motherboard and everytime I would get to the part in the award bios flasher it would say, press y to program or n to cancel and I would hit y and it would just sit there????? i di itover and over, made new disks, to no avail, then I thought I recaled reading along time ago about some motherboards having a jumper that is used to clear the cmos ( i believe this is what holds the bios settings) and that if this jumper is in place the bios is unwritable. well, i removed the jumper temporarily and sure enough, my new bios was flashed on the motherboard and I am now not getting the apic errors in my syslog anymore about the cpu error 40 something or other. anyway. 

**I think you should FYI people about a possibler jumper preventing them from writing to the cmos or bios or whatver the term is. hope this helps others.**

---

### Post by ciscosurfer on 2006-12-19
> **dannyboy79 said:**
> i used this to flash my foxconn motherboard and everytime I would get to the part in the award bios flasher it would say, press y to program or n to cancel and I would hit y and it would just sit there????? i di itover and over, made new disks, to no avail, then I thought I recaled reading along time ago about some motherboards having a jumper that is used to clear the cmos ( i believe this is what holds the bios settings) and that if this jumper is in place the bios is unwritable. well, i removed the jumper temporarily and sure enough, my new bios was flashed on the motherboard and I am now not getting the apic errors in my syslog anymore about the cpu error 40 something or other. anyway. 

**I think you should FYI people about a possibler jumper preventing them from writing to the cmos or bios or whatver the term is. hope this helps others.**Thanks for the tip.  I've added this information into my HOWTO as an "EDIT". :D

Glad this HOWTO was helpful for you. :D

---

### Post by gaxxter on 2007-05-05
Hi, I can't be bothered with the hassle to update manually so get a biosflash company to do my work 4 me, got a new chip with latest bios and use the old one as a back up for future failure!!! hope not :)

---

### Post by ciscosurfer on 2007-05-05
> **gaxxter said:**
> Hi, I can't be bothered with the hassle to update manually so get a biosflash company to do my work 4 me, got a new chip with latest bios and use the old one as a back up for future failure!!! hope not :)That's definitely one way to do it! :-)

---

### Post by Rhubarb on 2007-05-08
This is a great + very important thread.
Thanks :)

---

### Post by quail-linux on 2007-05-08
Hi ciscosurfer

Great Howto, i found it very helpful :)

---

### Post by loyeyoung on 2007-05-09
I'm glad you got it to work for you, but it's not a good solution. 
[LIST=1]
[*]Relies on software not tested in Debian or Ubuntu
[*]Not fault tolerant -- too easy to mess up your system.
[*]There is a much better way.
[/LIST]

Here's the RIGHT way to do it: 

(I am assuming you have obtained the BIOS update files from a reliable source, that they are unzipped and stored in a separate directory in your home directory, and no other files are in that directory.)

1.  Use your favorite package manager (Synaptic, Adept, aptitude, etc.) to install the dosemu package and the packages it recommends and suggests. 

2.  Open Konsole.

3.  At the command prompt, type:
```
user@localhost:~$ xdosemu
```
4.  Read the warnings. When you understand them, type "yes" (no quotes) where prompted.

5.  A DOS window will open. 

6.  Insert a floppy in your floppy drive. Note the capacity of the disk you are using. Most are 1.44MB, but there are others floating around. 

7.  At the C:\ prompt, type:
```
C:\ format a: /S /F:[number of KILOBYTES of your disk] /V:[SOMENAME]
```
and press Enter on your keyboard. You need to replace "[number of KILOBYTES of your disk]" with the size of your disk, in kB. For instance, if your floppy is a 1.44MB, you would use 1440. For 720kB, use 720, etc. Replace "[SOMENAME]" with a name that helps you remember what the disk is. In my case, I typed:
```
C:\ format a: /S /F:1440 /V:BIOS-UPDATE
```

8.  To find your files:
```
C:\ d:
D:\ ls
```
This will give you a directory list of your home directory. Dosemu maps your home directory to the DOS D: drive. You will note that Dosemu mangles the filenames in order to make them 8.3 filename compliant. Not to worry, it hasn't done anything to them; you'll just have to decide based on the first few characters of the actual file name. The commands "cd" (change directory") and "ls" (list) are your friends. 

9.  Copy your BIOS files from their directory (we'll call it "STOREDIR" as an example) to the floppy:
```
D:\ copy BIOSDIR\* a:\
XYZ123.BIN => a:\XYZ123.BIN
AUTOEXEC.BIN => a:\AUTOEXEC.BIN
BFLASH.EXE => a:\BFLASH.EXE
OTHERFILE.COM => OTHERFILE.COM
D:\
```

10. Exit Dosemu:
```
D:\ exitemu
```

11  Now, back at the Konsole terminal, unmount the floppy and exit:
```
user@localhost:~$ umount /dev/fd0
user@localhost:~$ exit
```

12. Follow the instructions of the BIOS vendor.

Happy Trails,

Loye Young
[http://www.iycc.net](http://www.iycc.net)
Laredo, Texas

---

### Post by quail-linux on 2007-05-09
> **loyeyoung said:**
> I'm glad you got it to work for you, but it's not a good solution. 
[LIST=1]
[*]Relies on software not tested in Debian or Ubuntu
[*]Not fault tolerant -- too easy to mess up your system.
[*]There is a much better way.
[/LIST]

Here's the RIGHT way to do it: 

(I am assuming you have obtained the BIOS update files from a reliable source, that they are unzipped and stored in a separate directory in your home directory, and no other files are in that directory.)

1.  Use your favorite package manager (Synaptic, Adept, aptitude, etc.) to install the dosemu package and the packages it recommends and suggests. 

2.  Open Konsole.

3.  At the command prompt, type:
```
user@localhost:~$ xdosemu
```
4.  Read the warnings. When you understand them, type "yes" (no quotes) where prompted.

5.  A DOS window will open. 

6.  Insert a floppy in your floppy drive. Note the capacity of the disk you are using. Most are 1.44MB, but there are others floating around. 

7.  At the C:\ prompt, type:
```
C:\ format a: /S /F:[number of KILOBYTES of your disk] /V:[SOMENAME]
```
and press Enter on your keyboard. You need to replace "[number of KILOBYTES of your disk]" with the size of your disk, in kB. For instance, if your floppy is a 1.44MB, you would use 1440. For 720kB, use 720, etc. Replace "[SOMENAME]" with a name that helps you remember what the disk is. In my case, I typed:
```
C:\ format a: /S /F:1440 /V:BIOS-UPDATE
```

8.  To find your files:
```
C:\ d:
D:\ ls
```
This will give you a directory list of your home directory. Dosemu maps your home directory to the DOS D: drive. You will note that Dosemu mangles the filenames in order to make them 8.3 filename compliant. Not to worry, it hasn't done anything to them; you'll just have to decide based on the first few characters of the actual file name. The commands "cd" (change directory") and "ls" (list) are your friends. 

9.  Copy your BIOS files from their directory (we'll call it "STOREDIR" as an example) to the floppy:
```
D:\ copy BIOSDIR\* a:\
XYZ123.BIN => a:\XYZ123.BIN
AUTOEXEC.BIN => a:\AUTOEXEC.BIN
BFLASH.EXE => a:\BFLASH.EXE
OTHERFILE.COM => OTHERFILE.COM
D:\
```

10. Exit Dosemu:
```
D:\ exitemu
```

11  Now, back at the Konsole terminal, unmount the floppy and exit:
```
user@localhost:~$ umount /dev/fd0
user@localhost:~$ exit
```

12. Follow the instructions of the BIOS vendor.

Happy Trails,

Loye Young
[http://www.iycc.net](http://www.iycc.net)
Laredo, Texas


That is another way to do it, but if you have no floppy drive the freedos on a cd-rw with the bios update and the flash program is an option to get the job done. I upgraded the bios in my laptop with a bootable cd-rw with my bios tool and update with no problems.

---

### Post by ciscosurfer on 2007-05-09
@loyeyoung,

I applaud your effort and think other ways of accomplishing this task are worth mentioning.  I don't, however, know very many people who still use a floppy.  But if you do and it works for you (notice I included similar code to create a floppy bios flasher as well, and all in all, the code is less than yours.  But that's neither here nor there. :-)).  I also don't know what you mean when you say my instructions contain untested software to be used on Debian or Ubuntu.  All software I mention is available through the repositories (and has been tested on Debian and Ubuntu) with the exception of the FreeDOS FDOEM image, which doesn't get used in any capacity until the reboot anyhow to provide the environment to allow your machine to process the new bios code.

But like I said, and am a firm believer in: it's always good to have many points of view.

---

### Post by msak007 on 2007-05-10
This is a very informative post and not to take anything away from it, but Dell already has a utility that I just learned about for flashing the BIOS on their machines running GNU/Linux:
 
[http://linux.dell.com/projects.shtml](http://linux.dell.com/projects.shtml) (BIOSdisk, a little past halfway)
 
It seems pretty interesting and lets you make a floppy, floppy image, installable package (currently only RPM, but my hope is that they update it to include DEBs since they're pre-installing Ubuntu now), and even an option to add it to your bootloader so your next boot will kick off the update automatically! I've never tried it so I can't say how well it works, but I'd be interested to see if any Dell owners have tried it and used it successfully.

---

### Post by marmux on 2007-05-11
> **msak007 said:**
> This is a very informative post and not to take anything away from it, but Dell already has a utility that I just learned about for flashing the BIOS on their machines running GNU/Linux
 

I just gave Dell's utility a try, and it worked perfectly to make a bootable image to flash the BIOS. However, their software is targeted to Fedora, so it needs some little tweaks.
I have a Dell Inspiron 1300 laptop running Ubuntu Feisty.
I had tried before to run the .exe file under M$Windoze, but since my battery is dead it didn't let me go through. So this is what I did under Ubuntu. Again, try it at your own risk...

1) I went to [ftp://ftp.dell.com/bios]("ftp://ftp.dell.com/bios") and downloaded the updates I needed (I was 6 versions behind!!!). In my case,  they are executables files with name ME051xyy.EXE where xyy is the version number.

2) I downloaded the biosdisk-<version>.tar.gz tarball from [http://linux.dell.com/biosdisk/]("http://linux.dell.com/biosdisk/")

3) biosdisk needs dos2unix and some other stuff. Everything should be ok doing
```
sudo apt-get install sysutils syslinux
```

4) I unpacked and installed biosdisk with (in the directory where the tarball is)
```
tar -xzvf biosdisk-<version>.tar.gz
cd biosdisk-<version>
sudo sh install.sh 
```
which should install the script /usr/sbin/biosdisk

5) since the installed script is a sh script, under Ubuntu (and under any Debian based distro I think) this must be modified into a bash script because of some shell conflict. Therefore, do
```
sudo gedit /usr/sbin/biosdisk
```
edit the first line #!/bin/sh into #!/bin/bash, save and exit. 

6) Install the FILE.EXE executable Bios update file downloaded from Dell with 
```
cd <the directory where FILE.EXE is>
sudo biosdisk install FILE.EXE
```
this produces a /tmp/FILE.img image file and then exits, complaining that the automated procedure only works under Fedora. The file must then be manually copied with
```
sudo mv /tmp/FILE.img /boot/
```

7) modify grub's boot menu with
```
sudo gedit /boot/grub/menu.lst
```
adding the following lines at the end:
```

title           BIOS Flash FILE
kernel          /memdisk
initrd          /FILE.img
```

Then reboot and select the new entry in the boot menu. This should launch the DOS utility to flash the BIOS. If everything goes well, it should check if the system is OK, ask if you want to update the BIOS, update it and automatically reboot.

I hope this helps!

---

### Post by r2d22 on 2007-05-12
i fount the part where i'm told to unzip the .exe a bit confusing, but once i realized you are simply telling me to unzip whatever file i have to get to the .exe, everything went smoothly. thank you for taking the time and writing this!

---

### Post by Mebyon.Kernow on 2007-05-12
I just completed the BIOS update to A14 on my Inspiron 6400 and it worked. The instructions from marmux are spot on.

---

### Post by ciscosurfer on 2007-05-13
> **msak007 said:**
> This is a very informative post and not to take anything away from it, but Dell already has a utility that I just learned about for flashing the BIOS on their machines running GNU/Linux:
 
[http://linux.dell.com/projects.shtml](http://linux.dell.com/projects.shtml) (BIOSdisk, a little past halfway)
 
It seems pretty interesting and lets you make a floppy, floppy image, installable package (currently only RPM, but my hope is that they update it to include DEBs since they're pre-installing Ubuntu now), and even an option to add it to your bootloader so your next boot will kick off the update automatically! I've never tried it so I can't say how well it works, but I'd be interested to see if any Dell owners have tried it and used it successfully.Sounds good to me! :)

---

### Post by ciscosurfer on 2007-05-13
> **r2d22 said:**
> i fount the part where i'm told to unzip the .exe a bit confusing, but once i realized you are simply telling me to unzip whatever file i have to get to the .exe, everything went smoothly. thank you for taking the time and writing this!Sorry for the confusion.  The main reason I was so detailed was to allow users to understand the full scope of what is about to occur.  Could it be rewritten to better explain what's going on?  Possibly.  But all in all, I believe most users will get the gist of it.  And I'm glad you got it working for yourself. :KS

It is my hope that in the future that more and more computer manufacturers will adopt native methods to flash our motherboards BIOSes.  If you can find a native solution, that's fantastic, and by all means (usually) a quicker and smoother solution.  

As always, read up on current flashing information for your board before attempting anything--you might be surprised to find a solution that "fits the bill" and takes care of everything for you. :-)

---

### Post by thomasaaron on 2007-06-15
Is there any way you could create a variation of this how-to for making bootable USB pen/flash drives?

---

### Post by thomasaaron on 2007-06-15
When I try to create the CD image, and I get to the part where I need to copy my .exe and new bios file to /mnt/temp, I get an error:

No space left on the device.

Any thoughts on that?

Best,
Tom

---

### Post by Alanholt on 2007-07-02
> **ciscosurfer said:**
> Thanks for the tip.  I've added this information into my HOWTO as an "EDIT". :D

Glad this HOWTO was helpful for you. :D

I have tried many options to flash a Foxcon 661 board and have failed after about 500 attempts thinking Iwas so dumb.
I have removed and changed the BIOS jumper the TBL_EN jumper, tried AFU860H and AWDflash all to no avail
AWD flash stops when you get to the Program and the AFU860 comes back and says the jumper must be in as the Bios is write protected.
Any tip would help. have tried all combinations of jumpers and there is no write protect jumper on this board.
The manual is absoluteley ****** useless.
Their tech support is laughable and has suddenly today disappeared from the Auto reply address they send you email from
HELPPPPPP.:(

---

### Post by thomasaaron on 2007-07-02
Hi, Alanholt.

We don't do any testing or work with your computer model, so I'm not sure where to point you.
Flashing the BIOS on our computers requires no jumpers.

Try going into your BIOS menu and seeing if there is a setting anywhere that removes the BIOS write-protection.

Best,
Tom

---

### Post by Apostata on 2007-07-06
I'm a little confused - when I run the command to create an ISO, I get the following:
>  ~/Desktop$ sudo mkisofs -o Bootable-CD-BIOS-Image.iso -b FDOEM.144 FDOEM.144
I: -input-charset not specified, using utf-8 (detected in locale settings)
genisoimage: No such file or directory. Invalid node - 'FDOEM.144'.

I'm not clear on how mkisofs is supposed to know where FDOEM is if I've unmounted /mnt/temp.

---

### Post by aparigraha on 2007-07-25
I can't move my BIOS exe file into the mounted directory. Write access is denied, and impossible to change once FDOEM.144 is mounted. I can move it there before it is mounted but it disappears once I mount.
I got the APIC error 40(40) and this is my last resort. Windows is NOT an option.

Please help.

EDIT: After extracting the .exe using cabextract to get a lot of files I realized that the image would be too big to fit the mount. I found a 12-year-old 2 gig HD, unplugged all other HDDs, installed XP-StrippedToTheBone and updated the BIOS through there instead. Solved!

---

### Post by maikunari on 2007-07-27
I've done everything as per instructions, but when I boot into Freedos and type the command AFLASH.EXE or AFLASH i get an error saying the system cannot find the Bios' hook.

Any clue as to what I should do?

---

### Post by reacocard on 2007-07-31
When I try to extract the exe, it gives me this:

```
aren@aren-laptop:~/Installs/bios junk$ unzip sp32790.exe 
Archive:  sp32790.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of sp32790.exe or
        sp32790.exe.zip, and cannot find sp32790.exe.ZIP, period.
```

Any ideas?

EDIT: I think I got it, I had to extract the main one with cabextract first, then unzip the exe that produced. Now to see if it works.

EDIT2: another snag: the extracted files are too big for the image. I'm using a cd, so is there any way to increase the space?

---

### Post by Tumpster on 2007-08-06
I'm running a bootable cd and i get the flash utility up and running it gives me "source file not found" when I attempt to flash it. I only have so many files and I've tried to get it to work. What could I be doing wrong?

---

### Post by fugative on 2007-08-16
got the same  problem as thomasaaron 
freedos 1.4m
sp30341.exe   DON'T fit 
help!!

otherwise howdo i make ados bootable  cdrom

cheers

---

### Post by Tristan Schmelcher on 2007-08-24
I used the CD approach here on Debian to upgrade the BIOS of my Dell XPS M1710 laptop, and it worked perfectly. Thanks for the guide!

---

### Post by dayd on 2007-09-02
Hi! 

Great post! 

It does not work for me, though! :(

I've tried the steps many times with no luck.

I'm using the bios from Gigabytes webpage. I go through the steps with out any errors. However, when I run the flash.exe I always get the following error. And nothing happens.

Error 10 : Bus ID error

Ive also tried using AwardBios. That utility complained about the Program File's part number does not match your system! And it did nothing.

So, has anyone seen this error, and then was able to get around it? Any suggestions about a possible work around? I've been searching for hours with no good leads!

Thanks a million!

-DD

OS: Debian etch
MotherBoard: GA-K8NSC-939 nForce3 250Gb chipset
CPU: AMD64 x2 4200+
Floppy: NONE!!!!!!!!!

---

### Post by tech9 on 2007-09-05
sweet, I will have to try this.... of course on a test workstation - you can never be too cautious.

---

### Post by henriquemaia on 2007-12-14
Thanks [ciscosurfer]("http://ubuntuforums.org/member.php?u=122263") for this howto. It was very useful (and works nicely too).

---

### Post by h4mx0r on 2007-12-18
The floppy image was far too small to fit my bios and installer so I used bartpe to create a minimal windows live cd with the bios installer file on it. I couldn't find any documentation as to how to use freedos with a cd otherwise I would have.

---

### Post by Rhubarb on 2007-12-18
> **h4mx0r said:**
> The floppy image was far too small to fit my bios and installer so I used bartpe to create a minimal windows live cd with the bios installer file on it. I couldn't find any documentation as to how to use freedos with a cd otherwise I would have.
If you look at page 1 of this thread, under the heading,
" Creating the disk (CD-method) "

It'll tell you how (this works wonderfully, thank you OP).

---

### Post by micschk on 2008-01-13
Thanks! 
Just updated my HP nc6220 to bios version F13 using your CD way!

(now see if I can hack the BIOS to support my new Atheros wireless card ;) )

---

### Post by jabeez on 2008-01-23
Thanx man, after a lil (or alot) dickin' around I finally got it to work and work it did, now on to other problems...........:)          Cheers!!!!

---

### Post by olek54321 on 2008-02-02
I think the subject pretty much says it all.  It's laughably easy to update your BIOS now... if you're using a Dell.  Thank goodness for their recent embrace of Ubuntu!! :)

I have a Power Edge SC420 server and since it's never had MS installed I was still running the original (**very** old) BIOS.  I was about to [upgrade my Ubuntu]("http://ubuntuforums.org/showpost.php?p=4252984&postcount=28") and I figured that this was a good opportunity to **finally** upgrade by BIOS too.  I spent a while searching around for this info but hopefully that will make things easier for a few other people out there.

The Dell wiki walks you through the 4 (yes, you read that correctly: _***4***_) commands that you need to enter to flash your BIOS.

[http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)

Or, if you're impatient, you can just skip to the cliff notes.

[http://linux.dell.com/wiki/index.php/Repository/firmware#Putting_it_all_together](http://linux.dell.com/wiki/index.php/Repository/firmware#Putting_it_all_together)

Note that in both places they have specific instructions for Ubuntu.  Yay for things that "just work"!! \\:D/

---

### Post by AdamTheNewbie on 2008-02-04
> **olek54321 said:**
> I think the subject pretty much says it all.  It's laughably easy to update your BIOS now... if you're using a Dell.  Thank goodness for their recent embrace of Ubuntu!! :)


Laughable - in a bad way - Not available for the Dell 530.

a.

---

### Post by rjgwalt3 on 2008-07-10
> **Apostata said:**
> I'm a little confused - when I run the command to create an ISO, I get the following:


I'm not clear on how mkisofs is supposed to know where FDOEM is if I've unmounted /mnt/temp.

Hi, I got the same results too, but after a few tries and trying to
read the manpages I came up with this.

Started with FDOEM.144 and *copies* of my flash files in a directory named "/bios" in my home directory (clever name huh!).

> 
rjgwalt3@Colossus:~$ sudo /bin/bash
root@Colossus:~# mkdir /mnt
root@Colossus:~# mkdir /mnt/temp
root@Colossus:~# modprobe loop
root@Colossus:~# mount -o loop -t vfat /home/rjgwalt3/bios/FDOEM.144 /mnt/temp
root@Colossus:~# cp /home/rjgwalt3/bios/AFUDOS.exe /mnt/temp
root@Colossus:~# cp /home/rjgwalt3/bios/M2NX0907.ROM /mnt/temp

// checked for all files I needed ...

root@Colossus:~# dir /mnt/temp
AFUDOS.exe    command.com  kernel.sys	 readme
autoexec.bat  config.sys   m2nx0907.rom  sys.com

// back to HowTo instructions ...

root@Colossus:~# umount /mnt/temp
root@Colossus:~# mkisofs -o Bootable-CD-BIOS-Image.iso -b FDOEM.144 /home/rjgwalt3/bios
I: -input-charset not specified, using utf-8 (detected in locale settings)
Size of boot image is 2880 sectors -> Emulating a 1440 kB floppy
Total translation table size: 2048
Total rockridge attributes bytes: 0
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 0
1177 extents written (2 MB)

// and burned it here ...

root@Colossus:~# cdrecord -v Bootable-CD-BIOS-Image.iso
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
Device was not specified. Trying to find an appropriate drive...
Looking for a CD-R drive to store 2.30 MiB...
Detected CD-R drive: /dev/sr0
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identification : 'DVDRW LH-20A1S  '
Revision       : '9L02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 988416 = 965 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data     2 MB        
Total size:        2 MB (00:15.72) = 1179 sectors
Lout start:        2 MB (00:17/54) = 1179 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 358667
Forcespeed is OFF.
Speed set to 8467 KB/s
Starting to write CD/DVD at speed  48.0 in real TAO mode for single session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    2 of    2 MB written (fifo 100%) [buf  98%]  21.5x.
Track 01: Total bytes read/written: 2410496/2410496 (1177 sectors).
Writing  time:   17.733s
Average write speed   3.2x.
Min drive buffer fill was 98%
Fixating...
Fixating time:   14.780s
BURN-Free was never needed.
wodim: fifo had 38 puts and 38 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
root@Colossus:~# 


The trick was to substitute the directory where FDOEM.144 was in
place of the second reference to FDOEM.144 .
Hope this might help someone else.

rjgwalt3

---

### Post by FakeOutdoorsman on 2008-07-28
Excellent!  Worked perfectly on an old Dell Optiplex GX1.  Thanks for the tutorial.

---

### Post by ray_niblock on 2008-08-25
CISCOSURFER - Thanks.  Worked a treat on an old KM400 mobo and now recognises my Sempron CPU.  Used the method of writing to a CD and was amazed at the ease of flashing without a serious hitch.

---

### Post by ivotron on 2008-09-14
For those unable to put their files into the floppy image, [this guy]("http://liquidat.wordpress.com/2007/05/20/howto-update-bios-on-linux/") describes a different approach that might work.

Cheers!

---

### Post by hmarkg on 2008-11-04
Is there anyway to fit in the BIOS flash files into the floppy image with the different approch that ivotron suggested.?

---

### Post by Rhubarb on 2008-11-04
> **hmarkg said:**
> Is there anyway to fit in the BIOS flash files into the floppy image with the different approch that ivotron suggested.?

The approach that ivotron suggested uses a live CD + usb flash drive.
I'm a little confused as to what you're specifically asking for there hmarkg, as there are no floppy disks or floppy disk images in ivotron's link there (though there is one for this tutorial).

On a separate but related note, I did discover a very nice utility called **flashrom**.
It's in the 8.10 repositories, it lets you flash many BIOSes right from the terminal.  I haven't tried it out, but it looks promising.

---

### Post by hmarkg on 2008-11-05
What I meant was I do not want to use the CD + USB method...

---

### Post by hmarkg on 2008-11-05
Sorry... But what I meant was I do not want to use the CD + USB methos to flash my BIOS. If you see the HOWTO in the first post:

Unzipping the .EXE

   1. Okay. So you've downloaded an .EXE that contains your BIOS manufacturers flash program as well as the new BIOS ROM file. In addition, you'll probably find a Readme.txt file of some sort that will tell you exactly the syntax they want you to use to flash your BiOS. You can then you unzip the .EXE file -- you can grab unzip by going to [http://packages.ubuntu.com](http://packages.ubuntu.com), selecting your release, and then choosing the unzip application.
   2. If you want a much more robust set of archiving apps, then you can run the following in a terminal (universe and multiverse will need to be enabled. See Enabling Extra Repositories, written by aysiu, for information on how to enable extra repositories)
      Code:

      sudo aptitude update && sudo aptitude install rar unace unrar p7zip arj unzoo lha libarchive1 libarchive-tar-perl libarchive-zip-perl dpkg-dev

   3. The unzipping process would look something like this:
         1. unzip ~/Desktop/hpbios.exe
         2. various files have now been extracted to your Desktop
         3. view the Readme file by issuing cat or less:
               1. cat Readme.txt or less Readme.txt
         [B]4. copy the new flash bios program and the new bios rom to /mnt/temp [1]
               1. [1] (which now should include your flash program and the new BIOS ROM file as well...in addition, there may be other files that you wish to copy over, such as an Autoexec.bat file to automate the process. If you don't want to enter any commands manually upon reboot, then copy over all files that were extracted to your Desktop and make sure they are part of FDOEM.144 located under the /mnt/temp directory. You can check to make sure that all files were copied over successfully by changing directories into /mnt/temp and viewing the newly copied files from the "deflated" .EXE)[/B]
         5. move to the next step of unmounting the image

I encounter problem when i come to the step where I have to copy the new flash bios program and the new bios rom to /mnt/temp. I can't seem to fit all the files into the /mnt/temp file. 

I think there are two more person in this tread is also encountering the same problem. Please help. Many thanks in advance...

---

### Post by hmarkg on 2008-11-06
My Laptop is a Compaq Presario CQ45-129TX. These are the files that I got after extracting my .EXE file downloaded from the manufacturer official website. 

[CENTER][IMG]http://i66.photobucket.com/albums/h267/hmarkg/Screenshot-3.png[/IMG][/CENTER]

My problem is that I cannot fit in all the files into /mnt/temp directory. And my question now is if I were to copy only the important files, which are the files..?? I'm running on 64-bit ubuntu 8.10 intrepid (Kernal Linux 2.6.27-7-generic)

---

### Post by Rhubarb on 2008-11-07
hmarkg, I found that typically hp and compaq (compaq is owned by hp anyway) release windows-only BIOS flash update programs.
These programs don't usually run in DOS, freedos, reactOS, wine, or perhaps even flashrom for that matter.

I have a hp laptop, and have been unable to update it without having to backup ubuntu, install windows, apply BIOS update, delete windows, restore ubuntu.
Which is a really big pain to do.
So, unless there's any other solutions available to you, I recommend you send compaq (hp) an email letting them know that you would like to flash your BIOS without having to purchase / install windows.  I send them an email every time I update my BIOS.

---

### Post by hmarkg on 2008-11-07
Thanks Rhubarb for the info really appreciate it. I shell have that email send first thing in the morning tomorrow. Thank you.

---

### Post by Alzyme on 2008-11-08
Hi hmarkg,
  sorry for the late reply, I normally do not frequent this forum but saw someone was having a bit of trouble so made a quick post to try and help. I don't know of how to flash insyde BIOS the ubuntu way but there are three options I do know of.

1. Windows (using winflash)

2. DOS (using flashit)

3. Using the built-in BIOS crisis recovery

I guess you don't want option 1 so for option 2 you could try downloading [[color=blue]**_here_**[/color]]("http://www.filefactory.com/file/6faed2/n/1_BIOS_rar") and change as necessary with the BIOS version you require. Note that the included BIOS files are f.11c although they are named the same as f.12. Normally one would use the flash.bat file to flash. AFAIK some of the Acer insyde BIOS updates also provide flashit and _might_ be compatible with the HPs but I've never tried them.

The 3rd option is really for crisis recovery, a flash gone wrong and no longer able to boot. It uses just the BIOS file renamed appropriately (in your case to 30F7.BIN) and placed on a fat16/32 formatted usb flash drive (doesn't need to be bootable). The battery needs to be removed and the adapter power cable disconnected. Place the usb flash drive in any of the usb receptacles then while holding down the 'windows key' and the 'B' key reconnect the power cable and switch on (hope you've got two hands). You can then let go of the keys and hopefully watch the usb being read by the notebook. After the file has been read wait a while and the notebook should switch itself off if everything worked properly. The whole operation from switching on to the notebook shutting down should take about 1 minute.

Note that after f.04 the HP BIOS updates contain two BIOS files, I believe one is for discrete graphics (D) or (DIS) and one for integrated shared memory graphics (U) or (UMA).

Hope this helps.

---

### Post by hmarkg on 2008-11-09
One question. I am just wondering as i asked my lecturer about this BIOS flashing thing with ubuntu. He said it is very dangerious. If fail i may need to throw my laptop away. My question is that is it safe to do so, this is my first time doing such thing. And if I failed, is it as bad as what my lecturer said. I do not wan to lose the laptop.

---

### Post by Alzyme on 2008-11-09
The short answer would be that what your lecturer said is possible.

---

### Post by ciscosurfer on 2008-11-09
> **hmarkg said:**
> One question. I am just wondering as i asked my lecturer about this BIOS flashing thing with ubuntu. He said it is very dangerious...He must have read my tutorial and noticed all the times I mentioned that flashing a BIOS is destructive/dangerous/hazardous/etc.  

> ...If fail i may need to throw my laptop away...That's a little extreme.  You need to flash your BIOS per your manufacturers guidelines and suggestions.  If you flash it once and it fails, yes, you've borked your system, which is why you will have already made a copy of your current (or later) BIOS so you can flash it properly the next time. :-D

> ...My question is that is it safe to do so, this is my first time doing such thing. And if I failed, is it as bad as what my lecturer said. I do not wan to lose the laptop.Do you know anyone locally who can help you through this process (we're always here for you, btw :-)).  Here's the thing: it *is* potentially dangerous b/c of all the warnings previously mentioned.  It's important to do it the right way.  When done correctly, increased functionality and potentially a slew of bugs that were present in the original BIOS, are then fixed.  The idea is greater functionality (or proper functionality in the event the BIOS never worked or worked too poorly to begin with).

You've downloaded a 32bit/64-bit Vista flashing tool that is well over 1.44MB is size.  In total, it's in the 7 to 9MB range.  Here are my suggestions: You can go with the link provided above by ivotron, you could use a pre-exectution environment like BartPE (also mentioned by another poster on this thread), or you can use Windows.  If you have a dual-boot environment, I would suggest flashing your BIOS using the OS it was designed for.

You should also write to Compaq requesting they provide a BIOS flashing tool native to Linux, preferably a Debian-based tool.  

The flashrom utility mentioned above is nice, has support for many chipsets/motherboards, but it too has its limitations.  For example, when trying to read my BIOS using the utility, it correctly identified my chipset but couldn't read the information to a file b/c it failed for some reason.

---

### Post by hmarkg on 2008-11-10
> Do you know anyone locally who can help you through this process (we're always here for you, btw )

As far as I do not have anyone that is able to help me in my friend cycle. So I am totally relaying on this forum. 

> You should also write to Compaq requesting they provide a BIOS flashing tool native to Linux, preferably a Debian-based tool

I have send them an e-mail but no reply.

> You've downloaded a 32bit/64-bit Vista flashing tool that is well over 1.44MB is size. In total, it's in the 7 to 9MB range. Here are my suggestions: You can go with the link provided above by ivotron, you could use a pre-exectution environment like BartPE (also mentioned by another poster on this thread), or you can use Windows. If you have a dual-boot environment, I would suggest flashing your BIOS using the OS it was designed for.

I am flashing my lappy to solve the sound problem. I guess I shell get a vista and flash it because I am kinda of blur to flash the BIOS.

---

### Post by ciscosurfer on 2008-11-10
> **hmarkg said:**
> As far as I do not have anyone that is able to help me in my friend cycle. So I am totally relaying on this forum.We'll try to assist the best we can ;-)

> I have send them an e-mail but no reply.I wouldn't hold your breath waiting on a reply.  If they do reply with suggestions, that's great.  But mainly the point is to make them aware there are users of their products out here that don't only use Windows.  Unfortunately, though, they may not support Linux in any capacity.  If enough people express their concerns then it's in their better interests to try to serve their customers in this regard.  Did you inherit this laptop? Is it still under manufacturer warranty?

> I am flashing my lappy to solve the sound problem. I guess I shell get a vista and flash it because I am kinda of blur to flash the BIOS.Have you looked into sound issue solutions posted elsewhere on this forum?

Ultimately of course, the decision is yours to shell out the money for Vista, but that seems like a high price to pay to simply flash your BIOS.  Trying to work through the methods suggested thus far may prove successful; just remember to heed all warnings and cautions.  Is your sound issue a known bug that Compaq has addressed?  If they have, does it only relate to sound w/in Windows?  Since they only provide Windows-based flashing tools, I would assume the answer to that would be: yes (if, in fact, there are known sound issues related to your current BIOS and a Windows environment).  Do they specifically say that flashing your BIOS will solve this problem?  Does Compaq offer free community-based support where you could pose these questions as well?  Here's a thought: you could get into a live chat with a tech support / sales person concerned about potential issues, etc., etc., and see what they have to say about this problem..that you've "heard about".

---

### Post by august495 on 2008-11-16
At the building the ISO stage, I am doing this:

```
mkisofs -o Bootable-CD-BIOS-Image.iso -b FDOEM.144 /home/paris/Desktop/folder/burn
```

With this as the error:
**genisoimage: Uh oh, I cant find the boot image 'FDOEM.144**

I have tried adding the path to FDOEM.144 with the same result.
Can you please point me in the right direction? I appreciate any help.

**EDIT**
I pointed to the wrong directory. I thought /home/... was where to place the created image file, not where FDOEM.144 was.  Fixed it, thanks.

---

### Post by VeeDubb on 2008-11-17
I just want to say, that the warnings here are serious.

I have flashed dozens and dozens of motherboard bios chips over the years, and have never had a problem until I followed the directions.  

The directions are just fine, but stuff happens, and even with loads of experience, I managed to fry my bios.

The only reason I used these directions, is that my computer doesn't even have a floppy drive, so making a CD that 'thinks' it's a floppy was a great trick.

Sadly, my motherboard also has an incorrectly implemented BIOS protection feature, which will cause the bios to get half-way through and then error out; and I didn't know about it.


Should anyone else fry their bios, don't worry.  I went to biosman.com and they were able to ship a replacement BIOS chip, pre-flashed with the latest bios for my board the very next day.  Should be arriving soon.  Then I can go back to posting at home, and actually doing my job at work. lol

---

### Post by Alzyme on 2008-11-18
> **VeeDubb said:**
> Sadly, my motherboard also has an incorrectly implemented BIOS protection feature, which will cause the bios to get half-way through and then error out; and I didn't know about it.Which mainboard / BIOS ?

Interesting, I have seen other posts where the OPs have failed when using a CDROM (notebooks) but Ok when using a USB flash drive.

---

### Post by unprinted on 2008-12-02
Thanks for this. I came across two issues trying to do it the 'CD' way:

a) The BIOS image was 2Mb in size and thus doesn't fit on a 1.44Mb floppy image!

Solution: use the FDSTD.288 one instead, changing the filename as appropriate. Fortunately, the flashing .exe was small.

b) An illegal instruction crash on running the .exe the first time I booted the CD.

Solution: say no to every boot option FreeDOS gives (no to loading DOS high, no to EMM386, etc.) 

... and it worked!

---

### Post by ciscosurfer on 2008-12-02
@unprinted,

Glad to hear that it eventually worked for you.  

It was very common (at least it was a few years ago) to have BIOS images stay under the standard floppy mark.  Times have changed though and mobo makers are increasingly using larger images.  I'm glad you found a method that worked for you.

---

### Post by bja888 on 2008-12-06
OMG!!! THANK YOU!!!!

I spent over 12 hours trying to fix this problem before this thread saved me. Turns out my board was shipped with an old version of the bios full of bugs that where making to impossible to work with. To top it all off, there is no floppy port on the board.

The CD solution worked wonders for me!!!!

Here is my full story on my blog...
[http://jacksdepression.com/post/7](http://jacksdepression.com/post/7)

**Edit:** Link updated. Since it is still getting traffic and I changed url scheme.

---

### Post by ciscosurfer on 2008-12-06
@bja888,

Very happy to hear you found this thread and that it was able to help you get your board working again. :)

---

### Post by ender353 on 2008-12-28
yo thanks. nice how to. how can you do this using a live cd?:)

---

### Post by ciscosurfer on 2009-01-05
> **ender353 said:**
> yo thanks. nice how to. how can you do this using a live cd?:)Not sure. Might be tricky. Theoretically I suppose you could roll your own distro and add the flashing files to it and force it to load on boot, thereby allowing a BIOS flash before entering a live environment. Other than that, not sure.  Alternatives to this HOWTO are to use a USB flash drive, a burned CD w/BIOS files, or a floppy.

EDIT: I assume you mean using a live Ubuntu CD, for example?

---

### Post by rexmo on 2009-02-12
Can you give any suggestion as to why I run out of space on the device???

> johnny@heythere-desktop:~$ cd Desktop
johnny@heythere-desktop:~/Desktop$ cd jaystonish
johnny@heythere-desktop:~/Desktop/jaystonish$ sudo gunzip FDOEM.144.gz
[sudo] password for johnny: 
johnny@heythere-desktop:~/Desktop/jaystonish$ dir
AFUDOS.exe  FDOEM.144  S8VM1023.ROM
johnny@heythere-desktop:~/Desktop/jaystonish$ mkdir /mnt/temp
mkdir: cannot create directory `/mnt/temp': File exists
johnny@heythere-desktop:~/Desktop/jaystonish$ sudo modprobe loop
johnny@heythere-desktop:~/Desktop/jaystonish$ sudo mount -o loop -t vfat FDOEM.144 /mnt/temp
johnny@heythere-desktop:~/Desktop/jaystonish$ sudo cp ~/Desktop/jaystonish/* /mnt/temp
cp: writing `/mnt/temp/FDOEM.144': No space left on device
cp: writing `/mnt/temp/S8VM1023.ROM': No space left on device
johnny@heythere-desktop:~/Desktop/jaystonish$ 



Thanks in advance!

---

### Post by ciscosurfer on 2009-02-13
rexmo,

You shouldn't need to use sudo when gunzipping the FDOEM.144 image, you should however use sudo or get root when creating the temp directory under /mnt

Is /mnt its own partition? Does it have enough available space? You can run a df -h to what's going on. Does /mnt/temp even exist? Change directories or take a file listing to see. How big is the image you are trying to copy over including your new flash rom? Which method (floppy, CD, other) are you attempting to copy to?

What I think is occuring is that the file AFUDOS.exe is too large and will not fit nicely into the 1.44 MB FreeDOS image we are using. There are alternative methods in this thread (links in the main post as well as comments throughout the thread) that can help you to flash using other means (there are even 2.88 MB images available if you need just a little more room). 

Lastly, have you checked to see if your board can be flashed using a native Linux utility?  If so, I would suggest going that route b/c it might be easier.

---

### Post by rexmo on 2009-02-14
Ok, I think the AFUDOS.EXE is well over 1.2 MB  and that doesn't leave enough room for the .ROM BIOS file.   

I am using this process to create a bootable CD so using any image up to about 740 MB should be fine.  

I currently cannot update the bios of my friends computer without creating a bootable CD because is does not have an OS yet and I need the update to install UBUNTU.

Is the 2.88 or even larger image file availabe through the FreeDOS link?
Could you send me the links?

Thanks very much!!!

---

### Post by ciscosurfer on 2009-02-15
A link to these images was posted in the Howto found on the first page, but here it is again for your convenience: [http://www.fdos.org/bootdisks/](http://www.fdos.org/bootdisks/)

You should be able to find what you are looking for on that page. 

Good luck!

---

### Post by reanbootsma on 2009-02-17
Great How-to

BUT it failed to work on Acer TravelMate 6592 with the following message:
(freeDOS) "InitDiskBad or missing Command Interpreter"

It is because the current BIOS on the laptop does not support a floppy drive (A:)...

Maybe  ciscosurfer  can add that as a note to save someone else some time - please.

It works on a desktop though.

rean

---

### Post by oo-boon-too on 2009-02-18
Very informative, very nice indeed!
Definitely going to remember this thread for the future.

---

### Post by nyarnon on 2009-02-28
Hi Guys,

Read this HOWTO and wonder what's it all about? Why wouldn't you just use FLASHROM [http://www.coreboot.org/Flashrom](http://www.coreboot.org/Flashrom)

install with 

> sudo apt-get install flashrom.

Backup your existing bios with 

> sudo flashrom -r original.rom

Write the new one with

> sudo flashrom -w new.rom

reboot and be happy.

---

### Post by dcstar on 2009-02-28
> **nyarnon said:**
> Hi Guys,

Read this HOWTO and wonder what's it all about? Why wouldn't you just use FLASHROM [http://www.coreboot.org/Flashrom](http://www.coreboot.org/Flashrom)

install with 

> sudo apt-get install flashrom.

Backup your existing bios with 

> flashrom -r original.rom

Write the new one with

> flashrom -w new.rom

reboot and be happy.

FYI I had to use "sudo" for the flashrom commands, but it worked for me on my ASUS/HP motherboard.

---

### Post by ciscosurfer on 2009-03-01
> **nyarnon said:**
> Hi Guys,

Read this HOWTO and wonder what's it all about? Why wouldn't you just use FLASHROM [http://www.coreboot.org/Flashrom](http://www.coreboot.org/Flashrom)

install with 

> sudo apt-get install flashrom.

Backup your existing bios with 

> flashrom -r original.rom

Write the new one with

> flashrom -w new.rom

reboot and be happy.Use whatever method works best for you.  Using flashrom always gave me errors (even thought it claims my chipset is supported).  The flashrom utility seems to work well for many people. You can see which devices are supported by going to [http://www.coreboot.org/Flashrom](http://www.coreboot.org/Flashrom) or by issuing```
flashrom -L
```Yes, there are commands to "force" flashrom to probe/read/erase/write...but I wouldn't suggest doing so unless you are absolutely sure you know what you are doing.  Again, use the method that works best for you.  Thanks to [nyarnon]("http://ubuntuforums.org/member.php?u=597388") for bringing up this method again in this thread as all methods of flashing are good to know about. :)

---

### Post by nyarnon on 2009-03-02
> **ciscosurfer said:**
> You can see which devices are supported by going to [http://www.coreboot.org/Flashrom](http://www.coreboot.org/Flashrom) or by issuing```
flashrom -L
```

This is partially true as the list only shows known boards. Therefore it would be nice if you own a board that flashes you expand the list. Or if you have one that doesn'r you do the same stating it doesn't work.

> **ciscosurfer said:**
> Yes, there are commands to "force" flashrom to probe/read/erase/write...but I wouldn't suggest doing so unless you are absolutely sure you know what you are doing.  

Let's face it, this extends to the whole procedure of flashing your rom, with or without flashrom.

> **ciscosurfer said:**
> Again, use the method that works best for you.  Thanks to [nyarnon]("http://ubuntuforums.org/member.php?u=597388") for bringing up this method again in this thread as all methods of flashing are good to know about. :)


Your welcome, considering the many existing procedures It would be nice to see it mentioned in the very first message of this tread, the app can save a lot of people a lot of headache.

---

### Post by nyarnon on 2009-03-02
> **dcstar said:**
> FYI I had to use "sudo" for the flashrom commands, but it worked for me on my ASUS/HP motherboard.

Your right, I will correct my message accordingly. Thank you for chipping in.

---

### Post by ciscosurfer on 2009-03-02
@nyarnon,

I've amended the first post to talk about flashrom as well. Hopefully people can make use of it if they choose to.

---

### Post by nyarnon on 2009-03-03
@ciscosurfer

Great work, maybe around the release date of Jaunty would be a good time to tidy things up in a v2 of this howto. These distro releases are often a point in time where people also consider flashing :-)

---

### Post by ciscosurfer on 2009-03-03
> **nyarnon said:**
> @ciscosurfer

Great work, maybe around the release date of Jaunty would be a good time to tidy things up in a v2 of this howto. These distro releases are often a point in time where people also consider flashing :-)Thanks and agreed :) I hope to give this tutorial a refit in the coming weeks.

---

### Post by happy_pig on 2009-03-05
I have the same problem as others who have to use a windows based bios update - HP provides a file SPXXXXX.exe which runs like a windows installer program when windows is running. Which when after using cabextract provides a bios.wph file along with the other files needed by windows to install it.

Now to see if flashrom would work as described above I backed up my original bios.bin then I wrote it back to see if flashrom would work. Success! Now to see if flashrom handles .wph files. I tried to back up my original using .wph instead of .bin and re-wrote using the same. Success. 

Now when trying to use the bios.wph file that I got from the cabextract it says it is too big 514kb as opposed to 512kb. Now I read somewhere that the difference is size may be just a bit of the file that refers to the Windows program that uses that file in its install process and that this bit can be stripped out.
Now does anyone have any experience in doing this and how would I work out which bits to strip out?

This thread [http://popey.com/Installing_HP_BIOS_Updates_under_Linux](http://popey.com/Installing_HP_BIOS_Updates_under_Linux) is the one I read about stripping bits out - not sure about trying wine to install as he suggests but the second bit about making the image file the correct size has some potential 

Thanks for this thread.

---

### Post by joris1977 on 2009-04-18
Hi 

Thanks for this howto, I used it successfully a while ago. Now i want to flash another bios, but i can't find the FDOEM.144.gz file anymore. the links in this howto are no longer correct because the freedos moved to a new website. [http://www.freedos.org](http://www.freedos.org) 

I know i am an idiot, but i really cannot find the FDOEM.144.gz file. If i find it later i'll drop a link here... I guess the file must be somewhere on the new site. If someone can provide a link in this howto than that would be appreciated a lot.

---

### Post by twowheeler on 2009-04-18
I tried the biosdisk method from this thread, but the bios upgrade file from Dell is R71684.exe, a windows-only file.  In freedos I get "This program will not run in DOS mode."  It will not run in wine either (no great surprise.)  Any suggestions?

---

### Post by nyarnon on 2009-04-18
> **twowheeler said:**
> I tried the biosdisk method from this thread, but the bios upgrade file from Dell is R71684.exe, a windows-only file.  In freedos I get "This program will not run in DOS mode."  It will not run in wine either (no great surprise.)  Any suggestions?

Try a windows live cd, there are several available on the net, ofcouse stricktly illigal but they will do the job. Be carefull and check them for virusses before using them. On the other hand if you only use it for the bios update and don't run a windows partition who cares :-)

---

### Post by joris1977 on 2009-04-19
In my previous post I mentioned that I really couldn't find the fdoem.144.gz file on the freedos website. Flashrom didn't recognize my BIOS either so that wasn't an alternative. 

In this thread loveyoung mentioned dosemu, but his howto made use of a floppy and my computer doesn't take floppies. So that didn't seem like a solution for me. It could have pointed me in a right direction, but I am not really an experienced linux user or have a lot of technical computer knowledge.  

I went to the freedos IRC to ask if someone might know where I could find the fdoem.144.gz file. On the freedos IRC I met mcericicq, who was very friendly and helpful. Though he couldn't help me with the fdoem.144.gz file, he described in 8 steps howto create a bootable BIOS cd with the use of dosemu. It took me some small steps more, but they were easy to figure out. 

I promised mcericicq to post in this thread how I did it.  So here it is. Create a bootable BIOS CD  with the help of dosemu. It worked for me and should work for you... but no guarantees!           

1 Start with installing dosemu. Open up a terminal and paste:

```
sudo apt-get install dosemu
```

and run dosemu from the command line

```
dosemu
```

close it afterwards, but this creates the .dosemu directory you need later

2 Next step is to create an floppy image you can use in dosemu. Copy & paste this line in the terminal 

```
dd if=/dev/zero bs=1024 count=1440 of=floppy.img
```

3 To be used in dosemu this floppy image needs to be dos read/writeable, To do this type in the terminal 

```
mkdosfs  floppy.img
```

4 copy the floppy.img to the .dosemu directory. On the command line:

```
mv -i floppy.img .dosemu
```  

5 To be able to mount the floppy image in dosemu you need to create a   dosemu.conf file in your home directory and edit a line. The dosemu.conf is available in /etc/dosemu/dosemu.conf So copy it to your home directory by typing this at the command line:  

```
cp -i /etc/dosemu/dosemu.conf ~/ 
```

Dosemu will only use this file when you rename it to .dosemurc
You can rename it on the command line with: 

```
mv -i dosemu.conf .dosemurc 
```

6 Next step is to edit your ~/.dosemurc Type in a terminal

```
gedit ~/.dosemurc
```

Find line 81, that says: # $_vbootfloppy = ""

delete the # and change that line in

$_vbootfloppy = "floppy.img +hd"

save the file and close gedit.

7. Now it is time to boot dosemu with in the terminal 

```
xdosemu -C
```

8.In xdosemu: note this line:

D: = LINUX\FS/HOME/yourusername attrib = READ/WRITE  

D:, or whatever letter is mentioned, is where dosemu has your home directory mounted, that will be usefull to know later on  

Look for this line: 

Z: = Linux\FS\${DOSEMU_LIB_DIR}/DRIVE_Z attrib = READ ONLY 

It probably says Z: otherwise use the letter mentioned. 

type

```
z:
```
 
and then type 

```
sys a:
```

This will copy KERNEL.SYS and COMMMAND.COM to the floppy.img

you can check if it worked by going to A: and type ls 

9 Now copy all the files you need to flash your bios to A:
Go to D: or wherever dosemu has your home directory mounted,  you can copy the files with

```
copy yourfilename a:\
```
 
use ls to see your directories and you can switch directories with cd or go back with cd\  

9 close dosemu with

```
exitemu
```

copy the floppy.img from .dosemu to your home directory and create and image with

10 
```
mkisofs -o Bootable-CD-BIOS-Image.iso -b floppy.img floppy.img
```

This will give you an Bootable-CD-BIOS-Image.iso file that you van burn to an empty disc with many cd burners. Or from the command line with:

```
cdrecord -v Bootable-CD-BIOS-Image.iso 
```  


Please post any questions about this howto in this thread and i will try to answer them. Be aware that i have very limited knowledge about this subject. Now that fdoem.144.gz is no longer available, maybe ciscosurfer wants to rewrite his howto and incorporate mine. He seems to understand what he is suggesting and i cannot totally say that ;) But that is up to him ofcourse. (It would be a good thing; just search for fdoem.144.gz with google and you see how often his howto is copied on other sites/forums)

---

### Post by twowheeler on 2009-04-20
> **nyarnon said:**
> Try a windows live cd, there are several available on the net, ofcouse stricktly illigal but they will do the job. Be carefull and check them for virusses before using them. On the other hand if you only use it for the bios update and don't run a windows partition who cares :-)

If only it were that simple.  This @*&#! Dell program won't run on the ram disk that the windows live cd uses.  It apparently will only run on the hard disk.  

I can't believe it, but I may have to partition my hard drive and install windows 2000 (I have an old CD) just to run the BIOS update!!!
](*,)

-----------------------------------------------------
Edit: Eureka -- all I needed was [this site.]("http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate")

---

### Post by johnjohn2 on 2009-04-22
Gigabyte support only offer bios updates for windows machines, but i have found that wine makes the process easy for extracting the .exe file and then copy to usb thumb drive and and select the Q-Flash utility from the bios options.

Regards John

---

### Post by hissyfut on 2009-07-07
> **marmux said:**
> I just gave Dell's utility a try, and it worked perfectly to make a bootable image to flash the BIOS. However, their software is targeted to Fedora, so it needs some little tweaks.
I have a Dell Inspiron 1300 laptop running Ubuntu Feisty.
I had tried before to run the .exe file under M$Windoze, but since my battery is dead it didn't let me go through. So this is what I did under Ubuntu. Again, try it at your own risk...

1) I went to [ftp://ftp.dell.com/bios]("ftp://ftp.dell.com/bios") and downloaded the updates I needed (I was 6 versions behind!!!). In my case,  they are executables files with name ME051xyy.EXE where xyy is the version number.

2) I downloaded the biosdisk-<version>.tar.gz tarball from [http://linux.dell.com/biosdisk/]("http://linux.dell.com/biosdisk/")

3) biosdisk needs dos2unix and some other stuff. Everything should be ok doing
```
sudo apt-get install sysutils syslinux
```

4) I unpacked and installed biosdisk with (in the directory where the tarball is)
```
tar -xzvf biosdisk-<version>.tar.gz
cd biosdisk-<version>
sudo sh install.sh 
```
which should install the script /usr/sbin/biosdisk

5) since the installed script is a sh script, under Ubuntu (and under any Debian based distro I think) this must be modified into a bash script because of some shell conflict. Therefore, do
```
sudo gedit /usr/sbin/biosdisk
```
edit the first line #!/bin/sh into #!/bin/bash, save and exit. 

6) Install the FILE.EXE executable Bios update file downloaded from Dell with 
```
cd <the directory where FILE.EXE is>
sudo biosdisk install FILE.EXE
```
this produces a /tmp/FILE.img image file and then exits, complaining that the automated procedure only works under Fedora. The file must then be manually copied with
```
sudo mv /tmp/FILE.img /boot/
```

7) modify grub's boot menu with
```
sudo gedit /boot/grub/menu.lst
```
adding the following lines at the end:
```

title           BIOS Flash FILE
kernel          /memdisk
initrd          /FILE.img
```

Then reboot and select the new entry in the boot menu. This should launch the DOS utility to flash the BIOS. If everything goes well, it should check if the system is OK, ask if you want to update the BIOS, update it and automatically reboot.

I hope this helps!

tried this and shows the following on boot:
"Error 11: Unrecognized device string

Press any key to continue..."

which then returns to the grub menu.

fyi, the biosdisk install option is somewhat silly
in that it places the img boot entry above all other
kernel boot entries and changes the the default number
to the normal default kernel. back up menu.1st 1st.

---

### Post by Eric89GXL on 2009-07-09
> **ciscosurfer said:**
> 
To create the disk you must first unpack the image file by changing directories to where the image was downloaded and issuing the following:```
gunzip FDOEM.144.gz
```


Just wanted to add a third method (my preferred method). I'm not sure how you'd format it to match with the rest of the methods on the page, so I'll include all of the instructions that I use when updating a bios. Why use physical media (floppy or CD rom) and physical effort (inserting/removing media) when you could make the computer do all the work for you?

[SIZE=4][COLOR=RoyalBlue]** Creating the disk (No CD or Floppy method) **[/COLOR][/SIZE]

First, acquire the appropriate DOS image and extract it:

```
wget http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz
gunzip FDOEM.144.gz
```

Now mount the image so that you have access to it:

```
mkdir /tmp/floppy
sudo mount -t vfat -o loop,quiet,umask=000 FDOEM.144 /tmp/floppy
```

Put the files in the floppy image by placing them in the folder where you just mounted the image. For my Foxconn motherboard, this was:

```
unzip Motherboard.zip -d /tmp/floppy
```

Now that the BIOS updating files are on the floppy image, unmount it and move it to the /boot/ directory so that GRUB can use it to boot:

```
sudo umount /tmp/floppy
rmdir /tmp/floppy
sudo mv FDOEM.144 /boot/biosupdate.img
```

For GRUB to boot the disk, it needs memdisk. This is in the syslinux package, so install it (if necessary) and copy memdisk to where GRUB can get to it easily:

```
sudo apt-get install syslinux
sudo cp /usr/lib/syslinux/memdisk /boot/
```

Finally, we need to add the boot-screen option to boot up our bios update disk, so open the GRUB menu:

```

sudo gedit /boot/grub/menu.lst

```

and add the following lines at the end of the file (after the line "### END DEBIAN AUTOMAGIC KERNELS LIST"):

```

title       BIOS upgrade
kernel      /boot/memdisk
initrd      /boot/biosupdate.img

```

Note that **for nonstandard installations** where the standard boot options are **not** executed from the path /boot/, you will need to modify the paths above correspondingly. For example, I have /boot/ on its own partition, and instead of seeing the default "/boot/initrd.img-2.6.28-13-generic" as a boot path in /boot/grub/menu.lst, I saw "/initrd.img-2.6.28-13-generic". This meant that the paths had to be put in as "/memdisk" instead of "/boot/memdisk".

Reboot, and you should have the option to select "Bios Update" from the GRUB boot menu.

EDIT: Also, in addition to the posts linked to from the first post, this post was helpful in coming up with this method:
[https://lists.ubuntu.com/archives/ubuntu-devel/2005-January/003637.html](https://lists.ubuntu.com/archives/ubuntu-devel/2005-January/003637.html)

---

### Post by unutbu on 2009-07-09
That is very cool. Thank you, Eric89GXL.

---

### Post by ciscosurfer on 2009-07-09
@Eric89GXL,

Well done! Will incorporate into tutorial. Thanks for sharing this :)

---

### Post by m0jack01 on 2009-07-16
This is a helpful post, but there was an issue for my situation I had to approach another way. 

My Compaq Presario V6000 (AMD 64) had problems and needed a flash upgrade. Dual boot with Vista and Ubuntu 9.04. The Windows Vista partition was dead. 

Unfortunately for me, HP uses an .exe flash utility that only works in a Windows environment: WinPhlash. The best solution is to use a Windows boot disk, which you can make with BartPE. But my laptop wouldn't read any Windows boot disks from CD or USB.

Solution:

After much trial and error and Web research, I hit upon a flash solution that works with HP and Compaq laptops. Here's a short list of steps:

1. Download the HP Bios upgrade .exe file for your model from [www.hp.com](www.hp.com).
2. Extract all the files. 
3. HP Bios files have the extension .WPH (i.e. 30B7F42.WPH) - make a note of the file. It should be about 1MB.
4. Search the Web for the Phoenix DOS flash utility phlash16.exe and download.
5. Search and download a DOS boot disk image (iso file)
6. Use an Ubuntu utility such as ISO Master to add the bios file (.WPH) and the  Phlash16.exe program to the DOS boot disk image.
7. Burn the image to a CD (I like to use a read/write CD if getting the image right takes several tries)
8. Shut down the machine
9. Boot to the CD. Dos will load.
10. At the command line type "phlash16  ########.wph  /X" (Notes: substitute the name of your bios file for #; the /X switch is needed for phlash16 to work, bypassing HIMEM)

Follow the prompts - a lot of beeping later, your HP or Compaq laptop will be reflashed.

---

### Post by desertgeek on 2009-08-16
I tried the method described by Eric89GXL, but the BIOS files were Win32. After poking around in the BIOS files, I found the boot disk image. After verifying the image was correct, I copied it to /boot/biosupdate.img instead. When I rebooted into it it worked perfectly.

So, following his instructions and using the boot disk image directly from the manufacturer worked perfectly. It may be a better/easier method for others, since any new BIOS updates can be performed by copying the new bootdisk image to /boot/biosupdate.img, then rebooting into it.

---

### Post by JarlG on 2009-08-16
Hello!

I am very new to Ubuntu and the whole concept of Linux, so please excuse my lack of knowledge within this topic.

This is a great guide, however I encountered some difficulties;

When attempting to unzip the 'sp40182.exe' (the BIOS update from HP to my nc8430), I encounter the following message in Terminal:

```
unzip:  cannot find or open /root/home/jarlg/BIOS/sp40182.exe, /root/home/jarlg/BIOS/sp40182.exe.zip or /root/home/jarlg/BIOS/sp40182.exe.ZIP.
```Now, the file is clearly stored in my home-folder, and I even copy-pasted the link - to no use.

If I, however, access the file through the folder it's located in, and select to 'open with Archive Manager', I get another error-message;
```
[/home/jarlg/BIOS/sp40182.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/jarlg/BIOS/sp40182.exe or
          /home/jarlg/BIOS/sp40182.exe.zip, and cannot find /home/jarlg/BIOS/sp40182.exe.ZIP, period.

```Everything but this step seems to work. I can mount the file to the temporary directory, and even access it's contents from it's mounted location.

If it's any help,
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=321957&prodSeriesId=1839150&prodNameId=1839197&swEnvOID=1093&swLang=8&mode=2&taskId=135&swItem=ob-63512-1"> this]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=1839197&prodTypeId=321957&prodSeriesId=1839150&swLang=8&taskId=135&swEnvOID=1093#120")  is the link to my BIOS-download. 
  Beneath you'll also see the link to the BIOS-downloads section of the same page, perhaps I've downloaded the wrong file? :-?

[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=1839197&prodTypeId=321957&prodSeriesId=1839150&swLang=8&taskId=135&swEnvOID=1093#120](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=1839197&prodTypeId=321957&prodSeriesId=1839150&swLang=8&taskId=135&swEnvOID=1093#120)

Anyways, I'd be very grateful if I were to receive any advice or help here as to how my problem can be solved. Currently, my computer can reach horrific temperatures even when it's fan is going at full speed. I've heard this BIOS-upgrade should make the laptop more silent, and that is something I'd really like.

Thanks in advance, and please tell if you need more information or anything! :)

---

### Post by Harper45 on 2009-08-16
wats the problem with ur bios ??????

---

### Post by JarlG on 2009-08-16
I'm not sure if you are referring to me, but I might as well be on the safe side. :)

As I noted in the end of my post, the reason as to why I'd like to update my bios is the fact that people have experienced a more silent laptop after the update. This is something I would really like. :)

Again, thanks in advance!

---

### Post by ticket on 2009-09-19
Just like to add the results of my endeavours here.

I needed to upgrade the BIOS of a Dell Precision 340.  I opted for the CD method.  First of all, I downloaded the latest BIOS from the Dell website. It was called WS340A07.EXE. 

This was the 'non-packaged' version, which means it is not an archive, so no need to extract anything. The file is in fact the BIOS flash program together with the BIOS. In a DOS system, all you need to do is execute the file to flash the BIOS. 

As I don't have DOS, I built a bootable DOS CD using the instructions of this thread and with help from: 

[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

In my home directory I did:

```
mkdir bios
cd bios
copy FDOEM.144.gz to this directory
gunzip FDOEM.144.gz
``` 

There no need to do a 'modprobe loop' when using Jaunty (and if you do, you will get an error).  Next:

```
sudo mkdir /tmp/floppy
sudo mount -t vfat -o loop FDOEM.144 /tmp/floppy
sudo cp WS340A07.EXE /tmp/floppy
sudo umount /tmp/floppy
sudo mkisofs -o bootcd.iso -b FDOEM.144 FDOEM.144
```

This will have created the file bootcd.iso in ~/bios, with the BIOS executable WS240A07.EXE on it.
I burnt it to a cd, rebooted using the CD and from the DOS prompt A:\ ran the WS340A07.EXE.  

Worked fine!

Probably could avoid all those sudo's by doing a 'sudo su', but I wasn't sure if that would land me in a different directory. The commands I used are safe and worked perfectly.

PS. I think for older motherboards like mine, the DOS method is the safest.  I was thinking of using the dellBiosUpdate utility which requires 'rbu' to be supported by the motherboard. When I looked at the ini file that came with the BIOS hdr file for this method, I saw it was blacklisted - meaning unreliable for my brand of motherboard.

Thanks for this thread - very helpful and I have learned more about Linux!

---

### Post by sdowney717 on 2009-09-26
cp: writing `/tmp/floppy/ep43ds3l.bin': No space left on device

I was so close, It only worked the first time creating the iso. Now the device is full even on a reboot. I had to do it over since the downloaded exe file I copied would only run in windows and I extracted the bin and flash program 2 files, but cant wright to the device.

How do you start over clearing the device?

OK, if I "sudo rm /tmp/floppy/ the files I dont need"
then the space is freed up.

---

### Post by JdeP on 2009-11-11
Can anyone help? I'm pretty new to Ubuntu, and any help, stated in simple terms, would be very gratefully received.

Using Method 2 I get as far as this step:

sudo cp ~/NewBiosFiles/* /tmp/cdr

but I keep getting a "No such file or directory" error.
The BIOS file is called BIOS_v1.45.exe (for an Acer 5315). I've tried replacing "NewBiosFiles" with "BIOS_v1.45.exe"

I've also tried copying the BIOS_v1.45.exe file to the /tmp/cdr folder manually using Nautilus, but I run into another problem: the BIOS_v1.45.exe file is 1.4Mb, and Nautilus tells me I only have 1.3Mb free in the folder

Maybe I'm doing something really dumb, or maybe Acer are just making life difficult, as usual ...

(I've got a clean re-install of Karmic; no floppy drive; and I want to flash the BIOS because of a well-documented and widely-suffered problem with the fan not switching on to cool the CPU, causing the laptop to just shut down without warning)

---

### Post by ciscosurfer on 2009-11-11
> **JdeP said:**
> Can anyone help? I'm pretty new to Ubuntu, and any help, stated in simple terms, would be very gratefully received.

Using Method 2 I get as far as this step:

sudo cp ~/NewBiosFiles/* /tmp/cdr

but I keep getting a "No such file or directory" error.
The BIOS file is called BIOS_v1.45.exe (for an Acer 5315). I've tried replacing "NewBiosFiles" with "BIOS_v1.45.exe"

I've also tried copying the BIOS_v1.45.exe file to the /tmp/cdr folder manually using Nautilus, but I run into another problem: the BIOS_v1.45.exe file is 1.4Mb, and Nautilus tells me I only have 1.3Mb free in the folder

Maybe I'm doing something really dumb, or maybe Acer are just making life difficult, as usual ...

(I've got a clean re-install of Karmic; no floppy drive; and I want to flash the BIOS because of a well-documented and widely-suffered problem with the fan not switching on to cool the CPU, causing the laptop to just shut down without warning)@JdeP,

Here are my suggestions:
[LIST=1]
[*] **sudo cp ~/NewBiosFiles/* /tmp/cdr** means the following: copy all the new BIOS files to the /tmp/cdr directory (NewBiosFiles is pseudocode for your newly downloaded BIOS files found inside the executable after you extract it. So wherever you've extracted the BIOS files, this chunk of code is telling you to copy everything (the asterisk is a wildcard that matches everything)). It was a quick way of saying to copy all extracted files to /tmp/cdr directory. You may not need or want all of these files though. At the very least, the flashing utility and the new BIOS file need to be included when you copy to /tmp/cdr directory. If there are extraneous files inside the BIOS_v1.45.exe, this may help you in reducing the size footprint and allow you to stick with the 1.44 image rather than the suggested workaround when needing larger or more files by using the 2.88 image listed under SIZE CONTRAINTS.
[*]Do you have a dual-boot environment, Linux + Windows, for example? If so, boot to Windows and flash from there. Might save you a few headaches
[*]Do you know someone that is good with computers? If so, ask them to help you out; for all intents and purposes, this is not a beginner's tutorial.
[*]Does ACER have a flashing utility native to Linux? If so, try using it.
[*]You need to extract the executable file using unzip, for example. See my FOOTNOTES section at the bottom of the tutorial.
[*]The main issue you are experiencing is a size contraint issue. Please see my tutorial again and look under the heading SIZE CONSTRAINTS.
[*]There are althernative methods mentioned in my tutorial that allow you to go about flashing your BIOS is a variety of ways. Perhaps you can try using Flashrom, a native-to-Linux catch-all utility (it may or may not work for you, but it's worth a shot...please check their web site to see if your board is supported and/or workarounds are available).
[*]Another solution might be to get a USB Floppy drive. I don't really recommend this as it will cost you money unless you borrow one from a friend. Then you can try Method 1, the easiest of all methods.  Remember though about size constraints! Using the CD Method or the GRUB method gets around this issue entirely.
[*]I would lastly suggest that you carefully read the tutorial again, top to bottom, taking into account any and all tips and warnings.
[/LIST]
Good luck!

---

### Post by kio_http on 2009-11-11
No need for me!):P):P

My bios updates from bios image in USB flash drive or cd from the bios menu itself.:KS

---

### Post by JdeP on 2009-11-13
Dear ciscosurfer,

Many thanks for your extensive help. I've been trying all sorts of things before asking for help again. Unfortunately I'm still stuck. 

If you are trying to keep the How To up-to-date you would help other people, and hopefully me too, if you provide some info under Method 3:GRUB about using GRUB2 -- as far as I have been able to understand, the "menu.lst" file no longer exists in GRUB2, so the last two segments of your instructions (from "sudo vim /boot/grub/menu.lst") won't work

Best wishes

---

### Post by ciscosurfer on 2009-11-13
> **JdeP said:**
> Dear ciscosurfer,

Many thanks for your extensive help. I've been trying all sorts of things before asking for help again. Unfortunately I'm still stuck. 

If you are trying to keep the How To up-to-date you would help other people, and hopefully me too, if you provide some info under Method 3:GRUB about using GRUB2 -- as far as I have been able to understand, the "menu.lst" file no longer exists in GRUB2, so the last two segments of your instructions (from "sudo vim /boot/grub/menu.lst") won't work

Best wishesYou are correct: Method 3 is geared towards original GRUB users (pre-Karmic). The best advice I can give you regarding Method 3 + GRUB 2 is to check the Tips and Warnings section, number 6. Unfortunately, GRUB 2 is a bit more involved than its predecessor in the way it functions. If that seems too daunting (it's not really all that bad once you read up on how the latest GRUB works) I would suggest trying to use a larger FreeDOS image. The 2.88MB image, which is a standard image and not a bare OEM image, should allow you to complete the tutorial due to its larger size. Here is a link to the 2.88MB image ([http://www.fdos.org/bootdisks/autogen/FDSTD.288.gz](http://www.fdos.org/bootdisks/autogen/FDSTD.288.gz)). Once downloaded, and after you have extracted the file and mounted it to a location of your choosing, you can remove the fdos directory and both umb* files (umbpci.sys and umbpci.txt) to free up more space. At that point, the image is essentially like the 1.44MB image you downloaded previously, just twice as large--which should help accommodate your new BIOS image + related files. It is also helpful to note that once you've downloaded your new BIOS image + related files, you may want to take a look inside it (by unzipping the .exe) and checking to see if these files come in under the 2.88MB mark collectively. If they don't, and if you can't remove some of these files without sacrificing the ability to use them as a flashing service, then I'm afraid even the 2.88MB FreeDOS image will also not suffice.

Continued good luck!

---

### Post by nss0000 on 2009-11-13
> **gaxxter said:**
> Hi, I can't be bothered with the hassle to update manually so get a biosflash company to do my work 4 me, got a new chip with latest bios and use the old one as a back up for future failure!!! hope not :)

Yes ... the risk of hosing a $200 mobo and trashing 6-mo of sys-integration effort far out-weighs any "mental" satisfaction gained by jumping_thru convoluted BIOS_flash hoops. 

I didn't exactly count, but a guess is - start.to.finish - BIOS_flash requires several hundred key_strokes performed in_order without ONE (1) mistake. I'm sure some-few retros enjoy the jumping ....

---

### Post by crankyadm1n on 2009-11-14
Or save yourselfs alot of hassle and use flashrom from the coreboot guys.  [http://www.coreboot.org/flashrom](http://www.coreboot.org/flashrom)

Flash your BIOS without having to leave or reboot linux.

:D

---

### Post by ciscosurfer on 2009-11-14
> **nss0000 said:**
> Yes ... the risk of hosing a $200 mobo and trashing 6-mo of sys-integration effort far out-weighs any "mental" satisfaction gained by jumping_thru convoluted BIOS_flash hoops. 

I didn't exactly count, but a guess is - start.to.finish - BIOS_flash requires several hundred key_strokes performed in_order without ONE (1) mistake. I'm sure some-few retros enjoy the jumping ....Yes, well, it's not for the faint of heart, as I've clearly stated multiple times in the tutorial and throughout this thread. You should use (or not use) any method or action you see fit. This includes having someone else flash your BIOS for you, or ignoring updates related to your BIOS entirely.

If flashing your BIOS won't give you any significant gains or improvements as indicated by your manufacturer, then I agree that you must carefully weigh your options if presented with an intricately configured system and the possibility to flash your BIOS. No one likes hosing their system. This is especially relevant in systems that require as much uptime as possible (data centers, corporate environments, et cetera).

Tread carefully :).

> **crankyadm1n said:**
> Or save yourselfs alot of hassle and use flashrom from the coreboot guys.  [http://www.coreboot.org/flashrom](http://www.coreboot.org/flashrom)

Flash your BIOS without having to leave or reboot linux.

:DFlashrom has decent, albeit limited, support as stated previously. It is given as an option in the tutorial; use (or don't use) whichever method works best for you.

---

### Post by dimeotane on 2009-11-17
This how-to should also include how to creating a bootable USB with DOS for flashign the BIOS on netbooks without a CD drive or floppy.

  Perhaps this method should be incorporated in this how to guide? 

Here is one example: [http://www.aselabs.com/articles.php?id=243](http://www.aselabs.com/articles.php?id=243)


Also flashing the BIOS in Dells maybe should be added: [https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)

---

### Post by Alex22 on 2009-11-23
Hello Everybody

Unfortunatelly, I haven't got a CD recorder. 
So i tried method 3, but i failed. In GRUB boot menu, when i choose this prepared option, it only says "No such file". 
I double checked the correctness of filenames&paths. :[]

No Windows and floppy access neither.


I have one question: Can i run this DOS programme (prepared by mainboard manufacturer) from DosBox emulator - right from the Gnome panel?
Coz i cannot transfer the sys to usb stick, there is no "sys" command in DosBox.

I have ECS K7S5A mainboard.

Thanks, Alex

P.S. Dimeotane, Dell howto is mentioned on 2 or 3 page.


ADDED: I tried something more. 

1) I tried this:

```
If you can boot from USB you better go by that;
wget http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz
tar xzf FDOEM.144.gz
dd if=FDOEM.14 of=/dev/$USB #!!!Will delete all files on $USB

Mount usb, (deplug, plugin)
unzip *BIOS_Dos ; cp *BIOS_Dos/* $USB
Umount usb ! umount /dev/$USB.

Reboot, start from usb, A:> flash… (start flash tool from your manufacturer ).

MKN
```

And the stick boots, says "FreeDOS" and freezes (maybe it's FreezeDOS ;)).
Maybe i should dd zeros the MBR in this method?


2) And also tried the method linked by Dimeotane, but Dosemu says, it cannot acces my stick (GEO data of it).

---

### Post by Zyrtec on 2010-01-06
Sorry for bumping the topic, but I may as well post it here rather than making a new one. 

I have a few questions concerning all of this. I'm running Ubuntu 9.10 64bit. I want to flash my BIOS because I've read that some people with the motherboard I purchased said that their CPUs were overclocking out of the box until they flashed the BIOS. I'm not entirely sure (because I don't really know anything about overclocking), but my Processor is running pretty hot compared to what other people with the same processor say... It's running at about 48-50 degrees C when I boot up and look at the temperature in the BIOS. I used a couple of commands in the terminal to check on info about the processor, and it says that all 4 cores are running at 800MHz... so 4 x 800 = 3.2GHz  (I dunno if this is how it works, lol...)  when my processor is rated at 2.8GHz. 


So that's my reasoning for wanting to flash the BIOS, even though I would classify as the "faint of  heart". So my main question is, how would I go about backing up my current BIOS in case anything does go wrong? I haven't tried any of the methods posted here yet to flash the BIOS... I wanted to back things up first.

***I don't have a floppy drive!

---

### Post by iponeverything on 2010-01-06
> **Zyrtec said:**
> Sorry for bumping the topic, but I may as well post it here rather than making a new one. 

I have a few questions concerning all of this. I'm running Ubuntu 9.10 64bit. I want to flash my BIOS because I've read that some people with the motherboard I purchased said that their CPUs were overclocking out of the box until they flashed the BIOS. I'm not entirely sure (because I don't really know anything about overclocking), but my Processor is running pretty hot compared to what other people with the same processor say... It's running at about 48-50 degrees C when I boot up and look at the temperature in the BIOS. I used a couple of commands in the terminal to check on info about the processor, and it says that all 4 cores are running at 800MHz... so 4 x 800 = 3.2GHz  (I dunno if this is how it works, lol...)  when my processor is rated at 2.8GHz. 


So that's my reasoning for wanting to flash the BIOS, even though I would classify as the "faint of  heart". So my main question is, how would I go about backing up my current BIOS in case anything does go wrong? I haven't tried any of the methods posted here yet to flash the BIOS... I wanted to back things up first.

***I don't have a floppy drive!


48-50 degrees C

Is quite cool and the 2.8GHz. is per core.

The 800Mhz because of speedstep lowering the clock, because the processor is does not have enough work. 

I don't think you need to mess with your bios, unless you just like taking chances..

---

### Post by Zyrtec on 2010-01-06
Well, other people are saying that their same processors are idling at around 35 degrees C, and go between 45-50 under load. When looking at mine, it's 45-50 all the time -- unless looking at the BIOS would be considered "under load". 

I've got four case fans, the CPU fan and heatsink, and it's not sitting on the floor or anything :confused:

---

### Post by iponeverything on 2010-01-06
do what ya gotta do.

---

### Post by Zyrtec on 2010-01-06
So yeah, can anyone tell me how to backup the BIOS before I even attempt to flash it? :-?

---

### Post by iponeverything on 2010-01-07
I have a single core 1.7Ghz low power mobile cpu that rarely drop below 55c, the fan does not even come on till it hits 65c.

Your running a quad core desktop? cpu at 2.8Ghz and you think 50c is hot? If you want your cpu running at 35c, try changing your cooling method to liquid instead of air. You can't really compare other peoples temp's to your unless you are looking at the same cpu (not just same Ghz) but the same part# and same cooling method -- and even then you don't know the ambient temperature of room that person your comparing to is at. He might be in meat locker or at McMurdo.

---

### Post by Zyrtec on 2010-01-07
Yeah, I know what you're saying, but I tried looking up documentation to see what the "high" temp was for this processor, and it said something like 60-65C which isn't too far off from what I'm idling at. I would think that they'd design the processors so that they're at least, 20 or more below their critical temperature at end-user conditions. 

I still want to flash my BIOS though!

---

### Post by LinLux451 on 2010-01-24
Hey, I think this thread is a little outdated. While Hardy is probably one of the best OS's ever created in the history of the universe (even beating HAL from 2001 Space Odyssey) I had to upgrade to Karmic for ath9k wireless support which is still a little finicky at times. Oh well. I'm using a clean Karmic, which uses grub2 and a noneditable .cfg file. I think I can piece together how to add a boot image to the menu, but my end file from extracting the zip into the /tmp/floppy folder is too much of a chunker! My zip file off of Gateway website it 4.0MB (Wayyy to big for a floppy.) Thus I always get CRC checksum errors and diskfulls. If anyone would like to help me it would be excellent. My current BIOS is older then Moses and has about 3 options... Maybe manufacturer's should should start shipping these things updated... NAH! Anyway. I have a  Gateway NV52 stuffed with 64 Karmic Koala's..haha..ha. If you would like any outputs just ask. Thanks in advance!

---

### Post by ciscosurfer on 2010-01-25
> **LinLux451 said:**
> [...]I'm using a clean Karmic, which uses grub2 and a noneditable .cfg file. I think I can piece together how to add a boot image to the menu, but my end file from extracting the zip into the /tmp/floppy folder is too much of a chunker! My zip file off of Gateway website it 4.0MB (Wayyy to big for a floppy.) Thus I always get CRC checksum errors and diskfulls.[...]The GRUB2 grub.cfg file is a read-only file and should not be edited directly. I've provided a link under "Tips and Warnings" on the first page of my instructions to a thread on UF that you should read in its entirety if you want to mess with GRUB2. Additional links have also been provided for larger image sizes. The flashrom utility or using unetbootin are also other possible options for you.

---

### Post by Ayers on 2010-02-08
elijah@elijah-laptop:~$ flashrom
flashrom v0.9.1-r706
ERROR: Could not get I/O privileges (Operation not permitted).
You need to be root.
elijah@elijah-laptop:~$ 



I get this message everytime

---

### Post by ciscosurfer on 2010-02-08
> **Ayers said:**
> elijah@elijah-laptop:~$ flashrom
flashrom v0.9.1-r706
ERROR: Could not get I/O privileges (Operation not permitted).
[COLOR=Red] You need to be root.[/COLOR]
elijah@elijah-laptop:~$You need to be root. Try running with sudo like```
sudo flashrom
```Reading the man pages or [documentation online]("http://flashrom.org/Flashrom") is probably a good idea as well```
man flashrom
```

---

### Post by ambush_xx on 2010-02-11
How do i edit the grub menu in 9.10

I tried copying the code given on the opening post on the grub.d folder, but it did not work. Could somebody post a woking code.

---

### Post by ciscosurfer on 2010-02-11
> **ambush_xx said:**
> How do i edit the grub menu in 9.10

I tried copying the code given on the opening post on the grub.d folder, but it did not work. Could somebody post a woking code.First page > Tips and Warnings > GRUB 2

---

### Post by cguy on 2010-03-20
The CD way worked like a charm!
I'm impressed every day by the genius of opensource developers. :D

Thanks a million!


Thing learned today: don't always trust changelogs. Updating the BIOS fixed a nasty problem with the SATA harddrives that wasn't listed in the changelog (they were not recognized upon reboot), so I shouldn't have had a reason to flash it.
Phew!
That was exasperating me.

---

### Post by Herman on 2010-04-04
> 
Quote:
Originally Posted by ambush_xx View Post
How do i edit the grub menu in 9.10

I tried copying the code given on the opening post on the grub.d folder, but it did not work. Could somebody post a woking code.
First page > Tips and Warnings > GRUB 2
:) Hello there, ciscosurfer,
I'm sorry but I wasn't able to find out how to boot the biosupdate.img from the page you linked to there. Maybe I didn't read enough.

After some googling and a few experiments, I think I have found out the very easiest way to do it with GRUB2. 
Since we're probably only planning on doing this once, rather that taking the time to make a permanent menu entry, it's easiest to press the 'c' key from the GRUB2 menu for GRUB's Command Line Interface and boot with live commands.

The commands I used were:
```
linux16 (hd0,1)/boot/memdisk
initrd16 (hd0,1)/boot/biosupdate.img
boot
```... and thank you for your excellent how-to! 
Regards, Herman ):P

---

### Post by likemindead on 2010-05-19
I have a Lenovo 3000 N100 and I don't think it's supported by CoreBoot, which is the way I really hoped to go.

```
likemindead@likemindead-laptop:/$ sudo lshw
likemindead-laptop        
    description: Notebook
    product: 07686EU
    vendor: LENOVO
    version: 3000 N100
    serial: L3D9625
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=oem-specific chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=B3D43438-CC97-11DA-9F7E-000FB0C96821
  *-core
       description: Motherboard
       product: MPAD-MSAE Customer Reference Boards
       vendor: LENOVO
       physical id: 0
       version: Not Applicable
       serial: 41W1220Z1ZBUA64S3KH
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 61ET16WW (03/14/06)
          size: 100KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           T2300  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          slot: U2E1
          size: 1GHz
          capacity: 2048MHz
          width: 32 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 2MiB
             capabilities: burst external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 32 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 32 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 11
          slot: System board or motherboard
          size: 2GiB
          capacity: 3GiB
        *-bank:0
             description: SODIMM DDR Synchronous
             physical id: 0
             slot: M1
             size: 1GiB
             width: 32 bits
        *-bank:1
             description: SODIMM DDR Synchronous
             physical id: 1
             slot: M2
             size: 1GiB
             width: 32 bits
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.14.8
          serial: 0000-06E8-0000-0000-0000-0000
          size: 1667MHz
          capacity: 1667MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:b0080000-b00fffff ioport:1800(size=8) memory:c0000000-cfffffff(prefetchable) memory:b0040000-b007ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:b0100000-b017ffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:b0000000-b0003fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:3000(size=4096) memory:84000000-841fffff memory:84200000-843fffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:4000(size=4096) memory:b0200000-b02fffff memory:84400000-845fffff(prefetchable)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 02
                serial: 00:13:02:4a:15:b1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11abg
                resources: irq:26 memory:b0200000-b0200fff
        *-usb:0
             description: USB Controller
             product: N10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1880(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:b0004000-b00043ff
        *-pci:2
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:2000(size=4096) memory:b0300000-b03fffff memory:80000000-83ffffff(prefetchable)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:05:01.0
                logical name: eth0
                version: 10
                serial: 00:0f:b0:c9:68:21
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
                resources: irq:21 ioport:2000(size=256) memory:b0300000-b03000ff
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:05:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:b0301000-b0301fff ioport:2400(size=256) ioport:2800(size=256) memory:80000000-83ffffff(prefetchable) memory:88000000-8bffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 6
                bus info: pci@0000:05:06.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
                resources: irq:22 memory:b0300800-b0300fff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.1
                bus info: pci@0000:05:06.1
                version: 19
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:23 memory:b0300400-b03004ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 6.2
                bus info: pci@0000:05:06.2
                version: 0a
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: driver=ricoh-mmc latency=0
                resources: irq:7 memory:b0302000-b03020ff
           *-generic:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 6.3
                bus info: pci@0000:05:06.3
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
                resources: memory:b0302400-b03024ff
           *-generic:3 UNCLAIMED
                product: Illegal Vendor ID
                vendor: Illegal Vendor ID
                physical id: 6.4
                bus info: pci@0000:05:06.4
                version: ff
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master vga_palette cap_list
                configuration: latency=255 maxlatency=255 mingnt=255
                resources: memory:b0302800-b03028ff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18b0(size=16)
           *-disk
                description: ATA Disk
                product: TOSHIBA MK8032GS
                vendor: Toshiba
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: AS11
                serial: 569D2007T
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0008a314
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 4642ad5b-0732-4cb7-b65c-fc3c58bda5a7
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2010-04-23 09:46:16 filesystem=ext4 lastmountpoint=/&#65533;&#65533;P&#65533;t&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;n&#65533;u^ &#65533;U/&#65533;&#65533;&#65533;n&#65533;~!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;t&#65533;&#65533;&#65533;&#65533;&#65533;n&#65533;&#65533;n&#65533;a modified=2010-05-17 08:56:01 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2010-05-18 11:49:56 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 1427MiB
                   capacity: 1427MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1427MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GMA-4082N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: HA01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18c0(size=32)
  *-remoteaccess UNCLAIMED
       vendor: Intel
       physical id: 1
       capabilities: inbound
likemindead@likemindead-laptop:/$ 

```

Should I give this tutorial a shot?

---

### Post by Moozillaaa on 2010-05-19
sudo cp ~/NewBiosFiles/* /tmp/cdr


What goes in place of NewBiosFiles ?

My extracted file contained a folder in which there are 3 files - ROM file, batch file, and application file...

Is it 'TitleOfFolder'??? In my case, Motherboard_AMD_SocketAM2_A7DA_BIOS_81BF1PO9 ???

---

### Post by ciscosurfer on 2010-05-19
> **likemindead said:**
> [...] Should I give this tutorial a shot?If you can, I would suggest using a native Linux updater if Lenovo provides one. Otherwise, make sure you read and understand what you are getting into before beginning the process.

The later posts in this thread address various ways of utilizing GRUB2 to update your BIOS -- I would suggest this method if you are coming up against size constraints (I've found it to be the easiest way and it's slick). The first page of the thread also has GRUB2 and size constraint links as well as other info worth taking the time to read. 

Good luck!

---

### Post by ciscosurfer on 2010-05-19
> **Moozillaaa said:**
> sudo cp ~/NewBiosFiles/* /tmp/cdr

What goes in place of NewBiosFiles ? [...]
Mentioned on page 1 under method 1 and method 2:

> Note: "NewBiosFiles" listed below is pseudocode for the extracted location of the new BIOS image + related files that you just downloaded


---

### Post by Moozillaaa on 2010-05-19
> **ciscosurfer said:**
> Mentioned on page 1 under method 1 and method 2:

Yes - I saw that.

I presumed that the 'extracted location' was the folder in which the 3 files are.

But no? The 'extracted location' is the entire filepath? OR, is the folder name INCLUDED after 'Desktop'???

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157594&d=1274323065[/IMG]

---

### Post by ciscosurfer on 2010-05-20
> **Moozillaaa said:**
> Yes - I saw that.

I presumed that the 'extracted location' was the folder in which the 3 files are.

But no? The 'extracted location' is the entire filepath? OR, is the folder name INCLUDED after 'Desktop'???Unless you change directories to that folder, then the full absolute path would be required.

If the extracted zip folder resides on your Desktop and Motherboard_AMD_SocketAM2_A7DA_BIOS_81BF1PO9 is the name of this folder, and the three files you mentioned are contained in that folder, then the correct syntax should be```
sudo cp ~/Desktop/Motherboard_AMD_SocketAM2_A7DA_BIOS_81BF1PO9/*  /tmp/cdr
[COLOR="Red"]#this line above is the same as this line below[/COLOR]
sudo cp /home/chuckbhp/Desktop/Motherboard_AMD_SocketAM2_A7DA_BIOS_81BF1PO9/*  /tmp/cdr
```If I've misunderstood your question, let me know.

---

### Post by Moozillaaa on 2010-05-22
I still cannot copy these files to the /tmp/dir

What is my incorrect syntax here?

> chuckbhp@chuckbhp-laptop:~$ gunzip FDOEM.144.gz
gzip: FDOEM.144 already exists; do you wish to overwrite (y or n)? y

chuckbhp@chuckbhp-laptop:~$ mkdir /tmp/cdr
mkdir: cannot create directory `/tmp/cdr': File exists

chuckbhp@chuckbhp-laptop:~$ sudo mount -t vfat -o loop FDOEM.144 /tmp/cdr

chuckbhp@chuckbhp-laptop:~$ sudo cp ~/Desktop/Motherboard_AMD_SocketAM2_A7DA_BIOS_81BF1PO9/*  /tmp/cdr
cp: cannot stat `/home/chuckbhp/Desktop/Motherboard_AMD_SocketAM2_A7DA_BIOS_81BF1PO9/*': No such file or directory

chuckbhp@chuckbhp-laptop:~$ sudo cp ~/Desktop/Motherboard\AMD\SocketAM2\A7DA\BIOS\81BF1P09
cp: missing destination file operand after `/home/chuckbhp/Desktop/MotherboardAMDSocketAM2A7DABIOS81BF1P09'
Try `cp --help' for more information.

chuckbhp@chuckbhp-laptop:~$ sudo cp ~/Desktop/Motherboard\AMD\SocketAM2\A7DA\BIOS\81BF1P09/*
cp: missing destination file operand after `/home/chuckbhp/Desktop/MotherboardAMDSocketAM2A7DABIOS81BF1P09/*'
Try `cp --help' for more information.

chuckbhp@chuckbhp-laptop:~$ sudo cp ~/Desktop/Motherboard\AMD\SocketAM2\A7DA\BIOS\81BF1P09/* /tmp/cdr
cp: cannot stat `/home/chuckbhp/Desktop/MotherboardAMDSocketAM2A7DABIOS81BF1P09/*': No such file or directory

chuckbhp@chuckbhp-laptop:~$ sudo cp /home/chuckbhp/Desktop/Motherboard\AMD_SocketAM2\A7DA\BIOS\81BF1PO9/*  /tmp/cdr
cp: cannot stat `/home/chuckbhp/Desktop/MotherboardAMD_SocketAM2A7DABIOS81BF1PO9/*': No such file or directory

chuckbhp@chuckbhp-laptop:~$ sudo cp ~/home/chuckbhp/Desktop/Motherboard\AMD\SocketAM2\A7DA\BIOS\81BF1P09 /tmp/cdr
cp: cannot stat `/home/chuckbhp/home/chuckbhp/Desktop/MotherboardAMDSocketAM2A7DABIOS81BF1P09': No such file or directory

chuckbhp@chuckbhp-laptop:~$ sudo cp ~/Desktop/Motherboard\AMD\SocketAM2\A7DA\BIOS\81BF1P09 /tmp/cdr
cp: cannot stat `/home/chuckbhp/Desktop/MotherboardAMDSocketAM2A7DABIOS81BF1P09': No such file or directory

chuckbhp@chuckbhp-laptop:~$ sudo cp ~/home/chuckbhp/Desktop/Motherboard_AMD_SocketAM2_A7DA_BIOS_81BF1P09 /tmp/cdr
cp: cannot stat `/home/chuckbhp/home/chuckbhp/Desktop/Motherboard_AMD_SocketAM2_A7DA_BIOS_81BF1P09': No such file or directory

chuckbhp@chuckbhp-laptop:~$ 


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157923&d=1274570138[/IMG]

---

### Post by ciscosurfer on 2010-05-22
> **Moozillaaa said:**
> [...]What is my incorrect syntax hereCommand line tab completion and character escape sequences are beyond the scope of this tutorial. Suffice to say, you either need to escape those backslahes with additional backslashes or use command completion via the tab key to finish out the line. To get around this entirely you can rename the **Motherboard\AMD\SocketAM2\A7DA\BIOS\81BF1P09** directory to something easy like **biosfiles** by right-clicking the directory on your Desktop and choosing Rename.

---

### Post by Moozillaaa on 2010-05-22
I re-named the folder to 'Motherboard', and modded filepath, and got to the next step...

sudo cp ~/Desktop/Motherboard/* /tmp/cdr[FONT=Verdana]

What will that make [COLOR=Red]THIS

[/COLOR][/FONT]> mkisofs -o [COLOR=Red]newBIOS[/COLOR].iso -b FDOEM.144 FDOEM.144
and THIS:
cdrecord -v [COLOR=Red]newBIOS[/COLOR].iso

[COLOR=Red]Motherboard[/COLOR].iso?



And will 'cdrecord' become 'Brasero'?

---

### Post by ciscosurfer on 2010-05-23
> **Moozillaaa said:**
> I re-named the folder to 'Motherboard', and modded filepath, and got to the next step...

sudo cp ~/Desktop/Motherboard/* /tmp/cdr[FONT=Verdana]

What will that make [COLOR=Red]THIS[/color]

> mkisofs -o [COLOR="Red"]newBIOS.iso[/COLOR] -b FDOEM.144 FDOEM.144
and THIS:
cdrecord -v [COLOR="red"]newBIOS.iso[/COLOR]

[/FONT][COLOR=Red]Motherboard[/COLOR].iso?

And will 'cdrecord' become 'Brasero'?The options for genisoimage (mkisofs) can be found in its man page```
man genisoimage
```or```
genisoimage -help
```The options (or flags) on this line```
mkisofs -o newBIOS.iso -b FDOEM.144 FDOEM.144

```means:
```
SYNOPSIS
       genisoimage [options] [-o filename] pathspec [pathspec ...]

``````
-o filename
              Specify  the  output  file for the the ISO9660 filesystem image.
              This can be a disk file, a tape  drive,  or  it  can  correspond
              directly  to the device name of the optical disc writer.  If not
              specified, stdout is used.  Note that the output can also  be  a
              block  device  for  a  regular disk partition, in which case the
              ISO9660 filesystem can be mounted normally to verify that it was
              generated correctly.
``````
-b eltorito_boot_image
              Specifies the path and filename of the boot  image  to  be  used
              when  making  an El Torito bootable CD for x86 PCs. The pathname
              must be relative to the source path  specified  to  genisoimage.
              This  option  is required to make an El Torito bootable CD.  The
              boot image must be exactly 1200 kB, 1440  kB  or  2880  kB,  and
              genisoimage  will use this size when creating the output ISO9660
              filesystem.  The PC BIOS will use the image to emulate a  floppy
              disk,  so the first 512-byte sector should contain PC boot code.
              This will work, for example, if the boot image is  a  LILO-based
              boot floppy.

              If  the  boot image is not an image of a floppy, you need to add
              either -hard-disk-boot or -no-emul-boot.  If the  system  should
              not boot off the emulated disk, use -no-boot.

              If -sort has not been specified, the boot images are sorted with
              low priority (+2) to the beginning of the medium.  If you  don't
              like  this,  you need to specify a sort weight of 0 for the boot
              images.
```So this line```
mkisofs -o newBIOS.iso -b FDOEM.144 FDOEM.144
```means:

Create an El Torito-like bootable ISO9660 image called newBIOS.iso from the FreeDOS image that was modified to include the new BIOS image. Once this line is called, you can use whatever burning program you see fit: k3b, brasero, cdrecord. If you use brasero remember you are wanting to burn an image. The name newBIOS.iso is arbitrary and unrelated to the name of directory that contained your new BIOS image files. You can call it frodo.iso if you want.

---

### Post by deepclutch on 2010-06-11
Hello ,

I've a Asus P5GC-MX/1333.I wanted to backup current bios image as *.rom file booting with memdisk and floppy.img(grub2) .
Booted Successfully and I invoked the command(afudos) to make a backup of current BIOS.rom .

"DIR" Command shows the backed up bios image is there.but ,once I exit the freedos environment ,I lose it(understandably).
Is there  a way that I can backup the old bios.rom to Hard disk  ?

---

### Post by ciscosurfer on 2010-06-11
> **deepclutch said:**
> Hello ,

I've a Asus P5GC-MX/1333.I wanted to backup current bios image as *.rom file booting with memdisk and floppy.img(grub2) .
Booted Successfully and I invoked the command(afudos) to make a backup of current BIOS.rom .

"DIR" Command shows the backed up bios image is there.but ,once I exit the freedos environment ,I lose it(understandably).
Is there  a way that I can backup the old bios.rom to Hard disk  ?This [link]("http://support.asus.com/search/search.aspx?keyword=p5gc-mx/1333&SLanguage=en-us") provided me with two places to look on the ASUS site for information and downloads. It would seem there is a native Linux updater you can use, allowing you to effectively bypass all methods I list on the first page of this thread. If you use the native Linux utility, I would then assume you should be able to save the backup locally to your hard disk (and then onto a floppy, a USB flash drive, a CD, or some other medium). If that fails for some reason, you can try using the flashrom utility I mention on the first page. I believe there is functionality built into the flashrom utility to allow you to make a backup of your BIOS.

---

### Post by deepclutch on 2010-06-12
@ciscosurfer:I already saw that.For Linux downloads ,they provide the same dos utility "afudos".
--
If I press ctrl+alt+delete ,the system restarts;but does not save the oldbios.rom into the floppy.I think "backup" is the dos command to be  used to copy into floppy image which is unfortunately not present in the FDOEM or FDSTD file. :(
--
I've another doubt:
My BIOS Version is 0312 -oldest version.and the latest is 0413 .Do I need to upgrade to successive versions or Can I directly upgrade to the latest?

Thanks.

---

### Post by ciscosurfer on 2010-06-12
> **deepclutch said:**
> @ciscosurfer:I already saw that.For Linux downloads ,they provide the same dos utility "afudos".
--
If I press ctrl+alt+delete ,the system restarts;but does not save the oldbios.rom into the floppy.I think "backup" is the dos command to be  used to copy into floppy image which is unfortunately not present in the FDOEM or FDSTD file. :(
--
I've another doubt:
My BIOS Version is 0312 -oldest version.and the latest is 0413 .Do I need to upgrade to successive versions or Can I directly upgrade to the latest?

Thanks.Are you reading the manual that came with the motherboard or that you can download from the ASUS site? The manual -- starting in section 2.1 -- describes multiple methods of going about the process of backing up the current BIOS. One method describes backing up to a floppy using the following systax [section 2.1.3 in the manual] The floppy should not be write-protected and at least 1024K should be free to make a copy```
afudos /o[filename]
```You need to read this information in the manual; there is more there that you need to read. There is information there also about CrashFree BIOS 2, a recovery BIOS. I recommend you read that.

There is no need to incrementally update your BIOS through multiple versions; the latest should be fine.

---

### Post by deepclutch on 2010-06-12
yup,I've already done that.afudos /oOLDBIOS1.rom   is the command that I ran it backed up the BIOS(Atleast to the RAM).But ,what happens  is ,the freedos floppy image I boot into ,cannot save the backed up BIOS.rom.it is lost immediately after I restart.
"dir" command shows:
OLDBIOS1.rom 
^^^but ,what I meant is ,it is cached in the memory of the system.the fdos image  ,is read only ,I presume;since ,It cannot save the changes.
will update later.

---

### Post by ciscosurfer on 2010-06-13
> **deepclutch said:**
> yup,I've already done that.afudos /oOLDBIOS1.rom   is the command that I ran it backed up the BIOS(Atleast to the RAM).But ,what happens  is ,the freedos floppy image I boot into ,cannot save the backed up BIOS.rom.it is lost immediately after I restart.
"dir" command shows:
OLDBIOS1.rom 
^^^but ,what I meant is ,it is cached in the memory of the system.the fdos image  ,is read only ,I presume;since ,It cannot save the changes.
will update later.Maybe try the floppy method if you want to write a backup file to disk. You could also try Herman's method; don't know if you'll be sandboxed in /boot or otherwise unable to access any other directory. It's worth a shot, though.

Herman's post [http://ubuntuforums.org/showpost.php?p=9073538&postcount=120](http://ubuntuforums.org/showpost.php?p=9073538&postcount=120)

---

### Post by ciscosurfer on 2010-06-13
> **Herman said:**
> :) Hello there, ciscosurfer,
I'm sorry but I wasn't able to find out how to boot the biosupdate.img from the page you linked to there. Maybe I didn't read enough.

After some googling and a few experiments, I think I have found out the very easiest way to do it with GRUB2. 
Since we're probably only planning on doing this once, rather that taking the time to make a permanent menu entry, it's easiest to press the 'c' key from the GRUB2 menu for GRUB's Command Line Interface and boot with live commands.

The commands I used were:
```
linux16 (hd0,1)/boot/memdisk
initrd16 (hd0,1)/boot/biosupdate.img
boot
```... and thank you for your excellent how-to! 
Regards, Herman ):P[COLOR=Black]*Excellent method! Thanks for posting your experience!*[/COLOR]

---

### Post by deepclutch on 2010-06-13
I used the same lines **Herman**'s post mentioned to boot DOS.It is Mentioned Here[B]:
[/B][http://syslinux.zytor.com/wiki/index.php/MEMDISK#What_is_MEMDISK.3F](http://syslinux.zytor.com/wiki/index.php/MEMDISK#What_is_MEMDISK.3F)[B]
--
[/B]Anyways ,I successfully Flashed BIOS to the latest Version the best and easy way- using **flashrom** Utility(Linux native).
Motherboard is a ASUS P5GC-MX/1333(Intel 945GC chipset) with very old BIOS version(0312) flashed to the latest version(0413).
Chipset - Winbond 25x40

 flashrom-0.9.2-r1043 version is used(Debian binary built from source).
Great tool!
I had already set up freedos image with afudos tool booted using syslinux memdisk via grub2.Compared to that ,this tool serves great.  :D
[http://www.flashrom.org](http://www.flashrom.org)

Thanks!

---

### Post by ciscosurfer on 2010-06-13
@deepclutch,

Glad to hear flashrom worked for you!

---

### Post by wayward4now on 2010-06-18
I'm trying to use your CD method, but when I try to copy the new rom image and the exe file to install it, 
[FONT=monospace]wayward4now@iam:~/Downloads/tmp$ sudo cp k8u939.f5 /tmp/cdr
cp: writing `/tmp/cdr/k8u939.f5': No space left on device

I can't imagine not having enough space? Please help. Ric

[/FONT]

---

### Post by ciscosurfer on 2010-06-18
> **wayward4now said:**
> I'm trying to use your CD method, but when I try to copy the new rom image and the exe file to install it, 
[FONT=monospace]wayward4now@iam:~/Downloads/tmp$ sudo cp k8u939.f5 /tmp/cdr
cp: writing `/tmp/cdr/k8u939.f5': No space left on device

I can't imagine not having enough space? Please help. Ric

[/FONT]The FreeDOS image is 1.44MB so if it's mounted to the /tmp/cdr directory, then that's the amount of space you have to work with on /tmp/cdr. You can try a larger image size as listed under 'size contraints' on the first page or another method (also listed there). Here's a direct link to the 2.88MB image: ```
wget http://www.fdos.org/bootdisks/autogen/FDSTD.288.gz
```To be clear, the files you are trying to copy over exceed 1.44MB, which is the amount of space you are working with, not the size of a 650+ MB CD (that's just the max size/medium you are using to store it). Remember, with this method, you are constrained to the size of the FreeDOS image so your files must come in under this limit (or 2.88 MB provided above) or you must use another method like using GRUB. Your other option would be to use flashrom.

---

### Post by sergiomb on 2010-06-27
When you got a 5273 KB file to flash , this method fails , because , floppy disk are limit to 1.44 (or 2.88 ).
So , I will share the solution that I used ...
with a pen USB , format pen usb let say /dev/sdb with a simple mkfs.vfat /dev/sb1  and use qemu.
boot floppy  FDOEM.144 
qemu -hda /dev/sdb -fda FDOEM.144 -boot a
in qemu do: 
sys.com c:
you also may need do: 
fdisk /mbr 1 (for this use odin ( [http://odin.fdos.org/odin2005/odin1440.img](http://odin.fdos.org/odin2005/odin1440.img) ) instead FDOEM.144 )
copy command.com, autoexec.bat and config.sys from FDOEM.144 to C:  
and now you have a usb stick bootable with freedos and without space limit.
Now you may leave qemu.
mount yours pen and copy yours files for bios update,  shutdown linux and boot with usb pen.
At the end, you can check if everything is fine without reboot , using:
qemu -hda /dev/sdb -boot c 
Check if pen usb boots ! 
that's all .

---

### Post by Kangarooo on 2010-07-20
For me didnt work.
i read manual from [http://www.gigabyte.de/Support/Motherboard/HowToReflashBIOS.aspx](http://www.gigabyte.de/Support/Motherboard/HowToReflashBIOS.aspx)
my motherboard exe file is from [http://www.gigabyte.com/products/product-page.aspx?pid=1415&dl=1#bios](http://www.gigabyte.com/products/product-page.aspx?pid=1415&dl=1#bios)
i just copied all commands and executed them in terminal
```

wget http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz
gunzip FDOEM.144.gz
mkdir /tmp/floppy
sudo mount -t vfat -o loop,quiet,umask=000 FDOEM.144 /tmp/floppy
unzip newBIOS.zip -d /tmp/floppy
sudo umount /tmp/floppy
rmdir /tmp/floppy
sudo mv FDOEM.144 /boot/biosupdate.img
sudo apt-get install syslinux
sudo cp /usr/lib/syslinux/memdisk /boot/

sudo **mousepad** /boot/grub/menu.lst

*and there it was empty file so copied there

title       BIOS upgrade
kernel      /boot/memdisk
initrd      /boot/biosupdate.img

```

and after restart i didnt had any new grub options.
i have xubuntu 10.10 so theres latest grub

but also where to put motherboard_bios_6vx7_4x_f45.exe
 ?
its an self-extracting file i extracted it with wine and in it theres
autoexec.bat
flash855.exe
6VX7-4X.F45

---

### Post by sergiomb on 2010-07-22
> **Kangarooo said:**
> For me didnt work.
i read manual from [http://www.gigabyte.de/Support/Motherboard/HowToReflashBIOS.aspx](http://www.gigabyte.de/Support/Motherboard/HowToReflashBIOS.aspx)
my motherboard exe file is from [http://www.gigabyte.com/products/product-page.aspx?pid=1415&dl=1#bios](http://www.gigabyte.com/products/product-page.aspx?pid=1415&dl=1#bios)

is easier because yours flash bios are less than 1.44 , if not yours method doesn't work, and don't try enlarger a floppy disk , because is not possible . :wink:

---

### Post by wayward4now on 2010-07-23
> **sergiomb said:**
> is easier because yours flash bios are less than 1.44 , if not yours method doesn't work, and don't try enlarger a floppy disk , because is not possible . :wink:

I finaiily used a 2.8 meg dos image as that gave me enough space for the exe file and the flash file. I held my breath and it worked! Thanks, Ric

---

### Post by ybukhman on 2010-07-27
> **ciscosurfer said:**
> [SIZE=3]**HOW TO FLASH YOUR BIOS**[/SIZE]

[SIZE=2][COLOR=Black] M2: CD[/COLOR][/SIZE]
[/B][SIZE=1]*Unpack FreeDOS image &#8594; create temp dir &#8594; mount FreeDOS image to /tmp/cdr &#8594; copy flashing tool*[/SIZE][SIZE=1]* and new BIOS image to /tmp/cdr *[/SIZE][SIZE=1]*(see footnotes below) &#8594; unmount image &#8594; install mkisofs &#8594; create ISO &#8594; burn ISO to disc *[/SIZE][SIZE=1][I]&#8594; reboot following vendor instructions

[/I][/SIZE][SIZE=1]*Note: "NewBiosFiles" listed below is pseudocode for the extracted location of the new BIOS image + related files that you just downloaded*[/SIZE]```
wget http://www.fdos.org/bootdisks/autogen/FDOEM.144.gz
gunzip FDOEM.144.gz
mkdir /tmp/cdr
sudo mount -t vfat -o loop FDOEM.144 /tmp/cdr
sudo cp ~/NewBiosFiles/* /tmp/cdr
sudo umount /tmp/cdr
sudo apt-get install mkisofs
mkisofs -o newBIOS.iso -b FDOEM.144 FDOEM.144
cdrecord -v newBIOS.iso

```[note: in later releases, /usr/bin/mkisofs symlinks to /usr/bin/genisoimage]
[note: in later releases, /usr/bin/cdrecord symlinks to /usr/bin/wodim]

Reboot from the CD and flash your BIOS with the commands provided by the BIOS vendor. Check the **README** file for exact syntax.[COLOR=Navy][SIZE=2][B]
[COLOR=Blue]END OF METHOD[/COLOR]
[/B][/SIZE][/COLOR] 



I have tried the CD method on my laptop, Acer Aspire 5315-2582.  First, 
```

sudo cp ~/NewBiosFiles/* /tmp/cdr

```
didn't work: I got a "no space on device" message.  However, I copied the BIOS files on a flash card, and the DOS was able to find that.

Second, the Acer flash executable refused to run under DOS.  Fortunately, I had an old Windows repair disk.  I was able to boot from that and get to the Windows command prompt (you say that you want to repair your computer, then cancel, and that gets you to a menu that has a command prompt option).  Starting the flash executable from the Windows command prompt didn't give the "unable to run in DOS mode" error.

Third, the flash executable still couldn't run because it was missing oledlg.dll.  Downloading it from [http://www.dll-files.com/dllindex/dll-files.shtml?oledlg](http://www.dll-files.com/dllindex/dll-files.shtml?oledlg) and putting it in the same folder as the BIOS files fixed that issue.

---

### Post by Muschl on 2010-08-13
Hi,

the following short guide / script can be used to boot the Free Dos ISO image from USB Stick and update your Motherboard Bios.

You have to install Grub2 and Grub4Dos to your USB Stick.
Download and copy the FreeDos Iso image fdbasecd.iso to <YOUR-MOUNTED-USB-DEVICE>/
Copy the Script to <YOUR-MOUNTED-USB-DEVICE>/boot
Copy your Bios files to <YOUR-MOUNTED-USB-DEVICE>/boot/bios
And finaly run the AddBiosFlashFiles.sh to update the FreeDos ISO image with your Bios files.

Optional copy linux iso files to <YOUR-MOUNTED-USB-DEVICE>/boot/iso
and boot it with Grub2.

@ciscosurfer: please add the instructions to your first post

Detailed instructions as comments in the script...

```

#!/bin/sh
#
#        AddBiosFlashFiles.sh --- The Flash Bios Integrator by Muschl
#       ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
# 
# 1. Install Grub2 to your USB Stick
#	grub-install --no-floppy --root-directory=/mnt/<YOUR-MOUNTED-USB-DEVICE> 
#
# 2. Install Grub4Dos to your USB Stick 
#	wget http://downloads.sourceforge.net/project/grub4dos/GRUB4DOS/grub4dos%200.4.4/grub4dos-0.4.4.zip
#	unzip grub4dos-0.4.4.zip
#	cp ./grub4dos-0.4.4/* /mnt/<YOUR-MOUNTED-USB-DEVICE>/boot/grub
#
# 3. Change Grub2 Configuration, Add Menue Entry
#	vi /mnt/<YOUR-MOUNTED-USB-DEVICE>/boot/grub/grub.cfg	
#
#	menuentry "Switch to Grub4Dos" {
#	linux16 /boot/grub/grub.exe
#	}
#
#	menuentry "Ubuntu 10.04 Netbook Edition" {
#	loopback loop /boot/iso/ubuntu-10.04-netbook-i386.iso
#	linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-netbook-i386.iso noeject noprompt --
#
# 4. Change Grub4Dos Configuration, Add Menue Entry
#	vi /mnt/<YOUR-MOUNTED-USB-DEVICE>/boot/grub/menu.lst
#
#	title FlashDos (cp Bios files to /boot/bios & run AddBiosFlashFiles.sh)
#	find --set-root /fdbasecd.iso
#	map /fdbasecd.iso (0xFF)
#	map --hook
#	root (0xFF)
#	kernel /isolinux/data/memdisk
#	initrd /isolinux/data/fdboot.img
#
# 5. Download FreeDos
#	wget http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/1.0/fdbasecd.iso
#	mv ./fdbasecd.iso /mnt/<YOUR-MOUNTED-USB-DEVICE>
#	
# 6. Install ISO Update Script for Flash Bios Files
#	mkdir -p /mnt/<YOUR-MOUNTED-USB-DEVICE>/boot/iso
#	mkdir -p /mnt/<YOUR-MOUNTED-USB-DEVICE>/boot/bios
#	cp ./AddBiosFlashFiles.sh /mnt/<YOUR-MOUNTED-USB-DEVICE>/boot
#
# 7. Create Directory for the Motherboard Bios (like: /boot/bios/msi-k9a)
# 8. Copy your bios flash files into the created Motherboard Bios directory
# 9. Run this Script with sudo to integrate the bios flash files into fdbasecd.iso
#
work=$(pwd)
error=0
rights ()
{
	if [ "$(id -u)" != "0" ]; then
	echo "!-This script must be run as root or with sudo-!" 1>&2
   	exit 1
	fi
}
clean ()
{
echo "+ Clean up..." 1>&2
umount $work/source 
rm -rf $work/target $work/source
}
error ()
{
	if [ $? != 0 ]; then
	error=1
	quit
	fi
}
quit ()
{
	{
	if [ $error != 0 ]; then
	echo "!-ERROR-OCCURRED-! Please look into the logfile." 1>&2
	fi
	}
clean
exit
}
rights
clean
echo "+ Create directorys..." 1>&2
mkdir -p $work/source $work/target
error
echo "+ Mount ISO file..." 1>&2
mount $work/../fdbasecd.iso $work/source -o loop,ro
error
echo "+ Copy ISO content..." 1>&2
cp -R $work/source/* $work/target
error
echo "+ Create Bios directory..." 1>&2
mkdir -p $work/target/bios
error
echo "+ Copy Bios files..." 1>&2
cp -R $work/bios/* $work/target/bios
error
echo "+ Create ISO image..." 1>&2
mkisofs -lrJ -V "FreeDos FlashDos" -no-emul-boot -boot-load-size 4 -b isolinux/isolinux.bin -c isolinux/boot.cat -input-charset utf-8 -o fdbasecd.iso $work/target
error
echo "+ Update Boot Image..." 1>&2
mv -f $work/fdbasecd.iso $work/../
error
quit

```

---

### Post by FakeOutdoorsman on 2010-09-17
Is there another source for *FDOEM.144.gz*?  The link to fdos.org is 404.

---

### Post by ciscosurfer on 2010-09-17
> **FakeOutdoorsman said:**
> Is there another source for *FDOEM.144.gz*?  The link to fdos.org is 404.[http://www.mediafire.com/file/26md8hs5aablqke/FDOEM.144.gz](http://www.mediafire.com/file/26md8hs5aablqke/FDOEM.144.gz)

---

### Post by FakeOutdoorsman on 2010-09-17
Thanks.  This old beast of a machine will live a little longer.

---

### Post by Ian Clark on 2010-11-06
I really recommend for noobs to sign on to the #flashrom IRC channel (on irc.freenode in your pidgin or empathy accounts, then add yourself to the #flashrom room) and ask a real person if your chipset is supported or what you need to do. They're helpful and can keep you from messing up your machine.

---

### Post by Rodnox on 2010-11-13
Hint for acer users: 
On [this Page](http://support.acer-euro.com/drivers/utilities.html#BIOS) you can download an iso image for a bios update tool, bootable from cd. 

Works like a charme.

---

### Post by naskoos on 2011-01-09
I was trying to update the bios of my Toshiba portege m800 laptop. There was no update running in dos, all the updates where only for windows as Toshiba technicians said, so nothing of above works for me. So I've searched and found a "windows live CD" and the job done for me!!!! Maybe this is off topic but I had to write it somewhere because it was really difficult and time consuming for me to find searching all Ubuntu ways...

---

### Post by runbux on 2011-02-26
What a thread.

The first proposal is technical to the point of incomprehensibility! Does anyone actually understand all that stuff?

At least on my computer dosemu appears to be dead. It won't start from the GUI (Applications/System Tools/Dos Emulator) and when I try to start it in a terminal it complains about low memory???? How much memory does DOS need?

tim@tim-XXXX:~$ dosemu
LOWRAM mmap: Operation not permitted
Cannot map low DOS memory (the first 640k).
You can most likely avoid this problem by running
sysctl -w vm.mmap_min_addr=0
as root, or by changing the vm.mmap_min_addr setting in
/etc/sysctl.conf or a file in /etc/sysctl.d/ to 0.
tim@tim-System-Product-Name:~$ 

The first method assumes WAY to much technical prowess and the second doesn't work, at least for me.

Thanks to both of the posters, but I'm still stuck..

Any other ideas how to flash a BIOS update?

---

### Post by ciscosurfer on 2011-02-26
> **runbux said:**
> What a thread.Totally.

> The first proposal is technical to the point of incomprehensibility!Which "proposal" are you referring to?

> Does anyone actually understand all that stuff?Yes.

> At least on my computer dosemu appears to be dead. It won't start from the GUI (Applications/System Tools/Dos Emulator) and when I try to start it in a terminal it complains about low memory???? How much memory does DOS need?

tim@tim-XXXX:~$ dosemu
LOWRAM mmap: Operation not permitted
Cannot map low DOS memory (the first 640k).
[COLOR=Red]You can most likely avoid this problem by running[/COLOR]
[COLOR=Blue]sysctl -w vm.mmap_min_addr=0[/COLOR]
[COLOR=Red]as root[/COLOR], or by changing the vm.mmap_min_addr setting in
/etc/sysctl.conf or a file in /etc/sysctl.d/ to 0.
tim@tim-System-Product-Name:~$As root (or elevated user), did you try running the code it recommends to fix your error?```
sudo sysctl -w vm.mmap_min_addr=0
dosemu
```> The first method assumes WAY to[o] much technical prowess and the second doesn't work, at least for me.

Thanks to both of the posters, but I'm still stuck..

Any other ideas how to flash a BIOS update?There are many alternatives listed in the original post as well as the rest of this thread.

---

### Post by wayward4now on 2011-02-27
If you are uncertain on how to proceed, I'd recommend you take it to a shop and pay them to do it for you. It's a short road to bricking your computer, playing around with flashing your rom. Myself, I created a bootable DOS dvd with the update program on it. I booted the DVD, and from DOS ran the command line flash program that did the job. But, I have to tell you I held my breath when I hit the enter key to do it.  Unless you have a very valid reason for updating your bios, I'd leave it alone. Ric

---

### Post by runbux on 2011-03-04
Thanks to Criscosurfer, running the fix in the error message did solve the problem, and I admit that I also misinterpreted the meaning of "low RAM" in that same message. It's been so many DECADES since I thought about DOS that I forgot that Low Memory meant the first 640K - not that 3 gigs wasn't enough to run DOS.

Another problem is that I am ignorant of any feasible method to make a freedos startup floppy when my computer doesn't have a floppy drive.  :confused:

The frequently mentioned freedos startup floppy file seems not available, and I don't know which live CD version to use. I assume it should include the term OEM, right? Does it make any differemce?

is it possible to MAKE a live cd with an .img file that includes both the freedos .img and the AMI dos installer?

Last, I did ask a couple repair shops about doing it for me, but they only do Windows. No Linux aware shops around here! Their responses: You know more about this Linux stuff than we do!

Should I consider myself a guru?  :)

---

### Post by 3miel on 2011-03-07
hello
i don't have a time to read whole 16 pages of topic, maybe you can edit first post and add how to upgrade bios with grub2 

```
menuentry "Flash BIOS" {
 linux16 /boot/memdisk
 initrd16 /boot/flashbios.img
 }
```works perfect for me
and great job, this haw to is amazing

---

### Post by coolbrook on 2011-03-19
> **ciscosurfer said:**
> [http://www.mediafire.com/file/26md8hs5aablqke/FDOEM.144.gz](http://www.mediafire.com/file/26md8hs5aablqke/FDOEM.144.gz)

The CD method works nicely.  Please replace the original link in your opening post.  You may also mention that you have to blank a used CD-RW to get the current process to work.

---

### Post by Bruceper on 2011-08-06
I used the grub method, and everything appears to work great until I try to boot, and then I get a grub error

Error 15: Unable to find file

I'm a linux n00b and this one is beyond me. Any help?

---

### Post by medhi on 2011-08-25
Hi guys,
Here what I did to upgrade my P5LP-LE motherboard from BIOS 3.17 to 3.19 using ubuntu 11.04 and flashrom ([http://www.flashrom.org/Flashrom](http://www.flashrom.org/Flashrom))
Everything was done with the help of the volunteers from #IRC channel **#flashrom** on [irc.freenode.net]("http://www.freenode.net/") 


```

svn co -r 1157  svn://flashrom.org/flashrom/trunk flashrom
cd flashrom
patch -p0 < ../Board-enable-for-ASUS-P5LP-LE.patch

```edit file "board_enable.c" and look for your motherboard P5LP-LE, should be located line 1816.
Look for string "0x1043" (appears twice) and replace it by string by "0x103c"

```
make 
``````
sudo lspci -nnvvvxxx
```copy paste the output to [http://paste.flashrom.org]("http://paste.flashrom.org/")

```
sudo ./flashrom -V -w ../sp35100/319.rom 
```copy paste the output to [http://paste.flashrom.org]("http://paste.flashrom.org/")

---

### Post by medhi on 2011-08-25
thanks,
All the credits go to the amazing volunteers from #IRC channel **#flashrom** on [irc.freenode.net]("http://www.freenode.net/")

---

### Post by movieplayer on 2011-08-30
flashrom doesnt support my chipset, now what?  i'm not into long lists of creating live cd's and have not floppy drive...

---

### Post by CJ_Hudson on 2011-10-20
I have tried the EZ Flash in the BIOS, AFUDOS and the ASUS proprietory Windows BIOS updater, but to no avail. I have also e-mailed ASUS because of the compatibility issue of the new BIOS (my motherboard is a slightly modified version from the normal one because of the chipset, I think.) And I have tried Flashrom.

Edit:
Those nice people at flashrom helped me out- BIOS safely flashed and up and running now!
I had to 'force'-flash it in the end because of the compatibility problem.

[http://www.flashrom.org/Flashrom](http://www.flashrom.org/Flashrom)

---

### Post by michaeljt on 2011-11-01
Shouldn't this tutorial be on [http://help.ubuntu.com/community](http://help.ubuntu.com/community) too?  I think it must be mature enough by now.  I would put it there myself but I don't know the most appropriate place (and that is probably better done by the tutorial maintainer anyway to avoid confusion).

---

### Post by ]SiB[ on 2011-12-28
Hello everybody,
I use "M3: GRUB" method with success but I have 30x the same machine as my.
Do you have any idea to change Grub2 to this:
1) Run PC with 'FreeDOS_BIOS' Grub2 entry (not default!!) and reboot at end
2) Run PC with default Grub2 entry (normal boot)

I have this 30x PCs in different localization, I looking a full remote way to upgrade a BIOS. On my one PC is working good a "M3: GRUB.." method", all 30PCs are the same Foxconn Nettop.

PS. Flashrom & CoreBoot don't work on my platform.

---

### Post by ]SiB[ on 2012-01-13
**[COLOR="Red"]SOLVED[/COLOR]**
I find solution.
In Ubuntu (**/etc/default/grub.cfg**) change:
**GRUB_DEFAULT=saved**

Type in terminal:
sudo **updategrub**
sudo **grub-set-default 0**

PC is always working on grub 0 entry [default], PC working without keyboard (nobody change anything local).

When I want to reboot PC with other grub entry only ones time I use command in terminal:
sudo **grub-reboot 1**
After reboot PC will work with default grub entry every time.

I hope this help others.

---

