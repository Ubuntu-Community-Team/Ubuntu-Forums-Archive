---
title: "I need some help with accessing windows and some other things"
date: 2007-07-12
forum: The Cafe
---

### Post by blakcode on 2007-07-12
Hello, I am using on a ASUS A7F laptop. I am using Ubuntu feisty. Anyway, I have been using it for a little while now and I need some help so I decided to post everything I need help with in this one post.

Firstly I need help with getting into my Windows Vista. Well I could do it at first with GRUB no problems but when messing around with resizing partitions (using paragon partition manager in windows) it messed something up. When I rebooted my computer (I was suspecting I might get an error 17) I got to the point of where the bootloader should be but instead nothing happened at all I just got a constant beep noise. So I loaded up my Ubuntu live CD and reinstalled GRUB :) it worked fine and I can get back into my Ubuntu partition fine. When I try to select my windows partition however the screen goes black and then my computer restarts. I think when I was messing with the partitions it might have either deleted something to do with my windows partition or maybe it changed that number (you know: hd0,x) Anyway I was hoping to get some help with this.  (and another thing, I have a button on the front of my computer for InstantFunPlus, anyway I could turn on my computer before and I would boot into vista and then  open media center straight up. I used to use this button whenever I accidentally deleted a bootloader. The button doesn't work now either :( thats why I suspect it might have something do with the windows startup files).

Secondly is a problem with getting the sound to work properly, when I first installed Ubuntu both the sound and display worked okay, but the resolution was off and the sound is flaky and doesn't have any bass sound. After trying a lot of things I finally got the display to display at my resolution (1440x900) and it turned out to be the simplest solution :) All I had to do was install the INTEL drivers. Well now that thats been done something weird happens when I watch videos or try to have those random effects going on my totem media player it automatically closes. Is there a way to fix this so I can watch videos and look at random effects? 

I still haven't managed to fix the sound either, do you guys know why I am not getting full sound. I think it might be because I am still using the default that came with Ubuntu and I haven't got any of my own sound drivers yet. I did have a look for sound drivers but I don't really know how to find them >.> (come on I need my music :guitar:)

Any help with these problems would be much appreciated :)

**-ßÎâ&#269;&#1220; &#986;&#1147;Ð&#441;**

---

### Post by Epilonsama on 2007-07-12
For your first problem, you should use a windows partitioner to modify your partition table cuz this leads to corruption, second I suggest reinstalling Vista but this may damage your ubuntu instalation.

---

### Post by blakcode on 2007-07-12
Do you know of a good program I could use to try to fix it with?

---

### Post by ajgreeny on 2007-07-12
Are you certain that your windows files and OS are still in place on the disk?  What is the output of sudo fdisk -l from ubuntu as this will help make sure that the partition naming is still OK for your grub menu.lst.  Also, can you mount your windows partition from ubuntu to make sure everything is still there as it should be?

---

### Post by blakcode on 2007-07-12
Yes I have looked at my vista disk through ubuntu and everything is there exactly as it used to be, I just can't boot into it. I typed that command you said and I got this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         638     5120634   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         638        8546    63521088    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            8546       10387    14790720   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4           10387       14594    33787128    f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5           10387       14594    33786810    7  HPFS/NTFS

```

I have linux booting from hd0,2 and it is trying to boot windows form hd0,1. lol so by the looks of this list it should be working. but when I try to boot windows I get a reboot :(

Anyway like I said before I have a button on my computer that used to work even if I didn't have  bootloader at all (I deleted it before lol). Now it doesn't work so I think something is wrong with my windows partition. But on the disk everything is the way it used to look. All my windows files and all.

---

### Post by amadeus266 on 2007-07-12
This may be incorrect since I haven't played with vista yet, but can you boot vista in safe mode? If so then try to turn off the automatic reboot, vista should either boot and attempt to correct the problem itself or at least give you some sort of error message to work with. Of course, if you can't get into safe mode then you may have a bigger problem. You may even try reinstalling Grub.

ANYONE feel free to correct me if am wrong.

EDIT: I would try booting to your vista install disk and see if you can repair the windows bootloader (worked for me in windows xp) and then try reinstalling grub after you get vista going again.

---

### Post by blakcode on 2007-07-12
:) I tried safe mode and no, it dosn't let me get that far -_-

For you edit: yea I would do that as I have done similar stuff on my friends desktop but atm I only have this laptop and the backup CD looks different and wants to reformat the windows volume so I don't really trust it.

Probably in the end I will end up using the backup CD and reinstalling Vista but I would like to try to be able to get it working first.

I was thinking of downloading an official vista DVD off a torrent to get the repair utility but it would take too long (a week or so).

Oh well..

---

