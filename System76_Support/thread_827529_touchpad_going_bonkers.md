---
title: "touchpad going bonkers"
date: 2008-06-12
forum: System76 Support
---

### Post by dgermann on 2008-06-12
Hi--

End of May I upgraded my GAZV4 (I think--you'll see why I don't know in a minute) from 7.10 to 8.04.

This is a machine I use sometimes, so I am not sure if this issue existed immediately after the update.

In any case, I cannot use the touchpad at all. I move the mouse pointer someplace on the screen, remove my finger and it runs all over the screen, right to left, top to bottom, jumping, dancing, quantum-leaping. Where it ends up, nobody can guess.

So I cannot use the menus in the panel (unless there is some way to do that via the keyboard).

Earlier tonight I was able to make some adjustments to the touchpad settings. I turned sensitivity to lowest possible and tapping to just the low side of middle.

Guessing that this file might have some clues, I include it below:

```
<?xml version="1.0"?>
<gconf>
        <entry name="fast_taps" mtime="1183512693" type="bool" value="false">
        </entry>
        <entry name="sensitivity" mtime="1213317287" type="int" value="-2">
        </entry>
        <entry name="edge_motion_use_always" mtime="1183512451" type="bool" value="true">
        </entry>
        <entry name="horiz_scroll_delta" mtime="1185632022" type="int" value="0">
        </entry>
        <entry name="circular_scrolling" mtime="1183823619" type="bool" value="false">
        </entry>
        <entry name="circ_scroll_delta" mtime="1183823619" type="int" value="0">
        </entry>
        <entry name="vert_scroll_delta" mtime="1213317269" type="int" value="60">
        </entry>
        <entry name="max_tap_time" mtime="1213317356" type="int" value="350">
        </entry>
        <entry name="off" mtime="1213317269" type="bool" value="false">
        </entry>
</gconf>
```

Thanks for any hope you can give me!

---

### Post by thomasaaron on 2008-06-13
Go to System > Administration > System76 Driver. It will tell you which Gazelle you have -- which is relevant.

Also, have you installed gsynaptics, or any other touchpad adjustment software?

---

### Post by dgermann on 2008-06-13
Thomas--

Thanks for your quick-as-always reply.

<< Go to System > Administration > System76 Driver.

I say this to document this for others having the same problem: It would have been impossible to go to that menu because the mouse pointer was bouncing around so much I could not go to anything via the panel menus!

What I bumped into was to press the Windows key; it brought up the Applications menu, and from there I could use the right arrow and get to this menu.

Is there another way to activate the panel menus? This does not work on my desktop machine, for instance.

So, to answer your questions: I remembered right, it is gazv4.

I only have what comes installed standard with 8.04, so I do not think I have the other stuff you mention. Should I install it, Thomas?

Thanks very much!

---

### Post by thomasaaron on 2008-06-13
Honestly, I have doubts that it will make any different. I've not seen your problem before on a System76 computer, and I've not seen it mentioned in conjunction with Gsynaptics. It would be a long shot.

But if you like long shots, here is a tutorial on installing it...
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

That said, it may be something that got hosed when you upgraded. You could boot into your previous kernel and see if you get the same result. To do that, press Esc when you see the grub countdown upon booting. Boot into a Gutsy kernel and see if you still have the problem. This may not be conclusive either.

You might also try unloading and reloading the touchpad module and see if that fixes it:

sudo modprobe -r psmouse
sudo modprobe psmouse

Might be a good idea to have a USB mouse handy in case that goes awry.

Let us know what you find, and we'll keep working on it.

---

### Post by dgermann on 2008-06-15
Thomas--

I am always pleased to see you here--I know I get reliable and quick help from you.

What seems to have calmed it down was playing with the settings. Not sure what I found that did the trick--I know I played around in the mouse area and in the touchpad area. In the latter I set most of the settings right near dead center.

I will have a couple days using just this machine in a few days, so that may tell the tale. Will let you know if there is any change, Thomas.

I always thought I would like a touchpad mouse, but now that I have one, I find they are difficult to learn to use. The help screens are not helpful, and I have a sneaking suspicion that the labels for the various settings are backwards. For instance, if you want it more sensitive you set it to less, etc. If you know of any good tutorial on using the touchpad, I would love it!

Thanks, Thomas!

---

### Post by dgermann on 2008-06-23
Thomas and all--

Looks like it is working OK. Seems that when I changed to making it super sensitive one way or the other was when it went bonkers. Using the trick in this thread for getting the menu and putting it back in the middle seems to have been the ticket.

Thanks!

---

### Post by Brandon Jenko on 2008-06-26
HI my name is Brandon Jenko touchpads are the hardest thing to work on and it seems you guys worked it out. touchpads have really come a long way over the past couple of years along with touch screens however they are avoiding us from fixing and editing without manufactures

Brandon Jenko

---

