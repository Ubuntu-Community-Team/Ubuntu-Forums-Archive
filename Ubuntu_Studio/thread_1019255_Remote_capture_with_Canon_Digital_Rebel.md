---
title: "Remote capture with Canon Digital Rebel"
date: 2008-12-22
forum: Ubuntu Studio
---

### Post by SlothPaladin on 2008-12-22
I've been using the Cannon EOS utility in Windows to take still life photos and I really like that it downloads the photo to the hard drive and shows it full screen, that way I can easily see any problems make any adjustments and save myself a lot of work in post.  It is also nice to control the shutter speed and ISO via the computer.

Problem is my Windows computer is not easy to move so I only get that kind of control at my home near my computer.  I have an EEE 900 with Xubuntu 8.10 and I would love to use it for photography, I've installed gPhoto2 but have not had much luck.

if I run **gphoto2 --autodetect** I get this:
```
Model                          Port                                            
----------------------------------------------------------
Canon EOS 350D                 usb:            
Canon EOS 350D                 usb:005,003    Model                          
```
That seems fine, then if I run **gphoto2 --capture-image** (in 'PC Connection' mode) the shutter is released and the image is saved to the cameras compact flash card but I get this message:
```
Detected a 'Canon:EOS 350D (normal mode)'.                                     

*** Error ***              
Error capturing image
ERROR: Could not capture.
*** Error (-114: 'OS error in camera communication') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --capture-image

Please make sure there is sufficient quoting around the arguments.

```

if I run **gphoto2 --list-files** I get a numbered list of all images, so I could run **gphoto2 --get-file=**(last #) it will download the file to my home directory but I will get this error:
```
Detected a 'Canon:EOS 350D (normal mode)'.                                     
Downloading '_MG_0450.JPG' from folder '/DCIM/104CANON'...
                                                                               
*** Error ***              
canon_usb_set_file_attributes: canon_usb_dialogue failed
Saving file as _MG_0450.JPG
```

I had installed **digiKam** and **gtkam**, digiKam is an awful super bloated program that does not seem to do anything I want and gtkam seems like the simplest way to preview and download photos, but is not a valid program for my remote capture needs.


Sorry if I was to verbose
**My Question**
Is there a GUI program for gphoto2 that will capture an image, display it, an have a back button to look at previous captured images?

If not could I make my own browser based app that used AJAX with a little Perl (or something) that would interface with gphoto and let me capture and view with one button press.  I guess the question is can I use perl to call commands in linux (surely you can, but I'm a perl noob)  If you can then I will try to lean enough Perl over the holidays to build this tool myself as it seems like there is enough working gphoto commands to do what I need, it just needs to be automated.

(btw I looked up running Canon's EOS utility with wine [COLOR="Navy"][but it is rated Garbage]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14473")[/COLOR])

---

### Post by 11ni17ge29 on 2008-12-24
how much about a [nike dunk](http://www.afkicks.com) ??every one know??

---

### Post by maphilli14 on 2009-05-15
Hey this post looks old but it popped up in a search I did looking for shutter control over my Canon XTi in Ubuntu.  I did find the front end, gtkam in the Jaunty sources.... not sure It'll do what your asking for but I'm going to play with it and will post findings here...

Mike

---

### Post by indiestudio on 2010-02-15
umount camera first

---

