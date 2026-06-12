---
title: "Anybody ever got 1Click DVD Copy working under Wine?"
date: 2010-05-04
forum: Wine
---

### Post by inameiname on 2010-05-04
I've been using Linux (Ubuntu) for a while now, and the only thing I really miss is the ease of 1Click DVD Copy to copy/backup DVDs. Unfortunately, no matter how much I try to figure it out, it just won't work. 

It will install, but the issue seems to be that it won't detect the DVD drive.

So I'm curious if anybody has gotten it to work, or perhaps knows of a way to get programs to detect the drive.

---

### Post by anaconda on 2010-05-04
Why do you want to use wine for that?

I am perfectly happy using k9copy, and its wizard for copying DVD:s. 
Yeah. It isn't one-click, but most of us do want to choose some options. ..

---

### Post by cogadh on 2010-05-04
It might help if you provided a bit more detail, like the terminal error output from Wine. If I had to guess, the detection issue is caused by the fact that Ubuntu no longer relies on an fstab entry to define CD/DVD drives and simply allows them to dynamically mount based on the volume label. This causes a lot of problems with Wine, since it usually likes to have all drives it is going to use clearly defined in advance. The terminal output from Wine might be able to confirm that.

---

### Post by inameiname on 2010-05-04
To Anaconda, actually I currently use DVDFab, through Wine, which works just fine, removes all encryption, and basically does everything 1Click would do, just not as good. It's one of only two apps for Windows I have on my computer (other being ConvertXtoDVD). However, while it's ok, it's not as easy, requires a little more, and every once in a while an update just doesn't copy a DVD the same.

And actually, I do have k9copy installed, and do use it if DVDFab has an issue. However, only as a last resort, because if you do not know, k9copy doesn't remove ALL encryption. It removes some, but because it doesn't remove it all, you sometimes can't just copy the DVDR and play it on ALL DVD players. I've done enough research for that. However, it is an excellent program, and I sometimes use k9copy first, and then have DVDFab make an exact copy, which all that does is remove whatever encryption k9copy doesn't remove the first time, leaving the video untouched.

To Cogadh, actually 1Click installs just fine, and seemingly would work just fine. However, when you open it, you either (depending on if you have it set to 'WinXP' or 'WinVista' or 'Win7') get it to open just fine, but there is no DVD drive detected, and you simply cannot enter the directory for it and have it accept it, or it opens for half a second and then closes, saying there is no DVD drive and that's that. Actually my other Windows app, ConvertXtoDVD, while lets me make an ISO just fine, it gives me the same exact error, saying it cannot find a DVD drive to use. 

I was not aware of Ubuntu no longer using fstab entries for the drives; I can see how that would cause issues. Is there any way to change that, or trick it or whatnot to get my desired result? Oh, and how do I give the terminal output from Wine? If you mean opening the folder of the exe file, and inserting './1ClickDvdCopyPro.exe' and hit 'enter', then this is what results:

fixme:reg:GetNativeSystemInfo (0x5fdf74) using GetSystemInfo()
err:ole:CoGetClassObject class {1643e180-90f5-11ce-97d5-00aa0055595a} not registered
err:ole:CoGetClassObject class {1643e180-90f5-11ce-97d5-00aa0055595a} not registered
err:ole:CoGetClassObject no class object {1643e180-90f5-11ce-97d5-00aa0055595a} could be created for context 0x3
fixme:quartz:AMGetErrorTextA (80040154,0x32f71c,255) stub

---

### Post by cogadh on 2010-05-04
You could try [creating a default fstab entry]("http://www.tuxfiles.org/linuxhelp/fstab.html") for your DVD drive, then run winecfg to set up the drive in Wine. I've had some success with getting that to fix drive detection issues in Wine.

---

### Post by inameiname on 2010-05-04
Hmmmm, I'll try that, thanks. Not sure how, but of course I'll read that link you gave and see what happens. My current 'fstab' is the following:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e4d262e1-9d1d-4237-b2fc-f6b1992731ca /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b91c8870-8380-48c5-9fe9-dc1affb5e822 none            swap    sw              0       0

.....and if I insert a DVD into my laptop, [FONT=monospace]here is m[FONT=Verdana]y 'sudo lshw -C disk:

[/FONT][/FONT][FONT=monospace]*-cdrom                 
       description: DVD-RAM writer
       product: DVDRAM GSA-T20F
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: EG02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
[/FONT]
[FONT=monospace][FONT=Verdana] 
Guess now all I need is to find the correct fstab entry. 

I did find this entry that I'm hopeful will help: [http://ubuntuforums.org/showthread.php?p=9224205](http://ubuntuforums.org/showthread.php?p=9224205)
[/FONT][/FONT]

---

### Post by Animal X on 2010-05-04
> **inameiname said:**
> To Anaconda, actually I currently use DVDFab, through Wine, which works just fine, removes all encryption, and basically does everything 1Click would do, just not as good. It's one of only two apps for Windows I have on my computer (other being ConvertXtoDVD). However, while it's ok, it's not as easy, requires a little more, and every once in a while an update just doesn't copy a DVD the same.

And actually, I do have k9copy installed, and do use it if DVDFab has an issue. However, only as a last resort, because if you do not know, k9copy doesn't remove ALL encryption. It removes some, but because it doesn't remove it all, you sometimes can't just copy the DVDR and play it on ALL DVD players. I've done enough research for that. However, it is an excellent program, and I sometimes use k9copy first, and then have DVDFab make an exact copy, which all that does is remove whatever encryption k9copy doesn't remove the first time, leaving the video untouched.

To Cogadh, actually 1Click installs just fine, and seemingly would work just fine. However, when you open it, you either (depending on if you have it set to 'WinXP' or 'WinVista' or 'Win7') get it to open just fine, but there is no DVD drive detected, and you simply cannot enter the directory for it and have it accept it, or it opens for half a second and then closes, saying there is no DVD drive and that's that. Actually my other Windows app, ConvertXtoDVD, while lets me make an ISO just fine, it gives me the same exact error, saying it cannot find a DVD drive to use. 

I was not aware of Ubuntu no longer using fstab entries for the drives; I can see how that would cause issues. Is there any way to change that, or trick it or whatnot to get my desired result? Oh, and how do I give the terminal output from Wine? If you mean opening the folder of the exe file, and inserting './1ClickDvdCopyPro.exe' and hit 'enter', then this is what results:

fixme:reg:GetNativeSystemInfo (0x5fdf74) using GetSystemInfo()
err:ole:CoGetClassObject class {1643e180-90f5-11ce-97d5-00aa0055595a} not registered
err:ole:CoGetClassObject class {1643e180-90f5-11ce-97d5-00aa0055595a} not registered
err:ole:CoGetClassObject no class object {1643e180-90f5-11ce-97d5-00aa0055595a} could be created for context 0x3
fixme:quartz:AMGetErrorTextA (80040154,0x32f71c,255) stub







well said, I myself am using DVD Decryptor, and have noticed the same issues, in wine i can see my c: drive, but no other drives, and i need a drive to show up here so i can select it.

---

### Post by Animal X on 2010-05-04
> **inameiname said:**
> I've been using Linux (Ubuntu) for a while now, and the only thing I really miss is the ease of 1Click DVD Copy to copy/backup DVDs. Unfortunately, no matter how much I try to figure it out, it just won't work. 

It will install, but the issue seems to be that it won't detect the DVD drive.

So I'm curious if anybody has gotten it to work, or perhaps knows of a way to get programs to detect the drive.
sad to say i am still quiet Noobish, i just figured out how to add my DVD drive to wine:

Applications>Wine>Configure Wine  , click on drives then auto detect then ok.

Edit: nope, that still didn't get it.


Edit2:funny, here's what did work- for DVD Decryptor anyway, in its Tools>Settings after click on I/O i selected WNASPI32.DLL as opposed  to ASPI.DLL and now it seems to be working without any changes to how the drive is mounted in my filesystem. We'll see if it successfully copies the DVD.

---

### Post by inameiname on 2010-05-05
Doh! I wish I had the I/O setting in 1Click. Or even ConvertXtoDVD.


Sadly I couldn't figure out the correct fstab; nothing seems to work. Ah well.

---

