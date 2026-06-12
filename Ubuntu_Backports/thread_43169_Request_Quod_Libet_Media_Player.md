---
title: "Request: Quod Libet Media Player"
date: 2005-06-21
forum: Ubuntu Backports
---

### Post by McQuaid on 2005-06-21
I've Seen this mentioned here in other forums and it's looks great.  Kind of surprised that it's not mentioned more.
[http://www.sacredchao.net/quodlibet](http://www.sacredchao.net/quodlibet) 

Looks like a good alternative to rhythmbox.  

Requesting quodlibet and it's extensions quodlibet-ext which are currently in breezy.

---

### Post by ametade on 2005-06-21
To install QuodLibet take a look at the following thread:

[http://www.ubuntuforums.org/showthread.php?t=41817](http://www.ubuntuforums.org/showthread.php?t=41817)

But I would rather prefer installing QuodLibet from backports, so I'm requesting it too :)

---

### Post by drummer on 2005-06-21
[QUOTE=ametade]To install QuodLibet take a look at the following thread:

[http://www.ubuntuforums.org/showthread.php?t=41817](http://www.ubuntuforums.org/showthread.php?t=41817)

But I would rather prefer installing QuodLibet from backports, so I'm requesting it too :)[/QUOTE]
 I agree, while it's fairly easy to install from the tarball.. it would be better/easier for many people to have it in backports to save having to resolve dependencies themselves as seen in the above link. It would hopefully also encourage more people to use such a great program.

---

### Post by pulp on 2005-06-21
I also second that. Although I would prefer a new Rhythmbox version, but the developers seem to be not collaborating very well. So everybody debugs and improves something but nobody puts it all together. So maybe Quod Libet is a good alternative

---

### Post by whatever on 2005-06-21
didn't know quod libet, tried it, liked it -> second request ^^

---

### Post by graabein on 2005-06-21
it looks nice. does anyone know if it works with gtkpod?

---

### Post by McQuaid on 2005-06-21
Well, I rebooted to sid just to check this out and it is pretty cool, but the one area where it's lacking is making your own custom playlists.  It's clunky to say the least right now.  But the next version will address this according to their website.  Also, a minor thing, but you have to edit configs to change the output to esd or alsa instead of being able to do it in the gui.  On the otherhand it does seemer quicker in loading large lists of songs (seems faster than rhythmbox).

I really like making my own playlists so I'll probably keep to rhythmbox for the time being but again it's still a great program that surprisingly doesn't get mentioned much.

---

### Post by sjmorgan on 2005-06-29
So is this a candidate for backporting or not? It looks pretty neat and I'm in need of an audio player because Hoary rhythmbox doesn't work for me with esound disabled (internal gstreamer error).

---

### Post by malte on 2005-12-02
In Dapper there's version 0.15. I'd like it backported, maybe with the MPC plugin too!
Thanks :)

---

### Post by Donza on 2005-12-02
One more vote for Quod Libet :)

---

### Post by suoko on 2005-12-12
How can I open an mp3 in quodlibet from nautilus ?
I tried adding quodlibet to nautilus applications but quodlibet starts without opening the selected file.

---

### Post by Dax0r on 2005-12-18
nice software

---

### Post by jannol on 2005-12-20
I think it should be default

---

### Post by ember on 2005-12-22
For anyone interested: I have made a personal backport of QuodLibet, QuodLibet-Ext and QuodLiebet-Plugins (0.16). Download the debs at [my personal backports site]("http://www.doeweling.com/dists/breezy-backports-staging/universe/").

Please note that you will have to upgrade python-gst, too. For building I had to upgrade debhelper, but I guess that won't be necessary just for using it. Also you could install a new version of python-ctypes, but that is also not compulsory.

There's no warranty, so there's a small risk of braking something. However it works for me.

Best,
ember

---

### Post by piedamaro on 2006-01-08
Thanks a bunch! ;)

---

### Post by tonderai on 2006-01-18
Thanks. 

Its a real relief not to have to compile in that flac and musepack support any more :) Does quodlibet now use gstreamer?

---

### Post by Gnobody on 2006-01-20
Does Quod Libet now support Gstreamer 0.10.1?  If so, this would become my ideal music jukebox since I've rolled my own Gstreamer 10 debs.

---

