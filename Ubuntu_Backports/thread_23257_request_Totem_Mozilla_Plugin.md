---
title: "request: Totem Mozilla Plugin"
date: 2005-04-01
forum: Ubuntu Backports
---

### Post by Nis on 2005-04-01
For Hoary (when it's released).  According to [this](http://bugzilla.gnome.org/show_bug.cgi?id=144937) Totem now has a working Mozilla plugin.  Would it be possible to backport this into hoary-extras?

---

### Post by bored2k on 2005-04-01
[QUOTE=Nis]For Hoary (when it's released).  According to [this](http://bugzilla.gnome.org/show_bug.cgi?id=144937) Totem now has a working Mozilla plugin.  Would it be possible to backport this into hoary-extras?[/QUOTE]
 Whats wrong with [http://ubuntuforums.org/showthread.php?t=17727](http://ubuntuforums.org/showthread.php?t=17727) method ?

edit > nevermind , official totem is wicked awsome ./

---

### Post by NeoChaosX on 2005-04-01
Mozplugger doesn't allow for controls to be used with embedded movies, like in [this](http://www.hadess.net/blog/images/totem-mozilla-plugin.jpg) screenshot with the Totem plugin.

---

### Post by bored2k on 2005-04-01
[QUOTE=NeoChaosX]Mozplugger doesn't allow for controls to be used with embedded movies, like in [this](http://www.hadess.net/blog/images/totem-mozilla-plugin.jpg) screenshot with the Totem plugin.[/QUOTE]
 Nice, nevermind then ^_^ .
*knock knock jdong*

---

### Post by RastaMahata on 2005-04-01
I say go for it, this is a ++

---

### Post by JDay on 2005-04-07
Well, I'd certainly love to see this. Mozplugger hasn't worked very well and is suboptimal even when working as intended. I've been forced to install mplayer and its plugin which seems bloated and dirty to me.

---

### Post by Nis on 2005-04-07
[QUOTE=JDay]Well, I'd certainly love to see this. Mozplugger hasn't worked very well and is suboptimal even when working as intended. I've been forced to install mplayer and its plugin which seems bloated and dirty to me.[/QUOTE]
 Until the official Totem Mozilla plugin infects our browsers you can always use [this HOWTO](http://ubuntuforums.org/showthread.php?t=17727) to embed Totem in Firefox using mozplugger.  This came about after many hours of frustration with Mplayer and mplayerplug-in and its horrible UI.

---

### Post by Remix_88 on 2005-04-13
The topic below bescribes how to re-package Totem to include the Mozilla plug-in. Is this enough to help get it backported?

[http://ubuntuforums.org/showthread.php?t=21405](http://ubuntuforums.org/showthread.php?t=21405)

---

### Post by JDay on 2005-04-14
It would be great if we could get 1.1.1 from breezy which includes "major enhancements to the experimental mozilla plugin." The version in hoary only seems to only work well with quicktime (although I haven't been able to compile the breezy plugin, so it might not actually be much better).

---

### Post by jdong on 2005-04-14
Excellent, this is enough info to file this into a backport :)

---

### Post by Remm on 2005-04-14
I think anything Totem or gstreamer related is worth backporting. In Hoary, totem-gstreamer has rather serious issues (for me, even after enabling dma on the dvd player, DVD playback is choppy, and there are problems playing certain files, while totem-xine works perfectly for everything).

---

### Post by RastaMahata on 2005-04-26
[QUOTE=Remm]I think anything Totem or gstreamer related is worth backporting. In Hoary, totem-gstreamer has rather serious issues (for me, even after enabling dma on the dvd player, DVD playback is choppy, and there are problems playing certain files, while totem-xine works perfectly for everything).[/QUOTE]
 bumping threads here :P

I hope this gets backported anyway :D

About what you say, totem-gstreamer is unable to get binary files (plugins) to play other files, whi totem-xine is able. Although there's a recent post in the backports forums about a plugin that would allow totem-gstreamer to use the plugins from the w32codecs package.

---

### Post by SKLP on 2005-05-06
we need this :)

(bump)

---

### Post by zafar on 2005-05-12
I've been waiting for this aswell and would like to see a backport released. Also, i saw the guide for creating backports and followed it as best I could and I've got two debs that include the totem mozilla plugin.. You can [download the xine version](http://z.narutochaos.com/ubuntu/totem-xine_1.1.1-0ubuntu3_i386.deb) or [the gstreamer version](http://z.narutochaos.com/ubuntu/totem-gstreamer_1.1.1-0ubuntu3_i386.deb). Since they are my first backports and I have no idea if they even work outside my system, I didn't want to submit them, but if you would like to try em out, go ahead :-) .

---

### Post by JDay on 2005-05-12
You can also get the version from Breezy which supposedly has improvements to the mozilla plugin.
[Gstreamer version](http://archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstreamer_1.1.1-0ubuntu3_i386.deb)
[Xine version](http://archive.ubuntu.com/ubuntu/pool/universe/t/totem/totem-xine_1.1.1-0ubuntu3_i386.deb)
[Dummy package](http://archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_1.1.1-0ubuntu3_all.deb)
I've used these for several weeks of a few different Hoary boxes with no problems. I recommed you use the Xine version and make sure you have w32codecs installed (you can get it from backports' extras repository). To install:
```
sudo dpkg -i totem*.deb
```
And to use in firefox:
```
sudo ln -s /usr/lib/mozilla/plugins/libtotem_mozilla.* /usr/lib/mozilla-firefox/plugins/
```

---

### Post by zafar on 2005-05-12
[QUOTE=JDay]You can also get the version from Breezy which supposedly has improvements to the mozilla plugin.
[Gstreamer version](http://archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstreamer_1.1.1-0ubuntu3_i386.deb)
[Xine version](http://archive.ubuntu.com/ubuntu/pool/universe/t/totem/totem-xine_1.1.1-0ubuntu3_i386.deb)
[Dummy package](http://archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_1.1.1-0ubuntu3_all.deb)
I've used these for several weeks of a few different Hoary boxes with no problems. I recommed you use the Xine version and make sure you have w32codecs installed (you can get it from backports' extras repository). To install:
```
sudo dpkg -i totem*.deb
```
And to use in firefox:
```
sudo ln -s /usr/lib/mozilla/plugins/libtotem_mozilla.* /usr/lib/mozilla-firefox/plugins/
```[/QUOTE]

The debs I built are from the latest breezy version compiled using Hoary libs/packages. You also have to link the plugins from moziilla to mozilla-firefox for the ones i built too.

---

### Post by Spif on 2005-05-13
Can't install the Totem plugin on Hoary, as it needs libc6 version 2.3.4-1 or higher.

jdong, could you please backpot libcs6?

---

### Post by Technoviking on 2005-05-13
I have a backport ready, but it is installing the plugin to /usr/lib/mozilla/plugins and not to /usr/lib/mozilla-firefox/plugins. As soon as I get this figured out I will upload it to backports.

Mike

---

### Post by Technoviking on 2005-05-14
I have uploaded the new totem (1.1.1)  to hoary-backport-staging/main. It works great, but has two know issues.

1. You will need to link the plugins to the firefox.
```
sudo ln -s /usr/lib/mozilla/plugins/libtotem_mozilla.* /usr/lib/mozilla-firefox/plugins/
``` 
2. There is a bug showing gifs. Totem will show up with a fd:\\0 message. This is a known bug, and the Totem developers know about it.

Mike

---

### Post by stoffe on 2005-05-15
[QUOTE=Mike Basinger]I have uploaded the new totem (1.1.1)  to hoary-backport-staging/main. It works great, but has two know issues.

1. You will need to link the plugins to the firefox.
```
sudo ln -s /usr/lib/mozilla/plugins/libtotem_mozilla.* /usr/lib/mozilla-firefox/plugins/
``` 
2. There is a bug showing gifs. Totem will show up with a fd:\\0 message. This is a known bug, and the Totem developers know about it.

Mike[/QUOTE]
 Seems to work just fine, many many thanks! =)

 I had so much trouble with the stupid vlc plugin it was unimaginable, now it just seems to work. The functionality seems a bit limited, but it is already miles better. Thanks again!

---

