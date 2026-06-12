---
title: "Search for a OpenSource Microsoft Movie Maker, only better"
date: 2009-01-18
forum: Ubuntu Studio
---

### Post by ToastyMallows on 2009-01-18
I've searched for so long to find a good program to make videos, in many different formats, of pictures.  I want to make a great time lapse video, and of course I need to have the ability to make the pictures go by very quickly, about one tenth of a second or less.  On top of this, I would love to edit the duration of all the pictures at one time, so I don't waste my time changing the duration of each photo in the movie, Movie Maker does not allow me to do this.

Does anyone have anything to suggest to me?  And if I cannot obtain it from the Add/Remove program list or through a sudo apt-get install command, can someone tell me how to install the program?

Thanks in advanced to anyone who helps me.

Running Ubuntu 8.04.

---

### Post by Takmadeus on 2009-01-18
Well, I know about a program called LiVES that runs finely in ubuntu and perhaps is what you need, else look for kino (easiest video editor in linux IMO) or cinelerra which I haven' really tried but I have read good things about it

---

### Post by Sef on 2009-01-18
Check the [Linux Movies]("http://www.linuxmovies.org/software.html") site.

---

### Post by ToastyMallows on 2009-01-18
Thank you both I'll look into all of these programs when I get home.

---

### Post by hitekwaiter on 2010-01-31
HELP. it is a year later and I'm trying to edit my photography.

Kino, do NOT edit snapshots well...help.

---

### Post by hitekwaiter on 2010-01-31
I need something that will allow me to take .jpg files and turn them into vidoe files....just like windows movie maker.


Again, I've just spent an entire day trying to get kino to do it. 
Its a video editor, not a slideshow editor.

---

### Post by amac777 on 2010-01-31
I've used dvd-slideshow to take a directory full of jpg's and make them into an extremely fast running slideshow (e.g., a 9-month gestation video of weekly shots in 30 seconds). You might want to check that out:

```
sudo apt-get install dvd-slideshow
man dvd-slideshow
```

Also see the webpage at: [http://dvd-slideshow.sourceforge.net/wiki/Main_Page](http://dvd-slideshow.sourceforge.net/wiki/Main_Page)

---

### Post by LuridCinema on 2010-01-31
you can do it w/ ffmpeg

ffmpeg -f image2 -i %04d.jpeg -r 06 -sameq movie.avi

the -r 06 indicates 6 images per second adjust to the frame rate you want
The 04 in "%04d.jpeg" indicates the files are numbered w/ 4 digits. save all files as .jpeg and number them 0001.jpeg up to 9999.jpeg have all in one folder have the pics sized the format you want the movie to be ie 720x480 or 640x480 1280x720
open terminal in folder and you will have an avi movie

---

### Post by wildhostile on 2010-01-31
Hi hitekwaiter,

you can easily make slideshow and animations with cinelerra (or other NLEs like openshot, kdenlive, jahshaka, Blender etc ...)

With Cinelerra, just look these links:
- [http://makefx.wordpress.com/2008/10/07/how-to-load-images-to-make-a-simple-presentation-slideshow](http://makefx.wordpress.com/2008/10/07/how-to-load-images-to-make-a-simple-presentation-slideshow)
- [http://makefx.wordpress.com/2009/01/04/stop-motion-animations-with-cinelerra-the-pesci-example](http://makefx.wordpress.com/2009/01/04/stop-motion-animations-with-cinelerra-the-pesci-example)

---

### Post by cotcot on 2010-02-01
Nearly any NLE can do this (see posts above).
If you want an app only making slideshows you could have a look at [[COLOR="Red"]Smile[/COLOR]]("http://linux.aldeby.org/smile-powerful-slideshow-maker-in-linux.html").

---

### Post by createsean on 2010-02-01
This [url=http://ubuntuforums.org/showthread.php?t=1348318[/url] has several recommendations for movie editors.

---

### Post by Docaltmed on 2010-02-02
Tonight, I just made my first slideshow with Imagination. Worked for me; combined jpg files with vorbis audio files, everything was groovy. Ramped up to speed < 30 minutes. Downloads through Software Center.

I've only tried vorbis output, so I can't vouch for the other formats.

---

