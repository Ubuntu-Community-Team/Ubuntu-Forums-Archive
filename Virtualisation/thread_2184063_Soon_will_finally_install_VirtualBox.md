---
title: "Soon will finally install VirtualBox"
date: 2013-10-27
forum: Virtualisation
---

### Post by Tom_ZeCat on 2013-10-27
My Lenovo Laptop came with 4 GB of RAM.  I just sent off for a kit to upgrade that to 8 GB.  Soon as that's installed, I'm going to install VirtualBox and Windows 7 under Kubuntu 13.10.  I'll divide the memory as 4 GB for Kubuntu and 4 for Windows 7.  That way I'll still have the same 4 gig in each OS that I have now.  (I dual boot now.)  I didn't want to split it 2/2, hence the order of memory.  

I can accomplish most of what I want to do in Kubuntu.  However, in Windows I run the Final Draft screenwriting word processor, Photoshop, PhotoImpact, Quicken, and ConvertXtoDVD.  (I might switch to KMyMoney at some point.)  I don't do a lot in Windows anymore.  When writing in Final Draft I save straight to a thumb drive, never using the internal drive.  

I'm curious if people have had good luck using USB-based devices like thumb drives in Windows virtualboxed under *buntu.  This will be important to me.  The one other thing I still do in Windows is copy OGG sound files from a thumb drive to a Sandisk Clip MP3 player.  I've gotten the Clip to show up in Kubuntu, but I don't have any luck seeing my files on it or copying files to it.  Until I can solve that problem in Kubuntu, I'll handle that with Windows.  Should this work well under VirtualBox?

---

### Post by ian-weisser on 2013-10-27
Yes, VB USB support for many devices has worked great for years.

Are you telling VB to use the USB device? Devices --> USB --> (your USB stick)

---

### Post by Tom_ZeCat on 2013-10-27
> **ian-weisser said:**
> Yes, VB USB support for many devices has worked great for years.

Are you telling VB to use the USB device? Devices --> USB --> (your USB stick)

Thanks.  I've saved that info.  I haven't even installed VB yet.  I'm waiting until my memory upgrade arrives in the mail.  I'll have 8 GB, 4 for Kubuntu and 4 for Windows 7.  That should be plenty to run both OSes well.  If Win 7 runs well enough under VB/Kubunutu, I'll uninstall the Windows 7 that I now have under dual boot.

---

### Post by chasrcoleman on 2013-10-27
Just a note that took me a long time to discover.  Virtual box, current edition does not work well under Windows 7 (what I have).  However the previous edition I used VirtualBox-4.2.16-86992-Win.exe operates quite well and installs perfectly then allows the 12.04 (LTS) to install and operate without a hitch.  The latest edition (VirtualBox-4.3.0-89960-Win.exe) is a terrible upgrade and messed me up for days, setting back my development of a C++ program.  It failed to install Ubuntu 12.04 over and over, but all this disappeared when I went back to my original version of Virtualbox (4.2.16).  So don't install the upgrade (even a clean install won't work), use the older version if you can find it.  If you have a problem I can email you mine (10 megs) and you can do your normal paranoid virus check on it but it's clean.  C.C.

---

### Post by Tom_ZeCat on 2013-10-28
> **chasrcoleman said:**
> Just a note that took me a long time to discover.  Virtual box, current edition does not work well under Windows 7 (what I have).  However the previous edition I used VirtualBox-4.2.16-86992-Win.exe operates quite well and installs perfectly then allows the 12.04 (LTS) to install and operate without a hitch.  The latest edition (VirtualBox-4.3.0-89960-Win.exe) is a terrible upgrade and messed me up for days, setting back my development of a C++ program.  It failed to install Ubuntu 12.04 over and over, but all this disappeared when I went back to my original version of Virtualbox (4.2.16).  So don't install the upgrade (even a clean install won't work), use the older version if you can find it.  If you have a problem I can email you mine (10 megs) and you can do your normal paranoid virus check on it but it's clean.  C.C.

Thanks for the heads up.  Looks like the version in Kubuntu's Muon Discover repository is VirtualBox 4.2.16-dfsg-3.  With any luck they won't update that repository between now and when I receive my memory.  I don't want to install it until I have all 8 GB in my machine.  

If they have updated the repository, I'll be in touch if I can't find the install files.  Thanks again for the info.

---

### Post by coldraven on 2013-10-28
I would install the latest version of VirtualBox from their site and not the one in the repos. You need to add the Extension Pack for USB support.
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
After you have installed Windows in a VM and got all the updates I would suggest that you do at least one of the following things.
1.Take a snapshot of the drive with the Virtualbox "snapshot" button.
2.Export the drive with the Virtualbox "Export" function and save to an external drive. (takes about 15mins although it always says 2hrs to begin with)
3. Just copy the whole VM to an external drive.

So when Windows slows down or dies you can do a fast restore to mint condition. I don't know about Win7 but XP takes hours to install so the ability to restore it quickly is a real bonus.

---

### Post by ian-weisser on 2013-10-28
> **coldraven said:**
> I would install the latest version of VirtualBox from their site and not the one in the repos. You need to add the Extension Pack for USB support.

In the past, but I just replaced manually-installed VB with the packagedversion from the 13.10 repos...and USB support works from the repo version also now.

---

### Post by JKyleOKC on 2013-10-28
Last time I checked for updates in my 4.2.18 installation, I was told it was the latest version -- although 4.3.0 is there on the Oracle download page. My experience is that 4.3.0 is not yet ready for serious use; it disallows snapshots and saved states! My recommandation to the OP is that he download the 4.2.18 package NOW from the Oracle download site, together with its matching extension package; there's no need to install them now, but it's good to have them on hand.

Once 4.3 has been tamed, the 4.2.18 package will suggest that you upgrade. Until the bugs are killed, they're keeping it away from the automatic-upgrade features (according to posts on Oracle's forums).

---

### Post by SeijiSensei on 2013-10-28
You can dynamically adjust the memory allocation for a VM after you've created it from the VM's Settings > System dialog.  Ubuntu has no problem running easily in 2-3 GB of memory, especially if you have a swap partition allocated, so that leaves 5-6 GB free for Windows.  Try the 4/4 split, but if Windows slows down, move the slider over to 6 GB and see if that solves the problem.

---

