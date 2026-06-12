---
title: "Idea for Rhythmbox plugin: too ambitious?"
date: 2010-02-01
forum: Ubuntu Dev Link Forum
---

### Post by mtanner on 2010-02-01
Hello all.  I have an idea for a Rhythmbox plugin, and would like to get some ideas as to 1) the feasibility of this plugin, 2) methods of implementation, 3) any related projects or good resources you can point me to.  And who knows, maybe a project like this already exists, but I've searched for a while and haven't come up with anything.

I'd like to have a plugin which would allow me to connect a USB footpedal (like the 3-button kind used by transcriptionists) and use it to pause, rewind, and fast-forward songs.  I think this would be very useful for musicians in practice, guitarists & bassists especially.  Being able to rewind a song with your feet without having to take your hands/eyes away from your instrument/tabs/what-have-you.

1) I have no experience with (but am obviously willing to learn :) USB programming.

2) I have very little experience (also willing to learn :) with Python.

3) I've got some experience with C/C++ and Java.

The basic idea I'm working off of is writing a RB plugin in Python and using pyusb to connect to the footpedal and read control data from it.  I'm thinking that the particular footpedal in mind can be read as a HID device.

The other idea that might work is to implement it as some sort of generic HID device loaded by Gnome and have it call up the built-in keyboard shortcuts for Gnome (xf86play, pause, etc).  But I'm not sure how I would handle rewind/fast-forward functionality with that approach.

Do either of these ideas sound possible or feasible for one such as myself with limited USB/Python knowledge?  Anyone have any advice?  Sites I should visit?

TIA

---

