---
title: "mpv addon for Firefox"
date: 2015-06-04
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2015-06-04
Just want to tell you about this incredibly useful addon for streaming on Firefox which I came upon a few weeks ago. I think many people who have been having flash or other streaming problems on Firefox would find it very useful.. Basically it can replace flash on many sites and also other media  formats (quicktime, html5) by using mpv and youtube-dl. 
[https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)

It is possible to use mpv with vaapi or vdpau for hardware decoding so it is really light on resources if the graphic card supports these features. I find it to be a better option than using geckomediaplayer + Greasemonkey scripts such as Viewtube for flash replacement. It works on a lot more sites (because of youtube-dl), It is more up to date (both mplayer and gecko-mediaplayer are kind of semi-maintained) and mplayer doesn't do vaapi on intel machines(but can use vdpau through vaapi if install libvdpau-va-gl)

Back in 2012 many people thought that the sky was falling that adobe has dropped flash for Linux, now thanks to the community developers we have many options. We can easily use pepper-flash on Firefox via the freshplayer plugin,--it now performs better than system flash on sites where both work such as Youtube,-- and there are options like the mpv addon (and even pipelight). Things are not bad at all for Firefox users. :) There is now even less reason for me to fire up Chrome (which I don't mind, just don't find it as versatile and extendable as Firefox)

Edited: of course you need to install up to date youtube-dl and mpv. There are ppas for both.

---

### Post by BlinkinCat on 2015-06-04
Hi, just  to let you know that the link didn't work for me - :p

---

### Post by monkeybrain20122 on 2015-06-04
Fixed now. :)

---

