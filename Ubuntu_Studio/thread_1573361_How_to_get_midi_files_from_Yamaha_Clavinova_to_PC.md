---
title: "How to get midi files from Yamaha Clavinova to PC"
date: 2010-09-12
forum: Ubuntu Studio
---

### Post by dl1dby on 2010-09-12
Hi,
I am not (yet) using Ubuntu Studio but the regular Ubuntu 10.04. I have the following problem: we have a Yamaha Clavinova CLP-320 piano. We want to transfer music pieces that have been played and saved on the Clavinova to the PC (I think they are MIDI files, but I am not sure). I can transfer saved pieces to my PC (and back to the clavinova) using Windows and the Yamaha MusicSoft downloader software.

But as I want to get rid of Windows completely I want to do this with Ubuntu. So what linux programs can be used to access the Clavinova, transfer saved file to the PC and back?

Any help is highly appreciated.

Thanks in advance,
Dieter

---

### Post by frogotronic on 2010-11-10
Maybe MuseScore?

[http://musescore.org/](http://musescore.org/)

---

### Post by sgx on 2010-11-11
Hi, if your Clavinova uses usb for midi connection instead of
5 pin midi cables, try using the lsusb and usbview commands to see if the
storage location on the yamaha is seen as a linux mass storage device. Run the commands and save the output, run them again after using the yamaha to open its file transfer setup, browse to a file on the Clavinova, and run the linux commands again looking for differences in the output. 

If the Clav can save to usbstick or sd card, those cards should work
in linux. 

You may also try playing the files on the Clav while using Qtractor, Rosegarden, or Muse, to record them live in linux, then just use those apps to record with in the future.

You can also try installing the Yamaha software in wine, google probably knows if this has been done before.

Since you already own windows, might as well keep it on a small partion in a dualboot role, and just use it as needed. Backup your data, run the windows dfrag and disk repair utilities, and then use the linux installer to resize the windows partition, and create new partitions for linux:

/
/home
swap

Cheers

---

### Post by ssokolow on 2012-01-19
If it's anything like the Yamaha PSR-E413, the USB interface is just a built-in version of those $15 eBay USB-MIDI adaptors and it does it using an undocumented set of MIDI SysEx messages.

However, you could always install MusicSoft Downloader inside Wine and use it that way.

I just tested with Wine 1.3.37 (current [wine 1.3.x PPA](http://www.winehq.org/download/ubuntu) version) on 64-bit Oneiric and, aside from one trivial tweak that's described in [the AppDB entry](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24541), the song-transfer functionality works perfectly.

---

### Post by nothingspecial on 2012-01-19
[IMG]http://img696.imageshack.us/img696/7058/necrov.png[/IMG]

---

