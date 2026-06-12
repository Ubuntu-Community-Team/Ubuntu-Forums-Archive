---
title: "Scroll not working after upgrade to 9.04"
date: 2009-04-25
forum: System76 Support
---

### Post by EmilyRose on 2009-04-25
Hi there, I just upgraded to 9.04 this morning and have only two issues, one of which I seem to have resolved (tracker error, seems to have been fairly common), and the other which I can't figure out. My mouse works peachy fine, except for I can't scroll up or down with it like I used to. I'm on a gazp5.

---

### Post by VOLKOV9 on 2009-04-25
Same problem here.

---

### Post by thomasaaron on 2009-04-26
Well, this is weird.

Just fired up a GazV5. Go to System > Prefs > Mouse > Touchpad (Tab) and make sure vertical scrolling is enabled.

It is actually done DIFFERENTLY now. Remember how you used to be able to put just one finger on the right edge of the touchpad and scroll? Now you must put two on the pad... say, your forefinger and middle finger. Keep the forefinger stationary, and scroll with the middle finger.

I don't care for it, but apparently that's how you do it!

---

### Post by EmilyRose on 2009-04-26
AAhh! I didn't know I had to use TWO fingers now! Problem solved! Thanks!! I actually must have done so accidentally earlier today cause' it scrolled for a moment, I just couldn't figure out how I did it;) Thanks again!!

---

### Post by VOLKOV9 on 2009-04-30
Solved it for me too.  Except I'm really bad at this two-finger thing ](*,) .  I'm guessing there's no way to force this to revert?

---

### Post by thomasaaron on 2009-04-30
No.

I'd love to know the rationale behind *that* one.

---

### Post by Sean-Michael on 2009-05-05
I just ran into this one... very lame!

I've resorted to using my mouse until I'm ready to train my brain and hands lol

Thanks for the tread!

---

### Post by Naenyn on 2009-05-05
> **thomasaaron said:**
> Now you must put two on the pad... say, your forefinger and middle finger. Keep the forefinger stationary, and scroll with the middle finger.

I have a Serp4 and this doesn't seem to work for me. If I keep one finger on the pad and try to use another to scroll, the page just jumps up and down a bunch. I have to slide two fingers simultaneously on the pad to get it to scroll vertically.

No idea how horizontal scrolling is supposed to work. I attempted to enable it to experiment, but nothing seems to work.

Not quite sure what to make of this.. :-k

-Naenyn

---

### Post by andrewdied on 2009-05-05
> **thomasaaron said:**
> Well, this is weird.

Just fired up a GazV5. Go to System > Prefs > Mouse > Touchpad (Tab) and make sure vertical scrolling is enabled.

It is actually done DIFFERENTLY now. Remember how you used to be able to put just one finger on the right edge of the touchpad and scroll? Now you must put two on the pad... say, your forefinger and middle finger. Keep the forefinger stationary, and scroll with the middle finger.

I don't care for it, but apparently that's how you do it!

I did some experimenting, and if you use two fingers and push them both up and down it scrolls much better.  Move the fingers in tandem, together.  I haven't tried left/right, but up/down works.  This is an OK change, though the mixed steady/move stinks.

---

### Post by riseringseeker on 2009-05-08
> **thomasaaron said:**
> Well, this is weird.

Just fired up a GazV5. Go to System > Prefs > Mouse > Touchpad (Tab) and make sure vertical scrolling is enabled.

It is actually done DIFFERENTLY now. Remember how you used to be able to put just one finger on the right edge of the touchpad and scroll? Now you must put two on the pad... say, your forefinger and middle finger. Keep the forefinger stationary, and scroll with the middle finger.

I don't care for it, but apparently that's how you do it!

Just out of curiosity, I tried the two finger scroll on the Darter (right side of pad works fine).  Lo and behold, it works on the Darter as well, both as described above and by moving both fingers simultaneously.

For me/us this is an advantage, as the wife's netbook has the same behavior, and she doesn't have to do it differently on the Darter those few times she would use it.

---

### Post by phyzome on 2009-05-09
From what I understand, this is how scroll works on Mac touchpads, and I *much* prefer it. You no longer have to worry about your finger accidentally landing on the scroll strip, and multi-touch scroll is not any harder.

However, this requires hardware cooperation. My Pangolin's touchpad doesn't seem to emit multi-touch info, so, I have to use the scroll strip. However, my Acer Aspire's pad emits this info, so the two-finger method is automatically enabled.

---

### Post by drewbenn on 2009-07-17
I know it's been a while, but there is a way to force the old behavior (use the right side of the touchpad to scroll up and down).

Disable the touchpad and then re-enable it with 'proto=imps':
```
modprobe -r psmouse
modprobe psmouse proto=imps
```
If you want to make it permanent, add the option to modprobe.d/options.conf:
```
echo "options psmouse proto=imps" | sudo tee -a /etc/modprobe.d/options.conf
```
and you will use the 'imps' mode next time you power up (or modprobe -r psmouse;modprobe psmouse).

---

