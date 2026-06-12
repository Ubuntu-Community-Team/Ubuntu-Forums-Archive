---
title: "[SOLVED] Totem in hardy is very slow.."
date: 2008-04-28
forum: The Cafe
---

### Post by chris4585 on 2008-04-28
I've upgraded to Hardy like most people have, and I've had a major problem.  One I usually install ubuntu-restricted-extras so I can watch/listen to pretty much any media need I have.  Well when i tried to watch video's in totem, the video's play really slowly.  How can I fix this?  I've installed VLC and it only works half the time, and I really don't even like VLC to start with.  Any solutions?  If not then I'll just downgrade back to Gutsy.  I feel a little disappointed in Hardy after so much waiting, and telling others how great it will be.  I've had other problem's too, but not as major.

Now i see why some people stayed with Feisty when Gutsy came out.

---

### Post by loell on 2008-04-28
a number of people have problems with upgrading from gutsy to hardy too, you could either reinstall gutsy or maybe do a clean hardy install.

---

### Post by chris4585 on 2008-04-28
> **loell said:**
> a number of people have problems with ugrading too, you could either reinstall gutsy or maybe do a clean hardy install.

Sorry, what I meant by upgrading was actually going from gutsy to hardy clean install from a CD install.  I actually first tried a install from the CD, that's when I noticed it, then i whipped off my hard drive, and installed gutsy, out of curiosity I upgraded to hardy and no errors at all.

I'm probably going to go to Gutsy.

---

### Post by loell on 2008-04-28
yeah, if its giving you a slow performance then downgrading would be good :)

i'm also keeping my gutsy partition, just in case.

---

### Post by chris4585 on 2008-04-28
> **loell said:**
> yeah, if its giving you a slow performance then downgrading would be good :)

i'm also keeping my gutsy partition, just in case.

Good thing for me its no biggie switching between system's.

---

### Post by FuturePilot on 2008-04-28
What does this say?
```
apt-cache policy totem-gstreamer
```

---

### Post by GeneW on 2008-04-29
I'm having the same problems.  Slow is not even the right word, maybe glacial would be a better description.  Totem runs at something like one frame a minute, I thought that it had locked up at first but then realized that it was still moving but very slowly.  Mplayer works fine but I'd rather use totem if I could get it to work.

---

### Post by loell on 2008-04-29
do what futurepilot suggested and paste it here.

---

### Post by GeneW on 2008-04-29
Fixed it.  Re-installing gstreamer-totem and then rebooting did the trick.

---

### Post by chris4585 on 2008-04-29
> **GeneW said:**
> Fixed it.  Re-installing gstreamer-totem and then rebooting did the trick.

wish i knew that before i installed gutsy back, i'll remember that next time i do install hardy, which probably will be a long while, my system is rock solid with gutsy so i'm not complaining at all.

---

### Post by Fidim on 2008-07-26
Hi:

I just registered to say I had the same problem, and solved it just like it has been said on this thread, installing gstreamer-totem and rebooting. Totem is going smooth now, sad thing Chris had to go back one version because i think hardy is nice.

Thanks!

---

### Post by chris4585 on 2008-07-26
> **Fidim said:**
> Hi:

I just registered to say I had the same problem, and solved it just like it has been said on this thread, installing gstreamer-totem and rebooting. Totem is going smooth now, sad thing Chris had to go back one version because i think hardy is nice.

Thanks!

hey, I'm on Hardy as my main system now, I didn't think anyone else would post on this thread again, well heres a update, I never did install gstreamer-totem (not sure) but how I got my problem fixed was killing pulseaudio every time worked, once i switched everything to alsa it just works flawlessly now. =)

---

### Post by leandromartinez98 on 2008-08-06
> **chris4585 said:**
> hey, I'm on Hardy as my main system now, I didn't think anyone else would post on this thread again, well heres a update, I never did install gstreamer-totem (not sure) but how I got my problem fixed was killing pulseaudio every time worked, once i switched everything to alsa it just works flawlessly now. =)

The same thing here. Killing pulseaudio makes the film run fine.
I had the problem running firefox, and when I closed firefox the
film could be seen. Now I realise that this pulseaudio killing solves
the problem as well. This is probably a pulseaudio or totem bug.

---

### Post by nittybitty on 2008-08-07
Same here. Super slow playback in totem, VLC is nice and fast. WTF

---

### Post by Lexicon101 on 2008-08-07
I hope pulseaudio is matured in intrepid.. it does seem nice, it just doesn't always work right.
(Although I've got mine right.. I'll edit this with a link to a post I found useful.)

EDIT: here it is...[Pulseaudio fixes.]("http://ubuntuforums.org/showthread.php?t=789578")

---

