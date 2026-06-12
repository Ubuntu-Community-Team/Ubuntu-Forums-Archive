---
title: "Ubuntu phone compatiblility"
date: 2015-03-25
forum: Ubuntu Phone and Tablet
---

### Post by Jaxilian on 2015-03-25
Hi
I just got my Ubuntu phone (BQ Aquaris E4.5). I thought it would be fully compatible with my Ubuntu desktop, but it was not. It says version 14.10 on the phone, but it could hardly talk to my 14.10 desktop at all.
I can pair it through bluetooth...barely, but it keeps disconnecting and when I finally managed to create a mobile broadband connection it can't connect at all. If I have it connected through USB cable it gives errors on random occasions.

Anyone else got this? Anyone managed to get their Ubuntu phone to work with the desktop?
I know it's a new device, but it doesn't give good vibes

---

### Post by howefield on 2015-03-25
> **Jaxilian said:**
> Anyone else got this? Anyone managed to get their Ubuntu phone to work with the desktop?

Haven't bluetoothed it to the computer yet, might try on the laptop later. Have had the phone connected to the car bluetooth though, where it was rock solid for an hour and a half playing music. And also solid in transferring the music to an SD card from the computer to the phone.

---

### Post by Jaxilian on 2015-03-26
I tried with earlier version 14.04 and then I managed to copy over my music, which worked even though it was iTunes format (it even show album covers). I then tried some avi-files which worked too. However it couldn't handle video files over ~2GB (stopped exactly at 2.1GB each time and gave some error.). I wanted to test movies that I have bought through iTunes and see if it could handle that too.

---

### Post by Jaxilian on 2015-03-30
Also same poor support in Ubuntu 15.04 beta. Doesn't seem to get a DUN connection to it and use it's connection. Why make this phone so incompatible with the desktop OS i don't get it :-( Even my iPhone works with the Ubuntu desktop...grr

---

### Post by Lutz_Fechner on 2015-03-31
On Windows 7 I get the folders on the SD card to repeat itself any time I do modify the SD card itself.

---

### Post by rolandbreedveld on 2015-04-21
Running Ubuntu 14.10 on my desktop, no problems at all

---

### Post by gwaew on 2015-10-29
Hi, 
I just installed to latest Ubuntu Phone build of version 15.04 (r24) on my Nexus 4 (came via Update notification in the phone itself, i.e. didn't need to flash-update the phone via desktop) =d>
Aparently some work has been done on the bluetooth part of the OS.

Anyway, before that update (with 15.04 (r23)) I wasn't able to connnect or even find the handsfree set built into my Toyota Auris at all.
Now, however, at least the handshake (pairing) seems to work: The Nexus 4 finds the infotainment system as a bluetooth device (of type headset or something similar) and offers to exchang a pin to pair the phone with the device. Likewise the Toyota Touch 2 System displays a message asking whether the pin is displayed on the mobile phone.

Unfortunately after the pairing, when the system actually tries to "automatically" open a bluetooth connection, it fails. I've tried switching the auto-connect switch in the bluetooth settings of Ubuntu Phone on and off, and also hit the "Connect" button several times but to no avail.

There have been some older articles regarding Toyota Touch claiming not all bluetooth protocols for all phones had been implemented on the infotainment system, yet. However when I tried another Nexus with android installed the pairing AND the actual connection workd instantly, so it's not the phone (hardware) nor Toyota Touch 2 that's causing the problem.

I'll give it one more shot and try to find a software update for the infotainment system and see if that helps, but my guess it I'll need to wait until r25 of 15.04 or so to get some more parts of the bluetooth protocol(s) implemented :-k.
I wish I could be of any help there, but while being actually a programmer, I don't have any experience with driver implemetation or other such "hardware-focused" software.

---

