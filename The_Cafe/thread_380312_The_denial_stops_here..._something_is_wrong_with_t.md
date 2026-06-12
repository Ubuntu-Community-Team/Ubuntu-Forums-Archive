---
title: "The denial stops here... something is wrong with the windowing system"
date: 2007-03-09
forum: The Cafe
---

### Post by NoTiG on 2007-03-09
there is some bad code that results in jagged windows... when you click and hold them and move them around.

I have tried this on decent hardware... i have tried it on modern hardware with dual core processors

I have tried this with nvidia cards... i have tried it with ATI cards

I have tried it with open source drivers... i have tried it with properly installed official binary drivers

and it ALWAYS is the same... the CPU usage spikes when you move windows around. In fact it is so bad that if you simply hold the window down and move it in slow circles.... the computer becomes completely locked up and unusable momentarily. That is on a computer with 2 GB of ram... an athlon x2 4400 etc... i have also tried it on 3 different computers.

It is NOT a visual glitch or synchronization error... because that does not explain the CPU usage spiking to 100 %.

I don't know where the problem is... but i am worried that with the switch over to 3d desktops.... the code will remain because people won't notice it as much anymore with the additional power of the graphics card drawing the desktop.

So the code is either in Gnome, the metacity window manager.... xorg... or somewhere. But i hope someday it gets fixed . I posted a youtube video in case you had no idea what im talking about:

[//www.youtube.com/watch?v=8gh7ABSs1NY]("//www.youtube.com/watch?v=8gh7ABSs1NY")

edit: btw, windows doesn't have this problem

---

### Post by ~LoKe on 2007-03-09
While I can't say the movement quality is anything amazing, I can at least say that on my end the CPU usage never jumps to 100%, and certainly never passes xorg (at ~22).

---

### Post by hizaguchi on 2007-03-09
Yeah, I just tried this and, though it does work the CPU harder than normal, I'm not seeing the problem you describe.

---

### Post by Tomosaur on 2007-03-09
Yeah same here - completely unrepeatable. I don't even get any kind of unreasonable spiking.

---

### Post by DoctorMO on 2007-03-09
It's a screen refresh problem, and yes it does happen in windows when you have either a crashed app or a locked desktop. the problem here is that it's not locked it's just very very busy.

Have you run diagnostics with top and a few other apps to see what is going on?

---

### Post by Phatfiddler on 2007-03-09
Hmm, I cant repeat it either, in Gnome/Metacity or KDE/Konqueror.  This is on a laptop, Radeon 7500 and Pentium M 1500MHz Processor.....  I dont even get close to 100%.

---

### Post by banjobacon on 2007-03-09
Try doing this without Firefox running. This only happens to me when Firefox is running behind the window I'm moving. I suspect it's a Firefox/XUL thing.

---

### Post by Phatfiddler on 2007-03-09
Well if you throw Firefox into the equation, yes I have issues, and always have.  I have made several posts about this and so far havent found a solution.  You can actually use Firefox as a drawing pad if you like!  Try dragging a desktop icon around on the firefox window and you'll see what I mean.

---

### Post by DoctorMO on 2007-03-09
Well firefox is known for being slow, but the slow clipping processing is a concern. a quick test shows at least a 300ms delay between clear and repaint; what is suposed to happen is that when a window moves the image of what was behind it is stored some place and repainted in a double blit (you got to paint back the window you moved too) but if you have to generate the content again then this takes time, the slower the render the slower the performance.

A 3D desktop should solve this problem because each window is a polygon in the video card memory and it's the video card that handles redrawing the behinds of windows for you.

But that doesn't help us with 2d desktops, perhaps there is an option in xorg compile that discards the image behind windows in order to save memory?

---

### Post by prizrak on 2007-03-09
I think nVidia's proprietary driver with RenderAccel option would take care of it. I don't remember that happening back when I was on the lowly 2D desktop though. Is it just one version that is affected?

---

### Post by KaroSHiv0n on 2007-03-09
i just tried 2 of the things from this thread, 
1. dragging a window around in cirlces, my cpu (amd 64bit 3200+ ) hit 57%
2. dragging a icon around firefox - nothing happend.
i have a nvida card with drivers installed via the envy driver if this helps.

---

### Post by macogw on 2007-03-09
With Beryl and moving rather wobbly windows around quite a bit, my CPU usage stays down around 30%.

---

### Post by DoctorMO on 2007-03-09
Beryl is a 3d desktop

---

### Post by Phatfiddler on 2007-03-09
Hmm, I'm using the stock drivers.  To give you an idea...I installed Kubuntu, and thats it!  Everything is stock in every other sense (except for music codecs and other software that doenst affect the video).  I could try the prop. drivers and see if it persists.  The original poster has had issues with different drivers, so maybe that isnt the cause.

---

### Post by tacm on 2007-03-09
> **Phatfiddler said:**
> Well if you throw Firefox into the equation, yes I have issues, and always have.  I have made several posts about this and so far havent found a solution.  You can actually use Firefox as a drawing pad if you like!  Try dragging a desktop icon around on the firefox window and you'll see what I mean.
Just one more reason not to use Fire Fox,  When it came out I thought it was the slickest chit I had ever seen.  Then I discovered Opera and have never looked back.  just my $.02

---

### Post by public_void on 2007-03-09
I've had this kinda happen when I've drag an OpenOffice widget around, it left a trail of grey, but it didn't happen every time. However I had four instances of OpenOffice, aMSN, Firefox, Nautilus and Folding@Home running. TBH that is no surprise, and CPU usage was 100% with F@H anyway.

---

