---
title: "XGL/Compiz ready for the desktop?"
date: 2006-08-18
forum: The Cafe
---

### Post by 3rdalbum on 2006-08-18
I occasionally use XGL and Compiz, and I've gotta say that there are some big issues which stop me from having it as my default session.

1. Clicking the launchers in the Gnome panel cause horrible visual artifacts.
2. The screen-dimming effects used by Gksudo and the Log Out screen make the background go all funny. Oh, and screen capture programs don't work on an XGL session.
3. The Shift-Delete combination for killing XGL is something I accidentally hit once an hour, so I lose my unsaved work.
4. Sometimes, my windows just disappear off my screen and off my taskbar for no reason. If I do the Expose effect they appear, and clicking on them brings them partially back onto the screen and back onto the taskbar. I have to right-click their entry on the taskbar and do a "Move" in order to get them fully back.
5. Nexuiz seems to crash X or XGL when running an XGL session.
6. When Gnome is loading, the background of the splash screen is an ugly grey. Also, my desktop pagers are white on an XGL session, rather than transparent to the colour of the panel. Ugly!

So my question is: How ready are XGL and Compiz for the desktop, and why? Are some of these just isolated incidents, caused by buggy ATI drivers and my sloppy typing style; or are they real problems which prevent the system's adoption?

---

### Post by GuitarHero on 2006-08-18
Both are still pretty early in development.  Give them time to mature and they will be much more stable.

---

### Post by Iandefor on 2006-08-18
You're aware that both are stopgap hacks on the verge of being consigned to the dustbin? XGL was a stopgap until we finally got AIGLX in Xorg- which has happened. Compiz was a stopgap until metacity finally got compositing- the next stable of GNOME is slated to have the metacity compositor compiled in. Now at this point, they're about to become pointless. ATI has already released updated drivers for the new Xorg and NVIDIA says it'll follow suit in September. By Edgy, the infrastructure for an XGL/Compiz-less desktop that's faster, more stable, and just as cool should be in place.

Oh, and XGL/Compiz are still alpha products anyways.

---

### Post by 23meg on 2006-08-18
[QUOTE=Iandefor]NVIDIA says it'll follow suit in September.[/QUOTE]Source?

---

### Post by Iandefor on 2006-08-18
> **23meg said:**
> Source? My magic jump-to-conclusions box, silly!

Can't find the source at the moment, will post again when I find it.

---

### Post by mcduck on 2006-08-18
> **3rdalbum said:**
> I occasionally use XGL and Compiz, and I've gotta say that there are some big issues which stop me from having it as my default session.

1. Clicking the launchers in the Gnome panel cause horrible visual artifacts.

If you are talking about the ugly wirefame animations, it's not a feature of compiz but Gnome. You can disable it with gconf-editor.
> 
2. The screen-dimming effects used by Gksudo and the Log Out screen make the background go all funny. Oh, and screen capture programs don't work on an XGL session.

Never noticed anything funny. And screencapture works fine for me.
> 
3. The Shift-Delete combination for killing XGL is something I accidentally hit once an hour, so I lose my unsaved work.

For some reason I've never had that problem myself. But there are howto's in both this and Compiz forums about fixing that.
> 
4. Sometimes, my windows just disappear off my screen and off my taskbar for no reason. If I do the Expose effect they appear, and clicking on them brings them partially back onto the screen and back onto the taskbar. I have to right-click their entry on the taskbar and do a "Move" in order to get them fully back.

Doesn't happen to me. Are you running XGL/COmpiz from Ubuntu repositories or from QuinnStorm's repositories?
> 
5. Nexuiz seems to crash X or XGL when running an XGL session.

All 3D-games I've tried work fine, but I haven't tried Nexuiz. Have you searched the Compiz forums, as most likely somebody already has a solution for that.
> 
6. When Gnome is loading, the background of the splash screen is an ugly grey. Also, my desktop pagers are white on an XGL session, rather than transparent to the colour of the panel. Ugly!

I agree about the background, but I don't see it as a problem as it's only visible for very short time when logging in. The Workspace Switcher uses GTK colors, I've never seen it being transparent in Gnome, not even in regular Gnome session. So it depends on the GTK theme you are using.
> 
So my question is: How ready are XGL and Compiz for the desktop, and why? Are some of these just isolated incidents, caused by buggy ATI drivers and my sloppy typing style; or are they real problems which prevent the system's adoption?

If you ask me, they are as reafy as anything. If you have hardware that supports using them, you can usually make them work to your liking. But they don't work for everybody, and you must be prepared to do some researching to solve your possible problems. This far I've installed XGL/Compiz on 4 machines including my laptop with no problems that couldn't be solved with either a quick search on Compiz forums or tuning some setting in gconf-editor.

---

### Post by cord on 2006-08-18
> **Iandefor said:**
> My magic jump-to-conclusions box, silly!

Can't find the source at the moment, will post again when I find it.

I dont have the september figure, but the fact that they are releasing aiglx compatible driver was stated on their official forums.

edit: forgot to say

I have been using xgl/compiz since 1-2 days after I installed ubuntu (which was like last week). It has not given me much issues after I set it up how I liked it (disabled wobbly, water, 2 bottom corner actions, etc...) the only issues I have which really bug me are the following:

1. the fact that its somewhat of a pain to play 3d games with it
2. horrible video playing that I experience. really really bad such that whenever I want to watch videos for an extended period I reboot to windows.

---

### Post by gnomeuser on 2006-08-18
I have Compiz running on AIGLX here with very few problems, I also believe that Fedora are moving towards replacing Metacity with Compiz if not for Fedora Core 6 then for 7. I honestly believe Compiz at least will be the official window manager in GNOME soon.

XGL is the stepping stone towards xegl which is what we really want, an X server written on top of OpenGL entirely with fallback on software (MESA). AIGLX is an more evolutionary approach then XGL and since that has seen adoption upstream it wouldn't surprise me if that would become the solution of choice for a while.

---

### Post by fuscia on 2006-08-18
i'll be waiting for the dumbass version to come out before i try it again.

---

### Post by orbital on 2006-08-18
I haven't been able to play Enemy Territory after installing XGL/Compiz

---

### Post by 3rdalbum on 2006-08-18
I did hear that nVidia were in the process of adding AIGLX support in their proprietry driver and that it should come later this year. So September seems a fairly reasonable bet.

> **mcduck said:**
> If you are talking about the ugly wirefame animations, it's not a feature of compiz but Gnome. You can disable it with gconf-editor.

I read your post, and after two minutes of searching I found the setting. Thanks :-)

> **mcduck said:**
> Never noticed anything funny. And screencapture works fine for me.

Yeah, I was wondering why everyone else could get screen captures and not me :-)

> **mcduck said:**
> Doesn't happen to me. Are you running XGL/COmpiz from Ubuntu repositories or from QuinnStorm's repositories?

From Quinn's, which is what surprised me. Just updated to a new version now though, so hopefully that's fixed the problem.

And admittedly Nexuiz is the only real 3D game I've tried. I wouldn't play it in XGL, as I've only got a minimum of memory anyway.

> **mcduck said:**
> The Workspace Switcher uses GTK colors, I've never seen it being transparent in Gnome, not even in regular Gnome session. So it depends on the GTK theme you are using.

I have my panels semi-transparent, but I was mistaken when I wrote that part of my message. The switcher is usually grey, and the desktop background at that part is grey, so the switcher looks transparent to me.

Also I just did an apt-get update and found some new mesa packages from Quinn's, so maybe they fix some important stuff.

---

### Post by GoA on 2006-08-18
> **mcduck said:**
> 
If you ask me, they are as reafy as anything. If you have hardware that supports using them, you can usually make them work to your liking. But they don't work for everybody, and you must be prepared to do some researching to solve your possible problems. This far I've installed XGL/Compiz on 4 machines including my laptop with no problems that couldn't be solved with either a quick search on Compiz forums or tuning some setting in gconf-editor.

Yes, it isn't that hard to set it up. Out there are bugs and it's still too diffecult to install for basic user. There have been a lot of questions and problems with XGL installation and broken X etc. It has to be as simple as click on a mouse or an automatix install, with an option to revert back to old config if it doesn't work.

---

### Post by halucard22 on 2006-08-18
Hi everyone !!
I've read some posts about xgl (english and french) but never found a post talking about the old video cards. In some wiki, there is a list of supported video cards but i didn't read any notice about the technicals specifications in order to have a usuable desktop like MAC OS X.
I've got a G4 Ti 4200, 64Mb. Every time I launch a XGL/Compiz-Quinn session, it works fine but it's very slow when I run some applications like klibido, firefox, evolution, beagle in the same time.
Whithout XGL, the same applications run very fine together, no lags.
Yes, I know it's still in developpement, updates are very fast but it's still slow ... in my case.
So, everyone can tell me if it's normal, where to find a howto to optimize, etc.

PS: sorry if my english is a little bad.

---

### Post by GoA on 2006-08-18
Too old display adapter.

---

### Post by robinl on 2006-08-20
Well compiz had been very good lately with all the new plugins and very active development. If compiz was able to accomplish all this in such a short amount of time and considering metacity had been around far longer than compiz, compiz may as well be the default in edgy +2 or something... But I agree with XGL is not ready. 3D games and extended input devices (graphics tablets anyone?) are the two major setbacks for me and I had to go back to Windows to use those two features (vanilla metacity lags for some reason...)...](*,)

---

