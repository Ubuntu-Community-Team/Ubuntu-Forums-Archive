---
title: "intipunku 0.5. released"
date: 2009-07-08
forum: The Cafe
---

### Post by irielion on 2009-07-08
I want to announce everybody that I recently released intipunku 0.5. I has ton of features over the other release.

Look for screenshots and downloads at [http://intipunku.berlios.de](http://intipunku.berlios.de)

Here is a list of what intipunku can do:

Supported formats:
- Image files: jpeg, png, gif, and more
- Video files: avi and mov
- Raw: any support format by dcraw

Photo editing
- Enhance you photos with autofixes and filters
- Use tools to fix red eyes, crop your photos and create a blue sky
- Use more advanced controls on your photos like brightness, contrast, etc

Photo import
- You can import from camera or folder
- Download photos from picasaweb
- Get photos with a scanner

Photo export
- Upload fotos to Picasaweb and Flickr
- Export to flash slideshow
- Export to folder
- Export to HTML album (gallery)

Other:
- Send photos by mail
- Printing support
- Change or correct date and time of the creation date of your photos. (For example you moved to another timezone or you want to synchronize with photos of someone else)

Advanced tools:
- Create panoramas
- Create collages

Kubuntu users:
- Intipunku integrate till some extent to KDE, for example it uses the kde native dialogs and icon theme.

There are some usues in 0.5.0 which will be fixed in 0.5.1
- Video support is broken  due to broken gstreamer
- Scanning is broken due to typo


(I don't want to spam the forum, I just want to tell the people about the great program I created in order it may make their life easier)

---

### Post by Dragonbite on 2009-07-08
Look promising.

Is this a potential replacement for F-Spot?

---

### Post by bluebyt on 2009-07-08
The deb for Intrepid give me this error:
Error: Dependency is not satisfiable: exiv2

---

### Post by Closed_Port on 2009-07-08
Looks really good but it seems that the deb doesn't install all necessary dependencies. This is what I get:
```
using intigtk
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
Traceback (most recent call last):
  File "/usr/share/intipunku/intipunku.py", line 70, in <module>
    from inti.editor import SunEditor
  File "/usr/lib/python2.6/dist-packages/inti/editor.py", line 34, in <module>
    import gtkimageview
ImportError: No module named gtkimageview

```
Any idea what could be missing?

---

### Post by irielion on 2009-07-09
Looks like exiv2 is missing in intrepid
The gtkimageview module should get installed automatically when it is missing, but i doesnt due to a typo (fixed in bazaar). 

This all will be fixed this weekend in 0.51

(For me this is the potential replacement for f-spot)

---

### Post by Sealbhach on 2009-07-09
> **irielion said:**
> Looks like exiv2 is missing in intrepid
The gtkimageview module should get installed automatically when it is missing, but i doesnt due to a typo (fixed in bazaar). 

This all will be fixed this weekend in 0.51

(For me this is the potential replacement for f-spot)

I got that gtkimageview error in Jaunty 64-bit too. 

The screenshots look nice and I'm not entirely happy with F-Spot so would like to give this a try.

.

---

### Post by pt123 on 2009-07-09
the screenshots look promising? does it suffer from being slow and unresponsive like F-spot?

---

### Post by Ranko95 on 2009-07-09
Looks cool I'll try it out later, I'm on my iPod right now. Also one off topic question, is there a way to Showa preview of an image on it's icon while in The folder?

---

### Post by irielion on 2009-07-10
Okay i released 0.51 it should have all this problems fixed.
The problem is that pygtkimageview is not in the ubuntu repos, so I put it in my own PPA, and in order you make your life easier, it is not a dependency of the intipunku*.deb and intipunku will install it when you run it the first time. The same counts for exiv2.

I think the program is the definitely not slow. Depending on the size of your album it takes a second. If you use difficult graphic filter, then yes the program is quite slow, but image that you make an iteration through 3000x2000 pixels. 
Anyhow i think most stuff works fine, I use it because it is quick way of managing my photos. 

Ranko, i dont know what you mean with show a preview of an image icon.

---

### Post by irielion on 2009-07-16
Dear people,

I just released 0.52 in which I fixed quite some bug that were present in 0.50 and 0.51, and I added a new feature, lossless rotation with the use of jpegtran. Enable it in preferences and install jpegtran. If there is enough demand, I will also implement lossless cropping.

Check it out: [http://intipunku.berlios.de]("http://intipunku.berlios.de")

---

