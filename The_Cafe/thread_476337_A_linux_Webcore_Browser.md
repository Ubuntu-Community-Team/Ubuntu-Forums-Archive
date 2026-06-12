---
title: "A linux Webcore Browser"
date: 2007-06-17
forum: The Cafe
---

### Post by bonzodog on 2007-06-17
I have always wanted to find a browser that did not use the bloated gecko engine, and was fully gtk2 compatible.

Dillo was only gtk1.2, and has never been updated.

So, I decided to start my hunt by trying to find the other web engines available.

It got me to wondering what OSX was using, so a deeper look at Safari revealed the Open Source Webcore engine, which is in the process of being ported to [Gtk2]("http://gtk-webcore.sourceforge.net/")

Then, a further hunt revealed this:

[The Atlantis Web Browser]("http://www.akcaagac.com/index_atlantis.html")

I really think that Ubuntu/Canonical could push this a lot further and progress the port of the webcore Gtk engine, along with the Gnome team. A gnome web browser that used Webcore gtk2 as it's engine would be cool.

Currently, there is almost no Java support (although the gtk2-webcore homepage seems to hint that there is), and there is no flash support.

---

### Post by kripkenstein on 2007-06-17
Atlantis is 2 years old, and doesn't seem to be currently active.

Likewise gtk-webcore is not very active, although I hear that in subversion there is some progress.

Anyhow, it would be great if this stuff would be successful, but it seems doubtful for now, especially given Firefox's popularity.

---

### Post by bonzodog on 2007-06-17
Yes, I know the project is almost completely dead, more's the pity.

But, someone like Canonical and the Gnome devs could actually pick up these projects and actually run with them, and make them into something of a viable alternative to FF.

---

### Post by Erunno on 2007-06-17
Some guys at Trolltech are working actively on a Qt/Webkit port so I guess this would qualify as a "Linux Webcore Browser" once someone builds a shell around it or implements it as a KPart into Konqueror. Hopefully this will find its way into KDE4 down along the road to replace KHTML (after all, Webkit evolved out of KHTML).

---

### Post by ButteBlues on 2007-06-17
Kazehakase (sp?) supports an option to compile against Webcore. :)

---

### Post by juxtaposed on 2007-06-17
> **bonzodog said:**
> I have always wanted to find a browser that did not use the bloated gecko engine, and was fully gtk2 compatible.

Dillo was only gtk1.2, and has never been updated.

So, I decided to start my hunt by trying to find the other web engines available.

It got me to wondering what OSX was using, so a deeper look at Safari revealed the Open Source Webcore engine, which is in the process of being ported to [Gtk2]("http://gtk-webcore.sourceforge.net/")

Then, a further hunt revealed this:

[The Atlantis Web Browser]("http://www.akcaagac.com/index_atlantis.html")

I really think that Ubuntu/Canonical could push this a lot further and progress the port of the webcore Gtk engine, along with the Gnome team. A gnome web browser that used Webcore gtk2 as it's engine would be cool.

Currently, there is almost no Java support (although the gtk2-webcore homepage seems to hint that there is), and there is no flash support.

Great idea =)

I am trying to use Atlantis, but I get an error when I do it in the terminal:

atlantis: error while loading shared libraries: libnrcit.so.0: cannot open shared object file: No such file or directory

---

### Post by ButteBlues on 2007-06-17
> **juxtaposed said:**
> Great idea =)

I am trying to use Atlantis, but I get an error when I do it in the terminal:

atlantis: error while loading shared libraries: libnrcit.so.0: cannot open shared object file: No such file or directory
You have installed all the webcore stuff, yeah?

---

### Post by juxtaposed on 2007-06-17
> You have installed all the webcore stuff, yeah?

I just realised that there was a readme after I posted that (didn't show up in the archive, but it was there after I untared it) and it said to download it.

There are 4 different things to compile or something, and the readme doesn't explain it that well. I guess it's not worth my time unless it was easier :P

---

### Post by Extreme Coder on 2007-06-17
KHTML will be replaced by a QT port to WebKit in KDE 4 ;)

---

### Post by bonzodog on 2007-06-17
But I am talking about a GTK2 browser, not QT. 

It would be really nice to have a GTK Webcore browser.

---

### Post by tbroderick on 2007-06-17
> **bonzodog said:**
> But I am talking about a GTK2 browser, not QT. 

It would be really nice to have a GTK Webcore browser.

Kazehakase can use Webcore and GTK2.

---

### Post by pistooli on 2007-06-20
if it is still relevant,,, :-)

in Feisty...

apt-get install kazehakase

installs and works fine...

---

### Post by ButteBlues on 2007-06-20
> **pistooli said:**
> if it is still relevant,,, :-)

in Feisty...

apt-get install kazehakase

installs and works fine...
It's compiled against and uses Gecko in Feisty.

---

### Post by uggeli on 2007-06-25
I believe the future will bee webkit, instead of webcore (not saying that Mozilla will "die", or won't be the future but it's just another story). In [[color=blue]gtk-webcore-devel[/color]](http://sourceforge.net/mailarchive/forum.php?thread_name=460F8B38.50704%40iki.fi&forum_name=gtk-webcore-devel) there is mentioned:

[quote=Kimmo Kinnunen]
...This doesn't mean that I would encourage people to work on gtk-webcore
instad real port of current webkit to gtk...
[/quote]

And there is some [[color=blue]progress in webkit/gtk+[/color]](http://www.atoker.com/blog/2007/06/12/webkitgtk-is-coming/). Also intresting blog post to read: [[color=blue]Hubert Figuiere: Browser wars: a new hope[/color]](http://swik.net/GNOME/Planet+GNOME/Hubert+Figuiere%3A+Browser+wars%3A+a+new+hope/ba22x)

But sure if you want to use browser NOW, choice will is webcore until webkit gtk-port is finnished. I'm just typical user myself, allmost newbie. But I really can't wait to see Epiphany for example using webkit. :)

---

