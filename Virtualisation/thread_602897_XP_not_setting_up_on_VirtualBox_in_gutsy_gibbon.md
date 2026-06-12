---
title: "XP not setting up on VirtualBox in gutsy gibbon"
date: 2007-11-04
forum: Virtualisation
---

### Post by revolverocelot on 2007-11-04
Hi i'm really new to Linux and i was setting up virtual box on gutsy gibbon o have been following this set up [http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/)
and have done everything it has told me to do.....but when i come to install the OS it does some installing stuff but then it asks me to enter the disk and press enter or press F3 to quit i don't know what to do its really frustrating i have tried it many times and done the old restart after doing the settings but still no success. Please help :)

Thank you

---

### Post by Jose Catre-Vandis on 2007-11-04
Not quite sure at what point in the install process you are hitting a brick wall.

Assuming

You have an XP CD
You have created a virtual hard disk for your VM of sufficient size for the OS installation
You have set the Virtual Machine (VM) to use your physical CDROM
(or you have XP as an iso and you have set your VM to use this iso)
Your VM boots up OK from the XP CD/iso
You have formatted the disk as required

Where do you get to in the install? Do you get past the DOS part and into the graphical part? Do you get past regional info and entering the key?

---

### Post by revolverocelot on 2007-11-04
umm im still dont get past the blue screen, i have a iso image and the propper disk for Win XP and it goes through the whole setting up files (still in a blue screen)

then it goes
 "welcome to set up"
this portion of the setup program prepares Microsoft (R) Windows(R) XP to run on your computer.

[LIST]
[*]To set up Windows XP now, press ENTER.
[*]To repair a Windows XP instalation using Recovery Console, press R.
[*]To quit Setup without installing Windows XP, press F3.
[/LIST]

so i hit ENTER

and it goes to the licensing agreement
F8= I Agree  ESC=i dont agree PAGE DOWN=next page

so i then hit F8
(after reading it all of course ;) lol)

then it comes up with

Windows XP Professional Setup

"Setup cannot find a previous version of windows installed on your computer. To continue, Setup needs to verify that you qualify to use this upgrade product."

Please insert one of the following Windows product CDs into the CD-ROM drive: Windows XP Home Edition (full version), Windows XP Professional (full version), Windows 2000 Professional, Windows Millennium, Windows 98, Windows NT Workstation 4.0, Windows 95, or Windows NT Workstation 3.51

[LIST]
[*]When the CD is in the drive, press ENTER
[*]To quit Setup, press F3
[/LIST]

so i then insert the Legal Windows XP professional service Pack 2 into the CD-ROM drive (the same disk i used to install my main computer) and hit ENTER

Then setup says please wait and then goes back to 

Windows XP Professional Setup

"Setup cannot find a previous version of windows installed on your computer. To continue, Setup needs to verify that you qualify to use this upgrade product."

Please insert one of the following Windows product CDs into the CD-ROM drive: Windows XP Home Edition (full version), Windows XP Professional (full version), Windows 2000 Professional, Windows Millennium, Windows 98, Windows NT Workstation 4.0, Windows 95, or Windows NT Workstation 3.51

[LIST]
[*]When the CD is in the drive, press ENTER
[*]To quit Setup, press F3
[/LIST]

i have got 20 GB of virtual HDD for the setup.....is that to much?

IM AM SO CONFUSED IM TO CONFUSED TO BE ANGRY OR HAPPY LOL 
:confused: :) :(  lol

Thank you

---

### Post by Jose Catre-Vandis on 2007-11-04
You have an upgrade only XP CD!

This needs a full version of XP installed, or for you to have a full version XP CD to hand.
(or any other of the products you have listed)

If you have one of those you will need to install that first, and then upgrade to XP from there.

20gb is plenty for what you need to do.

Good luck :)

---

### Post by dtwwtd on 2007-11-04
He doesn't need to install the full version of XP first. What it is asking for is a cd of a previous version of Windows. All you need to do is put in a cd from a older version of windows when it says this. It will check that disk and then ask for the one that you are currently using. Any old Windows will do 98, 2000, etc.

---

### Post by revolverocelot on 2007-11-04
Thnx ill try this wen i get home from uni :)

---

### Post by Jose Catre-Vandis on 2007-11-05
> **dtwwtd said:**
> He doesn't need to install the full version of XP first. What it is asking for is a cd of a previous version of Windows. All you need to do is put in a cd from a older version of windows when it says this. It will check that disk and then ask for the one that you are currently using. Any old Windows will do 98, 2000, etc.

I quote from my previous post: **or for you to have a full version XP CD to hand (or any other of the products you have listed)**

---

### Post by Proshka on 2007-11-06
Hi,

     Although I do not have the same problem, I am still working on trying to  install Window$ 98 or XP from original and ISO CDs but I always get stuck when the following message appears:

Fatal. Could not read from the boot medium. System halted.

     According to VirtualBox, the CD is mounted on /dev/cdrom. Following other threads, I have created symlinks to dev/cdrom0, /media/cdrom, /media/cdrom0 and all possible combinations which might be feasible, with no avail. 
     It is very frustrating since the only things that still keep me using Window$ sometimes are my Lexmark scanner and some teaching tools which do not work under Wine. Any ideas?

Proshka

---

### Post by siafulinux on 2007-12-07
[SIZE="3"]First create two image files of the media you will be using. I used a Windows XP upgrade disk and a Win98 full version disk.

dd if=/dev/cdrom1 of=~/winxx.iso

I installed 98 onto the drive first and then booted with XP. When you get to the screen asking to verify, look down at the bottom of your Virtualbox window and you will see a CD picture. Right click on this and choose "CD/DVD-ROM image" and now select the Win98 (in my case) image you made earlier and added to Virtualbox.

XP can now verify this disk. When it is done it will ask if you want to format a partition and then ask for the XP disk again. Do the same as the above, but choose the XP image file.

It will then continue with the installation. I honestly don't know why XP cannot verify the install on the HDD, but alas, this works.

Hope that helps
Siafu

P.S. I am on Gutsy.[/SIZE]

---

