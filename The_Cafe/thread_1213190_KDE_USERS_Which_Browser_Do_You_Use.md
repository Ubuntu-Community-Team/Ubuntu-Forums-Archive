---
title: "KDE USERS: Which Browser Do You Use?"
date: 2009-07-14
forum: The Cafe
---

### Post by izizzle on 2009-07-14
I'm just curious to know what other KDE users use as a browser. I'm trying to shift over from Firefox to Konqueror but I have some flash issues. What do you guys use?

---

### Post by Skripka on 2009-07-14
Konqueror when run with the KDEWebkit Kpart is fast and speedy and renders things great (just as fast as Midori...and only slightly slower than Windows Safari).  Konqueror's greatest liability is KHTML.  The biggest problem with Konqueror currently is that kio_http multiplies like bunny rabbits and does not go away until your machine bogs down.


Until kio_http behavior is fixed I'm on Opera10 Qt4 64bit.

---

### Post by vishzilla on 2009-07-14
I use Fx 3.5.. it suits my needs with the addons and all.. with QtCurve you won't its a non-Qt app.

---

### Post by fatality_uk on 2009-07-14
Firefox.

---

### Post by khelben1979 on 2009-07-14
Firefox 3.5. Works excellent.

---

### Post by SuperSonic4 on 2009-07-14
Firefox, I would use konqueror but checking my bank online is a must. Plus the flashblock extension is a bandwidth hero

---

### Post by izizzle on 2009-07-14
> **Skripka said:**
> Konqueror when run with the KDEWebkit Kpart is fast and speedy and renders things great (just as fast as Midori...and only slightly slower than Windows Safari).  Konqueror's greatest liability is KHTML.  The biggest problem with Konqueror currently is that kio_http multiplies like bunny rabbits and does not go away until your machine bogs down.


Until kio_http behavior is fixed I'm on Opera10 Qt4 64bit.

Care to enlighten me on how I can run Konqueror with KDEWebkit Kpart? :P

---

### Post by doorknob60 on 2009-07-14
I used to use Konqueror, and it's still a great browser, but lately I've gotten hooked on a few greasemonkey scripts (and StumbleUpon) so if I still used KDE I would consider Firefox.

---

### Post by Skripka on 2009-07-14
> **izizzle said:**
> Care to enlighten me on how I can run Konqueror with KDEWebkit Kpart? :P

1)  You'll need to go hunting for kdewebkit (or something to that effect) in Synaptic, in the description it should call it "kpart"...probably something like:

```

#apt-get install webkitkde

```

See: [http://packages.ubuntu.com/jaunty/webkitkde](http://packages.ubuntu.com/jaunty/webkitkde) for description

then

2) in a terminal in KDE:
```

#keditfiletype text/html

```

3) in the Window that pops up from #2, click on the "embedding" tab-and move "Webkit (kdewebkit kpart)" to the top of the list.  This will make Konqueror use Webkit by default-if you want to undo your jandiwork, move "KHTML" back to the top.

4) restart Konqueror, and you'll be using Konqueror/Webkit by default

---

### Post by izizzle on 2009-07-14
Thanks skripka. It seems nice, but really buggy. I can't access my yahoo mail with it and fonts are too small. I reverted to KHTML.

---

### Post by OutOfReach on 2009-07-14
Firefox 3.5.

---

### Post by Sxeptomaniac on 2009-07-14
> **SuperSonic4 said:**
> Firefox, I would use konqueror but checking my bank online is a must. Plus the flashblock extension is a bandwidth hero

Seconded.  Flashblock has become my favorite add-on.

---

### Post by swoll1980 on 2009-07-14
Firefox. Konqueror is garbage.

---

### Post by garba on 2009-07-14
i wonder why khtml is still around, who's using it anyway? tried arora on karmic and it's great, still needs some work but webkit is the way to go

---

### Post by descendent87 on 2009-07-14
Arora, it's going to be the default in kubuntu karmic and it's really improved. Only thing I would like is an adblock plugin and ability to store passwords then it would be perfect

---

### Post by izizzle on 2009-07-14
How can I use arora on Kubuntu 9.04 64-bit? I only found a i386 version [HERE]("http://code.google.com/p/arora/downloads/list").

---

### Post by Skripka on 2009-07-14
> **izizzle said:**
> How can I use arora on Kubuntu 9.04 64-bit? I only found a i386 version [HERE]("http://code.google.com/p/arora/downloads/list").

Should be in the repos....another equivalent of Arora is Rekonq.

---

### Post by izizzle on 2009-07-14
I downloaded arora 0.5 from the repos and it starts up then freezes and I have to kill it. Here is the Konsole output:

```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
server bind: Address already in use
*** NSPlugin Viewer  *** ERROR: failed to initialize plugin-side RPC server connection
Killed

```

Any ideas?

---

### Post by Exershio on 2009-07-14
> **izizzle said:**
> I downloaded arora 0.5 from the repos and it starts up then freezes and I have to kill it. Here is the Konsole output:

```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
server bind: Address already in use
*** NSPlugin Viewer  *** ERROR: failed to initialize plugin-side RPC server connection
Killed

```

Any ideas?

Not sure what the errors mean exactly, but try using a more recent release. 0.7.1 is the latest "stable" release. Also helps if you use a more recent QtWebKit.

I'm about to give Arora a try, compiling both the latest commit of QtWebKit and Arora.

---

### Post by Zorael on 2009-07-14
I use a mix, having a hard time deciding on what to use as my main browser. I keep returning to Firefox largely because of some extensions I can't seem to do without, but it's so sluggish (much like other GTK apps) I keep thinking about switching to Konqueror, Arora or rekonq.

My main issue with Konqueror is page compatibility. (Developers of) KHTML have directed criticism towards Mozilla for "bending over" to bad HTML coding habits instead of sticking to the standard, but to the end user one app works with Gmail and the other doesn't. Sure, you can set it to use Webkit, but then it doesn't honor Konqueror options (like *FONT SIZE*, which **should** be set to Serif 16pt as default) and generally feels like a token gesture instead of something that could combine a proven interface (Konqueror) with a proven rendering engine (Webkit). I'll not go into whether KHTML is bad or not, since I lack the expertise to place the blame accurately.

My main issue with rekonq is that it's really just a developers' plaything, at least at the moment. It's arguably just the Qt webkit test app, given a new name and some basic functionality, yet it has the feel of a KDE app. As such it's keenly dbus-aware, so it could (allegedly) easily be converted into giving each tab its own process like Chromium does. Did you know "browser crash" is as common as to get its own quasi-verb in Japanese? burakura suru. Gotta love those portmanteaus.

My main issue with Arora is the lack of KDE integration. Every other app I use *fits* into my environment. Arora, much like Firefox, just don't mix with the rest, which is unfortunate. If there were some better KDE integration, proper Java support, Greasemonkey scripting (in the making currenty afaik) / extensions, it would be my default. As it currently is, it isn't.

The ideal browser for me would be a Qt Firefox with attention given to KDE integration; snappy, sharing code, and consistent. Or a rekonq with a real interface, and with real features. Or a KDE Arora, but with it aiming to be portable, I'm not expecting very much. Hoping though.

---

### Post by Tipped OuT on 2009-07-14
Gotta love that Firefox. :p

---

### Post by Skripka on 2009-07-14
> **izizzle said:**
> I downloaded arora 0.5 from the repos and it starts up then freezes and I have to kill it. Here is the Konsole output:

```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
server bind: Address already in use
*** NSPlugin Viewer  *** ERROR: failed to initialize plugin-side RPC server connection
Killed

```

Any ideas?

Get a newer version-0.5 was bad even by beta standards-the current is 0.7, and has been out for a few months now....and is fairly good.

---

### Post by Skripka on 2009-07-14
> **Zorael said:**
> I use a mix, having a hard time deciding on what to use as my main browser. I keep returning to Firefox largely because of some extensions I can't seem to do without, but it's so sluggish (much like other GTK apps) I keep thinking about switching to Konqueror, Arora or rekonq.

My main issue with Konqueror is page compatibility. (Developers of) KHTML have directed criticism towards Mozilla for "bending over" to bad HTML coding habits instead of sticking to the standard, but to the end user one app works with Gmail and the other doesn't. Sure, you can set it to use Webkit, but then it doesn't honor Konqueror options (like *FONT SIZE*, which **should** be set to Serif 16pt as default) and generally feels like a token gesture instead of something that could combine a proven interface (Konqueror) with a proven rendering engine (Webkit). I'll not go into whether KHTML is bad or not, since I lack the expertise to place the blame accurately.

My main issue with rekonq is that it's really just a developers' plaything, at least at the moment. It's arguably just the Qt webkit test app, given a new name and some basic functionality, yet it has the feel of a KDE app. As such it's keenly dbus-aware, so it could (allegedly) easily be converted into giving each tab its own process like Chromium does. Did you know "browser crash" is as common as to get its own quasi-verb in Japanese? burakura suru. Gotta love those portmanteaus.

My main issue with Arora is the lack of KDE integration. Every other app I use *fits* into my environment. Arora, much like Firefox, just don't mix with the rest, which is unfortunate. If there were some better KDE integration, proper Java support, Greasemonkey scripting (in the making currenty afaik) / extensions, it would be my default. As it currently is, it isn't.

The ideal browser for me would be a Qt Firefox with attention given to KDE integration; snappy, sharing code, and consistent. Or a rekonq with a real interface, and with real features. Or a KDE Arora, but with it aiming to be portable, I'm not expecting very much. Hoping though.

I will say the latest Git builds of Rekonq for Arch, 0.1.8 is quite good.  The only functional things it really misses for being a good minimalist browser are session saving and autoscrolling.

Another to try that isn't minimalist is the latest Opera10 Qt4 shared builds-that are available for BOTH  (gasp) 32 and 64bit now.

---

### Post by izizzle on 2009-07-14
Arora 0.7 is not available in the repos and I can't seem to find the 64-bit build, if there is one. I tried Opera 10 QT4 and it is fast and stable. But, I had flash troubles with it as well. Firefox seems to be the only browser that plays flash for ALL the websites I want, not just a few like with Konqueror and Opera. See THIS: [http://ubuntuforums.org/showthread.php?t=1212137](http://ubuntuforums.org/showthread.php?t=1212137)

---

### Post by SunnyRabbiera on 2009-07-14
Firefox with gtk-qt and qtcurve

---

### Post by Skripka on 2009-07-14
> **izizzle said:**
> Arora 0.7 is not available in the repos and I can't seem to find the 64-bit build, if there is one. I tried Opera 10 QT4 and it is fast and stable. But, I had flash troubles with it as well. Firefox seems to be the only browser that plays flash for ALL the websites I want, not just a few like with Konqueror and Opera. See THIS: [http://ubuntuforums.org/showthread.php?t=1212137](http://ubuntuforums.org/showthread.php?t=1212137)

Comedy Central related websites seem to have done something really wierd to their Flash players.  I know that Daily Show vids will not run in just about any browser on Linux here.  I haven't tried Firefox-but don't want to, as it will bloat my system with depends-and usually resort to booting my Win7 to watch John Stewart.

I reported the Daily Show problems to the testers at Opera about a week ago-you might want to do the same for SouthPark.

---

### Post by izizzle on 2009-07-15
> **SunnyRabbiera said:**
> Firefox with gtk-qt and qtcurve

How do I use Firefox with qt? I downloaded "gtk-qt-engine" and "gtk-qt-engine-kde4" from the repos but nothing in firefox looks different.

---

### Post by izizzle on 2009-07-15
I ran found the 0.7 amd64 build of Arora and I got the same exact error I did with 0.5: ```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
server bind: Address already in use
*** NSPlugin Viewer  *** ERROR: failed to initialize plugin-side RPC server connection
Killed
imran@eVga:~$ arora
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
*** NSPlugin Wrapper *** ERROR: failed to initialize brower-side RPC events listener
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
server bind: Address already in use
*** NSPlugin Viewer  *** ERROR: failed to initialize plugin-side RPC server connection
Killed
```

Any ideas?

---

### Post by lykwydchykyn on 2009-07-15
I use firefox, but I keep my bookmarks sync'd to konqueror so that I can pull up things using krunner.  I wish krunner could read my firefox bookmarks, but oh well.

Tried rekonq and it looks nice, and runs FAST.  I just miss a few of my extensions.

---

### Post by infoseeker on 2009-07-15
Firefox 3.5  FTW
Google Chrome is jumping forward in leaps and bounds.  Firefox had better watch it.

---

