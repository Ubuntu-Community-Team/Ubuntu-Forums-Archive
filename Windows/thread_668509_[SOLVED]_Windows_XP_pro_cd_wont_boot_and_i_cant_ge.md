---
title: "[SOLVED] Windows XP pro cd wont boot and i cant get into bios"
date: 2008-01-15
forum: Windows
---

### Post by travismoore on 2008-01-15
I'm having yet more problems here, i was about to do a fresh windows install before I install ubuntu but not the xp disc does not want to boot and i cant get into my bios. Any ideas?


Thanks,

Travis

---

### Post by steve-shinn on 2008-01-15
Pressing F1 or delete (depending on mobo) when the pc fires up generally should get you into the bios.

---

### Post by Cypher on 2008-01-15
Installing Ubuntu wouldnt' have anything to do with your XP CD not working. Was the BIOS previously setup to boot from CD first? Why can't you get into the BIOS?

---

### Post by travismoore on 2008-01-15
Sorry should have mentioned this is unrelated to ubuntu its an XP problem i just tend to get the quickest replies on this forum. Im pretty sure the key for my mobo is delete and its what i have been using but now when I try it just hangs on a black screen.

Bios was set up to boot from cd but I've been swapping the IDE cables around recently and i thought maybe its not plugged in the way it was originally so i was trying to get into bios to change it to boot from the cd.

---

### Post by travismoore on 2008-01-15
Bump,

Help please?

my end goal is to dual boot linux and windows

---

### Post by cyberion on 2008-01-15
I have that on my laptop.

I installed Windows on my drive..  split up into 3 partitions.  Make sure that its all the way in the back too.

Linux(Ubuntu) should be at the front of the pack, so GRUB can load up and give you those pretty options.  Though for me its just text, but I'll hack the gui of GRUB (or ask about it later).

Make sure when you install Ubuntu that the installer is pointed to the front partition.  For me this allows me to use a working copy of Windows and working copy of Linux.. just need to reboot to switch.  

I was thinking that we have to install a FAT32 partition (like 5 GIG), but Ubuntu can read/write NTFS, I downloaded MADwifi to get my wireless card working, and didn't have the driver installed in windows, but download and just moved it from the mounted drive to another mounted drive.  

I think when we get acustomed to this, its just going to be installing a VMware client and using Windows off of Linux..  Anyhow, my first post and its already starting to be a novela.  I hope my experience with this helps, and I KNOW that I'll be soaking up alot very soon.

---

### Post by travismoore on 2008-01-15
yea i take it that its a bad thing my pc just started beeping?

that means a bios error or something dosn't it?

P.S to guy above: I cant install windows because it wont boot the CD.

---

### Post by travismoore on 2008-01-15
I think the only option i have is to clean up my current windows install and install ubuntu with it but my current windows install has been runnig for years and is quite/very bloated.

Unless i can format this hdd with ubuntu live cd and partition off the 40GB for windows and install it later.

---

### Post by Het Irv on 2008-01-15
If it is continually beeping then you have a problem with your RAM.  Check to make sure that it is seated correctly.  If there seems to be a pattern to the beeps check online for beep codes for you motherboard.  A single beep means that everything is good.

---

### Post by travismoore on 2008-01-15
Well i restarted to try count the beeps and I just got a single beep and all seems fine ..

---

### Post by ARhere on 2008-01-15
> **travismoore said:**
> Sorry should have mentioned this is unrelated to ubuntu its an XP problem i just tend to get the quickest replies on this forum....
hehehehehe.  you know what my answer is to _that_ one!  ;-)

> **travismoore said:**
> Bios was set up to boot from cd but I've been swapping the IDE cables around recently and i thought maybe its not plugged in the way it was originally so i was trying to get into bios to change it to boot from the cd.
You PC will beep if you memory is not installed properly, check to see if you bumped it.  More then likley, your HDD Master/Slave jumpers are not set properly.  If you are using IDE cable, remember that the last connector is the master position, and the middle connector is the Slave position.  The jumpers on your HDD and CD-ROM must match this or be set to 'cable detect'.

-AR

---

### Post by travismoore on 2008-01-15
Problem is I need to put a  fresh windows install on in order to dual boot with linux. Its a bit of a catch 22 situation really.

I will check my ram, hdd and cd drive now but im pretty sure that they are in correctly.

---

### Post by travismoore on 2008-01-15
Everything is in correctly it must be something I've messed up along the way..

Is there anyway to format this drive without using the windows CD?

Could I format my 80GB hard drive then put ubuntu and leave 40GB NTFS to put windows?

---

### Post by ARhere on 2008-01-15
Ok...back up a bit.

Are you wanting to do what I suggested in my last post to your dual boot question? [ ...about formatting your 500GB HDD and 80GB HDD?](http://ubuntuforums.org/showthread.php?t=667385&page=3)  Remember to mark the post as SOLVED please if you question was answered.

If so, you _really_ need to get into your BIOS.  That needs to be your #1 priority right now.  Did you try F10, F2, F1, & DEL keys?  Don't hit them like mad, just a few times the second you see your POST (Pre Operating System Test, *if it is a DELL or something like that, it is when the logo first appears.*)  This is important becasue your SATA cards BIOS could be interfering with your MB BIOS and this is important to fix first.

Did you already partition your 500GB drive and back up your data onto an NTFS partition?

-AR

---

### Post by ARhere on 2008-01-15
> **travismoore said:**
>  Could I format my 80GB hard drive then put ubuntu and leave 40GB NTFS to put windows?

No, you have to install Windows first.  *NOTE: you don't **have** to install Windows first, but not doing so will add more headache!*

---

### Post by travismoore on 2008-01-17
> **ARhere said:**
> Ok...back up a bit.

Are you wanting to do what I suggested in my last post to your dual boot question? [ ...about formatting your 500GB HDD and 80GB HDD?](http://ubuntuforums.org/showthread.php?t=667385&page=3)  Remember to mark the post as SOLVED please if you question was answered.

If so, you _really_ need to get into your BIOS.  That needs to be your #1 priority right now.  Did you try F10, F2, F1, & DEL keys?  Don't hit them like mad, just a few times the second you see your POST (Pre Operating System Test, *if it is a DELL or something like that, it is when the logo first appears.*)  This is important becasue your SATA cards BIOS could be interfering with your MB BIOS and this is important to fix first.

Did you already partition your 500GB drive and back up your data onto an NTFS partition?

-AR

Really i dont want to make it to confusing with to many partitions but i would do something similar. My bios is the DEL key because it was working fine with that the other day. 

My 500GB is just all of it NTFS at the momment. 

But things have got worse because i can't install windows or linux and iv already formatted the 80GB to NTFS. If i try get into bios i just get a black screen.

---

### Post by ARhere on 2008-01-17
> **travismoore said:**
> But things have got worse because i can't install windows or linux and iv already formatted the 80GB to NTFS. If i try get into bios i just get a black screen.

Alright.  Lets just focus on that first.  Unplug the SIL Labs card the SATA HDD is plugged in to, reboot and tell me if you can get into the BIOS.  If you can, then the BIOS on the SIL Labs card is conflicting with your MB bios.  Promise RAID cards have this problem as well.

-AR

---

### Post by travismoore on 2008-01-17
> **ARhere said:**
> Alright.  Lets just focus on that first.  Unplug the SIL Labs card the SATA HDD is plugged in to, reboot and tell me if you can get into the BIOS.  If you can, then the BIOS on the SIL Labs card is conflicting with your MB bios.  Promise RAID cards have this problem as well.

-AR

Unplugged the pci card but still no luck getting into bios unfortunatley.

---

### Post by lenswipe on 2008-01-17
try first turning the machine off

then physicaly disconnecting the hard drive(s)

then try and get into the BIOS/CD Drive

I had to do that as i had an old box with windows 98 and it wouldnt boot from the CD so i had to disconnect both the hard drives then it worked. :)

try that

---

### Post by ARhere on 2008-01-17
> **lenswipe said:**
> try first turning the machine off

then physicaly disconnecting the hard drive(s)

then try and get into the BIOS/CD Drive

I had to do that as i had an old box with windows 98 and it wouldnt boot from the CD so i had to disconnect both the hard drives then it worked. :)

try that

:lolflag:  I _hope_ he unplugged power before removing the SATA adapter card! hehe.

Ok, this sux, but next you need to unplug the 80GB (*all you hard drives*) then try getting into the BIOS.

-AR

---

### Post by travismoore on 2008-01-17
It didnt work =(

---

### Post by zipperback on 2008-01-17
> **travismoore said:**
> Well i restarted to try count the beeps and I just got a single beep and all seems fine ..


If you get your hardware situation figured out, the following link will help you get your dual boot setup.

[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)

- zipperback
:popcorn:

---

### Post by ARhere on 2008-01-17
> **travismoore said:**
> It didnt work =(

So all of your HDD are unplugged and when you hit 'DEL' key upon start, it tries to go into the BIOS but you just get a blank screen.

If you don't hit DEL, will the BIOS POST?  (This is where the BIOS tries to detect HDD and a boot partition)

If it  is just a blank screen, no POST, no nothing, then check the following.
1. Is your monitor plugged in?
2. Did you wiggle loose your video card?
3. Is you BIOS chip (if it is a DIP) not pushed in all the way?
4. When you push the power button, do the power supply fans go?
5. Did you accedently unplug the power connector on your MB?

-AR

---

### Post by Omnios on 2008-01-17
Has similar problem with my old P2 that did not like booting with the win CD. I used to use a win98 setup floppy with the dos stuff on it and use it to run setup on the cd.

---

### Post by travismoore on 2008-01-18
> **ARhere said:**
> So all of your HDD are unplugged and when you hit 'DEL' key upon start, it tries to go into the BIOS but you just get a blank screen.

If you don't hit DEL, will the BIOS POST?  (This is where the BIOS tries to detect HDD and a boot partition)

If it  is just a blank screen, no POST, no nothing, then check the following.
1. Is your monitor plugged in?
2. Did you wiggle loose your video card?
3. Is you BIOS chip (if it is a DIP) not pushed in all the way?
4. When you push the power button, do the power supply fans go?
5. Did you accedently unplug the power connector on your MB?

-AR

Well i do get the post its just after that it goes black pretty much no matter what i do.

4. Yea my fan goes.

I am at college now but i will try your suggestions when i get home.

Home now will have a go at your suggestions

---

### Post by travismoore on 2008-01-18
> **ARhere said:**
> So all of your HDD are unplugged and when you hit 'DEL' key upon start, it tries to go into the BIOS but you just get a blank screen.

If you don't hit DEL, will the BIOS POST?  (This is where the BIOS tries to detect HDD and a boot partition)

If it  is just a blank screen, no POST, no nothing, then check the following.
1. Is your monitor plugged in?
2. Did you wiggle loose your video card?
3. Is you BIOS chip (if it is a DIP) not pushed in all the way?
4. When you push the power button, do the power supply fans go?
5. Did you accedently unplug the power connector on your MB?

-AR

1. yep monitor is plugged in because i get the post
2. just cehcked card and it seems intact although it has been being weird on some games recently which used to run fine.
3. not quite sure what you mean
4. fans working.
5. well i get post so there must be power.

---

### Post by ARhere on 2008-01-18
Sorry to say this, but you need to recruit the help of someone that can look at your machine.  There is only so much I can do not being able to see the machine and diagnose it.

Maybe you can bribe a computer geek at school to look at it?

-AR

---

### Post by travismoore on 2008-01-18
Unfortuneatly all the people in my class at school are wannabe geeks and suck. 

But i might be able to get my brothers freind to look at it he knows loads of stuff.

---

