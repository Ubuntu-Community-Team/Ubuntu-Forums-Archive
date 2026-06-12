---
title: "Getting Scancodes"
date: 2013-08-16
forum: Ubuntu Application Development
---

### Post by Lars_Baronat on 2013-08-16
I currently try to get a special key on my X200 Tablet to work. I want to bind a script to it that locks the screen but if I keep the button pressed for about 2 seconds or so it should put the device into standby. I already know how to bind a script to such a button (there are four of them and one is already bound to a script) but know there is the problem with holding the button. My idea of doing this was to let the script wait for 2 seconds and then check if the button is still pressed by reading the keyboard scancodes. My problem is that i was not able to find a command that just gives me the current scancodes and works in a simple script. Is there a command that does this or is there another way to make this work?

---

