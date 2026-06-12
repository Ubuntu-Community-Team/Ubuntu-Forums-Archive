---
title: "Installing Ubuntu Studios over a Windows 8 and Linux Mint dual boot"
date: 2016-05-30
forum: Ubuntu Studio
---

### Post by Responsive on 2016-05-30
YO,

Used to use Ubuntu for awhile then installed LinuxMint as a dual boot with Windows 8. Mint has my favourite UI so far. I am pretty much married to the idea that start panel should be at the bottom and not the top. But Mint had problems using audio and video software, so I am going to try Ubuntu Studios.

Is there away to just install it over my windows 8, which came with the hard-drive? Or at least shrink it so it doesnt take half of my hard-drive?

Balls. I bought a Linux magazine that had a DVD with it, and now I cant find it.

---

### Post by yancek on 2016-05-30
You should be able to use Disk Management in windows 8 to resize (shrink) the windows partition to make unallocated space for Ubuntu Studio.  After doing this, defragment and run chkdsk from windows.

---

### Post by Responsive on 2016-06-02
so far stuck on rebooting Ubuntu Studios. I have it written on to a USB. I try pressing, esc, f2 and f12 when "Toshiba" pops up on my screen when i restart.

is there any special way to install Ubuntu?
I will Google comandline to install Ubuntu.

---

### Post by oldfred on 2016-06-02
Is system older BIOS with MBR partitioning, or newer UEFI with gpt partitioning?

 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) 


       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 8 screens or similar to Windows 10
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

### Post by Responsive on 2016-06-02
Pretty sure its UEFI.

When Toshiba pops up, I rapidly press ESC.

The menu option appears.

LinuxMint
Advanced Options.
Memory Test.
Memory test serial consol.

None of these lead to the Ubuntu Studios.

I am not using windows 8 for a year. been using LinuxMint.

---

### Post by oldfred on 2016-06-02
The escape key gets you into the grub menu.

You should with Toshiba have f12 which gets you into UEFI/BIOS boot options. If BIOS it may just be the one install booting from MBR. With UEFI multiple installs share the ESP - efi system partition and all can be booted from UEFI, or usually grub menu if others are in same boot mode BIOS or UEFI as grub.

       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by yoshii on 2016-06-02
Personally, I like to use Linux's gParted LiveCD or bootable USB drive (from .ISO file and uNetBootIn software).  
I use gParted to create, modify, or erase partitions.  I will create the SWAP area too.  

Then, when I want to install Ubuntu Studio from it's LiveCD or bootable USB drive, I select "Do Something Else" from the installer menu so that it doesn't just erase the whole hard drive or whatnot.  From there, I will make sure that the correct partition setup is happening and manually set the parts that need editing.  Then I continue the install.  

After the install completes, I usually run gParted again, just to check on everything and make sure it's OK.  Ubuntu Studio seems to like to put the SWAP area into an extended partition, but I prefer to use a SWAP in it's own primary partition.  I use MBR/BIOS booting, not GPT.  

Then I'll reboot into Ubuntu Studio and start configuring it.  
Maybe you'll find this way of working useful too.

---

### Post by Responsive on 2016-06-02
the only place that sells live cds, is the boat. i wont be on the boat for a week.

tried f12. no effect. 

is there a way to get to the UEFI/BIOs from comandline?

tried f1 to f12. 

tried DEL and got a bunch text flying down my screen. one said "virtual machine disabled".

How com I ca install Linux Mint but not Ubuntu?

---

### Post by oldfred on 2016-06-02
With my older Toshiba it was f2 to get into BIOS and f12 to get boot menu.

New UEFI systems have the last grub boot entry as a way to get into UEFI.

Sometimes you need a cold boot, not warm reboot. And that may also mean removing plug & battery and holding power switch to drain any left over power.

---

### Post by Responsive on 2016-06-03
good info. so i will try two cold boots with f2 and f12. thanks.

FYI, I also tried booting with a LM KDE.

shuting down and then turning on again didnt work.

---

### Post by oldfred on 2016-06-03
So are you able to boot a flash drive?

If cold boot does not let you get into UEFI, some systems have a tiny reset hole at bottom of system. With others you have to get to motherboard and jumper pins or remove coin battery on motherboard. These all reset UEFI settings to defaults, so you have reset them.

---

### Post by Responsive on 2016-06-06
thats whats i am trying to do. boot from a flash drive. i've done it before with this computer. dont know what i am doing wrong this time.

now trying a dvd. still doesnt work!

---

### Post by oldfred on 2016-06-06
If you left fast boot on in UEFI it can be difficult. But try the cold boot again.

---

### Post by Responsive on 2016-06-07
how do  check the UEFI in LinuxMint?

[I][COLOR=#111111][FONT=Consolas][ -d /sys/firmware/efi ] && echo UEFI || echo BIOS


[/FONT][/COLOR][/I][COLOR=#111111][FONT=Consolas]this returns *BIOS*.

does anyone know how to force LM to boot to BIOS?

I keep trying to cold boot, but it doesnt work.[/FONT][/COLOR]

---

### Post by oldfred on 2016-06-07
You have to get into UEFI and make sure the UEFI Secure boot is off, and then it is either UEFI off or CSM/Legacy/BIOS on. Some have settings for both or either.
Then which ever system it finds and boot order settings will boot first. 
Or one time boot key, like f12, f8 or f10.

If totally powering down & removing battery does not totally reset, you may have to jumper pins on motherboard or remove coin battery on motherboard to totally reset entire system. All settings then go back to default, so you have to go into UEFI and reset all the changes you made.

---

### Post by Responsive on 2016-06-07
Ubuntu Studios installed.

The magic ingredient was tapping F2 for one second after laptop powers on, and letting go BEFORE Toshiba appears on screen. So not tapping rapidly or holding it down.

Almost ready to work on.

Switched panel to the bottom so looks more like LinuxMint.

Now my computer is running slowly. The previous home partition of LM is still there with all my files. So I guess after I transfer the filesover, i need to find away to delete that partition so i can expand the new Ubuntu home. Then find away to shrink the windows partition.

So I guess I will download gparted, and whatever Ubuntu books I can find to master this. i need to have this working by this week.

thanks so far.

[IMG]https://pbs.twimg.com/media/CkXgY6VXAAALdTv.jpg[/IMG]

highlighted is what i think is old LM partition. do i just resize the others, then delete this one?

---

### Post by oldfred on 2016-06-07
If you have an UEFI setting for fast boot, turn that off. It should give more time to get into UEFI. Or at least until you have totally reconfigured system.

If resizing NTFS partitions only use Windows own tools, & immediately reboot so it can run chkdsk. Best to defrag before a resize also as then resize can be quicker. But with NTFS, it likes 30% free space inside the NTFS partition or it starts to slow down. At 10% free a defrag can take forever as there is no working room.

And you can use gparted to edit all the Linux partitions.
If you have not run the summary report from Boot-Repair run that, even if just for your own info. It will show what is installed where.
And backup any data in all partitions before making changes to avoid issues.

       [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Responsive on 2016-06-08
what happens if i resize the windows from linux? i don even know how to run windows. i havent used windows since i first got this laptop last year.

---

### Post by oldfred on 2016-06-08
It usually is ok, but some have then had issues with Windows and blamed Linux/gparted or whatever.
Usually not Linux issue, but something in Windows, so we always suggest using Windows.

I do not know Windows well as I have to look up every command now for my one Windows install.
[http://www.everydaylinuxuser.com/2015/11/how-to-shrink-windows-10-to-make-space.html](http://www.everydaylinuxuser.com/2015/11/how-to-shrink-windows-10-to-make-space.html)

---

### Post by Responsive on 2016-06-08
I dont knw how to go on to windows from linux.

I have now messed up my partitions even more.

i cant resize the windows one from linux.
i deleted the old LM partition. then couldnt resize the new one to make it bigger than 20gb.
so i made a new partition as a temporary solution.  

how do I fix this? 

reinstall ubuntu again?

[IMG]https://pbs.twimg.com/media/CkcixF7UgAIuUEK.jpg:large[/IMG]

[IMG]https://pbs.twimg.com/media/CkcixF7UgAIuUEK.jpg[/IMG]

---

### Post by oldfred on 2016-06-08
Are you using live installer version of gparted?

All partitions must be unmounted, otherwise you can create even more issues.
And even live installer may auto mount swap, so you have to click on it and swap off.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Responsive on 2016-06-09
OK. thanks for those links.

I shrank the windows partition down to 195gb. good enough for now? can it be smaller?

the partition which Ubuntu uses for downloads, pictures and videos, wont increase beyond 20gb. which isnt good enough for downloads or all my Turkish music files.

I made a temporary partition so i can tat least start doing work this week.

there is also 268gb unallocated which i want my home partition to use.

swap becomes mounted again after i swap off.

how can I put my unallocated memory on the home partition?

[IMG]https://pbs.twimg.com/media/Ckgtac8WUAAVW3t.jpg[/IMG]

---

### Post by oldfred on 2016-06-09
You can make Windows just about any size, but it works best if you have at least 30% free inside the NTFS partition. At 10% free you have so little working room it may take forever to run a defrag.

I have a 160GB for data, not sure what you are doing. Are you trying to use wubi, it is the only one I know that had size limits, and it is not supported anymore.

```
fred@Z170N:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        30G  7.6G   21G  27% /
/dev/sda1        50G   11M   50G   1% /boot/efi
/dev/sdb6       202G   34G  159G  18% /mnt/data
/dev/sdc2        21G  4.5G   15G  24% /media/fred/yakkety
/dev/sdc3        36G   17G   18G  48% /media/fred/data64
/dev/sdb4        49G  3.1G   44G   7% /media/fred/backup_b
```

I just noticed I made a mistake on this system and made ESP 50GB, should be 500MB.
The sdc is a full install of 16.10 on a 64GB flash drive.

---

### Post by Responsive on 2016-06-09
I have gparted installed on my Ubuntu computer and I can use it through the USB. 

it says the home partition is at maximum size, even though I have 268gb unallocated. i tried using gparted on the usb, same situation.

---

### Post by oldfred on 2016-06-09
Are you then creating a new /home during install with only 20GB of available space.

If you have partitioned in advance, you choose that partition, click on change button, choose /home & ext4. If you previous had data in /home you would not tick/check the format box or your data is erased. But first install you normally would tick it.

---

### Post by Responsive on 2016-06-09
i am happy to delete all my data. i backed up all my important files on an external disk.

should i delete all these partitions and install again? which ones should i delete? just the two ext4? home and media?

---

### Post by oldfred on 2016-06-09
Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html) 
    
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)

---

### Post by Responsive on 2016-06-09
no. i dont follow that example. still stuck with this partition not expanding above 20gb. its going to be awhile before i fix this. i dont know which exactly partitions i should delete before trying to install ubuntu again.

---

### Post by oldfred on 2016-06-09
Probably only need to see current partitions but this will show a lot more.

 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Responsive on 2016-06-09
[http://paste2.org/IU3Km3Pp](http://paste2.org/IU3Km3Pp)

Thanks. this is great. boss a little mad i cant get to work yet, but at least I am learning more about Linux. 

so i can probably delete sda7,8 and 9 and reinstall Ubuntu?
still i would have 268gb unallocated.

---

### Post by oldfred on 2016-06-09
Your Windows is installed in UEFI boot mode on a gpt partitioned drive.
But you have a bios_grub partition for Ubuntu BIOS boot, grub installed in MBR for BIOS boot. So Ubuntu is configured for BIOS booting.

Best to also have Ubuntu in UEFI mode but not absolutely required. But UEFI & BIOS are not compatible. You have to start booting from UEFI/BIOS and boot only in mode selected. Or you cannot dual boot from grub menu. As grub can only offer to boot other systems installed in same boot mode.

Can you turn on BIOS, or turn off UEFI and boot Ubuntu now?

You also booted live installer in BIOS mode, best to boot in UEFI mode.
It also looks like you labeled sda9 as /home but it is / (root). 

I prefer to use smaller / (root) of about 25GB and then either separate /home or /mnt/data and/or another /mnt/shared that is NTFS to share data with Windows. But Windows still must have fast start up off or its hibernation keeps the data partition mounted and not usable from Linux.

While it may seem like a lot of information, I suggest you review link below in my signature and click on some of the links for even more info.

---

### Post by Responsive on 2016-06-10
gign to try read all that information. but i dont what to do. do i delete the ubuntu partitions and install again?

"[COLOR=#000000]Can you turn on BIOS, or turn off UEFI and boot Ubuntu now?[/COLOR]"

I dont have a clue how to do that.

---

### Post by oldfred on 2016-06-10
It is in your UEFI.
You may also need to change UEFI Secure boot. And BIOS is often called CSM.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.


Screen shots of secure boot settings, several models
 [URL="http://www.rodsbooks.com/efi-bootloaders/secureboot.html"]http://www.rodsbooks.com/efi-bootloaders/secureboot.html
[/URL]
 Screenshots of secure boot settings Asrock, Asus, HP, Acer
[https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/) 

[URL="http://www.rodsbooks.com/efi-bootloaders/secureboot.html"]
[/URL]

---

### Post by Responsive on 2016-06-10
CMS mode is on. so do I delete thos partitions ubuntu created and install again?

---

### Post by oldfred on 2016-06-10
You want UEFI boot mode. You do not have to uninstall to convert, just use Boot-Repair's advanced mode to uninstall/reinstall grub.

Or turn CSM on to boot Ubuntu or turn CSM off to boot Windows.
Some let you auto switch as it knows boot mode, by using one time boot key like f10 or f12, check your manual on correct key.

---

### Post by Responsive on 2016-06-10
OK. New installation seems faster. still not 100% as efficient as I would like it. But maybe it will do for work.

still have this 206gb unallocated i would like back. maybe I will just make it a drive for project work.

Any sugestions does this look ok??

[IMG]https://pbs.twimg.com/media/CkmxbUAXEAEd_xX.jpg:large[/IMG]

---

### Post by oldfred on 2016-06-10
Does what look ok?

Post this:
sudo parted -l

---

### Post by Responsive on 2016-06-10
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  1075MB  1074MB  ntfs            Basic data partition  hidden, diag
 2      1075MB  1180MB  105MB   fat32           Basic data partition  boot, esp
 3      1180MB  1314MB  134MB   ntfs            Basic data partition  msftres
 4      1314MB  211GB   210GB   ntfs            Basic data partition  msftdata
 7      211GB   261GB   50.0GB  ext4
 9      261GB   277GB   16.0GB  linux-swap(v1)
 6      499GB   499GB   1049kB                                        bios_grub
 8      499GB   989GB   489GB   ext4
 5      989GB   1000GB  11.7GB  ntfs            Basic data partition  hidden, diag

does it look like i have done the partition properly?

how do i win back the unallocated gb?

---

### Post by oldfred on 2016-06-10
Partitions look ok. 
What do you want to do with the space between sda9 and sda6?

I normally try to put bios_grub, ESP & swap at ends of drive. They rarely need changes and more often than not get in the way if other changes are desired.
If booting in UEFI mode, you do not need bios_grub.
And you can delete and recreate swap if desired, but if already installed, will have to manually update fstab with new UUID from new swap.

---

### Post by Responsive on 2016-06-14
the bios_grub doesnt move. if i could move it up or down, then i could add the unallowcated memory to the home.

plan b is see if i am gong to stick with US for the summer and make the unallocated memory an extra drive for a specific purpose. 

I have linux books and videos to go through. i'll make a thread for each issue i have to go through. right now thw more important ones is to get chromium and the software manger to stop crashing. and be able to move tabs in my pannel.

---

### Post by oldfred on 2016-06-14
You can delete bios_grub.
If booting in BIOS mode you have to recreate it, and reinstall grub.
If booting in UEFI boot mode, you do not need the bios_grub.

I normally put ESP - efi system partition and bios_grub as first two partitions on every new drive before anything else. And have swap at end of drive.

---

### Post by Responsive on 2016-06-15
good to know thanks.

---

