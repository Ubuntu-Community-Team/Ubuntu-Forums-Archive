---
title: "Techie people...... HELP ME!!!! (Please?)"
date: 2006-03-21
forum: The Cafe
---

### Post by Kernel Sanders on 2006-03-21
Hi everyone!

I have a GPS navagation system that gets its maps from an SD card.

The SD card *was* in RAW file format, and contained the maps. 

In an effort to add more maps to it, I accidentally formatted the card in FAT file format....... :cry: 

So now, any maps I put on it cant be read....... :cry: 

How do I reformat my SD card in RAW format?

Thanks in advance, I am totally screwed right now!

John \\:D/

---

### Post by ComplexNumber on 2006-03-21
i looks like you've lost your maps. 
whats stopping you from formatting it in RAW format?

btw is it a tom tom?

---

### Post by Kernel Sanders on 2006-03-21
Its one of [*****THESE*****]("http://www.packardbell.co.uk/products/Live/On-The-Go/GPS/GPS-400/gps-400/productsheet-C041940001-53.html")

Dont laugh! :mrgreen: 

The good thing is that I have the maps backed up, but the bloody GPS system wont recognise the SD card unless its in RAW format..... :cry: 

I'm still using Windows XP Pro SP2 as i'm still learning on Ubuntu, so all I can do is reformat the card in FAT, FAT32, or NTFS formats..... :cry:

---

### Post by ComplexNumber on 2006-03-21
i'm not laughing :). its not a bad system that you've got.
how is it normally formatted? on mobile phones, the SD card is formatted from the actual phone, so i would have thought there is an option to do the same on the GPS system.

as an aside, i've just noticed this at the top of the page:"Packard Bell recommends Windows® XP." isn't that what Dell are forced to say by microsoft to ensure that they get a good licence deal? :D. oh well, as long as they have no shame in lying through their back teeth.

---

### Post by Kernel Sanders on 2006-03-21
[QUOTE=ComplexNumber]i'm not laughing :). its not a bad system that you've got.
how is it normally formatted? on mobile phones, the SD card is formatted from the actual phone, so i would have thought there is an option to do the same on the GPS system.

as an aside, i've just noticed this at the top of the page:"Packard Bell recommends Windows® XP." isn't that what Dell are forced to say by microsoft to ensure that they get a good licence deal? :D. oh well, as long as they have no shame in lying through their back teeth.[/QUOTE]

Thanks!

Unfortunately, I cant format the card on the GPS :(

I need to find a way of formatting it in RAW mode on a PC

Just a thought...... can Ubuntu format an SD card in RAW mode? Cos I have the Live CD! (Its what i've been learning on)

John

---

### Post by ComplexNumber on 2006-03-21
i would have thought a typical camera application would be able to achieve that - something like digikam, f-spot, etc.

i've just googled and found [this]("http://www.artplus.hr/adapps/eng/dpr.htm"). it allows you to recover lost files. maybe it will help, but i don't know.

---

### Post by Kernel Sanders on 2006-03-21
Thanks for your help!

I'll try that now! \\:D/

---

### Post by Kernel Sanders on 2006-03-23
Didnt work........ :cry: 

Anyone know a way of formating an SD card in RAW mode? Its currently in FAT

Using Windows XP or the Ubuntu Live CD?

PLEASE HELP!!! :cry:

John

---

### Post by Stealth on 2006-03-23
Mm...RAW is not some sort of filesystem, its actual the file format of the images, you really can't format the card in "RAW" as far as I know...try formatting in FAT32? Or format it from withing the device?

---

### Post by Kernel Sanders on 2006-03-23
Hi!

I cant format it within the device unfortunately..... :cry:

The card *WAS* in RAW, until I stupidly formatted it in FAT. Now, the device cant use it as its not in RAW. I have tried formatting it in FAT, FAT32 and NTFS, and the GPS device cant recognise it in any of those formats.

I need to find some way of getting the card back to RAW, not FAT, FAT32, or NTFS?

Any Idea's?

Thanks!

John

---

### Post by nocturn on 2006-03-23
[QUOTE=*John*]Hi!

I cant format it within the device unfortunately..... :cry:

The card *WAS* in RAW, until I stupidly formatted it in FAT. Now, the device cant use it as its not in RAW. I have tried formatting it in FAT, FAT32 and NTFS, and the GPS device cant recognise it in any of those formats.

I need to find some way of getting the card back to RAW, not FAT, FAT32, or NTFS?

Any Idea's?

Thanks!

John[/QUOTE]

I don't know what is meant by raw.  I can just offer one thing you could try.

Use fdisk on the card (if the card is sda, use fdisk /dev/sda).
Delete all partitions and insert it again.

RAW usually means not formatted...

---

### Post by ssam on 2006-03-23
are you sure a your want it raw formated? i assume that means no file system, just strings of bytes. you would not be able to mount a raw device and add files.

most devices use fat formating.

---

### Post by Kernel Sanders on 2006-03-23
Thanks for the interest guys!

I have a Packard Bell GPS 400, thats running Windows CE with a Destinator ND on it as the Navigation software.

Windows CE, and Destinator can only read SD cards that are not formatted (ie RAW)

And since I stupidly formatted the card in FAT format, I need to find a way to "un-format" it back to RAW

Any Ideas?

John

---

### Post by nocturn on 2006-03-23
[QUOTE=*John*]Thanks for the interest guys!

I have a Packard Bell GPS 400, thats running Windows CE with a Destinator ND on it as the Navigation software.

Windows CE, and Destinator can only read SD cards that are not formatted (ie RAW)

And since I stupidly formatted the card in FAT format, I need to find a way to "un-format" it back to RAW

Any Ideas?

John[/QUOTE]

How did you make a backup of your maps?

Normally, RAW means the files are just on the drive, without an underlying FS.
You can do this by fdisking the partitions off, or not format them and catting the files to the raw device.

cat test.map >/dev/sda

Will put the file on drive sda (not a partition of it) without any formatting.

---

### Post by Kernel Sanders on 2006-03-23
I'm a total ubuntu noob, so I'm still running XP primarily while I learn on the Live CD :oops:

Will that work on the live cd? I have the latest maps downloaded onto Zip File, so I didnt make a backup.

---

### Post by Bender the Robot on 2006-03-23
You may find what you require here:- [http://www.google.co.uk/search?q=format+sd+card+in+raw&start=0&ie=utf-8&oe=utf-8](http://www.google.co.uk/search?q=format+sd+card+in+raw&start=0&ie=utf-8&oe=utf-8)

---

### Post by SeanTater on 2006-03-23
If RAW means the lack of a filesystem, this should do it.. No guarantees.
[LIST]
[*]Plug in the SD card
[*]Open a terminal
[*]Type in cfdisk
[*]Look for the Fat partition - there should not be many others.
[*]Memorize it's size
[*]Cross your fingers
[*]Remove the partition
[*]Create another partition on equal size
[*]You now have a partition containing nothing - no formatting

[/LIST]

---

### Post by Kernel Sanders on 2006-03-23
will this work on the live cd?

---

### Post by jbennett on 2006-03-23
[QUOTE=*John*]will this work on the live cd?[/QUOTE]

Any of the methods mentioned by the other users should work just fine on the LiveCD.  Just make sure you use the Breezy LiveCD (Ubuntu 5.10).

Glad to help.

---

### Post by Kernel Sanders on 2006-03-23
Thankyou so much!

I'll give the live cd a go, and report back with whether or not it works!

Thankyou! 

John \\:D/

---

