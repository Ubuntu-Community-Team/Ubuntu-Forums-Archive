---
title: "Python GUI design"
date: 2006-04-07
forum: The Cafe
---

### Post by nocturn on 2006-04-07
I would like to start to make GUI Python programs for Gnome (I'm not sur if wxwidgets fit nicely).

I was searching for a good environment to do this is, is there an IDE that has both source code editing and a visual designer on board?

Most of the options I looked at are source code only.

---

### Post by ComplexNumber on 2006-04-07
try eric. it needs the qt toolkit, though. [here]("http://www.die-offenbachs.de/detlev/eric3.html")'s the link to the homepage. it also needs pyqt.

---

### Post by gord on 2006-04-07
qt isn't very nice
i use glade and gtk.

---

### Post by psychicdragon on 2006-04-07
Python + Glade is a very nice way to develop apps. The Glade Interface Designer is called glade-2 in apt, and you can use whatever editor you like best to write the code. There are a lot of people on these forums using these tools (search for "python glade" or "pygtk" in the Programming Talk forum).

---

### Post by engla on 2006-04-07
Pygtk and glade is very nice, it gives you gui interface editing. Glade even has code generation, but for what I know that is only for C and C++. Not a big deal, though, it's easy to handle in very little python anyway.

I don't know about any pygtk/python IDE though.

---

### Post by ComplexNumber on 2006-04-07
> Glade even has code generation
i thought that feature had been deprecated. developers are encouraged to use libglade instead.

---

### Post by christhemonkey on 2006-04-07
Pygtk all the way.  So simple, is just python!

---

### Post by psychicdragon on 2006-04-07
[QUOTE=ComplexNumber]i thought that feature had been deprecated. developers are encouraged to use libglade instead.[/QUOTE]
Yeah it is. The code generation feature is not included in glade-3.

---

### Post by LinuxGuy1234 on 2007-12-02
PyGTK all the way.
Here's the infamous "Hello World" sample:
```
#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import gtk

class HelloWorld:

    def delete_event(self, widget, event, data=None):
        return False

    def destroy(self, widget, data=None):
        gtk.main_quit()

    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.connect("delete_event", self.delete_event)
        self.window.connect("destroy", self.destroy)

        self.button = gtk.Button("Close this application")
        self.label = gtk.Label("Hello World! This is a PyGTK application, all in Python!")
        self.button.connect("clicked", lambda w:gtk.main_quit())
        self.window.add(self.box)
        self.button.connect(
        self.box.show()
        self.button.show()
        self.box.pack_start(self.button, False, False, 3)
        self.label.show()
        self.box.pack_start(self.label, False, False, 3)
        self.window.show()

    def main(self):
        gtk.main()

if __name__ == "__main__":
    hello = HelloWorld()
    hello.main()

```

---

### Post by machoo02 on 2007-12-02
[Stani's Python Editor]("http://pythonide.blogspot.com/search/label/spe") (SPE) will fit your bill.  Full-blown Python IDE that includes wxGlade along with it, so you can design GUI applications using wxWidgets.

---

### Post by bash on 2007-12-02
Any IDE directly for python and gtk/pygtk/glade. Stani's seems nice except for using wxwidgets. I think they look ugly in the GNOME GTK enviremont.

---

### Post by ssam on 2007-12-02
> **psychicdragon said:**
> Python + Glade is a very nice way to develop apps. The Glade Interface Designer is called glade-2 in apt, and you can use whatever editor you like best to write the code. There are a lot of people on these forums using these tools (search for "python glade" or "pygtk" in the Programming Talk forum).

there is glade-3 which is newer.

glade-3 removed code gerneration in favour of libglade.

this means that an xml file is made that describes the interface, and your program loads this as it starts. the old method where glade wrote a source code file has been depriciated.

---

### Post by pelle.k on 2007-12-02
I swear by pyqt and wxpython. pygtk feels a bit awkward if you ask me.
pygtk would probaly make better sense if you only want the bare essentials though, since qt and wxwidgets api:s deal with network connectivity and other stuff as well as gui design...

---

### Post by machoo02 on 2007-12-02
> **ubun-two said:**
> Any IDE directly for python and gtk/pygtk/glade. Stani's seems nice except for using wxwidgets. I think they look ugly in the GNOME GTK enviremont.I thought the whole point of wxWidgets was that it simply put wrappers around the native widgets of most environments (Win32, OS X, GTK, Motif, etc) so that you could easily write cross platform applications easily and quickly.  Everything that I've written in wxPython/wxWidgets and ran in Gnome looks *exactly like a native GTK application*.

---

### Post by jondecker76 on 2007-12-02
Glade3 and PyGTK all the way. Its a nice clean way to keep your interface and code spearate.

I personally use Glade3 for the UI and the Geany IDE for scripting. Its a nice combination to try out

---

### Post by pelle.k on 2007-12-02
> **machoo02 said:**
> I thought the whole point of wxWidgets was that it simply put wrappers around the native widgets of most environments (Win32, OS X, GTK, Motif, etc) so that you could easily write cross platform applications easily and quickly.  Everything that I've written in wxPython/wxWidgets and ran in Gnome looks *exactly like a native GTK application*.

You are correct - wxwidgets *are* gtk widgets really. ubun-two must have mixed it up with some other toolkit.

---

### Post by bash on 2007-12-02
I thougth so as well, but I swear I can remember a couple of applications look rather out of place. The had more or less the same style but it wasn't 100% the same as natvie GTK+ applications.

---

### Post by stani on 2008-01-14
> **bash said:**
> Any IDE directly for python and gtk/pygtk/glade. Stani's seems nice except for using wxwidgets. I think they look ugly in the GNOME GTK enviremont.

Do you think this looks ugly?
[IMG]http://photobatch.wikidot.com/local--files/getting-started/actions-scale.png[/IMG]

[IMG]http://photobatch.wikidot.com/local--files/getting-started/scale-round-shadow.png[/IMG]

These are screenshots of a new application I am developping with [SPE]("http://pythonide.stani.be"). It is called Phatch, which stands for Photo Batch Processor to manipulate all your pictures at once. It is similar to imagemagick, but with a nice (or should I say ugly?) graphical user interface. For more screenshots you can browse the tutorial: [http://photobatch.wikidot.com/getting-started](http://photobatch.wikidot.com/getting-started)

If you want to try it out, you can grab a deb installer at [http://photobatch.stani.be](http://photobatch.stani.be) > free download.

wxPython just uses GTK on linux, so you won't see the difference. (Unless the application is using an older version of wxpython which uses an older version of gtk.) You only have the advantage that it can also run on Mac Os X and Windows... for free!

Stani

---

### Post by forrestcupp on 2008-01-14
If you're creating programs for Gnome, like you said in your OP, please don't use PyQt.  Qt is good for KDE apps.

I like wxWidgets, but I've used PyGTK, too.  I actually used PyGTK in SPE without any trouble.

---

### Post by Tundro Walker on 2008-01-14
I've been looking into doing some Python GUI, too, but I was hoping to have something cross-platform compatible, which could run on Windows & Linux.  Won't using PyGTK limit the GUI to just Linux/Gnome?

EDIT: As a side note, I don't really like how python Qt gui's look.  They're kind of scrunched and ugly.  I guess wxWidgets, then?

---

### Post by 23meg on 2008-01-14
[QUOTE=Tundro Walker]Won't using PyGTK limit the GUI to just Linux/Gnome?[/QUOTE]

From [http://pygtk.org](http://pygtk.org) :

> PyGTK applications are truly multiplatform and they're able to run, unmodified, on Linux, Windows, MacOS X and other platforms.


(Side note: GTK isn't bound to GNOME, and GNOME isn't bound to Linux.)

[QUOTE=Tundro Walker]EDIT: As a side note, I don't really like how python Qt gui's look.[/QUOTE]

Can you cite examples, if possible with screenshots?

---

