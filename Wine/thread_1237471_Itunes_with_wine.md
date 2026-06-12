---
title: "Itunes with wine?"
date: 2009-08-11
forum: Wine
---

### Post by hufferd on 2009-08-11
I have looked I will admit not exhaustively but If it can be done can someone direct as to how I can install and run itunes on 9.04 and if I can get that far will itunes function 100% running on ubuntu 9.04?  I just bought an iphone and would really like to be able to use my ubuntu machine for itunes and syncing and backing up the phone.  

thanks Dan

---

### Post by jaxxstorm on 2009-08-11
As far as I'm aware, there is no way of syncing an iPhone with Ubuntu. You can run iTunes under wine (details [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=16848")) but syncing definitely doesn't work.

---

### Post by jaxxstorm on 2009-08-11
Also, I believe if you jeailbreak your iphone you can sync with Amarok, but I'm not sure. There is lots of information [here]("https://help.ubuntu.com/community/PortableDevices/iPhone")

---

### Post by hufferd on 2009-08-11
> **jaxxstorm said:**
> Also, I believe if you jeailbreak your iphone you can sync with Amarok, but I'm not sure. There is lots of information [here]("https://help.ubuntu.com/community/PortableDevices/iPhone")

Ok thanks for the info I also have another thread going I have a virtual box running windows so I could do it that way but I found out that the OSE  ver of VB does not support USB or so I have seen..  And that sucks too so I can't do it that way :(  Oh well the frustration that comes from being a ubuntu user some times LOL 

:lolflag:

---

### Post by andrea000 on 2009-08-12
Songbird will sync with a i pod so i would say it
will a i phone.The new itunes software will not work
with wine as far as i know but you can always download
a older one from [here]("http://www.oldapps.com/itunes.php") to get it to work in wine.

---

### Post by hufferd on 2009-08-12
> **andrea000 said:**
> Songbird will sync with a i pod so i would say it
will a i phone.The new itunes software will not work
with wine as far as i know but you can always download
a older one from [here]("http://www.oldapps.com/itunes.php") to get it to work in wine.

Ok thank you for the info

---

### Post by theGlitch on 2009-08-12
I'm too lazy to find your virtual box post. I've gotten iTunes to work with my iPod touch using the newest VB. Just download that and install windows. 

Next you plug in the USB devices you want recognized in the VB. Go to the setting for the machine you've created and you'll see a USB tab, activate the USB device(s) and start the machine (you won't have to activate them again). Next download and install the most recent iTunes from within the machine.

That should solve your issue. If not, there is a line you'll need to add to your fstab

Add this line to the bottom of /etc/fstab, replace the devgid number with your devgid:
> none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

---

### Post by krazytreee on 2009-08-12
actually, if you're willing to drag and drop files into your eyephone, you can use gtkpod to add files to it directly. it will even give you the album art. all you have to do is make sure it's coded in mp3 or acc, otherwise it won't play. just go to add/remove apps and type it in. i <3 ubuntu!

---

### Post by alex.rayu on 2009-08-12
Eyephone. Lol.

---

### Post by JavaJoeUK on 2009-08-14
You could try using Mediamonkey under Wine. The last report i read about it says most of it works but they dont mention using an Iphone.
 
 
 
Report on WineHQ
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15795](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15795)
 
Mediamonkey
[http://www.mediamonkey.com](http://www.mediamonkey.com)

---

### Post by aysiu on 2009-08-14
> **jaxxstorm said:**
> As far as I'm aware, there is no way of syncing an iPhone with Ubuntu. You can run iTunes under wine (details [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=16848")) but syncing definitely doesn't work.
This post is correct.

The rest, as you can see, is just speculation.

---

### Post by jeb800e on 2009-08-14
RealPlayer should work with your iPhone. But, IDK if it will update, though.....

---

### Post by hikaricore on 2009-08-14
> **jeb800e said:**
> RealPlayer should work with your iPhone. But, IDK if it will update, though.....

I doubt the linux version of Real will work with the iphone at all..

---

### Post by hufferd on 2009-08-16
Thanks for all the replies I had not been able to look at this for a few days :)

---

### Post by Poyntz on 2009-09-12
> **andrea000 said:**
> Songbird will sync with a i pod so i would say it
will a i phone.The new itunes software will not work
with wine as far as i know but you can always download
a older one from [here]("http://www.oldapps.com/itunes.php") to get it to work in wine.

So does gtkpod and all the others. an iPhone is not an iPod. one's practically a mini computer, the other is a media player. until version 8 of iTunes it would have been impossible to sync the iPhone with iTunes. the reason is that one just involves uploading music and video, which is simple enough that many native linux applications will do it (why bother with wine stuff?); the iPhone by comparison, requires comprehension of the iPhone format, in order to recognise and backup applications/settings/contacts/calendar's, etc. it's become a much more complex issue. 

you're dealing with a functional computer here that handles email, internet, media, etc. not a media player

---

