---
title: "synaptic touchpad utility, anyone? ;)"
date: 2005-04-08
forum: The Cafe
---

### Post by kiddo on 2005-04-08
Mmmh, I just thought I might post it here, since I haven't found any traces for it in the wiki and in the forums: is anything planned to have a graphical manager for synaptic touchpads? (Well, touchpads in general!)

Now, why the hell? Well I discovered that it's nice to have it all work natively and all (like the scrollbar area on the right of my Dell Inspiron 5000 touchpad, which works flawlessly), BUT the current gnome mouse preferences dialog don't affect touchpads. It only affects, say, a plugged USB mouse.

And that touchpad has waaaaaaaaaaay to much acceleration! It's getting a bit on my nerves, I'm almost wishing for a decrease of sensitivity to an "iBook" level ;). I guess there's a way to do it without a graphical interface, but I thought it would be nice to have it someday. Meanwhile, could anyone give me some tips on how to fix this little annoyance? Then there will only be ACPI support and linksys WPC11 support left on my "kill list" ^^

Edit: hm, since I'm not so interested in creating a thread for every question I have, let's have a two in one :) I'd like to know, are there plans to "de-uglify" firefox's forms widgets? Is this part of a) ubuntu b) firefox-gnome c) firefox ? Any idea when that could appear?

---

### Post by soul_rebel on 2005-04-08
in the repos you can find ksynaptic, qsynaptic, tpconfig. At least the first two are graphical. Tell us if one of them does the job.

---

### Post by kiddo on 2005-04-08
Thanks for the reply, but it didn't work at all (I tried those before posting it seems).
[list]
[*]ksynaptic needs kde. I don't really want to spawn all those libs for configuring my touchpad only.   
[*]qtsynaptics is for Xfree86 it seems, from what synaptic (package tool) told me :)   
[*]tpconfig: not really helpful. Can't guess how to use it really. Rate? What's that, I'm not even sure. Then I just did -i (for info) just like I did last night: fatal: could not open PS/2 port [/dev/psaux] 
[/list] So it looks like some fix for this would be cool ^^

---

### Post by soul_rebel on 2005-04-08
ubuntu mouse is located at /dev/input/mice
perhaps that's the error.

I think you will probably end up installing kde libs or editing xorg.conf by hand. :-?

---

### Post by AndEat on 2005-05-08
[*]tpconfig: not really helpful. Can't guess how to use it really. Rate? What's that, I'm not even sure. Then I just did -i (for info) just like I did last night: fatal: could not open PS/2 port [/dev/psaux] 
[/list] So it looks like some fix for this would be cool ^^[/QUOTE]


I'm in the midst of learning to operate tpconfig. 

It won't run while GNOME is running, you need to create a script that goes somewhere on start-up.

---

### Post by benplaut on 2005-05-08
that would be awesome!

i've been trying, for a while now, to make my touchpad scroll-only, but it always kills X  :mad:

---

