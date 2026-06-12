---
title: "Triple-boot problems after moving xp partition"
date: 2015-03-29
forum: Windows
---

### Post by konungursvia on 2015-03-29
I have a strange mix of issues but I think the solution might be similar to the one on ubuntuforums.org/showthread.php?t=1609385. 

I have been triple-booting Linux Mint 16, Windows 7 Pro and Xp64 pro for a long time. Forgot the Linux Mint password, so I installed 14.04 MATE over Mint 15.
But, foolishly, I tried to resize the xp partition a bit during the installation.

Now, I can boot 14.04 Mate, or Windows 7, but the Windows 7 boot option has xp below it... yet it returns "HAL.DLL file corrupt or missing."

I can't log into ubuntuforums.org from MATE for some reason (gives an error), but can here in Windows 7. 

My boot sector info scan shows all looked fine for most partitions but said, of the xp partition, something like:

"Boot sector info says sda5 starts at 6018 but information from fdisk shows sda5 starts at 1819971720."

So I downloaded a hex editor in 14.04 but don't know how to edit the boot sector info, and I don't know whether to make it match the fdisk or the other way around.

Does this make sense?

---

### Post by yancek on 2015-03-30
Not knowing the details of what resizing you tried to do, where xp was in relation to the other drives will make it difficult to make suggestions.  Probably the best thing you can do is to go to the boot repair site and download it in Ubuntu and run it with the option to Create Boot Info Summary.  You can then post that output here and someone might be able to help.

There is nothing I am aware of that any Linux system can do to replace a windows boot file such as HAL.DLL.  The boot repair script might tell if it can find it or you could try mounting the xp partition from Ubuntu to see if it is there.

---

### Post by CantankRus on 2015-03-30
Did you change the number of partitions?
Your boot.ini file in windows specifies a partition.
eg my boot ini with 2 XP installs
```
[boot loader]
redirect=usebiossettings
redirectbaudrate=
timeout=3
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="SOF2" /noexecute=optin /fastdetect /usepmtimer
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XP" /noexecute=optin /fastdetect /usepmtimer
```

---

### Post by konungursvia on 2015-03-30
Yancek - Thanks, I tried boot repair. 
Cantak - I kept the same number of partitions. I have windows 7 and xp, may I ask where boot.ini is? I searched the xp drive for such a file, but didn't see it.

---

### Post by CantankRus on 2015-03-30
> **konungursvia said:**
> Yancek - Thanks, I tried boot repair. 
Cantak - I kept the same number of partitions. I have windows 7 and xp, may I ask where boot.ini is? I searched the xp drive for such a file, but didn't see it.
It's on the highest level.
See pic looking from Ubuntu.

In XP I can run msconfig.exe to check boot paths.
[http://www.herongyang.com/Windows/msconfig-Manage-BOOT-INI-File.html](http://www.herongyang.com/Windows/msconfig-Manage-BOOT-INI-File.html)

---

### Post by konungursvia on 2015-03-31
I installed xp first, then win 7 pro, then ubuntu. So I think that affects where boot.ini is.
Here is my results.txt file:
[ATTACH]260993[/ATTACH]

---

### Post by yancek on 2015-03-31
What generally happens with windows is that the newer install will create an entry in its bootloader for the older windows so in your case, the boot file for windows 7 are on the first partition, sda1.  sda1 also has the xp boot.ini file which should be in the root of the filesystem, that is if you open My Computer and go to C:\, it should be there.  It might be a hidden file, can't remember.  It shows the partition for xp as (3) while your xp is actually on sda5.

It looks like sda1 is a separate boot partition, is that correct?  If you installed xp first, you would not have been able to install and boot it from sda5 where it is now because that is a logical partition and windows needs its boot files on a primary.  You could try running:  sudo update-grub from Ubuntu to see if it detects the xp, nothing to lose there.  I think you will need to find some way to update or modify the windows 7 boot file, bcdedit, I think.

---

### Post by CantankRus on 2015-03-31
> **konungursvia said:**
> I installed xp first, then win 7 pro, then ubuntu. So I think that affects where boot.ini is.
Here is my results.txt file:
[ATTACH]260993[/ATTACH]


You said you can boot into Windows 7 but it also gives you an XP option.
Grub just sends you to your windows boot.
eg in my grub menu I just see a windows loader which hands off to the windows boot.
[ATTACH=CONFIG]261010[/ATTACH]
 
So when you see the option to choose between  Windows 7 and XP you're already in windows.
If the Xp option doesn't work it's a Windows problem.

One possibility is the number or order of partitions has changed thus boot.ini is pointing
to the wrong partition to boot XP. You may have caused this when attempting to resize your XP partition.
You don't need to know where the boot.ini is.
You can boot into Windows7 and use msconfig.exe to check your XP boot path and edit the boot.ini if necessary.

---

### Post by yancek on 2015-04-01
> One possibility is the number or order of partitions has changed thus boot.ini is pointing
to the wrong partition to boot XP

Agree as the output the OP posted show xp on sda5 and his boot.ini file shows it on partition 3.

---

### Post by konungursvia on 2015-04-01
Thanks guys, but I don't see anything useful in msconfig.exe. There, we only see my Win7 boot information. Nothing about my xp.

What I was asking was, how specifically did this guy edit his boot information so it matched the results.txt:
[http://ubuntuforums.org/showthread.php?t=1609385](http://ubuntuforums.org/showthread.php?t=1609385)

He says "I did it" but doesn't explain how. That's what I think I need to do...

---

### Post by yancek on 2015-04-02
Grub gets you to the windows bootloader.  From there, it is up to the windows bootloader to boot the different windows operating systems.  You have a message that a hal.dll file is missing.  You are not going to be able to replace it from Ubuntu or any Linux.  You might try going to some windows forum and indicate that you had xp installed and then installed windows 7 and now you can't boot xp.  I'm not sure how you would edit the windows 7 boot file which, I think, is called bcdedit.

---

### Post by konungursvia on 2015-04-02
> **yancek said:**
> Agree as the output the OP posted show xp on sda5 and his boot.ini file shows it on partition 3.

Ah, interesting, how do I fix that?

---

### Post by yancek on 2015-04-02
Boot windows 7, look on whatever sda1 is for windows, probably some letter for the drive.  I believe you would need to log in as an administrator to be able to modify the boot.ini file there and I also believe it is a hidden file so you will have to find out, probably from a windows forum, how you can access/view a hidden file in windows.  I haven't used windows for years so I don't know.

---

### Post by Kenneth_Benson on 2015-04-04
The results txt is saying win 7 is the controlling boot. There is a hidden directory at the root level in Windows called Boot. just go to c:\ and cd boot to get there. The boot.ini should be there.

---

### Post by konungursvia on 2015-04-04
Ah, thanks, that was a good hint. In fact here is what I found... to install triple-boot, I must have used EFI underneath grub...

[ATTACH=CONFIG]261094[/ATTACH]

But, I honestly don't know for sure what to do from there.

---

### Post by konungursvia on 2015-04-09
So it seems to be in my win7 c:\windows\boot\ directory, but which files do I edit, do you know? are they hex?

---

### Post by CantankRus on 2015-04-09
Search for guides on how to use BCDEdit in windows 7.
eg [http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)
or 
search for ways to use the windows recovery option to fix boot/add installs to boot.
[https://msdn.microsoft.com/en-us/library/windows/hardware/ff543419(v=vs.85).aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/ff543419(v=vs.85).aspx)
If you go this route you will then have to [**_[COLOR="#B22222"]reinstall grub[/COLOR]_**]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

