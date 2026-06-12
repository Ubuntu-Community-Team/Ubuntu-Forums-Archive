---
title: "why I despise Linux -&gt; another weekend lost to a blinking cursor"
date: 2013-04-28
forum: Ubuntu, Linux and OS Chat
---

### Post by raxman on 2013-04-28
I built a cutting edge system more than a year ago.  [http://ubuntuforums.org/showthread.php?t=1927626](http://ubuntuforums.org/showthread.php?t=1927626)
I spent a weekend trying to install Linux (details in that post).  I  have used Linux for more than 10 years and used it regually at work and  am quite cofortable with emacs, sed, bash scripting, and gcc.  But one  waisted weekend and I did the unthinkable: I bought windows 7 and it  installed with no problems.  

For the last year I occasionally checked out new Linux edtions hoping  they would install on my desktop system.  Finally, Ubuntu 13.04 booted!   Of course, it had problems with my GTX 590 so I had to use nomodeset  but after that the installer at least ran.  I installed it along  windows7 and booted to a blinking cursor.  No GRUB, just a black screen  with a blinking cursor. No windows either.  In a fit of anger I  installed Ubuntu 13.04 over windows hoping it would fix the blinking  cursor.  Of course it did not.  So then I spend Saturday and Sunday  trying to figure out why.  

I wasted a lot of time just trying to write ISO images to USB in linux.   The dd command never produced a bootable USB device.  Unetbootin works  for most of them but not for Ubuntu 13.04. I installed it on Windows  with the Universal USB installer but of course I don't have a Windows  install anymore so that's no use.  But Mint, Manjaro,...all give the  blinking cursor.  The main problem I'm having I think is related to  having UEFI and a SSD only system.  I'm too burnt out to go into details  but probably these two links have the info I need
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://www.rodsbooks.com/efi-bootloaders/index.html](http://www.rodsbooks.com/efi-bootloaders/index.html)

I started off wanting to install the Intel C++ compiler for Linux along  with MKL to compare some of my code with GCC and Visual Studio and  instead I end up with blinking cursor.  I think I'll install Windows7  again and go back to Visual Studio and go back to spending my weekends  doing things more enjoyable.

---

### Post by coldraven on 2013-04-28
Sorry to hear that your hardware has a problem with Linux.
I have had the opposite experience, Linux has installed on everything I tried and using Win7 at work is a pain.
When I do have a problem I remind myself that Linux did not cost me any money. 
Even Photoshop had bugs that would delete all your images, no kidding. I used automate with the destination folder above the source folder and without warning all my images were permanently gone. 
I agree that computers in general can be incredibly annoying and crash or freeze just when you are in a rush to get something done.
Of course when you're not in a rush they work perfectly. Sod's law I suppose :)
I hope that your situation improves.

---

### Post by oldos2er on 2013-04-28
Moved to Ubuntu, Linux & OS Chat.

---

### Post by GameX2 on 2013-04-28
> When I do have a problem I remind myself that Linux did not cost me any money.

Same here, I perfectly agree with that (I do have problems, a few times, for sure!) .

---

### Post by codingman on 2013-04-28
Hmm... That's odd. I have a UEFI board with an SSD only and have a Fermi based GPU (Quadro 2000) and can run Ubuntu 13.04 just fine. In a way, I have the same specs as you do, unless you can find a difference in the engine of two Fermi devices.

---

### Post by Bashing-om on 2013-04-28
I also attest I have never had a serious problem installing 'buntu. I can not count how many installs I have done over the years; friends, clients and passerbys.
I am running three flavors on this beast of a box I built myself with no problems at all// My old radeon card might not hack it when I install 13.04 in a week or so// But, that I can understand.
[INDENT=2]
ubuntu, when all said and done, my operating system Of CHOICE
[/INDENT]

---

### Post by angryfirelord on 2013-04-28
UEFI is tricky and I've had issues with other distros getting it to work. If the USB method doesn't work, it's advisable to just boot it from a disc.

Just by chance, is Secure Boot disabled on your computer? Leaving it enabled might cause the "blinking cursor" symptom. I've also read posts where the drive was formatted as MBR instead of GPT or the boot flag wasn't active on the EFI partition.

---

### Post by lykwydchykyn on 2013-04-28
You use an OS for 10 years, buy an incompatible piece of hardware, decide to ragequit over it, then come back to make your very first post to Ubuntu forums to tell us about it.  Thanks so much for sharing.

---

### Post by iamkuriouspurpleoranj on 2013-04-29
Despise? Fit of anger? LOL

These moments are annoying. You'll sort it out, though, with help from the friendly people on this forum. That's why I love Linux.

---

### Post by oldfred on 2013-04-29
Whether BIOS or UEFI, you need nomodeset on every boot with installer, and on first boot after install. 

Then you install the nVidia version you want, as now the system settings offers several versions of nVidia proprietary driver.

       You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi partition and Windows partition before Install of Ubuntu.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

Grub still has a bug in creating correct entries to dual boot Windows in UEFI mode. But Boot-Repair will fix that.

With UEFI you only get the grub sceens not the normal BIOS boot screens. The editing of grub menu then is the same on installer boot and first boot after install. You have to manually edit grub with e and replace splash quiet with nomodeset. Some new systems do need additional boot parameters also.


 Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by VietCanada on 2013-04-29
I've been building my own PCs since 2000. I'm due to do that again this  year. I get start with the best Intel chip but I draw the line at $1000  video cards or any sound cards. I've installed every MS OS from ME,  every Ubuntu since 10.04 and Mint Mate 13. I've encountered all kinds of  issues from bent processor pins, to SCSI issues when they first came  out to things improperly plugged in from case to MB (by a retailer) to  OS issues (ME was the worst) I loved Amiga but I had to go into the  install disc and make some changes to the OS for it to install properly.  I also had to do some re-writing on my SCSI install floppy just to get  the HDD to boot up so that I had something to install on. I had a  Voodoo3000 installed but the guy didn't include a fan, big problems for  days there. An MS OS disabled all my DVD burners because I installed  Nero. I once had a little cheap HDD given to me. 5oo MB. It had all  kinds of software on a separate partition. One them- an famous anti  virus actually had a virus on it. So every time I installed and then  installed the anti virus I got a virus that disabled my system. Took me a  while to figure that out.

I could go on but I love building PCs  and installing the latest OSs on them. Lately the restaurant cash  register touch screen style interface has left me cold but not so much  as the loss of functionality that I've enjoyed over the last 13 years,  coupled with the frustrating responses that imply these MacDonald's cash  register style OSs are the future when actually they come from the past  and loss of functionality is moving backwards not forwards.

Yet I persevere. Lately I'm taken to bitching on-line.

I  moved to Ubuntu because it's free, it works as welll as anything out  there and it's much easier to get in the places that I work. Did I  mention that on Ubuntu 13 my claendar is in the native language and  style of the country I now reside? So is SM player. They are useless to  me.

A black screen with a flashing curser? I had a purple screen  once. Spent the weekend re-installing a couple times, searching the net.  Then I found that because I had my HDMI plugged into my TV set but I  was watching TV while I worked so I didn't know that Ubuntu 10.10 had  chosen my TV as the default screen. That's where the log-in was while my  secondary PC screen was just purple waiting for me to log in before it  came to life.

My PC kept rebooting. The problem? A bad wall outlet. The plug was kinda loose I guess so plugging my system into another outlet solved the proble. Fortunately the house I was living in didn't burn down. Another lost weekend.

Booting with a USB failed and failed until I found  that I have to check some box to discard extra files or the USB install  wouldn't function properly. That was a black screen with a flshing  curser. Startup disc creator has had this issue for  year or more. Why  doesn't someone fix it? 

This is a fun hobby but sometimes I have  to work and that's when I get really po'd if something breaks or an  upgrade kills off funtionality in the name of trendiness, mindless  change for change sake or whatever.

This board is pretty good at helping *except when it comes to separate X screens*. I take back the italicized comment. I am now following advice from another poster to fix this. :D

---

### Post by mastablasta on 2013-04-29
slightly offtopic: the fun are similar posts by Linus on G+. he then often discribes how he hacked the linux incompatible hardware and made it work...

ontopic - lesson learned: widnows [only] compatibly hardware will work well with windows.

---

### Post by raxman on 2013-04-29
Wow, that's more comments than I expected!  If it's any consolation I installed Linux on my asus ux31a ultrabook with no problems a few months ago.  I overwrote Windows8 which is a disaster.  Anyway, if I find some time in the next week, month, or year I'll try installing Linux again on this desktop.

---

### Post by VietCanada on 2013-04-29
> **mastablasta said:**
> slightly offtopic: the fun are similar posts by Linus on G+. he then often discribes how he hacked the linux incompatible hardware and made it work...

ontopic - lesson learned: widnows [only] compatibly hardware will work well with windows.

Thanks for reminding me.
When I upgraded to Vista my brand new, just purchased, just on the market $1100 3ccd Panasonic video camera software wouldn't work. My brand new $125 just on the market just purchased HP printer software wouldn't work. My new $100 pc camera wouldn't work, even my $10 optical mouse died although I think that was a coincidence. I already mebtioned the issues with my brand new just on the market SCSI with ME and brand new Nero software.

I've had many problems with NVIDIA cards with MS over the years. I even switched to ATI for a time because of it. Updating issues.

Like I said, IMHExperience Linux works as well as anything out there. Companies that only write software for MS are not a Linux problem IMHO that's a systemic issue that should die out as the OS market diversifies and the market share shrinks for those fossils.

---

### Post by sireangelus on 2013-04-29
do you have uefi? do this.
Download ubuntu amd64 iso. 
Put the pendrive on a linux system. even a VM is fine.

Use partition tools to create the pendrive to be witha GPT partition table.
Have the partition on the pendrive formatted/created as "EFI SYSTEM PARTITION"(a couple of clicks in disks do the trick)
Copy the files from the iso on the new pendrive. yes, simply copy over the files.
reboot, disable secureboot and set the boot devices as the pendrive
install.

---

### Post by codingman on 2013-04-29
> **raxman said:**
> Wow, that's more comments than I expected!  If it's any consolation I installed Linux on my asus ux31a ultrabook with no problems a few months ago.  I overwrote Windows8 which is a disaster.  Anyway, if I find some time in the next week, month, or year I'll try installing Linux again on this desktop.

Thanks for sharing your rage, it really helps, especially when you seem to like Windows more and don't have time for Linux, it seems like your rage sure is **surprising** to me.

---

### Post by JohnnyMc on 2013-04-30
> **lykwydchykyn said:**
> You use an OS for 10 years, buy an incompatible piece of hardware, decide to ragequit over it, then come back to make your very first post to Ubuntu forums to tell us about it.  Thanks so much for sharing.

This response had me looking for the "Like" button!  I was wondering about the 10 years vs. 1 weekend part too!

---

### Post by dtconnor on 2013-04-30
WOW! I am new to this forum - got some great help the other nite and now this . . .  sooo entertaining. This forum is awesum!

BTW I am a recent convert and still run Windows 7 in virtualBox, you know "just in case" been on Windows since Windows 95
so don't tell me about hassals with new releases oh and not to mention security and stability and poor performance issues and the 
biggest issue - the MS rip off 

I am running Ubuntu 13.04 FOR FREE and if I don't like it I can try Linux Mint FOR FREE (actually I am running it right now on virtualBox)
Try hopping around between version and re-installing Windows at a whim.

Sorry - sometimes playing with this stuff gets you burned but at least with Linux it never cost you anything but your time and if you don't want to mess
with it then don't mess with it.

---

### Post by codingman on 2013-04-30
^Welcome! Practically all Linux forums are amazing, although not all are as friendly as some!

---

### Post by raxman on 2013-05-01
Thanks your for your reply.  I managed to to finally install Kubuntu 13.04 on this system and boot.  
I followed the device at the following link and used a MBR partition with gparted to create a MSDOS partition.
[http://community.linuxmint.com/tutorial/view/858](http://community.linuxmint.com/tutorial/view/858)

Then I installed Kbuntu which failed to install grub at the end of installation.  The reason I used Kubuntu 13.04 is because unetbootin fails to install ubuntu 13.04 on my USB but Kubuntu works.  
[http://ubuntuforums.org/showthread.php?t=2140424](http://ubuntuforums.org/showthread.php?t=2140424)

Finally, I downloaded "linux-secure-12.10-64bit.iso" and installed that on my USB, booted with a freeze, rebooted with nomodeset which worked and ran BootRepair.  Then I rebooted and finally no blinking cursor and Grub started.  
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Kubuntu and ubuntu don't work with my wireless device so I don't have Internet working yet.  In other words, I could not download BootRepair.

Here is a suggestion.  Install BootRepair on the main Ubuntu iso images not just the secure one!!!

Now to fix my wireless...

---

### Post by raxman on 2013-05-01
I believe EFI is still being used.  BootRepair just fixed it.  If I had my wireless working on this system I would post the output.  If I look in /boot I see a "efi" and "grub" directory.  In efi is a a "EFI" directory.  In that directory are three directories: "Boot", "kubuntu", and "microsoft".

---

### Post by raxman on 2013-05-01
I can install ubuntu 13.04 to USB now and boot.  The problem was a bad iso file
[http://ubuntuforums.org/showthread.php?t=2140424](http://ubuntuforums.org/showthread.php?t=2140424)

However, I tried to install ubuntu 13.04 the same way I did kubuntu.  I overwrote the kubuntu installation.  It booted to a blinking cursor.  I ran BootRepair.  The system booted and said something about a problem with /boot/efi and then freezes.  I tried bootrepair again.  I just get a purple screen...nomodeset does not help.

It's very inefficient to keep installing to USB (13.04 then secure 12.10) over and over.  Would be better if BootRepair was on the default iso (or my wifi was working).

---

### Post by iamkuriouspurpleoranj on 2013-05-01
You'd be better off posting a support question, either here or on Ask Ubuntu.

At the moment, I've filed you under "suspected troll/shill" and I'm surely one of only a few people actually reading your updates.

---

### Post by oldfred on 2013-05-01
IF you have a flash drive add persistence and save Boot-Repair.

 [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

        [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)


 Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)


 With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2128205](http://ubuntuforums.org/showthread.php?t=2128205)
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

---

### Post by raxman on 2013-05-01
I moved my computer to another room and connect it to a LAN line.  Now I have internet.  I reinstalled Kubuntu and installed BootRepair and generated the output.  In case you're interested you can find the details here
[http://paste.ubuntu.com/5623550/](http://paste.ubuntu.com/5623550/)

I bought the components of this system at the end of 2011.  My UEFI bios has no option for secure boot (when I boot i always says secure boot disabled) or to disable UEFI.

"[COLOR=#000000]File system:       vfat[/COLOR]
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  FAT32    Boot sector info:  According to the info in the boot sector, sda1 starts                        at sector 0. But according to the info from fdisk,                        sda1 starts at sector 2048."I'm going to try and get my wireless USB device working now.

---

### Post by oldfred on 2013-05-01
The only issue I see is the FAT32 reporting the wrong start. Windows file system have the same info in the PBR - partition boot sector as the partition table. Usually chkdsk fixes that. 

But you need Windows to run chkdsk.
If you have another system you can create a Windows repair CD or flash and then run chkdsk on sda1.
But I do not think that caues any issues except with NTFS Windows boot partitions. I think I have seen the error with the efi partition before and it did not matter.

---

### Post by codingman on 2013-05-01
Y'know, you don't seem to be noticing peoples posts that you should move this thread to a SUPPORT AREA? Because now it's support not exactly "Why I despise Linux".

---

### Post by raxman on 2013-05-02
Thanks for the help OldFred!!!  My system is mostly working now.  I still don't have the wifi up but I'm going to buy a ethernet cable today and use that until I work out the wifi issues.

I compiled and ran my code with GCC last night and it's much faster than it was in Visual Studio on this system!  That's the main reason I installed Linux.  That, and I missed it.  It's taking a bit of time to get back into Linux.  I underestimated the importance of finding compatible hardware...but then again I'm not interested in running yesterday's hardware.

---

### Post by lykwydchykyn on 2013-05-02
> **raxman said:**
>  I underestimated the importance of finding compatible hardware...but then again I'm not interested in running yesterday's hardware.

[https://www.system76.com/](https://www.system76.com/)

If I had any money at all I'd be buying from those guys.

---

### Post by raxman on 2013-05-02
I'm thinking of getting a X51 alienware with ubuntu.  The problem is the video card is rather weak.  But there are a lot of vidoes of people putting 670s and even 680s in the X51.
[http://www.alienware.com/ubuntu/](http://www.alienware.com/ubuntu/)

---

### Post by lykwydchykyn on 2013-05-02
> **raxman said:**
> I'm thinking of getting a X51 alienware with ubuntu.  The problem is the video card is rather weak.  But there are a lot of vidoes of people putting 670s and even 680s in the X51.
[http://www.alienware.com/ubuntu/](http://www.alienware.com/ubuntu/)

I'm not really an expert on graphics hardware, but I note that the system76 bonobo extreme comes with either the 670 or 680.  Of course, it's pretty pricey, but in terms of supporting Linux well I'd trust system76 over dell.

After all:
> 
Dell recommends Windows®


---

### Post by codingman on 2013-05-02
ASUS is nice. I have had three generations of their products working well with Linux. Both the OEM's and the MOBO's are good from them. Think Penguin, Emperor Linux, and System76 are all good Linux vendors.

EDIT: I currently have an ASUS Maximus V GENE (EFI) motherboard working fine under Arch.

---

### Post by raxman on 2013-05-03
You can see my original post over a year ago here (this thread I started was my second post not first).  This system with "ASUS LPCIe 3.0 and UEFI BIOS P8Z68-V PRO/GEN3" would not even boot without adding "acpi=off, noapic, and nolapic" (yes all three had to be used).  But those parameters neutered my system.
[http://ubuntuforums.org/showthread.php?t=1927626](http://ubuntuforums.org/showthread.php?t=1927626)

That was the first lost weekend I spent.  I gave up and waited over a year and tested new kernels occasionally.  The Kernel in 13.04 was the first that did not need those three boot options.  However, I discovered more problems due to EFI and a SSD only system (also I had to use nomodeset but that was the smallest of the problems). It's possible that motherboard was too new.  I think it was one of the first UEFI motherboards.

---

### Post by oldfred on 2013-05-03
It is not just Linux catching up with UEFI, but the vendors fixing UEFI as that is a huge change for them also. I think most vendors are issuing regular updates to UEFI/BIOS as they need fixes.

And Microsoft using Secure Boot adds a monkey wrench into the works for all new Windows 8 systems that are pre-installed. And many of those vendors are not following the UEFI spec and only letting Windows efi file boot (by looking at file name).

---

### Post by raxman on 2013-05-03
I have not updated the BIOS on this motherboard.  Actually, I have never done that.  Maybe I'll give it a try.  But I'm a bit afraid to try anything now that this system is finally working.
I don't find an option for my motherboard with lINUX
[http://www.asus.com/Motherboards/P8Z68V_PROGEN3/#support_Download_8](http://www.asus.com/Motherboards/P8Z68V_PROGEN3/#support_Download_8)

---

### Post by oldfred on 2013-05-03
I am surprised they have different versions for XP and Windows 7 or 8?

With my Gigabyte, I have 3 ways to update. From Windows which is easy, from a bootable DOS flash drive, or from a file on a flash drive that the BIOS reads directly. 
Not sure how you upgrade yours or which version you should use. What Windows did system originally have?

---

### Post by raxman on 2013-05-03
I just updated it.  There is a utilty in the UEFI bios called "EZ Flash 2'.  I download the bios on "2012.05.29" put it on a USB with fast32 format and rebooted.  Went into the EZ Flash 2 bison and ran the update.  

I don't se many new options.  Still no option to use MBR instead of EFI.  No secureboot option (that's probably a good thing).  I wonder what would happen if I used the Windows 7/8 bios that's a bit newer.  I don't think I'll try.

---

### Post by oldfred on 2013-05-03
Systems with Windows 7 did not have secure boot. Only Windows 8 pre-installed, although I expect motherboard mfg. to add secure boot as an option eventually.
XP does not boot with UEFI and cannot read gpt partitioned drives. That may be part of difference? So you only have BIOS mode?

---

### Post by codingman on 2013-05-03
Really? I had a Z68 MOBO working fine! Current gen Z77 also works for me.

---

### Post by raxman on 2013-05-04
Oldfred, I used the wrong terminology.  I only have UEFI, no BIOS option.

---

### Post by raxman on 2013-05-04
Codingman, my motherboard works fine for me now with Linux.  Do you have a SSD only system?  Have you updated your bios?  If sow which version of the ROM did you use?  The latest ROMs on the ASUS site for my MB say Windows only.

---

### Post by codingman on 2013-05-04
I have the latest ROM for my MOBO, and yes it is an SSD only system with a Fermi graphics card.

I am using version 1707, for other OS.

---

### Post by raxman on 2013-05-04
What do you mean by 1707?  And what is the latest ROM for your MOBO?  
If I go to the latest ROM for my MOBO it says Windows only (2012.11.27).  I upgraded to 2012.05.29 yesterday because that's the latest version that does not say Windows only.  I'm afraid to put the Windows only version on my system.
[http://www.asus.com/Motherboards/P8Z68V_PROGEN3/#support_Download_8](http://www.asus.com/Motherboards/P8Z68V_PROGEN3/#support_Download_8)

---

### Post by codingman on 2013-05-04
I don't think that there should be any difference, but then again... 

If it works for now, then I would leave it.

---

