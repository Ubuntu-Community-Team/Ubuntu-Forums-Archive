---
title: "Lost with jack audio server"
date: 2008-04-29
forum: Ubuntu Studio
---

### Post by kachofool on 2008-04-29
I have a Lenovo Thinkpad T61 with an Intel HDA soundcard.

I'm using Ubuntu Studio 8.04

I followed this guide to get Jack running:
[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

However once I get it running, no applications that have audio actually output anything. For example if I use Audacious with the Jack plugin and play a file, nothing actually happens. If I start up Hydrogen and try to play a drum loop, it's the same thing. I click play, nothing happens. It doesn't even indicate that something is playing, but nothing happens when I click play.

Is there a tutorial on how to use Jack? I'm pretty lost at this point.

---

### Post by warbread on 2008-04-30
When Jack is running,  you have to manually configure your inputs and outputs.  This is simple, though, with the use of Patchage.  Start Jack and open it up (Applications -> Sound & Multimedia -> Audio Production -> Patchage) and you'll get a graphical representation of all of your jack enabled programs.  

Connect blue boxes to blue boxes.  An output has its name justified to the right and an input has its name justified left.  Click on one and drag to the other to make a connection.

---

### Post by robeast on 2008-05-01
Patchage is great! Also check to make sure you have the prope hardware device selected in your jack settings, usually hw0 or something like that, but it may be another option on your system.

---

### Post by Stochastic on 2008-05-01
These issues could also be stemming from not having jack selected in audacious as your output sound server (would be in the preferences section of all sound apps).  But not having your software connected through jack is more likely.  You can also manage connection in qjackctl's connections window, but patchage is generally more feature-rich.

---

