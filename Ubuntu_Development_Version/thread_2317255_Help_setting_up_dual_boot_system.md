---
title: "Help setting up dual boot system"
date: 2016-03-14
forum: Ubuntu Development Version
---

### Post by PsychedelicWonders on 2016-03-14
How do I set up a dual boot system? 

I'm running an Asrock x99m Extreme4 mobo so I have UEFI but when I plug both of the SSDs in it's only seeing the windows


I  have Ubuntu 16.04 on a 128 SSD and Win 7 on a 256 SSD and when I plug  them both in it only shows the 256/Win7 SSD in boot manager, but if I  unplug it completely it will see the 128/Ubuntu SSD.



I  know you're normally supposed to install windows first, but I couldn't  get it to work so installed Ubuntu first, so I assume Windows overwrote  the GRUB like normal, but is there an easy way to set up a dual boot  system inside of UEFI once windows takes control of GRUB?

---

### Post by Bucky Ball on 2016-03-14
Get boot repair, with both SSDs plugged in run the bootinfo script (not the recommended repair), post the output link here. 

With both plugged in do you have the BIOS set to boot from the correct drive? Anyway, installing Windows second would have obliterated anything Ubuntu on the MBR so that's why you can't boot it.

Presuming this is a BIOS install and not UEFI. Please confirm.

---

### Post by yancek on 2016-03-14
Did you install both windows 10 and Ubuntu in UEFI mode?  If Ubuntu is not, that is the expected results.  See the link below for info on UEFI dual-booting. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If that doesn't help, go to the site below and get boot repair and run it selecting the option to CREATE BOOTINFO SUMMARY, do not try to do any repairs.  Post a link to the output here and someone should be able to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Bucky Ball on 2016-03-14
> **yancek said:**
> Did you install both windows 10 and Ubuntu in UEFI mode?

The OP says nothing about Win 10. This is Win7/Ubuntu. :)

But yes, I missed that before. If one is in UEFI, both must be. And vice versa. Presume that is your problem, and a common one it is.

---

### Post by PsychedelicWonders on 2016-03-15
Correct, this is a Ubuntu 16.04 and Windows 7 dual install on separate SSDs BOTH done in UEFI mode 

And the reason I did Windows 2nd was because I couldn't get it to install 1st at the time through UEFI so I just installed Ubuntu so I can use my new computer.  I plan to use Ubuntu 90% of the time, but need to jump to windows once in a while for a couple of things and already have the 2nd SSD and a Win7 key.

So I need to do the Boot Repair for sure?

---

### Post by dragonfly41 on 2016-03-15
There is another option you could evaluate.
If you use Windows infrequently I understand that Windows 7 can be installed as a VM on VirtualBox installed on Ubuntu 16.04 (although I have not done this myself).
So you could switch between Ubuntu and Windows without rebooting.
But you might prefer native performance rather than using an emulation layer.

---

### Post by howefield on 2016-03-15
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by kansasnoob on 2016-03-15
I'm still learning UEFI but during one of my tests I used two hard drives, each with a separate install of Ubuntu (Trusty and Vivid), and I created each install with only that drive connected. I ended up with a mess because each drive had it's own EFI/boot partition. It was unpleasant to try and fix but *[COLOR="#800080"]oldfred[/COLOR]* helped me through it. So with any luck, if you post the link to your boot info, *[COLOR="#800080"]oldfred[/COLOR]* will pop in and set us straight.

---

### Post by grahammechanical on 2016-03-15
The last Windows OS I installed was Windows 8 preview. I can confirm that the Windows installer will not only over-write the Linux boot loader on the disk that Windows is being installed to but it will also install the Windows boot loader to any disk that is connected.

So, yes you do need Boot Repair. For sure you do.

Regards.

---

### Post by psychedelicwonders2 on 2016-03-30
In the process of finally getting boot repair and installed and repair the boot loader

But once this is done and I have both SSDs hooked up, will it give me a GRUB menu at bootup to pick with OS SSD I want to load at that time, or is that an additional step I need to do?

---

### Post by oldfred on 2016-03-30
Best to just post link to summary report from Boot-Repair, it is does not work.

---

### Post by psychedelicwonders2 on 2016-03-30
[http://paste2.org/pIfGvYMU](http://paste2.org/pIfGvYMU)

So now with both SSDs hooked up at the same time, I am getting a grub menu, but only the Ubuntu SSD is showing up, but once I am logged into Ubuntu the second SSD is showing up on my left hand task bar

So how do I get the windows SSD to also show up under grub so I can pick with OS I want to load on the fly and is there any way to make the grub menu look a little nicer than just a DOS menu lol?

And for some reason under the Boot menu in UEFI, only the Ubuntu SSD is showing up as an allowable bootable SSD, it's not showing me the secondary SSD or allowing me to pick it that way?  Obviously I would still prefer the grub menu so I don't have to load UEFI every time I want to pick a specific OS

---

### Post by Bucky Ball on 2016-03-30
Open a terminal:

> sudo update-grub

Reboot. Windows on the list?

---

### Post by oldfred on 2016-03-30
Rerun report with both drives plugged in.

You only show Ubuntu installed in BIOS boot mode.
If Windows is in UEFI boot mode, you will not be able to boot from grub only UEFI boot manager.

Grub can only boot systems installed in same boot mode as grub/Ubuntu.
And how you boot install media is then how it installs. UEFI or BIOS.

Lots more useful info in link in my signature.

---

### Post by psychedelicwonders2 on 2016-03-30
> **Bucky Ball said:**
> Open a terminal:



Reboot. Windows on the list?

Yes it is now, thank you!

> **oldfred said:**
> Rerun report with both drives plugged in.

You only show Ubuntu installed in BIOS boot mode.
If Windows is in UEFI boot mode, you will not be able to boot from grub only UEFI boot manager.

Grub can only boot systems installed in same boot mode as grub/Ubuntu.
And how you boot install media is then how it installs. UEFI or BIOS.

Lots more useful info in link in my signature.

I was pretty sure I installed both in UEFI?  I must have because now after running update-grub they are both showing on the list

Now is there a way to re-arrange the grub menu or make it look better than a DOS prompt?  lol

---

### Post by oldfred on 2016-03-30
I usually change grub setting to only show for 3 sec, so I do not see it for long.

You can add background, colors and other fancy things:
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

UEFI is a boot manager(menu), grub is both a boot manager and boot loader.
But you can add still another boot manager that is gui based.
       
 [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by Cavsfan on 2016-03-30
Thanks oldfred for mentioning my wiki!

The link to the thread to post questions is in my signature and the 1st post has a green link to the wiki mentioned above.

Here is my current grub menu and I have Arch Linux, Xubuntu 16.04 and Windows 10 on my non-SSD HD.

[[IMG]http://www.zimagez.com/miniature/20160229163727.jpg[/IMG]]("http://www.zimagez.com/zimage/20160229163727.php")

That grub is installed on Arch and only has 2 colors, but in Ubuntu you can have 3 colors - 1 for top and bottom, 1 for the box and non-highlighted lines and 1 for the highlighted line.

I've had as many as 7-8 installs on this one drive but multiple drives is not a problem as the custom grub points to the drive/partition and not the UUID.

Here's one on Ubuntu from 2014 just to illustrate the 3 colors:

[[IMG]http://en.zimagez.com/miniature/20141222105039.jpg[/IMG]]("http://en.zimagez.com/zimage/20141222105039.php")

This is on a 28" monitor.

---

### Post by Cavsfan on 2016-03-30
If you do choose to try out my custom grub screen. It looks more difficult that it actually is. 
But, once you set it up, you never have to change it unless you remove or add a partition with an OS on it.
 
The best way to start would be to post the contents of your existing **/boot/grub/grub.cfg** in that link in my signature.

Regards..

---

