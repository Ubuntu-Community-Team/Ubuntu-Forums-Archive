---
title: "Skype Anyone???"
date: 2009-10-04
forum: Ubuntu Moblin Remix
---

### Post by swallisa on 2009-10-04
Anyone got skype up and running on Moblin???

TIA

---

### Post by om26er on 2009-10-05
mann u kiddin. have you ever used ubuntu if not download skype from skype.com and install and enoy

---

### Post by carlo_01 on 2009-10-05
Sure!  Skype works just fine on my Dell 10v using Ubuntu Moblin Remix.

---

### Post by pmains on 2009-10-07
The Medibuntu repository has several versions of Skype. So, add the Medibuntu repository to your sources and the use the "add/remove program" feature. That's how I installed it on my laptop, and it works fine (after changing all sound to pulseaudio under options).

If you need a different version of Skype (i.e., the MID version), then I recommend that you look for a deb package on skype.com and install with dpackage.

---

### Post by zeiz on 2009-10-08
But I just found out that skype ( 2.0.0.72) doesn't work on my box.
It used to work (same hw) on one of previous Ubuntu versions but not on 9.04.
No sound at all and video is complete mess. How to tune it?
____________________________________________________________
Asus P4S333/c, P4 2.4GHz, DDR333 2.5GB, Logitech webcam w/mic, 
SB16 Live!, GeForce3 Ti200.

---

### Post by amsum on 2009-10-08
For me also, there is no sound in skype. I am using ubuntu 9.04. Looks like Pulseaudio is not working for me and the worst is that it is the only option showing there. Am I missing something?

---

### Post by zeiz on 2009-10-09
I read somewhere that the pulse must be removed and asound installed instead but I'm not brave enough to try 'cause 9.04 is my main OS (I'm not using M$).
I'm also using FreeBSD and all the forum curses that pulse audio.
May be somebody more knowledgeable could help us?

---

### Post by tars_ac on 2009-10-11
I had to fiddle with skype's sound settings to get it to work for me.  In Skype's settings, there should be choices for different sound methods, and testers to see if it works.  I think ALSA eventually worked for me, although I don't have my netbook here to verify right now.

I also had to fiddle with the mixer levels in the volume control applet.  I'm not sure I could reproduce it again without fiddling for a while.

My netbook is an Eee PC 1000 if it helps.

I'm not sure what to do if Pulseaudio is the only option.  I can't remember anything ever working with Pulseaudio for me, not my desktop, laptop, or netbook.

---

### Post by michael37 on 2009-10-13
By far the best version of Skype for netbooks is skype-mid which is NOT available on skype website.

Do get it working, add "deb [http://archive.canonical.com](http://archive.canonical.com) jaunty partner" and install skype-mid package.  Blows aways skype 2.

---

### Post by swallisa on 2009-10-15
> **michael37 said:**
> By far the best version of Skype for netbooks is skype-mid which is NOT available on skype website.

Do get it working, add "deb [http://archive.canonical.com](http://archive.canonical.com) jaunty partner" and install skype-mid package.  Blows aways skype 2.

Make that "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner"

---

### Post by YOUKN on 2009-10-15
hey how do I post something on here?

---

### Post by michael37 on 2009-10-15
> **YOUKN said:**
> hey how do I post something on here?

Cheers, u just did.

---

