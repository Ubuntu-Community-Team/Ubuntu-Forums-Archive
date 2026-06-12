---
title: "VirtualBox + WM6 Active Sync"
date: 2008-05-31
forum: Virtualisation
---

### Post by pormogo on 2008-05-31
Well it looks like I too am searching for a way to get my WM6 device to sync with my laptop. Finding linux support to be pretty poor I guessed my best luck would be to try in VirtualBox (I installed the non-free ed some time ago). I have usbfs setup correctly (I think). VirtualBox itself never complains about my USB setup and I am able to add a filter correctly for my device (HTC generic serial is the filter it gives for my mogul). When I boot into windows My Computer shows the device but does not appear to be able to connect to it. Active sync does not see the device either. 

I check the forums and google and checked this thread

[http://ubuntuforums.org/showthread.php?t=648608&highlight=virtualbox+active+sync](http://ubuntuforums.org/showthread.php?t=648608&highlight=virtualbox+active+sync)

and found that my kernel was loading the ipaq module when I plugged in my phone. Some of the people in that thread found that to be problematic. I went ahead and blacklisted that module and now all /var/log/messages says when I plugin my phone is 

[i]May 31 03:02:56 Fenrir kernel: [   87.803707] usb 5-1: new full speed USB device using uhci_hcd and address 2
May 31 03:02:56 Fenrir kernel: [   87.826671] usb 5-1: configuration #1 chosen from 1 choice[/i]

I guess the assumption is that the linux kernel was locking the phone not allowing the windows VE to access it. Regardless that didn't work at all. I still see the device available in My Computer but active sync is not able to access it.

In oppose to before where the output was 


[i]Fenrir kernel: [  548.249040] usb 5-1: new full speed USB device using uhci_hcd and address 2
May 30 20:41:06 Fenrir kernel: [  548.422294] usb 5-1: configuration #1 chosen from 1 choice
May 30 20:41:06 Fenrir kernel: [  548.552464] usbcore: registered new interface driver usbserial
May 30 20:41:06 Fenrir kernel: [  548.552741] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
May 30 20:41:06 Fenrir kernel: [  548.553428] usbcore: registered new interface driver usbserial_generic
May 30 20:41:06 Fenrir kernel: [  548.553432] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
May 30 20:41:06 Fenrir kernel: [  548.566003] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PDA
May 30 20:41:06 Fenrir kernel: [  548.566009] /build/buildd/linux-2.6.24/drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
May 30 20:41:06 Fenrir kernel: [  548.566045] ipaq 5-1:1.0: PocketPC PDA converter detected
May 30 20:41:06 Fenrir kernel: [  548.568190] usb 5-1: PocketPC PDA converter now attached to ttyUSB0
May 30 20:41:06 Fenrir kernel: [  548.568205] usbcore: reglalistered new interface driver ipaq
[/i]

Any help would be most appreciated.

---

### Post by mattze on 2008-06-16
disabling "enhanced network functions" in settings->connections->usb-to-pc in my smartphone did the trick for me. you might want to give it a try.

---

### Post by toster13 on 2008-07-08
I tried disable "enhanced network functions" but got only error message abount RNDIS and Serial
After some googling I found this posts which were useful for me. I did both and could disable the box. Now I can sync my dell axim v51x with windows xp guest system.
[http://www.mobilitysite.com/boards/1173015-post637.html](http://www.mobilitysite.com/boards/1173015-post637.html)
[http://www.mobilitysite.com/boards/1175015-post650.html](http://www.mobilitysite.com/boards/1175015-post650.html)

---

### Post by pormogo on 2008-07-30
> **toster13 said:**
> I tried disable "enhanced network functions" but got only error message abount RNDIS and Serial
After some googling I found this posts which were useful for me. I did both and could disable the box. Now I can sync my dell axim v51x with windows xp guest system.
[http://www.mobilitysite.com/boards/1173015-post637.html](http://www.mobilitysite.com/boards/1173015-post637.html)
[http://www.mobilitysite.com/boards/1175015-post650.html](http://www.mobilitysite.com/boards/1175015-post650.html)

I went into those links and tried all the solutions in them. Still no dice. I downloaded resco but I didn't have any of the registry entries they where referring to on my phone....

Is there any way to get this synced. It's rather annoying not to have a way to backup my contacts,

---

### Post by charlesbh on 2008-08-04
FWIW, tonight I got my HTC universal running WM6.1 to sync by installing VBox 1.6.4 and turning off the USB advanced network setting on my universal, nothing else. Using this release of VBox, USB 2.0 works for me. I didn't try 2.0 in the older release (1.5.6) because I couldn't get sync started and I had already upgraded by the time I found the posts about the advanced network change.

Host: Ubuntu Heron AMD64
VBOX: 1.6.4
Guest:XP Professional 32 bit, Outlook 2003, ActiveSync 4.5 (downloaded today).
PPC: HTC Universal G3, WM6.1 ROMs (Tomal v7.7 from xda-developers)
My PPC is recognized by VBox as 'WindowsCE.Net 5.0'

---

### Post by mordoc on 2009-03-03
> **pormogo said:**
> I went into those links and tried all the solutions in them. Still no dice. I downloaded resco but I didn't have any of the registry entries they where referring to on my phone....

Is there any way to get this synced. It's rather annoying not to have a way to backup my contacts,

To get my HTC touch working, I had to blacklist the following:

rndis_host
rndis_wlan
cdc_ether

After that WM6 and the phone were able to communicate

---

### Post by rockorequin on 2009-07-22
Thanks mordoc! Blacklisting those modules lets my ActiveSync work with Jaunty/VirtualBox 3.02 with 'advanced network functionality' turned on. When I turned it off the windoze mobile device said it couldn't find the USB port, so that was a pointless exercise.

---

### Post by Rihards on 2009-07-25
Big thanks to Mordoc, it was enought to disable those modules to get ActiveSync working on VBox 2.2.4

---

### Post by Onesimus on 2009-08-12
Thanks Mordoc, I blacklisted said modules, rebooted machine, restarted VirtualBox and needed to disable the mobile device in the Device Manager on Windows XP before it connected.

---

### Post by Paulplex on 2010-04-22
> **mordoc said:**
> To get my HTC touch working, I had to blacklist the following:

rndis_host
rndis_wlan
cdc_ether

After that WM6 and the phone were able to communicate

Got to love this forum and good old Google in general; that's done the trick for me too :)

---

### Post by arma0012 on 2010-05-06
Can someone please tell me exactly how to blacklist as in:
 
> To get my HTC touch working, I had to blacklist the following:
 
rndis_host
rndis_wlan
cdc_ether

 
Cheers

---

### Post by skarosg3 on 2010-09-07
its been a while, but i just did that so i know it works.
go to /etc/modprobe.d/blacklist.conf
there add these lines:

[I]blacklist rndis_host
blacklist rndis_wlan
blacklist cdc_ether
[/I]

and done!

thanks Mordoc!!!

---

### Post by ppp0 on 2010-09-14
blacklisting modules really helps on Maverick

---

