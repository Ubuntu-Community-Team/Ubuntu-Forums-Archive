---
title: "In Ubuntu, the right edge of my synapstics touch pad works as a scroll!"
date: 2007-06-02
forum: The Cafe
---

### Post by wersdaluv on 2007-06-02
I have just figured out a while ago that if I move my finger up and down the right edge of my laptop's synapstics touch pad, it works as a scroll! 

It's amazing! In other operating systems, my touch pad does not work this way.

Do you have an idea how my touch pad works this way and how I can edit its configuration?

---

### Post by eentonig on 2007-06-02
I don't know about it't configuration. But I do not that mine does the same thing when I'm a work using Windows.

And off course at home when I'm running Ubuntu on the same pc

---

### Post by FuturePilot on 2007-06-02
Hehe, same here. In Windows it does nothing. In Ubuntu I can scroll with it. I think there's a package in the repos that is a GUI for configuring the driver. At least in Debian there is.

---

### Post by Bou on 2007-06-02
That's not all, if you move your finger along the bottom edge you get horizontal scrolling.

Just install gsynaptics :)

---

### Post by mips on 2007-06-02
Lol, it took you some time to figure that out. It has always worked for me in ubuntu & windows.

Do you know you can also tap on the pad and it performs mouse clicks ?

---

### Post by matthew on 2007-06-02
That's a cool deal, isn't it? I remember being just as excited when I first discovered it. With Windows I had to upgrade the touchpad driver on my laptop to get this functionality.

Congratulations on the discovery! :)

---

### Post by zanglang on 2007-06-02
It's amazing how you can discover all sorts of mind-blowingly cool functions just by randomly testing out packages in Linux. :) I've had gsynaptics installed for months, but only discovered middle-clicking and right-clicking days ago... took me some time to figure out why things were pasting themselves into textboxes when I didn't hit Ctrl-V. My laptop has two huge buttons for left and right click, but they're hard to press, loud, and I can't middle-click stuff, so this turned out to be a really welcome feature.

---

### Post by wersdaluv on 2007-06-02
> **zanglang said:**
> It's amazing how you can discover all sorts of mind-blowingly cool functions just by randomly testing out packages in Linux. :) I've had gsynaptics installed for months, but only discovered middle-clicking and right-clicking days ago... took me some time to figure out why things were pasting themselves into textboxes when I didn't hit Ctrl-V. My laptop has two huge buttons for left and right click, but they're hard to press, loud, and I can't middle-click stuff, so this turned out to be a really welcome feature.

You can right-click, middle-click, and paste using the touch pad? How?

---

### Post by mthakur2006 on 2007-06-02
it works in windows as well, just go to [www.synaptics.com](www.synaptics.com) and download the driver if you have got a synaptics touchpad. ;)

---

### Post by zanglang on 2007-06-02
[QUOTE="wersdaluv"]You can right-click, middle-click, and paste using the touch pad? How?[/QUOTE]

You need to install configure synaptics first (install gsynaptics, or k/qsynaptics if you prefer KDE). Afterwards the edges of the touchpad will be mapped:
- Tap the top-right corner = Middle-click
- Bottom-right = Right-click
With that, you can use the X clipboard by *highlighting* text in one application and *middle-clicking* on where you need it.

You can also tap the touchpad with two fingers to middle-click, but I can never get it working perfectly just using one hand, so sometimes I just tap with both index fingers. :)

---

### Post by wersdaluv on 2007-06-02
WOW!

That's so cool! 

Thanks dude!

---

### Post by mips on 2007-06-02
> **wersdaluv said:**
> WOW!

That's so cool! 

Thanks dude!

Everyday is a suprise with Linux ;)

---

### Post by nescafe1001 on 2007-06-02
> **Bou said:**
> That's not all, if you move your finger along the bottom edge you get horizontal scrolling.

Just install gsynaptics :)

Too bad horizontal scrolling defaults to back/forward in Firefox.  That annoys me to no end... :evil:

---

### Post by mech7 on 2007-06-02
it does not work for me on my acers :(

---

### Post by Bou on 2007-06-02
> **wersdaluv said:**
> You can right-click, middle-click, and paste using the touch pad? How?

Just tap the touchpad with two fingers for a middle-click, or three fingers for a right-click.

---

### Post by zanglang on 2007-06-02
> **Bou said:**
> Just tap the touchpad with ... three fingers for a right-click.
Ah, now that's something new for me. Thanks. :D

---

### Post by reacocard on 2007-06-02
You can do lots of stuff like this, you can even get circular scrolling or corner tapping, things the windows driver doesn't even have as an option. It's all done through the xorg.conf, here's my entry:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option          "SHMConfig"             "on"
	Option		"MinSpeed"		"0.3"
	Option		"MaxSpeed"		"0.75"
	Option		"AccelFactor"		"0.015"
	Option		"VertScrollDelta"	"20"
	Option		"HorizScrollDelta"	"20"
	Option		"VertEdgeScroll"	"1"
	Option		"HorizEdgeScroll"	"1"
	Option		"RTCornerButton"	"2"
	Option		"LTCornerButton"	"8"
	Option		"RBCornerButton"	"3"
	Option		"LBCornerButton"	"9"
	Option		"CircularScrolling"	"1"
	Option		"CircScrollDelta"	"0.1"
	Option		"CircScrollTrigger"	"3"
EndSection

```

That turns on vertical, horizontal and circular scrolling (circular from right edge only), sets some speeds (gnome overrides this, I think), and also maps the corners to various buttons.

type 'man synaptics' in a terminal for the full list of options and what each does.

---

### Post by FuturePilot on 2007-06-02
> **mips said:**
> Everyday is a suprise with Linux ;)
Lol. That's so true. I've been using Linux for almost a year now and I'm still discovering these awesome little features.:D

---

### Post by ThinkBuntu on 2007-06-02
Works that way for me in Sabayon and openSuSE, amongst others. Nothing new here.

---

### Post by FuturePilot on 2007-06-02
Hmmm. No gsynaptics in Dapper:-k

---

### Post by Sunflower1970 on 2007-06-02
:shock: Wow! Thanks for the tip! I had no idea I could do that on my laptop. Works great :)

---

### Post by Pobega on 2007-06-02
You could set your touchpad up to do circular scrolling too, which is what I use personally. Circular scrolling is hard to do "accidentally", so the scrolling doesn't get in your way while you try to move the mouse (I remember when I used to try move the mouse up, and I accidentally scrolled the touchpad, which annoyed the hell out of me)

---

