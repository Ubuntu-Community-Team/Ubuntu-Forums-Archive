---
title: "Good photo management software?"
date: 2007-03-05
forum: The Cafe
---

### Post by MeBeMikeyC on 2007-03-05
Hi everyone,

I'm struggling with managing my photos.  In the Windows world, I used Google's Picasa.  I have been using that through Wine, but it's sort of clunky.  I have also tried F-Spot, but didn't care for its file storage scheme.

Anyone have a good recommendation?

On a side note...  After a year of using Ubuntu,  I just now discovered Amarok.  I had been happily using XMMS, but Amarok is just wonderful.   I guess I'm looking for a Amarok for pictures.

Thanks.

---

### Post by gjtoth on 2007-03-05
> **MeBeMikeyC said:**
> Hi everyone,

I'm struggling with managing my photos.  In the Windows world, I used Google's Picasa.  I have been using that through Wine, but it's sort of clunky.  I have also tried F-Spot, but didn't care for its file storage scheme.

Anyone have a good recommendation?

On a side note...  After a year of using Ubuntu,  I just now discovered Amarok.  I had been happily using XMMS, but Amarok is just wonderful.   I guess I'm looking for a Amarok for pictures.

Thanks.

Picasa has a version for Linux.

---

### Post by maniacmusician on 2007-03-05
> **gjtoth said:**
> Picasa has a version for Linux.
not...really...

Their "Linux" version is basically just Picasa + Wine + a few basic optimizations. It's not a native Linux port by any means.

---

### Post by gjtoth on 2007-03-05
> **maniacmusician said:**
> not...really...

Their "Linux" version is basically just Picasa + Wine + a few basic optimizations. It's not a native Linux port by any means.

BUT... it works flawlessly.  At least it does for me.

---

### Post by glotz on 2007-03-05
On GNOME side of the fence I use GQview and on KDE there's ShowImg.

---

### Post by zAo on 2007-03-05
.. or F-Spot (slow as *@#&) of DigiKam (QT based).

There's nothing in the line of Lightroom/Aperture though.

---

### Post by thomasaaron on 2007-03-05
This is a little fecetious, here, but I just pull up a terminal and type in:

locate *.jpg | grep <name associated with picture>

But I'm trying to become more involved with the command line, so ignore me.

Best,
Tom

---

### Post by karellen on 2007-03-05
I use Picasa for linux and gthumb especially for viewing, it's enough for my needs

---

### Post by Bloodfen Razormaw on 2007-03-05
> On a side note... After a year of using Ubuntu, I just now discovered Amarok. I had been happily using XMMS, but Amarok is just wonderful. I guess I'm looking for a Amarok for pictures.
You want Digikam.

---

### Post by MeBeMikeyC on 2007-03-05
> **thomasaaron said:**
> This is a little fecetious, here, but I just pull up a terminal and type in:

locate *.jpg | grep <name associated with picture>

But I'm trying to become more involved with the command line, so ignore me.

Best,
Tom

More manual than I'm looking for, but a great one-liner to remember.  :)  Thanks.


> **Bloodfen Razormaw said:**
> You want Digikam.

Thanks... this is exactly what I was looking for.

---

### Post by Mooseknuckle on 2007-03-30
None of these seem to be that good...

I'm a recent widows convert, and used Thumbsplus, which is the best photo management software I've ever seen ...

Call me disorganized, but I have about 3000 folders with images I've taken, each folder a separate shoot, then I have a 'random' folder with about 12,000 images sitting there.

Thumbsplus handled this fine, and had really slick image manipulation abilities.

Picassa is a trainwreck.   I couldn't figure out how the life of me to get a treeview working, and It tried to put the thousands of my albums in the main pane, and ended up crashing while trying to read the folder with 12,000 images.

Gthumb kinda works, but it's VERY slow in loading the large folder (Thumbsplus loads it instantly), and lacks the image manipulation tools I have grown to love.

Is there anything out there, free or not that comes even close to Thumbsplus?

Thanks in advance!

---

### Post by cowlip on 2007-03-30
.

---

### Post by futz on 2007-03-30
> **Mooseknuckle said:**
> Is there anything out there, free or not that comes even close to Thumbsplus?
Another Thumbsplus user. I love Thumbsplus, and when I first started using Linux I tried every program I could get my hands on in a vain attempt to find a Linux Thumbsplus equivalent. It doesn't exist.

Nothing in Linux comes close to Thumbsplus. It seems that most people don't have to manage the massive collection of pics that I do, and they always point to FSpot or Picasa or other useless (to me) programs. They're mostly unpleasant to use and can't handle large numbers of photos. I have many hundreds of thousands of pics, maybe a million or more. I haven't really counted. They're spread across several machines.

I fought for a while trying to get it to run in Wine, but the ODBC database part refused to work. Somebody more expert than me with Wine might be able to get it going.

I've finally settled on Gthumb. It's no Thumbsplus, but it's ok. The newer versions are much better than v2.7.9 that's in the Edgy repositories. I run 2.9.1 at present.

It crashes now and then, but it does the job reasonably well.

EDIT: Oooohh!! Lightzone looks interesting. Off to get a copy to test... OUCH! It's expensive! Where's the demo? I won't buy unless I can try first. Ah, found it on the Home page. **THERE'S NO LINUX VERSION.**

Never mind. It's in the second link.

Running v2.1. Not impressed so far. Nope, this won't do. Lotta money for not much program.

---

### Post by slimdog360 on 2007-03-30
Just tried that lightzone, a little on the slow side but works great. I like it a lot.

---

### Post by tbroderick on 2007-03-30
> **Mooseknuckle said:**
> Is there anything out there, free or not that comes even close to Thumbsplus?

Thanks in advance!

Did you try digiKam?

[http://www.digikam.org/](http://www.digikam.org/)
```

Features includes with digiKam 0.8.x series
Driving all digital camera types supported by the Gphoto2 project by:
Serial connection
USB connection
USB/IEEE Mass storage connection
Organization of Photos in Albums and sub-Albums
Comments can be added to Albums
Tags can be added to Albums
Albums can be classified by user-specified categories and tags
Automatic sorting of Photo Albums in chronological order:
By folder
By collection name
By creation date
Automatic sorting of Album items in chronological order:
By name
By path
By date
By files size
Drag and drop support between digiKam and other KDE applications
Using Kipi plugin architecture so that new plugins can be written for added functionality. Currently implemented plugins are described on the Kipi page
Comments can be added to photos which are shown in the thumbnail display (along with filesize and file modification date)
A SQLite database is used to store all Albums and items information
Four different thumbnail sizes:
Small: 64x64
Medium: 100x100
Big: 160x160
Very big: 256x256
EXIF Information viewer
Fast image editor with keyboard shortcuts and basic photo editing/management features (all without losing EXIF information). The core options available are:
Red eyes correction
Brightness / Contrast / Gamma correction
Hue / Saturation / Luminosity correction
Color balance
Invert colors
Normalize / Equalize / Auto levels / Stretch Contrast
Blur / Sharpen
EXIF viewer
Histogram viewer
Convert to black&white (BW + color filter, sepia, chemical tonal)
Ratio-cropping (with proportion aids)
Free cropping
Exporting to another image format
Printing images
Removing images from current Album
Image comments editing
Image file properties
Rotation
Flipping
Zooming
The digiKam image editor provides a plugins architecture to add new options. Please visit the DigikamImagePlugins project page for more information
Importing pictures from digital cameras. Other operations currently supported are:
Deleting images
Uploading images
Camera information
Auto-rename during import
Auto-rotate during import
Themes support for the main GUI interface
```

---

