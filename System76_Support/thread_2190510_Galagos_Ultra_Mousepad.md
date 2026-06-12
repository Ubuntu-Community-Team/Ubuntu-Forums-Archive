---
title: "Galagos Ultra Mousepad"
date: 2013-11-27
forum: System76 Support
---

### Post by joedog on 2013-11-27
I just an Ultra Pro and I'm generally happy with it. You know there's a but ... BUT I can't stand the mouse pad. I've tried just about every setting possible but at the end of the day it's the physical hardware that drives me nuts. There's no separate between right and left clicks. It's one piece of metal. Simple tasks like copying text and right-clicking to paste are anything but simple. I just wasted a minute of my life trying to do just that. 

Is there a replacement option for this laptop? Can I get replace the mouse pad with a more traditional one that contains left and right buttons?

---

### Post by xagent2 on 2013-11-27
Yes, I just got mine as well yesterday. The touchpad is horrible. Why can't it have separate buttons from the touchpad? This makes highlighting to copy much easier. Also, when you click, it doesn't interfere with the pointer position because the button is separate. On the Galago, when I click, it moves the mouse in random directions... because go figure the button is also the same as the touchpad. Very annoying.

Also, how do you middle click? I haven't been able to figure out a way to middle click. Discovering that the bottom left region was right-click itself took me a while to figure out. How do I configure multitouch?

---

### Post by keith5 on 2013-11-27
I actually really like the touchpad, but I was using a Macbook Pro before this, which also has buttons built in underneath.

---

### Post by xagent2 on 2013-11-27
> **keith5 said:**
> I actually really like the touchpad, but I was using a Macbook Pro before this, which also has buttons built in underneath.

How are you middle clicking? How do you configure this?

---

### Post by joedog on 2013-11-28
And how do you draw the line of demarcation between right and left clicks. It would nice if there was an etched line on the metal - if you're to the right of it, then it's a right click.

BTW: My wife has a Macbook and she likes the single flat pad. Maybe I can grow to like it but if I I can swap in a buttoned mouse pad, I would like to do that.

---

### Post by beru2 on 2013-11-29
I hated the trackpad as well when I first received it, but, rest assured, you do get used to it. The right click is on the bottom right corner, and the rest is all left click. I prefer tap to click, though. One thing I would recommend everyone try out is [disabling the trackpad while typing]("https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Disable_trackpad_while_typing")

---

### Post by joedog on 2013-11-29
Could you post your xorg.conf.d/50-synaptics.conf? 

I don't have one and it's not clear what my complete syntax should look like. In the system preferences I have "disable while typing" checked but the mouse pad doesn't seem to be honoring it.

---

### Post by beru2 on 2013-11-30
> **joedog said:**
> Could you post your xorg.conf.d/50-synaptics.conf? 

I don't have one and it's not clear what my complete syntax should look like. In the system preferences I have "disable while typing" checked but the mouse pad doesn't seem to be honoring it.

I just added ```
syndaemon -t -k -i 2 -d &
``` to my startup applications. [Here's]("https://help.ubuntu.com/community/AddingProgramToSessionStartup") how to do that for ubuntu. You could also just add it to your ~/.xinitrc

to my

---

### Post by xagent2 on 2013-12-02
> **xagent2 said:**
> How are you middle clicking? How do you configure this?

So... I'll ask yet again, how did you guys configure middle click? i'm guessing no one here middle clicks? How do you paste?

---

### Post by xagent2 on 2013-12-02
> **beru2 said:**
> I hated the trackpad as well when I first received it, but, rest assured, you do get used to it. The right click is on the bottom right corner, and the rest is all left click. I prefer tap to click, though. One thing I would recommend everyone try out is [disabling the trackpad while typing]("https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Disable_trackpad_while_typing")

Ok... but where is middle click?

---

### Post by beru2 on 2013-12-04
> **xagent2 said:**
> Ok... but where is middle click?

I don't middle click. I've honestly never used a laptop with a middle click function before so, personally, I'm fine with that. I also paste using Ctrl+V. 

But, if you **have** to have a middle click, type this into a terminal:
```
synclient TapButton3=2
```

Now tapping 3 fingers on the trackpad will act as a middle click.

---

### Post by keith5 on 2013-12-05
> **beru2 said:**
> I don't middle click. I've honestly never used a laptop with a middle click function before so, personally, I'm fine with that. I also paste using Ctrl+V. 

But, if you **have** to have a middle click, type this into a terminal:
```
synclient TapButton3=2
```

Now tapping 3 fingers on the trackpad will act as a middle click.


Nice tip.  I use tap to click most of the time.  You can tap 2 fingers to right click as well.

---

