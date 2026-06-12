---
title: "Microsoft's Silverlight"
date: 2008-08-09
forum: Ubuntu Brainstorm
---

### Post by lsutiger on 2008-08-09
I was pumped about watching the HD web vids for the olympic opening ceremonies on NBC's olympic page, until I was b**ch slapped by microsoft.

Ya think we'll ever have a plugin developed in order to watch this video?
Is there anything in the works?

---

### Post by tvtech on 2008-08-09
if you develop it it will happen and they will come.

---

### Post by adewale on 2008-08-09
I've read of silverlight for linux. The project started at a coding festival. Try googling

---

### Post by .nedberg on 2008-08-09
[Moonlight]("http://www.mono-project.com/Moonlight")

---

### Post by damoxc on 2008-08-10
[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

---

### Post by skullmunky on 2008-08-12
There's a thread somewhere else around here with a method for watching the olympics using vlc or mplayer.  It involves running a python script to get the schedules and pull out the addresses for the video streams, which you then paste into vlc.  And it works!  (Though sometimes audio problems.)

---

### Post by gjoellee on 2008-08-12
silverlight is just a bad thing made by Microsoft

---

### Post by Slug71 on 2008-08-12
You mean just another bad thing, just like everything else!

---

### Post by irrdev on 2008-08-19
> **gjoellee said:**
> silverlight is just a bad thing made by Microsoft
I disagree. The Silverlight technology itself has potential. It is the philosophy and "copy-cat" approach behind Silverlight that is to be condemned. How many Microsoft products/technologies have been spinoffs of another successful product? Hmmm... just to name a few: Windows (Mac), multitasking (UNIX), .NET (Java), and now Silverlight! No wonder why the EU has found problems with Microsoft's business approach!

---

### Post by gnomeuser on 2008-08-19
> **lsutiger said:**
> I was pumped about watching the HD web vids for the olympic opening ceremonies on NBC's olympic page, until I was b**ch slapped by microsoft.

Ya think we'll ever have a plugin developed in order to watch this video?
Is there anything in the works?

Novell has an entire team working on this, they are already Silverlight 1 compatible to a very acceptable degree. Thanks to their business relationship with Microsoft they have access to the Silverlight compliance test which means the Moonlight implementation will eventually be 100% spot on.

Additionally Microsoft has agreed to provide a licensed codec pack for use with Silverlight (only as a browser plugin though), for which they pay the licensing cost for everyone so you end up have equal functionality at no cost. Alternatively you can compile moonlight against ffmpeg but then you know it has to go into the universe repo and can't be installed by default for reasons of patent stupidity. There is also work porting Moonlight to gstreamer which would allow us to install it and have codec issues worked out post install the same way we do with media support in totem now.

As for the specific case of the olympic site one of the moonlight hackers recently posted on this here:

[http://jeffreystedfast.blogspot.com/2008/08/moonlighting-olympics.html](http://jeffreystedfast.blogspot.com/2008/08/moonlighting-olympics.html)

As can be seen, it's not quite there yet but they are working on it. For now you will have to live without it. Sorry.

This LUGRadio Live talk by Miguel might shine some light on where Moonlight will be helpful to us outside of the browser, like giving us ultrablingy applications easily.

[http://blip.tv/file/get/Geeko-MigeulDeIcazaTalksAboutMono483.ogg](http://blip.tv/file/get/Geeko-MigeulDeIcazaTalksAboutMono483.ogg)

---

