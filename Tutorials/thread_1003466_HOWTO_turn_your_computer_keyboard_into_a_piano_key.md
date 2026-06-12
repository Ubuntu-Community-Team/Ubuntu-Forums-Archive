---
title: "HOWTO: turn your computer keyboard into a piano keyboard"
date: 2008-12-06
forum: Tutorials
---

### Post by anomalous_underdog on 2008-12-06
I came across [http://thebatman.net/keybored/](http://thebatman.net/keybored/) which allows the computer keyboard to play piano notes everytime a key is pressed.

Unfortunately this doesn't run on Ubuntu Linux, but there are equivalent programs that allow you to do this.


1. First you need a decent grand piano soundfont.

You can get a free one here:
[http://www.pianosounds.com/](http://www.pianosounds.com/)
(last I checked, it was a zip archive, inside of which is a self-extracting rar archive in .exe format, so you'll need wine to extract it)

Or install the fluid soundfont package via apt:
fluid-soundfont-gs
fluid-soundfont-gm (be warned, 100+ MB worth of download)


2. install these packages:

jackd
qsynth
qjackctl
vkeybd


3. run qjackctl (Applications > Sound & Video > Jack Control). click on the Start button to start the jack server.


4. run qsynth (Applications > Sound & Video > QSynth) and load the soundfont from there (Setup... > Soundfonts > Open...). It'll ask to be restarted, go ahead and let it.


5. run vkeybd (Applications > Sound & Video > Virtual MIDI Keyboard)


6. use qjackctl to connect vkeybd to qsynth (Connect > ALSA):
you can just drag and drop it
```

output                     input
----------------------     ---------------------------
130:Virtual Keyboard       129:FLUID Synth (2806)
   0:Virtual Keyboard ------> 0:Synth Input port (2806:0)

```

7. vkeybd should now play some piano sounds. click on View > Key/Velocity. It will show a key slider, use it to change the keyboard's octave.


Most programs I mentioned are on the KDE side (qjackctl, qsynth). I don't know which GNOME programs are the equivalent counterparts for those. Also, there may be a way to do this without needing a jack server but I'm not sure.

If you guys know of better ways to set it up, please contribute.


EDIT: There is another program called ZynAddSubFX which also has this functionality (available in apt). The advantage with ZynAddSubFX is there's no configuration needed; you can start playing paino sounds using your pc keyboard right away. Unfortunately, ZynAddSubFX is more on synthesized piano sounds, and none of its instruments sound like a real grand piano.
Also the nice thing with ZynAddSubFX is it makes use of most of your keys in the keyboard, while vkeybd only makes use two rows of keys in your keyboard: A through ' (single quote), and Z through ? (question mark).

---

### Post by cIIIz on 2008-12-18
thanks a lot :D this is really helpful

:D

:guitar:

---

### Post by iDleR on 2009-01-30
Thanks, very helpful

---

### Post by Boulemans on 2011-07-31
I have done all the above (with the soundfont of [http://www.pianosounds.com](http://www.pianosounds.com)), and it all works visually but I do not get any sound. Moreover, the method of ZynAddSubFX doesn't give a sound either. Can someone hint me in the right direction?

---

### Post by Whohlme on 2011-09-21
Without learning anything, this may help for ZynAddSubFX. Just install LMMS and invoke Zyn from the instruments tab on the left.

---

