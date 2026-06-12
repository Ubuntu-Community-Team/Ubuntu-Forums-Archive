---
title: "Audio software with gamepad interface?"
date: 2009-06-26
forum: Ubuntu Studio
---

### Post by skullmunky on 2009-06-26
Just found a Rock Band (tm) kit on the street that someone was throwing away.  I plugged it in, tested in the Gamepad section of the system preferences, it works fine.  Are there any sound apps that recognize gamepad controllers?  I can make something in Pure Data, but thought I'd check if anything already exists before I go to all that effort.

---

### Post by Stochastic on 2009-06-27
Hmm, I've had a bit of experience hooking a wii controller up to PD through bluetooth.

I don't know what version of Rockband you're using, but if it's a wii then you'll probably want to just do a google hunt to find your howto.  Here's a link I have trailing around in my bookmarks folder: [http://www.wiili.org](http://www.wiili.org)

Here's an explanation of what I did in PD, if you're curious: [http://ubuntuforums.org/showpost.php?p=5880129&postcount=5](http://ubuntuforums.org/showpost.php?p=5880129&postcount=5)

---

### Post by skullmunky on 2009-06-27
Thanks, it looks like Pd is the glue I need.  The drum kit is from the Playstation version of Rock Band, it looks like.  My current scheme is either to (1) use Pd, (2) use Pd to convert to MIDI and send to other things like Hydrogen, or (3) use Python to convert to MIDI.  

I'm trying to use the hid/joystick object in Pd right now, and I can't tell if it's working properly.  The drum kit is showing up as /dev/input/js0.  All the example patches in Pd apparently want to get input from /dev/input/event*.  I have event0 through event12, but no idea which one is related to the joystick; furthermore, I can't open any of them because they're all owned by root and don't have world readable permissions.  

Any idea how this is supposed to work?  I tried

[hid/joystick /dev/input/js0] 

and it didn't give me any errors, but I also get nothing from any of the outlets.

---

### Post by Stochastic on 2009-06-27
First I should say that PD is not the only glue you could use.  There are many other very capable audio programming environments for Linux: ChucK, Super Collider, and CSound are the other three big ones on the block but by no means the only ones.  PD is however the easiest for beginners who don't like to read code.

I'm not that familiar with the hid object in PD, for help with that I'd suggest you head over to the mighty PD Forum: [http://puredata.hurleur.com/index.php](http://puredata.hurleur.com/index.php)

---

### Post by kayosiii on 2009-06-28
Freewheeling also support joystick input... You will need to write a configuration file for your device however. (using it like this should be loads of fun)...

There is a QT3 app called qjoypad that can translate joystick buttons into keyboard events and some newer ones that can make the gamepad usuable with just about anything.

And finally I am thinking about reviving some of my old software that I have written for such purposes.

---

### Post by macinnisrr on 2009-08-13
I found a thread on the Hydrogen Forum that explains how to use rock band drums with Hydrogen drum machine software. It will actually output rock band drum events to midi so it can be used with any midi-capable program.

here's the link:
[http://www.hydrogen-music.org/forum/index.php?action=show_thread&fid=&thread=734&page=last#4551](http://www.hydrogen-music.org/forum/index.php?action=show_thread&fid=&thread=734&page=last#4551)

attached is a zip file containing the source code file as well as an executable I compiled for intel x86 machines. 64-bit users will have to recompile with the following command:

g++ -o rbd2midi_test rbd2midi.cpp -lasound

Note that this only work if the rock band kit show up as the first joystick (/dev/input/js0). Otherwise the source code needs modification, which I'd like to do as soon as I figure out how to do such a thing.

---

