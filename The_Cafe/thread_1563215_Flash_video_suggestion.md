---
title: "Flash video suggestion"
date: 2010-08-28
forum: The Cafe
---

### Post by wildman4god on 2010-08-28
I have downloaded flash video from sites like youtube and I have noticed significantly lower cpu usage to decode the video as opposed to the same video in the browser using adobe flash plugin. So I was wondering, would it be possible to build a plug-in for firefox/chrome that would play flash video using totem/vlc or the OS codec system instead of adobe flash plug-in. I am also sorry if this is the wrong place to post this not sure where it would go.

---

### Post by MasterNetra on 2010-08-28
> **wildman4god said:**
> I have downloaded flash video from sites like youtube and I have noticed significantly lower cpu usage to decode the video as opposed to the same video in the browser using adobe flash plugin. So I was wondering, would it be possible to build a plug-in for firefox/chrome that would play flash video using totem/vlc or the OS codec system instead of adobe flash plug-in. I am also sorry if this is the wrong place to post this not sure where it would go.

I don't think that would be practical remember there is also interactive flash content, such a thing would attempt to play the interactive as well. I don't see how it would tell them apart, keep in mind the movie, and its controls are all in one .swf, you would have to extract the movie from its flash file which means A: More CPU usage and B: longer wait time.

---

### Post by wildman4god on 2010-08-28
You make an good point, oh well just a suggestion.

---

### Post by ssam on 2010-08-28
look up HTML5, the <video> tag, and WebM.

---

### Post by stmiller on 2010-08-28
Yeah flash embedded on the web is a bit tricky.

It actually makes a call to the flash plugin specifically.

For it to work with the mozilla VLC plugin, web coders who code the page would have to specifically code to summon the mozilla-vlc-plugin.

[http://www.videolan.org/doc/vlc-user-guide/en/ch07.html](http://www.videolan.org/doc/vlc-user-guide/en/ch07.html)

---

### Post by lovinglinux on 2010-08-28
I develop such Firefox extension, that is compatible with YouTube (except channels), Vimeo and Blip.tv.

[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

More sites will be added in future versions.

Is perfect for users that can't watch HD videos on Youtube because of high CPU usage.

---

### Post by wildman4god on 2010-08-29
> **lovinglinux said:**
> I develop such Firefox extension, that is compatible with YouTube (except channels), Vimeo and Blip.tv.

[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

More sites will be added in future versions.

Is perfect for users that can't watch HD videos on Youtube because of high CPU usage.

sweet once installed will it work with chrome, for example if I install the plug-in for quake live in firefox once installed I can use google chrome to play it, even though they don't support the chrome browser, because chrome and firefox use the same plug-in system.

---

### Post by lovinglinux on 2010-08-29
> **wildman4god said:**
> sweet once installed will it work with chrome, for example if I install the plug-in for quake live in firefox once installed I can use google chrome to play it, even though they don't support the chrome browser, because chrome and firefox use the same plug-in system.

FlashVideoReplacer is not a plugin, is an extension that works only in Firefox. A lot of people use the term plugin to refer to extensions, but [there is a distinction between the two]("http://en.wikipedia.org/wiki/Plug-in_%28computing%29#Plug-ins_and_extensions"). Indeed you can use some plugins on both browsers, because they both use the [Netscape Plugin Application Programming Interface (NPAPI)]("http://en.wikipedia.org/wiki/NPAPI"), which is a cross-platform plugin architecture used by many web browsers. But this is not true for extensions, since Firefox and Chrome extension APIs are completely different.

FlashVideoReplacer acts like a intermediary between the web page and other plugins installed on your system. Basically, it detects the flash video content on a supported site page and replaces the flash object with a different video object (x-mplayer2 or quicktime). It also replaces the flv video URL with the available mp4 video URL, so any x-mplayer2 or quicktime compatible plugin is able to reproduce the video content. The extension itself does not handle the video streaming, it just replaces the code on the page in order to make the browser load a different plugin to stream the video. So you will need FlashVideoReplacer and a quicktime/x-mplayer2 compatible plugin like gecko-mediaplayer, gxine, kaffeine, mozplugger, totem or xine.

Before anyone asks, there is no current plan to port this extension to Chrome, but the code is released as GPL, so anyone is free to do it. I would ask to use a different extension name tho.

---

### Post by freeball1 on 2010-08-29
For Youtube you can use [-->this script<--]("http://userscripts.org/scripts/show/50771"), works perfectly for me with chromium + gecko-mediaplayer (see screenshot)

EDIT: forgot to say, you need an older version of chromium, because gecko-mediaplayer is currently blacklisted for chromium (see [-->here<--]("http://code.google.com/p/chromium/issues/detail?id=24507")). I use 5.0.342.9.

---

