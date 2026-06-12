---
title: "Web browser using compiz features"
date: 2008-01-13
forum: Ubuntu Brainstorm
---

### Post by Jay_Bee on 2008-01-13
Now that compiz-fusion is on by default, how about a web browser with integrated composite features like "live tab preview", "coverflow tab switcher", "scale tabs (instead of showcase)", new/close tab animations?
There could me many more possibilities, both functional and eye candy.
I already use Zoom and sometimes Negative when browsing the web.
Of course  there should be an option for turning these off and it should work without compiz.

I'd really like to see that happen, it would rock.
:guitar:

---

### Post by twright on 2008-01-13
that would be cool (it could be based on epiphany webkit)

you can get some of those features from firefox addons

---

### Post by st4rdr1ft3r on 2008-01-15
wouldn't this just require the browser to be accelerated/opengl?

---

### Post by smartboyathome on 2008-01-15
> **st4rdr1ft3r said:**
> wouldn't this just require the browser to be accelerated/opengl?

Yep, it would. It would also not work for some because of this. :(

---

### Post by Jay_Bee on 2008-01-15
Well, the effects would be optional so it would work for everyone (when starting for the first time, browser could check if compiz is enabled to enable its own effects, or it could be started from terminal like "browser -noeffects")

---

### Post by smartboyathome on 2008-01-15
I would say that this should be tested A LOT. A browser with this type of stuff is bound to have problems and take up loads of memory.

---

### Post by raynevandunem on 2008-01-15
> **Jay_Bee said:**
> Now that compiz-fusion is on by default, how about a web browser with integrated composite features like "live tab preview", "coverflow tab switcher", "scale tabs (instead of showcase)", new/close tab animations?
There could me many more possibilities, both functional and eye candy.
I already use Zoom and sometimes Negative when browsing the web.
Of course  there should be an option for turning these off and it should work without compiz.

I'd really like to see that happen, it would rock.
:guitar:

Well, it can't be accomplished through compiz (which is simply a compositing window manager), but it could be accomplished with a mix of Python, OpenGL, and Cairo in GTK+.

However, there's yet no API (that I know of, something like Core Animation) that can allow developers to plug into Epiphany (or other apps) and create such features for the browsers.

---

### Post by twright on 2008-01-16
webkit uses 1/10 of the memory that firefox (gecko) uses so it would probably be faster overall

it could initially be done with thumbnails not like previews

you can get live previews for firefox via addons
[IMG]http://i191.photobucket.com/albums/z76/tomdwright/Screenshot-8.png[/IMG]

however it is made it should probably be based on epiphany (with the super fast webkit backend) not firefox as XUL is none native and epiphany is a much simpler browser

---

### Post by Darkhack on 2008-01-17
Definitely possible.  Just would need to put the rendering engine widget inside of a GtkDrawingArea widget and use Cairo or OpenGL or something of the sort.  QGraphicsView has support for embedded widgets and 3D manipulation as can be seen from this [screenshot]("http://arstechnica.com/news.media/qt440_browser_demo.png").

---

### Post by mrThefter on 2008-01-24
I think the biggest reason you'd want a composite browser is to get rid of all the scrolling issues.
Currently, in the most recent stable kernel and xorg code, redrawing the content within a window has an overhead. While it normally isn't noticeable for typical windows because the contents are static. 
But for each pixel you scroll, the window needs to redraw its contents, which incurs a ton of overhead, because one cm on your monitor is probably like 10 pixels. 

A composited browser would render entire pages to a pixmap, and then, it fits in seamlessly with the composited window manager, as the middle step of redrawing to the buffer and having compiz update the window pixmap from the buffer would be gone.
Scrolling will be as smooth as butter, and it won't rape your CPU.
Of course, this would incur a memory overhead instead of a processor overhead...

However, I hear the new xserver/xorg, 1.5/7.4, combined with a more recent kernel, at least 2.6.24, will solve some of the problem, in addition to having redirected direct rendering (meaning GL apps will finally behave properly). However, it's only with open-source drivers. If you're using restricted drivers, you'll probably have to wait for the features to show up (2D EXA acceleration wtih TTM, specifically)
By the way, the version of xserver/xorg in question is supposed to make it in time for hardy's feature freeze. If not, we'll be using 1.4/7.3, which does have some EXA improvements, but not to the extent planned in 1.5/7.4

---

### Post by Mr. Picklesworth on 2008-01-27
Compiz is really just handling windows, though. What we are waiting for now is composited GTK :)

[http://macslow.thepimp.net/?p=150](http://macslow.thepimp.net/?p=150)
[http://arstechnica.com/news.ars/post/20071217-bringing-more-bling-to-gtk-with-opengl.html](http://arstechnica.com/news.ars/post/20071217-bringing-more-bling-to-gtk-with-opengl.html)

---

### Post by 23meg on 2008-02-06
Food for thought:

[http://www.spacetime.com/](http://www.spacetime.com/)

---

### Post by Jay_Bee on 2008-02-06
That is just awesome, not exactly what I had in mind but cool nonetheless :)
That SpaceTime looks very bandwidth hungry too and I just thought about classic browsing but remixed with cool and useful 3d effects ;) 
Anyway, I still hope someone will someday make a linux 3d browser.

---

### Post by bharkins on 2008-02-14
> **23meg said:**
> Food for thought:

[http://www.spacetime.com/](http://www.spacetime.com/)

The initial web site looks great, but did not install on my Vista machine (got error message) and unfortunately not available for Linux. Nice idea however.

---

