---
title: "Is it possible to boot from a SATA hdd and have an IDE Storage hdd?"
date: 2006-12-13
forum: The Cafe
---

### Post by v8YKxgHe on 2006-12-13
Hey,

Ok so I've finally got Ubuntu Edgy installed on my SATA Hard drive and it works perfectly (love what ever you guys did to the fonts, they look amazing!).

I also have an IDE Hard drive, that is formated to FAT32 (So I can easily transfer files between Windows and Linux). Here is my hard drive setup:

1x SATA Hard drive with Ubuntu installed
1x SATA Hard drive with Windows installed, but disconnected
1x IDE Hard drive, Master
1x DVD-RW, Slave to the IDE Hard drive

Now, Ubuntu will boot perfectly with the IDE Hard drive disconnected. But as soon as I connect the IDE Hard drive I can not boot into Ubuntu, it gets to the Ubuntu splash screen and just locks up. My SATA Hard drive gets no activity, yet my IDE Hard drive does - after about 10-20 seconds my CD Drive makes a noise like an old floppy drive (that horrible clicky, churning noise)!

So I'm starting to wonder, is it possible to do what I want? Have 1x SATA Hard drive with Ubuntu installed, then a spare IDE Hard drive in FAT32? I really need this setup so I can share files between Windows and Linux easily.

---

### Post by mips on 2006-12-13
I had a similair problem. Go into your bios and set the HD boot order. I must admit though that when i tried to install edgy withe the pata drive connected i had no luck, I had to disconnect it and it is still disconnected.

Otherwise it worked fine, I installed bsd on the pata drive and kubuntu dapper booted fine with the drive attached.

---

### Post by v8YKxgHe on 2006-12-14
> I must admit though that when i tried to install edgy withe the pata drive connected i had no luck, I had to disconnect it and it is still disconnected.

Yep, so did I! The liveCD wont boot at all with the IDE Hard drive connected.

How do I actually set the boot order? All I can do is:

First Boot: Hard Drive
Second Boot: CD-Drive

I can't actually say:

First Boot: SATA 120gb hard drive 
Second Boot: IDE 80GB hard drive

How else do I do it? Motherboard is Abit AW9D

Edit: Also, will the IDE Hard drive have to be set to Slave and the CD Drive set to Master?

---

### Post by Malta paul on 2006-12-14
Yes it is possible to boot from your SATA HD and also use your ATA HD.
I am using the same type of setup! But I did have to experiment with my BIOS setting to get it to work.
I changed the 'Intergrated Settings' and the HD boot order, then rebooted back into the BIOS until the Master and second master setting were correct. It took a few tries to get the HD's and the DVD/CD's in their correct order. Hope this is of some help to you  :)

---

### Post by v8YKxgHe on 2006-12-14
Malta paul, would you mind posting some BIOS options that you changed and their values please? I'm confused about the SATA settings, I have modes like Enhanced, SATA Only, Optimized etc .... ti's all confusing! I'm gonna go play around with it now, the IDE Hard drive should be set to master ( on the jumper settings ) yeah?

---

### Post by v8YKxgHe on 2006-12-14
yay!!

I don't know what I did but it's working fine now! 

IDE Hard drive is set to Master,
Set to boot from SATA Hard drive first, then IDE Hard drive
disable IDE Controller bus, I think.

All works! Thanks for your help guys.

---

### Post by Malta paul on 2006-12-14
Hi AlexC, The actual settings will depend on the type of BIOS you have on your motherboard.
I built my computer and use a AMIBIOS, but they all follow the same principal.

Standard CMOS Features are:
Primary IDE master   - set to the HD that has the maser boot record (MBR) I also duel boot using Grub.
Primary Slave           - Not installed.
Secondary master     - set to my DVD
Secondary slave        - set to my other DVD
Third IDE master      - set to my second HD

Advance BIOS Features are:
Boot device selected   - set to the HD that contains the MBR.

Integrated Peripherals are:
Native mode                   - Note Legacy mode my be required, but Native is preferred. 
ATA configuration           - S-ATA only
P-ATA Keep Enabled        - YES 
P-ATA Channel Selection  - BOTH
S-ATA Ports Definition     - P0 - 2nd, /P1 - 1st.

You will have to reboot a few time to check that the 'Standard CMOS Features' are correctly set to give the 'primary IDE Master'  as the HD with which contains the MBR.

When this is configured OK then boot into Ubuntu and Mount your second Drive.

Have fun ;)

---

### Post by Malta paul on 2006-12-14
Hay great news! good luck :D

---

