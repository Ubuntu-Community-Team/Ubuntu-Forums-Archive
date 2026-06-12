---
title: "Raring not compatible anymore with iPhone"
date: 2013-03-20
forum: Ubuntu Development Version
---

### Post by ninovolador on 2013-03-20
Hello Ubuntuers!
First of all, i want to apologize for my extremely Tarzan English. I am using a HP notebook with Raring Ringtail as my only OS

Second, Until Yesterday i was using Quantal, and iPhone worked acceptably good. When i connected the iphone to my notebook, a few errors displayed, and 2 devices showed up. "Batimovil" (my iPhone's name) and "Documentación de Batimovil" (i think it translate as iPhone Documents). The first i didn't knew how to use it, but the second displayed "folders" of some of my phone apps, where i could manage some apps files, and upload documents, music, etc.

With the Raring upgrade, 3 devices show up. The 2 usual and an "iPhone" one. First an error show up "No se pudo montar iPhone. Unable to open MTP device '[usb:001,005]'". The 3 devices are completely useless. If I manage to get into one of them, Nautilus lags for a while and then crashes, or the devices appear and disappear randomly. Then, only the iPhone icon stands in the "Devices" tab, and "Batimovil" blinks on the "Network" tab (nautilus)

What changed on the Raring upgrade? has anyone the same problems as I?

Regards,

---

### Post by pqwoerituytrueiwoq on 2013-03-21
try a different kernel and see if it makes a difference, i think it worked a week ago (the 14th) on raring

---

### Post by ninovolador on 2013-03-21
right now the behavior is very inconsistent.. after a few retries it worked.. sort of. Still having 3 devices but the documents one works.. if i unplg it again, it doesn't work anymore, it refuses to mount until i reboot.

sorry, didn't tried different kernel, only came here to post this

---

### Post by pqwoerituytrueiwoq on 2013-03-21
if it only happens on a certain kernel , you can report a regression bug
```
ubuntu-bug linux
```

---

### Post by dino99 on 2013-03-21
the first possible reason i can imagine about that issue is: old quantal iphone settings (you might found them somewhere inside .local or .gconf or .config) are not compatible with raring and then break the "mount" process. So you need to erase these old settings, the system will recreate the good ones when you will try your iphone again.

---

### Post by ninovolador on 2013-03-22
By any chance could this settings be located on .config/libimobiledevice? i don't wanna mess up stuff

---

### Post by cariboo on 2013-03-22
> **ninovolador said:**
> By any chance could this settings be located on .config/libimobiledevice? i don't wanna mess up stuff

Make a backup of the file, and store it somewhere else, before removing it. if something breaks, you can restore it, and be back where you are now.

---

### Post by Elfy on 2013-03-22
shouldn't even need to do that - just lose the leading . from the folder name 

not that I'm saying backing up is a bad idea of course ;)

---

