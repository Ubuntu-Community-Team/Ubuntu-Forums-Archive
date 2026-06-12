---
title: "remote desktop through browser?"
date: 2007-05-11
forum: The Cafe
---

### Post by PartisanEntity on 2007-05-11
Are there any remote desktop solutions that work through the browser?

---

### Post by PartisanEntity on 2007-05-13
Judging by the lack of responses and the fact that I could not find anything by searching the forum or search engines it would seem nothing like this exists for Linux?

---

### Post by reacocard on 2007-05-13
I think there's a java applet for VNC you might be able to use, but that's about it.

---

### Post by maagimies on 2007-05-13
> **reacocard said:**
> I think there's a java applet for VNC you might be able to use, but that's about it.That applet works quite well, I highly recommend it.

---

### Post by PartisanEntity on 2007-05-13
Thanks for the info, I found a vnc java applet in the repos, I am assuming that's the one? How exactly does it work?

---

### Post by mattyh on 2007-05-13
Check out logmein.com, it's a great solution though not for logging into a linux computer.  I'm pretty sure it only works for logging into windows computers so it may not be what you're looking for.

---

### Post by reacocard on 2007-05-13
> **mattyh said:**
> Check out logmein.com, it's a great solution though not for logging into a linux computer.  I'm pretty sure it only works for logging into windows computers so it may not be what you're looking for.

Yep, windows only. Works great for windows though.

---

### Post by PartisanEntity on 2007-05-13
> **mattyh said:**
> Check out logmein.com, it's a great solution though not for logging into a linux computer.  I'm pretty sure it only works for logging into windows computers so it may not be what you're looking for.

Actually that is what made me ask whether there was something similar for Linux, it would be great if I could point a browser at my ip number and then be able to access my computer through it.

---

### Post by reacocard on 2007-05-13
> **PartisanEntity said:**
> Actually that is what made me ask whether there was something similar for Linux, it would be great if I could point a browser at my ip number and then be able to access my computer through it.

That's kinda what VNC + Java Applet does. The applet is served from your computer, loads and then connects back to your computer's VNC server.

Alternatively, you could just put the VNC viewer on a USB drive and run it as a portable app.

---

### Post by PartisanEntity on 2007-05-13
> **reacocard said:**
> That's kinda what VNC + Java Applet does. The applet is served from your computer, loads and then connects back to your computer's VNC server.

Sounds great, are there any screenshots of what this will look like? I just want to get an idea before I install it.

> **reacocard said:**
> Alternatively, you could just put the VNC viewer on a USB drive and run it as a portable app.

hmm this also sounds good and might be safer than using the java applet since this applet would allow anyone with a browser to be able to connect, whereas without the applet I assume someone would have to first install the vnc application (just added hassle).

Any good HowTos for installing the client on usb stick?

---

### Post by reacocard on 2007-05-13
> **PartisanEntity said:**
> Any good HowTos for installing the client on usb stick?

Download the .zip of "VNC Free Edition Viewer for Windows" from [RealVNC]("http://www.realvnc.com/"). Extract zip to drive. Double-click to run.

The downside to this method it that it only works on Windows computers that have a USB port you can use. Fortunately(?), those are very common these days.

---

### Post by PartisanEntity on 2007-05-13
cool thanks, ill give it a try from work tomorrow :)

---

### Post by PartisanEntity on 2007-05-14
hmm how exactly does the vnc java applet work? I installed it through Synaptic. I also went to System > Preferences Remote Desktop in order to enable remote access.

But when I point my browser from another computer at my ubuntu laptop I get an error message that the page cannot be found.

*I am a little confused, this vnc applet is only for tightvnc? or are vnc and tightvnc the same thing?*

---

### Post by stalker145 on 2007-05-14
> **PartisanEntity said:**
> hmm how exactly does the vnc java applet work? I installed it through Synaptic. I also went to System > Preferences Remote Desktop in order to enable remote access.

But when I point my browser from another computer at my ubuntu laptop I get an error message that the page cannot be found.

*I am a little confused, this vnc applet is only for tightvnc? or are vnc and tightvnc the same thing?*

Not knowing anything about the Java-VNC, my first question is, if you have a router at home, did you forward the appropriate ports in said router?

---

### Post by PartisanEntity on 2007-05-14
Yes I am behind a router and yes I did forward the port. I have gotten so far that if I point my brothers IE browser (he is using XP) at my computer I get 'RFB 003.007' but nothing else happens. (I thought the java applet was supposed to load automatically)

---

### Post by reacocard on 2007-05-14
> **PartisanEntity said:**
> Yes I am behind a router and yes I did forward the port. I have gotten so far that if I point my brothers IE browser (he is using XP) at my computer I get 'RFB 003.007' but nothing else happens. (I thought the java applet was supposed to load automatically)

I don't think it's served by default, if it is it'll be port 5900 I think, so try going to<compuer's IP>:5900 in your browser. Otherwise, install nmap on the VNC computer and do
```
nmap localhost
```
to see what ports are open. If the java applet hasn't opened a port for itself, you'll have to set up an http server for it. 

You should probably just use the USB drive method, it's a lot less hassle.

---

### Post by PartisanEntity on 2007-05-14
> **reacocard said:**
> 
You should probably just use the USB drive method, it's a lot less hassle.

I think that's what ill do for now :)

---

