---
title: "HOWTO: Boot &amp; Install Ubuntu from the Grub Rescue Prompt"
date: 2010-10-17
forum: Tutorials
---

### Post by drs305 on 2010-10-17
[CENTER][SIZE=4][COLOR=DarkRed]**HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt**[/COLOR][/SIZE][/CENTER]

This guide will detail how to boot an Ubuntu Live CD ISO from the "grub rescue>" prompt. The procedure will also work from the "grub>" prompt for Grub 2 users. I started this thread to help netbook users who are unable to mount the Live CD to resolve Grub problems on a previously-working installation. No CD is required. While writing the guide, I realized there might be others who could also use the instructions so I removed references to "Netbook" from the title.

[SIZE=3][COLOR=DarkRed]Preconditions[/COLOR][/SIZE]

This procedure will work for:
[LIST]
[*]Ubuntu family releases using Grub 2 
[*]Malformed Grub 2 menu (grub.cfg)
[*]Missing Linux kernels & initramfs images
[*]Corrupted system folders (not including the module folder)
[/LIST]

In order for this procedure to work, you must:
[LIST]
[*]Have an Ubuntu family Live CD ISO image on a partition accessible from the Grub rescue prompt.
[*]Grub modules from a previous installation must be found and properly loaded.
[/LIST]

The procedure will not work for:
[LIST]
[*]Missing Grub 2 modules (normally in */boot/grub* or */usr/lib/grub/i386-pc* )
[*]Corrupted Ubuntu ISO images
[*]Corrupted partition structure  - "ls" returns only "(hd0)"
[/LIST]


[SIZE=3][COLOR=DarkRed]Boot Procedure[/COLOR][/SIZE]
[LIST=1]
[*]**[COLOR="Navy"]Download the ISO.[/COLOR]**
[LIST]
[*]Download an Ubuntu ISO from: [_http://www.ubuntu.com/desktop/get-ubuntu/download_]("http://www.ubuntu.com/desktop/get-ubuntu/download")
or
[*]Download an Ubuntu Netbook ISO from: [_http://www.ubuntu.com/netbook/get-ubuntu/download_]("http://www.ubuntu.com/netbook/get-ubuntu/download")
[/LIST]


[*]**[COLOR="Navy"]Locate the Ubuntu partition and the folder containing the Grub modules.[/COLOR]**
The Grub folder containing the modules must be located so the correct modules can be loaded. This folder would have been created during the initial installation of Ubuntu and should be located in the Ubuntu partition. This folder would normally be located at either *(hd[COLOR="Red"]X,Y[/COLOR])/boot/grub* or *(hd[COLOR="Red"]X,Y[/COLOR])/usr/lib/grub/i386-pc*


Find your existing Ubuntu partition and the module folder. 
```

ls                               # List the known drives (hdX) and partitions (hd[COLOR="Red"]X,Y[/COLOR])
ls (hd[COLOR="Red"]X,Y[/COLOR])/                      # List the contents of the partition's root
ls (hd[COLOR=Red]X,Y[/COLOR])/boot/grub             # Normal location of the Grub 2 modules.
ls (hd[COLOR=Red]X,Y[/COLOR])/usr/lib/grub/i386-pc  # Alternate location of the Grub 2 modules.

```
[LIST]
[*]**ls** - should return all known drives (hd[COLOR="Red"]X[/COLOR]) and partitions (hd[COLOR="Red"]X,Y[/COLOR])
[*]**ls (hd[COLOR="Red"]X,Y[/COLOR])/** - should show the contents of the root directory of the partition.
[LIST]
[*]If you get an "*[COLOR="Red"]error: unknown filesystem[/COLOR]*" this is not your Ubuntu partition; more on that later.
[*]If this is the Ubuntu partition, you will see the Ubuntu folders, including *lost+found/*, *home/*, *boot/* and *vmlinuz* and *initrd.img*. Use this address as the first part of the next command.
[/LIST]
 
[*]**ls (hd[COLOR="Red"]X,Y[/COLOR])/boot/grub** - should display several dozen *.mod files. **[COLOR="Green"]This is the folder you are looking for.[/COLOR]**
[LIST]
[*]If you don't find the modules, try the alternate location:  **ls (hd[COLOR="Red"]X,Y[/COLOR])/usr/lib/grub/i386-pc**
[/LIST]
[/LIST]


[*]**[COLOR="Navy"]Load the modules.[/COLOR]**
```
set prefix=(hd[COLOR=Red]X,Y[/COLOR])/<path to modules>
```
This command must correctly point to the folder containing the Grub modules. The address should be the one in the previous section which displayed the modules.
Examples:  
set prefix=(hd0,5)/boot/grub  
set prefix=(hd1,1)/usr/lib/grub/i386-pc

Load modules:
```

insmod linux
insmod loopback
insmod iso9660
insmod fat        # If ISO is located on fat16 or fat32 formatted partition.
insmod ntfs       # If ISO is located on an NTFS formatted partition.
insmod nftscomp   # If NTFS compression is used on the partition. Load if you aren't sure.

```

A "*[COLOR="Red"]file not found[/COLOR]*" error means that the path in the *prefix* is incorrect or the specific module does not exist. The prefix setting may be reviewed with the **set** command. Rerun the "*set prefix=*" command with the proper path.


[*]**[COLOR="Navy"]Locate the Ubuntu ISO file.[/COLOR]**
Using the same combinations of *ls* commands, locate the Ubuntu ISO image. 

```

ls (hd[COLOR="Red"]X,Y[/COLOR])/     

```
[LIST]
[*]You are looking for contents including the ISO, such as *ubuntu-10.04.1-desktop-i386.iso*
[*]Expand the path if the ISO image is not located in the / folder.
[*]If you receive an *[COLOR="Red"]error: unknown filesystem[/COLOR]* you may need to load the filesystem module (such as *ntfs* or *fat*. Return to the previous section for guidance.
[/LIST]


[*]**[COLOR="Navy"]Create the loopback device.[/COLOR]**
```

loopback loop (hd[COLOR=Red]X,Y[/COLOR])/<path to ISO>/<ISO-name.iso>
```Example:  
loopback loop (hd1,1)/ubuntu-10.04.1-desktop-i386.iso


[*]**[COLOR="Navy"]Load the Linux kernel and initrd image.[/COLOR]**
```

set root=(loop)
linux /casper/vmlinuz boot=casper iso-scan/filename=/<ISO-name.iso> noprompt noeject
initrd /casper/initrd.lz

```
*If the path to the ISO or filename is not correct, the boot will halt at the BusyBox screen and produce a message stating "[COLOR="Red"]can't open /dev/sr0: No medium found[/COLOR]".*

Note: If the ISO file is not in the / folder, include the [COLOR="DarkRed"]path[/COLOR] in the *iso-scan/filename=* entry. See second example.

Examples: 
linux /casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-10.04.1-desktop-i386.iso
linux /casper/vmlinuz boot=casper iso-scan/filename=/[COLOR="DarkRed"]my-iso/[/COLOR]ubuntu-10.04.1-desktop-i386.iso


[*]**[B][COLOR="Navy"]Boot.[/COLOR]**[/B]
That should be it. If the commands ran without any messages/errors, the commands were accepted as entered. It's now time to boot:
```

boot

```
[/LIST]

[SIZE=3][COLOR=DarkRed]Install Ubuntu  - From Live CD ISO[/COLOR][/SIZE]

**Note on Oneiric Daily ISO Installs**: The current daily build of Oneiric Ocelot requires login to get to the Desktop. Choosing the default user will not allow use of 'sudo' as no password exists for the user. Select 'Other', then username 'Ubuntu' and leave the password field blank. This will allow the use of 'sudo' to unmount the /isodevice during the installation process.

Installation onto your hard drive is possible from a booted ISO file. A CD is not required. An Internet connection is recommended but not required. Without a connection packages installed from the ISO will not be updated and additional packages will not be downloaded. 

[LIST=1]
[*]Boot to the Live CD Desktop using the above ISO boot procedure. 

Note: If you have a large amount of RAM you may be able to use the *toram* option. This will allow the system to boot into memory and permit automatic unmounting of the *isodevice*1 during the installation. */isodevice* must be unmounted for a successful installation. If */isodevice* cannot be unmounted by the installer, the installation will fail unless the user forces its unmounting. This forced unmounting is included in the procedure detailed later in this section.

[LIST]
If you would like to try the *toram* option, replace the *linux* line in the above and use this one instead:
> linux /casper/vmlinuz boot=casper iso-scan/filename=/<ISO-name.iso> noprompt noeject [COLOR="Red"]toram[/COLOR] --
[*]If */isodevice* can be unmounted by the installer at the prompt, the installation will continue. 
[*]If you have insufficient memory (it failed on my system with 3GB) and start the installation, the installer will be unable to unmount */isodevice*, the install will fail and the system may freeze. Reboot and complete all the steps in the "Boot Procedure" section. Do not repeat this subsection and continue below.
[/LIST]


[*]Open a terminal: Applications, Accessories, Terminal


[*]Unmount */isodevice*
```
sudo umount -l -r -f /isodevice
```

[*]Start the installation procedure by double-clicking the "*Install Ubuntu*" icon.


[*]The installation will proceed as would any installation of the same release, similar to the Alternate CD. 


[*]During the latter stages of the installation (Step 8 in Ubuntu 10.04), you may see an "Advanced" button. If so, this is how you access the Grub installation options.
[/LIST]


[SIZE=3][COLOR=DarkRed]Install Ubuntu - Network Install[/COLOR][/SIZE]

This procedure can be used on low-memory systems or by users who otherwise wish to download the installation files from the Internet. The process uses the free services of "[_netboot.me_]("http://www.netboot.me/")". The installer will attempt to connect to the Internet and download the installation files. Once the initial files are downloaded, the installation is similar to that of the Alternate CD installation. 
[LIST=1]
[*]Download the *netbootme.iso* from the link under the "Booting from CD" section of [_this page_]("http://www.netboot.me/gettingstarted").
[LIST]
[*]You can download the ISO via any means available: Windows, terminal with *wget*, etc.
[*]Note where the *netbootme.iso* is located on your drive. You will need to know the (hdX,Y) partition and path (if not stored in the root directory).
[*]While this guide focuses on ISO booting, *netboot.me* offers other installation options, such as USB booting, which the user may wish to consider.
[/LIST]


[*]From the "grub rescue>" or "rescue" prompt, run the following commands. **For detailed guidance, refer to the previous sections.**
[LIST]
```

set prefix=(hd[COLOR="Red"]X,Y[/COLOR])/boot/grub
insmod loopback
insmod iso9660
insmod fat           # If ISO is located on fat16 or fat32 formatted partition.
insmod ntfs          # If ISO is located on an NTFS formatted partition.
insmod nftscomp      # If NTFS compression is used on the partition. Load if you aren't sure.
loopback loop (hd[COLOR="Red"]X,Y[/COLOR])/<path if not in root directory of hdX,Y>/netbootme.iso  # Example:  loopback loop (hd1,1)/myiso/netbootme.iso
linux16 (loop)/GPXE.KRN
boot

```
[/LIST]
[*]Installer Notes
[LIST]
[*]Once the *netboot.me* installation begins, select the installation you desire. For the standard Ubuntu installation, make the following selections:
[LIST]
[*]Installers > Linux > Ubuntu > Version (Look in the status bar for the 32-bit/i386 or 64-bit/amd64, as the links are named the same).
[*]Other operating systems are also available for installation from the main menu display.
[/LIST]

[*]During the latter stages of the download and installation, download options are presented. Normally the user will want to include the "Ubuntu Desktop".
[/LIST]
[/LIST]


Other *drs305* Grub 2 Links:

[_5 Common Tasks_]("http://ubuntuforums.org/showthread.php?t=1302743")
[_ISO Booting with Grub 2 Menu Entries_]("http://ubuntuforums.org/showthread.php?t=1549847")
[_Password Protection_]("http://ubuntuforums.org/showthread.php?t=1369019")
[_Purge and Reinstall Grub 2 from the Live CD_]("http://ubuntuforums.org/showthread.php?t=1581099")
[_Title Tweaks_]("http://ubuntuforums.org/showthread.php?t=1287602")

[_Grub 2_]("https://help.ubuntu.com/community/Grub2") (help.ubuntu.com)

---

### Post by kamaru44ken on 2011-03-29
i tried the command 'insmod linux' but an error occured:

grub rescue> insmod linux
error: invalid object file.

What causes the error? Additional details:
grub rescue> ls
(hd0) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
grub rescue> ls (hd0,2)/
./ ../ lost+found/ var/ etc/ media/ bin/ boot/ ...
grub rescue> ls (hd0,2)/boot/grub/
...(many .mod files) ... grubenv core.img grub.cfg
grub rescue> set prefix=(hd0,2)/boot/grub
grub rescue> set
prefix=(hd0,2)/boot/grub
root=hd0,2
grub rescue> insmod linux
error: invalid object file
grub rescue>

I also tried setting the prefix to usr/lib/grub/i386-pc but the same error occured

---

### Post by drs305 on 2011-03-30
> **kamaru44ken said:**
> i tried the command 'insmod linux' but an error occured:
I also tried setting the prefix to usr/lib/grub/i386-pc but the same error occured

If you are still having problems, try to add the module by using the entire address:
```
insmod (hd0,2)/boot/grub/linux.mod
```

For what you have posted, you can try this sequence to boot:

```
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
insmod (hd0,2)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda2 ro
initrd /initrd.img
boot
```

---

### Post by jmrat on 2011-04-18
> **drs305 said:**
> If you are still having problems, try to add the module by using the entire address:
```
insmod (hd0,2)/boot/grub/linux.mod
```

For what you have posted, you can try this sequence to boot:

```
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
insmod (hd0,2)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda2 ro
initrd /initrd.img
boot
```

I used bottom part worked great untill shut down. than the same thing happened and had to do all over again what should i do? also my computer usually asks if i want to boot win7 or ubuntu  and it stoped what could be causing this?

---

### Post by drs305 on 2011-04-18
> **jmrat said:**
> I used bottom part worked great untill shut down. than the same thing happened and had to do all over again what should i do?

Changes made at the grub prompt are non-persistent (as you found). Do the procedure again. Once booted into your normal installation, run:
```
sudo update-grub
sudo blkid -c /dev/null

```
Compare the UUID for your Ubuntu partition in /boot/grub/grub.cfg (in the default menuentry) with the results from the second command and make sure they are the same. The update-grub command should have corrected any mis-identified UUIDs, but check to be sure they are all correct.

If you still have problems, you could try disabling the UUID entry in /etc/default/grub to see if that fixes things (Note it may be slightly different wording, depending on the version of Grub2 you are using). In any case, remove the # symbol.
> GRUB_DISABLE_LINUX_UUID="true"

---

### Post by egor123 on 2011-04-19
HI!
i have problems booting my ubuntu as i always get this grub prompt
so i try to boot it from here
when i start looking for the ubuntu .iso file is most directories like ls (hd0,1)/home or most of other folders i get error: out of disk
what should that mean?
thank you

---

### Post by drs305 on 2011-04-19
> **egor123 said:**
> HI!
i have problems booting my ubuntu as i always get this grub prompt
so i try to boot it from here
when i start looking for the ubuntu .iso file is most directories like ls (hd0,1)/home or most of other folders i get error: out of disk
what should that mean?
thank you

egor123,

'out of disk' can be caused by many things. Often it means the BIOS cannot read the drive. You should probably open up your BIOS setup during boot and check the reported drive size. If the BIOS does not report the full size of your drive, any files physically located beyond the limit seen by the BIOS will not be found.

At the grub prompt, when investigating I usually start with "ls" to see what partitions Grub2 sees, then go deeper step by step. Next "ls (hd0,1)/", then "(hd0,1)/boot" and then "(hd0,1)/boot/grub" for instance.

If Grub 2 can't find the file(s) with the 'ls' command, it won't be able to use them to boot.

---

### Post by chah on 2011-05-16
Hi DRS305, Thanks so much for all your time and effort, in writing the guide as well as answering questions!

I've got a new Dell Vostro 3300. I posted something in the Dell subforum, but I'm not sure whether what I'm experiencing is specific to Dell. 

I followed the instructions in this thread, and it goes through all the way to the end. After typing "boot", some words and numbers fly by on the screen. Then the screen goes blank and it hangs there, indefinitely. 

I'm able to boot this machine using a USB key that I created using Unetbootin. I've been going in and editing grub.cfg and rebooting trying to find out what's the problem, until I came across this set of instructions. Now I can now enter line-by-line to see what's wrong. But at this time, all the commands go through, but it still hangs. 

Any thoughts? 

Thanks!

---

### Post by drs305 on 2011-05-16
> **chah said:**
> Now I can now enter line-by-line to see what's wrong. But at this time, all the commands go through, but it still hangs. 
Any thoughts? 


chah,

It sounds like a video problem more than a grub problem. Grub will either pass control to the kernel or if it can't boot will produce an error message or grub prompt. Since you have neither of those the chances are good that it's kernel related.

If you have Maverick or earlier, and a blinking cursor on a blank screen, try editing the menu during boot (hold down the SHIFT key if you don't see the menu). Press 'e' to edit the top entry, then cursor to the 'linux' line. Remove **quiet splash** and add **nomodeset**. Then press CTRL-x to boot.

If it boots to the Desktop, System, Administration, Additional Drivers and add a driver for your video card to see if that fixes things.

If you have Natty, there have been some problems with the Grub/kernel interface. I'm going to give you a link, but it is major work wading through it all. For starters, you could try the above, but also remove **vt.handoff=7** and add **vga=771**. Try that first, then try **nomodeset** if that doesn't work.

Let us know if you have success with any of these methods.

---

### Post by chah on 2011-05-16
Hi DRS,

Thanks for the tips. I also thought it might be a video problem when it happened. However, I listened for the ubuntu start-up sound and did not hear it. Incidentally, I'm using Natty. 

So just to update what happened, I finally did the regular install, instead of booting from the ISO with persistence. It was a bit strange, the regular install crashed twice when I tried to do it from my office (I turned on updates and third party drivers). However when i came home, the installation seemed to work. For some reason though, it told me that my laptop does not have the hardware to support Unity, even though Unity was working when I boot from the Unetbootin USB key. I tried digging through the boot/grub/*.cfg file on the Unetbootin thumbdrive in the past, but copying parameters from that file into my own boot grub.cfg file didn't seem to work either. I don't suppose you have any information about how Unetbootin is able to boot or how I can copy its GRUB2 parameters to my HDD boot partition? This is out of curiosity as I'm fine without Unity.

I may come back to this at some point in the future. Thanks for your help.

---

### Post by drs305 on 2011-05-16
chah,

Thanks for the update. I received the same messages about not having the hardware to support Unity. In my case, it simply meant that I had to install the proprietary drivers for my video card (Nvidia). 

I'm running Unity and I can't remember what the panel looked like when I first installed Natty Alpha - so I don't remember what the non-Unity menu looked like. In earlier releases you would get to the Additional Drivers page via System, Administration, Additional Drivers. In my case (with an older Nvidia GS 7600) Natty found it without problem. As soon as I installed and rebooted Unity worked fine.

Best of luck.

---

### Post by johny why on 2011-08-28
hi, noob here, not sure this thread can help me. 

i have a linux livecd iso, and a laptop running ubuntu. i want to install this is to the hard drive from inside linux (or at the linux boot prompt,which i gather is possible?)

any suggestions?

thanks!

---

### Post by Flashyman on 2011-11-07
> **drs305 said:**
> If you are still having problems, try to add the module by using the entire address:
```
insmod (hd0,2)/boot/grub/linux.mod
```

For what you have posted, you can try this sequence to boot:

```
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
insmod (hd0,2)/boot/grub/linux.mod
linux /vmlinuz root=/dev/sda2 ro
initrd /initrd.img
boot
```
Thank you so much!
I had ubuntu installed and messed up something and ended up getting grub command (grub>) anytime I booted, I nearly grabbed the live cd to give up and completely reinstall the whole thing.

the other commands weren't working as in I couldn't find any ubuntu .iso file so it was giving errors.

By entering the commands you specified there with some minor adjustments as to what my drives are named, I am now able to boot back into ubuntu!!!! Thank you very much drs305, you are hereby my hero!


(btw, somehow my drives are named like: (hd0,msdos1) and (hd1,msdos1) I would love to get rid of this msdos text if possible, if only for the looks of it, I hate everything MS, so that includes msdos.... but I guess these steps require advanced techniques which would probably make me end up in the same situation again (grub>))

---

### Post by drs305 on 2011-11-07
> **Flashyman said:**
> (btw, somehow my drives are named like: (hd0,msdos1) and (hd1,msdos1) I would love to get rid of this msdos text if possible, if only for the looks of it, I hate everything MS, so that includes msdos.... but I guess these steps require advanced techniques which would probably make me end up in the same situation again (grub>))

Yes the partitions are now named 'msdos'... The good news is that if you have problems in the future you may be able to avoid the command line entirely and use the Boot Repair app to fix things. It's been developed within the past year and does a very good job of salvaging Grub 2 problems.

[Boot-Repair-Disk ]("http://ubuntuforums.org/showthread.php?t=1831869")

---

### Post by volinkov on 2011-11-08
Ok, I installed 10.04 on an external hard drive, and used grubrescue to boot it. I decided that I didn't want 10.04, so I installed 11.10 on my hard drive. Now, when I try to load the grub modules, grub can't find the files. I know that they are there, because when I boot up with a live cd, I can find them. Any suggestions?

---

### Post by drs305 on 2011-11-09
> **volinkov said:**
> Ok, I installed 10.04 on an external hard drive, and used grubrescue to boot it. I decided that I didn't want 10.04, so I installed 11.10 on my hard drive. Now, when I try to load the grub modules, grub can't find the files. I know that they are there, because when I boot up with a live cd, I can find them. Any suggestions?

volinkov,

Welcome to the Ubuntu Forums. We need more information. Please download and run the boot info script. Copy the contents of the RESULTS.txt it generates and post it here. The file will show us the status of your boot files and help us determine what went wrong.

[Boot Info Script]("http://bootinfoscript.sourceforge.net")

---

### Post by volinkov on 2011-11-09
When I try to run the script, it returns:
boot_info_script version 0.60

"gawk could not be found, using "busybox awk" instead. 
This may lead to unreliable results.

[: 326: busybox awk: unexpected operator
boot_info_script.sh: 353: syntax error: "(" unexpected ( expecting "fi")

I tried running the script straight from the downloads directory while booted with a live cd, and then I put the files onto my external drive and tried running them from the home directory there. I got the same error both times.

---

### Post by drs305 on 2011-11-10
volinkov,

You can install 'gawk' although the script can run with 'awk'. 

You might try installing and running the Boot Repair Tool. It may be able to fix your grub problem by itself, and if not it contains the Boot Info Script files and the script will run from within that app.

[Boot Repair Tool]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by volinkov on 2011-11-12
Sorry if Im asking  you too many questions, but do I install gawk and the boot repair while my computer is booted with a live cd? I guess I forgot to mention that I dont have an internal hard drive. My computer has fried two, so Im trying to boot strictly from an external usb drive. Do I somehow install the boot repair to the usb drive? Thanks for your patience!

---

### Post by drs305 on 2011-11-12
> **volinkov said:**
> Sorry if Im asking  you too many questions, but do I install gawk and the boot repair while my computer is booted with a live cd? I guess I forgot to mention that I dont have an internal hard drive. My computer has fried two, so Im trying to boot strictly from an external usb drive. Do I somehow install the boot repair to the usb drive? Thanks for your patience!


If you are going to run the script from the LiveCD, you can install 'gawk' there as well. It's installation will only last until you reboot. It's not critical to have gawk, but it will eliminate the messages. The same for the Boot Repair app. 

I believe Boot Repair can be installed and run from the LiveCD, but better yet would be to create a Boot Repair CD so you can boot directly from it.

If you install Boot Repair while running the LiveCD you may be able to fix the problem at that point. Again, once you reboot using the LiveCD the Boot Repair app will no longer be available until you reinstall it.

---

### Post by volinkov on 2011-11-12
I ran the boot repair, and it updated the grub modules on my hard drive, which I confirmed. I then went to boot from the hard drive, but I am still having the same problem with grub rescue. 

Using the "ls" command, it returns (hd0) (hd0,msdos1)
The second one is my external drive.
Using ls (hd0,msdos1)/ returns all of the directories and files in the home directory. Awesome.
Next, when I try to use "ls (hd0,msdos1)/boot/grub/" ,which is where the grub directory and modules are , it returns "error:file not found". If I just use "ls (hd0,msdos1)/boot/" it doesn't error, but it also doesn't return any of the files/directories that I know are in there.

Is my grub broken?

Also, I got the results.txt file:

Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107859968 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773164 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   968,452,095   968,450,048  83 Linux
/dev/sda2         968,454,142   976,771,071     8,316,930   5 Extended
/dev/sda5         968,454,144   976,771,071     8,316,928  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        c115a6e2-5b2a-4b13-a810-6373cec0e25e   ext4       
/dev/sda5        b39b8a64-11c5-48f4-a44e-c507334989a1   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root c115a6e2-5b2a-4b13-a810-6373cec0e25e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root c115a6e2-5b2a-4b13-a810-6373cec0e25e
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c115a6e2-5b2a-4b13-a810-6373cec0e25e
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=c115a6e2-5b2a-4b13-a810-6373cec0e25e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c115a6e2-5b2a-4b13-a810-6373cec0e25e
    echo    'Loading Linux 3.0.0-12-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-12-generic-pae root=UUID=c115a6e2-5b2a-4b13-a810-6373cec0e25e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c115a6e2-5b2a-4b13-a810-6373cec0e25e
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=c115a6e2-5b2a-4b13-a810-6373cec0e25e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c115a6e2-5b2a-4b13-a810-6373cec0e25e
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=c115a6e2-5b2a-4b13-a810-6373cec0e25e ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c115a6e2-5b2a-4b13-a810-6373cec0e25e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root c115a6e2-5b2a-4b13-a810-6373cec0e25e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c115a6e2-5b2a-4b13-a810-6373cec0e25e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b39b8a64-11c5-48f4-a44e-c507334989a1 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 376.131866455 = 403.868516352  boot/grub/core.img                             1
 356.174201965 = 382.439137280  boot/grub/grub.cfg                             1
   1.427730560 = 1.533014016    boot/initrd.img-3.0.0-12-generic               1
   1.005863190 = 1.080037376    boot/initrd.img-3.0.0-12-generic-pae           2
 356.172374725 = 382.437175296  boot/vmlinuz-3.0.0-12-generic                  1
   0.700729370 = 0.752402432    boot/vmlinuz-3.0.0-12-generic-pae              2
   1.427730560 = 1.533014016    initrd.img                                     1
 356.172374725 = 382.437175296  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by drs305 on 2011-11-12
volinkov,

The problem most likely is that your Grub files are located on a portion of the drive which can't be seen by BIOS or Grub 2. On many BIOS there is a 137GB limitation on what the BIOS can see. Your Grub 2 files are beyond that limit.

You can check by booting and entering the BIOS setup. Check the reported disk size. If it reports approximately 137 GB, that is the problem. If there is a setting to enable large drives or LBA, enable it. You might also be able to update the BIOS.

If your setup will allow it, shrinking your sda1 partition to approximately 130GB will probably also fix the problem, since it will force the Grub 2 files to be placed within the 137GB limit. If you have to shrink the partition, you will need to use the LiveCD or another 'rescue' type CD since your Ubuntu partition must be unmounted. Gparted is an excellent tool for resizing linux partitions. 

The usual caution about backing up critical data files whenever performing partitioning operations.

---

### Post by volinkov on 2011-11-12
I resized the partition and she booted up just fine. Thanks for your help!

---

### Post by brewmasterkyle on 2011-12-03
Help!

I've found that my linux partition is (hd1,1)

I've also found that my grub modules are in (hd1,1)/usr/lib/grub/i386-pc

I then typed 

```
set prefix=(hd1,1)/usr/lib/grub/i386-pc
insmod linux
```

At which point, it gives me the error:

error: symbol not found: 'grub-mm-base'.

I don't know what to do from here.  Please help!!

---

### Post by drs305 on 2011-12-03
> **brewmasterkyle said:**
> 
I've found that my linux partition is (hd1,1)

I've also found that my grub modules are in (hd1,1)/usr/lib/grub/i386-pc

I then typed 

```
set prefix=(hd1,1)/usr/lib/grub/i386-pc
insmod linux
```

At which point, it gives me the error:

Good for you for being able to locate the modules. 

Where you found them is where the originals are stored, but they are the source and are transferred to the boot folder during installation. You might be able to copy them to your /boot/grub folder. I don't know if the installation process does anything more than a direct copy regarding the modules. 


You can use the LiveCD to try a direct copy to the mounted grub folder. However, if you use a LiveCD I'd recommend chrooting into your Ubuntu partition and reinstalling Grub 2 completely. I suspect that would be more reliable unless your only problem is missing modules, and nothing else. That is covered in the "Chroot" link in my signature line.

If the modules exist in hd1,1/boot/grub, you can try manually booting with these commands:

```
ls (hd1,1)/boot/grub 
# Do you see the modules? If not, try the alternate module loading command later.
set prefix=(hd1,1)/boot/grub
set root=(hd1,1)
insmod (hd1,1)/boot/grub/linux.mod
# Alternate module load:
# insmod (hd1,1)/usr/lib/grub/i386-pc/linux.mod
# Other modules may be needed as well. Watch for errors when you try to boot.
linux (hd1,1)/vmlinuz root=/dev/sdb1 ro
initrd (hd1,1)/initrd.img
boot

```

---

### Post by sprintexec on 2011-12-17
>  'out of disk' can be caused by many things. Often it means the BIOS cannot read the drive. You should probably open up your BIOS setup during boot and check the reported drive size. If the BIOS does not report the full size of your drive, any files physically located beyond the limit seen by the BIOS will not be found.

This little snippet of information was all that I needed to find to get my otherwise no-starting 11.10 installation to boot. I had wondered how it could be that the CD would run perfectly but yet the full install did not. 

Thank you DRS305 :guitar:

---

### Post by drs305 on 2011-12-17
> **sprintexec said:**
> This little snippet of information was all that I needed to find to get my otherwise no-starting 11.10 installation to boot. I had wondered how it could be that the CD would run perfectly but yet the full install did not. 

Thank you DRS305 :guitar:

You are most welcome.

This issue comes up fairly often, especially on older systems.

Even with today's larger drive sizes some relatively recent BIOS's still have the 137GB limit built into them. Presumably because the manufacturers believe that users will only have one OS installed on their computers and the boot files will be very early on the disk.

---

### Post by c.cobb on 2011-12-19
Hi drs305, 
I was just going through your nice HowTo making some crib notes when I noticed that you could save a step (and some typing) by omitting the '[FONT=Courier New]iso-scan/filename=[/FONT]' kernel parameter. Without this, the [FONT=Courier New]/isodevice[/FONT] directory does not get mounted, and you are left with just the read-only [FONT=Courier New]/cdrom[/FONT] mount point -- at least this is how it works when booting 10.04. 

Also, for times when you do include the '[FONT=Courier New]iso-scan[/FONT]' param, the file you select can be any existing file on the drive; it doesn't have to be the ISO. A while back I dug down into the lupin-casper shell scripts to see how it worked, because I wanted to have [FONT=Courier New]/isodevice[/FONT] mounted when not booting from an ISO file -- again this is on 10.04, so hope it hasn't changed.
Solo mis dos centavos,

---

### Post by drs305 on 2011-12-20
> **c.cobb said:**
> Hi drs305, 
I was just going through your nice HowTo making some crib notes when I noticed that you could save a step (and some typing) by omitting the '[FONT=Courier New]iso-scan/filename=[/FONT]' kernel parameter. Without this, the [FONT=Courier New]/isodevice[/FONT] directory does not get mounted, and you are left with just the read-only [FONT=Courier New]/cdrom[/FONT] mount point -- at least this is how it works when booting 10.04. 

Also, for times when you do include the '[FONT=Courier New]iso-scan[/FONT]' param, the file you select can be any existing file on the drive; it doesn't have to be the ISO. A while back I dug down into the lupin-casper shell scripts to see how it worked, because I wanted to have [FONT=Courier New]/isodevice[/FONT] mounted when not booting from an ISO file -- again this is on 10.04, so hope it hasn't changed.
Solo mis dos centavos,

I appreciate the input. :-)

I've been swamped lately but I'll try to test this in my other releases and update the file. 

We struggled with how to set this up before there was any documentation and there are some pretty amusing posts by a group of us scattered around these forums as we tested various ideas. While we got it working, as you discovered there very well can be other and better ways of doing things.

In the meantime, happy holidays and thanks again.

---

### Post by c.cobb on 2011-12-20
Yes, I've followed several of your threads on Grub2, and they've all been very helpful. By coincidence I had a chance to confirm that [lupin-casper on Natty]("http://packages.ubuntu.com/natty/all/lupin-casper/filelist") still works the same way. 

After posting here last night, I tried [another of your suggestions]("http://ubuntuforums.org/showpost.php?p=11093176&postcount=793") to update Grub2 on a 10.04 install and, in addition to the three packages you mention, it also happened to update lupin-casper. So, this morning I went poking around and, while things have changed some (iirc), the 'iso-scan' mount part works the same. 

Thanks and happy holidays to you as well.
Cheers,

p.d. For Natty the pertinent parts are in these two scripts.[FONT=monospace]
[/FONT][INDENT] /usr/share/initramfs-tools/scripts/casper-premount/20iso_scan
 /usr/share/initramfs-tools/scripts/lupin-helpers[/INDENT]

---

### Post by drs305 on 2011-12-27
c.cobb,

If I remove the *isoscan* kernel option in the Lucid 10.04 LTS 3 I get a 'Can't open /dev/sr0: No medium found' error message and the system won't boot to the LiveCD Desktop. Here is the menuentry I am using:

> menuentry 'ISO Lucid.1 64                        ' 		{
isofile=ubuntu-10.04.3-desktop-amd64.iso
loopback loop (hd1,6)/iso/$isofile
linux (loop)/casper/vmlinuz boot=casper **iso-scan/filename=/iso/$isofile** noprompt noeject
initrd (loop)/casper/initrd.lz
}

---

### Post by xanderman on 2012-01-17
**I am stuck on Step 6 - Load the Linux kernel and initrd image.**

**The following code:**
linux /casper/vmlinuz boot=casper iso-scan/filename=/<ISO-name.iso> noprompt noeject

**produces this error:**
error: cannot read the Linux header.

**PLEASE HELP ME!**

---

### Post by drs305 on 2012-01-17
xanderman,

Welcome to the Ubuntu forums. 

The reference to /casper seems to indicate you are not using a standard installation. 'casper' usually involves trying to boot from an ISO image and not from a installed Ubuntu release.

I would suggest booting a LiveCD and installing the Boot Repair app. It may be able to fix your problem, and if not it will provide an option to run the 'boot info' script, which will provide us with information needed to help you.

You can learn more about the Boot Repair app from its link in my signature line.

---

### Post by mufler on 2012-02-07
Hey guys,

I got into "grub rescue" after trying to reinstall grub2. (I did the reinstall because of dual boot issue when i recently installed window7, in addition to ubuntu 10.04 LTS which was already installed on the netbook) 

The error message i get is "error: incompatible licence". And then i am left in the rescue mode. I tried to boot fra a usb stick with ubuntu Live, and guess what. I get prompted with  username and password. This has never happend before. Last time I used this LIVE ISO was 2 days ago. The problem is that i just cannot get logged in the LIVE ubuntu. Tried the ubuntu username with blank password. Did ctrl+shift+f1, set password for a user and then alt+f7, but still no go. So here i am stuck. 

I have also tried to work inside rescue mode with your advices. I can get into ls (hd0,1)/boot/grub and the .mods are there, but when i type insmod (name of the mod) I get incompatible licence error message. I feel pretty stucked at this stage. I can't execute essential commands in rescue mode, and live iso wont let me in either.

Any suggestions?

---

### Post by drs305 on 2012-02-08
mufler,

Welcome to the Ubuntu Forums. I'm out on a business trip and am not logging into the site frequently this week so I'm sorry your post didn't receive a more prompt response.

Normally the 'incompatible license' message means that the core.img that was created when 'grub-install' was created used different modules. Perhaps you were using a newer CD than the one with which you installed Grub originally.

What I would recommend is to boot a LiveCD and purge and reinstall Grub 2. To do this, you have to boot the CD then 'chroot' into your Ubuntu installation. The 'chroot' allows the commands you run on the LiveCD take their action on your real installation. 

I don't know how much experience you have, but the instructions on how to do this are in the 'Chroot' link in my signature line. If you have questions, just ask.

---

### Post by pirog on 2012-03-22
Hi guys, drs305!

One of them days I turned off my IBM T23 with a push of a power button because it had froze. Upon restarting it, I was greeted with a blinking cursor and the following message:

```

error: hd0 read error
grub rescue>_
```

“ls” gives “(hd0), (hd0,msdos5), (hd0,msdos1) (fd0)”

My guess is that the partition table is intact, hard drive is not dead, grub2 can't see the first block and hence can't boot. I finally logged into LiveCD account (took about 40 minutes with the specs) and tried to mount the drives to save the data. Nautilus didn't show any. Then I remembered (!) that the “/home” partition was encrypted at the install time. BTW it is Mint Katya (11).

Anyways, when in “grub rescue” mode I can't load any modules, heck, I can't list any folders with “```
ls (hd0,msdos1)/
```” (giving me the “error: hd0 read error”) presumably because of encrypted disks. Which btw can't be mounted in the Live-environment.

I am thinking of using LiveCD to re-install grub2 or try to mount encrypted drives through the magic of … hell, I am not too sure how to mount encrypted drives in live-environment. I searched but to no avail. I am not even sure what encryption type is on the HD.

Do you guys have any ideas on the "pickle" of an issue?

Thanks,

p.

---

### Post by drs305 on 2012-03-22
> **pirog said:**
> Hi guys, drs305!

One of them days I turned off my IBM T23 with a push of a power button because it had froze. Upon restarting it, I was greeted with a blinking cursor and the following message:

```

error: hd0 read error
grub rescue>_
```

&#8220;ls&#8221; gives &#8220;(hd0), (hd0,msdos5), (hd0,msdos1) (fd0)&#8221;

My guess is that the partition table is intact, hard drive is not dead, grub2 can't see the first block and hence can't boot. I finally logged into LiveCD account (took about 40 minutes with the specs) and tried to mount the drives to save the data. Nautilus didn't show any. Then I remembered (!) that the &#8220;/home&#8221; partition was encrypted at the install time. BTW it is Mint Katya (11).

Anyways, when in &#8220;grub rescue&#8221; mode I can't load any modules, heck, I can't list any folders with &#8220;```
ls (hd0,msdos1)/
```&#8221; (giving me the &#8220;error: hd0 read error&#8221;) presumably because of encrypted disks. Which btw can't be mounted in the Live-environment.

I am thinking of using LiveCD to re-install grub2 or try to mount encrypted drives through the magic of &#8230; hell, I am not too sure how to mount encrypted drives in live-environment. I searched but to no avail. I am not even sure what encryption type is on the HD.

Do you guys have any ideas on the "pickle" of an issue?

Thanks,

p.

Hey pirog,

I'm going to be pretty scarce on the forums for the next month and a half. I don't have a ready answer for you as I'm not educated on all the aspects of encrypted drives. Some of the things I'd recommend wouldn't work because of the encryption. 

What I'd recommend for now is to start your own thread and describe your situation. There are a lot of bright people on this forum and some understand and use encryption. Mention that the partition is encrypted in the thread title so you get the attention of users who can help you.  The good news is that your /home partition doesn't come into play during the initial part of the boot process so you might be able to fix things even with the encrypted home partition.

I'd suggest running the boot info script. The script generates a file called  RESULTS.txt which provides a lot of information about the status of your boot files. It can be run from a LiveCD, as can the tool mentioned next. 

You can try to fix things with the Boot Repair tool. If it can't help, it would at least provide the option to run the boot info script for you. You can learn more about Boot Repair from the link in my signature line. (Also BIS)

Best of luck. If I'm on the forums I'll check for your new thread and offer any help I can.

---

### Post by pirog on 2012-03-23
> **drs305 said:**
> Hey pirog,

I'm going to be pretty scarce on the forums for the next month and a half. I don't have a ready answer for you as I'm not educated on all the aspects of encrypted drives. Some of the things I'd recommend wouldn't work because of the encryption. 

What I'd recommend for now is to start your own thread and describe your situation. There are a lot of bright people on this forum and some understand and use encryption. Mention that the partition is encrypted in the thread title so you get the attention of users who can help you.  The good news is that your /home partition doesn't come into play during the initial part of the boot process so you might be able to fix things even with the encrypted home partition.

I'd suggest running the boot info script. The script generates a file called  RESULTS.txt which provides a lot of information about the status of your boot files. It can be run from a LiveCD, as can the tool mentioned next. 

You can try to fix things with the Boot Repair tool. If it can't help, it would at least provide the option to run the boot info script for you. You can learn more about Boot Repair from the link in my signature line. (Also BIS)

Best of luck. If I'm on the forums I'll check for your new thread and offer any help I can.

Hi drs305,

Thanks for the tips. You are certainly right in that I start a new thread, but I thought it would be a good place to start my search. I was hoping you had had a similar problem, since yours is related to mine.

I'll give the script a try and if anything good comes of it, I'll let you know. The thing about “/home” partition, you are right it won't come into play until later. I still think it is the grub2 issue. If I ever get to solve this problem, I'll write it up in a new post for others to see.

Thanks for your suggestions mate.

Regards,

p.

---

### Post by HotForLinux on 2012-04-15
How can I work with grub2's command line inside Ubuntu?


[LIST]
[*]```
If you don't find the modules, try the alternate location:  ls (hdX,Y)/usr/lib/grub/i386-pc
```
[/LIST]
In my case one location has 204 modules and the other 207 with only 9 differences **is that normal?** I thought that duplicate info was a sin.

It suddenly reminded me the disorder in Windoze's directories.

---

### Post by drs305 on 2012-04-15
> **HotForLinux said:**
> How can I work with grub2's command line inside Ubuntu?


[LIST]
[*]```
If you don't find the modules, try the alternate location:  ls (hdX,Y)/usr/lib/grub/i386-pc
```
[/LIST]
In my case one location has 204 modules and the other 207 with only 9 differences **is that normal?** I thought that duplicate info was a sin.

It suddenly reminded me the disorder in Windoze's directories.

I've never closely inspected/compared the two folders, but I know that the grub folder used for booting contains at least a couple of files that are generated 'locally' - grub.cfg (the menu) and grubenv. I'm sure there are several others as well, which would explain the differences.

---

### Post by HotForLinux on 2012-04-16
183 files!:
sun@milkyway:~$ for i in /boot/grub/*.mod; do cmp "/usr/lib/grub/i386-pc/$(basename $i)" "$i"; done

the differences:
sun@milkyway:~$ for i in /boot/grub/*; do cmp "/usr/lib/grub/i386-pc/$(basename $i)" "$i"; done
sun@milkyway:~$ for i in /usr/lib/grub/i386-pc/*; do cmp "/boot/grub/$(basename $i)" "$i"; done

the links:
?

who knows... ?

---

### Post by rajarjun on 2012-06-26
i have installed ubuntu inside windows and then afterwords i installed fedora 16...all time during start up its show os selection by grub loader but after i did some partition on windows its shows error:unknown filesystem.enterting rescue mode.. grub rescue>

grub rescue>ls
(hd0)(hd0,msdos9)(hd0,msdos8)(hd0,msdos7)(hd0,msdos6)(hd0,msdos5)(hd0,msdos3)(hd0,msdos2)(hd0,msdos1)
and then i found out content of partition root as u told..
grub rescue>ls (hd0,msdos7)/
./ ../ lost+found/ etc/ dev/ boot/ var/ sys/ proc/ lib64/ usr/ bin/ home/ lib/ media/ mnt/ opt/ root / run/ sbin/srv/ tmp/ .readahesd
grub rescue>ls (hd0,msdos7)/boot/grub
./ ../ splash.xmp.gz
grub rescue>set prefix=(hd0,msdos7)/boot/grub
  and then  if i give all load module command it says error:file not found.
what i can do now any body help this hoping for correct solution

---

### Post by drs305 on 2012-06-26
> **rajarjun said:**
> 
what i can do now any body help this hoping for correct solution

Welcome to the Ubuntu Forums. :-)

It looks like you have done a good job of troubleshooting. I don't use Wubi so I'm not comfortable giving advice about it. I believe with Wubi you should still see the Windows bootloader first; if Grub was installed in the MBR you would most likely have lost both the Windows bootloader *and* also not be able to boot from Grub.

There is an excellent GUI app called Boot Repair but I don't know if it works with Wubi. I think it can and if you have lost your Windows bootloader it probably has an option to restore it via a bootloader called *lilo*.

Even if BR can't repair your system, it has an option to run the boot info script which can help find out what is happening. There is a link to Boot Repair in my signature line.

Another good resource is the Wubi Megathread, which specializes in Wubi installations:
[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by mkalioby on 2013-01-12
Thanks, you have recused me

---

### Post by jpascua on 2013-06-26
[LIST=1]
[*]**[COLOR=navy]Load the modules.[/COLOR]**
```
set prefix=(hd[COLOR=red]X,Y[/COLOR])/<path to modules>
```
This command must correctly point to the folder containing the Grub modules. The address should be the one in the previous section which displayed the modules.
Examples:  
set prefix=(hd0,5)/boot/grub  
set prefix=(hd1,1)/usr/lib/grub/i386-pc

Load modules:
```

insmod linux
insmod loopback
insmod iso9660
insmod fat        # If ISO is located on fat16 or fat32 formatted partition.
insmod ntfs       # If ISO is located on an NTFS formatted partition.
insmod nftscomp   # If NTFS compression is used on the partition. Load if you aren't sure.

```

A "*[COLOR=red]file not found[/COLOR]*" error means that the path in the *prefix* is incorrect or the specific module does not exist. The prefix setting may be reviewed with the **set** command. Rerun the "*set prefix=*" command with the proper path.
[/LIST]


So I have gotten to this step but when I do the set prefix= command it does nothing... How can I change that??

---

