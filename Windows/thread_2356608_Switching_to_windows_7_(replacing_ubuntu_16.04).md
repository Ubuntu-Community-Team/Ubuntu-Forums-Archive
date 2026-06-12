---
title: "Switching to windows 7 (replacing ubuntu 16.04)"
date: 2017-03-24
forum: Windows
---

### Post by damosey on 2017-03-24
Hi. 

I just finished my first pc build. I tried ubuntu and decided it wasn't for me, so I got a live USB to boot win7 from. I put in the USB, set it as the priority boot and left bios settings. The computer went to a black screen which read:

error: unknown filesystem
Entering rescue mode...
grub rescue>

And now idk what to do. I'm super stuck, and dying to be rid of this headache so I can FINALLY use this pc. 

Thanks for any help in advance!!

---

### Post by yancek on 2017-03-25
> so I got a live USB to boot win7 from

What exactly do you mean by that?  Windows doesn't do 'live' systems so how did you put windows on the usb?  You could extract the files from the windows iso  and copy them to a usb and boot it from Grub from Ubuntu.  If you are getting the grub prompt on boot, it would seem to mean you are still booting from the hard drive where you have Grub.  Do you still have Ubuntu on the machine?

---

### Post by damosey on 2017-03-25
I put a 64 bit version of windows (ISO file) on a flash drive and took it to my school's ITS department. They formatted it for me so that the computer could boot from it essentially as though it were a CD. 
My computer had ubuntu on it (and still does, as far as I know). I put in the flash drive and rebooted, entering BIOS settings when it turned back on. I selected the USB to boot from, then I got the screen I described above. Also, trying to boot from any other drive returns the same screen. 

I apologize if anything is unclear, but I'm doing my best; to be honest this is definitely not my specialty!

---

### Post by mörgæs on 2017-03-25
Another option: If you post the problems you had in Ubuntu there is a good chance that people here are able to help you solving them.

---

### Post by Cavsfan on 2017-03-25
And to add to what          mörgæs said, you could easily boot both Ubuntu and Windows. Many of us do that.

I've got Window 10, Arch Linux, Xubuntu 16.04 LTS and Zesty Zapus 17.04 on my box and can easily select which one I want to boot into.

---

### Post by damosey on 2017-03-25
How do I do this?

---

### Post by yancek on 2017-03-25
> I put a 64 bit version of windows (ISO file) on a flash drive and took  it to my school's ITS department. They formatted it for me so that the  computer could boot from it essentially as though it were a CD.

I think there is a misunderstanding of terminology.  Formatting a drive/partition for all intents and purposes to an ordinary user is pretty much overwriting everything on the drive.  If you have a windows 7 iso somewhere, you can follow the instructions at the site below to extract it and copy it to a usb drive and be able to boot the usb or put an entry for the usb in your Ubuntu /boot/grub/grub.cfg file and boot from it.  Follow the instructions carefully, this worked for me with windows 7 and windows 10. 

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)  

Once you get whichever windows you want installed, you can install Ubuntu and dual boot it with windows.  There are any number of tutorials on doing this but make sure you use one that is using the same boot method you have, MBR or UEFI.

---

### Post by damosey on 2017-03-25
ah I'm sorry, I'm sure I don't know the terminology. I'm fairly confident that this was done correctly by them, as I watched them copy the file to the desktop, format the drive, then put it back on, and I went through a similar process the first time when I installed ubuntu on my blank hdd. I just don't understand what's going wrong. Anyway, it seems that I'm out of luck. I'll continue trying to figure it out, but thank you for all your help. Frustratingly, this is my first experience with building a pc and I can't believe what a hassle this process is turning out to be.

---

### Post by kurt18947 on 2017-03-25
> **damosey said:**
> ah I'm sorry, I'm sure I don't know the terminology. I'm fairly confident that this was done correctly by them, as I watched them copy the file to the desktop, format the drive, then put it back on, and I went through a similar process the first time when I installed ubuntu on my blank hdd. I just don't understand what's going wrong. Anyway, it seems that I'm out of luck. I'll continue trying to figure it out, but thank you for all your help. Frustratingly, this is my first experience with building a pc and I can't believe what a hassle this process is turning out to be.

Does the USB device your school prepared for you work in other machines? Does your new machine have a key to press to select the boot device? My machines use F12 during the P.O.S.T but that's not universal. I have had live USBs that, even though set in BIOS as the default boot choice weren't. Manual selection worked. I've always installed Windows first then Ubuntu. The Windows installer should overwrite any existing O.S. if you can get Windows to boot. It appears to me that Windows' boot manager doesn't notice other operating systems and will overwrite any in its way. GRUB, Ubuntu's boot manager seems more inclined to play well with others.

---

### Post by yancek on 2017-03-25
> I'm fairly confident that this was done correctly by them, as I watched  them copy the file to the desktop, format the drive, then put it back  on,

Ok, that's pretty standard.  From your earlier post it seemed that you had the windows on the flash drive and then it was formatted.  Totally different situation.
You might try the suggestions above by Kurt18947, at least verify if it boots on another computer.  If not something probably went wrong.  The method at the link I posted above works and is step by step but since you don't have Ubuntu, not much help.  Did you format or delete the partition(s) on which you had Ubuntu?

---

### Post by Cavsfan on 2017-03-26
Grub restore perhaps with a live DVD/USB or whatever plugged in?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I have a custom grub but, that's after you've gotten it to boot normally.

Grub/Ubuntu has to be installed after Windows, which it seems you have done. So, I don't see why recovering grub would not work.
There's not much to it; I've done it a few times myself.

---

