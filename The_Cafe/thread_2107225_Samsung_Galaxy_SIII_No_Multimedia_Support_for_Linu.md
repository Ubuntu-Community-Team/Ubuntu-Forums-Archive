---
title: "Samsung Galaxy SIII No Multimedia Support for Linux"
date: 2013-01-21
forum: The Cafe
---

### Post by dominictorreto87 on 2013-01-21
Hello Everyone!

What do you think about new Smartphones made by Samsung, for me it is funny that Android which is a Linux OS Doesn't have a support for Multimedia exchange with Linux Os like Ubuntu.

I know many of you will tell me that there is a way.
Yes but there is a great amount of work to do to make it working properly on Linux. I hope that this subject will become a longer discussion. I'am collecting 25 posts to make my user CP working :)

---

### Post by mamamia88 on 2013-01-21
I know it really sucks.   There is a way but it's stupid and not as convenient as pure usb transfer.  You have to use a program called go-mtpfs or use the android sdk and use the command adb push /file/directory /sdcard/folder/where/you/want/file

---

### Post by dominictorreto87 on 2013-01-21
You can use application KIESAIR but it uses the speed of Internet connection or wireless transfer so on my internet connection(10mb/s) it goes: 1,2MB/s when I have 59GiB of Movies on my SGS III the transfer will take about 18 hours. 
Have Fun :popcorn:

---

### Post by greg_ory on 2013-01-21
Stick your microsd card into your adapter and copy on to it whatever you want that is the way I do it and yes it sucks but couldn't find anything better. So would be open for something clever if existing

---

### Post by dominictorreto87 on 2013-01-21
Ok SD Card is easy, but what about those 16/32/64GiB Versions of SGS III, that don't need a SD Card to have capicty to record movies, when I want to transfer movie from them it takes great amount of problems to get it working. 

There is 40 000 000 000 Samsung Galaxy Users.
Every Galaxy Phone is on Android(Linux).
Now how many of those people will take their phone put usb cord to the hole and then usb in their NON-Mac and NON-Windows PC and cry about not having the posibility to transfer their movies to Youtube.

---

### Post by greg_ory on 2013-01-21
> **dominictorreto87 said:**
> Ok SD Card is easy, but what about those 16/32/64GiB Versions of SGS III, that don't need a SD Card to have capicty to record movies, when I want to transfer movie from them it takes great amount of problems to get it working. 

There is 40 000 000 000 Samsung Galaxy Users.
Every Galaxy Phone is on Android(Linux).
Now how many of those people will take their phone put usb cord to the hole and then usb in their NON-Mac and NON-Windows PC and cry about not having the posibility to transfer their movies to Youtube.

I am entirly with you as I own a SGS III myself, in the end of the day it was my fault to not look into this before I purchased the phone but I hope that something will come up soon what makes file transfer to my Ubuntu machine much easier.

-Greg

---

### Post by dominictorreto87 on 2013-01-21
I will put this conversation to Facebook, and maybe some developer from Samsung Corp will here our thoughts!

The other thing is that this Smartphone Has Everything Except Multimedia Connection. It is like a PC, very fast.

---

### Post by Mikeb85 on 2013-01-21
Blame Samsung.  HTC Android phones work just fine with Linux.

---

### Post by Nburnes on 2013-01-21
> **Mikeb85 said:**
> Blame Samsung.  HTC Android phones work just fine with Linux.

MTP is a standard Google chose. Not Samsung nor HTC.

Good news is, MTP devices such as my Nexus4 and Nexus7 auto-mount in 13.04 now thanks to an updated gvfs. 

[https://launchpad.net/ubuntu/+source/gvfs/1.15.2-0ubuntu1](https://launchpad.net/ubuntu/+source/gvfs/1.15.2-0ubuntu1)

Edit: and then actually this worked great for me before this update was pushed:[http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html)

---

### Post by SeijiSensei on 2013-01-21
I've installed Wifi File Transfer Pro on my S3 as a kludge as I described [here](http://ubuntuforums.org/showpost.php?p=12466242&postcount=7).

---

### Post by 3rdalbum on 2013-01-21
Linux has had MTP support for years. It is not Google's or Samsung's fault that our MTP support is still terrible.

---

### Post by greg_ory on 2013-01-22
> **3rdalbum said:**
> Linux has had MTP support for years. It is not Google's or Samsung's fault that our MTP support is still terrible.

I somehow disagree as hardware manufacturers should not only focus on Windows and/or Mac. They could come up with a solution but that would cost and they probably think this is not worth the effort and ignore the fact that there are Linux user out there. That is the reason why free developer have to workaround this problem rather then the manufacturer. What brings me back to the first statement that I will chose my hardware the next time more wisely.

-Greg

---

### Post by 3rdalbum on 2013-01-22
> **greg_ory said:**
> I somehow disagree as hardware manufacturers should not only focus on Windows and/or Mac. They could come up with a solution but that would cost and they probably think this is not worth the effort and ignore the fact that there are Linux user out there. That is the reason why free developer have to workaround this problem rather then the manufacturer.

Greg, the newer Android phones use MTP to connect to the computer.

MTP works fine on Windows. It works fine on the Mac, as far as I know. In theory it should work fine on Linux, because Linux has supported MTP for years, but in reality we still can't get MTP support to work properly. It's embarrassing, and it's the fault of the developers who work on the three wildly-varying implementations of MTP on Linux, with some guilt to be shared with distro makers such as Ubuntu and desktop developers such as Gnome.

The other two options Google had were to make the phone pretend to be an SD card, or write a proprietary protocol with its own driver for Macs and Windows. I think using MTP was probably the best option as it was easy for Google to do, and inherently cross-platform.

So, it's not a case of "Samsung Galaxy S3 no multimedia support for Linux", it's more a case of "Linux support for a standard widely used since 2004 is still buggy and incomplete". Of course, it's very ironic that Linux distros can't even talk to phones with a Linux kernel using an open standard!

---

### Post by BandD on 2013-01-22
While not a perfect solution (and when I'm too lazy to open up adb) I just change the usb mode to PTP (plug in your phone and touch the little usb symbol in your phone's notification bar and select PTP).  

It might pop open Shotwell if you have Ubuntu configured to automatically open Shotwell when it detects a camera, but the phone will also show up in Nautilus.  While it's not fully browsable (at least I couldn't figure out how to see folders other than the pciture folder) you can copy any file type you want to the phone.  

Then I just open up the file manager on the phone and move the file(s) to whatever folder I want within the internal SD card.

It's pretty simple really and isn't nearly as much of a pain as typing blah blah blah push/pull in the terminal or trying to get some of the other networded solutions to work.  All you need is your USB cable and a couple of fingers.

---

### Post by fontis on 2013-01-22
I agree.
I've also got a SGS3 and I think it's really silly how there has to be such an epic workaround to get things going smoothly..

In all honesty, it's one of those inconveniences that annoy you, but don't kill you :P

---

### Post by hydn79 on 2013-01-22
Also check out the play store app called AirDroid (free). You can transfer files without having to even plugin computer.  (uses wifi)

I feel you on the inconviences but I'll probably never use iPhone again haha

---

### Post by monkeybrain2012 on 2013-01-22
Don't know if this tutorial is any good, don't have a device to check it out. Seems to be just what you guys would need though.

[http://forum.xda-developers.com/showthread.php?t=2055563](http://forum.xda-developers.com/showthread.php?t=2055563)

---

### Post by bfmetcalf on 2013-01-22
I just use samba and ES File Explorer to copy and paste files wherever I want them.  It is via WIFI, but seems to be pretty quick on both my SGS showcase (which is a crap phone anyways) and my ASUS TF101

---

### Post by Ozor Mox on 2013-01-23
I just got an HTC One X+ to replace my HTC Desire and have come up against this annoying removal of USB mass storage.

While it's annoying that MTP isn't well supported in Ubuntu at the moment, the protocol itself isn't exactly brilliant even when using it in Windows. Plenty of people have found it to be unreliable and slow when transferring large amounts of data compared to mass storage.

I tried to transfer ~30GB of music and it simply refuses to do it with the message "the device has either stopped responding or has been disconnected", unless I painfully transfer single folders at a time.

I have tried running an OpenSSH server on my computer and using AndFTP on the phone to transfer the folder over sftp on wifi. This works, but I think 30GB is a bit much to ask over wireless. I maneged to get it to transfer around 10GB but then it collapsed in a heap.

Has anyone used Airdroid to transfer this much stuff? I assume under the hood it is also just an FTP transfer.

Next attempt will be go-mtpfs to try to get MTP working on Ubuntu, or using adb push.

---

### Post by dominictorreto87 on 2013-01-29
> **monkeybrain2012 said:**
> Don't know if this tutorial is any good, don't have a device to check it out. Seems to be just what you guys would need though.

[http://forum.xda-developers.com/showthread.php?t=2055563](http://forum.xda-developers.com/showthread.php?t=2055563)

I will try this and Let you Know if it's working properly):P

---

### Post by Nburnes on 2013-01-29
Upgrade your GVFS with MTP support.

[http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html](http://www.webupd8.org/2013/01/upgrade-to-gvfs-with-mtp-support-in.html)

---

