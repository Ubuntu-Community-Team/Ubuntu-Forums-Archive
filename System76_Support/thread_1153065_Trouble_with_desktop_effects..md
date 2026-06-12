---
title: "Trouble with desktop effects."
date: 2009-05-08
forum: System76 Support
---

### Post by Heathw on 2009-05-08
This might not be the right forum for this question but I just received my panp5 from System76. I was configuring compiz and I can't get the desktop cube to work properly. It's just a wall. I have four work spaces and desktop wall isn't enabled either. Also some of the window animations aren't working either. Any suggestions would be appreciated. Keep in mind I am very new to Linux.

---

### Post by riseringseeker on 2009-05-08
> **Heathw said:**
> This might not be the right forum for this question but I just received my panp5 from System76. I was configuring compiz and I can't get the desktop cube to work properly. It's just a wall. I have four work spaces and desktop wall isn't enabled either. Also some of the window animations aren't working either. Any suggestions would be appreciated. Keep in mind I am very new to Linux.

I like using a couple of addons to make configuring easier.  Open synaptic and find and put a check next to simple-ccsm and fusion-icon.  (Or from a terminal sudo apt-get install simple-ccsm fusion-icon).  You can have fusion-icon in your startups and be able to right click and configure choose desktop effects much easier.

I'm going to guess you have the "Desktop Cube" function enabled, have you also checked "Rotate Cube"?

---

### Post by Heathw on 2009-05-08
Yes I have "rotate cube" enabled. I will try what you suggested tonite when I get home. Thank you.

---

### Post by thomasaaron on 2009-05-08
Do you currently have *any* desktop effects?
If you press Ctrl-Alt-Left-arrow or Ctrl-Alt-Right-arrow, does your desktop smoothly glide to the next desktop? Or does the adjacent desktop just appear.

---

### Post by tomszyszko on 2009-05-08
Do the windows wobble, or when you press the super key [WINDOWS KEY] + tab do you get a window selector?? Maybe you have the key mapping in compiz-manager set wrong

---

### Post by Heathw on 2009-05-08
yes compiz is enabled I have wobbly windows and can switch to the next desktop. I will try a few things later today. Thanks.

---

### Post by Heathw on 2009-05-08
Ok I installed simple-ccsm and fusion-icon and it did help with the window animations. Those are working now. But I still can't get the cube to work correctly. I can Ctrl-Alt-Left or Right and it rotates to the next desktop but I can't make the cube unfold.

---

### Post by thomasaaron on 2009-05-09
What key-combination are you trying to use to unfold the cube? The key combination is configurable. On my machine it is Ctrl-Alt-Up Arrow. But I don't remember whether I specified that or it was the default.

---

### Post by Heathw on 2009-05-09
cntrl-alt-down

---

### Post by Derath on 2009-05-09
I had this problem a while ago. If it's the same issue I had, here's what you have to do: in Compiz settings, there's an option for Desktop Cube and Desktop Wall, take the check mark out of Desktop Wall, then add the check to Desktop Cube. For whatever reason, when both are selected, only Wall is used.

---

### Post by riseringseeker on 2009-05-10
> **Heathw said:**
> Ok I installed simple-ccsm and fusion-icon and it did help with the window animations. Those are working now. But I still can't get the cube to work correctly. I can Ctrl-Alt-Left or Right and it rotates to the next desktop but I can't make the cube unfold.

Ctrl-Alt-Left/Right is the default key combo to flip the cube to the next face.  If that is working for you, the rest should as well.  

The default key combo to have the cube "unfold" or "flatten" is Ctrl-Alt-Down.

Default for rotating the cube is Ctrl-Alt-Left-Mouse-Button.  Hold the Ctrl & Alt keys down first, then press and hold the left mouse button.  You should see your desktop change slightly.  While holding down the above keys, move another finger around on the mouse pad, and the cube should rotate.

---

### Post by Heathw on 2009-05-10
Yes I have tried all of that but the cube doesn't unfold. It's just 4 flat windows. I have attached a screenshot.

---

### Post by riseringseeker on 2009-05-10
> **Heathw said:**
> Yes I have tried all of that but the cube doesn't unfold. It's just 4 flat windows. I have attached a screenshot.

That is what it is *supposed* to look like when you hit Ctrl-Alt-Down.  What key combo are you using to get the effect in your screen shot?

Does holding down Ctrl-Alt then pressing the left or right arrow rotate the cube to a new desktop for you?

---

### Post by Heathw on 2009-05-10
ok so if ctrl-alt-down looks like that how do I get a cube? And yes ctrl-alt-left/right rotates to another desktop.

---

### Post by thomasaaron on 2009-05-10
Ctrl-Alt-Left Arrow / Right Arrow should rotate the cube.

Please check again in your configurator and make sure you have both Desktop Cube -and- Rotate Desktop enabled.

---

### Post by Heathw on 2009-05-11
Yes I have the cube enabled and rotate cube enabled but for some reason the cube isn't working. I've done this before on my iMac so this isn't my first time. I will just keep playing around with it.  Everything else works fine.

---

### Post by thomasaaron on 2009-05-11
Try ctrl-alt-<period> and ctrl-alt-<comma>.

That seems to be the default settings on one of my computers. Or open your configuration tool and click on Rotate Cube, and then the Bindings tab, and expand the Rotate Cube section to see/set your keybindings.

---

### Post by Derath on 2009-05-11
I believe it's also ctrl-alt left click and drag, as well as maybe the middle mouse button held down. While a little difficult with the touchpad, it's much easier with a mouse...

---

### Post by Heathw on 2009-05-11
Problem solved. Yep all I needed was a mouse. Then I had to go to ccsm and change it from cylinder to "none" for a cube. Thanks for everyone's help.

---

