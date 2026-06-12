---
title: "Pulseaudio for.. video"
date: 2009-05-02
forum: The Cafe
---

### Post by carl689 on 2009-05-02
I find myself in the situation where I want to "throw" video to devices.  
Ex: On my laptop in the living room and want to show up on the living room tv.
Ex 2:I want to be able to "show" my roomate my firefox window when he is in a different room.

Now I know, or at least think I know, that bandwidth would be a huge issue/3d Acceleration/etc.. but doesn't this seem like a direction it should be going?? It seems like this should be being worked on somewhere.  I attempted to google it but didn't find anything.

I am not exactly a Linux Guru but doesn't X already kinda have this ability? I know i can do "ssh -X", in which case it would be writing tools?

Thoughts? Am I being nuts? To much rambling?

---

### Post by GrouchoMarx on 2009-05-02
Gstreamer has the potential to do this. Unfortunately the implementation for video streaming changes depending on what you want to stream (ie: screencast, file, etc...), and so far only a limited number of gstreamer modules have been written.

[Introducing Gstreamer]("http://www.cin.ufpe.br/~cinlug/wiki/index.php/Introducing_GStreamer")

---

### Post by carl689 on 2009-05-02
In regards to what you would want to stream, I would think it would break up into

- Specific Applications
- Desktop/Screencast

A applet *slightly* similar to the padevchooser/volume control could let you pick whats going where/etc

I will give that gstreamer page a read, thanks.

---

