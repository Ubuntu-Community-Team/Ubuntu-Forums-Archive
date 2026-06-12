---
title: "Why Linux is and Apple OS X not dependent on Codecs, plugins and softwares?"
date: 2009-10-14
forum: The Cafe
---

### Post by icett on 2009-10-14
I would wish to know why Linux is always dependent on propritory codecs, plugins, software and such stuff to function properly while Apple's OS X is not dependent on any of them? Has Apple created its own codecs, plugins, softwares etc. and are therefore not dependent on proprietory and Windows codecs, plugins, softwares etc? Also I think Apple has their own version of DirectX as there are some games which are native for OS X and some are being released within sometime. If so why Linux has not yet been able to create their own codecs, plugins, softwares etc. as well as to make OpenGL compatible for newer games so that Linux becomes completely independent?:)

---

### Post by myusername on 2009-10-14
> **icett said:**
> If so why Linux has not yet been able to create their own codecs, plugins, softwares etc. as well as to make OpenGL compatible for newer games so that Linux becomes completely independent?:)

we do. its just not as mainstream. look at the ogg codec.

---

### Post by mcduck on 2009-10-14
OSX is *very* dependant of extra codecs. By default it won't play wmv, divx, rm or many other proprietary media formats but instead you need to install 3rd-party applications (like Perian and Flip4mac) to add support for them. I know I had to install quite many 3rd partyy packages to ge all my media files working on OSX.

And Linux community *has* created it's own codecs, that's what you are using. The problem is that making your own codec won't remove the legal restrictions those formats have, so the codecs still can't be installed by default.

What comes to OpenGL, it's not possible to "make OpenGL compatible with new games", it's simply a question of if the game was programmed using OpenGL or DirectX. You can't make OpenGL to run a game that was programmed to use DirectX. Also Apple has no support for DirectX but uses OpenGL instead, just like Linux does.

edit: Also, OSX includes by default some codecs that are missing from Ubuntu, like MP3 for example. That's possible because Apple *pays for the license* that allows them to ship those codecs. Considering that Ubuntu is free of charge it would be quite a lot to ask for Canonical to pay for those codecs just so that you don't have to install them yourself.

---

### Post by madjr on 2009-10-14
> **mcduck said:**
> 

What comes to OpenGL, it's not possible to "make OpenGL compatible with new games", it's simply a question of if the game was programmed using OpenGL or DirectX. You can't make OpenGL to run a game that was programmed to use DirectX. Also Apple has no support for DirectX but uses OpenGL instead, just like Linux does.



What he's trying to say is that some Games like WoW have a native openGL port while we linux users have no native but have to use the windows version with Wine.

Also mac has an "cedega" thingie (commercial wine) and companies like ea release official "embeded" versions (similar to picassa on linux)

---

### Post by mcduck on 2009-10-14
> **madjr said:**
> What he's trying to say is that some Games like WoW have a native openGL port while we linux users have no native but have to use the windows version with Wine.

Also mac has an "cedega" thingie (commercial wine) and companies like ea release official "embeded" versions (similar to picassa on linux)

It's up to the game's creator to port it to OpenGL, nobody else can do that. Since the games are not open source, nobody else has the code that they could port.

Cedega is also available for Linux, and so are Crossover & Crossover Games. Actually they have been available for Linux much longer time than for OSX, since using such programs to run Windows apps only became possible on Macs after Apple moved to Intel architecture. In that sense both Cedega and Crossover are actually originally Linux apps that have been ported to OSX... ;)

---

### Post by t0p on 2009-10-14
OP: OSX needs codecs just as much as Linux.  You can't play an mp3 unless you have the software to play mp3s.  OSX has them installed by default. So do some Linux distros.  Others (like Ubuntu and Debian) don't.  But they're just a quick download away.

> **mcduck said:**
> Also, OSX includes by default some codecs that are missing from Ubuntu, like MP3 for example. That's possible because Apple *pays for the license* that allows them to ship those codecs. Considering that Ubuntu is free of charge it would be quite a lot to ask for Canonical to pay for those codecs just so that you don't have to install them yourself.

And there's Ubuntu's Free as in freedom philosophy.  Ubuntu won't include the mp3 codec by default because mp3 is not a Free codec.  Ogg is.  Ubuntu includes ogg, which is why you can play .ogg format files without having to download anything else.

---

### Post by SunnyRabbiera on 2009-10-14
> **t0p said:**
> OP: OSX needs codecs just as much as Linux.  You can't play an mp3 unless you have the software to play mp3s.  OSX has them installed by default. So do some Linux distros.  Others (like Ubuntu and Debian) don't.  But they're just a quick download away.



And there's Ubuntu's Free as in freedom philosophy.  Ubuntu won't include the mp3 codec by default because mp3 is not a Free codec.  Ogg is.  Ubuntu includes ogg, which is why you can play .ogg format files without having to download anything else.

Yeh but I think gstreamer can circumvent such things.

---

