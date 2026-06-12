---
title: "New Nerolinux 3.0.2.1 available!"
date: 2007-11-08
forum: The Cafe
---

### Post by Kosimo on 2007-11-08
A new updated version of Nerolinux comes today and we reach the version 3.0.2.1. 


Changelog:

New features:

    * The 'Properties' dialog for files and folders now supports multiple selection.


Feature updates

    * The new kernel pata_xxx SCSI emulation drivers are now fully supported, and the burn engine has been updated to use them correctly.
    * The DVD ISO images burning process has been fixed. No weird speed or burn process that never ends should occur.
    * Added some additional information to the preview widget in the 'Open compilation' and 'Open Image' dialog box. The user is now able to get some properties of the selected compilation/image.
    * When loading a compilation with non-existing items, a warning dialog box will inform the user about it.
    * Added some more pre-burn checks:
          o for data discs, mode 1 is selected for any medium type other than CD
          o for CD EXTRA compilation: at least one audio track should be present
    * The item duplication now works correctly and does not delete the original item anymore.
    * When ripping an audio track, the '/' character is automatically replaced by '_' for the output file name.
    * The 'Disc Info' dialog output for DVD-RW is now fixed.
    * The Japanese manual has been updated.
    * The date chooser widget now contains 'Ok' and 'Cancel' buttons to be a little bit more user-friendly.
    * The splashscreen is now correctly centered with all window managers
    * Some keyboard accelerators have been added to the 'Encode Files' dialog.


Patches:

    * The 'Data' button of the Mixed-Mode/CD EXTRA compilation editor is now correctly working.
    * Fully erasing a disc on an IDE internal device with new kernels is now working.
    * The 'Eject the disc when the erase is complete' option is now working correctly.
    * Fixed a memory leak within the 'Erase Settings' dialog.
    * The direct connection to FreeDB servers now works like a charm.
    * The re-sampling of audio file when creating audio CD out of it is now working properly.
    * The 'Properties' dialog for files and folders is now counting the directory items and size correctly.
    * The 'Info' tab of the mixed-mode and CD EXTRA compilations in the 'New Compilation' dialog now show the correct size.
    * The data part of mixed-mode and CD EXTRA compilations can now be correctly re-burned.
    * Avoid application crash when loading a compilation with non-existing directory references.





You can download a perfectly functional Nero trial from here:
[http://www.nero.com/eng/downloads-linux3-trial.php]("http://www.nero.com/eng/downloads-linux3-trial.php")


Available in 32 and 64 bit deb and rpm package.


Works perfectly ;)

---

### Post by n3tfury on 2007-11-08
although i strictly use nero for windows, k3b has been great in linux-land.

---

### Post by FG123 on 2007-11-08
Nero do have an uphill battle here - convincing people to buy what they can get for free (without having to pirate) via something like K3b.

---

### Post by jethro10 on 2007-11-08
What I find sad and probably hard to fix is this :-

With windows, its often supplied on the PC via an oem version with a cost of perhaps $5 or less.

When buying a DVD drive, it's often included there also, for windows.

You can buy OEM copies of it for windows from [www.ebuyer.com](www.ebuyer.com) for ony a few $$ also.

But the linux version is 20 euro's. Thats it. Ok, 20 euros is not a massive amount, but it is a large percentage disparity to what most windows users obtain it for.

J

---

### Post by FG123 on 2007-11-08
> **jethro10 said:**
> What I find sad and probably hard to fix is this :-

With windows, its often supplied on the PC via an oem version with a cost of perhaps $5 or less.

When buying a DVD drive, it's often included there also, for windows.

You can buy OEM copies of it for windows from [www.ebuyer.com](www.ebuyer.com) for ony a few $$ also.

But the linux version is 20 euro's. Thats it. Ok, 20 euros is not a massive amount, but it is a large percentage disparity to what most windows users obtain it for.

J
There may be a certain "development cost" to "sales cost" ratio that has to be worked out. The windows version can be cheaper because volume of sales offset the costs needed to make the thing in the first place. Linux is somewhat more niche, but you still have to build the full program, so it's going to be slightly more expensive. It's just how it is.

---

### Post by R_U_Q_R_U on 2007-11-08
> **FG123 said:**
> There may be a certain "development cost" to "sales cost" ratio that has to be worked out. The windows version can be cheaper because volume of sales offset the costs needed to make the thing in the first place. Linux is somewhat more niche, but you still have to build the full program, so it's going to be slightly more expensive. It's just how it is.

It really does not matter how much the developer spends to create the product...the real price is determined by what people are willing to pay for it. If users find K3b and other FOSS products work and these products products cost the user $0.00, then Nero is competing against a great product selling for the time it takes to launch Synaptic and download it.

---

### Post by the_darkside_986 on 2007-11-08
Is Nero still trying to force their own cd image format on everyone via this software or does that only occur in the crippled version that comes with some cd burners? I'm referring to that stupid *.nrg format that no freeware Windows software knows how to use. I've never tried to deal with or burn nrg images in linux though. (But the world would be a better place if everyone would convert all of their files to standard open formats.)

---

### Post by JNowka on 2007-11-08
Personally, I have bought Nero Linux.  The big reason, my cd/dvd recorder on my laptop has always had a bit of trouble with k3b.  But for some reason, Nero Linux doesn't have the same problem.  Hell when I first got my laptop, windows default cd burner had the same problem as k3b.  So I tested it, it just worked, so I bought it.

---

### Post by thx11381974 on 2007-11-08
Dose Nerolinux support UDF ?

---

### Post by svtfmook on 2007-11-08
> **FG123 said:**
> Nero do have an uphill battle here - convincing people to buy what they can get for free (without having to pirate) via something like K3b.
nero has hd-dvd and blue-ray support.

---

### Post by svtfmook on 2007-11-08
> **jethro10 said:**
> What I find sad and probably hard to fix is this :-

With windows, its often supplied on the PC via an oem version with a cost of perhaps $5 or less.

When buying a DVD drive, it's often included there also, for windows.

You can buy OEM copies of it for windows from [www.ebuyer.com](www.ebuyer.com) for ony a few $$ also.

But the linux version is 20 euro's. Thats it. Ok, 20 euros is not a massive amount, but it is a large percentage disparity to what most windows users obtain it for.

J
the oem nero burning suite is a stripped down version of the retail nero burning suite.  it doesn't have all the options like nero digital, smart start, etc.

---

### Post by BradwJensen on 2007-11-11
Wow, i've been using the Trial of Nero for awhile because i used it back on my windows days and i just found this K3B thing now.. Wow.

It's pretty sweet, i just wish its looks blended in with my theme instead of using it's own.

Thanks guys!

---

### Post by FG123 on 2007-11-11
Are there any free burning programs, similar to K3B with roughly the same features, but written in GTK and so independant of all the KDE libs and such? Would be nice to know, as I have gotten by quite well without having to have a mismash of GNOME/KDE crap on my system.

---

### Post by ViRMiN on 2007-11-11
> **the_darkside_986 said:**
> Is Nero still trying to force their own cd image format on everyone via this software or does that only occur in the crippled version that comes with some cd burners? I'm referring to that stupid *.nrg format that no freeware Windows software knows how to use. I've never tried to deal with or burn nrg images in linux though. (But the world would be a better place if everyone would convert all of their files to standard open formats.)

I don't know if you've seen it but, there's an "nrg2iso" package in the "Universe" repo which will convert those NRG images into regular ISO format :)

---

### Post by takuhii on 2007-11-11
I agree with the majority of users on here, why pay for something like Nero, when I can use K3B...

---

### Post by Incense on 2007-11-11
> **FG123 said:**
> Are there any free burning programs, similar to K3B with roughly the same features, but written in GTK and so independant of all the KDE libs and such? Would be nice to know, as I have gotten by quite well without having to have a mismash of GNOME/KDE crap on my system.

Gnomebaker is what you are looking for. 

I don't think Nerolinux is a bad thing. I'm sure there are some windows users who would welcome a program that they used on the other side when they come to linux. Plus, it's great to see this company actually making software for linux. Won't pull me away from K3B, but it's still good to see.

---

### Post by zenwhen on 2007-11-11
I bought Nero Linux because I want to support companies like Ahead that are finally porting their products to Linux. 

This should be encouraged. There are many pieces of software out there, such as games, that do not have open source counterparts. We need to show companies that we are willing to support their support of Linux with our dollars.

Nero Linux is a great piece of burning software. It provides all the functions of K3B to me, but with a GTK interface. 

Great work, Ahead.

---

### Post by thx11381974 on 2007-11-11
K3B doesn't support UDF neither do the other free alternatives. Dose Nerolinux ?

---

### Post by Kosimo on 2007-11-11
> **zenwhen said:**
> I bought Nero Linux because I want to support companies like Ahead that are finally porting their products to Linux. 

This should be encouraged. There are many pieces of software out there, such as games, that do not have open source counterparts. We need to show companies that we are willing to support their support of Linux with our dollars.

Nero Linux is a great piece of burning software. It provides all the functions of K3B to me, but with a GTK interface. 

Great work, Ahead.

I completely support what you say.
But be careful, cuz opensource integrist will attack you saying that closed software will cause the end of the world attacking our computers.

---

### Post by jethro10 on 2007-11-12
> **svtfmook said:**
> the oem nero burning suite is a stripped down version of the retail nero burning suite.  it doesn't have all the options like nero digital, smart start, etc.

Correct, but neither does Nero Linux, making them approx comparable ? but at a vastly different price.

J

---

### Post by kustomjs on 2007-11-14
if you want to download it go here:[ftp://ftp1.usw.nero.com/PUB/e4817fb4a6dd1f84979542204b322e6a/nerolinux-3.0.2.1-x86.deb](ftp://ftp1.usw.nero.com/PUB/e4817fb4a6dd1f84979542204b322e6a/nerolinux-3.0.2.1-x86.deb)

---

