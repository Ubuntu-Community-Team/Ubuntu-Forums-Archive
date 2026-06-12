---
title: "Messed up /RebuildBcd command, now can't boot either Win7 or Ubuntu - blinking cursor"
date: 2016-07-28
forum: Windows
---

### Post by a-loefgren on 2016-07-28
Hello,

I spent about 10 hours last night trying all possible solutions I could find on this and other forums, so if this has already been solved elsewhere and I have not found it, I sincerely apologies for the double. It seems that none of the existing [solved] threads work for me. Here follows a description of i) **what I** **intended to do**, then ii) **what I** **actually did**, and, finally, iii) **what I have tried so far** and iv) **where I am at now**. Any help much appreciated! I really do not want to lose the existing Windows installation, because it contains several important pieces of licensed software that I use for work on a daily basis. Here goes:

**i) WHAT I INTENDED TO DO**

Yesterday, I decided that I wanted to remove my partition containing **Ubuntu Studio** and extend my **Windows 7** installation onto it -- in other words, I wanted to **get rid of my dual-OS setup** by removing Ubuntu but **keep Windows 7 Home Premium intact**. So, here's what I intended to do:

1. Insert Windows 7 installation/recovery CD in disc drive and **boot from CD** drive in BIOS.
2. In **Windows installation program**, select **Repair Your Computer** option in the dialogue prompt.
3. In the **System Recovery Options** menu, open the Command Prompt.
4. In the **Command Prompt (X:\Sources>)**, type the following, in order to restore the Windows boot manager in place of GRUB:

```

bcdedit /export C:\BCD_Backup
C:
CD Boot
Attrib bcd –s –h –r
ren c:\boot\bcd bcd.old
bootrec /RebuildBcd
```

[B]ii) WHAT I ACTUALLY DID
[/B]
I am pretty sure that the whole problem arose when I **forgot to execute** the first of the commands: ```
bcdedit /export C:\BCD_Backup
```
Instead, I started the whole process from

```

C:CD Boot
Attrib bcd –s –h –r
ren c:\boot\bcd bcd.old
bootrec /RebuildBcd
```

skipping the entire first line ```
bcdedit /export C:\BCD_Backup
```. After that, I rebooted and found myself staring at a blank screen with a blinking cursor, in other words no GRUB menu, and no Win7 boot. My only option is Ctrl-Alt-Del. This issue persists still today after all my attempted solutions below.


**iii) WHAT I HAVE TRIED SO FAR**

- Boot using the Windows installation CD in order to run the automatic **Startup Repair** option. Result: **Fail**, because the existing Windows 7 installation is not recognised by the installer.
- Boot using the Windows installation CD, and in the **Command Prompt** tried to repeat the whole sequence from the beginning, this time not forgetting to include the first command. However, this fails, because when I type ```
bcdedit /export C:\BCD_Backup
```, it says```
The store export operation has failed.
The requested system device cannot be found.
```
- Used Boot-Repair, MBRWizard, EasyBCD, Easy Recovery Essentials for Windows (NeoSmart Technologies) -- but all of them return with no results at all, or inform me that the partition is corrupted and cannot be accessed. The partition is designated as *Unmountable Volume* in Easy Recovery Essentials. So no automatic repair tool appears to work.
- Used **diskpart** from the Command Line to make sure the correct partition is set to *Active*.
- Tried various other commands in diskpart (perhaps recklessly, but I think I have mainly been using descriptive commands and never actually succeeded with any operations) that I have found on websites and forums. I have managed to establish that the disk containing my Windows 7 installation is listed as *RAW*, and that no volume is associated with it.
- Attempted to reinstall Ubuntu from scratch, hoping that it might recognize that Win7 is also installed on the system, but it does not (so have cancelled the installation, because I really do not want to overwrite Win7).

**iv) WHERE I AM AT NOW**

I can switch on the computer, but after the BIOS flash screen, the boot sequence simply stops at a blank screen with a blinking white cursor in the upper left hand corner. I can override the boot sequence using F12, in order to boot from CD or USB. I am certain that the Windows drive is first in the boot sequence.
Basically, I have tried all the solutions I have found, and am amazed that none of them work for me. People appear to have had the exact same problem, and they have for the most part been able to solve it using the above solutions. Any help is much appreciated, because I appear to have drained my capabilities here.

If it's any help, here are two links to two instances of Boot-Repair. I am not sure what I might have done inbetween the two, but I suppose the latest (last) of the two is the one to look into:

[http://paste.ubuntu.com/21204137/](http://paste.ubuntu.com/21204137/)
[http://paste.ubuntu.com/21204720/](http://paste.ubuntu.com/21204720/)

Many thanks in advance,

---

### Post by oldfred on 2016-07-28
Moved to Windows sub-forum since Windows issues.
You may also do better in a Windows forum.

Have you tried chkdsk? And you cannot do that from Linux.
While partition table still shows NTFS for sda1, it cannot mount & see it which is more likely some sort of corruption.

Linux tools like Boot-Repair can only do minor and a few Windows repairs. Just about all Windows repairs need your Windows repair disk or third party Windows tools.

       [http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[URL="http://www.w7forums.com/startup-repair-t441.html"]http://www.w7forums.com/startup-repair-t441.html
[/URL]
 
Vista or 7 repair
Comments by others:
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx) 

[URL="http://www.w7forums.com/startup-repair-t441.html"]
[/URL]

---

### Post by a-loefgren on 2016-07-29
Many thanks for your help. I will consider Windows forums as well.

---

