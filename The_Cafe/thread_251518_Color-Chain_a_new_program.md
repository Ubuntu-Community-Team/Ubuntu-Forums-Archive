---
title: "Color-Chain: a new program"
date: 2006-09-05
forum: The Cafe
---

### Post by daou on 2006-09-05
Being my self-centered self (me me me):mrgreen: , I thought I'd draw a little attention to a program I just released. Check this thread:
[http://www.ubuntuforums.org/showthread.php?t=251513]("http://www.ubuntuforums.org/showthread.php?t=251513")

Hopefully someone finds it useful.

---

### Post by Abstract on 2006-09-05
Hey,

I really like the idea of this program and I downloaded and installed the .deb successfully. I did the config copy thing - I didn't use the GUI. I then ran this:

```

color-chain --verbose --fast

```

It outputted all stuff but nothing changed. I look at my background and nothing changed. Any help?

---

### Post by daou on 2006-09-05
Are you sure you have a transparent background, ie an svg or a png background? Try taking your background off completely then run the program.

---

### Post by daou on 2006-09-05
Also make sure you have set your desktop background color to a gradient (either a vertical or a horizontal gradient). This is something I've forgotten to include in the program, I will add an option to set it.

EDIT: Even if your background color is set as "Solid" it should still change the color of the background. However, only changes to the primary (Color1) are visible.

---

### Post by Abstract on 2006-09-05
Okay it works if I take the background off and it looks pretty cool just on its own. I now have one more question:

What would I do to make it run everytime I login?

---

### Post by daou on 2006-09-05
I suppose the easiest way is to add it to your session startup programs list.
In your desktop menu:

System->Preferences->Sessions->Startup Programs.
Then click "Add" and type "color-chain" in the "Startup Command" textbox.

---

### Post by Abstract on 2006-09-05
Thanks! I really like this program. I'm just trying to find some wallpapers on [http://gnome-look.org](http://gnome-look.org).

Can you recommend any?

---

### Post by daou on 2006-09-05
There aren't many that have enough transparency for the gradient to come through well. I suggest you look for SVG backgrounds.

Or, if you adventurous, you can try Inkscape and make your own SVG background. It's quite easy to make nice looking backgrounds. You can get Inkscape by typing:

sudo apt-get install inkscape

I'm glad you like it! :D

---

### Post by daou on 2006-09-05
You can also install gnome-backgrounds

sudo apt-get install gnome-backgrounds

It has two translucent SVG backgrounds (ellipsis.svg and tentacles.svg). I suggest you try them.

---

