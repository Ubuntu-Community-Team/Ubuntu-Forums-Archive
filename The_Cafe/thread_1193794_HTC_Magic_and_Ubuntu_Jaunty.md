---
title: "HTC Magic and Ubuntu Jaunty"
date: 2009-06-21
forum: The Cafe
---

### Post by zfranciscus on 2009-06-21
Hi,

This is my first post in the forum. I have been thinking to buy HTC Magic. I just would like to know about your experience with HTC Magic:


[LIST=1]
[*]Does Jaunty recognize the phone when you connect it using the USB cable.
[*]Is it easy to synch your contact or appointments to Jaunty?
[*]Is it easy to transfer files from HTC to Jaunty and vice versa ?
[*]Overall will you recommend me to get HTC Magic as a smart phone ?
[/LIST]
Thank you :P

---

### Post by cdekter on 2009-06-21
I just got mine a few days ago...

1. Yes, works perfectly.
2. Well... yes and no. If you are using Gmail/GCal then yes it's fine, since both the phone and your PC sync with the Google servers. Haven't looked into other syncing techniques.
3. Very easy via the USB mass storage mode. Having said that, the files go onto the SD card (I got a free 8GB card with mine). Not sure if you can put files into the phone memory. Also, haven't tried doing it over Bluetooth.
4. It's a very nice phone, maybe not quite as capable as more established smart phones running Windows CE/others. There are some quirks, e.g. when pairing Bluetooth devices sometimes it doesn't give you enough time to enter the PIN before reporting that the pairing failed. I guess these kinds of minor foibles will be solved over time with O/S updates. 

Mainly, I got it because I've been waiting for a good touch-screen phone that's not an iPhone (flame me if you must, but I hate Apple). And not least because it runs an Open O/S :D

---

### Post by DeadSuperHero on 2009-06-22
Well this is great news, as I've been wanting to break into Android App development for some time now. Yay!

---

### Post by gmalac on 2009-06-22
> **zfranciscus said:**
> 

[*]Is it easy to synch your contact or appointments to Jaunty?


The whole point, I guess, is to synchronyze with Google apps. I can confirm that works wonderfull. You change/create a contact in Google for example and it will appear on your HTC Magic in no time! automatically!
With other applications? I am not sure.

On the minus side I am still under Hardy and although I can see in dmesg that the phone is recognized, nothing appear on the desktop!?! I am still looking for a solution.

Overall like very much the HTC Magic!

---

### Post by descendent87 on 2009-06-22
The phone automatically syncs with google, then if you setup evolution to sync with google you're sorted. I can add a date to my calender from evolution and within a few minutes it's updated on my google calender and on my phone

---

### Post by hanzomon4 on 2009-06-22
> **descendent87 said:**
> The phone automatically syncs with google, then if you setup evolution to sync with google you're sorted. I can add a date to my calender from evolution and within a few minutes it's updated on my google calender and on my phone

I just did this for my iphone and macbook pro dual boot. It's so cool having my contacts, calendars, and emails of course synced across 2 OSes and my phone.. it's like magic

---

### Post by jeferris on 2009-06-23
I also have just started with an HTC Magic and also with Ubuntu.
Please, is there something I need to do to get usb connectivity to work?
Ubuntu sees the phone / usb storage device. (usb plug is 2.0)
my Magic sees a usb connection, and I mount the sd card in android.
...
but when I ask Ubuntu to mount the usb drive, I get an error:
"Unable to mount location: no media in the drive"

This also happens with my attempts to connect via w2k and XP.
I am also able to read the microSD card via an external card reader if I take it out of the phone, and to see the files and folders on it inside the phone using OI File Manager app.

---

### Post by cdekter on 2009-06-23
> **jeferris said:**
> but when I ask Ubuntu to mount the usb drive, I get an error:
"Unable to mount location: no media in the drive"

This also happens with my attempts to connect via w2k and XP.
I am also able to read the microSD card via an external card reader if I take it out of the phone, and to see the files and folders on it inside the phone using OI File Manager app.

The fact that this happens on different O/S would seem to indicate there is some kind of fault with the phone. I would suggest having it looked at by the vendor under the warranty.

---

### Post by Excedio on 2009-06-23
This may also make HTC Magic and Google G1 (and soon G2) users very happy...

[http://arstechnica.com/open-source/news/2009/05/canonical-developers-aim-to-make-android-apps-run-on-ubuntu.ars](http://arstechnica.com/open-source/news/2009/05/canonical-developers-aim-to-make-android-apps-run-on-ubuntu.ars)

---

### Post by jeferris on 2009-06-23
> **jeferris said:**
> I also have just started with an HTC Magic and also with Ubuntu.
Please, is there something I need to do to get usb connectivity to work?
Ubuntu sees the phone / usb storage device. (usb plug is 2.0)
my Magic sees a usb connection, and I mount the sd card in android.
...
but when I ask Ubuntu to mount the usb drive, I get an error:
"Unable to mount location: no media in the drive"

This also happens with my attempts to connect via w2k and XP.
I am also able to read the microSD card via an external card reader if I take it out of the phone, and to see the files and folders on it inside the phone using OI File Manager app.

So it seems all I needed to do was install multiSync - with SynCE.
The issue for w2k and XP seems to be they're both with usb 1.1
...
Sorry to mess with the forums.
My newbie error.

---

### Post by Vadi on 2009-06-24
Got my HTC Magic... usb works because it changes from it, but Ubuntu doesn't see it at all. Not happy.

---

### Post by cdekter on 2009-06-24
> **Vadi said:**
> Got my HTC Magic... usb works because it changes from it, but Ubuntu doesn't see it at all. Not happy.

Did you mount the memory card on the phone after plugging in the USB (via the status bar)?

---

### Post by Vadi on 2009-06-24
It does not appear as a mountable device in Nautilus for some reason.

I think there was a command to show the output of devices as they are plugged in, but I forgot it atm. Would be useful here

---

### Post by cdekter on 2009-06-24
> **Vadi said:**
> It does not appear as a mountable device in Nautilus for some reason.

I think there was a command to show the output of devices as they are plugged in, but I forgot it atm. Would be useful here

I meant on the phone itself - at the top of the screen where the notification area is. When you plug the USB in, a notification appears here. If you expand the notification area, you can touch the notification about the USB being plugged in, which then gives you an option to mount the SD card. 

If you don't perform this step, you'll get exactly the symptoms you describe.

---

### Post by Vadi on 2009-06-24
Thanks for your help so far. Here is how the phone looks like when plugged in.

PS. How can I close an application? This QuickDroid thing is sitting there and really unusable for me with the pokeable keyboard.

---

### Post by Vadi on 2009-06-24
I got it. Wasn't using their home-made usb cable :P

---

### Post by cdekter on 2009-06-24
What is this QuickDroid business? Doesn't seem to be present on my version (Vodafone Australia).

---

### Post by Vadi on 2009-06-24
Some random app I installed... it's like gnome-do for ubuntu.

---

### Post by Netraam on 2009-08-20
Hi,

I cant seem to get the HTC Magic mounted either, works fine in windows XP and vista but every time that I go to mount it via the notification menu on the magic it cycles through the steps and then reverts to being unmounted, and all this in a few seconds. Further more while Ubuntu does seem to recognize that there is a device connected when I attempt to open up/mount the device from ubuntu's side I get a message that reads "Unable to mount location: no media in the drive".

Any advise on how I might solve this issue would be greatly appreciated. I've done some searching on the web and as have yet not found a decent solution.

---

### Post by Paqman on 2009-08-20
Just got one of these. It's a rocking little phone. It mounts fine over the USB, but Karmic doesn't seem to want to connect over Bluetooth.

---

### Post by Copernicus1234 on 2009-08-20
I think the Hero is a better choice today, no?

---

### Post by Paqman on 2009-08-20
> **Copernicus1234 said:**
> I think the Hero is a better choice today, no?

The Hero has a 3.5mm socket and (IIRC) Flash support, but otherwise it's a pretty similar animal really. You can get 3.5mm adaptors for the Magic for about £3 on eBay anyway.

---

### Post by sigge on 2009-09-01
I'm experiencing serious trouble connecting to or from the magic via bluetooth, as the device seems to time out even before I have time to punch a pin code... :(

Is there anybody out there with some sollution to this? Some Magic/Android forum maybe?

---

### Post by Paqman on 2009-09-01
> **sigge said:**
> I'm experiencing serious trouble connecting to or from the magic via bluetooth, as the device seems to time out even before I have time to punch a pin code... :(


So am I actually. I figured it was down to Ubuntu's Bluetooth implementation still being a bit buggy.

---

