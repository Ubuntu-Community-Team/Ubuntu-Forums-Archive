---
title: "Totem"
date: 2007-12-17
forum: The Cafe
---

### Post by Johnny3 on 2007-12-17
Why doesn't Totem come with mplayer installed? I am new to Ubuntu and tried all kind of things before I found it was as easy as installing mplayer in SPM and clicking mplayer to get it to play mpg files. 
Thanks Johnny3
Gainesville Fl
60+++ and get away from ms.

---

### Post by -grubby on 2007-12-17
I'd assume legal issues (e.g. with proprietary codecs,etc..)

---

### Post by bruce89 on 2007-12-17
Totem can play MPEG files if the right codecs are installed:

gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse

---

### Post by Nano Geek on 2007-12-17
> **bruce89 said:**
> Totem can play MPEG files if the right codecs are installed:

gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverseOr just```
sudo apt-get install ubuntu-restricted-extras
```That will get you just about everything you need.

---

### Post by Presto123 on 2007-12-17
FYI: I just installed Amarok and like it much better. It will take a bit of space, but is pretty nice.

It runs just fine on Gnome, too.

---

### Post by Presto123 on 2007-12-17
> **asjdfwejqrfjcvm msz34rq33 said:**
> Or just```
sudo apt-get install ubuntu-restricted-extras
```That will get you just about everything you need.

Actually, I had to install these things separately both on 7.04 and 7.10.

---

### Post by bruce89 on 2007-12-17
> **asjdfwejqrfjcvm msz34rq33 said:**
> Or just```
sudo apt-get install ubuntu-restricted-extras
```That will get you just about everything you need.

Indeed, but it depends on other things that aren't useful here.

---

### Post by tuebinger on 2007-12-18
> **asjdfwejqrfjcvm msz34rq33 said:**
> Or just```
sudo apt-get install ubuntu-restricted-extras
```That will get you just about everything you need.

Thanks for this!  Now I can play my video files on Ubuntu.  I was beginning to give up hope.
:)

---

