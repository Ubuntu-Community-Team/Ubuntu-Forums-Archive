---
title: "Post Your Awn Settings Here!"
date: 2007-03-25
forum: The Cafe
---

### Post by BOBSONATOR on 2007-03-25
Please Attach sceenshots of your settings, and upload your patterns.

Here is mine, its horrible cause i have no pattern,

Heres a good [HOWTO]("http://ubuntuforums.org/showthread.php?t=385929")

---

### Post by karellen on 2007-03-25
what is Awn?

---

### Post by dbbolton on 2007-03-25
> **karellen said:**
> what is Awn?
avant window manager, from google code.

i installed it but (in my case) it is too buggy to be usable.

---

### Post by maniacmusician on 2007-03-25
> **dbbolton said:**
> avant window manager, from google code.

i installed it but (in my case) it is too buggy to be usable.
I believe it's avant window **navigator**, hence the acronym AWN. I haven't tried it yet...is it gnome-centric?

---

### Post by karellen on 2007-03-25
ok, now I see...:D

---

### Post by dbbolton on 2007-03-25
> **maniacmusician said:**
> I believe it's avant window **navigator**, hence the acronym AWN. I haven't tried it yet...is it gnome-centric?
my bad

notice how it cuts off the bottom of the screen, and the glass engine doesn't work. maybe i can blame ATI for this.

[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/th_awn.jpg[/IMG]](http://i103.photobucket.com/albums/m128/envyouraudience/awn.jpg)

---

### Post by BOBSONATOR on 2007-03-26
comon guys, i know you awn users are out there!

---

### Post by stalker145 on 2007-03-26
> **dbbolton said:**
> my bad

notice how it cuts off the bottom of the screen, and the glass engine doesn't work. maybe i can blame ATI for this.

[[IMG]http://i103.photobucket.com/albums/m128/envyouraudience/th_awn.jpg[/IMG]](http://i103.photobucket.com/albums/m128/envyouraudience/awn.jpg)

I know it's only been a day, but I just stumbled across this, thought it was cool, and jumped right in with the same problem that you had. Any fix found on your end?

---

### Post by BOBSONATOR on 2007-03-27
have you guys compiled by svn>?

Check the howto i posted above in the first post.

---

### Post by dbbolton on 2007-03-27
> **stalker145 said:**
> I know it's only been a day, but I just stumbled across this, thought it was cool, and jumped right in with the same problem that you had. Any fix found on your end?
no fix found yet (by me, that is. i haven't really been looking :/ )

---

### Post by Kujen on 2007-03-27
I just installed it and love it.. but one question. Is there a way to make it so windows like firefox (when maximized) don't go under AWN, but instead STOP right at the top of AWN? Just a little annoying having to resize firefox everytime, or have a bunch of buttons at the bottom of the window, covering content.

---

### Post by BOBSONATOR on 2007-03-27
Maybe in a future release Kujen,

---

### Post by stalker145 on 2007-03-27
> **BOBSONATOR said:**
> have you guys compiled by svn>?

Check the howto i posted above in the first post.

Yes, I installed using the SVN method described

> Avant-Window-Navigator (svn):
First install the dependencies:

Code:
```
sudo apt-get install build-essential autotools-dev libgnome-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf subversionNow, open a terminal in the directory you want to build AWN in (I use ~/Installs/avant/) 
```

and do this:

Code:
```
svn checkout [http://avant-window-navigator.googlecode.com/svn/trunk/](http://avant-window-navigator.googlecode.com/svn/trunk/) avant-window-navigator
cd avant-window-navigator
./autogen.sh
make
sudo make install
```

I then ran AWN from the menu entry and encountered the issue. It's not that big of a deal, but it was pretty and I was hoping to add that to my desktop. I can either wait for a fix (since I'm a coding moron) or wait until I get a better lappytoppy :)

Thanks for the advice, though.

---

