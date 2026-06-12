---
title: "Image Size in Window"
date: 2019-07-30
forum: Virtualisation
---

### Post by merlot160 on 2019-07-30
Hi,
I have installed Ubuntu 18.04.2 within Virtualbox. Host system is Windows 10. All seem to work fine except that the Ubuntu image is stuck in size. I can drag the corner of the window to make it bigger but it just creates a border around the image which stays the same size. Same thing happens when I go full screen, same size image with a bigger border. I tried installing "Insert guest additional CD image" and thought I had but, it made no difference. I then tried installing it again and got the following error message:

Unable to insert the virtual optical disk **C:\Program Files\Oracle\VirtualBox\VBoxGuestAdditions.iso** into the machine **Testing**.Could not mount the media/drive **'C:\Program Files\Oracle\VirtualBox\VBoxGuestAdditions.iso'** (VERR_PDM_MEDIA_LOCKED).
[TABLE="width: 100%"]
[TR]
[TD]Result Code:[/TD]
[TD]E_FAIL (0x80004005)[/TD]
[/TR]
[TR]
[TD]Component:[/TD]
[TD]ConsoleWrap[/TD]
[/TR]
[TR]
[TD]Interface:[/TD]
[TD]IConsole {872da645-4a9b-1727-bee2-5585105b9eed}[/TD]
[/TR]
[TR]
[TD]Callee:[/TD]
[TD]IMachine {5047460a-265d-4538-b23e-ddba5fb84976}[/TD]
[/TR]
[/TABLE]

I take it this means the the installation has failed so any advice would be appreciated.

---

### Post by wildmanne39 on 2019-07-30
*Thread moved to **Virtualisation a more appropriate sub-forum**.*

---

### Post by cruzer001 on 2019-07-30
The guest addition iso is probably already mounted, just unmount (eject) it and try again.  Have you assigned #of cores, max rez and so on?

---

### Post by merlot160 on 2019-07-30
> **cruzer001 said:**
> Have you assigned #of cores, max rez and so on?

Many thanks for the quick reply, but can you elaborate please?

---

### Post by ajgreeny on 2019-07-30
If it is already mounted you may be able to find the guest additions virtual CD in Windows explorer (if that's what they still call it) and find the appropriate version of VBoxWindowsAdditions.exe file and run it as administrator with a right click.

You must also be sure that the additions CD version is exactly the same as your VBox version.

---

### Post by uRock on 2019-07-30
You can download the guest additions ISO here. [https://blogs.oracle.com/joshis/virtualbox-guest-additions-iso-download](https://blogs.oracle.com/joshis/virtualbox-guest-additions-iso-download) First open Virtualbox, At the top, click **Help**, then click **about **to get your proper version number, so you can download the correct ISO.

> **merlot160 said:**
> Many thanks for the quick reply, but can you elaborate please?

To set RAM, # of CPUs, click on your VM listed to the left to highlight, then click **Settings**, then click **System** on the left and you'll see a tab for **Motherboard** where you can change the amount of RAM and a tab for **Processor** where you can set how many of your physical CPU cores can be used by the VM.

Also, click **Display** over to the left, while in Settings, and make sure **Enable 3D** is checked.

If you're having any troubles finding these, then let me know. I don't mind taking some screenshots or making a screen record and loading it on YouTube.

---

### Post by merlot160 on 2019-07-30
Many thanks for the replies. 

Explorer could not find it but it appears to be mounted as it is showing under Storage/IDE controller in Vbox. There is also an icon at the bottom of Ubuntu and if I hover over it I get the path to the ISO file which is C:/Progamme Files/Oracle. I cannot see how to check the version that installed or how to eject or uninstall it. I have looked at file properties but there is no version number. I have VirtualBox 6.0.10 and  have now gone to the link and downloaded the matching Vboxguestadditions.iso Do I simply delete the one in the Oracle folder and move this one over? 

In Vbox, CPU is set to 2 and RAM is 2GB. Video Memory is max at 128MB and 3D acceleration is enabled. I have not changed any of the Ubuntu settings

---

### Post by cruzer001 on 2019-07-30
> it appears to be mounted as it is showing under Storage/IDE controller in Vbox.
That is it, right click on it and remove (eject).  Then install the new, do not manually mount it.  If that trick does not work, then it can be installed using the command line.

---

### Post by cruzer001 on 2019-07-30
[Mount and Install Guest Additions]("https://blog.jdpfu.com/2012/09/14/solution-for-slow-ubuntu-in-virtualbox")

---

### Post by uRock on 2019-07-30
> **merlot160 said:**
> Many thanks for the replies. 

Explorer could not find it but it appears to be mounted as it is showing under Storage/IDE controller in Vbox. There is also an icon at the bottom of Ubuntu and if I hover over it I get the path to the ISO file which is C:/Progamme Files/Oracle. I cannot see how to check the version that installed or how to eject or uninstall it. I have looked at file properties but there is no version number. I have VirtualBox 6.0.10 and  have now gone to the link and downloaded the matching Vboxguestadditions.iso Do I simply delete the one in the Oracle folder and move this one over? 

In Vbox, CPU is set to 2 and RAM is 2GB. Video Memory is max at 128MB and 3D acceleration is enabled. I have not changed any of the Ubuntu settings

Yes, move it over and delete the old.

---

### Post by merlot160 on 2019-07-31
OK. I opened Vbox/Storage, selected the guestadditions.iso, right  clicked and then remove attachment. It disappeared from Vbox but was still in the Oracle folder so I deleted it and replaced with the correct ISO. It was then showing in Vbox with an exclamation mark and when right clicked said "not accessible" I went back to the Oracle folder selected and right clicked the ISO, then "mount as a virtual drive" This was noted as successful but it is still showing the exclamation mark in Vbox although right clicking it has now changed to "remove attachment" which I have done. How do  I correctly install it from the command line?

---

### Post by cruzer001 on 2019-07-31
Create a new "guest" and try again.  Post #9 gives the command line option.

---

### Post by merlot160 on 2019-07-31
Update: I have now deleted the VM and started again. All is as before except that this I have not selected the "Insert the wrong version of Guest Additions CD images" in Ubuntu. I still have the version that matches my VBox version in the Oracle folder so how do I install it from the command line?

---

### Post by merlot160 on 2019-07-31
Your post came in while I was typing the update! I will check post 9.

---

### Post by cruzer001 on 2019-07-31
It installs itself to vBox in the initial download process.  You should of been prompted to install to vBox.

As uRock suggested you need to remove the old. It will be located in /media of the guest.
```
sudo rm /media/**package_name**
```

---

### Post by merlot160 on 2019-07-31
Sorry but still lost! I have read the link on post 9 and if I select "Machine Menu" there is no Devices menu. This is now appears to be a separate menu and when I select it and then Install Guest Additions I only get the option to download the image file from the internet. I have not done so as I think this will take me back to square one and it will download and mount the wrong version?
Apologies for being thick, but I already have the correct ISO. I have found and opened File Manager but cannot see how to open a terminal as advised in the instructions?

---

### Post by cruzer001 on 2019-07-31
No worries, I'm thick too :)

Do it and follow the prompt.  You know what package version you want, if the download is not a match, then abort.

---

### Post by merlot160 on 2019-07-31
I am now downloading the correct version and get this error as soon as it reaches 100% I have tried about a dozen times and also reinstalled Ubuntu to no avail.
[ATTACH=CONFIG]283707[/ATTACH]

---

### Post by merlot160 on 2019-08-01
All sorted! Managed to install guest additions from the terminal and all is working fine. I can now resize the Unbuntu window including the image.

Many thanks for all the assistance.

---

### Post by cruzer001 on 2019-08-01
Congratulations!

Don't forget
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

