---
title: "I just remembered why I don't use any photo manager"
date: 2009-11-19
forum: The Cafe
---

### Post by cguy on 2009-11-19
My mission: to rotate 90 degrees to the right a batch of 200 photos.

**F-Spot**: so f- slow! I can feel my beard grow in the meantime. 12 seconds to rotate an image? I'm faster than that! :D
Also, why do you start over with importing the images when I unselect "Check for duplicates"? You were half way ready!!

**Picasa**: why does it scan my folders automatically?? Let ME tell you what to do, freaky computer program! Also, why do you use Wine and call yourself a Linux program?
Oh, and your menus give me a headache even before I try to understand the entries.

**Digikam**: there's a reason I put my pictures in a certain folder: I want them there! :D Don't copy them to "my" "album" folder, please!

Here's my 3 minutes experience with each of these popular apps.
How freaky they are!!!

Looks like I'll have to bear with F-Spot until I get the job done.

Do you people really like them?

---

### Post by Bachstelze on 2009-11-19
> **cguy said:**
> My mission: to rotate 90 degrees to the right a batch of 200 photos.

ImageMagick yo.

---

### Post by ajy0852 on 2009-11-19
Install the package "gimp-plugin-registry". It comes with a batch processing plugin that you'll find in the "filters" menu of GIMP. You don't need to open all the photos in GIMP, just go through the tabs of the batch processor. Specify your input photos, enable the "turn" plugin, and specify the output filetype and any renaming options you want. Then just let it do it's thing.

Personally, I'm fine with F-spot once I go through the Preferences dialog and change a couple of stuff. But I don't use it for editing - only for importing and tagging my photos. I've never used Gthumb, but I've heard it's a less intrusive photo manager than F-spot and the others you mentioned.

Edit: yeah, Imagemagick is probably better.

---

### Post by ticopelp on 2009-11-19
IrfanView was the only photo manager app I really liked.

---

### Post by Simian Man on 2009-11-19
> **Bachstelze said:**
> ImageMagick yo.

That's what I was going to say:

```

#!/bin/bash

FILES="*.jpg"

for f in $FILES;
do
  convert $f -rotate 90 $f
done

```

.. and you're done :).

---

### Post by ZankerH on 2009-11-19
I used to organise my ~50GB photo collection spanning back 15 years with folders alone and shun photo managers because I saw them as redundant, but then my my cousin complained about how it takes forever to find a particular photo, so I ran them through f-spot and let him waste two days rotating and tagging every single one of them with data about the location, occasion, people in it and a dozen other details - needless to say, it feels much more organised now. Of course, if I didn't have a cousin with OCD, a photo manager wouldn't benefit me at all, but since then I've been dutifully tagging every new photo I add. There you have it. :D

---

### Post by spillz on 2009-11-19
phatch: [http://photobatch.stani.be/](http://photobatch.stani.be/)

or 

(to toot my own horn) phraymd: [https://launchpad.net/phraymd](https://launchpad.net/phraymd)

technically phraymd doesn't rotate your photos it just changes the image rotation flag in the Exif metadata.

---

### Post by slumbergod on 2009-11-19
I still like Picasa but for most quick edits I prefer gthumb. It seems fast to me.

---

### Post by cguy on 2009-11-19
My, my, F-Spot finished the job!

Weird thing: PNGs which were ~1.8MB now have sizes ranging anywhere between 3 and 6MB. :/
Why??

Thank you for the recommendation, Bachstelze! I didn't have a chance to use ImageMagick for rotating the images, but I'll use it for converting them.

--

Whoa, so many replies were posted while I wrote this post. Thanks for the help, guys!

---

### Post by Excedio on 2009-11-19
> **slumbergod said:**
> I still like Picasa but for most quick edits I prefer gthumb. It seems fast to me.
 
+1. Me likes the gThumb!

---

### Post by joey-elijah on 2009-11-19
@ the OP - you can tell Picasa NOT to scan photos you know - its there in the menu. You should also remember that it is designed to be a photo manager - that involves -managing- y'know... 

Also you can fix the UI problems in it with a copy and paste.

As for "why does it call itself a linux programme?" Firstly it has terrific integration into the Gnome desktop, secondly - Last time i heard, Wine only ran on Linux...

---

### Post by Aflack on 2009-11-19
> **cguy said:**
> My mission: to rotate 90 degrees to the right a batch of 200 photos.

**F-Spot**: so f- slow! I can feel my beard grow in the meantime. 12 seconds to rotate an image? I'm faster than that! :D
Also, why do you start over with importing the images when I unselect "Check for duplicates"? You were half way ready!!

**Picasa**: why does it scan my folders automatically?? Let ME tell you what to do, freaky computer program! Also, why do you use Wine and call yourself a Linux program?
Oh, and your menus give me a headache even before I try to understand the entries.

**Digikam**: there's a reason I put my pictures in a certain folder: I want them there! :D Don't copy them to "my" "album" folder, please!

Here's my 3 minutes experience with each of these popular apps.
How freaky they are!!!

Looks like I'll have to bear with F-Spot until I get the job done.

Do you people really like them?

I dont need to deal with that lol. I just organize my pictures by subfolders under Pictures. It's not hard.

---

### Post by V for Vincent on 2009-11-19
phatch is very easy to use and can perform most basic image manipulations.

---

### Post by cguy on 2009-11-19
> **joey-elijah said:**
> @ the OP - you can tell Picasa NOT to scan photos you know - its there in the menu. You should also remember that it is designed to be a photo manager - that involves -managing- y'know... 

Also you can fix the UI problems in it with a copy and paste.

As for "why does it call itself a linux programme?" Firstly it has terrific integration into the Gnome desktop, secondly - Last time i heard, Wine only ran on Linux...
[B]Well, i expected to find a native GTK/QT linux binary, but I found one for Windows.
Props to it for that superb Gnome integration ;)[/B]

Valid points, but overall it wasn't an enjoyable experience for me. Actually, I could barely stand over those 3 minutes in Picasa.

---

### Post by blur xc on 2009-11-19
> **cguy said:**
> My mission: to rotate 90 degrees to the right a batch of 200 photos.


Wait, what?  What year is this?  Who still has a camera w/o an orientation sensor, and photo software that doesn't automatically orient pictures anymore?  I can't even recall the last time I had to rotate a picture...

BM

---

### Post by cguy on 2009-11-19
Many, many people, blur xc... :)

But it doesn't relate to my situation since my pictures are actually scanned papers.

---

### Post by aysiu on 2009-11-19
> **joey-elijah said:**
> 
As for "why does it call itself a linux programme?" Firstly it has terrific integration into the Gnome desktop, secondly - Last time i heard, Wine only ran on Linux... Believe it or not, Wine runs on Mac OS X, albeit badly.

---

### Post by koshatnik on 2009-11-19
Buy Bibble or LightZone. They both have native linux clients and are excellent. Sometimes you have to pay for quality.

---

### Post by Xbehave on 2009-11-19
> As for "why does it call itself a linux programme?" Firstly it has terrific integration into the Gnome desktop, secondly - Last time i heard, Wine only ran on Linux...
Because IIRC it's compiled against against winelib, so it's using wine as a library, which is no different to a gtk app using gtklibs instead of talking to the kernel directly

Personally i don't see a need for a photomanager i have folders, but other people like my parents do so i think ubuntu should ship with one that works for them. Plus there are features like auto tagging by data/people/photo type/etc that folders don't offer.

---

### Post by Tibuda on 2009-11-19
> **Xbehave said:**
> Because IIRC it's compiled against against winelib, so it's using wine as a library, which is no different to a gtk app using gtklibs instead of talking to the kernel directly

No, it is a win32 binary shipped with wine in the same debian package, not an elf using winelib. It is installed on "/opt/google/picasa/3.0/wine/drive_c/Program Files/Google/Picasa3/Picasa3.exe".

---

### Post by John Bean on 2009-11-19
> **aysiu said:**
> Believe it or not, Wine runs on Mac OS X, albeit badly.
Of course it does, just as it does on Unix systems like (say) FreeBSD from which came OSX... in a fashion.

---

### Post by NoaHall on 2009-11-19
> **John Bean said:**
> Of course it does, just as it does on Unix systems like (say) FreeBSD from which came OSX... in a fashion.

.........
No.

Edit: Woops, read it as "freebsd came from osx".

---

### Post by John Bean on 2009-11-19
> **cguy said:**
> 
**Digikam**: there's a reason I put my pictures in a certain folder: I want them there! :D Don't copy them to "my" "album" folder, please!
RTFM and configure appropriately. Digikam is far from perfect but it's streets ahead of the competition you cited as an image manager (not just an image browser) and it's not nearly as simplistic as you seem to think it is.

---

### Post by Excedio on 2009-11-20
Has anyone tried [GTKRawGallery]("http://sourceforge.net/project/screenshots.php?group_id=199135&ssid=92513")?

---

### Post by lisati on 2009-11-20
> **blur xc said:**
> Wait, what?  What year is this?  **Who still has a camera w/o an orientation sensor**, and photo software that doesn't automatically orient pictures anymore?  I can't even recall the last time I had to rotate a picture...

BM

/me puts hand up. Just purchased a replacement yesterday, along with a larger SD card. 

(Good news: Both camera and SD card seem to work with Ubuntu, and the Windows software that came with one of my camcorders will happily recognize the camera and import photos and video from it as well, though its photo/video manager doesn't show the AVI files it imports.)

---

### Post by iiretepii on 2009-11-20
Picasa does whatever I need it to do.  It doesn't have to automatically scan for photos, although I do like that feature.  When it comes to editing, I just use gimp.  F-Spot is not bad, but its on board editing software is garbage.

---

### Post by natedawg on 2009-11-20
Don't Know what your talking about with Digikam. I have all my photos sorted in a special folder structure and Digikam keeps it that way.

---

### Post by saulgoode on 2009-11-20
> **cguy said:**
> My mission: to rotate 90 degrees to the right a batch of 200 photos.
If you wanted to do this batch-style with GIMP, you could use the following command from a terminal (you are basically passing an entire Scheme script from the command line):

```
pattern="/home/username/photo-folder/*.jpg" gimp -i -f -d -b "(let* ((names (cadr (file-glob \"$pattern\" 1))) (image 0) (layer 0) (name 0)) (while (pair? names) (set! name (car names)) (set! image (car (gimp-file-load 1 name name))) (gimp-image-rotate image ROTATE-90) (gimp-file-save 1 image (car (gimp-image-get-active-layer image)) name name) (gimp-image-delete image) (set! names (cdr names))))" -b '(gimp-quit 0)'
```

---

### Post by blur xc on 2009-11-21
> **saulgoode said:**
> If you wanted to do this batch-style with GIMP, you could use the following command from a terminal (you are basically passing an entire Scheme script from the command line):

```
pattern="/home/username/photo-folder/*.jpg" gimp -i -f -d -b "(let* ((names (cadr (file-glob \"$pattern\" 1))) (image 0) (layer 0) (name 0)) (while (pair? names) (set! name (car names)) (set! image (car (gimp-file-load 1 name name))) (gimp-image-rotate image ROTATE-90) (gimp-file-save 1 image (car (gimp-image-get-active-layer image)) name name) (gimp-image-delete image) (set! names (cdr names))))" -b '(gimp-quit 0)'
```

Ok- now do that to a folder w/ 400 images, and only 200 of them are vertical shots.

BM

---

### Post by treesurf on 2009-11-22
I still use the old school gqview.  Very simple and clean program that lets you use your own folder hierarchy and will do batch image rotations.  Quickly.

---

### Post by krige on 2010-03-21
> **cguy said:**
> **F-Spot**: so f- slow! I can feel my beard grow in the meantime. 12 seconds to rotate an image? I'm faster than that! :D
Also, why do you start over with importing the images when I unselect "Check for duplicates"? You were half way ready!!

I totally agree.


> **cguy said:**
> **Picasa**: why does it scan my folders automatically?? Let ME tell you what to do, freaky computer program! Also, why do you use Wine and call yourself a Linux program?
Oh, and your menus give me a headache even before I try to understand the entries.

I totally agree.

> **cguy said:**
> **Digikam**: there's a reason I put my pictures in a certain folder: I want them there! :D Don't copy them to "my" "album" folder, please!

I totally agree.

I also tried GQView, gThumb, Gwenview, Intipunku and for one reason or another I wasn't completely satisfied with them.

The one I liked the most is Shotwell:
[http://www.yorba.org/shotwell/](http://www.yorba.org/shotwell/)
It's quite similar to F-Spot but I found it faster, and having a nicer user interface.

What I really like of both F-Spot and Shotwell is the way they organize the photos, imported from a camera, into separate directories with a hierarchical structure by year, month and day. I would like them even more if they had a renaming facility during import: for example I like all my pictures files to have a prefix with the date and time when they were taken, and at the moment I am forced to do it manually after each import with another program.

What I really miss from all these photo managers is the importing videos feature! Who doesn't take videos with their own digital camera? Are we really supposed to use a separate software to import them or copy them manually?

---

