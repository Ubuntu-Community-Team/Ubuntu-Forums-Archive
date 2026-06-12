---
title: "New: PPA to re-enable system-wide JACK support"
date: 2009-10-23
forum: Ubuntu Studio
---

### Post by motin on 2009-10-23
Hi Ubuntu Studio users!

For years the stripped JACK support in Ubuntu has really been limiting Ubuntu user's ability to easily use this brilliant piece of software in their Ubuntu environment. 

For casual audio usage, we should still be able to surf on Youtube, answer Skype calls, watch a casual movie or listen to music without needing to shut down all our JACK connections... 

I have for long wanted an easy way to re-enable this support, and now I have put some jack-enabled packages in [https://launchpad.net/~motin/+archive/until-jack-is-included-in-main](https://launchpad.net/~motin/+archive/until-jack-is-included-in-main)

Do we want to put this in Ubuntu Studio's PPA instead and help each other maintain JACK-supported versions there? If so, please inform me how to access the PPA :)

If anyone is interested helping out, I'll polish and upload my notes on how to rebuild and put packages in the PPA, so that packages can be built very soon after a published Ubuntu update of the packages. 

Cheers!

Fredrik aka Motin

---

### Post by kayosiii on 2009-10-23
You rock :)

---

### Post by Stochastic on 2009-10-23
You really rock.

It does sound like Jack will get back into Main for Lucid's release.

---

### Post by AutoStatic on 2009-10-24
That would be awesome :)

---

### Post by Pablo_F on 2009-12-29
Hi Motin,

Thank you very much for your efforts! I am another "jack only" guy who wants jack support for all sounds in his PC.

I have two comments on your PPA.

1) The version name in the package "libxine1" (and related) ends with "+withjack1" whereas in portaudio2 ends with "+withjack2". Has this something to do with support for Jack1 OR Jack2 (aka jackdmp)? I don't think so, but it could be misleading. If you don't mind, confirm this point please.

2) I am not using alsa or pulseaudio plugins for jack, which in my case I would need for the flash player only. Instead, I am using the flash plugin for jack by Torben Hohn, as documented here:

[http://www.linuxmusicians.com/viewtopic.php?f=4&t=2323](http://www.linuxmusicians.com/viewtopic.php?f=4&t=2323)

I think this is the best solution for getting jack support for youtube, vimeo, myspace... 

I wish you made a deb package for this in your PPA!

Thank you again. You have saved me a lot of trouble.

I also hope Ubuntustudio Lucid is much more jack friendly.

Cheers! Pablo.

---

### Post by bluesscream on 2010-01-01
one more who would cavernously breath out. Tx Motin!

---

