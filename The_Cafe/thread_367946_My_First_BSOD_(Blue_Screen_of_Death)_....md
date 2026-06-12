---
title: "My First BSOD (Blue Screen of Death) ..."
date: 2007-02-22
forum: The Cafe
---

### Post by user1397 on 2007-02-22
Yep, today I officially got my first BSOD on my windows desktop, and I've been using it since 2004.

The main error says "Unmountable boot volume" but I can't think of anything I've added (software or hardware) that might have caused this, unless my hard drive completely doesn't work anymore.

The funny thing about it is the post I made on this thread yesterday: [http://ubuntuforums.org/showthread.php?p=2192053#post2192053](http://ubuntuforums.org/showthread.php?p=2192053#post2192053), post #345

---

### Post by Rhapsody on 2007-02-22
I've seen loads of BSODs on my old PC with Windows XP. The only time I managed to get a kernel panic out of Linux though was when attempting to boot the PC after it'd been dropped about three feet (it seems the motherboard bought the farm, along with one or both hard drives).

---

### Post by SunnyRabbiera on 2007-02-22
Its funny though, I only encountered the blue screen of death on XP only twice, once on a computer I owned and one on someone elses computer.
But on my aunts ME computer, BSOD was all over the place.

---

### Post by Polygon on 2007-02-22
all the stuff on your hard drive is most likely fine, its just that windows in its infinite wisdom most likely screwed something up and is unable to mount it

use your favorite flavor of linux cd, (the ubuntu linux cd can read from ntfs drives by default) so if you need to get important stuff off of their, simply pop it in, mount your windows drive and copy it somewhere else (another drive, not your desktop as thats just all RAM =P )

---

### Post by ice60 on 2007-02-22
you can have a look at the minidump if you have it configured to make one, or look at the Event Viewer logs too to see what might have caused the BSOD.

edit. if you can't bootup you can try using the recovery console, or knoppix to have a look at the boot.ini, if that's become corrupt it will not know which drive to boot from.

---

### Post by user1397 on 2007-02-22
do you mean the console from the recovery cd's?

i successfully mounted it using a feisty live cd, so i dont have to worry about important files (they're all still there)

here's my boot.ini file:

```

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
```

---

### Post by IYY on 2007-02-22
I have a machine that gives this error every time you try to dual boot Ubuntu and Windows on the same disk. The only way to fix it (as far as I know) is to erase Ubuntu and use XP's recovery console to 'fix' (convert to Windows's boot manager) the mbr, using the fixmbr command. The interesting thing is that even if I fix the mbr but leave Ubuntu there, Windows gives this nasty error and BSOD.

---

### Post by Nikron on 2007-02-22
I've never gotten a BSOD...  But then again I've only used Windows XP and a little ME...  Now I don't use Windows at all, so I might of missed the whole experience..

---

### Post by user1397 on 2007-02-22
the thing is, I don't even have ubuntu installed on this computer

its just my ntfs partition (windows xp)  and then my recovery partition (fat32)

---

### Post by riven0 on 2007-02-22
You didn't happen to pull out a usb drive while shutting down the comp, did you? That'll give a BSOD. 

And I still can't believe there are people have been using XP for years and haven't gotten the BSOD. It was a common occurence with me, (weekly, at least). It's also one of the reasons why I switched to Linux.

---

### Post by user1397 on 2007-02-22
> **riven0 said:**
> You didn't happen to pull out a usb drive while shutting down the comp, did you? That'll give a BSOD. 

And I still can't believe there are people have been using XP for years and haven't gotten the BSOD. It was a common occurence with me, (weekly, at least). It's also one of the reasons why I switched to Linux.nope, that did not happen.

---

### Post by Polygon on 2007-02-22
im thinking that the only way to fix this problem would to be to reinstall windows....usually when you get a problem like this its one of the core windows dll files that got corrupted or something

---

### Post by Kateikyoushi on 2007-02-22
Our desktop is a Viao LCD pc it is more than 5 years old but because of the beautiful 17" widescreen we still keep it runs the first installation and doesn't it do BSOD.
The record is still kept my girlfriend's father's Win 98 which runs for 8 years during that period he collected 2 viruses.

---

### Post by user1397 on 2007-02-22
well i found out that this is my exact error message: [http://support.microsoft.com/kb/297185](http://support.microsoft.com/kb/297185)

and i have already scratched out filesystem damage as a possibility (because the exact error message doesn't match)

so it has to be the other solution.  but i don't really understand it

---

### Post by Quillz on 2007-02-22
I've never gotten a BSOD in my life, and I've been using Windows since it was just a shell for MS-DOS. But then again, I'm quite computer literate.

---

### Post by ice60 on 2007-02-22
> **ubuntuman001 said:**
> do you mean the console from the recovery cd's?

i successfully mounted it using a feisty live cd, so i dont have to worry about important files (they're all still there)

here's my boot.ini file:

```

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
```

it depends how many drives and partitions you have. it's like grub i suppose if the numbers are wrong it will go looking on the wrong drive/partition when it tries to bootup. i'd have to look up what applies to what, i haven't used windows for a few years now.

---

### Post by ice60 on 2007-02-22
> **ubuntuman001 said:**
> do you mean the console from the recovery cd's?

i successfully mounted it using a feisty live cd, so i dont have to worry about important files (they're all still there)

here's my boot.ini file:

```

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
```

i haven't looked this up, but IF YOU CAN EDIT THE BOOT.INI then try changing the first 2 to a 1. i think as it is it might be trying to boot from a second HDD.

only do that if you are confident you can change it back if i am wrong. and if you are more sensible than me maybe look that up first. good luck.

---

### Post by 3rdalbum on 2007-02-23
I've been using Windows XP (not very much) since May, and I got my first BSOD a couple of days ago because of a bug in my video card drivers.

---

### Post by mcduck on 2007-02-23
> **SunnyRabbiera said:**
> Its funny though, I only encountered the blue screen of death on XP only twice, once on a computer I owned and one on someone elses computer.
But on my aunts ME computer, BSOD was all over the place.

In XP Microsoft changed the use of BSOD, when in older windows it was used as rather basic error message (and you often could just alt-tab back to desktop like nothing had happened) XP only uses it for serious errors and instead pops up small message windows for smaller errors. This has made the BSOD much less common in Windows XP than it was on any older version.

If you have never used any other Windows than XP, you really have no idea why people are telling so much jokes about BSOD ;)

---

### Post by user1397 on 2007-02-24
WOW, so check out the conclusion to my story:

So I decide to contact an HP specialist via live chat, (they're pretty nice about everything), but they cannot seem to understand that my recovery disc will not detect my hard drive.  so, when I'm on my fourth specialist, i finally get that message through to him, and he basically tells me that I have to do a hard recovery, i.e. reformat my hard drive and lose all my data.  good thing i had my most important data backed up on another computer.

so i decide, "well, if i try to install ubuntu on it, and it works, then it is not a hardware failure, but a windows failure, which would be a good thing because then i have reason to hate windows more than ever before."

so thats exactly what i did, i installed feisty herd 4, and now I'm enjoying all its benefits.

---

### Post by PatrickMay16 on 2007-02-24
Unmountable boot volume. This one happened to a few computors running Windows 2000, that I have seen in my life time. The funny thing was, after turning off, then on again, it would work fine once more.

Heh heh heh heh heh. I'll mount your boot volume any day. Heheheheheheheheh.

---

### Post by user1397 on 2007-02-24
And my story continues...

after i installed feisty (full install, erased my whole hard drive for ubuntu), i tried the HP recovery discs again, and they work now for some reason.

so i guess im going back to windows...not that I don't want to, but...

---

### Post by TravisNewman on 2007-02-24
SOmething that nobody told you apparently....

I've seen this error a few times, and booting off of the Windows CD (not the recovery cd) and going to the recovery console and running chkdsk worked every time.

---

### Post by fakie_flip on 2007-04-22
I installed Windows, and it worked. Then I installed Ubuntu to have a dual boot. Then I tried to reboot and go back to Windows. It loaded some, and then gave me the BSOD. Ubuntu has corrupted Windows, and now I can't have a dual boot. How can I have a dual boot without getting the BSOD?

---

