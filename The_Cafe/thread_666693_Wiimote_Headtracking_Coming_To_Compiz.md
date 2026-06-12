---
title: "Wiimote Headtracking Coming To Compiz"
date: 2008-01-13
forum: The Cafe
---

### Post by klange on 2008-01-13
I'm sure many of you have seen the videos by Johnny Chung Lee of the use of a Wii remote as a tool to detect head position for use in a virtual environment.

If you have, you'll probably be interested in knowing that a new plugin for Compiz Fusion is currently in the works to add this functionality to the everyday desktop.

By using sensor data collected through CWiiD, [WiiTrack](http://wiki.compiz-fusion.org/Plugins/Wiitrack) will determine the position of your head and distort the Compiz viewport accordingly.
The current release does not include Wiimote integration, but this is being worked on by others. However, it does have the basic framework that distorts the view and a virtual "head" can be moved with key bindings. The plugin also features automatic 3d stacking of windows, much like the 3d Windows plugin. This adds to the feel of the environment.

Future improvements will include smooth Z-level switching through an animation and anaglyph (red/blue 3d images) to create an even more believable virtual environment.

**Automatic Z-level stacking:**
[[img]http://ogunderground.com/random/compiz/headtracking/new/th_autozlevel.png[/img]](http://ogunderground.com/random/compiz/headtracking/new/autozlevel.png)
[Head on bottom](http://ogunderground.com/random/compiz/headtracking/new/head_on_bottom.png) [Head  on right](http://ogunderground.com/random/compiz/headtracking/new/head_on_right.png) (this images are old and show display artifacts that have since been fixed)

---

### Post by homegrown on 2008-02-07
Very cool, cant wait for this to be the norm!

---

### Post by klange on 2008-02-07
Didn't expect a 3 week bump on this, but glad to see that you're excited.

We've made some pretty good progress recently, and even have a (kinda crude) video on YouTube. [Check it out](http://youtube.com/watch?v=92i8to9njUo).

I've also been working on making the plugin a bit more aesthetically pleasing by adding [animations](http://youtube.com/watch?v=XXV436klYek) to the 3d window stacking.

---

### Post by SunnyRabbiera on 2008-02-07
Interesting

---

### Post by rowanparker on 2008-02-07
I don't actually get what it does.
Sorry but it's rather confusing :(

---

### Post by el_ricardo on 2008-02-07
i am soooo buying a wiimote lol!

---

### Post by klange on 2008-02-07
> **rowanparker said:**
> I don't actually get what it does.
Sorry but it's rather confusing :(

Short explanation: Wiimote + cool IR glasses + this = virtual 3d desktop

Long explanation: The Wiimote has a 1024x768-resolution infrared camera with built-in blob detection software that can track 4 points. By positioning the Wiimote on top of your screen such that it can see your head (sort of like a webcam), and by wearing special IR LED equipped safety glasses (which you have to make, but they're pretty simple. I'm sure some people at [Wiimote Project](http://wiimoteproject.com) will end up selling them for like $15-30 anyway), the plugin (through another polling plugin, actually) grabs data from the Wiimote with CWiiD. It uses this data (the coordinates of the IR points of the lights on your head) to determine your 3d head location (based on an trig algorithm used by Johnny Chung Lee). It then uses this information to distort Compiz's GL_PROJECTION matrix, switching it to a frustum view set up from your head location. The end result is that when you move left, the vanishing point moves left and so on. Another added benefit of the plugin is that it stacks your windows 3-dimensionally, so that you can actually see the effect (otherwise, you need to enable cube transparency and stuff, which I suggest anyway)

So, Wiimote, Compiz, Bluetooth dongle, IR glasses, CWiiD = Virtual 3d Desktop.

I actually just got my Wiimote a few days ago, and don't even have a bluetooth dongle yet.

---

### Post by days_of_ruin on 2008-02-07
Cant Wait!!!

---

### Post by quanumphaze on 2008-02-07
It won't be long before we see this as the selling point of the Wii 2.

This is really cool:cool:, I would love to see it being done by recognising your face on a web cam since most laptops have them already but I fear of the CPU overhead of that sort of thing. But then again we will have affordable quad cores by the time it goes mainstream.

Remember, it was on Linux first!

---

### Post by days_of_ruin on 2008-02-07
> **quanumphaze said:**
> It won't be long before we see this as the selling point of the Wii 2.

This is really cool:cool:, I would love to see it being done by recognising your face on a web cam since most laptops have them already but I fear of the CPU overhead of that sort of thing. But then again we will have affordable quad cores by the time it goes mainstream.

Remember, it was on Linux first!

I dont think it would use that much cpu.Its compiz so I think the graphics card would do a lot of it too.I may be completely wrong tho:lolflag:

---

### Post by klange on 2008-02-07
> **days_of_ruin said:**
> I dont think it would use that much cpu.Its compiz so I think the graphics card would do a lot of it too.I may be completely wrong tho:lolflag:
He was referring to a webcam identifying your face and tracking it, which would take a lot of processing power.

---

### Post by quanumphaze on 2008-02-07
> **days_of_ruin said:**
> I dont think it would use that much cpu.Its compiz so I think the graphics card would do a lot of it too.I may be completely wrong tho:lolflag:

I meant the "using a web cam instead of the Wiimote for head tracking" idea would use up CPU. Sorry for the confusion

---

### Post by quanumphaze on 2008-02-07
> **WindowsSucks said:**
> He was referring to a webcam identifying your face and tracking it, which would take a lot of processing power.

Oops, I didn't see the second page here.:oops:

---

### Post by rowanparker on 2008-02-08
> **WindowsSucks said:**
> Short explanation: Wiimote + cool IR glasses + this = virtual 3d desktop

Long explanation: The Wiimote has a 1024x768-resolution infrared camera with built-in blob detection software that can track 4 points. By positioning the Wiimote on top of your screen such that it can see your head (sort of like a webcam), and by wearing special IR LED equipped safety glasses (which you have to make, but they're pretty simple. I'm sure some people at [Wiimote Project](http://wiimoteproject.com) will end up selling them for like $15-30 anyway), the plugin (through another polling plugin, actually) grabs data from the Wiimote with CWiiD. It uses this data (the coordinates of the IR points of the lights on your head) to determine your 3d head location (based on an trig algorithm used by Johnny Chung Lee). It then uses this information to distort Compiz's GL_PROJECTION matrix, switching it to a frustum view set up from your head location. The end result is that when you move left, the vanishing point moves left and so on. Another added benefit of the plugin is that it stacks your windows 3-dimensionally, so that you can actually see the effect (otherwise, you need to enable cube transparency and stuff, which I suggest anyway)

So, Wiimote, Compiz, Bluetooth dongle, IR glasses, CWiiD = Virtual 3d Desktop.

I actually just got my Wiimote a few days ago, and don't even have a bluetooth dongle yet.

Oh right.
That makes it much simpler, thank you :)

And it does sound really really cool :D
I already have a wii and a bluetooth dongle so I'd be prepared.
IR glasses would be easy I suppose.
I'd love to test it out :)

I once tried to use the wiimote as an input device (using CWiiD). It half-worked. I had to light a candle in front of my monitor for it to work like. And it did move the mouse around on screen but I had a few problems with key presses (some worked, some didn't, some worked sometimes) so I guess its still a bit buggy. But nevertheless the whole idea of it was cool.

---

### Post by dnns123 on 2008-02-08
[QUOTE=Long explanation: The Wiimote has a 1024x768-resolution infrared camera with built-in blob detection software that can track 4 points. By positioning the Wiimote on top of your screen such that it can see your head (sort of like a webcam), and by wearing special IR LED equipped safety glasses (which you have to make, but they're pretty simple. I'm sure some people at [Wiimote Project](http://wiimoteproject.com) will end up selling them for like $15-30 anyway), the plugin (through another polling plugin, actually) grabs data from the Wiimote with CWiiD. It uses this data (the coordinates of the IR points of the lights on your head) to determine your 3d head location (based on an trig algorithm used by Johnny Chung Lee). It then uses this information to distort Compiz's GL_PROJECTION matrix, switching it to a frustum view set up from your head location. The end result is that when you move left, the vanishing point moves left and so on. Another added benefit of the plugin is that it stacks your windows 3-dimensionally, so that you can actually see the effect (otherwise, you need to enable cube transparency and stuff, which I suggest anyway).[/QUOTE]

I get it now! Thanks!

---

