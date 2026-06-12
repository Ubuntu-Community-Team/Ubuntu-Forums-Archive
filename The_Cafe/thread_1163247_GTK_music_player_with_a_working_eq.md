---
title: "GTK music player with a working eq?"
date: 2009-05-18
forum: The Cafe
---

### Post by swoll1980 on 2009-05-18
Anyone find one yet? Has there been one all along that I've over looked?

---

### Post by mc4100 on 2009-05-18
> **swoll1980 said:**
> Has there been one all along that I've over looked?
Banshee, for quite a [while]("http://banshee-project.org/download/archives/1.2.0/").

---

### Post by Regenweald on 2009-05-18
Exaile , QMMP also

---

### Post by dragos240 on 2009-05-18
What about rhythmbox?

---

### Post by mc4100 on 2009-05-18
> **dragos240 said:**
> What about rhythmbox?
There's an [unofficial plugin]("http://cs.helsinki.fi/u/ttokalli/rb-plugins/").

---

### Post by swoll1980 on 2009-05-18
> **Regenweald said:**
> Exaile , QMMP also

> **mc4100 said:**
> There's an [unofficial plugin]("http://cs.helsinki.fi/u/ttokalli/rb-plugins/").

Any eq that requires gstreamer good plugins doesn't seem to work.

---

### Post by swoll1980 on 2009-05-18
> **mc4100 said:**
> Banshee, for quite a [while]("http://banshee-project.org/download/archives/1.2.0/").

Thanks I will try this

---

### Post by swoll1980 on 2009-05-18
> **mc4100 said:**
> Banshee, for quite a [while]("http://banshee-project.org/download/archives/1.2.0/").

The Eq doesn't do anything in Banshee either. This is the same as rhythmbox, and exaile. That's why I said one that works, because these haven't worked in the past.

---

### Post by steeleyuk on 2009-05-18
[Listen]("http://www.listen-project.org/")? Not sure if it works though as I haven't tried it.

Its also another one that use Gstreamer...

---

### Post by dragos240 on 2009-05-18
why don't you use gstreamer, it comes by default with ubuntu. Or do you use something else like arch.

---

### Post by Wiebelhaus on 2009-05-18
> **swoll1980 said:**
> The Eq doesn't do anything in Banshee either. This is the same as rhythmbox, and exaile. That's why I said one that works, because these haven't worked in the past.

Something is up with your audio setup then , they all work fine here.

---

### Post by swoll1980 on 2009-05-18
> **Wiebelhaus said:**
> Something is up with your audio setup then , they all work fine here.

The eq in amarok works fine for some reason. I don't want install all those qt libraries for one app though.

---

### Post by RiceMonster on 2009-05-18
It works in Banshee and gmusicbrowser (if you use gstreamer rather than the other two backends available) in my experience. However, I really can't stand Banshee and gmusicbrowser would lock my sound card and not allow anything else to make sound for some reason, and required tons of Perl dependencies which was kind of annoying.

Audacious also has a working EQ, but that's only sort-of GTK, as the main window is a skinned UI. There's also no music library, which may or may not annoy you.

> **Regenweald said:**
> Exaile , QMMP also

Exaile's doesn't work in my experience.

> **swoll1980 said:**
> The eq in amarok works fine for some reason. I don't want install all those qt libraries for one app though.

I know how you feel. I really want to get rid of amarok, but I can't. I'm using mpd more and more because there's a lot of things that sound fine without an EQ, but some I can't listen to. I'm adjusting to it.

---

### Post by swoll1980 on 2009-05-18
> **RiceMonster said:**
> It works in Banshee and gmusicbrowser (if you use gstreamer rather than the other two backends available) in my experience. However, I really can't stand Banshee and gmusicbrowser would lock my sound card and not allow anything else to make sound for some reason, and required tons of Perl dependencies which was kind of annoying.

Audacious also has a working EQ, but that's only sort-of GTK, as the main window is a skinned UI. There's also no music library, which may or may not annoy you.



Exaile's doesn't work in my experience.



I know how you feel. I really want to get rid of amarok, but I can't. I'm using mpd more and more because there's a lot of things that sound fine without an EQ, but some I can't listen to. I'm adjusting to it.

I find myself using Ubuntu less now just because of the audio quality of my music. I have the SRS audio sandbox for Windows, and that thing is pretty amazing. When I boot Ubuntu I don't even have an Eq :-(

---

### Post by RiceMonster on 2009-05-18
foobar2000 is the one Windows program I really wish I had on Linux. Wine isn't an option, because it crashes and I try to avoid using wine as much as possible.

---

### Post by BoyOfDestiny on 2009-05-18
[http://audacious-media-player.org/](http://audacious-media-player.org/)

2.01 is out, which has support for an alternative interface (if you don't like the winamp/xmms style). The Ubuntu repos have the older stable release.

---

### Post by swoll1980 on 2009-05-18
> **RiceMonster said:**
> foobar2000 is the one Windows program I really wish I had on Linux. Wine isn't an option, because it crashes and I try to avoid using wine as much as possible.

I like the way the interface looks on that one. I will have to try it out. I'm using Media Monkey right now. While it has alot of features I'm not to crazy about the "Amarok like" interface it has.

---

### Post by swoll1980 on 2009-05-18
> **BoyOfDestiny said:**
> [http://audacious-media-player.org/](http://audacious-media-player.org/)

2.01 is out, which has support for an alternative interface (if you don't like the winamp/xmms style). The Ubuntu repos have the older stable release.

I guess I'm going to go ahead, and compile this one, and see what I get.

---

### Post by RiceMonster on 2009-05-18
SO I just compiled audacious2. How do you enable the alternate interface?

Ok, so you can launch it like: audacious2 -i newui

Now to see if there's an option to regularly enable it in a config file or something. Also, doesn't seem to be an EQ in this ui.

---

### Post by swoll1980 on 2009-05-18
> **RiceMonster said:**
> SO I just compiled audacious2. How do you enable the alternate interface?

Ok, so you can launch it like: audacious2 -i newui

Now to see if there's an option to regularly enable it in a config file or something. Also, doesn't seem to be an EQ in this ui.

I will hold off on the compilation until I get a confirmation on the Eq, as that is the whole purpose of this exercise

---

### Post by RiceMonster on 2009-05-18
> **swoll1980 said:**
> I will hold off on the compilation until I get a confirmation on the Eq, as that is the whole purpose of this exercise

Yeah may as well. I don't think the new UI is feature complete yet. You can only get the EQ if you use the skinned UI.

---

### Post by swoll1980 on 2009-05-18
> **RiceMonster said:**
> SO I just compiled audacious2. How do you enable the alternate interface?

Ok, so you can launch it like: audacious2 -i newui

Now to see if there's an option to regularly enable it in a config file or something. Also, doesn't seem to be an EQ in this ui.

just add that command to the menu entry to get it to launch like that every time

---

### Post by swoll1980 on 2009-05-18
> **RiceMonster said:**
> Yeah may as well. I don't think the new UI is feature complete yet. You can only get the EQ if you use the skinned UI.

mine won't run unless I use the new ui for some reason

---

