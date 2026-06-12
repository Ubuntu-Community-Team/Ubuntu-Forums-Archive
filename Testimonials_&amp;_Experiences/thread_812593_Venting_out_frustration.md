---
title: "Venting out frustration"
date: 2008-05-30
forum: Testimonials &amp; Experiences
---

### Post by futureal2032 on 2008-05-30
I think after tinkering with my USB Pen Drive and trying to give it  "Write" permissions... and toying with various commands and sudo..i found out one thing.. well 2 things actually..

**1.** i posted a thread on my problem to give write permissions so i can delete some files on my pen drive. Then i searched the forums for previous solutions.

i tried everything... and although i still have not been able to delete anything from my pen drive.. because the permission settings  still remain "Read Only". (yeah i tried every solution from chown to chmod to pmount etc.) But hey i got a result.
Result is..now my pen drive does not even get mounted as read only.
When i isert it..it gives me "Unable to Mount" Invalid arguement in Mount Point error. It only shows "Kingston Data Traveller Mini" in the FIle Browser under "media" and no matter what id o it does not get mounted.

And by the way Mounting USB drives does not have anything to do with "/etc/fstab" file. Because my "fstab" has remained the same as it was throughout my tries of solving this issue.
SO i guess the mount options for USB are stored in some other files..which i don't know and don't think i will ever know.

**2.** One thing i found out is the "SUDO" is so secure that it does not let me do a simple task like deleting the files on a pen drive. Its like being stuck in your own house because your own bodyguards kept for your own security won't let you out even for a walk in your own garden. 

AND THATS VERY FRUSTRATING.

Thank god i had a dual boot with Windows XP..i deleted my files from my pen drive. At least i know what problems i am going to face in XP and the workaround is easy. 

Hey and i though USB pen drives are so common these days that they would be the most easiest to use on any OS.

Bye Bye UBuntu as fas as using Pen Drives is concerned.:popcorn:

---

### Post by Sef on 2008-05-30
> One thing i found out is the "SUDO" is so secure that it does not let me do a simple task like deleting the files on a pen drive. Its like being stuck in your own house because your own bodyguards kept for your own security won't let you out even for a walk in your own garden.

Something was not done right.  [It is possible]("http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/").

---

### Post by armandh on 2008-05-30
time for a reload

the advantage to linux is you can change anything
the disadvantage is you can wreck everything.
with my skill level I avoid the terminal.

conflicting code???

---

### Post by ukripper on 2008-05-30
If you have formated your USB drive with NTFS partition then it will be in READ ONLY mode until you install and use ntfs-3g (ntfs-config) it is in repos, you can install via add/remove or synaptics or good old terminal) to make your NTFS partition  writable.

But I guess now you have already deleted your files you won't be needing it until next time you want to delete using ubuntu.

---

### Post by freebeer on 2008-05-30
I have 3 different USB pen drives from 3 different manufacturers.  They all work in all the various versions of Ubuntu that I've tried them in.  (6.04, 7.10, 8.04)  In all cases I was able to read and write to the drives.  They were formatted FAT 32, though, so that may be a difference.

---

### Post by ukripper on 2008-05-30
> **freebeer said:**
> I have 3 different USB pen drives from 3 different manufacturers.  They all work in all the various versions of Ubuntu that I've tried them in.  (6.04, 7.10, 8.04)  In all cases I was able to read and write to the drives.  They were formatted FAT 32, though, so that may be a difference.

Yes, NTFS works pretty different to FAT 32 and ntfs-3g is reverse engineered NTFS to work with linux. By default NTFS partions are read only in Ubuntu. To make it writable you need to have ntfs-config tool.

---

### Post by webcoded612 on 2008-05-30
> **armandh said:**
> time for a reload

the advantage to linux is you can change anything
the disadvantage is you can wreck everything.
with my skill level I avoid the terminal.

conflicting code???

Haha yeah I had this problem last night.  Tried to install the ATI drivers from ATI.com...rebooted and got a white screen with my mouse pointer.  No icons, nothing was clickable...ctrl+alt+f2 crashed xorg altogether.  

It is a disadvantage.  Windows is kind of idiot proof, which is nice, but honestly now that HH is out and Linux is much closer to "just working" (not quite there yet...but almost), Linux for the first time is the superior system as far as usability and intuitiveness goes.  

As for last night...I had to wipe the drive and reinstall.  Which was OK, because that's how I learned Windows.  I didn't sit down at Win 3.1 and go "OK, let's learn!".  I played with it, broke it, fixed it, and played with it some more.  

Same with Linux.  I don't mind Linux crashes when they're my fault.  They're learning experiences, and I think the OP might benefit from looking at his USB problem philosophically.  These issues might seem like problems now, but once you fix them (and you will, eventually) you can sit back and say a) you learned something new and b) you are now able to help others who have that issue.

It's all perspective.  :))  Good luck with the pen drive stuff.  :)

---

### Post by stchman on 2008-05-30
I have numerous USB flash drives and they all work perfectly under Linux.  I recommend you format them in FAT32 as that will be the most compatible with any OS.

---

### Post by azimuth on 2008-05-30
I have found that with my Datatraveler pen drives, if I hibernate XP without unmounting the usb mass storage, they will be unavailable in Ubuntu. It may just be my unique setup, but that is how they work for me. I assume it has an attribute bit set until they are properly unmounted. I have also found that a user change in Ubuntu, leaves them read-only for a new user. Whoever mounts them, owns the rights to write to them.

---

### Post by futureal2032 on 2008-05-30
> **ukripper said:**
> Yes, NTFS works pretty different to FAT 32 and ntfs-3g is reverse engineered NTFS to work with linux. By default NTFS partions are read only in Ubuntu. To make it writable you need to have ntfs-config tool.

Thanks..and thank you for all your replies.. I love ubuntu.. no two ways about it..and one thing i love is i get to learn so much while trying to configure things my way.

by the way i Have 3 Hard drives.. and 6 partitions formatted to NTFS..but i never get any problem writing to them... i mean i did not need any config changes or never used any commands..the partitions got automounted when i added the new hard drives. 
all i have to do is type my password..when i try to write for the first time after i boot..thats all...

so its bugging me why i can not use my USB pen drive.

---

### Post by starcannon on 2008-05-30
Did you try using gparted?
If not then:
```
sudo apt-get install gparted
```

I've had a couple usb flash drives give me hell and gparted has sorted every one of the lil' buggers out.

GL and hang in there.

BTW I've had no issues at all with PNY usb sticks if thats of any use to you for future purchases, sandisk sux, they put software on there that is a pita to get off.

---

### Post by mivo on 2008-05-31
I actually experienced a similar problem with a MicroSD card with an USB adapter in Gutsy a few months ago. From one use to the next, it became read only, and I had done nothing except sticking it in like I had many times before. I still don't know what caused it. It worked fine in Arch Linux on my other box, but it would no longer work in Gutsy. I formatted it (other computer) with Gparted after backing up the data, and the problems were gone. I never had the same trouble with any other card or stick, though. Just this one, and it came and went without obvious explanation.

---

### Post by SneakyWho_am_i on 2008-06-01
Yeah, I have a couple of MicroSD things that i use in Ubuntu and I must say that they work properly every time. I formatted them using my cell phone, I don't even know what filesystem it is.

Good luck, futureal2032. I guess the Ubuntu-usb-drive-gods are simply not smiling upon you. Linux had nothing on Windows in terms of usability ten years ago as far as I'm concerned, and now it beats it hands down *once you get the hang of it* (then again, try sitting a very-first-time-ever complete newbie in front of a computer and say "write me a letter" in Windows. See what happens....). In ten years, it will be so automatic, Ubuntu Zebra will just smell the pen drive in your pocket, as you if you're pleased to see it, and automatically delete the files when you nod and wink at it.
Then it will fetch you coffee (and a news paper) and rub your feet.

If it helps, I have had to use a Vista computer for work.. Every CD ROM I put in, it insists that I have to format it before I can browse it. The end result being, I can't load CD ROMs in Vista on that computer at this moment.

---

