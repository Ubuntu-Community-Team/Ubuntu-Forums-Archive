---
title: "Pangolin value, VGA out and cloning"
date: 2006-08-26
forum: System76 Support
---

### Post by lord trousers on 2006-08-26
I often need to output to a projector. The default setup for the Pangolin values doesn't output anything to the VGA pipe. I found you could make it do so by adding a couple of lines to the "Device" section of xorg.conf:

```

	Option		"MonitorLayout" "CRT,LFP"
	Option		"Clone" "true"

```

This tells the driver to patch CRT output through pipe A and LCD output through pipe B, and clone it. (Carl, you might consider making this the default setup for now.)

This works reasonably well. What it *doesn't* do is clone some types of graphical overlays, like the kind that gxine uses to play movies. That's right, I can use this to do presentations (yay), but not to watch movies (argh). I just get a blue rectangle.

Using this instead properly outputs those overlays:

```

	Option		"MonitorLayout" "NONE,CRT+LFP"

```

But what it's doing is patching the *same signal* through both. Because my desktop is running at 1280x800, it sends that out, and most projectors hate that kind of signal. It either doesn't show up or parts of it end up off-screen.

Now that everyone's up to speed, here's my main problem: if I could send an actual 1024x768 signal, I'd be fine. But when I change the resolution (in any way) to 1024x768, it *scales* it and sends a *1280x800* signal.

I've seen i810 chips output a non-native-resolution signal (the LCD centers it inside a black border), and from what I've read online, this particular model is capable of it, somehow. There's no xorg.conf option, though. Also, from what I've read online, once you set the option, it persists between reboots, so a small utility would do it just fine.

Any pointers would be appreciated. If it ends up being a VGA BIOS call, I'll write something myself.

---

### Post by crichell on 2006-08-26
```
	Option		"MonitorLayout" "CRT,LFP"
	Option		"Clone" "true"
```

We'll be testing this next week - great suggestion.

> 
I've seen i810 chips output a non-native-resolution signal (the LCD centers it inside a black border), and from what I've read online, this particular model is capable of it, somehow.

We use 915resolution for adjusting to non-native resolutions w/ Intel graphics chips.  Haven't testing it in this scenario though.

```
sudo apt-get install 915resolution
```
```
sudo 915resolution -l
```

Pick the mode and resolution you want to use.  Adjust /etc/deafult/915resolution appropriately and you should be using the new resolution.  The trouble I suppose is piping the 915resolution out to the VGA port while keeping the native resolution on the LCD.

---

### Post by lord trousers on 2006-08-26
Yeah, that's the main problem. BTW, thanks for the suggestion - I hadn't tried that method of changing resolution. Unfortunately, it didn't work, either setting the resolution to 1024x768 or back to its original (1280x1024, I think) to make it use another built-in mode.

(It'll be nice when you don't have to use 915resolution anymore. Apparently, there's an update coming in the i810 driver that'll let you do the same thing in xorg.conf.)

Browsing through i810 driver code now - should be fun. :D

---

### Post by lord trousers on 2006-08-26
Oh, one more thing. You might need another "Monitor" section to cover the external CRT - I didn't test mine without having one. (I don't have access to a projector right now, or I'd check it myself.) Also, you might want to test things like "CRT+DFP,LFP" as well, to clone the CRT signal through the digital out. (Is that what that is next to the CRT port?) I didn't have the hardware to test those kinds of setups.

---

### Post by lord trousers on 2006-08-28
Got a workaround for the blue rectangle. You can't do this in Totem, but in GXine you can set the output driver to "xshm," which doesn't use a video overlay. ("opengl" also doesn't, but it's choppy.) Unfortunately, it eats CPU (80% of one core vs. negligable with an overlay) and looks a little blocky when scaled to full-screen, but it'll get the job done for now.

---

### Post by reacocard on 2006-08-28
you can use xshm in totem. I do. you just have to manually edit ~/.gnome2/totem_config and change the video.driver setting.

---

### Post by reacocard on 2006-08-28
Sorry to double post, but the edit button isn't working.

I just tried this with a CRT monitor, works beautifully, without an extra monitor section. Totem + xshm works fine, both windowed and fullscreen.

And btw, that other port is the TV (S-video) out. So that'd be CRT+TV.

---

### Post by lord trousers on 2006-08-28
Got it.

Also, thanks for the Totem tip. I should have known it'd be in a config file even if the GUI didn't have the option.

---

