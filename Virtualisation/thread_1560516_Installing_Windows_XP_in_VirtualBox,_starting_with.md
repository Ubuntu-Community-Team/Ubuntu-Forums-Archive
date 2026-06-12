---
title: "Installing Windows XP in VirtualBox, starting with non-bootable disc"
date: 2010-08-24
forum: Virtualisation
---

### Post by raequin on 2010-08-24
Greetings.  Years ago I downloaded a copy of XP Pro through an educational offer (Ecademy) and have used it several times to install that OS.  It is not bootable, so when I would do so I'd have to use a floppy disc and enable CD-ROM support or something and then delve into the I386 folder and blah, blah.  I guess that's all because the disc is not bootable.  So, now I'd like to setup a virtual machine using VirtualBox and I'm wondering how to get an ISO from this disc or if there's some other way to use it to install XP on the virtual hard drive image.

Here's what's on the cd, that is, what files I have to work with.  Thanks.

Directories:

DOCS
I386
SUPPORT
VALUEADD

Files:

AUTORUN.INF
README.HTM
SETUP.EXE
WIN51
WIN51IP

---

### Post by mikewhatever on 2010-08-25
Any cd burning program has a cd to iso option, and if you need to change files inside an iso, use isomaster program from the repositories.

---

### Post by howefield on 2010-08-25
> **raequin said:**
> I'm wondering how to get an ISO from this disc.

If you're using Nautilus and have the CD in your drive, go to Places > Computer and then right click on the mounted CD-ROM, select "Copy Disc...".

Choose Image File as the "Select a disc to write to" option (you may need to go into properties and select ISO9660 image as the Disc image type).

---

### Post by varunendra on 2010-08-25
Simply make a bootable iso from your CD following any of these:-

[Using Nero]("http://www.onecomputerguy.com/install/winxp_bootable.htm")
[Using mkisofs]("http://hints.macworld.com/article.php?story=20080416134218704&utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%253A+macosxhints%252Frecent+%28Mac+OS+X+Hints%29") (guide for mac, should be same for linux)
You may wish to try [this]("http://ubuntuforums.org/showthread.php?t=1450722&page=2").

The common & imp. thing is that

[LIST=1]
[*]the no. of loaded sector has to be 4,
[*]Joliet - long filename has to be enabled &
[*]the XP bootsector file has to be downloaded.
[/LIST]
Best of luck.

(And by the way, I think it is a Windows support question, so this may not be the right place for it :))

---

### Post by raequin on 2010-08-25
Thanks.  I wonder if the iso is going to be bootable.  Will it be since the CD from which it's made is not bootable?

---

### Post by raequin on 2010-08-25
Well, I made an iso of the directory containing all the stuff I downloaded from Microsoft.  My current problem is that I do not know how to try and use it to install a guest OS on VirtualBox since it's not the first time I'm running this VM.  Therefore the "First Start Wizard" does not come to help me select the medium to install.  Can someone please direct me as to how to get the VM to boot from this iso?

---

### Post by varunendra on 2010-08-25
Select your VM in the VMs list.
In the right hand side pane, you should see list of its (virtual) hardware, select storage (click on it).

Then in the 'now shown list' of drives, click on cd drive icon (single disk icon). Against CD/DVD device field, there's a folder icon. Click on it.

In the now-opened field, click on 'Add'. It will open a browser to choose an iso image. Simply browse and choose your XP iso.


If you followed my previous links to create the iso, it will be bootable.

---

### Post by raequin on 2010-08-25
Okay well I figured out how to select the iso for boot, at least I think I did.

When the VM starts press F12 to select boot device.  Then go to Devices --> CD/DVD Devices, and select the iso file.

Then press "c" for other boot devices, CD-ROM.

I get "Fatal: could not read from the boot medium".

I guess this means the iso I made is not bootable.  I guess I will try the Windows support forum as that might be a more appropriate place for this installation question.  Thanks.  I'll still welcome comments though.

---

### Post by raequin on 2010-08-25
> **varunendra said:**
> Select your VM in the VMs list.
In the right hand side pane, you should see list of its (virtual) hardware, select storage (click on it).

Then in the 'now shown list' of drives, click on cd drive icon (single disk icon). Against CD/DVD device field, there's a folder icon. Click on it.

In the now-opened field, click on 'Add'. It will open a browser to choose an iso image. Simply browse and choose your XP iso.


If you followed my previous links to create the iso, it will be bootable.

Just read your instructions after I wrote the last reply.  It seems the method I detailed worked because I see the iso in the CD field.

You generously supplied three links for making the bootable iso.  I had problems will all of them.

The first link is for Nero, paid software.

The second link describes a process that requires "boot.img" from the original XP disc.  I do not have that file, as I believe it's not on my original disc.

The third link went no where but the forums, as far as I could tell.

Thanks again.  Still looking for how to make this XP disc bootable.

---

### Post by varunendra on 2010-08-25
In the first link, the linked page contains another link on top of the page that will download the bootsector file that you need (that bootsector is the only thing you need to make your cd bootable. Rest are the contents you already have)

You can also google for "XP CD boot-sector file" & will get plenty of links (including Microsoft's) to download it.

Also, I think trial version of nero(linux) would allow to use an 'image drive' that can burn to an image file (.nrg). You can then use any free cd-burning tool that can burn .nrg images.

However, trying the mkisofs command is really easier & I've tried it successfully (well.... see my third link ;))



**_PS_:** 
I guess there is a native command in Lucid '**genisoimage**' that works exactly as mkisofs. Perhaps it is a new version of it!

**_PPS_:** Oops! I just realized the error in my third link! Corrected.

---

### Post by raequin on 2010-08-25
Allright, it worked.  Instead of boot.img as shown in the "mkisofs" link you supplied, I downloaded "Microsoft Corporation.img" and changed the command from the page you linked to match.  I copied that into the same directory as all the other files and directories I posted in the first entry.  mkisofs created the iso with no problem and now XP is installing on my VM.  Stinkin' cool!  Thanks.

---

### Post by varunendra on 2010-08-25
Glad it helped :).

I think you should mark this thread as [solved] now.


**_EDIT_:** Oh.... one more thing..
You can use this method to create a customized CD. One that contains extra stuff to fill up the rest of the space in the CD.

---

