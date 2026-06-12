---
title: "I just did a clean install of WIndows and I am already having errors.. help"
date: 2007-04-04
forum: Windows
---

### Post by billdotson on 2007-04-04
I just formatted my HDD and reinstalled Windows XP Professional SP2.  I installed all the drivers I need and all of the programs I use.  I DID not activate or install any (Windows) updates  I then defragged and made a backup image w/ PartImage.  I then restored Windows from that disk image to see if it would work and it seemed to fine.  I then booted into Windows and went into control panel > user accounts and changed one of my user account's to a non-administrative account and also changed it's picture.  Then I exited and opened the user account again and I got an Internet Explorer Script error in something like: line 4, char 1, access denied.  Continue running scripts on this page? Yes    No.  

Whether or not I click yes or no I could still open the user account area.  I then activated automatic updates and installed all updates except for WGA.  After I rebooted I opened the user accounts area and I did not get an Internet explorer script error.  Before I did that I ran the command sfc /scannow while the Windows install disc was in and it scanned for errors in DLLs.  It finished reading all of the DLLs but didn't really do anything.    
It just had the mouse cursor with the hourglass but a dialog box never opened or anything.  

Is there something wrong w/ my Windows install or does it seem to be working fine?  I want to know because I do not want to spend my time making a backup disk image w/ PartImage if there is something wrong w/ my install.  

I know PartImage is experimental w/ NTFS and so I am wondering if there is a free ghost program that works officially w/ NTFS.  I know Ghost 4 Unix works.. but you have to have an FTP server to send the disk image to.. so I can't use that.  

Thanks again.

---

### Post by M$LOL on 2007-04-05
I don't think there is anything major wrong with your install.

Go Start -> Run and type [COLOR="Red"]control userpasswords2[/COLOR] and hit <enter>.

This should give you all the functionality of the other user management window.

I'd say all you need to do is restart to fix the problem though, I don't think it's anything serious. ;)

---

