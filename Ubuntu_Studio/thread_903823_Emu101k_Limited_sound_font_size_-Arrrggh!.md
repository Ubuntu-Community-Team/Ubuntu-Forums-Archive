---
title: "Emu101k Limited sound font size -Arrrggh!"
date: 2008-08-28
forum: Ubuntu Studio
---

### Post by Lensman99 on 2008-08-28
I don't even know how to tell you how pissed off I am at the world

The latest: I'm running Ubuntu Studio with Sound blaster Live (Emu10k1). I want to load large soundfonts, but I'm limited to about 128MB. It basically works fine otherwise.

I found this:
[http://alsa.opensrc.org/index.php/Emu10k1](http://alsa.opensrc.org/index.php/Emu10k1)

Look for the part that says:
------------------
BIG SOUNDFONT: By default, you can not load for more as 128MB soundfont with those cards. If you want to load more, it is very easy.

    * Add the following option for the emu10k1 module: 

options snd-emu10k1 max_buffer_size=<size_in_MB>
-----------------

In steps a baby would understand, can you please tell me where to find the emu10k1 module file, and where to find these options, as I've been looking all night, and havent found anything that looks right. I've got my /etc/modules file but it doesn't seem like the right place to put it. All it contains is:

----------
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
fuse
snd-seq
------------

 HELP!!!

---

### Post by Stochastic on 2008-08-28
> **Lensman99 said:**
> In steps a baby would understand...
A baby wouldn't be able to understand how to do this.

Really, they're talking about rebuilding the alsa module with a particular feature changed in the snd-emu101k module.  That's not baby's work - you can seriously break your software doing this.  If you're insistant on getting this setting changed, I'd talk to the guys in the #lad IRC channel or their mailing list ([http://lad.linuxaudio.org/index.html](http://lad.linuxaudio.org/index.html) for more info).

How much memory is on your card anyway?

I'd just stick with 128mb or less on that card and use Qsynth for the other fonts.

p.s. to find the file they're talking about do ```
locate snd-emu101k
```

---

### Post by Lensman99 on 2008-08-29
Hi Stochastic.. thanks

You'll be happy to know, I'm no longer feeling like killing my PC... Amazing what a good night's sleep can do. :)

Actually, the sound card uses system memory, but the performance is a Lot better than using a soft synth. I have a soundfont that is 'GM plus extras I've added' that adds up to about 225MB (It has a really big and sweet piano).

Re this problem: if it's that tricky, maybe I'll do some cutting down and get it under the size limit.

Sigh... I just want to make music, not spend years tweaking my PC.

Thanks again,

Mike

---

