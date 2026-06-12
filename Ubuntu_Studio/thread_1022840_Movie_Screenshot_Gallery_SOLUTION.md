---
title: "Movie Screenshot Gallery *SOLUTION*"
date: 2008-12-27
forum: Ubuntu Studio
---

### Post by ShoeUnited on 2008-12-27
I have been trying for quite a while to figure out how to do galleries of screenshots in movies on linux.  Unfortunately, so was a lot of other people.

I have verified this to work in Ubuntu 8.10 (Intrepid) 64-bit (also works on 32-bit)

The program is [mplayer-snapshot]("http://www.gnomefiles.org/app.php/mplayer-snapshot").

**You will need the following installed:**

[FONT="Times New Roman"][SIZE="4"]mplayer
libcairo2
libgdk-pixbuf2
libgtk2.0-0
build-essential[/SIZE][/FONT]

Easily install them by opening a console and typing:

```
sudo apt-get install mplayer libcairo2 libgdk-pixbuf2 libgtk2.0-0 build-essential

```

Now download [mplayer-snapshot]("http://www.gnomefiles.org/download.php?soft_id=2094&where=http%3A%2F%2Fmplayer-snapshot.googlecode.com%2Ffiles%2Fmplayer-snapshot-0.3.tar.bz2") and extract it with your favorite archive extractor to a directory of choice (I chose my /home/ directory).

In a console navigate to that folde by typing:

```
cd /home/shoeunited/mplayer-snapshot-0.3/
```

Then type:

```
./configure
```
```
sudo make
```
```
sudo make install
```

And now it's installed! :D

What this does is create galleries of movies. In your console you can navigate to the directory of your choice and use the options at your discretion.  

The options look like this:  
```
 mplayer-snapshot [options] filename
 -w	<width value>
 -h	<height value>
 -n				do not show time
 -r	<rows>			number of rows
 -c	<columns>		number of colums
 -p	<path>			where to save images
 -d	<directory>		for all movies from directory

 -s <value>			minimum size in MB

```

So if I want 16 (4x4) images of a home movie I shot at E3, I could just type in:

```
 mplayer-snapshot -n -r 4 -c 4 mki-edboon-low-rezcut.avi 

```


[[IMG]http://img523.imageshack.us/img523/8870/mkiedboonlowrezcutpk7.th.jpg[/IMG]](http://img523.imageshack.us/my.php?image=mkiedboonlowrezcutpk7.jpg)


The gallery image defaults to the directory the video is in.  If you have to do a mass gallery of each video simply type:

```
 mplayer-snapshot -n -r 4 -c 4 -d /home/shoeunited/Videos
``` 

(Video folder too large to have an example image.  :lolflag:)

There are some drawbacks though.  Some formats simply won't work with it.  As some MOV, Streaming, and WMV files are incompatible there is another possible solution.  A nautilus script called dhyana.pl is also available and uses ffmpeg & imagemagick to create & convert.

Unfortunately, I don't have the skills to figure out how to configure it or get it working.  But if you'd like to try it's available [here]("http://tobyinkster.co.uk/tag/dhyana/").

I found it on the Brazillian forums here.  So props to those guys for finding it first.  If someone could make a guide to getting that working I would appreciate it.  

Let me know what you think, and let me know if I need to correct anything here. :)

-Shoe

---

### Post by JuanC on 2009-01-03
Also try GFrameCatcher : 
[http://www.gnomefiles.org/app.php/GFrameCatcher](http://www.gnomefiles.org/app.php/GFrameCatcher)

> As some MOV, Streaming, and WMV files are incompatible there is another possible solution.

GFrameCatcher uses GStreamer , the library that uses Totem for example and i get no problems with mov and wmv files.

[IMG]http://developer.berlios.de/dbimage.php?id=4345[/IMG]

---

### Post by ShoeUnited on 2009-01-04
Interesting, when berliOS goes back up I'll give it a look.  :)  Thanks.

-Shoe

---

