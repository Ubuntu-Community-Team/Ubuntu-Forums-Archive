---
title: "OpenELEC multi boot Grub error"
date: 2016-08-04
forum: Ubuntu/Debian BASED
---

### Post by wickedx on 2016-08-04
Hi I'm brand new to these forums but have tried to find the answer to this but cannot anywhere. Not on these forums or Google!

I'm fairly new to ubuntu and linux in general so be gentle....

I've been running Windows 7 and Kodi for years now but getting more and more frustrated with windows so decided to dual boot to Linux. I now have successfully got Ubuntu and Win7 dual booting. But I now want to try out OpenELEC as a third install. I don't want to wipe my other installations.

My hard drive is partitioned as follows:

/dev/Sda
Sda2 NTFS - Win7 flag boot
Sda3 ext4 - ubuntu
Sda4 extended to:
 Sda5 linux swap
 Sda6 Ext6 OE_System flag boot
 Sda7 ext7 OE_Data

I copied the KERNSL and SYSTEM files from the extracted OpenELEC legacy as I'm running Acer Revolution with ION

I did this and added to grub menu using the following instructions: [http://wiki.openelec.tv/index.php/Dual_Boot](http://wiki.openelec.tv/index.php/Dual_Boot)

I have the option in Grub for OpenELEC but get the following error:

Error :file '/vmlinuz' not found
Error: You need to load the kernel first

I have tried making a live USB of Openelec and this work however it won't let me install it to the specific portion and only wants to wipe the entire drive which I don't want to do. 

Can anyone provide some guidance please? I know I have probably made a mistake somewhere in the openelec manual install as simply copying the kernel and system file seems to easy! Thank you in advance.

Loving Ubuntu BTW! So much quicker and enjoying getting back into programming! Really enjoying it.

---

### Post by howefield on 2016-08-04
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by oldfred on 2016-08-04
Some systems do not like two boot flags.
And surprised they want a boot flag as grub does not use boot flag, if using syslinux boot loader then it would need boot flag.

They are using partition label in grub search so labels must match search exactly.

Post link to summary report.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by wickedx on 2016-08-04
Hi thanks, I will take the boot flags off and see if that makes a difference. As I am manually sleecting the OpenElec option on grub I can't see why this would cause a problem?

Summary report uploaded [here]("http://paste2.org/BUPyPO6U")

---

### Post by oldfred on 2016-08-04
Did you delete a 100MB Windows boot partition (sda1)?
You are missing the boot files bootmgr & /boot/bcd.

 Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe  

Use your Windows repair flash drive to add boot files. But you must have boot flag on sda2. You do not have to have the separate Windows boot partition, but Windows only repairs partition with boot flag.

Did you use Grub Customizer? That adds its own grub scripts as proxy files. 
Boot-Repair's total reinstall of grub will houseclean out the proxy files.

You have a hint of (hd0,4) which is the extended partition.

You show label as OE_System , search for OE_System, but boot of OE_SYSTEM. Case is used in Linux systems so those are not the same.


```
 menuentry "OpenELEC DEBUGGING" {

 search --set=root --label OE_System --hint hd0,msdos4
linux /KERNEL boot=LABEL=OE_SYSTEM disk=LABEL=OE_DATA debugging 

 }
```

---

### Post by wickedx on 2016-08-04
Thank you I will try all of that and report back! Yes I deleted the 100mb partition as I didn't think it was needed. I'm not in too much need of windows 7 at the moment but I'll repair this so it's all correct. Thank you again and hopefully this will put me in the right direction.

---

### Post by wickedx on 2016-08-04
Thank you I will try all of that and report back! Yes I deleted the 100mb partition as I didn't think it was needed. I'm not in too much need of windows 7 at the moment but I'll repair this so it's all correct. Thank you again and hopefully this will put me in the right direction.

---

### Post by wickedx on 2016-08-05
Windows7 option has now gone from the grub menu (it must of auto detected the boot was missing). I tried windows repair but no luck. Win7 is gone but I'm not too worried about this. I have all the files I need backed up and I'm happy with ubuntu. If I can't get OpenElec working soon I'll probably just stick with ubuntu and Kodi with automatic startup. But it would be nice to figure this out!

I've ran the boot repair and this is the summary[Http://paste2.org/3e0m1zL9](Http://paste2.org/3e0m1zL9) . 

I had used grub customised to try and get the OPENELEC working as I got the error showed on the first post when adding the menu item via the commands at the guide:
[https://blog.jordanhopfner.com/2013/01/10/triple-boot-windows-7-linux-openelec/]("https://blog.jordanhopfner.com/2013/01/10/triple-boot-windows-7-linux-openelec/")

I'm just about to reboot but in case I have any problems I thought I would paste this. I will update the items for the grub menu once I've proved my ubuntu installation and boot is all correct. 

Am I able to use the grub customised to add the entries for OPENELEC or should I add them via the terminal as at the guide?

Thank you. I really appreciate your help.

---

### Post by wickedx on 2016-08-05
So Ubuntu is starting up no problems. So happy I still have a working system.

I've ran the startup repair and it's uninsulated and reinstalled grub boot. 

I've now added an entry using the following command:

	
sudo gedit /etc/grub.d/40_custom

Added my OPENELEC entry as follows:

menuentry "OpenELEC" {
	set root=(hd0,6)
	linux /KERNEL KERNEL boot=/dev/sda6 disk=/dev/sda7 quiet nosplash
}


This isn't showing up on the grub entry boot options. What have I done wrong with the entry onto the grub boot options? I know I'm so close to getting this resolved. It's clearly my lack of experience and knowledge of this holding me back. Loving learning though.

---

### Post by wickedx on 2016-08-05
Strange, I ran the grub customiser and OpenELEC appeared on the menu so I moved it to the top of the list and restarted and it now shows up and runs! So apart from my Windows installation now not working I'm all sorted! Thank you very much oldfred!! Your steer to check the case, menu entries and boot repair tool pushed in exactly the right direction. 

Thank you very much and hopefully this will be easily findable for anyone else having trouble!

---

### Post by oldfred on 2016-08-05
Glad you got it working. Please change post to solved. (see my signature.)

Perhaps after editing 40_custom, did you forget the sudo update-grub? I do that all the time and when I reboot I know I forgot it.

---

### Post by wickedx on 2016-08-05
Yes I think I did, I ran through everything again and did that, I never thought I had forgotten it but that would make perfect sense. Thank you very much. I've learnt a lot these past few days! Wish I had switched to Linux years ago!

---

