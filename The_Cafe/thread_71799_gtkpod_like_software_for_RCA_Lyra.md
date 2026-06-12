---
title: "gtkpod like software for RCA Lyra?"
date: 2005-10-04
forum: The Cafe
---

### Post by macewan on 2005-10-04
Is there anything like gtkpod that can be used for the RCA Lyra? Something to read/write the the mp3 player - updating the playlist.

I've got an ipod, thanks aptsoft, but my wife has an RCA Lyra mp3 player.

---

### Post by poofyhairguy on 2005-10-04
Only this:

[http://usbat2.sourceforge.net/](http://usbat2.sourceforge.net/)

---

### Post by macewan on 2005-10-04
Thanks for the link, but I was actually asking about gnome software that would mimic the function of itunes, just as gktpod mimics itunes in that it provides a client to interface with the mp3 player

---

### Post by poofyhairguy on 2005-10-04
[QUOTE=macewan]Thanks for the link, but I was actually asking about gnome software that would mimic the function of itunes, just as gktpod mimics itunes in that it provides a client to interface with the mp3 player[/QUOTE]


Looking in Google I must ask:

Have you ever just tried plugging it in? Seeing waht happens?

---

### Post by poofyhairguy on 2005-10-04
And jsut thinking about it, I would try amarok. Sure its a KDE app, but its far superior to all Gnome apps to do that stuff. I like it better than gtkpod for my ipod.

---

### Post by somuchfortheafter on 2005-10-04
poofy did you do anything special to get amarok to work with your ipod... dont have mine available to try at the moment but i shall later...

---

### Post by poofyhairguy on 2005-10-04
[QUOTE=somuchfortheafter]poofy did you do anything special to get amarok to work with your ipod... dont have mine available to try at the moment but i shall later...[/QUOTE]


nothing in breezy amarok (gnome otherwise) just plug it in.

---

### Post by macewan on 2005-10-05
[quote=poofyhairguy]Looking in Google I must ask:

Have you ever just tried plugging it in? Seeing waht happens?[/quote]

sure, the file system is accessible no problem. transferring songs to the player is no problem. just like with the ipod. you can open a nautilus window & transfer the songs to the ipod but using gtkpod for the ipod is much cleaner. it allows for making playlist.

that's what we're search for in the case of the RCA Lyra, a nice gui program to transfer the songs and write playlist to the device. i could just use nautilus, but that's sorta sloppy.

---

### Post by poofyhairguy on 2005-10-05
[QUOTE=macewan]
that's what we're search for in the case of the RCA Lyra, a nice gui program to transfer the songs and write playlist to the device. i could just use nautilus, but that's sorta sloppy.[/QUOTE]

GTKPod exists because iPods don't act like standard USB devices. It was needed to get the ipods to work at first.

I'm pretty sure there isn't a Gnome program that does the same job for standard MP3 players. Since nautilus works, the community has left it at that. Maybe Banshee will be able do it one day.

In fact, the only thing I know close to what you want is Amarok. It works fine in Gnome.

---

### Post by macewan on 2005-10-06
Sounds good, thanks for your suggestions. I'm close to just giving her (wife) my ipod and I'll take the RCA

---

### Post by macewan on 2005-10-16
[http://meadowsonline.com/stereo/](http://meadowsonline.com/stereo/)


OK, this is what I was looking for -^

---

### Post by sword- on 2006-01-16
bump

Anyone had success with stereo or found any similar programs to manage your mp3 player? I currently have an RCA Lyra sport and when I run stereo I get this error message:

sword@ubuntu:~/stereo0.0.3$ stereo

** (/usr/lib/stereo/stereo.exe:7261): WARNING **: The following assembly referenced from /usr/lib/stereo/stereo.exe could not be loaded:
     Assembly:   gtk-sharp    (assemblyref_index=0)
     Version:    2.0.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/stereo).


** (/usr/lib/stereo/stereo.exe:7261): WARNING **: Missing method Init in assembly /usr/lib/stereo/stereo.exe, type Gtk.Application

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object

---

