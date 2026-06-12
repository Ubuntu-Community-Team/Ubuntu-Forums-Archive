---
title: "Windows 10 and Phoenix OS dual boot - troubles with GRUB"
date: 2017-03-23
forum: Windows
---

### Post by frank105 on 2017-03-23
Hi all, 

I need some help with GRUB in installing Phoenix OS on my laptop.
[COLOR=#454545][FONT=Hind]HP Pavilion x2 12-b020nr 12" Detachable Laptop with Intel Core M3, 4 GB RAM, 128GB SSD.

I have a pastebin results of Boot Repair [/FONT][/COLOR]http://pastebin.com/8BPj2eCc
The grub troubles are that the grub file seems to have Android-x86 as the option and kernal and I have finished testing that and have moved on to testing Phoenix OS.
When you choose it you get "Error - no such device.... Error file not found.

Actually - I have two problems.  I don't have grub installed correctly.  Windows 10 boots directly without a grub screen or choice.  But to get to any of the OS's I was testing I would hit ESC during boot to choose "Boot form EFI File"
Select file system 
PhoenixOS (for example)
boot
grubx64.efi 

Above are my current choices and it brings up a grub page that shows the x86 install and not my current Phoenix OS install. 

I think I am making this sound more complicated than it is.  
Summary
Grub is not booted by default (but I am handy at getting around that)
The current grub.cfg is not updated and I don't know how to update it

Oh and - I have the following bios settings:
USB Boot - Enabled
Network boot - Disabled
Legacy Support - Enabled
Secure Boot - Disabled
Platform Key - Enrolled

Anyway - thanks in advance for any help or pointers.

Regards,
Frank

---

### Post by frank105 on 2017-03-24
Oh one more note - during the unetbooting install of Phoenix it asks:
Do you want to install EFI grub 2 (I say Yes but I have tried No just for fun)
Select partition - I always pick SDA1
Do you want to format the boot partition - I always say no (but I am wondering if I should say yes?)
Next it goes on to
Do you want to install boot loader GRUB - I say yes but i have tried No

Just a little more info.
Thanks,
Frank

---

### Post by oldfred on 2017-03-24
Is this system one with 32bit UEFI?
You show this in sda1. /EFI/Boot/bootia32.efi which is for 32 bit UEFI boot?
But also have this: /EFI/Boot/bootx64.efi for 64 bit.

Most systems require Legacy/CSM off/UEFI on, and often better with secure boot off. But every system seems to have different ways to configuring those settings.
And a few like Dell seem to boot better in UEFI mode with legacy on. Most only boot in Legacy mode with Legacy/CSM/BIOS on.

Most HP are not UEFI dual boot friendly. 
       HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 
    
You already have /EFI/Boot/bootx64.efi, Boot-Repair will now copy shimx64.efi from /EFI/ubuntu to be bootx64.efi, but do not think with other systems it does that, so you have to manually do the copy like these older threads. And then boot the fallback/hard drive UEFI boot entry.

       HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by frank105 on 2017-03-25
Thanks Old Fred!

Okay - This stuff is still a little greek to me and I am going through it and learning. 

BUT - just a couple of generic questions:

Where/how can I edit the GRUB file that comes up when I get to "Boot from EFI file".  Any of the EFI files I choose all have the x86 android in there and not the Phoenix OS.  

I found the grub.cfg that DOES have the correct Phoenix OS listed in the menu.  So if I could just somehow edit the EFI file or where it points to?  

Wrinkle - by the way the boot repair usb program that I posted in the pastelink can't find my wireless nic so it can't connect to the internet.  Not sure if it finds other solutions if it were connected?  

When I install Phoenix using unetbooting it asks where to put EFI grub and if I want to format that partition.    Should I choose SDA1?  Should I choose to format it?  

Thanks again for all of your help,
Frank

---

### Post by oldfred on 2017-03-25
Do not know Phoenix.
But with grub you always install to a drive like sda, never to partition like sda1. 
With BIOS it installs to MBR, and with UEFI it installs to the ESP on sda (no matter what you say). Not sure if other systems have modified grub to correctly install to anything other than ESP on sda.

If UEFI boot, often easier to just do a full reinstall of grub.
But UEFI has a /EFI/ubuntu/grub.cfg to refer to install with full grub menu, then now sure how Phoenix does it. When I install another copy of Ubuntu it overwrites my main working install's /EFI/ubuntu. But all I have to do is restore or edit the /EFI/ubuntu/grub.cfg to be the UUID & drive of main working install. Reinstall of grub from Main working install would also fix that.

---

### Post by frank105 on 2017-03-26
Okay - I feel close. 

Sorry that I just don't understand how the links get me to my answer.  I know I am just not getting it.  But I copied my boot loader partition so I have a backup.  I have tried installing Phoenix with Unetbooting several times.  

Follow the link to pictures of my install to follow along...
Photo Link: 
[https://www.dropbox.com/sh/wltrlv2ueq9yg91/AADLBfKA0IGFnavcKRx5lyVAa?dl=0](https://www.dropbox.com/sh/wltrlv2ueq9yg91/AADLBfKA0IGFnavcKRx5lyVAa?dl=0)

I get options throughout the install:
where to install = sda5 (okay - I lost the real picture but it looks similar to this one...)
Do I want to install EFI Grub2 <-  I tried yes and no... same answer
Where do you want to install EFI Grub2 <- I have tried SDA1, 5 and 3 (5 is my Android partition, 3 is my Windows partition)
Do you want to format the boot partition dev/sda1 <--  I always say no except... more below
Do you want to install boot loader Grub <-- I tried yes and no ... same answer.  I guess this is Grub and not EFI grub??
Then I hit esc during boot to allow me to choose my boot and get this option <--- I choose boot from EFI file
It asks where to find the file <--- no other option at the top of the tree
Many options <--- tried em all
More options <--- tried them too.
If I choose the Android during the Grub screen I always get this error 

I think I have tried reinstalling so many times that I have 6 or 8 xxx.efi files in a variety of places.  I tried each one and they just don't work...

Okay - so with Peppermint linux (a favorite of mine on my multiboot thumb drive;)) I backed up SDA1 and then screwed with the original.  I was able to mount the partition and edit grub.cfg .  I got Phoenix OS listed in there and thought I was close - but it doesn't boot it either.

I choose to format SDA1 during the latest install.  I did successfully screw up my ability to boot Windblows but I figured I would... Ironically the copy of SDA1 shows up during the "Select a file system" when finding the .efi file to boot and windows will boot from there.  I am not worried.  

Okay so how do I properly build a custom .efi file.  How can I clean up all my .efi errors.  Can I just delete them in Peppermint?

My latest theory for an easy fix is to install Peppermint and see if the grub during install figures out where everybody lives and builds a good grub.cfg?  Trouble is with a 128GB drive I really don't have room so I was going to install it to my android partition and then reinstall Phoenix and then edit the grub.cfg by hand.

OR??  

Anyway - thanks again for all of the hints!

Regards,
Frank

---

### Post by oldfred on 2017-03-26
You want to install efi grub to sda, If your install is specific you can say the ESP, the FAT32 partition with the boot flag. But with Ubuntu you say sda, and it installs to ESP whether sda1, sda2 or whatever.

You do not build .efi files. 

Every system I have seen so far, installs in UEFI mode, if you boot installer in UEFI mode. Or installs in BIOS boot mode if you boot installer in BIOS/CSM/Legacy boot mode.

What is Phoenix? Or what is it based on? Link?

---

### Post by frank105 on 2017-03-26
Okay.  SDA1 is the FAT32 partition with the boot flag.  And so yes I did install EFI Grub there.  

Phoenix is Android that runs on x86 processors.
[http://www.phoenixos.com/en/download_x86](http://www.phoenixos.com/en/download_x86)
A better review of Phoenix (but older version) [https://liliputing.com/2016/01/phoenix-os-is-another-android-as-a-desktop.html](https://liliputing.com/2016/01/phoenix-os-is-another-android-as-a-desktop.html)

So Phoenix is part of the X86 project - porting Android OS to x86 processors:
[http://www.android-x86.org/](http://www.android-x86.org/)

For this little touch screen laptop - I think Android will make for a slick and speedy little tablet for daily browsing and emailing that can also boot into Win10 for anything OS restricted.  It will open up all of the free apps from the play store for video streaming and texting etc.  I had it working for 1 day and it was sooooo cool.  Trouble was - it doesn't support Widgets so I tried a CM13 port and then straight up X86 port...  X86 jazzed up the grub menu and then I just reinstalled anything and was never able to get my .efi files back.  

So - I am open to some surgery and I have a 1TB external if I need to backup any other partitions?

I was thinking of installing Peppermint install on SDA5 and ??  I am space limited so I haven't figured out what I could do yet...  

What do you think would be an easy way out of this?

Thanks again,
Frank

---

### Post by oldfred on 2017-03-27
Just do not know anything about Android based systems and how they work.

You can install Linux/Lubuntu on an external drive in UEFI or BIOS boot mode. I have several flash drives and have full installs in 16, 32 & 64GB flash drives, one or two still BIOS and all newer ones UEFI.
With UEFI Ubuntu installs the grub UEFI boot loader only to the ESP on sda. But to directly boot an external you must have an ESP, FAT32 partition on external and have the /EFI/Boot/bootx64.efi as boot file as that is the only file used to boot external UEFI devices. bootx64.efi can be Windows, grubx64.efi or shimx64.efi.

---

### Post by frank105 on 2017-03-27
Imagine Phoenix is just like a typical flavor of Linux. You use unetbootin to put the downloaded iso on a thumbdrive.  Choose install etc.  

The trouble I have is that I jazzed up my uefi files and have a bunch everywhere and none of work except for booting windows. 
My real question is how best to edit the boot files and how to get the boot file to boot first.  

I remember a few years back you had to go in and edit the grub.cfg files and I would be happy to do that I just don't know exactly what to type in there.  I know that grub is updated now and there are more tricks to it now.  

I am still reading and if I figure it out or find something close enough I will take another stab at it and see what happens.

Regards,
Frank

---

### Post by oldfred on 2017-03-27
The grub.cfg file in /EFI/ubuntu or /EFI/phoenix?
Or the full grub.cfg in your install?

The grub in the ESP is just a configfile entry to point to a full grub.cfg in your install.

If wanting to modify grub.cfg in your install, often easiest to just copy a boot stanza you know works into 40_custom.
       sudo nano /etc/grub.d/40_custom 
    
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by frank105 on 2017-03-27
Okay - I am really close now. 

The laptop boots to a grub screen and I can now go into windows 10 with no issues. 

But the grub.cfg menu entry for the kernel and intrd.img are incorrectly pointed (I think) to boot the Phoenix OS

I have new photos here: [https://www.dropbox.com/sh/wltrlv2ueq9yg91/AADLBfKA0IGFnavcKRx5lyVAa?dl=0](https://www.dropbox.com/sh/wltrlv2ueq9yg91/AADLBfKA0IGFnavcKRx5lyVAa?dl=0)

Current grub menu
[TABLE="width: 100%"]
[TR]
[TD]set timeout=3

menuentry 'Phoenix OS' --class android-x86 {
    search --set=root --file /efi/PhoenixOS/kernel
    linux /efi/PhoenixOS/kernel quiet root=/dev/ram0 androidboot.hardware=android_x86 SRC=/PhoenixOS vga=788
    initrd /efi/PhoenixOS/initrd.img
}
menuentry "Windows (UEFI)" {
    search --set=root --file /EFI/Microsoft/Boot/bootmgfw.efi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}[/TD]
[/TR]
[/TABLE]

do I change "...set=root--file /sda5/kernel or something?  

Thanks again in advance for any help!
Frank

---

### Post by frank105 on 2017-03-27
Following Einstein's example... I now know another thing that doesn't work...

OldFred - Sorry I didn't see your post earlier.
The grub.cfg file is in SDA1 a vfat partition at the beginning of the internal hard drive.  
It is in EFI/Boot i think.  There are no other grub files like 
/etc/grub.d/40_custom or any other common grub files.  I have been doing all of this editing via an install of peppermint on a usb thumb drive.  


The entry that is stuck in this grub.cfg file is:
menuentry 'OPhoenix OS.1.efi.boot' --class android-x86 {
    search --set=root --file /efi/PhoenixOS/kernel
    linux /efi/PhoenixOS/kernel quiet root=/dev/ram0 androidboot.hardware=android_x86 SRC=/PhoenixOS vga=788
    initrd /efi/PhoenixOS/initrd.img
}
The above does not boot anything but doesn't throw any errors.

Just trying to remember how the old school format was I typed in:
menuentry 'Phoenix OS.1.efi.boot' --class android-x86 {
     set root='(hd0,4)
l     inux /kernel root=dev/sda5
      initrd /initrd.img
}

But that faults out grub and brings you to the grub bash menu.

On SDA5 is the phoenix kernel and initrd.img files right at the root.  I could move them or rename?

By the way - The windows entry works :
menuentry "Windows (UEFI)" {
    search --set=root --file /EFI/Microsoft/Boot/bootmgfw.efi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}

Thanks for any and all hints!
Frank

---

### Post by oldfred on 2017-03-27
It looks like Phoenix installs all the boot into the ESP.
Do you have this, with kernel & initrd? /efi/PhoenixOS

Since that is not using grub but directly booting from UEFI, you would have to use UEFI's boot menu or f10 or f12 to choose what to boot.
Is Phoenix normally just installed to one FAT32 partition? So all of system is in the ESP, used just for booting with Windows or Linux?

---

### Post by frank105 on 2017-03-27
Hmm...  I think that Grub thinks /efi/PhoenixOS is where the kernel and initrd are.  

But they really are at sda5 in the root of that directory.  Both files are there and they work.  I just don't know how to manually build a menuentry into grub to point directly there.  I think I have read too much stuff and nothing seems to make sense anymore.  But I know how to get the blkid so if you can just point me to what the menu entry would be I think we will push this over the edge and make it a winner.  

I am not sure how I got it to happen but windows is booting the grub.cfg in sda1 and I know how to edit it.  All other files I can get to and if I hit esc (HP uses esc instead of f10 in my case) I can boot those other files - but none of them work either.  So since I know where the default boot file is, it really doesn't matter.  If I figure out how to make a menuentry for sda5 I will be good to go. 

Can you help me build a menuentry do boot sda5?

Thanks a bunch,
Frank

---

### Post by oldfred on 2017-03-28
You cannot mix UEFI & BIOS boot. 
Once you start booting in one mode you cannot change.

I have many examples of both BIOS boot stanza or UEFI boot stanza (most just a chain into ESP), but none for any type of Android system.

You Phoenix has to install boot files in UEFI mode, and it seems then they all are in the ESP - FAT32 partition, so UEFI can see it to boot. But you only can have one ESP per device. Or hide one (turn off boot flag) and unhide before rebooting into other system.

If BIOS and other installs are UEFI, then you only can boot from UEFI boot menu, not from grub as then you have started booting in UEFI mode.

This mentions it is 32 bit only?
[https://www.hitricks.com/en/guide-how-to-install-phoenix-os-on-your-pc-uefi-legacy](https://www.hitricks.com/en/guide-how-to-install-phoenix-os-on-your-pc-uefi-legacy)

This says you put Phoenix boot files inside the Ubuntu /(root) partition?
[http://www.techbian.com/install-dualboot-remix-os-and-ubuntu/](http://www.techbian.com/install-dualboot-remix-os-and-ubuntu/)

---

### Post by frank105 on 2017-03-29
I flew too close to the sun and was playing fast and loose with my Peppermint Linux usb boot stick and...  Messed up too many things.  

I gave up and reinstalled windows 10 and I am betting Phoenix will install without troubles.  

Thanks Old Fred for hanging in there.

Regards,
Frank

---

### Post by Jan_Johansson on 2017-04-08
Hi Frank and Oldfred, not to butt in, but I have a reverse problem to the one Frank is facing: Windows 10 boot menu is wrong and boots to windows recovery instead of going to windows desktop. ASUS ROG G551VW with UEFI GPT partitioning and factory installed windows 10 64bit. Ubuntu 16.04 installed secondary on sda5.

I need help editing grub and correct the windows 10 grub entry, can you two help me on that since Frank have a working windows 10 entry?

Ubuntu 16.04 boots just fine.

Oldfred - boot-repair does not work with 16.xx. When running it, it will give you commands to paste into terminal and these commands are depreceated so they will fail, then boot-repair can't continue and you can only chose discard which will remove grub totally from the system and delete most files needed to repair or re-install grub - it's a nightmare I had to deal with yesterday - trying to manually re-install grub running from live media fails because boot-repair removed the needed files including grub-install, grub-common, grub-pc, /etc/default/grub /boot/grub/grub.cfg, 40_custom and so on. Supergrub2 disc saved me and re-installed grub but only partially - /etc/default/grub /boot/grub/grub.cfg, 40_custom is still missing. So I got /etc/default/grub /boot/grub/grub.cfg from my own pc and it seem to be the same.  Point being, don't use boot-repair with 16.xx.

grub customizer indicating missing files
[https://www.dropbox.com/s/p0hiheko4uwc39b/IMG_20170408_213421.jpg?dl=0 ]("https://www.dropbox.com/s/p0hiheko4uwc39b/IMG_20170408_213421.jpg?dl=0")

grub windows 10 not working entry
[URL="https://www.dropbox.com/s/iu94zgtd04zdffw/IMG_20170408_215354.jpg?dl=0"]https://www.dropbox.com/s/iu94zgtd04zdffw/IMG_20170408_215354.jpg?dl=0
[/URL]
Current partition table
[https://www.dropbox.com/s/52wpanh4mcpu8w0/IMG_20170408_215846.jpg?dl=0](https://www.dropbox.com/s/52wpanh4mcpu8w0/IMG_20170408_215846.jpg?dl=0)

EDIT: made a thread of my own here: [https://ubuntuforums.org/showthread.php?t=2358065&p=13631003#post13631003](https://ubuntuforums.org/showthread.php?t=2358065&p=13631003#post13631003)

---

