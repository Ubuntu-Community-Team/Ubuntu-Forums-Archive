---
title: "sluggish windows"
date: 2006-09-08
forum: The Cafe
---

### Post by NoTiG on 2006-09-08
Just wondering... im on  an athlon 64 3000 with 1.2 GB of ram ... and the windows when imove them they stutter and i get fragments all over. WHy is the windowing system so slow ? its so bad... that if i take hold of a window and move it in little circles my computer will grind to a halt if i keep it up. Is it metacities fault? will this ever be fixed???

---

### Post by PatrickMay16 on 2006-09-08
Whatever.

---

### Post by Brunellus on 2006-09-08
Might be a video driver issue.  I second the comment.

---

### Post by NoTiG on 2006-09-08
I read somewhere that its because in windows they windows are "buffered" in memory or something. Wherea i guess they are continuously redraw in linux. Im using an ati radon 9600... and i have the open drivers running DRI. are you sure it has to do with my video driver ? since we are talking 2d here. Your windows dont get distorted when you hold them and move them around real fast ?

---

### Post by .t. on 2006-09-08
I'm very sorry to say this (free software and all), but it's the fault of the driver.

---

### Post by NoTiG on 2006-09-08
i dont think its the driver. whether i use mesa, Dri, or the ati binary it does this. i think this is a known problem with metacity. The redraw problem when windows are moved is because its not buffered or something.

---

### Post by %hMa@?b&lt;C on 2006-09-08
i have the same problem, I believe this is a known metacity problem, try using iceWM if you want to test it for yourself.

---

### Post by NoTiG on 2006-09-08
I found my answer! 

> You are wrong. The visible application redraw, either during expose or
configure events, is very much a synchronization issue.  Sure redrawing
at light speed would eliminate the symptom, but it wouldn't address the
problem (and it would be very inefficient anyway).

Sure Xcalc redraws itself fast enough so as not to have visible
redrawing because the ops are very simple.  However, most of the time on
my fast nvidia graphics card and machine I can't see GTK apps redraw
either.  GTK is orders of magnitude more complicated and intensive that
the Xaw widgets.  GTK widgets are all dynamically sized on the fly.
That is one reason why GTK may be slower to redraw than Xaw.  But Xaw is
not very useful and you wouldn't want to make a full app out of it.

Back to synchronization.  The problem is that as you rapidly move one
window past another, or resize a window, the events queue up and ask the
app to redraw.  However the redraw app will likely have to happen all
over again before redraw is finished. So GTK queues up the events,
halting the redraw momentarily.  The upshot of this is that you save a
lot of CPU and in the end redraw faster (cause you're only doing it 5
times instead of 1000), but there is visible stutter.  If the redraw
events and the movement of the windows are synchronized according to a
frame rate, everything does get smoother.  The biggest win here is
resizing a window.  With the proposed X11 synchronization extension
stuff (as I understand it), GTK app resizes will be silky smooth (well
at a frame-rate your computer can handle CPU-wise).  

Here is a quote from an unknown source that explains it better: "Because
X11 is asynchronous, as the window resizes, configure and expose events
are sent to the GTK widgets to get them to redraw. Because of this
asynchronous nature, until recently there was no good way to synchronize
the redrawing to the actual expanding of the window, as OS X and Windows
do. This is changing and a synchronization mechanism is being built into
X11 that will allow Gtk (and Qt and any other widget set) to be able to
resize fluidly."

In answer to your original question, GTK apps are double-buffered at the
widget level, not the window-contents level.  Xgl and AIXGL (composite
generally) make all apps "double-buffered" at the window level,
eliminating expose redraws entirely, speeding up every window operation
except resize, which still depends on the speed at which the widgets can
dynamically resize.  

Once Xgl and AIXGL become widespread, and the synchronization mechanism
is released, I doubt you'll find anyone complaining about GTK speed.
It's been shown on this list and in other places to largely be a
perception issue.

---

### Post by .t. on 2006-09-09
I don't know why your problems would not affect others, since most people are more likely than not using the same versions of Mesa and Xorg, GTK+ and Metacity as you. Your only difference is the driver. And please don't insult me.

Double-buffering is likely to make applications slower, as the GPU does everything, effectively, twice. Synchronisation is not the same thing. What that means is whether windows are drawn in sync with the refresh rate, so that the screen doesn't have to do extra drawing, or not. In Mac OS X, there is a GUI option to turn this on or off. I don't know of one such in X, although I am sure it exists. Turn it off, and you will soon notice a difference.

---

### Post by NoTiG on 2006-09-09
> **.t. said:**
> I don't know why your problems would not affect others, since most people are more likely than not using the same versions of Mesa and Xorg, GTK+ and Metacity as you. Your only difference is the driver. And please don't insult me.



Well assuming that nobody else had that problem then i guess you might be on to something. But im pretty sure most everyone experiences this. Click your window and drag it around in circles fast and see if you see any graphical errors.

Anyways..... i am sure its not my video driver because with system monitor up my cpu spikes to 100% utilization. So its either Gtk or x11 or metacity.

---

### Post by .t. on 2006-09-09
Is DRI turned on? I don't really know why it would make much difference, but you never know: try ```
glxinfo | grep direct
```

---

### Post by argie on 2006-09-09
I dunno, but I don't have anything other than my pitiful on-board card, and I don't even have a dual processor but my CPU barely grumbles spinning windows around (GIMP, Picasa, firefox, OO:Impress).

Heck, I don't even have Direct Rendering on.


That is to say, I do not have your problem. Perhaps it is specific to your system.

---

### Post by kopilo on 2006-09-09
I have an AMD Athlon 64 3000+
and 512MB of ram and only experience this issue when executing 32bit applications...

Are you using the 32bit version of Ubuntu? Maybe try the 64bit version.. Other then that I don't know.

---

### Post by Reshin on 2006-09-09
a) Drivers
b) Your videocards busted
c) Try running sudo dpkg-reconfigure xserver-xorg again

---

### Post by PatrickMay16 on 2006-09-09
> **NoTiG said:**
> Well assuming that nobody else had that problem then i guess you might be on to something. But im pretty sure most everyone experiences this. Click your window and drag it around in circles fast and see if you see any graphical errors.

Anyways..... i am sure its not my video driver because with system monitor up my cpu spikes to 100% utilization. So its either Gtk or x11 or metacity.

I have never had any such problem, not even before I replaced my old Radeon 9000 with an Nvidia card. I tried quickly moving a window around as you said. I did it over other windows, too. The CPU usage meter showed around 50% CPU usage while doing this. Though when I resized windows (the windows I tried were Nautilus and Firefox), the CPU usage was 100%. Though things were still quick and pretty smooth. While moving the windows around or resizing them, I didn't notice any "graphical errors".

Maybe you're very sensitive to this kind of thing. Hmm...

Well, would you do me a favour? Try using the "vesa" driver just to test this out, and while using the vesa driver move windows around and resize them in the way that you say causes the problem.
After you've done that, did you notice any difference between the performance of the "vesa" driver and the performance of the drivers you usually use?

---

### Post by NoTiG on 2006-09-09
hmmm. i guess its a good thing that it sounds like im the only one then. Alright i will try those drivers, and yes btw I am using the 32 bit dapper on 64 bit amd

---

