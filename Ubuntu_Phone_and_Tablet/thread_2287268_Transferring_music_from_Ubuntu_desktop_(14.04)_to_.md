---
title: "Transferring music from Ubuntu desktop (14.04) to Ubuntu Phone (15.04)"
date: 2015-07-18
forum: Ubuntu Phone and Tablet
---

### Post by utnubu3 on 2015-07-18
Plugging in Ubtuntu Phone to Ubuntu desktop via USB results in device being recognized as a 'drive' by the desktop, but transferring file (e.g. mp3-files) is not possible triggering error message 'cannot write to this location' ? Data portability between desktop and device is key. 

Anyone having a step by step guide on file transfer between 14.04 desktop and the 15.04 phone ? If upgrading desktop to 15.04 makes any difference, glad to know. If Ubuntu Phone touting its horn on being 'open', is in fact a 'closed' device, barring users from writing privileges from their 'open' also Ubuntu flavored desktop, that is a joke. Cross-device dataportability is key. Dodging dataportability by suggesting users should get their music from commercial streaming subscription services like Soundcloud (which is installed on Ubuntu Phone), is not something each user wants.

Phone is brand new Meizu MX4 15.04 / Desktop is 14.04.

---

### Post by jos-vh67 on 2015-07-18
I haven't tried on 14.04 (I use 15.04), but you have to maken sure that your telephone is unlocked when you connect it to your pc.
Hope this helps.

---

### Post by grahammechanical on 2015-07-18
I think that there is something important that you do not understand about the Ubuntu Phone. As part of the security model the file system is read only. The openness that you so greatly desire would open the Ubuntu phone to all kinds of viruses and malicious software.

Furthermore, each application that runs on the phone is confined and limited in the access it can have to the system. This is to prevent what seems to be an innocent app from accessing stuff such as email contacts that it is not supposed to have access to. All requests by apps must go through what is called the Content hub which will force the app to get authentication from the user.

I do not have a Ubuntu phone but I have run the phone OS on a desktop. The Music app has a method for importing music files. That might be the answer. Also, the Terminal app might give you access to the file system on the desktop and allow you to drag and drop files on to the phone. And yes, the terminal app is closed in the sense of it being locked and the user has to authentic unlocking the terminal if it is to access areas of the file system. You might have better success if trying this operation from the phone to the desktop machine and not the other way around.

One more thing. The Ubuntu phone OS is open source. The phone as commercial device is designed to be closed to malware. 

Regards.

---

### Post by howefield on 2015-07-18
> **jos-vh67 said:**
> I haven't tried on 14.04 (I use 15.04), but you have to maken sure that your telephone is unlocked when you connect it to your pc.
Hope this helps.

This is most likely the cause.

First screenshot shows the locked phone connected to the computer and unavailable for writing, second screenshot shows the phone unlocked and the icons for the phone and SD card become instantly visible and ready for data.

---

### Post by Harald_Walker on 2015-07-18
> **grahammechanical said:**
> I think that there is something important that you do not understand about the Ubuntu Phone. As part of the security model the file system is read only.
Not all of it. You can add music to the music folder or delete image from the pictures folder when the device is mounted.

---

### Post by utnubu3 on 2015-07-19
Thank you Jos. Unlocking did the trick. Much appreciated.

---

### Post by utnubu3 on 2015-07-19
#Howefield: thanks for helpful reply. Importing music from 14.04 desktop to Ubuntu Phone works OK now.

---

### Post by jtappin on 2015-07-20
> **grahammechanical said:**
> I think that there is something important that you do not understand about the Ubuntu Phone. As part of the security model the file system is read only. The openness that you so greatly desire would open the Ubuntu phone to all kinds of viruses and malicious software.

To be more precise: The root file system is read-only, but /home and any SDHC card are not.

---

