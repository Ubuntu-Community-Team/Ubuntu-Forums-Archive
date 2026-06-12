---
title: "UEFI presents  security risk/soft brick"
date: 2014-08-03
forum: Ubuntu, Linux and OS Chat
---

### Post by ventrical on 2014-08-03
My most recent  endeavour to incorporate a dual-boot UEFI  system of Win8 sideXside with  ubuntu revealed that the process was able to manipulate the Intel Management Engine BIOS Extension (with password protect) and set the normally off  Intel ATM "M" state led to "ON".

 In plain english this means that when the PC is powered down the red LED should remain constant when the ATM/ME is in the off state. When the LED is blinking this means that an out of band remote access can be achieved with someone who has  the particular software that accesses these features of the ME.

 It is claimed the UEFI is supposed to give us more control over our computers but, gaining access to password protected ME can be indicative of a soft brick  in progress or the potential for a soft brick in the future tense - also lending to the possibility of a hard brick. Unfortunately I did not document the precise moment of this activity. After enabling UEFI in BIOS I proceeded to install Windows 8, then Ubuntu. I tired several different methods with varied success. Being that I do not recall the exact moment that the switch was flicked in the ME I cannot file a bug .. but I just thought I would make note of this for future reference.

Regards..

---

### Post by oldfred on 2014-08-03
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

And even more security lock-down is coming.

 Some UEFI also have TPM 
[http://technet.microsoft.com/en-us/windows/dn168169.aspx](http://technet.microsoft.com/en-us/windows/dn168169.aspx)
UEFI secure boot doesn't have anything to do with a TPM.
[https://www.ibm.com/developerworks/community/blogs/smartersecurity/entry/uefi_secure_boot_and_the_tpm20?lang=en](https://www.ibm.com/developerworks/community/blogs/smartersecurity/entry/uefi_secure_boot_and_the_tpm20?lang=en)
Microsoft has announced that from January 1, 2015 all computers will have to be equipped with a TPM 2.0 module in order to pass Windows 8.1 hardware certification.
[https://en.wikipedia.org/wiki/Trusted_Platform_Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module)

---

### Post by ventrical on 2014-08-03
I have 2 machines with TPM. I had read most of what you have linked previously. Thank you for the added information.

 As an added note I am just baffled at this whole ELAM form factorette.  The way I see it - the whole way MS is approaching this is that they are infecting current form factors with a legal form of malware.

 So .. the main point of all this is that a PC , mobile or whatever various other that has windows 8 with Secureboot installed and UEFI enabled will mother-bend any attempts of a linux/ubuntu install - not that it will security check it's own exploitable security vulnerabilities until they are "discovered".  It's almost right back to when they first released Vista . The only difference  is that probably there will be more time in the chair blackboarding work arounds. ... and malware writers will have a field day. Actually , in MHO, ELAM and UEFI is an open invitation.

Regards..

---

### Post by ventrical on 2014-08-03
Looks like I bricked my Intel DB43LD. I was able to get to ME, change password then disable ATM.  I cleared the onboard TPM of all keys.  For some  brain cramp of a reason I decided to boot up with the UEFI hdd with Win8 and Ubuntu on it. (UEFI disabled). From there all went south and now it is stuck on stupid - locks up at <Hit CTRL + P to enter Intel ME>.

  Iv'e set the jumpers , removed the battery , disabled passwords.. etc... she won't budge. But these are the problems which I thrive off of.  Looks like I'll have to burn some midnight oil.

Edit:

Ok... whew .. well .. I saved that system somewhat.  It is software bricked in the sense that ME in the <disabled> state will not allow the PC to run. I was able to get into ME and re-enable the ATM etc.. so I'll just have to put up with he blinking red LED when I shut down. It's only surplus anyways .. but man .. did that ever peeve me off.   I can use that one for UEFI/TPM experiments.... but what a lame concept. It's not a fun Ubuntu thing .. ya know :( lol

---

### Post by ventrical on 2014-08-04
Thanks ;)

I'm back at it :)lol

---

### Post by ventrical on 2014-08-04
I most likely wrote about this somewhere on the forums already. I have successfully repaired  the install in question. All I had to do was re-enable UEFI and then re-install Windows 8 on the originally resized partition that was created with gparted!! The re-install overwrote The Microsoft Recovery environment, the EFI and the reserved partitions. The previously installed Ubuntu 14.04.1 works just fine so far.

So I come up with a preliminary method-VSUFCUEFI or 'veesoofcoefi' for Ventrical's Simplified Ubuntu First Concept for UEFI.:) lol

1. Never buy any PC product that had Windows 8 installed on it unless a Windows 8 DVD comes with it. If you do so then you deserve to have your system bricked.


2.Use Ubuntu live, run gparted and create a ntfs for Windows 8 and an ext4 for Ubuntu (also 1MB for [biosgrub].

3. Install Ubuntu with UEFI enabled.

4. Install Windows 8


Now to update ubuntu and see what happens :)

Regards..

edit:

All smooth running here.

---

### Post by ventrical on 2014-08-04
Here is table:

```

ventrical@ventrical-desktop:~$ sudo parted -l|tail -n8
[sudo] password for ventrical: 
 2      316MB   420MB   105MB   fat32           EFI system partition          boot
 3      420MB   555MB   134MB                   Microsoft reserved partition  msftres
 4      555MB   53.0GB  52.4GB  ntfs            Basic data partition          msftdata
 5      53.0GB  76.1GB  23.1GB  ext4
 7      76.1GB  76.1GB  1049kB  ext4                                          bios_grub
 6      76.1GB  80.0GB  3978MB  linux-swap(v1)


ventrical@ventrical-desktop:~$ 


```

---

### Post by oldfred on 2014-08-04
The bios_grub is for BIOS boot and the efi partition is for UEFI boot. 
You do not need both unless you want to boot both ways like this:

       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

I do not think any Windows system comes with the install DVD. But almost all let you make the recovery set and you really should make a full backup if you spend the time to reconfigure Windows and remove the junk included, otherwise your recovery set makes you do it again when you restore it.

---

### Post by ventrical on 2014-08-04
> **oldfred said:**
> The bios_grub is for BIOS boot and the efi partition is for UEFI boot. 
You do not need both unless you want to boot both ways like this:

       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

I do not think any Windows system comes with the install DVD. But almost all let you make the recovery set and you really should make a full backup if you spend the time to reconfigure Windows and remove the junk included, otherwise your recovery set makes you do it again when you restore it.

I could not get Ubuntu to boot in UEFI without the [bios-grub].. but looks like more reading for me. :)

---

### Post by oldfred on 2014-08-04
If you are using bios_grub then you are booting in BIOS/CSM/Legacy boot mode. Some systems require you to turn on UEFI to boot Windows and turn on CSM/BIOS to boot Ubuntu then. Others recognize the difference and let you use one time boot key and it auto boots in correct mode. You cannot dual boot from grub menu as UEFI and BIOS are not compatible.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 



And since UEFI & BIOS are so different some systems need different boot parameters to implement correct drivers. A few only install in BIOS mode, but Boot-Repair can convert by uninstalling grub-pc (BIOS) and installing grub-efi-xxx. Several versions of grub-efi depending on secure boot on, only UEFI, Mac and maybe later a 32 bit version, so name now includes amd64.

---

### Post by ventrical on 2014-08-04
> **oldfred said:**
> If you are using bios_grub then you are booting in BIOS/CSM/Legacy boot mode. Some systems require you to turn on UEFI to boot Windows and turn on CSM/BIOS to boot Ubuntu then. Others recognize the difference and let you use one time boot key and it auto boots in correct mode. You cannot dual boot from grub menu as UEFI and BIOS are not compatible.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 



And since UEFI & BIOS are so different some systems need different boot parameters to implement correct drivers. A few only install in BIOS mode, but Boot-Repair can convert by uninstalling grub-pc (BIOS) and installing grub-efi-xxx. Several versions of grub-efi depending on secure boot on, only UEFI, Mac and maybe later a 32 bit version, so name now includes amd64.

  I am using the F10 boot option, not GRuB. The UEFI is <enabled>  in CMOS.  As in a recent message I  used :

```


sudo update-grub

```

and it broke the Windows 8 install.

  I also have Intel ME,TPM active and had cleared out  the old keys before re-installing.

  I'll get a pic of it.

 Regards..

---

### Post by ventrical on 2014-08-04
@oldfred

Here is pic:

I do not totally understand what you are trying to convey. (my bad I suppose)

Could you elaborate please.

Thanks

---

### Post by ventrical on 2014-08-04
> **oldfred said:**
> If you are using bios_grub then you are booting in BIOS/CSM/Legacy boot mode. Some systems require you to turn on UEFI to boot Windows and turn on CSM/BIOS to boot Ubuntu then. .

 My experience is that Windows 8 and Ubuntu get along just fine with UEFI disabled and GRuB taking over. I am doing this research in hopes to help find a more expedient way to work around the current problem of  the trusty version ubiquity installer not being able to recognize the windows8 or UEFI partitons during the installation stage.

  I am just trying different things here .

Thanks for your continued help and expertise on this matter.

Reagrds..

---

### Post by ventrical on 2014-08-04
... I am still reading the links you provided .. ie; on boot repair and etc..

regards..

---

### Post by oldfred on 2014-08-04
I know os-prober and some other tools want to open a partition and look to see what is in it. But the Linux NTFS driver will not mount a NTFS partition that is hibernated (fast boot) or needs chkdsk (which after any resize it needs).
But partition table will show the NTFS partitions. And just looking at partition table you know if something whether data or bootable system is there. Installer should be smart enough to at least ask about existing partitions if seen in partition table even if not mountable.

---

### Post by ventrical on 2014-08-05
> **oldfred said:**
> I know os-prober and some other tools want to open a partition and look to see what is in it. But the Linux NTFS driver will not mount a NTFS partition that is hibernated (fast boot) or needs chkdsk (which after any resize it needs).
But partition table will show the NTFS partitions. And just looking at partition table you know if something whether data or bootable system is there. Installer should be smart enough to at least ask about existing partitions if seen in partition table even if not mountable.


Yes.. agreed .. absolutely.

---

### Post by ventrical on 2014-08-05
I decided to do a little experiment using Maveric 10.10.  Surprisingly the Ubiquity installer was able to identify all of the partitions while in UEFI mode enabled. I then wanted to go further with <Install alongside other operating systems> and it came up with the Windows ntfs filesystem and recommended ext4 partition.  I decided to back out of installing Maveric but I hit the wrong button accidently and Maveric installed itself while resizing the ntfs partiton!! so I decided to finish the install.

  I then shutdown and rebooted. Windows 8 worked just fine. I then re-booted and entered UEFI and chose Ubuntu 14.04.1 and sudo update-grub. It found the 10.10 install plus the Windows 8 UEFI partition. I rebooted and entered back into Windows 8 and it was not borked. Just to be sure I allowed updates and reconfigure to take place before I go on any further.

So maybe the answer to all of this may be in the old Maveric Ubiquity Installer.

---

### Post by ventrical on 2014-08-05
After the Maveric episode I went back to 14.04.1 and sudo update-grub.

 Now I can safely boot Windows 8 , Maveric and 14.04.1 from the GRuB Menu from the F10 boot options menu when I choose <ubuntu>. The Maveric partitoner/installer did what 14.04.1 was not able to do. Just baffling... and I'm having fun too :) lol

There was one little error while booting maveric .. something about an efi gene. I'll try to capture that.

---

### Post by oldfred on 2014-08-05
I think 10.10 was well before UEFI, but does recognize gpt partitions. So that would only install in BIOS mode.

I saw somewhere that if you boot 14.04 in BIOS mode it will see Windows 8, but in UEFI mode it does not. Not sure why that would be different as grub is the main difference between UEFI & BIOS installs. 
But BIOS does write drive info for boot loader differently than UEFI, so something is not correctly identified.

       Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

---

### Post by ventrical on 2014-08-06
Still a long way to go.

[https://www.youtube.com/watch?v=V2aq5M3Q76U](https://www.youtube.com/watch?v=V2aq5M3Q76U)

---

### Post by oldfred on 2014-08-06
More current info in his blog.

 Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)
New Linux UEFI boot loader - hash based no key
[http://mjg59.dreamwidth.org/23113.html](http://mjg59.dreamwidth.org/23113.html)
UEFI generic shim - Secure Boot bootloader newer version than Ubuntu
[http://mjg59.dreamwidth.org/20303.html](http://mjg59.dreamwidth.org/20303.html)

---

### Post by ventrical on 2014-08-06
Quoting Matthew Garret"

> 
The security model on the Google Nexus devices is pretty  straightforward. The OS is (nominally) secure and prevents anything from  accessing the raw MTD devices. The bootloader will only allow the user  to write to partitions if it's unlocked. The recovery image will only  permit you to install images that are signed with a trusted key. In  combination, these facts mean that it's impossible for an attacker to  modify the OS image without unlocking the bootloader[1], and unlocking  the bootloader wipes all your data. You'll probably notice that.


I get the willies when people use the term "impossible".  It's like when I tried to bring a security hole in IE to the attention of MicroSoft brain trust .. and they reply .. 'That's impossible!' and then ... but ya know .. UEFI is the next new shiny thing and maybe we can have some fun with it. :)

---

### Post by ventrical on 2014-08-06
other links on UEFI security:

[http://www.itnews.com.au/News/338892,global-security-nightmare-for-pcs-narrowly-averted.aspx](http://www.itnews.com.au/News/338892,global-security-nightmare-for-pcs-narrowly-averted.aspx)

[http://it-beta.slashdot.org/story/13/08/03/0135248/researchers-demo-exploits-bypassing-uefi-secure-boot](http://it-beta.slashdot.org/story/13/08/03/0135248/researchers-demo-exploits-bypassing-uefi-secure-boot)

[http://support.microsoft.com/kb/2871690](http://support.microsoft.com/kb/2871690)

getting bricked by cyber sabotage
[http://www.se-eng.com/2014/06/02/more-security-issues-crop-up-with-uefi/](http://www.se-eng.com/2014/06/02/more-security-issues-crop-up-with-uefi/)


[http://securityaffairs.co/wordpress/25425/hacking/bypass-secure-boot-uefi.html](http://securityaffairs.co/wordpress/25425/hacking/bypass-secure-boot-uefi.html)

---

### Post by kansasnoob on 2015-02-05
I'm having all kinds of fun with a similar (or the same) mobo :lolflag:

I me-too-ed this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940)

---

### Post by ventrical on 2015-02-10
> **kansasnoob said:**
> I'm having all kinds of fun with a similar (or the same) mobo :lolflag:

I me-too-ed this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1050940)

:)

 I totally forgot about this thread :)

---

### Post by kansasnoob on 2015-02-10
> **ventrical said:**
> :)

 I totally forgot about this thread :)

I found it when I was googling DB43LD + something, maybe the AMT thing.

I ordered another hard drive and swapped cases because it would have been too much work to swap drives with the first case I used - it would have required disconnecting the 24 pin power connector and removing the CPU cooler each time I wanted to swap drives, way too much hassle for a testing PC.

I'll post some pics when I'm actually done. It's turning out to be quite a nice PC for its age. I bumped the RAM up to 3 GB since you included the extra sticks, and I then used the 2 GB in another compatible box, and I was then able to use a 1 GB stcik out of that one to bump another PC from 1 GB to 2GB. So it feels like Xmas here :D

I haven't tried the DVI output yet but that's about next on the list.

---

### Post by kansasnoob on 2015-02-10
BTW I'm using it now as a temporary replacement for my media center box so I could move that one into my test suite and more efficiently work on this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1412602](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1412602)

So thanks again for the UEFI test hardware. Between the additional testing capabilities it provides me and the tests you'll be able to perform with the new 3 TB hard drive Canonical is the big winner ;)

---

