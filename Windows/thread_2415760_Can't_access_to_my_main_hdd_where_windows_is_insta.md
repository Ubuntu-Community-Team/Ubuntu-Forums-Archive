---
title: "Can't access to my main hdd where windows is installed (Failed to read NTFS $Bitmap)"
date: 2019-03-31
forum: Windows
---

### Post by seniorbrayan on 2019-03-31
Hello, i have a problem. I have 2 OS, Windows 7 and Ubuntu 16.04. Therefore, it's partitioned.
I have 4 partitions:
-C:/
-Another that i have Ubuntu
-Another 2 where i have data (created in Windows).
In Ubuntu I was running out of memory. So i tried to install ntfs-3g (For an error that appeared to my hard drive c: / in GParted) and that was the last thing i did.
At the moment that i try to access to my partitions on Ubuntu of Windows i get an error (Failed to read NTFS $ Bitmap: NTFS input / output error is either inconsistent, or there is a hardware fault, or it's a SoftRAID / FakeRAID hardware. In the first case run chkdsk / f on Windows then reboot into Windows twice). 

Ok, i tried to use Windows 7. But there is a Blue screen when i try to enter. Then the computer restarts and shows me the grub again to select my OS.
I select Windows again. Now shows me the option to "repair computer" or "use windows normally". So i select "repair computer". The black screen appears with a Windows loading to give place to the other screen, but suddenly the screen is completely black and the computer is still on. But nothing load. 

So, i can only shutdown with the button.

I used a USB with Windows 7, i booted. I click on "Repair computer" and when i click, only the mouse and the Windows 7 boot background remains.

What can i do? I don't want to format my c:/ because i have my projects of the school there :(. 
Sorry for my bad english. Thank you for read.

---

### Post by yancek on 2019-03-31
> For an error that appeared to my hard drive c: / in GParted)

What error?  Why were you using GParted?

> Bitmap: NTFS input / output error is either inconsistent...

The above error is very common with windows 8/10 which hibernate by default which 7 does not.  Do you have windows 7 hibernated?  If so, turn it off before trying to access from Ubuntu.

Installing or trying to install ntfs-3g on Ubuntu isn't going to have any effect on your windows partitions.

> In Ubuntu I was running out of memory. So i tried to install ntfs-3g

Do you mean you were running out of disk space on your Ubuntu partition?  Did you modify your partitions with GParted?

---

### Post by Impavidus on 2019-03-31
Ubuntu gave you a fairly generic error message. It's unlikely you had to install ntfs-3g, as that is normally installed by default. It has been like that for ten years or so. It's quite safe to use it to access ntfs data partitions. If damage occurs (which is possible, as ntfs drivers on Linux aren't perfect), Windows can fix it. Accessing the C partition is less safe, as damage there (not just filesystem damage, but also deleting or modifying the wrong files) may make Windows unbootable. On the only Ubuntu/Windows dual boot computer I have here, I automatically mount several ntfs partitions using fstab, but put the C partition in there with the options to make sure it's not mounted.

I hope you've got backups of your important files, both on the Windows side and on the Ubuntu side. You should always have those. If not, make them now.

A damaged ntfs partition is a Windows problem. The tool most likely to fix it is a Windows repair disk.

---

### Post by seniorbrayan on 2019-03-31
>  [COLOR=#000000]What error? [/COLOR] 
"Impossible to read the contents of this file system.
Because of this, some operations may not be available.
The cause may be that a software package is missing.
The following list of software packages is required for the support of the ntfs file system: ntfs-3g / ntfsprogs."

> [COLOR=#000000]Why were you using GParted?[/COLOR]
To expand the Ubuntu space, but I did not expand it or anything.

> [COLOR=#000000]Do you have windows 7 hibernated? [/COLOR]
Nope :s

Also i cannot access to "Repair computer" on my bootable usb and in my windows 7

> [COLOR=#000000]Do you mean you were running out of disk space on your Ubuntu partition? [/COLOR]

Yeah!, but at the final i did not modify any partition

---

### Post by yancek on 2019-03-31
> "Impossible to read the contents of this file system.

If I understand correctly, you got this message while in GParted, correct?

> The following list of software packages is required for the support of the ntfs file system: ntfs-3g / ntfsprogs."


Were you able to install either/both of thoss programs.  You can verify this in  terminal with either the whereis or which command, i.e:  whereis ntfs-3g
So it would appear your windows system is corrupted or has some problem.  THere is Linux software (ntfsfix) which if installed and used correctly, can sometimes make very minor repairs but if it anything more than that, you need windows tools.

---

### Post by seniorbrayan on 2019-03-31
Yep, that was the GParted.
I used "sudo ntfsfix /dev/sda2" (where is C:/) and this happens
[IMG]https://i.imgur.com/BcnYEG9.png[/IMG]
What should i do?

---

### Post by oldfred on 2019-03-31
You cannot fix most Windows errors from Ubuntu.
The NTFSfix application really just sets the chkdsk flag so Windows on reboot will run chkdsk. 

But if you cannot boot in Windows recovery mode, you need to use your Windows repair flash drive or installer with repair console. Probably chkdsk but perhaps other repairs are then required.

---

### Post by seniorbrayan on 2019-04-01
When i boot with my pendrive and i click "Repair computer" nothing happens :s (only the mouse and the background of windows 7 installer remains on the screen) 
And i tried to run in Safe mode, loads a little bit of drivers (i guess XD) but appears a blue screen.

---

### Post by oldfred on 2019-04-01
You can only fix from Windows, but post this to see if NTFS has correct partition boot sector.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by seniorbrayan on 2019-04-01
Sorry, i can't understand o.O

---

### Post by lisati on 2019-04-01
> **seniorbrayan said:**
> Sorry, i can't understand o.O

At the link @oldfred provided, there's a link to a page about a tool called "boot repair." One of the options provided by the tool is to create a text file containing diagnostic information that might be of some help to the community members who are trying to help you.

---

### Post by oldfred on 2019-04-01
Just wanted you to run & post link to summary report from Boot-Repair.
It will not fix Windows but may show issues.

---

### Post by seniorbrayan on 2019-04-02
But i should install on my ubuntu or use it with the iso in a usb? xD i can't understand that, sorry

---

### Post by oldfred on 2019-04-02
You can run it from your live installer, the flash drive you create to install Ubuntu from the ISO.

---

### Post by seniorbrayan on 2019-04-03
Sorry for the delay u.u
Here is the summary:
[http://paste.ubuntu.com/p/kpmQCNMGWN/](http://paste.ubuntu.com/p/kpmQCNMGWN/)

---

### Post by oldfred on 2019-04-03
And report shows issues with your NTFS main partition sda2.
But sda1, the Windows boot partition seems to be ok. Can you boot to Windows recovery mode with f8?
Grub usually boots into Windows too fast for the f8 key to have time to be pressed. One user posted that after trying many times and being really quick he did get it to work. But typically you have to temporarily reinstall Windows boot loader to MBR of grub. You still have grub in MBR.

You can reinstall the Windows boot loader from your Windows repair disk or Windows install disk with repair console.
Boot-Repair may let you install a Windows type boot loader since it can see sda1. In advanced options see if you can choose Windows & sda as drive to install into. If not only a Windows repair disk will work.

---

### Post by seniorbrayan on 2019-04-04
I tried to boot windows 7 with my usb and this happens (when i try to boot windows normal, in safe mode, or with the install disk)
I can't access to repair computer :s
What should i do?
[https://www.youtube.com/watch?v=UIGC6bMaxrY](https://www.youtube.com/watch?v=UIGC6bMaxrY)

---

### Post by oldfred on 2019-04-04
Moving to the Windows sub-forum.
We only know minor Windows fixes, some of us do dual boot and they may look in Windows sub-forum.
Best to ask on a Windows forum. But post issue not long video.
I think Windows 7 also expires next year.

       [http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[https://support.microsoft.com/en-us/kb/927392/](https://support.microsoft.com/en-us/kb/927392/)

---

### Post by seniorbrayan on 2019-04-08
Now i fixed that, using a rescue disk and chkdsk.
But when i try to boot i have the error "No such partition, entering rescue mode".
I booted Windows with supergrub2, but how can i recover my ubuntu dual boot grub? :s sorry

---

### Post by yancek on 2019-04-09
Use the Ubuntu 'live' usb and repeat the process to get and run boot repair and post the new link since things have changed.

---

### Post by oldfred on 2019-04-09
With all the Windows fixes it probably is the Windows bug (Windows may call it a feature?) that re-writes the partition table but conveniently forgets to include Linux partitions.
If not then we need a new Summary report from Boot-Repair.

       Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988) &
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[https://www.gnu.org/software/parted/manual/parted.html#rescue](https://www.gnu.org/software/parted/manual/parted.html#rescue)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition](https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition)

---

