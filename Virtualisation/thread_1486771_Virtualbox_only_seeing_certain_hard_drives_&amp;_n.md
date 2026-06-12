---
title: "Virtualbox only seeing certain hard drives &amp; no sound in virtual Win7 install."
date: 2010-05-18
forum: Virtualisation
---

### Post by Phosphorror on 2010-05-18
** POSTED UNDER HARWARE AND LAPTOPS THREAD IN ERROR, ORIGINALLY **
Greetings, 
 
I am running Ubuntu 10.4LTS, and using Virtualbox.
 
The Virtualbox I have installed if from the Sun website, and not the Ubuntu repository as apparently USB support isn't on the version from the repository.
 
I have had a friend email me some instructions of his own installation and it was worked perfectly fine for him.
 
Unfortunately, my virtual installation of Windows 7 has no sound, and isn't seeing on of my external hard drives.
 
I have a Toshiba 1GB drive external hard drive PX396U-3T01 (USB2.0) in FAT32 - This works in Ubuntu and has difficulty in capturing under virtual Win7 (says its installing drivers then says that the USB item has failed to install).
 
The other is a Medion HD2GO divided into 4 NTFS partitions which works faultlessly in Ubuntu and sees all the 4 partitions without an issue in either Ubuntu or the virtual install. 
 
Maybe I was over adventurous in using Win7 and should have used XP?  
I used the OEM copy of Win7 32bit what the PC originally came with in the first place (Medion Akoya E4355D - Intel i3, 3gb RAM). The PC also comes with a 64bit version to use if I so desired. 
 
Close, but no cigar up to now. But it was damn cool seeing Win7 inside Ubuntu!
 
[img]http://i260.photobucket.com/albums/ii13/Site_Rehost/Screenshot.png[/img]

---

### Post by pcdctor on 2010-05-18
What worked for me was downloading the AC,97 Audio Codecs software at the following location: [http://www.realtek.com.tw/Downloads/](http://www.realtek.com.tw/Downloads/)

---

### Post by Phosphorror on 2010-05-18
> **pcdctor said:**
> What worked for me was downloading the AC,97 Audio Codecs software at the following location: [http://www.realtek.com.tw/Downloads/](http://www.realtek.com.tw/Downloads/)

Is this to be downloaded in the virtual machine and installed on the virtual Windows7, or on the Linux side of the PC?

With regards to the FAT32 configured hard drive, a friend of mine recommends converting the drive to NTFS. It was suggested to format it to EXT3 or EXT4, but I still need some Windows programs that are on there for my Notebook on the XP side of the machine (I set up my Notebook to dual boot Windows XP and Ubuntu 9.04, skipping 9.10 because of the mobile broadband issue).

---

### Post by BobVila on 2010-05-18
Yeah, download the AC97 driver install within your VM. That'll clear up the Windows 7 sound problems. 

As far as the external drive, have you opened Virtualbox and actually added the drive to the USB passthrough list for your Win7 VM?

---

### Post by Phosphorror on 2010-05-18
> **BobVila said:**
> Yeah, download the AC97 driver install within your VM. That'll clear up the Windows 7 sound problems. 

I see, I shall try that out.

> As far as the external drive, have you opened Virtualbox and actually added the drive to the USB passthrough list for your Win7 VM?

Yes, I have given the 1TB drive the necessary permissions. In virtual Win7, it goes through the motions of trying to find it (prompt on screen the usual 'looking for drivers') and then it fails ('drivers not installed, device may not work properly' or something similar).

As i mentioned, the 250gb external that is in NTFS is perfect. There is a dos prompt in Windows XP that converts the drive into NTFS (which I shall do on the Notebook with WinXP booted up).

---

### Post by Phosphorror on 2010-05-18
Further developments:

NOW have sound. But, not with the installing of Realtec drivers though the virtual machine - in fact virtual Win7 said they were unsuitable drivers that could trash the machine. Somehow, managed to change on a combination that worked for getting sound capture from the virtual Win7. :-)

Now, there is still the hard drive issue. Win7 makes the 'Buh dum' noise to indicate that the 1TB drive is there, but still no joy. It sees it as a drive every so often on booting back up appears but refers to it as Drive I:/ and asked me to format it in one instance (NO WAY!!).

I shall try the NTFS conversion and see how it goes.

---

### Post by Phosphorror on 2010-05-18
UPDATE:

NOW WORKING with 1TB drive. :-D

It turns out, that there may have been a lag with accessing the 1TB drive. Turns out, that if you let it sit there and have 'A Good Old Think' it eventually sees it. This may be an issue with the size of the drive in question and the virtual machine trying to access it, possibly. I am not sure.

Possible suggests for further reference for others:
(1) Convert the external hard disc into NTFS from FAT32. NTFS seems to be discovered far more easier than FAT32 drives in my case.

(2)Try removing, then re-adding the USB hard drive in question. That may 'coax it' into working.

(3)Right Click on the Filter in the adding a USB device selection, and try changing remote from 'No' to 'Any'

These are POSSIBLE solutions I have discovered this evening, but I believe changing an external hard disc to NTFS will work wonders.

The above are 'educated guesses/playing around'.

Cheers.

---

