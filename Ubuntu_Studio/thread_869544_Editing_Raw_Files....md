---
title: "Editing Raw Files..."
date: 2008-07-24
forum: Ubuntu Studio
---

### Post by Cholito on 2008-07-24
Hi!
I must first say it: I've searched...a lot! ;)

Long story short: nikon d40, images taken in RAW, while using Windows: photoshop to edit them and then saved as jpeg and life was beautiful. switching to linux and the only software that gives me a *good* image is irfanview (wine), while RawStudio, Gimp and UFRaw give me different images (all of them a really ugly one!). see screenshot:

[[IMG]http://img61.imageshack.us/img61/4027/pantallazo2lu8.th.png[/IMG]](http://img61.imageshack.us/my.php?image=pantallazo2lu8.png)
The one in the middle is my goal ;)

Even editing the pics A LOT, I can't come close to what I get with win software.

I have ufraw plugin for gimp, which doesn't change a thing. dcraw saves very good images (the closest one) but the exif info is very small!

I wonder if any of you have the same problem, or this is just me? I saved the image using irfanview as jpeg but the exif info is lost (not cool as I like to have it for flickr and for personal reference).

Thanks in advance for the time ;)

---

### Post by aeiah on 2008-07-25
it seems like you're on the right track. maybe this will help. it details colour profile issues (for the d300 but its probably relevant).

[http://blog.crushedredpepper.com/nikon/raw.html](http://blog.crushedredpepper.com/nikon/raw.html)

---

### Post by Cholito on 2008-07-26
I've found this [[link]]("http://pages.quicksilver.net.nz/pepe/d70/Nikon_D70_on_Linux.html") which will restore the exif into the file.

The problem is that I have no idea on how to install it. The doc is 0.

> To compile neftags2jpg, download and install exiv2
([http://home.arcor.de/ahuggel/exiv2](http://home.arcor.de/ahuggel/exiv2)) version 0.7 or newer.

I will be glad to get some help about installing this ;)

---

### Post by cotcot on 2008-07-27
Yesterday I came across [[COLOR="Red"]Lightzone[/COLOR]]("http://www.lightcrafts.com/products/index.html"). It was free for linux before their 3.5 release. I could download a 2.4 release but unfortunately I cannot find anymore from where I got it.
There is a trial version (also for linux) valid for 30 days.

---

### Post by Cholito on 2008-07-27
The only problem I have is installing nedtags2jpg. Once done that, I can make a script to convert+add_exif_data. Now I'm shooting using jpeg and not raw.

---

### Post by Cholito on 2008-07-27
Well, I kind of find it :)

Fist you have to convert the NEF file to JPG:
```
exiftool -overwrite_original -TagsFromFile file.nef file.jpg
```
then add the exif data:
```
exiftool -overwrite_original -TagsFromFile file.nef file.jpg
```

Sadly I haven't found a icm file to use it with ufraw (and others) so for now I'll be shooting in JPEG high quality :)

Using this script, I get what I need :)

```
#!/bin/bash
exiftool -JpgFromRaw $1 -b > $2

exiftool -overwrite_original -TagsFromFile $1 $2
```

Usage: *./addexif file.nef file.jpg*

---

