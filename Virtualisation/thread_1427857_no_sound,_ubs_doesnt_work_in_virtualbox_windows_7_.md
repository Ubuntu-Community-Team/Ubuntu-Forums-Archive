---
title: "no sound, ubs doesnt work in virtualbox windows 7 guest"
date: 2010-03-12
forum: Virtualisation
---

### Post by davarse on 2010-03-12
hey guys, i run windows 7 using virtual box on ubuntu jaunty host to get my ipod gen 5 working on itunes. it runs ok,internet, networking all fine. but there's no sound. i download realtek AC'97 audio driver but i dont know how to install it. i looked up on the net ([http://www.compdigitec.com/labs/2009/07/21/installing-sound-drivers-for-virtualbox-sound-in-windows-7/](http://www.compdigitec.com/labs/2009/07/21/installing-sound-drivers-for-virtualbox-sound-in-windows-7/)), and follow the instruction to run the setup.exe and but error occured:

[I][/home/david/.cache/.fr-0QQcRe/6305_Vista_PG537/setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/david/.cache/.fr-0QQcRe/6305_Vista_PG537/setup.exe or
          /home/david/.cache/.fr-0QQcRe/6305_Vista_PG537/setup.exe.zip, and cannot find /home/david/.cache/.fr-0QQcRe/6305_Vista_PG537/setup.exe.ZIP, period.
[/I]

btw, it says "Run setup.exe in the temporary directory." what does it means? i just click on setup exe, and the error message comes up.

second, the usb in virtual machine is working.

i need some help. thanks

peac
dave

---

### Post by hashimoto on 2010-03-12
> **davarse said:**
> 
second, the usb in virtual machine is working.

i need some help. thanks

peac
dave

I take it from your subject line that USB does _not_ work (?)

If you are running the "OSE" version of VirtualBox from the repos, it does not have the support for the USB (or at least it did not have it in past times). 

To get the USB support you must install the "PUEL" version. The instructions are here:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by MSich on 2010-03-12
Are you running that setup.exe file from inside the host, or inside the guest?

---

### Post by pricetech on 2010-03-12
The OSE Version does not support USB.  You'll need the PUEL version for that.

Either way, install Guest Additions.  That should make everything work.

DO NOT install any drivers for winders.  Virtual Box (both versions) use virtual hardware that should work with winders just fine.

---

### Post by davarse on 2010-03-12
sorry, it's wrong typing. i mean it doesn't work. 
i think i installed the PUEL version, because i download from the same page.
i run the setup.exe from the host.

---

### Post by MSich on 2010-03-12
You shouldn't have to install any drivers in the host or guest.  Do you have guest additions installed?  That should install "virtual" drivers for all your hardware.

---

### Post by davarse on 2010-03-13
> **MSich said:**
> You shouldn't have to install any drivers in the host or guest.  Do you have guest additions installed?  That should install "virtual" drivers for all your hardware.

how you do it?

---

### Post by MSich on 2010-03-13
Here's how I did it.  Start VB and load your Win7 guest.  Let it load up.  From the menu if you select Devices there should be a Install Guest Additions on the bottom.  During a normal install, it should go out and download the latest Guest Additions.  If it auto mounts (mine did) then it will start the install process in Win.  If not you can click on Devices again and select the CD and then select the Guest Additions ISO which should now be in the list.  THe Guest Editions it installed on mine is 3.0.8, which I think is the latest.  Once that is done, restart your Win.  After I restarted my XP I was able to adjust the video resolution, the usb starting working and other features which didn't work before all worked.

I don't have Win7, so maybe it's different, but I wouldn't think so.  Also, my sound worked from the beginning, but I have a really basic sound card.

I hope you get it figured out.  I like it a lot.

---

### Post by areteichi on 2010-03-13
> **MSich said:**
> You shouldn't have to install any drivers in the host or guest.  Do you have guest additions installed?  That should install "virtual" drivers for all your hardware.

Actually, you do need to install Realtek drivers in order to get sound to work in Windows 7.
See: [http://www.compdigitec.com/labs/2009/07/21/installing-sound-drivers-for-virtualbox-sound-in-windows-7/](http://www.compdigitec.com/labs/2009/07/21/installing-sound-drivers-for-virtualbox-sound-in-windows-7/)

Just follow the instructions and the sound should work just fine. I had the same issue and I managed to solve it simply by installing AC97 audio codec.

---

### Post by MSich on 2010-03-13
> **areteichi said:**
> Actually, you do need to install Realtek drivers in order to get sound to work in Windows 7.
See: [http://www.compdigitec.com/labs/2009/07/21/installing-sound-drivers-for-virtualbox-sound-in-windows-7/](http://www.compdigitec.com/labs/2009/07/21/installing-sound-drivers-for-virtualbox-sound-in-windows-7/)

Just follow the instructions and the sound should work just fine. I had the same issue and I managed to solve it simply by installing AC97 audio codec.

I was wondering if there might be a difference since it was Windows 7.  Good to know.  Thanks.

---

### Post by ShadowTek on 2011-02-08
The downloads on Realtek's website don't seem to be working. I tried with Firefox and Epiphany, and neither worked. I eventually got the proper driver through Windows Update.

---

