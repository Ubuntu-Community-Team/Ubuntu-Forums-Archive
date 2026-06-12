---
title: "Wacom Intuos 3 and Gimp window mode"
date: 2010-02-25
forum: Ubuntu Studio
---

### Post by picelli2002 on 2010-02-25
Hi all,

I got a problem with my Intuos 3 (wide A3 model) and Gimp (Ubuntu studio 9.10).
The wacom works properly but when I use it to draw in window mode I got problems.

I have a laptop (Dell 4400) and a second monitor (Acer). The dual monitor is set up in twin view. The wacom is set up using the fdi file in 10-linuxwacom.fdi.  wacomcpl works properly and I can set all my tablet preferences from there.

When I use gimp setting my stylus and eraser in window mode they follow till the main cursor is inside the window. As soon as the cursor leave the window they stop following.

Anybody got the same problem? Any idea?

Cheers

---

### Post by atrus on 2010-09-11
Same issue here under Jaunty, unclear what to do about it.

No dual-monitor setup, and a Wacom CTE-440.

---

### Post by dsonck on 2011-12-03
It is a bit late but for anyone who comes across this, here is the simple answer:  In order to use your tablet (wacom intuos or other tablet) you have to set the mode to 'screen'. This mode is often what you want as it translates the mouse position directly. In other words: where the cursor is shown, GIMP has it's brush and draws at the same place.  The answer to 'I want to use GIMP in window mode is': I'm currently looking for a way to use the 'window' mode. Somehow Xorg 'steals' the mouse and when the cursor goes out of the window, GIMP won't receive the input events generated. I'm thinking that GIMP must have a way of directly reading the /dev/input/event device in order to allow for window restriction. But then Xorg mustn't steal the mouse and always send the events to GIMP.  Why would you choose window mode: - It won't leave the screen so you don't have to worry about that. - You have more precision as the size of the window is smaller but the mapped region of your tablet is the same.  I will post the answer to the true window mode

---

