---
title: "Large image made up of smaller photos"
date: 2007-08-15
forum: The Cafe
---

### Post by PartisanEntity on 2007-08-15
Right, I am not sure what this technique is called, but quite often you will see a large image made up of countless smaller photos.

Anyone know what this is called and whether there is a tool to do that?

Thanks.

---

### Post by happy-and-lost on 2007-08-15
It's called a photomosaic, and the Wikipedia article about them points to some free software for creating them. [http://en.wikipedia.org/wiki/Photomosaic#Free_photographic_mosaic_software](http://en.wikipedia.org/wiki/Photomosaic#Free_photographic_mosaic_software)

edit: metapixel looks good [http://www.complang.tuwien.ac.at/schani/metapixel/](http://www.complang.tuwien.ac.at/schani/metapixel/)

---

### Post by @trophy on 2007-08-15
On XP I use AndreaMosaic and I would highly recommend it.  I made a huge picture of the Mexican flag out of pictures of me and friends in Mexico... I need to get it printed but it'll be poster sized and that costs a lot.  Anyways yeah AndreaMosaic rocks.

---

### Post by happy-and-lost on 2007-08-15
Oh, or *sudo apt-get install pixelize*

---

### Post by PartisanEntity on 2007-08-15
> **happy-and-lost said:**
> Oh, or *sudo apt-get install pixelize*

Oh very cool, I shall have to try it out soon. Thanks

---

### Post by PartisanEntity on 2007-08-17
I installed pixelize from the repo but I keep getting this error when I launch it:

```
Gtk-WARNING **: Failed to load module "libgail.so": libgail.so: cannot open shared object file: No such file or directory

Gtk-WARNING **: Failed to load module "libatk-bridge.so": libatk-bridge.so: cannot open shared object file: No such file or directory
amr@ubuntunb:~$ pixelize

Gtk-WARNING **: Failed to load module "libgail.so": libgail.so: cannot open shared object file: No such file or directory

Gtk-WARNING **: Failed to load module "libatk-bridge.so": libatk-bridge.so: cannot open shared object file: No such file or directory
```

Has anyone managed to get it to work?

---

### Post by happy-and-lost on 2007-08-17
Works on Gutsy. Is libgail18 installed?

---

### Post by PartisanEntity on 2007-08-17
Yes. And the two modules are present in /usr/bin/gtk2.0/modules/

---

### Post by happy-and-lost on 2007-08-17
I'm on Debian at the moment, so can't rummage around Ubuntu for an answer, but pixelize uses GTK1 libs, not GTK2 ones

---

### Post by vanadium on 2007-08-17
imagemagix tools:

convert infile.jpg crop 100x100 outfile.jpg

will split a larger image in several 100x100 files.

---

### Post by PartisanEntity on 2007-08-17
> **vanadium said:**
> imagemagix tools:

convert infile.jpg crop 100x100 outfile.jpg

will split a larger image in several 100x100 files.

Thanks but that is not quite what I am looking for. I want to create photomosaics.

After searching through Google I found out that one must run *make_db* before pixelize can create a photomosaic. But running ```
make_db /media/disk/pics-folder
``` doesn't work. I get this error:

```
IMLIB ERROR: Cannot load image: /media/disk/pics
All fallbacks failed.
See /usr/share/doc/imlib2/README.fallback.
Error: Can't load image /media/disk/pics
```

Anyone know how make_db is used? The man pages are scarce on help and tips. I have about 2500 images in the folder.

---

### Post by fuscia on 2007-08-17
you can do the same thing in gimp if you add smaller images to the larger by selectining *file > open as layer*.

---

### Post by ThrobbingBrain66 on 2007-08-17
> **PartisanEntity said:**
> Thanks but that is not quite what I am looking for. I want to create photomosaics.

After searching through Google I found out that one must run *make_db* before pixelize can create a photomosaic. But running ```
make_db /media/disk/pics-folder
``` doesn't work. I get this error:

```
IMLIB ERROR: Cannot load image: /media/disk/pics
All fallbacks failed.
See /usr/share/doc/imlib2/README.fallback.
Error: Can't load image /media/disk/pics
```

Anyone know how make_db is used? The man pages are scarce on help and tips. I have about 2500 images in the folder.

Looks like the '-folder' part is giving it trouble as the error message only mentions /media/disk/pics

You could try renaming the folder to 'pictures' or issuing make_db /media/disk/pics-folder/*

---

### Post by PartisanEntity on 2007-08-17
> **ThrobbingBrain66 said:**
> Looks like the '-folder' part is giving it trouble as the error message only mentions /media/disk/pics

You could try renaming the folder to 'pictures' or issuing make_db /media/disk/pics-folder/*

Thanks for the tip, making the pic_db worked using this command:

```
make_db /media/disk/pics-folder/*
```

It's pretty cool software I must say, but you need a large amount of photos, I am trying to make a birthday card for a friend, I have about 2500 photos and the results are not bad, but with an additional 2500 photos they would be better :)

---

### Post by reyfer on 2007-08-17
I usually use this [http://imagemosaicgenerator.click42.com/](http://imagemosaicgenerator.click42.com/)

The site grabs thousands of images from Flickr to make the big image.

---

### Post by PartisanEntity on 2007-08-18
> **reyfer said:**
> I usually use this [http://imagemosaicgenerator.click42.com/](http://imagemosaicgenerator.click42.com/)

The site grabs thousands of images from Flickr to make the big image.

An interesting idea, but more suited to impersonal work. Since I am making a card for a friend I used our photos of friends that we have been making over the past couple of years to make up the image and give it a personal touch.

---

### Post by stooshbunutu on 2008-02-19
Hiya,

Front end for metapixel

I've created a webpage that gerneates the script based on input fields to be copy-and-pasted into terminal to run the command.

It is the attached file, just save the .txt file as a .html file, open it in firefox, and enjoy.

Let me know what you think, I am currently working on converting it into a program front end

Hope you like it :)

---

