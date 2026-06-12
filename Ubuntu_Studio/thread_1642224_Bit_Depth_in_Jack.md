---
title: "Bit Depth in Jack"
date: 2010-12-10
forum: Ubuntu Studio
---

### Post by dawiba on 2010-12-10
Just been reading another post which prompted me to have a look in Jack. It seems I can only use 16 bit for recording/playback. Sample rate seems adjustable all the way up to 192khz.

How would I change bit depth to 24bit?

---

### Post by AutoStatic on 2010-12-10
You can't. It's not necessary as JACK runs 32bit by default unless you force it to use 16bit.

---

### Post by dawiba on 2010-12-10
That's what I thought, but when I look in my settings window, it shows word length as 16 (greyed out as is the option to force 16 bit on my settings page).

I always thought word length = bit depth. Is it greyed out because that value isn't active, rather than being fixed and not able to be changed?

---

### Post by AutoStatic on 2010-12-10
[http://www.rncbc.org/drupal/node/19#comment-46](http://www.rncbc.org/drupal/node/19#comment-46)

It's greyed out because it's an OSS option, not an ALSA one.

---

### Post by dawiba on 2010-12-10
Thanks for that :)

I did read on the Jack website that it was 32 bit floating point, but got a bit confused when I looked in the Preferences window. It's been a while since I was poking around in Ubuntu and I guess I need to take a bit more time reading up again :)

---

