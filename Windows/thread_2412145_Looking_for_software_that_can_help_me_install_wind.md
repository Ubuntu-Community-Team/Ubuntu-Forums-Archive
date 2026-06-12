---
title: "Looking for software that can help me install windows on a usb"
date: 2019-02-08
forum: Windows
---

### Post by hirno93 on 2019-02-08
There seems to be guides and software for installing ubuntu on a USB or other distributions of linux.

But i can't seem to find software that helps you install windows 10 on a USB.

I don't want to install windows 10 from the USB, i want to plug the USB in and run windows 10.

So i'm wondering if any of you know of a software that would help me achieve this?

---

### Post by HermanAB on 2019-02-08
Hmm, first get a chocolate bar and a big mug of coffee.  
Subscribe to the MS Beta Tester program and download a copy of Win10.  
Get more coffee.  
Install Linux on a USB widget.  
Install Virtualbox on Linux.  
Get another chocolate bar and coffee.  
Make a virtual machine with Win10. 
Install Win10 in the VM.

La voila!

---

### Post by howefield on 2019-02-08
Thread moved to the "*Windows*" forum.

---

### Post by hirno93 on 2019-02-08
well this kinda ruins the whole idea. i want a portable version of win 10, i guess i could try to use Rufus on the windows installation in oracle box though.. but it would be sad if thats the only way. :<

---

### Post by yancek on 2019-02-08
The windows installer (this is not specific to windows 10 but all windows versions) is designed not to install to a drive connected by usb or IEEE 1394 ports.  If you boot the windows installer and attempt to do so, the message you should expect to see is this:

> "windows setup does 
not support configuration or installation to a disk connected through usb or IEEE 1394 ports 


I've seen sites that claim to be able to put windows on a usb and maybe they can but using the windows installer won't work.  When you "buy" windows, you are not actually 'buying' anything but are paying them to give you permission to use their software on one and only one system  You can make a backup system but you can't use both simultaneously without violating the EULA.  Every windows system has a EULA and they vary to some degree so read yours to find out.  If you want background explanations for this, the microsoft site or windows forums will serve you better.

---

### Post by QIII on 2019-02-08
Provided you could install Windows on a USB, you would encounter problems the moment you plugged the USB into another machine and tried to run it.  Windows is keyed to a particular machine when it is activated.  If you were to move it to another machine it would choke and tell you either that you are not running genuine Windows or that you need to activate it.  You wouldn't be able to activate it because the new machine would not match the records for that installation.

You could call Microsoft and ask, pretty please, if you could activate it on a new machine, but they would ask, under pain of death, whether you had it installed on another machine.  If you told them you did not and they activated it, you'd be in the same boat going back to the original machine.  They probably wouldn't believe you a second time around.

That is the nature of the license.

You might be able to purchase something like [these]("https://www.windowscentral.com/best-stick-pcs"), but they are not powerful and you would need a monitor with the appropriate ports.

---

### Post by JayKay3OOO on 2019-02-09
Install ubuntu on the usb stick, install virtual box in the installation then install windows 10 - then the usb is portable linux with windows 10 vm.

I searched the web and wintousb is reviewed as working with windows 10 to make a bootable win 10 that will run from the usb drive. 

This whole process of having a portable Windows isn't legal from ms point of view though because ms keys are tied to the hardware and you can't take the key you own for one pc and re-use it for lots of others. I expect if this is for your own lab testing environment then ms probably won't care all that much, but it's way off the ms licensing page once you start using the stick all over the place.

What's the point of this? Super security for your pc? You can also use bitlocker with an encrypted usb key that you can have to use to start the machine, have a secure hard drive pass that a thief won't be able to use when they pull the drive for another pc or use  another file encryption tool like truecrypt that requires a password before OS level to start the PC.

Since I tried this a long time ago around the era of win 7 it was pretty slow on usb2. I expect performance is a bit better on usb3, but it's still a going to be a poor experience. I remember trying ubutu with similar results, only light versions of linux giving a really snappy experience.

---

### Post by C.S.Cameron on 2019-02-09
The only method I have found to install Windows 10 on a Flash drive is the Ubuntu/VBox method.

It was possible to install Windows XP on a flash drive using the Ngine method: [https://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf](https://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf)

This produced a very slow Win XP on USB2, but I never tried it with a USB3 drive.

---

