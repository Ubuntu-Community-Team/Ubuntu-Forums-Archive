---
title: "Boot an existing XP (Physical HD) install with VirtualBox"
date: 2008-04-26
forum: Virtualisation
---

### Post by Sand Lee on 2008-04-26
[URL="http://ubuntuforums.org/showpost.php?p=4839961&postcount=6"][SIZE=3][CENTER]:KS**[COLOR=Orange]..::Updates::..[/COLOR]**:KS[/CENTER]
[/SIZE][/URL]
[RIGHT][SIZE=2][COLOR=DarkRed]**HowTo for **[/COLOR][/SIZE][COLOR=DarkRed][B][SIZE=3]Vista [1]("http://ubuntuforums.org/showpost.php?p=6186193&postcount=157"),[2]("http://ubuntuforums.org/showthread.php?t=984437")
[/SIZE][/B][/COLOR][/RIGHT]
[URL="http://forums.virtualbox.org/viewtopic.php?t=9697"][B][RIGHT][COLOR=Blue]VBoxForums Version[/COLOR][/RIGHT]
[/B][/URL]

[SIZE=4]Introduction[/SIZE]
I made this tutorial because I have been searching for an open source virtualization solution. I've tried VMware, but didn't like the GUI (it felt too slow) and the fact that it was closed source. Virtualbox was more appealing because it is open source and because it doesn't currently require a hack to get running in Hardy. After tons of research, I've found that the solution couldn't be simpler. 
*[SIZE=1]Please read or skim the tutorial before attempting it. Note: This tutorial was tested to work with VBox 1.6 and may not work for users w/ SATA drives. [/SIZE]*

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=68820&stc=1&d=1209956343[/IMG]

[SIZE=4]Step 1: Create a grub boot cd[/SIZE]
Creating a grub cd will let you boot straight into your target Windows partition.[SIZE=1] 
**Following method adapted from [grub manual.]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html")**[/SIZE]
```
 cd ; mkdir -p iso/boot/grub ; cp /usr/lib/grub/*-pc/stage2_eltorito /boot/grub/menu.lst iso/boot/grub
```**[Configure]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS") /home/you/iso/boot/grub/menu.lst** to boot your target partition. Remove the "savedefault" option from your target entry if it exists. Then run the following to create the grub.iso file,
```
cd ; mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso iso
```[SIZE=4]Step 2: Create a virtual disk (.vmdk)[/SIZE]
When creating such a disk, it's preferable to only specify your Windows partition. This is a safety precaution that will prevent a data corruption problem that results from booting into the currently running OS. As a preliminary step, you must add yourself to the disk and vboxusers groups,
```
sudo usermod -G disk,vboxusers -a `whoami`
```Log out and log back in here... and edit the following command to point to your WinXP partition: (I specified my WinXP partition - /dev/sda2 - with "-partitions 2") 
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda -partitions 2 -relative -register
```[SIZE=4]Step 3: Create a new hardware profile in WinXP[/SIZE]
[LIST]
[*]Click Start > Control Panel > System
[*]    On the Hardware tab, select Hardware Profiles
[*]        Click Copy, name the new hardware profile Physical
[*]     Rename the current profile to Virtual
[/LIST]
[SIZE=4]Step 4: Change Windows XP's IDE controller[/SIZE]
[LIST]
[*]     On the Hardware tab, select Device Manager
[*]    Right-click the IDE Controller and click Update Driver
[*]        Click No,.. and Next
[*]    Click [Advanced] and Next
[*]    Click Don't search... and Next
[*]        Select Standard Dual channel PCI IDE controller
[*]        Click Next, Finish, then Close and Reboot into Linux
[/LIST]
[SIZE=4]Step 5: Run VirtualBox[/SIZE]
[LIST]
[*]    Realize that you may have to reactivate your copy of XP
[*]     Create a machine that uses the created .vmdk (in the drop-down menu of the HD selection section)
[*]Have this machine boot the CD-ROM first and mount the grub.iso file
[*]     You may have to try between the two IDE controllers types (Settings/Advanced) to see which works for you
[*]    Enable the IO-ACPI option and run your VM!
[/LIST]

[SIZE=5] [SIZE=4]Step 6: Bypass Windows Activation [[COLOR=DarkRed]Experimental[/COLOR]][/SIZE][/SIZE]

[LIST]
[*] Follow the directions in this [post]("http://ubuntuforums.org/showpost.php?p=6259708&postcount=167")
[*] Give your feedback here
[LIST]
[*] I will remove or improve this section as a result
[/LIST]

 
[/LIST]
[CENTER] [SIZE=4][COLOR=DarkOrange][COLOR=Plum] ***[/COLOR] [SIZE=4][COLOR=Teal]**TroubleShooting**[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=3][COLOR=DarkOrange] [COLOR=Plum]***[/COLOR][/COLOR][/SIZE]
[LEFT]
[LIST]
[*]Disk read error: [1]("http://ubuntuforums.org/showpost.php?p=6716355&postcount=202"), [2]("http://ubuntuforums.org/showpost.php?p=7029633&postcount=221")
[/LIST]
[/LEFT]
[/CENTER]
 
[CENTER][SIZE=4][COLOR=DarkOrange] *** [/COLOR]**[COLOR=Sienna]Warning![/COLOR]**[/SIZE][SIZE=3][COLOR=DarkOrange] ***[/COLOR][/SIZE]
[COLOR=Orange][SIZE=4][SIZE=3]About Guest Additions![/SIZE]

[/SIZE][/COLOR][/CENTER]
[SIZE=1]**Note: This problem may not exist for later versions of VBox (post-1.6).**[/SIZE]
Installing Guest Additions may cause the Windows installation in an existing partition to be unbootable (natively) - you might ***only*** be able to boot it from VirtualBox _from there on out_. This is a result of VirtualBox changing a significant amount of hardware in your configuration in order to have a user friendly virtual machine. If you already have installed Guest additions, you can try to remove it from within VirtualBox, and rebooting natively to XP.


**ToDo:**
[LIST=1]
[*]Find fix for native booting problem [SIZE=1][COLOR=Green]DONE*[/COLOR][/SIZE]
[*]Easy .vmdk creation that doesn't require installation of another large or closed source program. [SIZE=1][COLOR=Green]DONE*[/COLOR][/SIZE]
[*]Creation of boot.iso for direct booting w/o system's grub [SIZE=1][COLOR=Green]DONE[/COLOR][/SIZE]
[*]Port tutorial to Ubuntu community documentation and official VirtualBox page
[*]Find constant-activation fix [SIZE=1][COLOR=Red]NOPE (see update)[/COLOR][/SIZE]
[/LIST]
**Sources & Helpful Links: :-\"**
[VBox-migr]("http://www.virtualbox.org/wiki/Migrate_Windows"), [squidoo-virt]("http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu"), [mazimi-virt]("http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/"), [mazimi-bypass]("http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/"), [mesbalivernes-virt]("http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html"), [Dutch Translation]("http://relst.nl/site/index.php/handleidingen/54-virtual-box-handleiding-start-een-bestaande-xp-op-vanaf-een-bestaande-harde-schijf-op-in-virtualbox.html")

Comments and suggestions welcome!

---

### Post by kabanta on 2008-04-27
This is a very helpful guide. Since it warns that the result will make existing XP install unable to boot natively, it would be nice if there was a bit more detail to prevent confusion.

It may help clarify to point to some information about "dedicated grub partitions" (e.g., [here]("http://www.troubleshooters.com/linux/grub/grubpartition.htm"))

More important, for the **VBoxManage** command, can you provide more detail about what is your directory structure? 

Is /dev/sda1 your windows partition?
Is /dev/sda2 your dedicated grub partition?

thanks.

---

### Post by gladstone on 2008-04-28
So, by following this guide, I would be able to boot my existing Windows partition as a virtual machine in VirtualBox?

This sounds good, but I think I'm going to wait until it's possible to boot back into Windows natively. Whats the reason stopping this atm?

Also, what's the issue with GRUB when using this method? i.e. if you dont remove the timeout and it boots into Linux? I have my Linux and Windows installs on different partitions - would that still be an issue for me?

*Also* :) would there be a way to add an entry to boot straight into the Virtualised XP from grub?

---

### Post by spawn12345 on 2008-04-28
I will try it this week.

But the guide isnt good for a linux noob :/
It would be nice if some things are explained more.

like whats this: > sudo usermod -G disk -a USERNAME_HERE
sudo usermod -G vboxusers -a USERNAME_HERE 

> VBoxManage internalcommands createrawvmdk -filename WindowsXP.vmdk -rawdisk /dev/sda -partitions 1,2 

> Enable Passthrough in CD/DVD to watch DVDs (you'll need to install Win VLC as well) 
Enable IO-ACPI and run it! 

:confused:

---

### Post by Sand Lee on 2008-04-28
**UPDATE:** terminal command has been made simpler

**@ kabanta:** 
I added your suggestions. Thanks for giving the link to that tutorial (It's the one I used). 
/dev/sda1 = grub
/dev/sda2 = windows

**@ gladstone:**
As I said, Virtualbox changes a significant amount of hardware in XP. Chances are, XP will not function correctly if you boot it with your original hardware. Hopefully later versions of VBox will change this behavior.
Removing the timeout is a safety precaution. If you were not able to specify partitions, there is a chance that you may boot into your currently running install, thus corrupting your partition. Booting straight into the virtual machine would be cool, but I do not think this is possible.
[I][B]
Edit:[/B][/I] It seems significant changes are made after installing Guest Additions; so yes, you should be able to boot now after following this tutorial.

**@ spawn12345:**
With the current state of VirtualBox not allowing a user to boot into their partition natively, I do not encourage "linux noobs" to attempt this tutorial. I created the tutorial expecting that the reader have basic knowledge of Virtualbox's interface. The vbox command is explained in the VBox user manual. Any other commands are easily explained in the man pages.
If VirtualBox becomes more flexible and allows users to boot natively, I will then make this tutorial more beginner friendly. ):P
[I][B]
Edit:[/B][/I] Now that I've found a solution to the native booting problem (not installing the guest additions) I will try to make this tutorial friendlier.

---

### Post by Sand Lee on 2008-04-30
[LIST]
[*]**Major:** Native boot issue "solved": Users should not install guest additions[COLOR=Green]*[/COLOR] as it will dedicate the partition to virtualization - 4/30/08
[*]**Major:** Revamped the Tutorial (Now 5 steps!) to exclude WPA bypassing methods as I assume most people have already upgraded to SP3 - 07/08/08
[*]*Minor:* Added Guest Additions "undo" section, [SIZE=1]thanks **[Mr. Picklesworth]("http://ubuntuforums.org/showthread.php?t=769883&page=8#76")**![/SIZE] - 07/15/08
[*]*Minor:* Added note about version # and SATA drives. Hopefully a solution will be figured out. - 09/14/08
[*]**Major:** Added VirtualBox Forum version to the tutorial, [SIZE=1]thanks **[starfry]("http://ubuntuforums.org/showthread.php?t=769883&page=13#129")**![/SIZE] - 09/28/08
[*]**Major:** Suceeded in running Vista with Vbox 2.0.4_OSE. **[Reference]("http://ubuntuforums.org/showpost.php?p=6157782&postcount=149")**. - 11/12/08
[*]**Major: **Fixed MBR problem and ToDo #3 with grub.iso method. Creation of .vmdk's now possible with Opensource VBox - "finishes" ToDo #2 - 11/22/08
[*]*Minor:* Added Experimental Step 6 - 11/29/08
[/LIST]
**):PTesting:**

[LIST]
[*] ***BugFix:*** Included the possible "disk read error" workarounds noted by [ciucca]("http://ubuntuforums.org/showpost.php?p=7029633&postcount=221") and [borikru]("http://ubuntuforums.org/showpost.php?p=6716355&postcount=202"). - 11/13/09
[/LIST]

**:-$ Deprecated:**

[LIST]
[*]*Minor:* Partition safety issue resolved with "mbr" package[COLOR=Green]*[/COLOR][SIZE=1] - thanks **[lance2010]("http://ubuntuforums.org/showthread.php?p=4807656#9")**![/SIZE] Minor tutorial cleanups. - 05/02/08
[*]**Major: **Fixed issue of constantly having to activate windows; activation is now only needed once - 05/04/08
[*]**Major:** With further testing, it seems the activation bypass method outlined in the tutorial doesn't work for SP3. :confused: - 05/09/08
[*]**Major:** Troubleshooting section added. Alternate Step 1 added. - 05/12/08
[*]*Minor:* Attached Microsoft WPA Documentation
[*]**Major:** [Digging this tutorial]("http://digg.com/linux_unix/Boot_an_existing_XP_Physical_HD_install_with_VirtualBox") (it's been baking for quite a while) - it's now or never - 08/09/08
[*]***BugFix:*** Fixed VERR_FILE_NOT_FOUND error. **[SIZE=1][Reference.]("http://ubuntuforums.org/showpost.php?p=6170643&postcount=154")[/SIZE]** - 11/13/08
[/LIST]

---

### Post by the8thstar on 2008-04-30
> **Sand Lee said:**
> [LIST]
[*]Native boot issue "solved": Users should not install guest additions as it will dedicate the partition to virtualization - 4/30/08
[/LIST]

Warning:

This is why it's important to create a _**SECOND HARDWARE PROFILE**_, to prevent massive confusion for XP. I wonder if you are able to transfer files b/w Ubuntu and XP without the Guest additions. Also, seamless virtualization of XP is not available if you don't have Guest additions enabled on your machine AFAIK.

---

### Post by natrixgli on 2008-04-30
Has anyone tried anything like this with Vista?

Cheers,

-n8

---

### Post by lance2010 on 2008-04-30
> Remove your grub's timeout option by commenting out the line (if you aren't able to specify the aforementioned partitions)
Thanks for the tutorial.  One important improvement that I gleaned from another post [here]("http://forums.virtualbox.org/viewtopic.php?t=2019") that eliminates any potential catastrophic problem of booting into the host OS (and hence the need for disabling grub's timeout) is to use a generated MBR.

[LIST=1]
[*]Install the mbr package:
```
sudo apt-get install mbr
```
[*]Generate a dummy MBR:
```
install-mbr winxp.mbr --force
```
[*]Use the MBR in creating the .vmdk file.  The command I use is the following; adjust accordingly for your particular configuration.  Note that I have XP on the first partition.
 ```
VBoxManage internalcommands createrawvmdk -filename /home/me/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 1 -mbr winxp.mbr -relative -register
```
[/LIST]
This should allow you to boot directly into your WinXP partition without going through grub.  Works for me.

---

### Post by softtower on 2008-05-01
Will this work with VirtualBox that comes with Ubuntu and installed via apt? I don't have "VBoxManage" but I have "vboxmanage" in my /usr/bin. That one doesn't have "internalcommand" option.

Then I found VBoxManage in /var/lib/virtualbox, but it won't start saying "cannot open shared object file".

---

### Post by Sand Lee on 2008-05-01
> #  This can be made in Vmware Server or in the closed-source Virtualbox (in Win/ or Linux) [See part 9.9 of user manual]

The VBox version in the repos is the opensource version, therefore you will need to the closed-source download from the link provided.

---

### Post by Sand Lee on 2008-05-01
Thanks for heads-up lance2010, I've seen this before but you've put it in a clear and understandable format. This will be added to the tutorial shortly. ToDo #3 = [COLOR="YellowGreen"]Done![/COLOR]
[B]
Tutorial Updates[/B]: [http://ubuntuforums.org/showthread.php?t=769883#6](http://ubuntuforums.org/showthread.php?t=769883#6)

---

### Post by armitage1337 on 2008-05-04
If I'm using a copy of XP activated with a corporate license, I shouldn't need to do the activation thing, right? Since the license works on multiple computers, and the "two" XPs (virtual and physical) would just be recognized as two separate computers?

---

### Post by Sand Lee on 2008-05-04
I don't know exactly how corporate licensing works, however it seems to me that it just allows the license to be on multiple computers. I think it you may still have to backup your activation keys because Windows will/should notice the significant change in hardware. The corporate key will probably make activation a trivial process for you though.

---

### Post by gladstone on 2008-05-05
Great work on the guide Sand Lee!!

Now if it were only possible to install the Guest Additions...:eek: Could it ever be possible?

If you attempted this using VMWare instead (as per [here]("http://ubuntuforums.org/showthread.php?t=631671")), does VMWare have its own "Guest Additions" that would work?

---

### Post by armitage1337 on 2008-05-05
I think that VMware Workstation 6.5 might allow you to install the 'addons' and boot from a physical partition, but it's currently in beta. You can get a free copy from the VMware site and try it out, but it may be buggy.

---

### Post by AndrewTheArt on 2008-05-06
Small note, you can refer to the currently running user's home directory as simply ~

For example, to go to a folder named "test" in /home/username, you'd type

~/test

No need for the clunky YOUR_USERNAME syntax (I used to do that too, seems noobish now)

---

### Post by Sand Lee on 2008-05-06
Thanks AndrewTheArt, wish I had known this before hand. This will make my commands a whole lot shorter !!

Oh, and thanks gladstone, I've put quite some time into making it..

---

### Post by spiffytech on 2008-05-07
I tried doing this with Windows 2000 and almost have it working. I get to boot and select the hardware profile, then the "loading Windows" progress bar goes by, but the OS hangs where it's supposed to transition to the graphical boot, never removing the completed progress bar from the screen. 

I followed your guide to a T, except for using the dual-channel IDE controller. Trying that made Windows die a horrible death upon reboot. Is that the problem? Is there an alternate driver I could try?

---

### Post by UnknownFear on 2008-05-08
I have a small question. I am trying to install VirtualBox and in the readme, it says

[I]How to "Install" and Run
------------------------

1. Unpack this archive somewhere.

2. Make sure you have a dot (.) in your LIBPATH statement in CONFIG.SYS.

3. Put the following line at the beginning of your CONFIG.SYS
   and reboot:

     DEVICE=<somewhere>\VBoxDrv.sys

4. Go to <somewhere> and run VirtualBox.exe (Qt GUI frontend).

5. Note that by default VirtualBox stores all user data in the
   %HOME%\.VirtualBox directory. If %HOME% is not set, it will use
   the <boot_drive>:\.VirtualBox directory. In either case, you may
   overwrite the location of this directory using the VBOX_USER_HOME
   environment variable.[/I]

Now, I don't know what exactly it means to put a (.) in the LIBPATH statment. And also, for the first line in the CONFIG file, I put "DEVICE=home\VBoxDrv.sys", I than saved it and rebooted.. but I dont see any VirtualBox.exe or anything in the home folder except my username folder with all my stuff in it. Some help please?

---

### Post by Sand Lee on 2008-05-09
**@ spiffytech & UnknownFear**

I can only answer questions about using VirtualBox in Ubuntu and using it to boot WinXP at this moment. Hopefully some other knowledgeable Vbox user can answer your questions...

---

### Post by jeremymiles on 2008-05-10
I'm stuck at the 

    *  Create a machine that uses the created .vmdk (found in drop-down menu)

Stage.  I can create a machine, but i don't ever get the option to tell it where the vmdk file is.  Or if I do, I haven't noticed.

---

### Post by Sand Lee on 2008-05-10
> **jeremymiles said:**
> I'm stuck at the 

    *  Create a machine that uses the created .vmdk (found in drop-down menu)

Stage.  I can create a machine, but i don't ever get the option to tell it where the vmdk file is.  Or if I do, I haven't noticed.

The option appears when VBox asks you to choose a virtual hard disk. You will (or should) find your .vmdk file in the drop-down menu of this section. I've edited the tutorial to make this clearer.

**@ All - Please note a change in the tutorial:** I have tested it against WinXP SP3, and the WPA backup does not work. This means you will have to find alternative methods to keep your dual-boot/virtual machine. What I have done is create an HD image (w/ Clonezilla) of my regular XP install and another of my Virtualized one. If I ever need to boot back into XP I can restore it's image. Since I don't expect to boot into XP for a while, or do I have to (for that matter), this solution suits me - it also lets me install VirtualBox guest additions as well =] !

---

### Post by beow on 2008-05-10
Followed the posts instructions carefully but on my Thinkpad T61 i get the dreaded "read error" message:

```
MBR

A disk read error occurred
Press Ctrl+Alt+Del to restart 
```

I.e. it prints "MBR", then sits there for one or a couple of seconds and then prints the "disk read error" message. (Ctrl+Alt+Del amounts to nothing). The last log message only says that it starts booting from HD:

```
00:00:06.940 Guest Log: BIOS: Booting from Hard Disk...
00:00:13.242 Changing the VM state from 'RUNNING' to 'SUSPENDED'.

```

(A couple of minutes later I turn off Vbox whicg then yields the next log message, so the log is not very helpful...). Have WinXP (don't know which SP but the T61 is from January this year) on /dev/sda1 which is the partition I try to virtualize.

Would be extremely grateful if someone could help with this...

---

### Post by Javed_Ahamed on 2008-05-10
Im getting this too.... I do all the steps in the article and when i start up the xp virtual machine i just get MBR on one line and thats it it just stays there.... what am i doing wrong? Am i choosing the wrong partition? I did cfdisk and it said the windows was on sda2 so....

---

### Post by Sand Lee on 2008-05-10
Javed_Ahamed & beow, could you guys give me a screenshot of your cfdisk output? And please try running the following to see if grub is installed on your windows partition,
```
grub
```
```
find /boot/grub/stage1
```
I've tried to reproduce the MBR hang, but couldn't. Thanks!

---

### Post by Javed_Ahamed on 2008-05-10
Here is my cfdisk... my hp laptop came with a recovery like 8 gig drive and the main drive so thats why there are 2 win ones.

[[IMG]http://img339.imageshack.us/img339/1342/screenshotjavedjavedhpdoc9.th.png[/IMG]](http://img339.imageshack.us/my.php?image=screenshotjavedjavedhpdoc9.png)

And here is my grub output:

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,4)

---

### Post by Sand Lee on 2008-05-10
Hmm.. nothing seems out of the ordinary. After some googling, it seems this problem may be caused by an [outdated or misconfigured bios]("http://www.technologyquestions.com/technology/244889-post8.html"), and not grub.

---

### Post by spiffytech on 2008-05-10
> **Javed_Ahamed said:**
> Im getting this too.... I do all the steps in the article and when i start up the xp virtual machine i just get MBR on one line and thats it it just stays there.... what am i doing wrong? Am i choosing the wrong partition? I did cfdisk and it said the windows was on sda2 so....

I had this problem too. In the following line, replace '2' with the partition number on which you keep windows:

```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
```

You'll need to first delete the vmdk file from the failed attempt.

---

### Post by Javed_Ahamed on 2008-05-10
2 is the partition that i have windows on though.... look at the picture i posted two replies up.

---

### Post by Javed_Ahamed on 2008-05-10
Im not sure if this makes any difference: but in this step


[B]Step 5: Change Windows XP's IDE controller

    * On the Hardware tab, select Device Manager
    * Right-click the IDE Controller and click Update Driver
    * Click No,.. and Next
    * Click [Advanced] and Next
    * Click Don't search... and Next
    * Select Standard Dual channel PCI IDE controller
    * Click Next, Finish, then Close and Reboot into Linux
[/B]

In my device manager i have Two Standard Dual Channel pci ide controllers already there... i dont have anything called ide controller.

I have under IDE ATA/ATAPI controllers
[LIST]
[*]prrimary ide channel
[*]primary ide channel
[*]secondary ide channel
[*]secondary ide channel
[*]standard dual channel pci ide controller
[*]standard dual channel pci ide controller
[/LIST]

i just followed the instructions for the 2 standard controllers anyway?

---

### Post by Javed_Ahamed on 2008-05-10
Well I updated my drivers/bios and did the steps all over again, updating those pci controllers even tho they already seemed correct. And i still get this :(

[[IMG]http://img329.imageshack.us/img329/2220/screenshotdxprunningsunlx2.png[/IMG]](http://imageshack.us)
[[IMG]http://img329.imageshack.us/img329/2220/screenshotdxprunningsunlx2.fbe46b82c6.jpg[/IMG]](http://g.imageshack.us/g.php?h=329&i=screenshotdxprunningsunlx2.png)

---

### Post by beow on 2008-05-11
Here is my cfdisk output:

```
                         cfdisk (util-linux-ng 2.13.1)

                              Disk Drive: /dev/sda
                       Size: 160041885696 bytes, 160.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 19457

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1        Boot        Primary   NTFS             []              27962.09*
                                      Unusable                             3.88*
    sda2                    Primary   Linux ext3                       19995.66
    sda4                    Primary   Linux ext3                      110078.93
    sda3                    Primary   Linux swap / Solaris              1998.75


```

grub output:

```
grub> find /boot/grub/stage1
 (hd0,1)

```

Anything unusual with this? Something I noticed when looking at the conf pages of the Virtualbox GUI is that is says that the partition is of size 149 GB (I'm not at the T61 now so I don't have the exact output) which is far from the real size. I also have the same issue like Javed with Step 5, that the options described is not available, however I found that option under the Hard drive device and changed to it but it didn't make any difference. But opposed to Javed I also get the "read error" message short after halting at the "MBR" print-out.

---

### Post by Sand Lee on 2008-05-11
Did you guys try changing the virtual IDE controller to PIIX3 or PIIX4?

---

### Post by Javed_Ahamed on 2008-05-11
yeah ive tried changing those a couple of times... :( 

hmmm

since it seems we are pointing to the right partition and its says it doesnt have a mbr, did windows mbr get erased when i installed linux? My computer came preinstalled with xp and i used ubuntus partitioning tool to allow it to be installed. But i can still boot into xp and ubuntu...

or might my xp being media center make a difference?

---

### Post by Javed_Ahamed on 2008-05-11
Hmmm ok, looking at another website I tried doing this step:

VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register

as 

VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -register

instead, bypassing the mbr/partition safeguards. This time it worked, the virtual pc went to the GRUB menu and i tried to load up my Xp. However now i just hang at the picture attached. What makes it even odder is in GRUB when i boot up my recovery partition that hp gives us... it loads up in the virtual machine! And the recovery partition is xp as well! So what the heck is going on here :? Why wont it load the media center partition but will load the other one?

---

### Post by beow on 2008-05-12
More experimenting: Followed [http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/](http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/) to back up the mbr and then created the virtual image using this command:
```
$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 1 -relative -register
```

I.e. skipped the MBR part. The new output when trying to run this is

```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 17
_
```

Any clues? BTW what can happen to the MBR when not using the -mbr option? Haven't rebooted yet since I'm at work and can't experiment too much...

---

### Post by Javed_Ahamed on 2008-05-12
beow try what i did 2 posts up. Just before you do it delete the mbr u made, and the virtual machines u made. basically a clean start. And when u load up grub in the virtual machine just make sure to choose ur windows and not linux or else you will screw your os over.

---

### Post by fofftorrent on 2008-05-12
Aplogies if this is a noob question :confused:

I created the raw disk with the command (mbr came from the install-mbr command of the mbr ubuntu package):
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinXP.vmdk -rawdisk /dev/sda -partitions 1 -mbr ~/.VirtualBox/WinXP.mbr -relative -register

I created a second hardware profile in WinXP BEFORE booting the rawdisk VM with virtualbox and using that HW profile. However, windows then tries to install all sorts of hardware and cannot find drivers. Also the mouse does not work in the VM!

Any thoughts? Should I install some drivers prior to booting with the VM? Where should I get the drivers? Windows was trying to install the "Base Sytem Driver" and "VGA" driver, but could not find them. Is it possible to uninstall some drivers from one HW profile but not my main native boot HW profile? :confused:

---

### Post by beow on 2008-05-12
> **Javed_Ahamed said:**
> beow try what i did 2 posts up. Just before you do it delete the mbr u made, and the virtual machines u made. basically a clean start. And when u load up grub in the virtual machine just make sure to choose ur windows and not linux or else you will screw your os over.

I think its actually to late, can't boot up winxp natively any longer, BSOD both in "undocked profile" and in the "virtualized profile"...

But essentially I did what you said removed everything from ~/.Virtualbox and created the new vmdk file (without the "-mbr" option). A difference was that i used "-partitions 1" to just virtualize the winxp partition while you, it seems, virtualized the whole hard drive?

OK, I see, by virtualizing the whole disk you booted into grub and could select winxp, ok, and it worked?

Any suggestions to undo the BSOD problem? Should I re-install the MBR i backed-up or what? I don't think Javed's suggestion will work until the blue screen is away... :|

---

### Post by Javed_Ahamed on 2008-05-12
Um other than reinstalling xp i dont know how to fix your problem and while i virtualized my whole drive and could get into grub i still couldnt load my xp... when it starts to load all it says is starting up... what was odd however is i could start up my xp recovery partition which basically uses xp as the underlying os. I think there is some setting in the xp we are trying to virtualize that is not allowing us to do so.

---

### Post by sarfa on 2008-05-12
Thank you for the information here. [SOLVED]The problems I'm having, if I boot into Windows normally, my mouse doesn't work. I cancel all the update driver install requests as stated and then reboot the computer as it asks. Upon reboot, it hangs at the Windows Startup screen. So I have to hard boot it and it don't get past this point. However I can boot into Windows in safe mode just fine and the mouse work. from here I can reboot the machine and it will boot back into Windows normally but again the mouse will not work.[SOLVED]

Patients is a virtue!

---

### Post by beow on 2008-05-13
Can boot winxp natively now after using some kind of "revert to last working conf" or something that was given as a boot option when starting winxp using key F8. So far so good. Then I did what Javed suggested and virtualized the whole /dev/sda disk. After starting the virtual machine I was presented the same grub boot loader in the VM as when booting natively. I selected Windows XP and then i was back to comment #24 again, at least almost...

```
Starting...

A disk read error occurred
Press Ctrl+Alt+Del to restart 
```

So it's back to square one again...

---

### Post by Javed_Ahamed on 2008-05-13
yay your at the same step as me. cept mine doesnt say extra stuff like disk error occured :/ you're lucky.

---

### Post by rrhoglund on 2008-05-20
I have an ibm t61p and have been following other tutorials that do not mention anything about installing dual channel pci ide controllers.  I have been getting the dreaded boot disk error.  In the device manager under the ide ata/atapi controllers, I have the following items.

sata ahci controller
intel ich8m ultra ata storage controllers 2850
primary ide channel

There is no ide controller; therefore, how do I install the dual channel pci ide controller?

Do you think that sata could be the source of the problem?  Has anyone tried turning this off in the bios?

thanks

---

### Post by Sand Lee on 2008-05-21
In VirtualBox v1.6, there is an option to enable a SATA controller in the "Hard Disks" section of your virtual machine's settings. Have you tried this instead of installing the Dual Channel Controller?

---

### Post by rrhoglund on 2008-05-21
FYI...I did try enabling the sata controller and it still gave me the disk read error.

---

### Post by Sand Lee on 2008-05-23
After some googling, it seems that SATA controllers may need the VMware scsi driver. See my second source, mazimi-virt, to see how to install it. Let me know how it goes, if you decide to try it.

---

### Post by mactea on 2008-05-27
As rrhoglund I have a SATA DD and I get the BSOD if I enable and use a SATA controler (0 or 1). If I use the IDE one controler, it works, but as soon as there is a disk access CPU goes 100%. So the VM is just not usable (way to slow).

I have installed VMware scsi driver to test, but it does the same as above.

I should say that I am using VirtualBox 1.6 on Hardy. I might have to try with WB 1.5.6

Btw, Sand Lee you say for Step 7:
Copy your wpa.dll [...]
It actually wpa.dbl not dll

---

### Post by eZtaR on 2008-06-15
I get the following error :(

```
eztar@eztar-laptop:~$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda1 -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
VirtualBox Command Line Management Interface Version 1.6.2
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

ERROR: VMDK: cannot go backwards for partition data in '/home/eztar/.VirtualBox/WindowsXP.vmdk'
Error code VERR_INVALID_PARAMETER at /home/vbox/vbox-1.6.2/src/VBox/Devices/Storage/VmdkHDDCore.cpp(2527) in function int vmdkCreateRawImage(VMDKIMAGE*, VBOXHDDRAW*, uint64_t)
Error while creating the raw disk VMDK: VERR_INVALID_PARAMETER

```

---

### Post by Sand Lee on 2008-06-15
> **eZtaR said:**
> I get the following error :(

```
eztar@eztar-laptop:~$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda1 -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
VirtualBox Command Line Management Interface Version 1.6.2
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

ERROR: VMDK: cannot go backwards for partition data in '/home/eztar/.VirtualBox/WindowsXP.vmdk'
Error code VERR_INVALID_PARAMETER at /home/vbox/vbox-1.6.2/src/VBox/Devices/Storage/VmdkHDDCore.cpp(2527) in function int vmdkCreateRawImage(VMDKIMAGE*, VBOXHDDRAW*, uint64_t)
Error while creating the raw disk VMDK: VERR_INVALID_PARAMETER

```
eZtaR, you received the error message because you typed in /dev/sda1 rather than /dev/sda which basically means you asked for the second partition in the first partition of your Hard drive! To change which partition you use, do it in the "-partitions" option.

---

### Post by eZtaR on 2008-06-16
> **Sand Lee said:**
> eZtaR, you received the error message because you typed in /dev/sda1 rather than /dev/sda which basically means you asked for the second partition in the first partition of your Hard drive! To change which partition you use, do it in the "-partitions" option.

Okay :) I'll try that :) Thanks :D

---

### Post by Mecharuva on 2008-06-17
I get to step 2 and this is what happens:

```
VirtualBox Command Line Management Interface Version 1.5.6_OSE
(C) 2005-2008 innotek GmbH
All rights reserved.

Usage: VBoxManage internalcommands <command> [command arguments]

Commands:

  loadsyms <vmname>|<uuid> <symfile> [delta] [module] [module address]
      This will instruct DBGF to load the given symbolfile
      during initialization.

  unloadsyms <vmname>|<uuid> <symfile>
      Removes <symfile> from the list of symbol files that
      should be loaded during DBF initialization.

  setvdiuuid <filepath>
       Assigns a new UUID to the given VDI file. This way, multiple copies
       of VDI containers can be registered.

WARNING: This is a development tool and shall only be used to analyse
         problems. It is completely unsupported and will change in
         incompatible ways without warning.

Syntax error: Invalid command 'createrawvmdk'
```
:(

---

### Post by Sand Lee on 2008-06-18
From step two,

> For reasons unknown, this can only be made in the closed-source Virtualbox and not the open source version [See part 9.9 of user manual]. 

---

### Post by Mecharuva on 2008-06-18
I thought I had the closed source version...
I'll double check.

edit:
No, I have OSE.
But I can't find the Closed Source version anywhere :confused:

---

### Post by Sand Lee on 2008-06-18
Check in step 2 of the tutorial, I've linked to the webpage.

---

### Post by Mecharuva on 2008-06-18
Well, that's what I had... so I uninstalled it.
And then I installed the new package (NOT ose)
Aaaand... it says it's there but it's not.
Wtf :confused:

---

### Post by Sand Lee on 2008-06-19
> **Mecharuva said:**
> it says it's there but it's not.

I'm guessing you downloaded the Ubuntu binary from the sun download portal?.. what exactly do you mean by "it?"

---

### Post by Mecharuva on 2008-06-20
> **Sand Lee said:**
> I'm guessing you downloaded the Ubuntu binary from the sun download portal?.. what exactly do you mean by "it?"

Ah my bad, I should've explained in more detail.
No matter which version of VirtualBox I get, or even how I get it,
I click the program link in the Applications menu,
And it never starts.
:(

---

### Post by Sand Lee on 2008-06-21
> **Mecharuva said:**
> Ah my bad, I should've explained in more detail.
No matter which version of VirtualBox I get, or even how I get it,
I click the program link in the Applications menu,
And it never starts.
:(

Try running "VirtualBox" (or "virtualbox") in a terminal, without the quotes, and please post the output here.

---

### Post by Ng Oon-Ee on 2008-06-21
Terrific guide, works like a charm.

An additional note, I had to enable IO APIC or my Windows XP would hang on booting (gave me a small heartattack the first time that happened, but could still boot into it normally by dual-boot).

Otherwise, this means I now have no real reason to dual-boot except for games (and when I do want to dual-boot, no problem!:))

Thank you!

---

### Post by taffypride on 2008-06-25
I've tried various options in attempting to run XP via VirtualBox but I am still having problems.

My system is configured with 2x80Gb HDD's.

XP is installed on the Primary HDD.
Ubuntu is installed on the Secondary HDD which is set as a SLAVE (grub setup on Primary HDD (HD0) )

I've used the command
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirBox/WinXP.vmdk -rawdisk /dev/sda -partitions 1 -mbr ~/.VirtualBox/WinXP.mbr -relative -register

```
and it will create the file.

Setup a new virtual machine in VirtualBox, using the WinXP.vmdk and configured extra settings.

Went to run the Virtual Machine and it stops short with a message
```
MBR 2FA
```

Can't get any further.  Any help?

Edit: Don't know if it makes a difference but I have XP Home Service Pack 3 installed.

---

### Post by rdiaztushman on 2008-06-27
Hello!

Thanks for the terrific tutorial!

I'm having a problem logging all the way back into the existing WinXP installation, though.  I get to the WinXP login screen, enter my name and password, but when I get the "Loading Personal Settings"  windows, WinXP hangs and I have to manually close it with VirtualBox. 

Any ideas?

Here are the relevant specs (and if I haven't listed something, let me know)

Sony Vaio VGN-SZ160P
WinXP SP2
Ubuntu 8.04 LTS
Virtual Box (binary, not OSE)

Yes, I uncommented the lines for USB support.
Yes, I created the hardware profile in WinXP.

VirtualBox WindowsXP configuration:
------------------------------------
General
Name
WindowsXP
OS Type
Windows XP
Base Memory
192 MB
Video Memory
8 MB
Boot Order
Floppy, CD/DVD-ROM, Hard Disk
ACPI
Enabled
IO APIC
Enabled
VT-x/AMD-V
Disabled
PAE/NX
Disabled
 

Hard Disks
IDE Primary Master
WindowsXP.vmdk [Writethrough, 93.16 GB]
 

CD/DVD-ROM
Host Drive
MATSHITA UJ-832D (/dev/scd0)
 

Floppy
Not mounted

 

Audio
Disabled

 

Network
Adapter 0
PCnet-FAST III (NAT)
 

Serial Ports
Disabled

 

USB
Disabled

 

Shared Folders
None

 

Remote Display
Disabled
------------------------------------

Any help is greatly appreciated.  Thanks in advance!!

---

### Post by Sand Lee on 2008-06-27
Thanks for the compliments Ng Oon-Ee! I really appreciate it! and just fyi, the IO APIC option was mentioned in the tutorial :)

@ taffypride
I don't know if you have, but have you tried alt. Step 1/2? If not, can you open gnome-system-monitor and tell me the name of the device where "/" is mounted?

@ rdiaztushman
I've recently encountered the same problem with the newer VBox versions, and so have other people on the Vbox mailing list (though, with general performance issues). What you can do instead is install VBox OSE, after removing the closed-source version (I'm not sure how the modules will react). And what's great, is that you can use reuse the .vmdk you created with this tutorial, you'll probably also have to use alt. Step 1/2.

---

### Post by Sand Lee on 2008-06-27
I was wondering. Since I don't believe anyone would use WinXP SP2 over SP3 (and removing SP3 for this tutorial doesn't work!), and I am unsure if the WPA backup method still works, should I remove the related sections from the tutorial? This would shorten the tutorial from 8 to 5 steps! On the other hand however, it would stop people from being able to bypass WPA if switching back and forth from native to virtual. :confused:

I was thinking of adding a poll, but I didn't want to make the change and have a permanent and possibly irrelevant poll on top of the tutorial..

---

### Post by benner on 2008-07-02
I have tried a million times and must be missing something. I get

MBR

NTLDR is missing
press any key to restart

(I am using the closed source version of virtualbox, Hardy Heron, IBM T43 laptop, XP sp3)

any help is appreciated.

---

### Post by Sand Lee on 2008-07-02
> **benner said:**
> I have tried a million times and must be missing something. I get

MBR

NTLDR is missing
press any key to restart

(I am using the closed source version of virtualbox, Hardy Heron, IBM T43 laptop, XP sp3)

any help is appreciated.

I'm guessing you've already tried the troubleshooting section?

---

### Post by andrew_awp on 2008-07-02
I assume this same strategy would work with Xen? I will try it now....

---

### Post by andrew_awp on 2008-07-02
See, why I think this wouldnt work is, every time i have significantly changed video cards, windows 2000 and up hangs on bootup with a black screen, and you must reinstall windows or at least do a full repair. the same goes for a virtual video card, i would guess.

---

### Post by Sand Lee on 2008-07-03
I have personally confirmed this to work however in Windows XP and Vista.
And I don't know a thing about Xen, I would look for guides online...

---

### Post by woomg on 2008-07-04
dear,

I also had a same problem as like 'beow' and 'Javed_Ahamed'.
However, I found workaround(but little bit complex) method to boot directly into Windows XP. If someone has more simplest process, please share your knowledge with us.

Requirement : Ubuntu CD, Windows CD...
Status: My harddisk partitions are
sda1 : linux boot('/boot')
sda2 : NTFS (VBox XP boot)
sda3 : linux root('/')
.
.
.

First, backup your current MBR(grub), "dd if=/dev/sda of=~/grubboot.mbr bs=512 count=1"
Second, I confirmed Win XP(from VBox) can boot correctly with grub(created vmdk without -partitions option).
Third, make system can boot directly into Windows XP(repair the MBR by Windows CD), and confirm it.
Fourth, boot by Ubuntu CD.
Fifth, make MBR file("dd if=/dev/sda of=~/.VirtualBox/WinXP.mbr bs=512 count=1') which can boot Windows XP natively.
Sixth, restore MBR with the file created at step 'First', or repair grub.
Seventh, create VMDK file with whole partitions.

CAUTION:
1. You must contains whole partitions for VMDK, otherwise you can not boot.
```
  ex) VBoxManage internalcommands createrawvmdk -filename WinXP.vmdk -rawdisk /dev/sda -partitions 1,2,3,5,6,7 -mbr WinXP.mbr -relative -register
```

2. If you have other NTFS partition before WinXP partition that you want to use for VBox, you can not use this method. VBox always try to boot from first NTFS partition.

Thanks,
MG

---

### Post by andrew_awp on 2008-07-04
I have run into 2 problems with this solution:
virtualbox isnt capable of 64bit guests yet, so i cant run my XP/amd64 installation.
i havent found a way to create and use the rawdisk image (.vmdk) without being root, which means i have to always run VirtualBox as root.

---

### Post by Sand Lee on 2008-07-04
> **andrew_awp said:**
> 
i havent found a way to create and use the rawdisk image (.vmdk) without being root, which means i have to always run VirtualBox as root.

Adding yourself as to the disk group (step 2 of the tutorial) solves this problem.

---

### Post by andrew_awp on 2008-07-04
oh, i forgot to log out first. anyway, moot point in trying to use a 64bit OS until that changes.

---

### Post by drubin on 2008-07-15
Hi 

Thanks for taking the time to write this tutorial. I have had windows dualbooted for some time (but can never be bothered to reboot my pc mainly for testing websites in IE6,7)

running this code give me these warnings and I am not sure if i am doing something wrong. Any suggestions?

Ps not sure if it makes any difference but my hard drive is sata, and on a completely different hard drive to ubuntu/grub
```

VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sdb1 -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
```
> 
VirtualBox Command Line Management Interface Version 1.6.2
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

WARNING! The following VirtualBox settings files have been automatically
converted to the new settings file format version '1.3-linux':

  /home/drubin/.VirtualBox/VirtualBox.xml  (1.2-linux)

The current command was aborted to prevent overwriting the above settings
files with the results of the auto-conversion without your permission.
Please put one of the following command line switches to the beginning of
the VBoxManage command line and repeat the command:

  -convertSettings       - to save all auto-converted files (it will not
                           be possible to use these settings files with an
                           older version of VirtualBox in the future);
  -convertSettingsBackup - to create backup copies of the settings files in
                           the old format before saving them in the new format;
  -convertSettingsIgnore - to not save the auto-converted settings files.

Note that if you use -convertSettingsIgnore, the auto-converted settings files
will be implicitly saved in the new format anyway once you change a setting or
start a virtual machine, but NO backup copies will be created in this case.


---

### Post by Mr. Picklesworth on 2008-07-15
Quick lesson of the day:
Do not. DO NOT install VirtualBox Guest Addins for the "guest" OS if you still plan to dual boot with it; Windows will fail on startup when booting on its own. If you (like I) do this, do not panic. Boot Windows via VirtualBox, uninstall the guest addins, restart, and then (still in VirtualBox) run System Restore. And then never do it again.

---

### Post by drubin on 2008-07-15
@Mr. Picklesworth  

Was that directed at me? Because I did not install "guest addins" or at least i think i didn't

---

### Post by Sand Lee on 2008-07-15
**@ rubinboy**

Your thanks is greatly appreciated. I am not familiar errors you are receiving, but they do look like they're emanating from old configs. What I would suggest is backing up -moving/renaming- your old virtualbox folder and starting over fresh. The 1st command in the tutorial should do that for you.

**Edit:** About your SATA setup, try changing the hd settings in Vbox, from IDE to SATA, if the first go-around doesn't prevail.

---

### Post by Sand Lee on 2008-07-15
> **Mr. Picklesworth said:**
> Quick lesson of the day:
Do not. DO NOT install VirtualBox Guest Addins for the "guest" OS if you still plan to dual boot with it; Windows will fail on startup when booting on its own. If you (like I) do this, do not panic. Boot Windows via VirtualBox, uninstall the guest addins, restart, and then (still in VirtualBox) run System Restore. And then never do it again.

:popcorn: I'm glad it all worked out for you Mr. Picklesworth! I am thankful that you posted your experience here. I had done the same with Vbox 1.6.2 and was surprised that Windows would work normally afterwards - this is not the case with earlier versions. I thought this happened by chance, but since you've reproduced the outcome, I can go ahead and add this to the tutorial!

---

### Post by Mr. Picklesworth on 2008-07-15
Nope, my little lesson is directed at nobody. I just did that, then thought I should share what I learned lest anyone else bumps into it :)

That was with Windows Vista Home Premium, by the way. Results elsewhere may vary. (But don't count on it :/).
Kind of a shame, since the guest addins certainly did work. Ah well, can't have everything. It's still plain cool, regardless of how the integrity of the universe hangs by a thread whenever it is attempted.

---

### Post by narcan on 2008-07-16
So uninstalling guest additions by itself would not do the trick ? A system restore was also necessary ?

I'm tempted to install the guest additions. I'm figuring that I'll be using this windows install via linux for 99% of the time, but I still want a resuce plan if I natively need to use windows. 

So I'm just wondering if I have to reenable system restore before I install the guest additions, or whether the uninstall should restore everything.

---

### Post by narcan on 2008-07-16
Another question.. how are you all getting around having to activate XP everytime the switch is made from real/virtual.

It keeps having me activate XP which is become pretty annoying.

---

### Post by drubin on 2008-07-16
> **Sand Lee said:**
> **@ rubinboy**Your thanks is greatly appreciated. 

Least I can do to some one that took the time to write such a tutorial.

> **Sand Lee said:**
> 
**Edit:** About your SATA setup, try changing the hd settings in Vbox, from IDE to SATA, if the first go-around doesn't prevail.

Not 100% sure where you mean, according to the tutorial I would not have even started Vbox?  (At work right now will give it another go when i get home)

---

### Post by specialbuddy on 2008-07-16
> **eZtaR said:**
> I get the following error :(

```
eztar@eztar-laptop:~$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda1 -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
VirtualBox Command Line Management Interface Version 1.6.2
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

ERROR: VMDK: cannot go backwards for partition data in '/home/eztar/.VirtualBox/WindowsXP.vmdk'
Error code VERR_INVALID_PARAMETER at /home/vbox/vbox-1.6.2/src/VBox/Devices/Storage/VmdkHDDCore.cpp(2527) in function int vmdkCreateRawImage(VMDKIMAGE*, VBOXHDDRAW*, uint64_t)
Error while creating the raw disk VMDK: VERR_INVALID_PARAMETER

```

I get the same error when I type this in#
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register

Anyone know how to fix this?

---

### Post by Sand Lee on 2008-07-16
> **narcan said:**
> So uninstalling guest additions by itself would not do the trick ? A system restore was also necessary ?

I'm tempted to install the guest additions. I'm figuring that I'll be using this windows install via linux for 99% of the time, but I still want a resuce plan if I natively need to use windows. 

So I'm just wondering if I have to reenable system restore before I install the guest additions, or whether the uninstall should restore everything.

Well for me, a system restore was not necessary - I guess it would be safe to remove that part from the tutorial...

About the constant activation, I did figure out a solution for WinXP-SP2 (or at least I think I did), but since I take it everyone has/will upgrade to SP3 (which the workaround won't work for), I've removed it from the tutorial. Also, I only recommend going into either mode (native or virtual) if you'll be staying in it for a while, otherwise you'll have to continuously go through the reactivation hassle.

---

### Post by drubin on 2008-07-16
> **Sand Lee said:**
> **@ rubinboy**

Your thanks is greatly appreciated. I am not familiar errors you are receiving, but they do look like they're emanating from old configs. What I would suggest is backing up -moving/renaming- your old virtualbox folder and starting over fresh. The 1st command in the tutorial should do that for you.

Did that now i get this output
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sdb1 -partitions 1 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
VirtualBox Command Line Management Interface Version 1.6.2
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

Cannot open replacement MBR file '/home/drubin/.VirtualBox/WindowsXP.mbr' specified with -mbr: VERR_FILE_NOT_FOUND
```

Any suggestions?

---

### Post by narcan on 2008-07-16
> **Sand Lee said:**
> Well for me, a system restore was not necessary - I guess it would be safe to remove that part from the tutorial...

About the constant activation, I did figure out a solution for WinXP-SP2 (or at least I think I did), but since I take it everyone has/will upgrade to SP3 (which the workaround won't work for), I've removed it from the tutorial. Also, I only recommend going into either mode (native or virtual) if you'll be staying in it for a while, otherwise you'll have to continuously go through the reactivation hassle.

Thanks.

I'm still on WinXP-SP2. We haven't yet made the move at work here.

Yeah, it's still a bit of a shame about the reactivation stuff, kind of makes this a little less useful to me as most of the time when I'm switching between the two I'll be without internet access.

---

### Post by drubin on 2008-07-17
> **narcan said:**
> Thanks.

I'm still on WinXP-SP2. We haven't yet made the move at work here.

Yeah, it's still a bit of a shame about the reactivation stuff, kind of makes this a little less useful to me as most of the time when I'm switching between the two I'll be without internet access.

Take a look at this link [http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/](http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/)

---

### Post by drubin on 2008-07-17
Created the "hard drive"  got that part working at least


But is it supposed to have a blank (black) window with a menu bar, when i click start on my windows Vm?

Not sure what other info i can give..

---

### Post by kejava on 2008-07-18
> **mactea said:**
> As rrhoglund I have a SATA DD and I get the BSOD if I enable and use a SATA controller (0 or 1). If I use the IDE one controler, it works, but as soon as there is a disk access CPU goes 100%. So the VM is just not usable (way to slow).I get the same behavior too.  sata hd (ST980811AS) but have to keep it as an IDE controller.  Have dual core but at least one of the CPUs is always pegged at 100%.  Alternates between the two.

UPDATE: stopped the CPU from being pegged at 100% by editing the registry.  however, still can't go from ide to sata w/o bsod.

---

### Post by conb123 on 2008-07-19
Hi thanks for this guide it was exactly what i needed just one problem i just booted into it in Virtualbox for the first time and my mouse wont move and the keyboard doesn't work.

EDIT: Sorry it is now working i should have waited before posting for anyone having this porblem just wait and your keyboard and mouse will initialise.

---

### Post by naknak987 on 2008-07-21
I just cant seem to get step 2 to work for me. This is what I get.

```
thefunkiller@naknak987-desktop:~$ sudo usermod -G disk,vboxusers -a 'thefunkiller'
[sudo] password for thefunkiller: 
thefunkiller@naknak987-desktop:~$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda1 -partitions 1 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
VirtualBox Command Line Management Interface Version 1.5.6
(C) 2005-2008 innotek GmbH
All rights reserved.

Error opening the raw disk: VERR_ACCESS_DENIED
thefunkiller@naknak987-desktop:~$ sudo VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda1 -partitions 1 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
VirtualBox Command Line Management Interface Version 1.5.6
(C) 2005-2008 innotek GmbH
All rights reserved.

Cannot open replacement MBR file '/home/thefunkiller/.VirtualBox/WindowsXP.mbr' specified with -mbr: VERR_FILE_NOT_FOUND
```

Please help, I have no clue what I did.

---

### Post by Sand Lee on 2008-07-21
@naknak987

The line, "sudo usermod -G disk,vboxusers -a `whoami`," should be used as is - you don't have to insert our username.

---

### Post by drubin on 2008-07-22
> **Sand Lee said:**
> @naknak987
The line, "sudo usermod -G disk,vboxusers -a `whoami`," should be used as is - you don't have to insert our username.


> thefunkiller@naknak987-desktop:~$ sudo usermod -G disk,vboxusers -a 'thefunkiller'

Also remember that the ` is not quotes,It is the key on the left hand side of the 1 key.

---

### Post by Ximbiot on 2008-07-23
> **natrixgli said:**
> Has anyone tried anything like this with Vista?

Cheers,

-n8

I started trying to get my native Vista partition to boot in VMWare and never got it past an early BSoD.  According to [this thread]("http://ask.metafilter.com/91050/UbuntuVista-Dual-Boot-With-a-Twist-Virtual-PC-in-ubuntu-booting-existing-Windows-Partition-exp-ins"), the lack of hardware profiles under Vista and the Windows Genuine Advantage EULA enforcement is going to enforce reactivation with every reboot into the other mode (native vs. virtual) until you hit a limit of like 3 reactivations, at which time you have to call MS customer support and try to convince them to reactivate you, which will probably become tedious or stop working after a little while.

Most of the information on the net about booting a native Vista partition in a virtual machine isn't encouraging, but the link above offered the fullest explanation as to why it may not be worth bothering with at all.  For kicks, I did install a new Vista machine in a VM w/a virtual disk and everything went fine, using my original Vista install disks, so the BSoD was likely just some driver issue, but I don't really know enough about it to go into more detail.

---

### Post by Aaditya_DMW on 2008-07-23
I already Have An Installed XP and Ubuntu 8.04 on My Hard Disk. Currently I Installed VMware On Ubuntu 8.04 ,
I want to Boot My Already Installed XP Using VMware(I Didn’t Installed Xp Using VMware and i Don't want To Install Again) And Work on it. Will dre Be Ny After-Effects On My Windows XP If i Boot It traditionally without Using VMware
Plz Help By Giving Ur Suggestion, i m Desperately Waiting For FollowUp Comments

---

### Post by teejcee on 2008-07-24
> **rubinboy said:**
> Take a look at this link [http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/](http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/)

Has anyone tried this with Virtualbox & XP  or is this the method that no longer works with SP3 applied???

---

### Post by drubin on 2008-07-25
> **teejcee said:**
> Has anyone tried this with Virtualbox & XP  or is this the method that no longer works with SP3 applied???

Haven't tried it on SP3 but according to some where in this thread or on that site it does not work with SP3 as MS changed the way their activation works.

---

### Post by specialbuddy on 2008-07-26
If I have SP3, does that mean I can't do this then?

---

### Post by drubin on 2008-07-26
> **specialbuddy said:**
> If I have SP3, does that mean I can't do this then?

According to the comments and docs. You should be able to run XP in Vbox as the tutorial says. But every time you switch over from Vbox to actually booting into XP you will have to re-activate it. 

Hope this helps but  I have never tried it with xpS3

---

### Post by Ghuloomo on 2008-07-29
Worked perfect! thank you

---

### Post by marcelotmelo on 2008-07-30
> **Mr. Picklesworth said:**
> Quick lesson of the day:
Do not. DO NOT install VirtualBox Guest Addins for the "guest" OS if you still plan to dual boot with it; Windows will fail on startup when booting on its own. If you (like I) do this, do not panic. Boot Windows via VirtualBox, uninstall the guest addins, restart, and then (still in VirtualBox) run System Restore. And then never do it again.

Ok, so I did not install the guest additions, and almost everything is working. The problem is, I had a similar setup before, but I was using vmware (under Hardy) but I got sick of patching/recompiling it. So I deleted the vmware profile, and followed the tutorial. I am now able to boot from VirtualBox, but have no network. There was a "VMWare..." network adapter on my Device Manager, which I removed, and there is an unrecognized PCI device (so is a VGA adapter) that I suppose is the virtual network adapter, but no drivers for it. Where can I find the drivers? Am I missing something?

Thanks!

---

### Post by marcelotmelo on 2008-07-31
So... I found the answer to my own question. I removed the network adapter under XP and switched the VirtualBox adapter for an Intel Pro 1000 T Server, for which XP has built-in drivers. Worked like a charm. Now I am trying to find a suitable video driver. :)

---

### Post by Zeikcied on 2008-07-31
I'm having some trouble with this.

When I tried to use the dummy MBR, it mostly hanged.  It would display "MBR:" followed by about four characters I can't remember.  I was able to hit the A key, and get the set of characters to change, and if I hit 1 it would tell me that the device selected is not bootable, and it instructs me to insert a bootable floppy disk.

When I tried using the entire hard drive, Grub would load but it wouldn't boot to Windows.  I figured out that it's because Grub has Windows XP set to hd(1,0) and that's probably the issue with the VM.  (My root partition, and thus Grub, is on an IDE drive while Windows is on an SATA drive.  For some reason, Grub and Linux seem to prioritize the IDE drive, which puts Windows on hd(1,0).)

I copied the Windows XP lines, renamed it to Windows XP VM, and changed the line to hd(0,0).  I had to reboot for this to take effect.  When I selected the VM line, it again gave me the error that the device is not bootable and that I should insert a floppy disk.

I can only assume that it isn't launching the Windows XP boot loader for some reason.  But I don't know why.  I'm a total newbie as far as virtual machines go.  (Same for boot loaders.)

EDIT: Never mind.  For some reason, the newer versions of Kubuntu keep designating my SATA drive as sdb, even though the other hard drive is an IDE drive (and should thus be hda while the SATA drive should be sda).

---

### Post by specialbuddy on 2008-08-05
When I was selecting Windows from the grub bootloader, nothing was happening.  I forgot one minor detail and now it works fine.  Make sure 'Enable IO APIC' is selected and it might work.  I feel like an idiot for missing the step.

---

### Post by emmettl on 2008-08-07
I have the same problem as several other posters on this thread:  My Windows XP is on its own SATA HD and while it still dual boots just fine, VirtualBox brings up the BSOD in the middle of the boot process.  

I have tried four combinations:  leaving the IDE drivers alone and trying either IDE Master or SATA 0 in VirtualBox, then trying both again with the two Intel IDE drivers replaced with the Standard Dual Channel IDE PCI driver.  All four options result in the exact same BSOD.  

I noticed a warning in section 5.1 of the VirtualBox user manual saying basically that SATA drives could be a problem because of Windows XP lacking AHCI drivers.  Is this a show-stopper?

---

### Post by crouton976 on 2008-08-21
So, correct me if I'm wrong, but there is still no support for usb, we can't use fullscreen or seamless mode unless we install the guest additions (which is bad) to correct these 3 problems, right?

---

### Post by mysterio2004173 on 2008-08-26
How do I point it towards my winxp partition? I installed ubuntu inside windows and I don't know where to look. Please help!

---

### Post by marcelotmelo on 2008-08-26
> **crouton976 said:**
> So, correct me if I'm wrong, but there is still no support for usb, we can't use fullscreen or seamless mode unless we install the guest additions (which is bad) to correct these 3 problems, right?

That's what I understood as well. Unfortunately I am not being able to use the virtualization, since I only have 1GB of RAM and it runs really slow on my machine. I don't know if it is even slower because of the lack of the guest additions.

---

### Post by drubin on 2008-08-26
> **mysterio2004173 said:**
> How do I point it towards my winxp partition? I installed ubuntu inside windows and I don't know where to look. Please help!

Did you install Ubuntu via wubi? I am not sure but I would not see the need for installing Vbox inside ubuntu that is inside windows?

If you need access to your windows files from inside ubuntu I would suggest starting another thread spesific to your needs.

If not could you explain what you mean by installed inside windows?

---

### Post by jflowers on 2008-08-29
I am a little confused.  So, can we use the open source version or do we require the close source one?  I installed the open source and then tried to install the closed source using the debian package and it did not allow me to do it.

---

### Post by Sand Lee on 2008-08-30
To create the virtual disk you must have the closed source version of vbox. So, if you're a free software kinda person, you can install the closed version just to make the .vmdk, uninstall it, install the Opensource version and use the created .vmdk. 

Or you can just install and use the closed source version.

---

### Post by anxiousdog on 2008-09-05
How can I do this without booting into XP? My original XP install was corrupted and I have never been able to fix it. Is there a way to still use the partition through VB?

---

### Post by anxiousdog on 2008-09-05
> **anxiousdog said:**
> How can I do this without booting into XP? My original XP install was corrupted and I have never been able to fix it. Is there a way to still use the partition through VB?

Hmm, looks like I can't do this until I fix that corrupted boot issue. Dang.

---

### Post by lengo on 2008-09-06
I got to step 2b (like naknak987, page 10, #92). Terminal output was:
```
paul@T61-CTO:~$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 1 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
VirtualBox Command Line Management Interface Version 2.0.0
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

Cannot open replacement MBR file '/home/paul/.VirtualBox/WindowsXP.mbr' specified with -mbr: VERR_FILE_NOT_FOUND
The raw disk vmdk file was not created
```
I copied/pasted all the commands from the tutorial (so ` is actually ` and not '). The only similarity I can see is that naknak987 and I both specify /dev/sda1 as -partitions 1 whereas many others specify it as partitions 2. But I swear my XP partition is sda1. Any clues?

EDIT: I tried this (from [here]("http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html"); note slightly different approach):
```
paul@T61-CTO:~$ VBoxManage internalcommands createrawvmdk -filename ./WinXP.vmdk -rawdisk /dev/sda -partitions 1 -mbr ./myBootRecord.mbr -relative -register
VirtualBox Command Line Management Interface Version 2.0.0
(C) 2005-2008 Sun Microsystems, Inc.
All rights reserved.

Segmentation fault
```
Different error; same result--no VirtualBox . . .

EDIT 2: I tried starting over at Step 1. This is what I get:
```
paul@T61-CTO:~$ sudo apt-get install mbr && mkdir ~/.VirtualBox && install-mbr ~/.VirtualBox/WindowsXP.mbr --force
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mbr is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 233 not upgraded.
mkdir: cannot create directory `/home/paul/.VirtualBox': File exists
```
Funny thing is, I can't find .VirtualBox in /home/paul/. Funny peculiar, not funny haha . . .

EDIT 3: Oops. I didn't have 'Show Hidden Files' selected . . . But there is no "WindowsXP.mbr" in the .VirtualBox folder. Just 'compreg.dat', 'VirtualBox.xml', and 'xpti.dat'. Help?

EDIT 4: I renamed .VirtualBox to .VirtualBox1 and started over. This time it created a .VirtualBox folder with WindowsXP.mbr in it. I ran the piece of magic code and got a segmentation fault again. But now the .VirtualBox folder has six files in it: 'compreg.dat', 'VirtualBox.xml', 'WindowsXP.mbr', 'WindowsXP.vmdk', 'WindowsXP-pt.vmdk', and 'xpti.dat' What *should* I have in there?

---

### Post by mssever on 2008-09-06
I've followed this tutorial, but I've had two problems.

[LIST=1]
[*]VirtualBox wouldn't recognize the mbr. I worked around that by using a rescue ISO, so I can now begin the boot process just fine.
[*]XP hangs during the boot process for quite some time, while one of my processor cores is pegged. Finally, it reboots itself. I saw a blue screen once for a fraction of a second before the reboot, but it didn't stick around long enough for me to read it and I haven't seen it since. I'm attaching a screenshot of the hang when booting in safe mode. How can I fix this? By the way, I can boot just fine the normal (non-VM) way.
[/LIST]

---

### Post by Sand Lee on 2008-09-07
In response to some errors, I want to note that this tutorial was tested to work with Vbox 1.6 - I will add this note on the 1st post. I will test newer releases when I have time and hopefully update this tutorial.

---

### Post by mssever on 2008-09-07
> **Sand Lee said:**
> In response to some errors, I want to note that this tutorial was tested to work with Vbox 1.6 - I will add this note on the 1st post. I will test newer releases when I have time and hopefully update this tutorial.
Do you mean specifically 1.6, or does your test cover 1.6.4 (my version)? I'm assuming the former.

---

### Post by lengo on 2008-09-10
Good news: I successfully got to Step 4 with VirtualBox 1.6.6 (virtualbox_1.6.6-35336_Ubuntu_hardy_i386.deb)! I sailed through the setup without a single error or glitch (though this may be of small comfort to you, mssever . . . ) 

Bad news: I hit the wall at Step 4, where I am supposed to make changes to XP's IDE controller. I suspect this has to do with my machine's SATA drive (T61), since others in this forum have noted the same roadblock. Perhaps this incompatibility could be noted in the tutorial, so that others with SATA drives (i.e., most recent notebooks) don't wade through the entire process only to find that it's not possible? Unless I missed a solution along the way?

Good news (part 2): I learned a lot! That's worth something. :-)

---

### Post by mssever on 2008-09-10
> **lengo said:**
> (though this may be of small comfort to you, mssever . . . ) 
You might have helped identify my problem. Thanks. I assume that I have a SATA drive since this machine (ThinkPad R61i) is fairly new. But I followed the instructions and used the IDE controller. When I gat a chance, I'll look at it. Googling my error message told me that it was likely something wrong with my hardware configuration.

---

### Post by Beanyhead on 2008-09-13
> **mssever said:**
> I've followed this tutorial, but I've had two problems.

[LIST=1]
[*]VirtualBox wouldn't recognize the mbr. I worked around that by using a rescue ISO, so I can now begin the boot process just fine.
[*]XP hangs during the boot process for quite some time, while one of my processor cores is pegged. Finally, it reboots itself. I saw a blue screen once for a fraction of a second before the reboot, but it didn't stick around long enough for me to read it and I haven't seen it since. I'm attaching a screenshot of the hang when booting in safe mode. How can I fix this? By the way, I can boot just fine the normal (non-VM) way.
[/LIST]

Same problem, it stops booting at the exact same spot.

---

### Post by DutchMountains on 2008-09-14
Hi There,

I have just registered to be able to reply to your tutorial.
First of all, great tutorial. Really works nice!!! It was just what I was looking for so that I can finally really use my XP copy without rebooting so many times.

I figured I have a problem though. I have two copies of XP here, once XP Pro and once XP-MCE. The first one is only present as virtual machine, whereas Windows XP-MCE is an original physical install (System: Dell Inspiron AMD64 X2 running 64bit kernel).

It is the last one that has to go virtual. Your method however describes only a solution for XP Pro, since only there one can right-click on the IDE controllers in Windows (step 4.2). In MCE this is not possible, one has to go into the menus. I set all IDE controllers to standard, but every time I start the virtual XP-MCE, I get up to the Windows-logo and then the blue screen saying it detected a change and shut down Windows. 

Is there any solution? I think if you'd be able to help me over this step, I'd be there where we all want to be!! =)

Thanks for your time and once more for this GREAT tutorial!!
Cheers,
DutchMountains

---

### Post by darksidez4 on 2008-09-15
i followed the guide exactly. but im having problems.

when i try to start the VM with just the XP partition it stops at a screen saying "mbr" - screen shot attached

with the whole hard drive booting it stops at a grub screen saying "starting up..." - screen shot attached

the vmdk files are created with no problems.
ive tried running it in the OSE, 2.0 , and 2.0.2
the latest version stops a 'segmentation fault' i got when creating the vmdk files.

there were a few post earlier which seemed address similar issues but i could not get a solution from them.

any ideas?

edit: running it on a lenovo x61 tablet, if thats of any use.

---

### Post by Harry Muscle on 2008-09-15
Not sure if anyone has mentioned this already or not, but I was having a bunch of issues with either getting the MBR message or Operating System Not Found, etc.  My problem was that my active or boot partition wasn't set properly.  What I did was boot a Ubuntu Live CD inside the Virtual Machine and change the boot flag to the correct partition that I was to boot.  Hope that helps someone.

Harry

---

### Post by LeAstrale on 2008-09-16
a wa to get past the re-activation issue would be to use a Volume License if you have access to one of those.

---

### Post by darksidez4 on 2008-09-17
to add to my problem, a few post above-
neither my restore partition nor bootable disks start in virtual box...

---

### Post by blastedmax on 2008-09-19
i did that and all i get is a code thats says "MBR 1FA" wut do i do

---

### Post by run1206 on 2008-09-23
> **blastedmax said:**
> i did that and all i get is a code thats says "MBR 1FA" wut do i do

run the alternative update and make a vmdk for the WHOLE disk.  make sure you capture the screen so you can change to the windows partition.

enter this code into a terminal...
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/SystemHD.vmdk -rawdisk /dev/sda -register
```

when you open up VirtualBox, choose SystemHD.vmdk instead, this will take you to your GRUB screen

edit: Sand Lee, thank you sooo much!!! :D
your alternative vmdk setup helped me cuz i also had frozen at MBR.

---

### Post by starfry on 2008-09-23
Good tutorial.

A few points that may or may not be interesting.

1) I use a corporate copy of XP and I have never had to activate it . Ever.

2) The thread below explains how to reconfigure your VM so it presents itself as if it has the same hardware as the raw metal, to fool activation. I have not tried this as I don't need to but thought someone may find it useful.
 [http://forums.virtualbox.org/viewtopic.php?t=9697&highlight=dell+computer+corporation](http://forums.virtualbox.org/viewtopic.php?t=9697&highlight=dell+computer+corporation)

3) Instead of doing Step 4, I used "MergeIDE" just because it's what I've done before. It's mentioned in a load of other threads on this subject and seems to work ok. 

[http://virtualbox.org/attachment/wiki/Migrate_Windows/MergeIDE.zip](http://virtualbox.org/attachment/wiki/Migrate_Windows/MergeIDE.zip)

4) My initial tests exhibit no problems booting natively after installing the Guest Additions when booted virtually.

---

### Post by pwaugh on 2008-09-24
I can now boot into my XP, after disabling agp440.sys, and adding myself to the "data" group.

But, my USB mouse will not function, and I cannot use my keyboard.  Any ideas?

I enabled USB per the directions, and added a line to my fstab, but I still cannot get USB working, or mouse or keyboard.

UPDATE: Solved it.  I just needed to NOT turn on the USB mouse, as it is on through the host system, and not separately enabled for the guest.  Then, I just had to be patient and wait long enough for the system to fully come up the first time.  Works great, but DO NOT change the HD controller type, or you will most likely crash your partition.  (Happened to me), and you do not have to do this to boot the existing XP partition.

If you have an AGP video card, you will have to turn off the agp440.sys service, (and if you use intelppm.sys, the same with that service).  This is done (correctly) in the recovery console.

Patrick

---

### Post by spidermagicat on 2008-09-28
Thanks to this great thread I have been able to install xp in a partition and boot it up in virtualbox. Not only that I have been able to boot normally still :-), so far so good

I have even successfully installed guest additions and all works fine.

The problem is CPU usage, which ACPI and ACPI I/O enabled virtualbox was constantly maxing one of my CPU cores. I hit upon a solution, disable ACPI...

I did this by changing the hal in XP first by going to devices, computer and intalling "Standard PC" instead of "ACPI multicore PC". In Virtualbox it worked perfectly. Booting normally it worked, it installed the drivers again on first boot and ran perfectly fine. However...

My sound card and wireless card require ACPI to function (something I was expecting)

At the moment I switch between hals manually depending on which machine I'm in as both boot with either hal. This is just about workable but not elegant

Is there a way to fix the CPU issue with ACPI enabled or select the hal on boot the same way I select hardware profile. I was hoping it would be part of the hardware profile but it seems not to be.

If you have any questions about what I've done so far please feel free to email me at "iamufromthefuture@gmail.com" (A handily annonymous email I use)

Ditto with any solutions to my problem if you like although post solutions here as well obviously.

Thanks for reading, I hope this will assure people that it's possible if they're struggling :-)

---

### Post by run1206 on 2008-09-28
> **spidermagicat said:**
> Thanks to this great thread I have been able to install xp in a partition and boot it up in virtualbox. Not only that I have been able to boot normally still :-), so far so good

I have even successfully installed guest additions and all works fine.

The problem is CPU usage, which ACPI and ACPI I/O enabled virtualbox was constantly maxing one of my CPU cores. I hit upon a solution, disable ACPI...

I did this by changing the hal in XP first by going to devices, computer and intalling "Standard PC" instead of "ACPI multicore PC". In Virtualbox it worked perfectly. Booting normally it worked, it installed the drivers again on first boot and ran perfectly fine. However...

My sound card and wireless card require ACPI to function (something I was expecting)

At the moment I switch between hals manually depending on which machine I'm in as both boot with either hal. This is just about workable but not elegant

Is there a way to fix the CPU issue with ACPI enabled or select the hal on boot the same way I select hardware profile. I was hoping it would be part of the hardware profile but it seems not to be.

If you have any questions about what I've done so far please feel free to email me at "iamufromthefuture@gmail.com" (A handily annonymous email I use)

Ditto with any solutions to my problem if you like although post solutions here as well obviously.

Thanks for reading, I hope this will assure people that it's possible if they're struggling :-)
I'm having the same problem.  i can get VirtualBox to work, but i can't get my network adapter to work.  i do however can get the sound card to work, but i can't play music in Linux while VirtualBox is up (and i have ACPI on at the time).  i could always play music from Linux while in Windows, but i'm worried about damaging the Windows partition by accessing the music AND "virtualizing" it at the same time.  :(
idk... if there's a fix that could be made to get the network adapters to run in VirtualBox, that would be nice.

---

### Post by spidermagicat on 2008-09-28
BINGO!!!

I have fixed the ACPI problem thanks to a post on the VMware forums.

1) Boot with virtualbox with "Standard PC" as your HAL

2) Go to the System32 folder and make copies of "hal.dll" and "ntoskrnl.exe" in that folder.

3) Rename the copies to something less else and no spaces I think is necessary. I renamed mine to "vbhal.dll" and "vboskrnl.exe"

4) Go into your boot.ini and copy your line for windows and paste it underneath. In the name add something to distinguish it like "virtual"

5) To the end of the line add /KERNEL=VBOSKRNL.EXE /HAL=VBHAL.DLL (in my case) change to match the file names you've used

6) Change the driver for computer to what it is automatically under windows. (In my case "ACPI Multiprocessor PC")

Next time you boot windows you will have 2 options, one with acpi and one without.

---

### Post by spidermagicat on 2008-09-28
Just as an example of a boot.ini file. Obviously the partitions will have to be your own.


[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional (Boot)" /fastdetect /noexecute=optin /usepmtimer 
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Professional (Virtual)" /fastdetect /noexecute=optin /usepmtimer /KERNEL=VBOSKRNL.EXE /HAL=VBHAL.DLL

Please note that there are in fact two lines below "[operating systems]" and not 4. That's just the text wrapping

---

### Post by Sand Lee on 2008-09-28
> **starfry said:**
> Good tutorial.

A few points that may or may not be interesting.

1) I use a corporate copy of XP and I have never had to activate it . Ever.

2) The thread below explains how to reconfigure your VM so it presents itself as if it has the same hardware as the raw metal, to fool activation. I have not tried this as I don't need to but thought someone may find it useful.
 [http://forums.virtualbox.org/viewtopic.php?t=9697&highlight=dell+computer+corporation](http://forums.virtualbox.org/viewtopic.php?t=9697&highlight=dell+computer+corporation)

3) Instead of doing Step 4, I used "MergeIDE" just because it's what I've done before. It's mentioned in a load of other threads on this subject and seems to work ok. 

[http://virtualbox.org/attachment/wiki/Migrate_Windows/MergeIDE.zip](http://virtualbox.org/attachment/wiki/Migrate_Windows/MergeIDE.zip)

4) My initial tests exhibit no problems booting natively after installing the Guest Additions when booted virtually.

Thanks dutchmountains, spidermagicat for the compliments and tips :). I'm bogged down w/ undergrad work atm and probably won't be able to "fix" major tutorial problems 'till break. It's nice to see this thread is still lively, I will gladly help port this to the Ubuntu Wiki if anyone wants to take the initiative ;]. 
Thank you starfry for providing that link to the vbox forums, I'll make sure to add it to the tutorial. I didn't mention MergeIDE in the tutorial because it caused my windows to BSOD on boot. It's funny, I talked with a dev on the vbox mailing list about giving more options for configuring the DMI BIOS settings (as a method to stop wpa activation problems!). 
:guitar:

---

### Post by itxaka on 2008-09-30
Great tutorial, worked perfectly!

---

### Post by Zularan on 2008-10-24
Trying to get this going on Intrepid 8.10. There seems to be no 'disk' group for me to add the user to to access the raw disk.

I got as far as Creating the Virtual Disk and went to type in 
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 2 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
```
but got an access denied message.

sudu cat /etc/group comes up with 

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:myusername
tty:x:5:
lp:x:7:
mail:x:8:

Checking properties of /dev/sda say it belongs to group '6'. Is it hidden or am I missing something here? When I did this with previous Ubuntu there was a group called disk and there was no problem.

I got it to work by chmod 666 on /dev/sda to confirm it's a permission/group problem but don't want to leave the system like that.

---

### Post by Zularan on 2008-10-25
I also read somewhere in this thread that someone had no problems with Vista, how do you get around the hardware profile step as Vista doesn't have profiles as far as I can tell ?

---

### Post by Sand Lee on 2008-10-26
> **Zularan said:**
> I also read somewhere in this thread that someone had no problems with Vista, how do you get around the hardware profile step as Vista doesn't have profiles as far as I can tell ?

That's strange, running sudo cat /etc/group lists the disk group w/ id 6 (as you said) on a "fresh" Intrepid and upgraded Intrepid installation. Also, I was the one that mentioned being able to run Vista w/ no problems on my Inspiron 1521. I don't remember the details (this was a while back) but I got Vista to run without having to fiddle w/ Vista's settings - I think the Linux side configuration was identical to the tutorial's though.

---

### Post by mssever on 2008-10-27
> **Zularan said:**
> sudu cat /etc/group comes up with 

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:myusername
tty:x:5:
lp:x:7:
mail:x:8:Is that your entire /etc/group? Mine is 72 lines long.

```
~:$ grep scott < /etc/group
adm:x:4:scott
**disk:x:6:scott**
dialout:x:20:scott
cdrom:x:24:scott
floppy:x:25:scott
audio:x:29:pulse,scott
dip:x:30:scott
video:x:44:scott
plugdev:x:46:scott
fuse:x:107:scott
lpadmin:x:109:scott
admin:x:115:scott
scott:x:1000:
vboxusers:x:130:scott
```Notice the bold line. I believe that's your problem. You need to be a member of the disk group. Typing "groups" will list your current groups: ```
~:$ groups
scott adm disk dialout cdrom floppy audio dip video plugdev fuse lpadmin admin vboxusers
```EDIT: By the way, no need to use sudo to list the contents of /etc/group. It's best to only use sudo when it's necessary. Sometimes, using sudo at the wrong time can cause incorrect results. Otherwise, if you use sudo even when it's not necessary, you might as well log in as root (which is, for good reason, considered to be a Bad Thing).

---

### Post by seancarlgrech on 2008-10-28
can anyone tell if i'm doing something wrong?

after i enter:
```
seancarl@seancarl-desktop:~$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 1 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -registe
```/dev/sda1   *           1       25898   208025653+   7  HPFS/NTFS

this appears:
> Cannot open replacement MBR file '/home/seancarl/.VirtualBox/WindowsXP.mbr' specified with -mbr: VERR_FILE_NOT_FOUND
The raw disk vmdk file was not created

---

### Post by Roig on 2008-10-28
Ok, the tutorial worked like a charm BUT! i'm stuck... yes.. virtualbox  shows the loading screen of my windows XP and when it finishes then the screen changes to a blue screen with a Windows XP logo in it, and dont finishes the load, its a step before i can select the users of windows XP.

Someone had the same problem? Solutions?:confused::KS

---

### Post by Steven_B on 2008-11-01
> **Mr. Picklesworth said:**
> Quick lesson of the day:
Do not. DO NOT install VirtualBox Guest Addins for the "guest" OS if you still plan to dual boot with it; Windows will fail on startup when booting on its own. If you (like I) do this, do not panic. Boot Windows via VirtualBox, uninstall the guest addins, restart, and then (still in VirtualBox) run System Restore. And then never do it again.

I have exactly the opposite problem.  After installing the guest additions, the VM won't boot.  When I hard-kill the VM and restart it, it goes to the "Windows did not shut down successfully" screen.  From there, I choose "Start Windows Normally" and it boots fine.  Every other time I reboot, it hangs at the login screen.  Any ideas?

---

### Post by Sanix on 2008-11-03
What's the command for Windows Vista to fix the mbr record?

---

### Post by Sanix on 2008-11-04
> **seancarlgrech said:**
> can anyone tell if i'm doing something wrong?

after i enter:
```
seancarl@seancarl-desktop:~$ VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 1 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -registe
```/dev/sda1   *           1       25898   208025653+   7  HPFS/NTFS

this appears:

Same problem for me. Some people say, you need to fix the partition order with fdisk. This didn't help me, except for killing my bootloader.

---

### Post by sciencequest on 2008-11-08
Thank you for the information. I am running gutsy and I followed the steps mentioned. It all looked great when I saw windows screen coming up in virtual box and it presented me with the login screen. I entered the credentials and after a few seconds I got stop error 0xE0000001. Any thoughts on what could be wrong?

Thanks
QS

---

### Post by sciencequest on 2008-11-08
one thing I failed to mention is VT-x/AMD-v option is not enabled (its greyed out). I am assuming my processor does not support hardware virtualization but I am able to run Ubuntu from the windows XP partition, so does not appears to be an issue. Just trying to provide as much information as possible.

---

### Post by az_s_za on 2008-11-08
Thanks for this tutorial, it looks great.  I'm stuck at step 2 though and hope someone can help...

My WinXP is on /dev/sda1, when I enter this command:
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WindowsXP.vmdk -rawdisk /dev/sda -partitions 1 -mbr ~/.VirtualBox/WindowsXP.mbr -relative -register
```

I get:
```
Overlapping partition description areas. Aborting
Error reading the partition information from '/dev/sda'
The raw disk vmdk file was not created
```

here is the output from fdisk -l:
 ```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1654    13285723+   7  HPFS/NTFS
/dev/sda2            1655        9729    64862437+   5  Extended
/dev/sda5   *        7433        8942    12129075   83  Linux
/dev/sda6            8943        9729     6321546   83  Linux
/dev/sda7            1655        1792     1108422   82  Linux swap / Solaris
/dev/sda8            1793        7432    45303268+  83  Linux
```

???

EDIT: I just bypassesd this problem by booting the whole disk.  I have no problem with grub and am happily using the VB now.  Thanks.

---

### Post by Sand Lee on 2008-11-12
Just a heads up to everyone. I was able to run Vista Home Premium off my HD using this tutorial and the Vbox provided in the Intrepid repos. I do want to warn others though that this took me two tries. 

The first try I **broke** my Vista and had to recover a cloned backup. The second try, I mounted the guest additions CD but didn't use it except to let Vista search the disc for drivers needed for the new hardware it found. Then after slowly disabling processes tailored to my specific hardware in msconfig (intel gfx, webcam, etc) I installed the guest additions. I did have to **reactivate** my copy of Vista online.

I haven't tried booting natively yet - I'll have to do a backup/clone first. [*What would I do w/out Clonezilla?*]. I will try to respond to questions, but most likely won't be able to. :oops:

Edit:
Rebooting back into Vista natively will force you to reactivate the copy. But for me at least, everything worked just as normally - don't take my experience as the standard though.

---

### Post by run1206 on 2008-11-12
> **Sand Lee said:**
> Just a heads up to everyone. I was able to run Vista Home Premium off my HD using this tutorial and the Vbox provided in the Intrepid repos. I do want to warn others though that this took me two tries. 

The first try I **broke** my Vista and had to recover a cloned backup. The second try I mounted the guest install CD but didn't use it except - I let Vista search the disc for drivers needed for the new hardware it found. Then after slowly disabling processes tailored to my specific hardware in msconfig (intel gfx, webcam, etc) I installed the guest additions. I did have to **reactivate** my copy of Vista online.

I haven't tried booting natively yet - I'll have to do a backup/clone first. [*What would I do w/out Clonezilla?*]. I will try to respond to questions, but most likely won't be able to. :oops:

keep us posted on how Vista works with Ubuntu in Vbox; i just bought a new laptop and still have to install Ubuntu on it, and i'm worried how it may act being run inside Intrepid :(

---

### Post by canabal on 2008-11-12
> **Sand Lee said:**
> Just a heads up to everyone. I was able to run Vista Home Premium off my HD using this tutorial and the Vbox provided in the Intrepid repos. I do want to warn others though that this took me two tries. 

The first try I **broke** my Vista and had to recover a cloned backup. The second try I mounted the guest install CD but didn't use it except - I let Vista search the disc for drivers needed for the new hardware it found. Then after slowly disabling processes tailored to my specific hardware in msconfig (intel gfx, webcam, etc) I installed the guest additions. I did have to **reactivate** my copy of Vista online.

I haven't tried booting natively yet - I'll have to do a backup/clone first. [*What would I do w/out Clonezilla?*]. I will try to respond to questions, but most likely won't be able to. :oops:



Thats great.  I am trying to do the same now (just started looking today so I guess good timing...)  How do you make a new hardware profile in vista?

Edit: ok I dont know if that matters,  Regardless, I never see the vista startup screen (the loading bar).  Working on that now.

Edit 2: I got it working.  Thanks, Great tutorial.

Edit 3: I did it all with the open source version and it works... nice

---

### Post by canabal on 2008-11-13
Only two problems now:

1. Everytime I re-start, windows runs chkdsk and finds a ton of errors.

2. Windows is looking for the Base System Device driver.

Any ideas?

---

### Post by Sand Lee on 2008-11-13
I don't know why you have those chkdsk errors, but you've got to mount the guest additions cd, then let windows search that CD for base system drivers.

---

### Post by Sand Lee on 2008-11-13
To everyone who had the VERR_FILE_NOT_FOUND error, I just posted a fix for it in the tutorial. It turned out that the mbr file was not created if there was already a .Virtualbox folder in your home directory so I had to add an "or" operator to the first code block you have to paste into your terminal. It's not as "elegant" as I would like it, but it will get the job done for now.


**Edit:**
A friend of mine helped me figure out an "prettier" fix. :guitar:

---

### Post by canabal on 2008-11-14
> **Sand Lee said:**
> I don't know why you have those chkdsk errors, but you've got to mount the guest additions cd, then let windows search that CD for base system drivers.

yea that got it, thanks.

As for the chkdsk, I think it may be when I try running firefox in both at the same time, because I have both pointing to the same profile.

You should create a new thread for vista, as it will make it clearer for people trying to do it.

And thanks a LOT again.

---

### Post by Sand Lee on 2008-11-15
@ canabal
I would make anther thread for Vista, but I don't have the time. I'll just add a link to directions for Vista.

---

### Post by Sand Lee on 2008-11-15
> **Sand Lee said:**
> Just a heads up to everyone. I was able to run Vista Home Premium off my HD using this tutorial and the Vbox provided in the Intrepid repos. I do want to warn others though that this took me two tries. 

The first try I **broke** my Vista and had to recover a cloned backup. The second try, I mounted the guest additions CD but didn't use it except to let Vista search the disc for drivers needed for the new hardware it found. Then after slowly disabling processes tailored to my specific hardware in msconfig (intel gfx, webcam, etc) I installed the guest additions. I did have to **reactivate** my copy of Vista online.
[...]
Rebooting back into Vista natively will force you to reactivate the copy. But for me at least, everything worked just as normally - don't take my experience as the standard though.

** Directions for *Vista*:**

[LIST=1]
[*]Follow Steps 1 and 2 (alternate step 2.5 if this doesn't work)
[*]Boot into Vista and disable hardware-specific and unnecessary start-up items in msconfig
[*]Boot back into Ubuntu and create a VM with the settings in the attached Picture. If they don't work try switching settings.
[LIST=1]
[*]Use the same MAC as your real network card for your virtual card if you experience network problems
[/LIST]
 
[*]Boot Vista in VBox - you'll have to reactivate it
[*]Mount the Guest additions CD to install the VBox Drivers, but don't install it
[*]Reboot Vista and install the Guest additions for a better experience.
[/LIST]

---

### Post by canabal on 2008-11-16
I will put it together and give you credit.  I think it will be much easier for people to find if it has vista in the title.

---

### Post by canabal on 2008-11-16
I posted it [here]("http://ubuntuforums.org/showthread.php?t=984437").

If you want to make any changes, let me know and I will do so.

---

### Post by Sand Lee on 2008-11-17
Great work on the tutorial canabal and thanks for the credit! I'm a guy, btw :lolflag: I like the way you included step 2.5 in the main tutorial so I'll do the same for this one sometime soon. I'll also link your tutorial from mine. I can PM you the code for this one if you want.

---

### Post by canabal on 2008-11-17
> **Sand Lee said:**
> Great work on the tutorial canabal and thanks for the credit! **I'm a guy, btw **:lolflag: I like the way you included step 2.5 in the main tutorial so I'll do the same for this one sometime soon. I'll also link your tutorial from mine. I can PM you the code for this one if you want.


Hahaha, I kept reading it as sand ee (sandy) in my head for some reason, hahaha.

---

### Post by Sand Lee on 2008-11-22
For everyone who has been receiving a hang at the MBR screen, I have found a fix that is bound to work for everyone. Will post later!:guitar:
** EDIT: **
Revamped Tutorial now up!

---

### Post by minivitale on 2008-11-22
While this may be the wrong place to ask this question, I am looking to have Ubuntu and Windows partitions both able to natively boot as well as the ability to pull up my Ubuntu partition through VirtualBox in windows and my windows partition through VirtualBox in Ubuntu.

Is this at all possible?

I definitely want to have each able to boot natively as I use some processor intensive programs in each OS, and don't want to sacrifice anything when it really counts, but would like to have quick access to each partition from both OSs.

I currently reboot about 3x an hour and use each OS about equally (really REALLY obnoxious)

---

### Post by canabal on 2008-11-22
> **minivitale said:**
> While this may be the wrong place to ask this question, I am looking to have Ubuntu and Windows partitions both able to natively boot as well as the ability to pull up my Ubuntu partition through VirtualBox in windows and my windows partition through VirtualBox in Ubuntu.

Is this at all possible?

I definitely want to have each able to boot natively as I use some processor intensive programs in each OS, and don't want to sacrifice anything when it really counts, but would like to have quick access to each partition from both OSs.

I currently reboot about 3x an hour and use each OS about equally (really REALLY obnoxious)

This tutorial will get you to be able to use XP inside ubuntu.  then you just need to set up ubuntu inside of xp elsewhere.

---

### Post by Sand Lee on 2008-11-23
**@minivitale**

If you often boot into XP, I wouldn't recommend using this tutorial as you'll have to reactivate everytime you switch back and forth between the native and virtual booting of XP. But nonetheless, what you're asking is certainly possible. I'm not sure if there's a tutorial out there for accessing the Ubuntu partition from XP, but the VirtualBox UserManual should have all the information you need to get started.

---

### Post by minivitale on 2008-11-26
Okay thanks for the tips.  I'll try to keep you guys in the loop through this thread in the case that I find anything useful for my situation b/c I doubt I'm the only one with this goal.

---

### Post by waydownsouth on 2008-11-26
@ Sand Lee,

I was conversing with you on another thread the other day and seem to have the activation fix working under VirtualBox.

what happened:

I ended up installing VirtualBox again after I recently installed a 64bit os and found I couldn't get vmware to install.

I followed the how to on this thread to get my existing 32bit WinXP Pro SP3 up and running in VBox. Installed the Vbox tools, rebooted the virtual machine, activated windows.

From there, I modified the windows script 'activation.bat' found here:
[http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/]("http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/")
 
on the third line, from this:
```
ipconfig /all | find "VMware" > network.tmp

```

to this:
```

ipconfig /all | find "[COLOR="Red"]AMD[/COLOR]" > network.tmp

```

[COLOR="Red"]AMD[/COLOR] being the start of the virtual net adapter name I'm using. 

I didn't change anything else in the script as I already had the folders created to work under vmware.

I hope that helps

---

### Post by Sand Lee on 2008-11-26
**@waydownsouth**

That's great news! Does it work after successive reboots? And how long has it been since you've used this method? Windows will generally whine after three days or after a couple reboots from my experience. Let me know if it still works after 3 days and I'll try to add it to the tutorial ASAP. I no longer have an XP installation to test this on, so I'll just wait on feedback from other users.

---

### Post by waydownsouth on 2008-11-27
It locked up hard the first 2 times I tried a physical boot, I'm guessing that was when windows was trying to start the Vbox service. 
Third and subsequent boots, physical windows doesn't start the service whilst virtual windows does?

I've been back and forth about 6 times already with no lockups or activation required so far, but, as you said, it may take a day or three for problems to manifest, will let you know.

I'm sure you'll be able to tidy up my methodology a bit for others too.

---

### Post by rfs1970 on 2008-11-27
Hi There,

I did everything (created the mbr and vmdk file and set my Virtualbox according to the tutorial).

My problem is: 

I can access my partition normally... no problem at all...
But after ~5 minutes it just freeze.
No mouse, no keyboard, nothing...

If I start my virtual Windows XP in safe mode,
it works well.

If anyone could help me on it,
I will really appreciate!

Thank you

---

### Post by hgurol on 2008-12-07
@Sand Lee

Are the updates to the tutorial merged in the 1st post? I guess not, since I can not see anything related with the dummy mbr creation.

There is a diff file attached somewhere on the first page, which includes the updates/changes/additions to the tutorial, however its not readable/usable enough for me. If there is a special way to use that diff file, I dont know how.

Will you please let me know how I can follow-up with the most recent version of this tutorial...

Thank you...

---

### Post by Serveck on 2008-12-07
I keep getting this error when following your instructions exactly, i had to modify the virtual disk file because it was on a different partition, but everything else should be the same.

i have the "-boot-load-size 4" and i've tried multiple different numbers for that but it still gives me this error. and i also made sure to delete that "savedefault" line.

"18 : Selected cylinder exceeds maximum supported by BIOS"

this is the description i managed to find about the error:

    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

any help would be greatly appreciated as i would really like to get this working.


edit.. nvm i did this using a different method with making a MBR to boot xp directly, it works fine now. now i'm dealing with bypassing windows activation.

---

### Post by Sand Lee on 2008-12-07
> **hgurol said:**
> @Sand Lee

Are the updates to the tutorial merged in the 1st post? I guess not, since I can not see anything related with the dummy mbr creation.

There is a diff file attached somewhere on the first page, which includes the updates/changes/additions to the tutorial, however its not readable/usable enough for me. If there is a special way to use that diff file, I dont know how.

Will you please let me know how I can follow-up with the most recent version of this tutorial...

Thank you...

The soonest time I can fully answer any questions will be on wednesday, I've got finals to take care of. But the diff is just saying what's the difference between the old and the new version. The new version is up, and there isn't too much to read into (the diff that is)... Hope that explains your question.

---

### Post by miaviator278 on 2008-12-11
> **Serveck said:**
> I keep getting this error when following your instructions exactly, i had to modify the virtual disk file because it was on a different partition, but everything else should be the same.

i have the "-boot-load-size 4" and i've tried multiple different numbers for that but it still gives me this error. and i also made sure to delete that "savedefault" line.

"18 : Selected cylinder exceeds maximum supported by BIOS"

this is the description i managed to find about the error:

    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). 

any help would be greatly appreciated as i would really like to get this working.


edit.. nvm i did this using a different method with making a MBR to boot xp directly, it works fine now. now i'm dealing with bypassing windows activation.


I have the exact same error message.  What did you do to fix the problem?

---

### Post by Sand Lee on 2008-12-13
Do you still have the error when completely removing the "-boot-load-size 4" option? It's really for compatibility with old machines. I'll probably remove it from this tutorial - since old machines won't virtualize :p

E: Actually it's neccessary for me to boot my vista partition. I don't want to post the old mbr method because it caused a lot of users problems. I'll try and figure out the problem.

---

### Post by miaviator278 on 2008-12-13
> Do you still have the error when completely removing the "-boot-load-size 4" option? It's really for compatibility with old machines. 
Made no difference. 

  But I don't remember what my original issue was. My current issues are Vista not loading as a VM and the VirtualBox ICH sound driving with raw disk using 55% CPU.

If anyone sees the CPU load issue with raw disk and the intel audio driver let me know.  There has been no acknowledgement that I have seen from VirtualBox.

---

### Post by hpklett on 2008-12-18
I apologize if these ideas have been explored before, but I figure the SP3 activation issue is pain enough to risk repetition.  I didn't really feel like reading 11 pages of posts.

The posted M$ guide suggests that, for OEM licenses, SP3 looks at some entries in the BIOS before doing other checks.  If the BIOS has the proper entries, no activation is needed.

The following post tells us how to compile those BIOS entries into VirtualBox.  The thread is mainly geared towards those with nothing but recovery CDs, but I don't see why it wouldn't work with standard OEM licenses for this purpose as well.

[http://forums.virtualbox.org/viewtopic.php?t=3224](http://forums.virtualbox.org/viewtopic.php?t=3224)



If that doesn't work, it appears the hardware checks are lightened if the MAC addresses for all network adapters are the same.  In addition, laptop users will be at an advantage here, due to docking station leniency.

This could help, but I don't know enough to be able to tell if cloning the MAC addresses would mess with the host arp cache.  If it would, the checks are only done on each login.  Perhaps they could be changed back to VirtualBox's settings after booting?

This idea seems more difficult.



At this point, I'm mostly looking for someone to poke the obvious holes in these ideas.  Perhaps someone with better knowledge of Windows activation would have a more direct approach.

---

### Post by samoul on 2008-12-24
Any one tried this tutorial with the latest version of VirtualBox? I tried with 2.1 and get en error while trying to boot windows inside VirtualBox... It says Error 13 ... can't remember de rest of it.

---

### Post by Natovr on 2008-12-30
Hi,
I just switched to Ubuntu, not completely though.. I'm dual booting with Vista. I can't switch completely because Vista is vital for my IT schoolwork... MS Office etc. No, it's something I can't do in OpenOffice. It involves me taking screenshots of what I'm doing in it. So my question is, will the steps in the first post work with Vista? And a bit off-topic, but, does anyone have any tips for new users that have immigrated from Vista? :D

I love Ubuntu so far, and don't want to use Vista much anymore.

EDIT: Yes, I know my join date is Apr 2008.. I think I joined a while ago for some reason :)

---

### Post by The Joe on 2008-12-30
Works perfectly! Thank you!

My only problem, and fatal problem as I can't activate Windows otherwise, is that I can't seem to move the mouse. I capture it, but it won't move. Quite odd.

Anyone know how or why?

---

### Post by Natovr on 2008-12-30
The Joe, I had exactly the same problem in Windows (as host). Once the keyboard and mouse were captured, I couldn't use them at all.. not even to un-capture them. I had to plug in a new mouse to use it, but couldn't find a keyboard to plug in to un-capture it. So I had to force restart it.
It's a Samsung R60 Plus laptop, Vista 32-bit as a host.

EDIT: I couldn't solve it.

---

### Post by run1206 on 2008-12-30
> **Natovr said:**
> Hi,
I just switched to Ubuntu, not completely though.. I'm dual booting with Vista. I can't switch completely because Vista is vital for my IT schoolwork... MS Office etc. No, it's something I can't do in OpenOffice. It involves me taking screenshots of what I'm doing in it. So my question is, will the steps in the first post work with Vista? And a bit off-topic, but, does anyone have any tips for new users that have immigrated from Vista? :D

I love Ubuntu so far, and don't want to use Vista much anymore.

EDIT: Yes, I know my join date is Apr 2008.. I think I joined a while ago for some reason :)


how is the dual-booting process with Ubuntu and Vista?
I ask cuz i havn'et installed Intrepid in my current laptop (my previous laptop i dual-booted XP/Intrepid and worked fine).  Any issues while dual-booting with Vista?

---

### Post by Natovr on 2008-12-31
> **run1206 said:**
> how is the dual-booting process with Ubuntu and Vista?
I ask cuz i havn'et installed Intrepid in my current laptop (my previous laptop i dual-booted XP/Intrepid and worked fine).  Any issues while dual-booting with Vista?

Not really. I followed the tutorial here (made for Hardy, should still work with Intrepid):
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
The only mistake I made once was modifying a partition with Vista's native partition manager after Linux was installed. It wiped Ubuntu off :(... but I took advantage and put my /home folder on a seperate partition this time :) which was a good idea. Would you like to see my partition map (screenshot on GParted)?

PS: I suggest using GParted Live (I think it does NTFS?) or QTParted (I used this) to resize NTFS when Linux is installed... before Linux is installed it's OK to use Vista's native one (which I did)

---

### Post by run1206 on 2008-12-31
> **Natovr said:**
> Not really. I followed the tutorial here (made for Hardy, should still work with Intrepid):
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
The only mistake I made once was modifying a partition with Vista's native partition manager after Linux was installed. It wiped Ubuntu off :(... but I took advantage and put my /home folder on a seperate partition this time :) which was a good idea. Would you like to see my partition map (screenshot on GParted)?

PS: I suggest using GParted Live (I think it does NTFS?) or QTParted (I used this) to resize NTFS when Linux is installed... before Linux is installed it's OK to use Vista's native one (which I did)

True, i saved that article too. 
Yes, please show your partition table.  I've noticed Vista splits its partition as well ("OS" and "Data" partitions); here is what i have...
[IMG]http://i165.photobucket.com/albums/u43/run1206/partition.jpg[/IMG]

The Data Partition has nothing in it currently; i was thinking about putting my Intrepid partiton there (maybe 35 GB should do).

---

### Post by Natovr on 2009-01-02
Here it is. At first I had a tiny partition for Ubuntu (10 GB) but I claimed more and more of the drive.
I compressed my recovery partition (10GB) and put that on a DVD, and formatted the partition as ext3 :) now I'm using it for big stuff in Linux.
Then I shrinked my Data drive further and made space for a /home partition. I might shrink them a bit more :)
sda1 is C:\ and sda2 is D:\
The one mounted /share used to be the Vista recovery partition.. I'm sharing it with Vista with an ext3 driver :)

---

### Post by Sand Lee on 2009-01-04
Note the links to the Vista How-to's at the top of the Tutorial.

---

### Post by Natovr on 2009-01-05
Oh, didn't notice them. Thanks

---

### Post by goneril on 2009-01-08
Hello Ubuntu Users :)

I have a question: did anyone try to do this with qemu instead of vbox?

---

### Post by SOME1 on 2009-01-17
Hi, 

for a long time I am trying to run my physical windows xp (on hd0,0) with virtualbox without success. Although I tried using this guide again and again, searching for what I have missed I always get same screen (screenshot attached), I am working on ibm thinkpad t43p laptop. 

thanks for helping.

---

### Post by waynedou on 2009-01-17
> **SOME1 said:**
> Hi, 

for a long time I am trying to run my physical windows xp (on hd0,0) with virtualbox without success. Although I tried using this guide again and again, searching for what I have missed I always get same screen (screenshot attached), I am working on ibm thinkpad t43p laptop. 

thanks for helping.

Yes, I am working on t43, too, and I have got the same screen. Anyone can help?

---

### Post by wrichtmyer on 2009-01-18
Upon doing these instructions, I get past the GRUB and I recieved an: Error 18: Selected cylinder exceeds maximum supported by BIOS.

Help please?

There is another boot menu inside the Vista Partition. Yes, I unmounted Vista, too.

I'm running Windows Vista with 2746 MB of RAM (I have 4GB)
and with 32 MB Video Memory (I could do a maximum of 128MB)

VirtualBox is 64 bit, I believe, Ubuntu is 64 bit, and my Vista is 64 bit.

---

### Post by mssever on 2009-01-18
> **wrichtmyer said:**
> Upon doing these instructions, I get past the GRUB and I recieved an: Error 18: Selected cylinder exceeds maximum supported by BIOS.

Help please?
This thread is for XP, not Vista.

---

### Post by SOME1 on 2009-01-18
> **waynedou said:**
> Yes, I am working on t43, too, and I have got the same screen. Anyone can help?
Do you think that perhaps a wrong bios configuration effect this?

---

### Post by Klobas on 2009-01-22
Hello i started reading this thread read about 8first pages then listed all other.. still looking for my answer.. 
I have working Virtualbox with working raw image of my whole harddrive i am using dualboot and i can boot my linux perfectly. but when i try to boot windows strange thing happen. see image down there.
i tried almost everything what i found.. enable disable sata support (its sata drive in X200 lenovo) use both ide profiles enable bios native virtualization etc etc.. and i got this image all the time.. any ideas?
this screen will popup after choosing windows boot in grub menu.

---

### Post by angelmb on 2009-01-26
> **mactea said:**
> As rrhoglund I have a SATA DD and I get the BSOD if I enable and use a SATA controler (0 or 1). If I use the IDE one controler, it works, but as soon as there is a disk access CPU goes 100%. So the VM is just not usable (way to slow).

I have installed VMware scsi driver to test, but it does the same as above.

I should say that I am using VirtualBox 1.6 on Hardy. I might have to try with WB 1.5.6

Btw, Sand Lee you say for Step 7:
Copy your wpa.dll [...]
It actually wpa.dbl not dll

I am stuck here too. Any other ideas? or is it that those with sata drives cannot virtualize our physical HDDs??

---

### Post by phantom@atom-desk on 2009-01-29
Hi, I also used your guide to boot my native XP partiotion using virtualbox. The guide is perfect. I was able to boot successfully. Even i made it work in seemless mode.
But then began the problems. 
First under start>control panel>"system, it showed my system as "intel pentium dualcore.....@ 2.00Ghz 57.24 GHz (?) than after a reboot, it became 12.34 GHz!!!!!!!!
When i clicked D:\ (My other NTFS partition for documents and other files), it says disk in the drive is not formatted format now!!!!!!!!
I don't know what is happening

---

### Post by torpicana on 2009-02-03
Hey all,

Thanks to Sand Lee for the great tutorial.
Just wanted to share my experience with you.

I am running ubuntu 8.10 with the latest updates and the guest XP is SP3 (OEM). virtual box version is 2.1.2 . the pc itself is a desktop pavilion zd7000 with only 500M of RAM (yet)

at the start of the virtualized XP, it looks for new drivers it takes forever ! eventually it finds them and the machine can be used although it is painfully slow. It was way faster with a full virtual (and fresh) XP install. otherwise XP froze after a while and I had to close VBox. due probably to the lack of ram ?
I am now to investigate if the guest additions / native reboot / XP activation tricks work or not...

---

### Post by Ailurus on 2009-02-05
Hi, I tried to make a .vmdk file by using this command, but I got an error message. When I press enter, the "VirualBox Command ..." lines are printed, and after about 2 minutes the error message :(

```
sudo VBoxManage internalcommands createrawvmdk -filename /home/pieter/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda -partitions 1 -relative -register

VirtualBox Command Line Management Interface Version 2.1.2
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

Error while creating the raw disk VMDK: VERR_INVALID_PARAMETER
The raw disk vmdk file was not created

```

Any ideas?

---

### Post by borikru on 2009-02-06
> **beow said:**
> Followed the posts instructions carefully but on my Thinkpad T61 i get the dreaded "read error" message:

```
MBR

A disk read error occurred
Press Ctrl+Alt+Del to restart 
```

I.e. it prints "MBR", then sits there for one or a couple of seconds and then prints the "disk read error" message. (Ctrl+Alt+Del amounts to nothing). The last log message only says that it starts booting from HD:

```
00:00:06.940 Guest Log: BIOS: Booting from Hard Disk...
00:00:13.242 Changing the VM state from 'RUNNING' to 'SUSPENDED'.

```

(A couple of minutes later I turn off Vbox whicg then yields the next log message, so the log is not very helpful...). Have WinXP (don't know which SP but the T61 is from January this year) on /dev/sda1 which is the partition I try to virtualize.

Would be extremely grateful if someone could help with this...


I had the same problem with my Thinkpad t60p.
1) After trying many solutions, I noticed that disk geometry reported by fdisk before Windows is installed is different from geometry reported after Windows XP was installed *running fdisk from LIVE CD). This led me to investigate how disk geometry might cause problems, and as a matter of fact, most posts on this matter say geometry should not be an issue. However, I tried to tweak geometry setting in the .vmdk file and it worked. Windows XP booted from physical partition on Thinkpad T60p.

Entries that I changed in the .vmdk file:
ddb.geometry.biosCylinders="12921"
ddb.geometry.biosHeads="240"
ddb.geometry.biosSectors="63"

The numbers correspond to how Windows discovered the geometry (same as reported by fdisk after windows overwrites the MBR). 
I believe this has something to do with LBA mode, which I cannot change in the BIOS on Thinkpad T60p. 

There are also "ddb.geometry" entries, which correspond on my computer to real geometry as printed on the disk's label. Have not changed those.

2) I also hit the problem with intelppm.sys, found resolution here:
[http://blogs.msdn.com/virtual_pc_guy/archive/2005/10/24/484461.aspx](http://blogs.msdn.com/virtual_pc_guy/archive/2005/10/24/484461.aspx)

3) Had 100% CPU with IO APIC, so had to add additional hal and ntoskrnl. I use the halacpi.dll (vs halmacpi.dll that was installed by default by Windows)

4) I use WindowsXP MBR file that I created with dd command before installing Ubuntu. (there is a post on this thread that explains how to get Windows MBR if linux is already installed)

5) And obviously GuestAdditions caused BSOD after some time the system was up when booting natively, so had to remove Guest Additions. No real resolution yet. (The bug was reported to Sun [http://www.virtualbox.org/ticket/1633](http://www.virtualbox.org/ticket/1633))

---

### Post by bbbl67 on 2009-02-09
The activation script procedure suggests putting the script through the gpedit.msc's startup script facility. However, gpedit.msc only works with XP Pro and above, not with XP Home. Is there an alternative startup place I can install the activation script?

---

### Post by borikru on 2009-02-10
Resolved the BSOD with guest additions problem when booting natively. On my Thinkpad T60p this was caused by SynTP.sys (Synaptic Touchpad driver). Uninstalled the driver and everything works like charm now.

---

### Post by nemebean on 2009-02-11
> **borikru said:**
> I had the same problem with my Thinkpad t60p.
1) After trying many solutions, I noticed that disk geometry reported by fdisk before Windows is installed is different from geometry reported after Windows XP was installed *running fdisk from LIVE CD). This led me to investigate how disk geometry might cause problems, and as a matter of fact, most posts on this matter say geometry should not be an issue. However, I tried to tweak geometry setting in the .vmdk file and it worked. Windows XP booted from physical partition on Thinkpad T60p.

Entries that I changed in the .vmdk file:
ddb.geometry.biosCylinders="12921"
ddb.geometry.biosHeads="240"
ddb.geometry.biosSectors="63"

The numbers correspond to how Windows discovered the geometry (same as reported by fdisk after windows overwrites the MBR). 
I believe this has something to do with LBA mode, which I cannot change in the BIOS on Thinkpad T60p. 
I still can't figure out where you got those numbers from, but changing the biosHeads to 240 did the trick for me.  I left the cylinders alone because I couldn't find any way to get fdisk to report 240 heads so I wasn't sure what the right value was, but it doesn't seem to matter.  So a big thank you from me.

I'm on a T42, BTW, and I think this will fix it for people who were getting the corrupted screen after selecting Windows from Grub too.  Depending on how I did it, I either got a disk read error or the corrupted screen before, so I think the underlying problem is the same.

---

### Post by jnewm on 2009-02-13
Thank you Sand Lee!  This post worked great for me.  I do have a SATA drive (500gb Seagate), so apparently it can work.  I didn't do anything outside the tutorial.  Well, I actually got confused for a while and tried MergeIde and a bunch of other things, but it turned out they were totally unnecessary (I believe).  

Instead, I just had to follow Step 5 more carefully.  First, to get around a grub bootloader error 17, by having Virtualbox load the grub.iso created in the earlier steps.  And, second, when I was past the bootloader, but Windows XP froze, by enabling IO-ACPI.  And, finally, when Windows told me I had to reactivate my copy of XP, by rebooting into non-virtual windows (since my USB mouse/keyboard weren't working yet).  Oh, and at the very end I did install Guest Additions, since my Windows XP was going crazy slow looking for video card and base device system drivers.  And Guest Additions made Windows totally usable and didn't mess up things for me at all (as far as I know).

PS I should note I using Intrepid and Sun Virtualbox 2.1.2 (not the totally open one).
PPS One question, in case anyone knows, I still have to set Virtualbox to load the grub.iso every time I run it.  Otherwise it goes back to my normal grub and error 17.  Is there a way to change this and actually load the grub.iso permanently for the virtual boot?  Thanks!

---

### Post by nicolam on 2009-02-13
hey...

what key(s) in the registry did you edit to get the CPU working correctly?

> **kejava said:**
> I get the same behavior too.  sata hd (ST980811AS) but have to keep it as an IDE controller.  Have dual core but at least one of the CPUs is always pegged at 100%.  Alternates between the two.

UPDATE: stopped the CPU from being pegged at 100% by editing the registry.  however, still can't go from ide to sata w/o bsod.


thanks :)

---

### Post by borikru on 2009-02-13
> **nemebean said:**
> I still can't figure out where you got those numbers from, but changing the biosHeads to 240 did the trick for me.  I left the cylinders alone because I couldn't find any way to get fdisk to report 240 heads so I wasn't sure what the right value was, but it doesn't seem to matter.  So a big thank you from me.

I'm on a T42, BTW, and I think this will fix it for people who were getting the corrupted screen after selecting Windows from Grub too.  Depending on how I did it, I either got a disk read error or the corrupted screen before, so I think the underlying problem is the same.

I got those numbers from "fdisk /dev/sda" before and after installing windows. Before it showed 255 heads, and after windows installation booting with live cd shows 240 heads. Num of cyls from the same place.

---

### Post by Novex on 2009-02-23
Dear Sand Lee, et al.

Thank you so much for outlining the steps so simply! I now have a happy XP install running in ubuntu WITH usb which makes things sooooooooo much easier! Syncing my ipod in ubuntu is the uber-convenience!

Anyway, two things I have noticed that may make things easier. I havent read the 20 odd pages of this post, so forgive me if they've been mentioned already.

1. Im using SP3 and have the Virtual NIC set to the same MAC Address as eth0 and when I restarted I didn't have to reactivate windows (perhaps I just got lucky? I've only been back in once since.

2. Im using 2.1.4 and installed the guest extensions and they didnt mess anything up at all, I can still boot natively and all is well!

Thanks again!

---

### Post by inphektion on 2009-02-25
that would be great if you could install the guest additions and still boot natively.  Anyone else confirm this?  Maybe newer virtual box versions have fixed this since this post was originally created?

---

### Post by peppergrower on 2009-02-27
I followed the instructions, with VirtualBox 2.1.4, but when I boot the virtual machine I get a BSOD with error STOP: 0x0000007B.  Booting in Safe Mode reveals that the last driver it loads (successfully?) is mup.sys.  I've tried experimenting with the type of IDE controller in the VirtualBox settings, but neither type (PIIX3/PIIX4) works.  I also tried some other instructions that suggested using the MergeIDE tool, but that doesn't seem to fix this.

My laptop, like all computers in the last several years, uses a SATA drive.  It appears that some people have managed to get those to work, though...

Does anyone have any suggestions?

---

### Post by duck72790 on 2009-03-03
Would this be possible to with OSX and bootcamp? I have Vbox set up with Ubuntu and xp sp2 set up with bootcamp.

---

### Post by dragos240 on 2009-03-09
I cannot get the grub iso,

I typed in:
[FONT=monospace]
[/FONT]cd ; mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso iso

and it said:

~$ cd ; mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso iso
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using MENU000.LST;1 for  iso/boot/grub/menu.lst~ (menu.lst)
Size of boot image is 4 sectors -> No emulation
Total translation table size: 2048
Total rockridge attributes bytes: 921
Total directory bytes: 4096
Path table size(bytes): 34
Max brk space used 0
245 extents written (0 MB)

---

### Post by Boxed on 2009-03-13
I'm using ubuntu 8.10 and virtualbox OSE 2.04 to try to boot a native windows XP installation.

By now i've followed 2 different tutorials to:
- Use a grub boot iso to boot windows
- Use the native installed grub to boot windows

In both cases i get the error: NTLDR is compressed
Which is very strange because natively Windows starts perfectly. Does anyone know what's going on here?

---

### Post by dishnub on 2009-03-16
I am a complete new-bee with linux.  Can somebody post complte and LATEST steps to follow in one place again.  I see the original post Sand Lee which show 6 steps.  It has diff.txt file attached that I have no clue what to do.  And then I see plenty of do's and don'ts posted throug-out this thread including some that are pasted for MBR problems.  Confusing.  So can somebody please please please post LATEST STEPS IN ONE PLACE?  Thank you very much.

---

### Post by riskomt on 2009-03-16
Hello guys. 

I have these problems. When I try to start Vista in virtualbox I get this error :error 13 invalid or executable format

I have no idea what to do with it. 

The second question is: If I try to share a folder or partition via shared folder in virtualbox it is available at \\vboxsvr\ and I need to have it as a folder or disk in windows. Can someone tell me how to do that ? For example : I have a folder C:/install/ witch in linux is under media/data/install and I need to get it to a virtual machine to C:/install like on the first harddrive. Is there a txt file in vbox to the paths of folders shared that I could edit to my will?

thx

---

### Post by Ailurus on 2009-03-17
Hi all, meanwhile I got a little further. The GRUB-thing works fine, it auto-selects my XP entry. When I press enter however, this screen appears: [IMG]http://redpanda.nl/Error.png[/IMG]. It doesn't do anything after that. Any ideas? I'm using Intrepid, and VB version 2.1.4.

By the way, I noticed something strange. VirtualBox says that the "IDE Primary Master" , WinHD.vmdk, is Normal, 93.16 GB. But if I understood correctly, only the size of my windows partition (about 40 GB) should be shown? I used this command to create the vmdk file

```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda -partitions 1 -relative -register

```

Because XP is on my sda1 partition.

---

### Post by Boxed on 2009-03-17
Ailurus, When is get the "NTLDR is compressed" message my screen also displays garbage like your screenshot shows.
I can't seem to figure out what the problem is though.

---

### Post by Boxed on 2009-03-19
I seem to be able to boot Windows Xp from a FAT partition, but not from a NTFS partition.... 

Anyone got the same problem before?

---

### Post by Ailurus on 2009-03-26
My XP is on a NTFS partition as well, no experience with FAT32 (that is, trying to get it working with VirtualBox).

It would be very nice if somebody could tell us why we get rubbish like this on our screens! :)

---

### Post by enabulator on 2009-03-30
SOMEONE HELP PLEASE! I CAN'T BOOT ANYTHING!:(

(I'm writing this from my mom's pc)

First, apologies if this has already been covered.

I got virtualbox booting into my partition, but with a bsod.

Booting in safe mode in virtual box, it stalled before the bsod at hpdskflt.sys.

What I have done: (moved files from windows/system32/drivers to desktop):
mup.sys
hpdskflt.sys
agp440.sys
intelppm.sys

It then stalled on mup.sys - which I moved out of the drivers folder. (like I said above)

I somehow got into hp recovery (I don't remember how, but it wasn't with a cd). I let recovery boot up, hit browse, and hit cancel - I didn't OK to anything. It then reboot. But when I try to boot, there is no grub (I put the suse grub on ubuntu if that makes any difference). Also, when I try to boot from windows (since I can't boot ubuntu), it still crashes!

If someone could help me boot into something, that would be nice. If they could then tell me what to do to get it working in virtualbox, that would be great.

I hope that all that happened to ubuntu is grub got bumped of the boot priority or something. . . I'm no expert - I don't know what happened.

I don't even know how to fix windows if I could boot into ubuntu because I haven't been able to mount my windows partition after an unsuccessful boot.

BYW: When I could boot into them both I tried both PCI3 and PCI4, or whatever they are. I had  primary ide channel and two other things under the ide controllers (I saw someone on this forum with kind of the same setup). I also had a separate hardware profile.

thanks:(

EDIT: I am making a separate new thread, since this is kind of urgent and I don't know if this will be looked at soon. . .

---

### Post by enabulator on 2009-03-30
Hi - can anyone help?, (I'm fine with regards to the above post)

I have got virtual box to basically boot strait into the windows partition. However, I keep getting a bsod.

I have moved agp440.sys and intelppm.sys from my windows/system32/drivers folder to my desktop. (It asked for confirmation the first time I tried moving files, but now it doesn't)

If I go into safe mode, it stalls and gives me a bsod at hpdskflt.sys and XP won't boot at all when if I move the file from my windows/system32/drivers folder to my desktop.

I have tried the PIIX3 and PIIX 4 or whatever they are.
I have used MergeIDE
I have IO-APIC enabled

As to the ide controller - I have three ide things. I don't remember now (I'm on ubuntu), but something to the effect of:
-something to do with intel
-something to do with intel
-primary ide channel (this I'm sure of)

I have an hp compaq 6710b

thanks

EDIT:I think I have a SATA drive, so. . .

EDIT:Nevermind - I skipped step 1. . . I'm trying to activate now

---

### Post by SomeIdiot on 2009-03-30
Slightly off topic (let me know if I should create a separate thread):
Does anyone know if the opposite is possible? By this I mean booting a physical Ubuntu partition in Windows.  

In addition, would it be possible to both be able to load the partition natively and Virtually? As I understand it there are problem hindering this with XP as the OS to be virtualized is the activation issue. This shouldn't be a problem with Ubuntu as the virtal partition right?

---

### Post by ciucca on 2009-04-07
> **nemebean said:**
> I still can't figure out where you got those numbers from, but changing the biosHeads to 240 did the trick for me.  I left the cylinders alone because I couldn't find any way to get fdisk to report 240 heads so I wasn't sure what the right value was, but it doesn't seem to matter.  So a big thank you from me.

I'm on a T42, BTW, and I think this will fix it for people who were getting the corrupted screen after selecting Windows from Grub too.  Depending on how I did it, I either got a disk read error or the corrupted screen before, so I think the underlying problem is the same.

Thanks to both of you guys!

After creating the .vmdk file the following were not in the file:

ddb.geometry.biosCylinders="1024"
ddb.geometry.biosHeads="255"
ddb.geometry.biosSectors="63"

I added them in the file, now I can get past the "disk read error" issue.  I have a thinkpad R40.  On to the next problem :)

Thanks again!

---

### Post by Sand Lee on 2009-04-13
:KS Updated tutorial to include the possible "disk read error" workarounds noted by [ciucca]("http://ubuntuforums.org/showpost.php?p=7029633&postcount=221") and [borikru]("http://ubuntuforums.org/showpost.php?p=6716355&postcount=202"). Thank you.

---

### Post by dvd_it on 2009-04-26
Hi!
nice guide!
I tried it to mount my debian (I don't use win...) but i get: "Error17: Cannot mount selected partition"
do you have any idea?
d


(I searched on this thread but there are lots of comments and it's quite messy to find out a hint on this specific problem; so i'm sorry if someone already asked for this)

---

### Post by soaenator on 2009-05-08
hi 

first thanks, great tutorial even though i havent got booted into my virtualXP i call it :)

i get error right after i select windows in grub:
```
Error 15 File Not Found

Press any key....
```i bet that there is something with my menu.lst...it looks like this:
```
title           Microsoft Windows XP Professional
root            (hd0,0)
makeactive
savedefault
chainloader     +1

```i have completely went through your tuto but i dont know what have i done wrong. 
i was thinking maybe that command:

```
sudo usermod -G disk,vboxusers -a `whoami`

```should there be after whoami my actuall $USER ?? 

thanks

---

### Post by soaenator on 2009-05-08
aha ok i got around that problem i have forgot to remove savedefault from menu.lst
then i got corrupted screen so i used that read disk error solution.
So i could get past that, which got me to, select my virtual machine and then it showed me a logo just for a second when a BSOD appeared which then restarted virtual machine.

anyone know what to do with BSOD during loading windows screen?

BTW will i be able to boot my windows natively again? i have the hw profiles. So i hope yes.

my system is intrepid on thinkpad t42p (2373-ktu) with ide hdd and have virtualbox-ose 2.0.4

---

### Post by cnkbrown on 2009-05-11
At tutorial step 4, my driver choices shows only "disk".  Where would I get the "Standard Dual channel PCI IDE controller"?   I have a Dell E6400.

---

### Post by nsfnd on 2009-05-15
Hi everyone, thx for all the info.

Ive followed through steps and managed to run my existing xp on VirtualBox.
However its darn slow :) I can tell just by watching the boot, its because of slow disk reading.
And my cpu usage is at %100 on one of the cores whole time starting with boot.

Im using nvidia's fakeraid on my system.

Some info;
Ubuntu 32bit-jaunty
ACPI, IO APIC, VT-x/AMD-V on.
Made grub.iso to auto boot to xp.

Tried with both IDE and Sata options on virtualbox hdd settings, slow with both.

Any thoughts?

---

### Post by dragos240 on 2009-05-31
Can anyone help me boot into win 7 RC? I got it to boot into the system and it said:

STARTING WINDOWS, but then vbox aborted :(.

---

### Post by zonemikel on 2009-05-31
Hello everyone, 


Its kinda hard to read through 11 pages of posts. 

I got the grub iso to load and such but when i select my winxp partition (or any) from the grub menu i get "error 15 file not found". 

Why would it work in the normal system but not in it's iso mode ? For me the "savedefault" was always commented out so im not sure if that is the problem. 

[PHP]
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false
[/PHP]

[PHP]
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Professional x64 Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1
[/PHP]

Anyone have any idea what is wrong ? Its like it does not even load the right boot location. Obviously its not loading the mbr for my windows partition or something. But my windows partition is located on /dev/sda1 or in (hd0,0) .... thats the same config i have when i start my pc  and normal dualboot always works. 

thanks

---

### Post by dragos240 on 2009-05-31
> **zonemikel said:**
> Hello everyone, 


Its kinda hard to read through 11 pages of posts. 

I got the grub iso to load and such but when i select my winxp partition (or any) from the grub menu i get "error 15 file not found". 

Why would it work in the normal system but not in it's iso mode ? For me the "savedefault" was always commented out so im not sure if that is the problem. 

[php]
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false
[/php][php]
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Professional x64 Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1
[/php]Anyone have any idea what is wrong ? Its like it does not even load the right boot location. Obviously its not loading the mbr for my windows partition or something. But my windows partition is located on /dev/sda1 or in (hd0,0) .... thats the same config i have when i start my pc  and normal dualboot always works. 

thanks

Trust me, the savedefault is the issue.

---

### Post by dragos240 on 2009-06-03
Bump? Help?

---

### Post by itsjareds on 2009-06-21
> **dragos240 said:**
> Can anyone help me boot into win 7 RC? I got it to boot into the system and it said:

STARTING WINDOWS, but then vbox aborted :(.

I was actually going to do the same thing, but then I realized that this thread was intended for Windows XP. AFAIK there's no way to create a new hardware profile in Vista or 7. That's when I had to undo what changes I'd made and re-do it to work on my XP partition.

-----

I accidentally posted this on the wrong thread, I meant to post it here but I posted it on [the thread I searched google for]("http://ubuntuforums.org/showthread.php?p=7495022"). I think I'll have a better chance of an answer here:

I just got the same problem with Mup.sys hanging when I boot (in graphical and safe mode).

Here's a screenshot of what my screen looks like when XP freezes in Safe Mode:

[IMG]http://i42.tinypic.com/15z1qb8.png[/IMG]

Thankfully, I was able to boot just fine when I booted physically into Windows.

--

Edit: After a little research, I read that Windows will hang if it tries to load drivers to inexisting (or in Virtualbox's case, inaccessible), and it catches all hardware errors at Mup.sys. One site also said that since you make two hardware profiles, you should be able to disable unnecessary drivers, but I'm not sure which drivers I should disable and where. Anybody know more about it?

---

### Post by jere.the.miah on 2009-07-08
did anyone ever figure out what was the issue with booting and getting jumbled colored letters and numbers on the screen? i'm booting a sata drive on a T61...

---

### Post by jere.the.miah on 2009-07-08
:( i cant get this to work on my lenovo T61 sata drive. in windows i installed the AHCI driver from the lenovo driver downloads site, and i've changed my SATA operation in BIOS from compatability to AHCI now, and it boots up fine in windows. 

so i re-made the virtual disk after that and try to boot it but it freezes at Starting up ..... andthere's funky colored symbols/letters on the screen. 

i'm on ubuntu 9.04 32bit running the new VBox 3.0.0 binary from the VBox site.

---

### Post by wcasper4 on 2009-07-14
Does anyone have problems with the reactivation issue when booting between vbox and natively?

---

### Post by jcm1107 on 2009-07-16
> **itsjareds said:**
> I was actually going to do the same thing, but then I realized that this thread was intended for Windows XP. AFAIK there's no way to create a new hardware profile in Vista or 7. That's when I had to undo what changes I'd made and re-do it to work on my XP partition.

-----

I accidentally posted this on the wrong thread, I meant to post it here but I posted it on [the thread I searched google for]("http://ubuntuforums.org/showthread.php?p=7495022"). I think I'll have a better chance of an answer here:

I just got the same problem with Mup.sys hanging when I boot (in graphical and safe mode).

Here's a screenshot of what my screen looks like when XP freezes in Safe Mode:

[IMG]http://i42.tinypic.com/15z1qb8.png[/IMG]

Thankfully, I was able to boot just fine when I booted physically into Windows.

--

Edit: After a little research, I read that Windows will hang if it tries to load drivers to inexisting (or in Virtualbox's case, inaccessible), and it catches all hardware errors at Mup.sys. One site also said that since you make two hardware profiles, you should be able to disable unnecessary drivers, but I'm not sure which drivers I should disable and where. Anybody know more about it?

Note to administrators and SAND LEE

I just wanted to ask if you will put in the trouble shooting section the fix to this problem(at least what fixed it for me, I had the exact same problem and had a hard time getting help).  I checked the Enable IO APIC. This fixed MY problem and I had the same screen as the screenshot here. THANKS!

---

### Post by Sand Lee on 2009-07-19
> **jcm1107 said:**
> Note to administrators and SAND LEE

I just wanted to ask if you will put in the trouble shooting section the fix to this problem(at least what fixed it for me, I had the exact same problem and had a hard time getting help).  I checked the Enable IO APIC. This fixed MY problem and I had the same screen as the screenshot here. THANKS!

That step is already part of the tutorial... :-k

---

### Post by erat123 on 2009-07-29
Great tutorial!!!!  :KS:KS:KS

And lance2010 I tried what you said about installing mbr to bypass grub and that fixed everything!   :D

---

### Post by wcasper4 on 2009-07-30
> **erat123 said:**
> Great tutorial!!!!  :KS:KS:KS

And lance2010 I tried what you said about installing mbr to bypass grub and that fixed everything!   :D

erat, glad you got things working! have you had any problems with activation or reactivation issues with msoft when switching to and from your virtual and native installs?

---

### Post by j0rd on 2009-08-01
> **itsjareds said:**
> I was actually going to do the same thing, but then I realized that this thread was intended for Windows XP. AFAIK there's no way to create a new hardware profile in Vista or 7. That's when I had to undo what changes I'd made and re-do it to work on my XP partition.

-----

I accidentally posted this on the wrong thread, I meant to post it here but I posted it on [the thread I searched google for]("http://ubuntuforums.org/showthread.php?p=7495022"). I think I'll have a better chance of an answer here:

I just got the same problem with Mup.sys hanging when I boot (in graphical and safe mode).

Here's a screenshot of what my screen looks like when XP freezes in Safe Mode:

[IMG]http://i42.tinypic.com/15z1qb8.png[/IMG]

Thankfully, I was able to boot just fine when I booted physically into Windows.

--

Edit: After a little research, I read that Windows will hang if it tries to load drivers to inexisting (or in Virtualbox's case, inaccessible), and it catches all hardware errors at Mup.sys. One site also said that since you make two hardware profiles, you should be able to disable unnecessary drivers, but I'm not sure which drivers I should disable and where. Anybody know more about it?

I've been trying to install WinXP under my Ubuntu 9.04, but not from physical disk, but by a virtual disk. After installing virtual box 3.0.2 and attempting to install WinXP on my virtual, I recieved this same mup.sys hang on my native (ie. existing physical install of windows non-vbox). To resolve my issue, I simply booted up with a repair disk and re-installed grub. 

This will not bring you any closer to getting vbox to work, but it did get my windows in working condition again.

My laptop is a thinkpad t61p.

---

### Post by Grandon on 2009-08-03
> **sciencequest said:**
> Thank you for the information. I am running gutsy and I followed the steps mentioned. It all looked great when I saw windows screen coming up in virtual box and it presented me with the login screen. I entered the credentials and after a few seconds I got stop error 0xE0000001. Any thoughts on what could be wrong?

Thanks
QS

I have the same issue like this member, but I haven't seen a reply to it.

The host system is a Ubuntu 9.04 - 64 Bit and the guest is Windows XP SP3  - 32 Bit, running on a Dell laptop.

---

### Post by {CGL}ToWeR on 2009-08-04
See my thread, I had a lot of instability around the login screen:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1209274](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1209274)

This was solved by ensuring correct virtualbox settings for the vm, particularly around harddisks.  This includes stop errors that give no more clues.

In your case, it indiicates vmx86.sys - i would hesititate to say that you have vmx extensions somehow enabled when your cpu doesnt support it, or something in that ballpark.

---

### Post by Grandon on 2009-08-05
> **{CGL}ToWeR said:**
> See my thread, I had a lot of instability around the login screen:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1209274](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1209274)

This was solved by ensuring correct virtualbox settings for the vm, particularly around harddisks.  This includes stop errors that give no more clues.

In your case, it indiicates vmx86.sys - i would hesititate to say that you have vmx extensions somehow enabled when your cpu doesnt support it, or something in that ballpark.

Thank you for the reply.
I will try the crazy image converting later, but the other settings are the same ;)

You are correct, I have enabled the virtualization support in BIOS.
My CPU is a Intel Core 2 Duo - T7500 @ 2.20GHz.

Booting the existing WinXP has worked already once with VMServer, but I lost the guide and wanted to see if it's going easier... doesn't seem so :P

I may found a ((very!)dirty) workaround for my issue.
I just moved the vmx86.sys which is located @ C:\Windows\System32\drivers into another directory and no bluescreen anymore.

BUT! The system is extremely(!!!) slow. I do not recommand this work around...

Greetz,
GND

---

### Post by bryonak on 2009-08-06
Could anyone please give a (more or less definite) answer whether this works with VirtualBox 3 + guest additions + WinXP for both virtual and native booting?

---

### Post by jcm1107 on 2009-08-06
> **bryonak said:**
> Could anyone please give a (more or less definite) answer whether this works with VirtualBox 3 + guest additions + WinXP for both virtual and native booting?

I can say yes it does work to boot your native windowx xp installation in virtualbox 3.0.4 with guest additions and all!!!

---

### Post by bryonak on 2009-08-07
Thanks jcm!


> **jcm1107 said:**
> I can say yes it does work to boot your **native windowx xp installation in virtualbox** 3.0.4 with guest additions and all!!!

Just to make sure I understand you correctly, the goal is to boot an existing WinXP partiton in VirtualBox **and** being able to boot the same installation directly (natively), not in VBox.
Guest additions is often said to bork the native install with VBox 1 and 2, leaving you only with the virtual boot of your "previously native" Windows.
So I wonder, does it work with VBox 3?

I'm helping a Windows user (who spends 90% of his time on Ubuntu already) migrate and he'd be happy to retain the option of native booting ;)

---

### Post by jcm1107 on 2009-08-07
I will tell you that yes you can still boot your windows natively or when in ubuntu you can use virtualbox. I will warn you that you will have to reactivate windows everytime you boot it with different hardware (if you activate windows when booted natively you will have to re-activate windows when you boot with virtualbox and vice versa) this does not bother me, I went to using windows in virtualbox any time that I do need windows for something.Oh here are some links that may fix the activation issue but I have not tried it so I don't know if it works.
[http://ubuntuforums.org/showpost.php?p=6259708&postcount=167](http://ubuntuforums.org/showpost.php?p=6259708&postcount=167)

[http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/](http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/)

---

### Post by bryonak on 2009-08-07
Thanks again :)
I'll give it a try next time I get to tweak my friends machine.

---

### Post by soulsinner on 2009-08-10
Hello all, 
first of all i would like to say many thanks to Sand Lee for making a marvelous tutorial.
I use VirtualBox 3.0 and followed ur instruction and i can boot my XP without any trouble at all but the problem is it cannot capture my mouse or keyboard.
I got in the OS but at the log in i can't do anything cos my mouse and keyboard didn't respond at all. How can i fix this. by the way im a newby here.
And for ur info i have a usb keyboard pair with a ps/2 mouse.

---

### Post by pwebster25 on 2009-08-29
> sudo usermod -G disk,vboxusers -a `whoami`
I am a domain user and am trying to set this up.  I get the following in the terminal, when I run this with my DOMAINNAME\username

It returns:
> DOMAINNAME\username not found in /etc/passwd
It returns the same thing when I leave 'whoami' in the command.

---

### Post by pwebster25 on 2009-08-29
> VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda -partitions 2 -relative -register

My windows partition is just 50GB and the whole hard drive is 230 GB (the rest of the partitions are various linux partitions).  The Windows partition is /dev/sda1 so I used "partitions 1" in the above command.

This works and I followed all the steps until I went into virtualbox and chose the WinHD.vmdk  It shows that the WinHD.vmdk is 230 GB.  This seems like an error and I don't want to corrupt my whole system by virtualizing into the same partition that I am running in.

Second, do I need to do something to prevent this windows partition from automatically mounting in ubuntu?

---

### Post by pwebster25 on 2009-08-29
> **pwebster25 said:**
> I am a domain user and am trying to set this up.  I get the following in the terminal, when I run this with my DOMAINNAME\username

It returns:

It returns the same thing when I leave 'whoami' in the command.

Found my own workaround:
```
sudo gedit /etc/group
```
Then I added my domain user after the proper groups (disk and vboxusers).  The lines looked like:
```
vboxusers:x:124:kids,DOMAINNAME\username
```

I verified that it worked by logging out and back in and then doing ```
groups
```
It returns all my domain groups as well as the two groups in question here disk and vboxusers

---

### Post by pwebster25 on 2009-08-31
While I did find my workaround for the domain user (see 252 above) I have not figured out why my WinHD.vmdk shows the size of the entire hard drive instead of just the partition (251 above).  I have not proceeded with setting up my virtualbox, as I can't afford to bork my whole system. I would appreciate any help y'all can lend.  Thanks.

---

### Post by pwebster25 on 2009-09-04
Anyone out there on this forum?

---

### Post by pwebster25 on 2009-09-05
Okay.  I just went ahead with my vbox setup using the WinXP.vmdk file that was setup.  It appears to use the entire hard drive in the virtual media manager (Scary).  When it boots it gets to grub and gets stuck.  

If I use the grub.iso as the cd on bootup I get my regular grub menu with all of my linux choices plus windows at the bottom (just like my regular bootup into Ubuntu).  However, if I choose windows xp then it gives me an "error 25".

If I don't use the grub.iso but just boot into the virtual hard disk then I get a grub error 17.  I am guessing I am missing the mbr or the boot configs on the virtual disk.  Can I safely reinstall it?  If so, how?  I want to still be able to dual boot into windows when necessary (I haven't done so in several weeks).

---

### Post by Chesh on 2009-10-03
Has anyone who has had trouble with this been able to get past the "Error 18: Selected cylinder exceeds maximum supported by BIOS" issues?

---

### Post by pwebster25 on 2009-10-04
I didn't get a reply here to my request about actually using the hard drive partition so I just pushed through and set up a virtual drive per default in virtualbox.  This was a piece of cake.  I will go back and delete my original windows partition.  I haven't used it for a couple months now.  I'm betting with the right knowledge I could have made it work this way but the default is so easy.

---

### Post by borikru on 2009-10-06
> **pwebster25 said:**
> My windows partition is just 50GB and the whole hard drive is 230 GB (the rest of the partitions are various linux partitions).  The Windows partition is /dev/sda1 so I used "partitions 1" in the above command.

This works and I followed all the steps until I went into virtualbox and chose the WinHD.vmdk  It shows that the WinHD.vmdk is 230 GB.  This seems like an error and I don't want to corrupt my whole system by virtualizing into the same partition that I am running in.

Second, do I need to do something to prevent this windows partition from automatically mounting in ubuntu?

Yeah, the size is reported for the whole disk, but it is actually your partition. I have the same issue  and yet it works fine.

---

### Post by tw805 on 2009-10-07
Hi all, 

Seems this thread may be a bit quiet but Im so close with this tutorial i thought it was worth a post...

So, i followed all the steps in the tutorial exactly. It mounts my grub.iso image and will let me choose to start Windows (i edited the copied menu.lst so that it only shows this entry). it'll show the splash screen for about 4 seconds and then BSOD arrives... i have an IDE drive, and it appears this problem appears mainly with SATA drives, so not sure what the problem is. have had a play around with PIIX3 and PIIX4 etc. 

each time i try again it says windows was closed down incorrectly etc and will try again resulting in the same. choosing the other options, safe mode etc, and it'll hang (not sure what on, can find this out if needed). booting natively will initially give the same message but will still boot OK. 

any ideas what i can try next? what is MergeIDE? i have downloaded it but not sure what to do with it or whether it is necessary for this problem. 

Thanks!

Tom

---

### Post by Rhetoric Camel on 2009-10-25
I'm getting the blue screen of death


"A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this Stop error screen, restart your computer. If this screen appears again, follow these steps:
Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated. Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Technical information:
*** STOP: 0x0000007B (0xBACBF524, 0xC0000034, 0x00000000, 0x00000000)"

I'm running Sun VirtualBox Version 3.0.8 r53138

Under settings>hard disks the IDE Controller type is PIIX4. There are two other options which I have tried.
I tried enabling additional controllers, SATA (AHCI), SCAI (Lsilogic), and SCSI (BusLogic)
I enabled ACPI and IO APIC

When it loads it goes to the windows loading screen with the scrolling blue bar, and then the BSOD appears with the info above.

I'm also on Ubuntu 9.04



oh and I noticed in the tutorial it says that this will ruin any chance to boot into windows natively. Is this still true to this date or is possible to run it in virtualbox and boot natively? I don't want to get this up and running to find out I can't restart my computer and boot right into windows.

---

### Post by motoplux on 2009-10-30
@Rhetoric Camel: I have the same problem. Did you manage to solve it?

---

### Post by Rhetoric Camel on 2009-11-01
> **motoplux said:**
> @Rhetoric Camel: I have the same problem. Did you manage to solve it?

no I haven't, I've posted a separate thread in this forum, and I posted the same thing on Virtualbox.org forums and no replies from anyone. I've just about given up, I've ran out of ideas. Just hoping someone would have some kind of answer for me. 
My dell computer didn't come with an XP disk just a reinstallation disk which apparently doesn't work the same so I have no choice but to try the existing install.

---

### Post by UnknownFear on 2009-11-13
By following this thread, will I be able to boot into my current Windows Vista, and use my programs/games without installing a new copy of Vista?

---

### Post by Jordanwb on 2009-11-14
VM starts up, "GRUB loading.", "error: biosdisk read error"

What do I do know? I read those two "disk error" links in the opening post, I changed biosheads to "240"

---

### Post by Markkreuzz on 2009-11-18
Thanks for the Guide !!!! I can now virtually boot my native Windows XP inside Ubuntu \o/.... 

My only gripe was its slow when i first booted. So then I looked around found some info and did [**[COLOR="DarkOrange"]THIS[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1330484").
And i got a reasonable boost. TS(Sand Lee) Check it out. If you like it you can add it to your guide...

Cheers:popcorn: !!!

---

### Post by Markkreuzz on 2009-11-18
> I'm getting the blue screen of death


"A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this Stop error screen, restart your computer. If this screen appears again, follow these steps:
Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers. Check your hard drive to make sure it is properly configured and terminated. Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Technical information:
*** STOP: 0x0000007B (0xBACBF524, 0xC0000034, 0x00000000, 0x00000000)"

I'm running Sun VirtualBox Version 3.0.8 r53138

Under settings>hard disks the IDE Controller type is PIIX4. There are two other options which I have tried.
I tried enabling additional controllers, SATA (AHCI), SCAI (Lsilogic), and SCSI (BusLogic)
I enabled ACPI and IO APIC

When it loads it goes to the windows loading screen with the scrolling blue bar, and then the BSOD appears with the info above.

I'm also on Ubuntu 9.04


The problems you may have could be related to HD drivers. you might've incorrectly configured/booted into the wrong hardware profile. Try booting into safe mode and redo the chanding of IDE Controller part.

And pls leave the IO APIC on enable if you dont know what you're doing.(it's evil)

> 
oh and I noticed in the tutorial it says that this will ruin any chance to boot into windows natively. Is this still true to this date or is possible to run it in virtualbox and boot natively? I don't want to get this up and running to find out I can't restart my computer and boot right into windows.
It will not ruin your chance unless you virtually booted to your host OS. 
And based on the Vbox manual, you really need the boot loader to boot the partition.

---

### Post by duf on 2009-12-25
I tried this out, but when I start XindowsXP in a VirtualBox all I get is a prompt with "MBR 3FA:_

How can I fix that. I really would like to start Windows in a virtual machine

Thanks

---

### Post by manco on 2010-01-06
I'm running Sun VirtualBox (not OSE) 3.1 (latest version) on Ubuntu 9.10 with the latest GRUB loader (from Update Manager)

Will this method work for me?  I'd like to access my XP partition without having to reboot.

Also, as of this posting, do the Guest Additions work?  I used to have XP installed as a virtual OS and the Guest Additions were great.

---

### Post by wlraider70 on 2010-01-14
is the guide at the beginning of this thread, from years ago, still a valid way to set up the virt?

---

### Post by chaosaddict on 2010-02-10
I just used the guide above to set up a VM on a new Ubuntu install. It mostly works. To create a GRUB boot CD iso, I used another, older linux install. Ubuntu 9.10 installs GRUB 2, which has many changes that break the guide's instructions.

I would also like to note that the computer I set up was a Lenovo ThinkPad T61p, with a 160GB SATA HD. I had Ubuntu 9.10 freshly installed along an existing Windows XP install. After following the guide, GRUB would load fine, but as soon as Windows started, I would get the "disk read error" issue. I tried changing the ddb.geometry and ddb.geometry.bios* entries to match what fdisk -l told me, but what eventually worked was changing ddb.geometry.biosHeads to 240. I left biosCylinders at 1024 and biosSectors at 63. That got XP booting, but it would then crash while booting. To solve that, I moved agp440.sys out of C:\windows\system32\drivers\ from the partition mounted in Ubuntu (I tried to do this from Windows, but it would recreate the file right after I moved/renamed/deleted it). I also moved the file agpcpq.sys, but I don't know if that was necessary or not. Otherwise I had it configured to use ACPI, and I had the HD partition disk set as a SATA(AHCI) Port 1, and the IDE Controller Type as PIIX4.

---

### Post by doballve on 2010-02-19
> **jere.the.miah said:**
> :( i cant get this to work on my lenovo T61 sata drive. in windows i installed the AHCI driver from the lenovo driver downloads site, and i've changed my SATA operation in BIOS from compatability to AHCI now, and it boots up fine in windows. 

so i re-made the virtual disk after that and try to boot it but it freezes at Starting up ..... andthere's funky colored symbols/letters on the screen. 

i'm on ubuntu 9.04 32bit running the new VBox 3.0.0 binary from the VBox site.

Did anybody solve this freeze + "funky colored symbols/letters on the screen"? I'm getting it on Ubuntu 9.10 + VirtualBox 3.1.4.

I tried VirtualBox ready binaries and compiled locally,  also with tried Ubuntu's 9.10 VirtualBox (version 3.0.8, if I remember right).. even went back to grub legacy.. all pointless. I'm on a HP notebook with SATA disk, if that helps..

---

### Post by kaustavdm on 2010-02-28
> **kejava said:**
> I get the same behavior too.  sata hd (ST980811AS) but have to keep it as an IDE controller.  Have dual core but at least one of the CPUs is always pegged at 100%.  Alternates between the two.

UPDATE: stopped the CPU from being pegged at 100% by editing the registry.  however, still can't go from ide to sata w/o bsod.

I'm using Ubuntu 9.04 with VirtualBox 2.14_OSE (Dual core CPU). XP is up and running fine. But either of the CPU core is always peaked at 100% while running the virtual OS.

**@kejava** Can you please specify the changes you made in the registry?

**@All**
 - Where to find the Base Drivers?
 - I have multiple NTFS partitions (C, D and E) all the partitions are auto-mounted in Ubuntu using NTFS Configuration Tool. When I boot into virtual OS (XP), I'm not being able to access drives D and E. It is prompting to format those partitions. I'm sure that the partitions are ok as I can access them through Ubuntu or by native booting in XP. Any idea what's the problem?

Thanks!:)

---

### Post by chyro on 2010-03-04
Hi

I'm currently running my XP installation directly from sda2,  partly thanks to this post.  I would like to make a  couple of comments:

First, on the step 1: Instead of using a boot CD, there is the option of  providing a MBR when creating the vmdk file. That's the solution I  used, after failing to locate the mysterious El Torito. The  apt-available "install-mbr" can create a MBR into a file that can then  be provided to VBoxManage to insert in the VMDK file. Maybe it's just  me, but I found that solution much easier since the source for the MBR  is easier to locate.

Second, on the step 6: Not only did the provided solution fail to detect  the hardware profile, but it ran _after_ the activation check. Instead  of debugging it, I opted for a different solution: At boot time, my  Linux mounts sda2 and copies the virtual wpa.dbl. When shutting down, it  copies the physical wpa.dbl. It's less graceful, but much simpler to  set up, and as far as I know more reliable.

Just my 2 yen. Good luck to all.

Edit: **@kaustavdm**: I strongly recommend NOT trying to mount a partition from Linux and Windows at the same time. Both systems seem to cache the file table and overwrite each other's modification (which actually makes perfect sense if you think about it). If you don't want to loose files frequently, you should find another way to share data. You can look into VBox's shared folders, or you can use WinSCP from the virtualized Windows to the physical Linux.

---

### Post by sindrit on 2010-03-19
On 9.10 I've gone through most of the tutorial
However the vboxusers group did not exist on my box.

When I get to selecting the .vmdk file in VirtualBox I get:

Failed to open the hard disk /home/sindrit/.VirtualBox/HardDisks/WinHD.vmdk.
Could not open the hard disk '/home/sindrit/.VirtualBox/HardDisks/WinHD.vmdk'.
VD: error opening image file '/home/sindrit/.VirtualBox/HardDisks/WinHD.vmdk' (VERR_ACCESS_DENIED).

Details:
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: HardDisk
Interface: IHardDisk {62551115-83b8-4d20-925f-79e9d3c00f96}
Callee: IVirtualBox {3f4ab53a-199b-4526-a91a-93ff62e456b8}

How do I create the vboxusers group so that this works?

---

### Post by ironjaw33 on 2010-03-31
> **chaosaddict said:**
> 
I would also like to note that the computer I set up was a Lenovo ThinkPad T61p, with a 160GB SATA HD. I had Ubuntu 9.10 freshly installed along an existing Windows XP install. After following the guide, GRUB would load fine, but as soon as Windows started, I would get the "disk read error" issue. I tried changing the ddb.geometry and ddb.geometry.bios* entries to match what fdisk -l told me, but what eventually worked was changing ddb.geometry.biosHeads to 240. I left biosCylinders at 1024 and biosSectors at 63. That got XP booting, but it would then crash while booting. To solve that, I moved agp440.sys out of C:\windows\system32\drivers\ from the partition mounted in Ubuntu (I tried to do this from Windows, but it would recreate the file right after I moved/renamed/deleted it). I also moved the file agpcpq.sys, but I don't know if that was necessary or not. Otherwise I had it configured to use ACPI, and I had the HD partition disk set as a SATA(AHCI) Port 1, and the IDE Controller Type as PIIX4.

Sometimes, you find exactly what you're looking for.  In a stroke of luck, I have the exact same laptop, hard drive and host OS, and the same problems you spoke of.  I had all but given up on the blue screen on boot when I came upon your post.  Now everything works, except for the Windows activation.  Thanks a lot for your post.

---

### Post by cefn on 2010-04-16
Absolutely massive thanks to borikru whose comment inlined below saved many days of messing about. 

I'd encountered this problem on a Lenovo T400 (close relative of the IBM thinkpads obviously). Same issue with the number of heads. Changing the number of heads to 240 suddenly solved my problem and the virtual image boots!

> **borikru said:**
> I had the same problem with my Thinkpad t60p.
1) After trying many solutions, I noticed that disk geometry reported by fdisk before Windows is installed is different from geometry reported after Windows XP was installed *running fdisk from LIVE CD). This led me to investigate how disk geometry might cause problems, and as a matter of fact, most posts on this matter say geometry should not be an issue. However, I tried to tweak geometry setting in the .vmdk file and it worked. Windows XP booted from physical partition on Thinkpad T60p.

Entries that I changed in the .vmdk file:
ddb.geometry.biosCylinders="12921"
ddb.geometry.biosHeads="240"
ddb.geometry.biosSectors="63"

The numbers correspond to how Windows discovered the geometry (same as reported by fdisk after windows overwrites the MBR). 
I believe this has something to do with LBA mode, which I cannot change in the BIOS on Thinkpad T60p. 

There are also "ddb.geometry" entries, which correspond on my computer to real geometry as printed on the disk's label. Have not changed those.

2) I also hit the problem with intelppm.sys, found resolution here:
[http://blogs.msdn.com/virtual_pc_guy/archive/2005/10/24/484461.aspx](http://blogs.msdn.com/virtual_pc_guy/archive/2005/10/24/484461.aspx)

3) Had 100% CPU with IO APIC, so had to add additional hal and ntoskrnl. I use the halacpi.dll (vs halmacpi.dll that was installed by default by Windows)

4) I use WindowsXP MBR file that I created with dd command before installing Ubuntu. (there is a post on this thread that explains how to get Windows MBR if linux is already installed)

5) And obviously GuestAdditions caused BSOD after some time the system was up when booting natively, so had to remove Guest Additions. No real resolution yet. (The bug was reported to Sun [http://www.virtualbox.org/ticket/1633](http://www.virtualbox.org/ticket/1633))

---

### Post by PyroFX on 2010-05-02
Ubuntu semi-noob here and I am having a problem with this tutorial.

I have scanned thought the posts, though it is likely I may have missed something.

After I use 
```
mkdir -p iso/boot/grub
```
followed by
```
cp /usr/lib/grub/i386-pc/stage2_eltorito /boot/grub/menu.lst iso/boot/grub
```

I get the following errors
```
cp: cannot stat `/usr/lib/grub/i386-pc/stage2_eltorito': No such file or directory
cp: cannot stat `/boot/grub/menu.lst': No such file or directory

```

when I look in that directory, I see that there is no stage2_eltorito.  What do I need to do for this?:confused:

---

### Post by cj.surrusco on 2010-05-15
Does anybody know if this would work with Mac OS X?

---

### Post by acermez on 2010-05-26
hi, i'm using kubuntu 10.04 LTS and i like your tutorial.
however i can't use it because there is a difference between kubuntu and ubuntu .

so please can you help me , i'm not a pro with linux but i can follow you if you help me.

thanks again :)

---

### Post by cj.surrusco on 2010-05-26
> **acermez said:**
> hi, i'm using kubuntu 10.04 LTS and i like your tutorial.
however i can't use it because there is a difference between kubuntu and ubuntu .

so please can you help me , i'm not a pro with linux but i can follow you if you help me.

thanks again :)

Check out this link.

[http://ubuntuforums.org/showthread.php?t=601700](http://ubuntuforums.org/showthread.php?t=601700)

Looks like all you need to do is install libqt3-mt and then you can install Virtualbox with Gdebi.

---

### Post by acermez on 2010-05-26
thanks a lot but i final found a solution with MBR package :) thanks alot very happy with the results ;)

---

### Post by parisv on 2010-05-27
Does this work with windows 7?
 
Sorry I haven't read all 29 pages but did search the thread for 7 which didn't get any results!

---

### Post by cj.surrusco on 2010-05-27
> **parisv said:**
> Does this work with windows 7?
 
Sorry I haven't read all 29 pages but did search the thread for 7 which didn't get any results!

No, these particular directions will not work with Windows 7 because of the way it handles file systems.

---

### Post by parisv on 2010-05-27
Thanks :)

Is there any instructions on doing this with windows 7?

---

### Post by cj.surrusco on 2010-05-27
> **parisv said:**
> Thanks :)

Is there any instructions on doing this with windows 7?

Yes, I found a thread on it.

[http://ubuntuforums.org/showthread.php?t=984437](http://ubuntuforums.org/showthread.php?t=984437)

---

### Post by rockoD on 2010-08-18
Hi Guys, 

I have started exploring Ubuntu/Linux world after 7 years or so, I have a HP Elite 6930p laptop.  I have tried to follow this tutorial to my best.  Some of the information so far

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12259    98464370    7  HPFS/NTFS
/dev/sda2           15605       19457    30949222+  83  Linux
/dev/sda3           12259       15604    26873857    5  Extended
/dev/sda5           12259       15461    25717760   83  Linux
/dev/sda6           15461       15604     1155072   82  Linux swap / Solaris


I have configured my SDA with MBR using 
VBoxManage internalcommands createrawvmdk -filename ./WinXP.vmdk -rawdisk /dev/sda -partitions 1 -mbr ./myBootRecord.mbr -relative -register

Using Virtual BOX ose on Ubuntu 10.04, I get a BSOD just afte hpdskflt.sys, I have tried all safe boot variations.  I did change the storage driver in xp, and the disk type in VB from 4 to 3.  But so far i have been unsuccessful,  do i need to move any sys files etc.  I have 2 hardware profiles.  So far the native boot is working fine.

Please help.

---

### Post by cocamoxb on 2010-09-09
I am stuck on this as is rockoD although I don't get to the BSoD, I get stuck on the MBR loading when I use:

VBoxManage internalcommands createrawvmdk -filename  /home/<username>/.VirtualBox/winxp.vmdk -rawdisk /dev/sda  -partitions 1 -mbr ~/.VirtualBox/winxp.mbr -relative -register


and I get a hung OS selection screen when I use:

VBoxManage internalcommands createrawvmdk -filename  /home/<username>/.VirtualBox/winxp.vmdk -rawdisk /dev/sda  -partitions 1 -relative -register

(without the MBR reference). Any help would be greatly appreciated. Thanks.

---

### Post by phsilver on 2010-10-04
p, li { white-space: pre-wrap; }  I can create vmdk file...
But when I try to load into VirtualBox, the following error pops up:



Fallo al abrir el disco duro /home/nany/.VirtualBox/WinHD.vmdk.
 Could not open the medium '/home/nany/.VirtualBox/WinHD.vmdk'.
 VD: error VERR_ACCESS_DENIED opening image file '/home/nany/.VirtualBox/WinHD.vmdk' (VERR_ACCESS_DENIED).


All permisions were applied, I already validate and include my user into the Virtual Box Group..
What esle can I do???
Thanx!

---

### Post by ndrs on 2010-11-22
> **phsilver said:**
> p, li { white-space: pre-wrap; }  I can create vmdk file...
But when I try to load into VirtualBox, the following error pops up:



Fallo al abrir el disco duro /home/nany/.VirtualBox/WinHD.vmdk.
 Could not open the medium '/home/nany/.VirtualBox/WinHD.vmdk'.
 VD: error VERR_ACCESS_DENIED opening image file '/home/nany/.VirtualBox/WinHD.vmdk' (VERR_ACCESS_DENIED).


All permisions were applied, I already validate and include my user into the Virtual Box Group..
What esle can I do???
Thanx!

Hi,

I had the same issue and adding my user to the disk group solved the problem.

sudo usermod -a -G disk <username>

Cheers

---

### Post by banka.ravi on 2010-12-18
I want todo this but, there is  no dev/sda in my box. I have two hard disks, one running ubantu and xp on other. I think the one run having ubantu is primary and other is secondary. please suggest how would my hard disk listed and what to use. thanks

---

### Post by ~Las~ on 2011-01-13
> **banka.ravi said:**
> I want todo this but, there is  no dev/sda in  my box. I have two hard disks, one running ubantu and xp on other. I  think the one run having ubantu is primary and other is secondary.  please suggest how would my hard disk listed and what to use.  thanks

use ```
sudo blkid
``` in a terminal.so you will get your hard disk info. like which one is /dev/sda etc.

---

### Post by fero4u123 on 2011-01-27
OKay so my computer is not usable at the moment now. Maybe someone here can help me.
 
I have been trying to get Ubuntu working on my laptop (which I have everything was working fine). I installed virtual box and ran my original os (windows XP) inside it following the direction here. I had some trouble getting it working because I kept getting "MBR 1FA:" for a while but then after reading run1206 post in this thread I got it to work.

SOOOO anyway here is what happend. Once I was done playing inside xp on virtualbox, I restarted my computer. When the boot selection screen came up this time i selected Windows XP on dev/sda1. It asked me to choose a hardware profile, so I chose the one called RawBoot (because I had created this hardware profile inside virtual box on the previous run, I was told this is a good idea to do. This was a clone of the current hardware profile running inside of virtual box) 

Okay so now this brings me to my problem that I am reaaaally hoping someone can help me with.

Once I selected RawBoot, The computer came up but the keyboard and mouse were not working...so I press the powerbutton and the computer shut down. Once it turned back on the Screen on my Laptop just stayed blank as if it was turned off. I can tell the computer is working because it makes all the sounds and everything like it use to... but THE MONITOR JUST STAYS BLACK / OFF NOW .

So anyone have any ideas on how to fix this problem ? I have tried restarted several times. It's really hard for me to troubleshoot anything when nothing EVER comes up on the screen, not even the Original manufactorer boot screen is ocming up.

---

### Post by mkylman on 2011-02-04
Kind of a stupid question, but I just need to make sure before I do this: Using the MBR method eliminates the need for making a grub boot disk, right? I'm using Ubuntu 10.10, which uses grub2, and I can't do the first step ._.

Edit: Nevermind...

---

### Post by 2boats on 2011-02-05
Has anyone tried this with Vbox 4.0 and Ubuntu 10.10?

---

### Post by mkylman on 2011-02-05
That's what I'm using, but I'm getting a blue screen on boot for XP Pro SP3. I did the step to change Windows' IDE controller and completely ****** up my system, I couldn't get it to boot natively. I wound up spending all night fixing it...more than I should have. Somehow my partition table got screwed up, but once I fixed that I found that doing a registry backup restore via Hiren's Boot CD restored my ability to boot.

But I still can't get past the BSOD on boot, so I haven't successfully done this yet. I skipped the GRUB step and used MBR instead.

I'll keep you posted if I get it working though.

---

### Post by mkylman on 2011-02-06
Okay, so I got this working. I've got an OEM install of XP Pro SP3 on this laptop, so I was having this activation window pop up and not allow me to log in. I found a tool to help with the WPA problem and am able to boot up my XP partition in VirtualBox 4.0!

---

### Post by 2boats on 2011-02-06
> **mkylman said:**
> Okay, so I got this working. I've got an OEM install of XP Pro SP3 on this laptop, so I was having this activation window pop up and not allow me to log in. I found a tool to help with the WPA problem and am able to boot up my XP partition in VirtualBox 4.0!

:pThat's great!!

So, to recap - you used the MBR instead of GRUB.  And followed the directions from there.
Did you have to change the Microsoft IDE controller back?(should this step be skipped?)
What tool did you use to help with the WPA problem and where did you get it?
Can you still native boot?


I really want to do this, but I NEED this computer for work tomorrow.  I was thinking of just installing winXP in Vbox but that seems like a lot of duplication if this works

Answered own Questions.  Installed without a hitch using MBR.  System Very slow to boot WinXP.

---

### Post by mkylman on 2011-02-07
> **2boats said:**
> :pThat's great!!

So, to recap - you used the MBR instead of GRUB.  And followed the directions from there.
Did you have to change the Microsoft IDE controller back?(should this step be skipped?)
What tool did you use to help with the WPA problem and where did you get it?
Can you still native boot?


I really want to do this, but I NEED this computer for work tomorrow.  I was thinking of just installing winXP in Vbox but that seems like a lot of duplication if this works

Answered own Questions.  Installed without a hitch using MBR.  System Very slow to boot WinXP.

I didn't actually follow this guide completely, I followed some suggestions from VirtualBox's website as well as a few other guides I found online on how to do this, though I primarily followed these steps I did do a few things differently.

Like I didn't change the IDE controller myself, I used MergeIDE instead. And I did some DMI stuff to try to get the hardware to match, but it ended up not working ANYWAY so I had to patch the system to completely disable WPA all together.

Either way it's great to hear that you got it all set.

---

### Post by 2boats on 2011-02-07
Yeah, unfortunately I spoke too soon.  I can't get past the WPA.
I've tried to do the BIOS DMI in the manual but it won't take.  I just keep getting errors.
It's all a learning experience and keeps me out of trouble.

---

### Post by mkylman on 2011-02-08
Is your machine 32bit? If so PM me.

---

### Post by 2boats on 2011-02-12
Got it all working finally.  Speed issue was lack of RAM.  I think you need at least 1 GB to make it happen properly.

Great "How to"  - I've done it many times now and it worked each time.

---

### Post by mkylman on 2011-02-12
Ah, that makes sense...I forgot to ask you how much you had >.<

Anyway that's great man!

---

### Post by n00ne on 2011-02-28
So I've managed to make the installation on Lucid, still running vbox 3.2.12

I've cross connected the explanation here with this one -
[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

mostly for the install-mbr instead of using grub iso that doesn't seem to work with grub2
and with this one 
[http://forums.virtualbox.org/viewtopic.php?t=9697](http://forums.virtualbox.org/viewtopic.php?t=9697)
for a lot of settings and tweeks.

my system seems to be booting well both native and virtual (I set up two hardware profile) but even tho I tried to fake my vb hardware to match the computer one (as explained in vb forum link) windows asked for reactivation.
I bypassed the activation for now but still getting the windows gwniunw message all the time (also when booting native) this is not too bad mainly ugly but I guess also solvable.

one thing I noticed is that its a huge memory hog.
first of all it runs very slow (but maybe I need to use the sata drivers) 
second it uses almost 100% of the cpu even at the startup window before windows even starts. I guess this has something to do with using the raw partition since I've been using a regular vdi on my old computer and never experienced such bad performances.

I think it will be easier and will work better to uninstall windows xp all together and make a fresh install on a vdi image.

---

### Post by mkylman on 2011-03-01
No, part of why it's running so sluggishly is because, I'm just guessing here, you have a dual core machine; when you're virtualizing your windows installation it's behaving as though it has two cores, and your CPU usage'll constantly be at 100%. You have to edit boot.ini and make a new entry using a different kernel...

[http://forums.virtualbox.org/viewtopic.php?p=37935&sid=f3f1bd8d3c44126b61423e60bebcdf2c#p37935](http://forums.virtualbox.org/viewtopic.php?p=37935&sid=f3f1bd8d3c44126b61423e60bebcdf2c#p37935)

See step 10, that fixed it for me.
I'd highly suggest steps 8 and 9 as well, because those also made a huge difference in performance for me.

I tried doing step 7 and my machine was NOT happy with me when I tried to boot natively, so I'd exercise caution with that one.

---

### Post by s_shuffle on 2011-04-12
Thanks to this guide I've managed to put my XP to work :D. and without errors.neither activation problems - at least on the VM - haven't tested booting the physical XP disk again ...
Now for the details and changes:
I've got  ubuntu 10.10 with Vbox 4.0.4
[INDENT]The Grub iso ( since I couldn't find the Stage2-Eltorito file) was created by using ***grub-mkrescue *** (check in this link- also in the initial post -[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html").
 To use this I add to install **xorriso** 
 created a dir(s) **iso/boot/grub**
 I copied  **/boot/grub/locale/grub.cfg **into **iso/boot/grub**
and finally  **grub-mkrescue -o boot.iso iso**
[/INDENT]
I see an error when booting the **boot.iso** file but the grub menu shows up and XP boots without problems 

The initial VM ram was directly of 1GB
All the rest is the same as the initial post
[LIST]
[*]Next things to try ( since I created the second Hardware profile in XP BEFORE running the VM)
[LIST]
[*]Create a vmdk of the entire disk(no -partitions parameter in the VBoxManage ( so no need of boot.iso ??- I've done it before and it worked - but Xp would block during boot)
[*]Use MBR instead of boot.iso ( if previous option doesn't work)
[*]try and install the Vbox guest additions

[/LIST]
[/LIST]
Did I say Thanks :) :) Thanks then ;)

---

### Post by mkylman on 2011-04-12
You should check out the link that I posted above as well; it's more thorough and foolproof. I got it working flawlessly through their methods, and there are a lot of extra tweaks provided to make everything run more smoothly. Also, make absolutely sure that you have created an alternate hardware profile and run MergeIDE on the original hardware profile before you try installing guest additions.

---

### Post by s_shuffle on 2011-04-14
> **mkylman said:**
> You should check out the link that I posted above as well; it's more thorough and foolproof. I got it working flawlessly through their methods, and there are a lot of extra tweaks provided to make everything run more smoothly. Also, make absolutely sure that you have created an alternate hardware profile and run MergeIDE on the original hardware profile before you try installing guest additions.

Thanks
 I'll try that. I've rebooted the machine but the phisical XP doesn't Start ( whatever the  hardware profile ).
I suppose this is mainly due to the newer drivers that the machine tries to add when it boots via Vbox ( but then why should it affect both hardware profiles ??? - anyway..)
 I'm re-"""flashing""" ):P the XP partition to restart again .
I'll come back in some days hopefully with good news...

---

### Post by mkylman on 2011-04-14
Yeah, that's why MergeIDE is necessary; Windows remembers what IDE it's installed on, and will not boot if it changes. MergeIDE makes those checks much more relaxed, allowing for native and virtual booting. Here's the link: [http://www.virtualbox.org/attachment/wiki/Migrate_Windows/MergeIDE.zip](http://www.virtualbox.org/attachment/wiki/Migrate_Windows/MergeIDE.zip)

Make sure you run it from a native boot!

Best of luck!

---

### Post by edempco on 2011-09-23
I'm using Ubuntu 11.04 and VirtualBox 4.0.4. I'm stuck at the re-activation message after XP boots within VBox. I would like to be able to boot natively on start up, and within VBox, without having to re-activate.

There is a reference to "MergeIDE", but there is no documentation as to what this program does or how to use the results. 

Can anyone offer a suggestion as to what solutions apply to my version of software?

---

### Post by impredario on 2012-02-12
This tutorial has worked for many people, but I'm not quite there yet. 

Has anyone encountered (& solved) the following error sequence when booting the VM?[INDENT]> **services.exe - Application Error**
The exception Breakpoint
A breakpoint has been reached.
(0x80000003) occurred in the application at location 0x7c839aad.
Click on OK to terminate the program[/INDENT]Clicking OK then brings up another error dialog, this time from lsass.exe:[INDENT]> **lssass.exe - Application Error**
The application failed to initialize properly (0xc0000142") Click on
OK to terminate the application.[/INDENT]Clicking OK again brings up the first error dialog from services.exe.
Clicking OK a third time produces just a blank blue screen. The VM is unresponsive but using 80-90% of the host CPU. (The host machine has only 1 CPU).

I can boot the VM in Safe mode and Win XP in native mode no problem. No activation required when switching native/virtual, probably because my company has a corporate license.

**System details:**
Toshiba Tecra M3 laptop, 1 CPU 2 Ghz, 2 GB RAM
Host OS: Ubuntu 10.04 LTS Lucid Lynx
Guest machine: 1000 MB RAM; chipset: PIIX3; Enable IO APIC; video memory 32 MB; IDE Controller Type PIIX3; Use host I/O cache; Bridged network adaptor with MAC address = host MAC address
Boot from grub boot cd image (iso) mounted on virtual CD/DVD-ROM drive)
Guest OS: Win XP SP3
VB Guest additions installed.
[B]
Virtualization method:[/B]
Followed Sand Lee's tutorial, with the following additions:[INDENT]Set DMI BIOS settings in VM according to [instructions by Vkov Tinsky]("https://forums.virtualbox.org/viewtopic.php?p=37935").
Added missing registry entries according to [MS KB 314082]("http://support.microsoft.com/kb/314082").
[/INDENT]I have tried changing IDE Controller Type (PIIX3, PIIX4). I have also tried removing/reintroducing drivers agp440.sys, intelppm.sys, and processr.sys, all with no improvement.

I have even used ProcMon (SysInternals Process Monitor) boot logging when booting VM Safe mode (which works OK), VM Normal mode (which hangs as described above), and native Normal mode (which works just fine). From the boot log for VM Normal mode, I can see where services.exe and lsass.exe encounter errors, but cannot figure out the cause.

I have read/reread the tutorial and all 31 pages of replies up to this point, but can't find any additional things to try. Any suggestions would be greatly appreciated.

---

### Post by japzone on 2012-02-12
Personally, I think using [**VMWare vCenter Converter**]("http://www.vmware.com/products/converter/") is the easiest way. The software is free and gives you a working VMDK. Then you can just use VirtualBox to boot the VMDK or convert it to a VDI first if you want a pure VirtualBox setup.

---

### Post by impredario on 2012-02-24
> **impredario said:**
>  ...

Has anyone encountered (& solved) the following error sequence when booting the VM?Clicking OK then brings up another error dialog, this time from lsass.exe:Clicking OK again brings up the first error dialog from services.exe.
Clicking OK a third time produces just a blank blue screen. The VM is unresponsive but using 80-90% of the host CPU. (The host machine has only 1 CPU).

I can boot the VM in Safe mode and Win XP in native mode no problem. No activation required when switching native/virtual, probably because my company has a corporate license.

... Any suggestions would be greatly appreciated.

It turns out the culprit was [Symantec Endpoint Protection (SEP)]("http://www.symantec.com/en/ca/business/endpoint-protection"), which I discovered by accident. After completely uninstalling SEP in native XP boot, the next reboot of XP as a VM worked fine. :grin: 

I now need to install a different AV/malware package that is compatible with VB and meets company IT standards. 

Just posting this update in case anyone has the same problem.

Btw, I did switch to [the MBR method described by Aaron on his blog]("http://blog.amhill.net/2010/01/27/linux-ftw-using-virtualbox-with-an-existing-windows-partition/").  It is simpler than the GRUB method, which doesn't work for some people  because they don't have the /usr/lib/grub/*-pc/stage2_eltorito file. It  also completely avoids the possibility of accidentally booting your  Ubuntu as a VM inside itself, a big no-no!

---

