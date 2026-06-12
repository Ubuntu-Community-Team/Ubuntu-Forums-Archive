---
title: "Help me find a good picture viewer"
date: 2008-04-11
forum: The Cafe
---

### Post by bash on 2008-04-11
Hello dear community,

I am currently plagued by an annoing problem. Whenevery I want to take a look at one of my images I notice it. What is he talking about you may wonder. Well its quite simple. To make it even easier I made a couple of screens to illustrate my problem.

So now here we have Excerpt A: How I would to have have my image viewer behave:

[[IMG]http://img84.imageshack.us/img84/5585/bildschirmfotojt5.th.png[/IMG]](http://img84.imageshack.us/my.php?image=bildschirmfotojt5.png)

And here is Excerpt B: How it currently is:

[[IMG]http://img231.imageshack.us/img231/6893/bildschirmfoto1rh0.th.png[/IMG]](http://img231.imageshack.us/my.php?image=bildschirmfoto1rh0.png)

As you can conclude from this highly complex analysis. Excerpt A and B are clearly different. Hence we have a problem. Oh my!

Now before you mention gPicView. Tried that. Did the same. I am running Hardy Beta atm. As far as I remember I think the picture viewer included in gutsy used to do it "correctly". Anyone using Gutsy that can check that for me. Pretty please? 

Besides that I would be happy about suggestions what other programm I could use to view my pictures.

---

### Post by reacocard on 2008-04-11
mirage? gthumb?

---

### Post by Bruce H. McCosar on 2008-04-11
Graphical solution: gthumb.  It allows fullscreen mode and custom zooming to any level you wish.

However, honestly, I use a holdover program from my old command line days, before I got so into KDE.  It's called [feh]("http://linuxbrit.co.uk/feh/").

Despite the name (it's not really that complimentary a term in Yiddish), it's a really good viewer program.  What I like is being able to load almost an entire drive full of pictures into it from the command line, with a few easy tricks.

For example, every picture I've ever taken with my digital camera is stored in a directory called /LARGEFILES/Photos (keeping it in a separate directory structure makes it easier for me to do full system backups without creating archives that are 98% music and image files).  If someone asks 'show me some pictures you have taken' I can go to the command line and type

```

feh -FzZ -D 4 -r /LARGEFILES/Photos

```

Believe it or not, this will:

F: blow it up to fullscreen

z: randomize the images in the slideshow

Z: size the images so they fit on the screen

D 4: change the image every 4 seconds

And, best trick of all:

r: recursively add photos to the list by scanning all the directories and subdirectories, creating one huge monster pile of images to draw from for the slideshow.

Cool, huh?  I thought so.  It's sort of the Amarok for images.  (Well, except without the GUI...)

---

### Post by wolfen69 on 2008-04-11
i hate to say this, but Vista has the best image viewer on the planet. (photo gallery) it is the one thing that is keeping my friend from using linux full time. (he has 165,000 photos) if linux could come up with something close, (hint- developers) he would never have to boot into windows. oh well.

Kphotoalbum does a good job though. probably the best ive seen for linux.

---

### Post by dislocated on 2008-04-11
Hey, thanks for the tip on feh! I just installed it and have been playing around with it. Very cool.

---

### Post by blastus on 2008-04-11
gqview

---

### Post by wolfen69 on 2008-04-11
feh is a good command line image viewer.

---

### Post by futz on 2008-04-11
Definitely GThumb. Not perfect, but very good.

---

### Post by chucky chuckaluck on 2008-04-12
another vote for **feh**. in addition to being a great viewer, you can use it to set backgrounds in a lot of window managers.

---

### Post by p_quarles on 2008-04-12
I like Gwenview and feh. Gwenview is an extremely flexible graphical image viewer, and has the added benefit of being integrated with Konqueror (for those of us who use that).

---

### Post by Darkhack on 2008-04-12
I also give a thumbs up to feh.  I was so sick of wanting to look at images and clicking the icon and waiting for the image viewer to launch.  I don't need all the fancy features.  Sometimes I just want to view and image and nothing more.  feh is perfect for this!  Plus I still have the ability to zoom in/out with the plus and minus keys.  feh loads instantly.  If there is any lag, it's waiting for the large image to load and not the viewer application.  I consider there to be a difference between an image viewer and an image editor.

---

### Post by misfitpierce on 2008-04-12
Mirage is the best hands down. It is the greatest picture viewer on the face of the planet. :)

---

### Post by stinger30au on 2008-04-12
aparently irfan view work well in wine. have not tried it myself

[www.irfanview.com](www.irfanview.com)

---

### Post by urukrama on 2008-04-12
> **Bruce H. McCosar said:**
> However, honestly, I use a holdover program from my old command line days, before I got so into KDE.  It's called [feh]("http://linuxbrit.co.uk/feh/").

+1 for Feh. It is a great and fast image viewer, with plenty of options. I hardly use anything else to view images.

---

### Post by Onyros on 2008-04-12
Yep, and feh can also manage your wallpaper. (for those of us who use Awesome, the *boxes, wmii, whatever)

---

### Post by Steveway on 2008-04-12
I prefer Ristretto.
It's very lightweight and a big plus is that it's one of the few image-viewers that support animated .gif files.
Also it has a very nice looking thumbnail-bar.

---

### Post by Polygon on 2008-04-12
I wish we had an infranview port, its like the most amazing file viewer...ever. Fast...plugin extensible......loads almost every file format known to man, PLAYS ANIMATED GIFS, 

but i will have to try a few of these out

---

### Post by SimbaSpirit on 2008-10-19
Just tried ristretto... and I gotta say -1
It loaded my small animated gif... in about a day and a half (dual core 2007 system...)Also you can't just open a picture from within it, you have to open a whole folder and use their little scroller to find the photo you want.

Guess i'll give feh a try :P

---

### Post by costamatrix on 2009-05-27
ok everyone.... but i need an image viewer that offer the same functionality windows does....of view an image, click "send to email" and then ask me if i want to resize the picture or send it on original size....and then create the email...


does anyone know some viewer that offers this functionality?

---

### Post by UbuWu on 2009-05-27
[Viewnior]("http://xsisqox.github.com/Viewnior/") is a really nice photo viewer...

---

### Post by RiceMonster on 2009-05-27
> **Polygon said:**
> I wish we had an infranview port, its like the most amazing file viewer...ever. Fast...plugin extensible......loads almost every file format known to man, PLAYS ANIMATED GIFS, 

but i will have to try a few of these out

Mirage plays animated gifs. That's what I use. Works great, and just opens pictures. That's all i want.

> **SimbaSpirit said:**
> Just tried ristretto... and I gotta say -1
It loaded my small animated gif... in about a day and a half (dual core 2007 system...)Also you can't just open a picture from within it, you have to open a whole folder and use their little scroller to find the photo you want.

Guess i'll give feh a try :P

What? I could open individual pictures no problem. Just open them from whatever file manager you use. I don't like risretto either though.

---

### Post by karatedog on 2009-12-14
Viewnior is just a bit different than GNOME's original picture viewer. Is that a spinoff project? I would really like a pic viewer with the functionality of AcdSee 5.0 (that's an old one, starts very fast, and it is lightweight).
The "special" function I'm looking for is:
- starting picture viewing in 1:1 size
- able to go forward/backward among pictures and retain the viewing position (that is especially good if you have several pictures with the same size and you want to compare a certain area)

---

### Post by Jr.Muffin on 2009-12-14
> **ubuwu said:**
> [viewnior]("http://xsisqox.github.com/viewnior/") is a really nice photo viewer...
+1

---

### Post by karatedog on 2009-12-14
Ok, tried Mirage and it does what I need. 
+1

---

### Post by dragos240 on 2009-12-14
What about fbi. Works great.

---

### Post by cong06 on 2010-03-09
Does anyone know of a good image viewer that displays images as if they're already in a comic book format: cbz, cbr, etc?

Edit: I mean so that the next image is just scrolling down... etc. Like a big pdf.

---

### Post by Tikkyca on 2010-03-09
I use default one it is great.

---

