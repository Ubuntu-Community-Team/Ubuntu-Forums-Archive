---
title: "*sigh* There goes another potential user"
date: 2008-11-15
forum: Testimonials &amp; Experiences
---

### Post by DrSpirograph on 2008-11-15
So our DVD player broke, and being a student household, I said "no problem I'll just stick Ubuntu on my flat mate's old laptop that they never use. Linux is so solid, so much more reliable than Windows".

How embarassing:
I installed MythBuntu on it, which turns out to be harder to get DVD decryption going than regular Ubuntu on my laptop.

The TV-out won't work because it turns out to be a legacy ATI card in the laptop - now I kind of understand this, Linux support is all volunteers, if no one who has this card gets it working.

But the two killers are:
a) VCD support is intermittent - some VCD's just won't play on either mplayer or xine for no reason I can figure
and
b) ALSA disappeared!
No kidding, one day we powered it on, and suddenly there's no sound, hmmm that's weird, check the debug output, hmmm ALSA and OSS xine plugins can't open the device.
Hmmm, that's because the device is gone!
No /dev/snd !
no /proc/asound !
Just disappeared over night!

More reliable than windows, boy am I eating those words!

So the upshot is I don't think my flatmate is going to be rushing to try out Ubuntu for themselves.

If you seriously want to tackle Launchpad bug #1, sound systems suddenly disappearing simply CANNOT make it into a release, I don't understand how that sort of thing happens, I really, really don't.

/rant

---

### Post by armandh on 2008-11-15
when unexplained things start happening I always think bad hardware first. [that is my experience]

I'm using an old 866 P-III with 512 ram, with a newer 128meg video hdmi connected to a flatscreen in the family room and it handles the 1080-P AV just fine.

perhaps there is a reason that one was unused?
PS +1 on VLC, and dont forget flash 10

---

### Post by wolfen69 on 2008-11-15
> a) VCD support is intermittent - some VCD's just won't play on either mplayer or xine for no reason I can figure
you just need to install extra codecs. gstreamer-good,bad,ugly, and also try vlc.

> b) ALSA disappeared!
you just need to remove pulseaudio, install esound, and set the default sound to alsa.

> No /dev/snd !
no /proc/asound !
with a little more digging and patience(ask for help) i'm sure it's fixable.

did you try another distro? i've installed linux on alot of computers and sometimes when one doesn't work right another one will. mandriva one 2008.1 has great hardware support.

ubuntu is NOT a 1 size fits all. use the right OS for the right hardware.

---

### Post by sirjoebob on 2008-11-15
> **DrSpirograph said:**
> 
a) VCD support is intermittent - some VCD's just won't play on either mplayer or xine for no reason I can figure


I would second the nomination for trying VLC. It is the ONLY video player I use regardless of OS. Also, you may want to try regular Ubuntu since it is easier to get going. I use my Ubuntu laptop with my TV and it works PERFECT. It does have an Nvidia card though. Good luck and don't hesitate to keep posting questions!

---

### Post by oldsoundguy on 2008-11-15
the amount of ram has not been mentioned.  I have a Myth set up running on a 1.2 AMD,  A Mint setup running on a 466 celreon, 8,10 running on a PIII 733, 8.10 running on a pIII 1.2, and 8,10 running on a pIV 2.4.
ALL machines have AT LEAST 768mb of ram and most have 1g. NO VIDEO ISSUES on any of them.

---

### Post by ugm6hr on 2008-11-15
I would have suggested regular Ubuntu (or whatever distro you use normally).

I have found that experimenting with Ubuntu media variants throws up different (unexpected) issues that can be confusing.  I also experimented with XBMC and Elisa on an Ubuntu base too... but they are slow and unreliable on old hardware.

My final solution was to use regular Ubuntu 8.04 with VLC (after removing gstreamer, totem, mplayer, xine etc) for my mum and a friend.  Both have had no problems since; Ubuntu then defaults to VLC as media player, which is pretty reliable.  A quick edit of the startup services and the menu / panels and it looks a lot tidier.

---

### Post by cshaobu830633 on 2008-11-16
hello ,everyone who know how to make [runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php) fast??

---

