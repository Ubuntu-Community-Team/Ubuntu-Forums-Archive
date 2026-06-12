---
title: "bye bye flash player hello Totem,vlc,mplayer"
date: 2009-05-16
forum: Tutorials
---

### Post by mysoogal on 2009-05-16
**[COLOR="Magenta"][B]Sorry i have updated it all i hope this all works now if not tell me ill try again**[/COLOR][/B]
[IMG]http://i40.tinypic.com/zm1f9x.png[/IMG]

now lets get this installed.

> 1. install Greasemonkey 0.8.20090123.1
[https://addons.mozilla.org/en-US/firefox/addon/748](https://addons.mozilla.org/en-US/firefox/addon/748)

> 2. install YouTotem script
[http://userscripts.org/scripts/show/25481](http://userscripts.org/scripts/show/25481)
Please remember to also install all the gstreamer plugins and audo video codecs such as ugly packs etc

> sudo apt-get install mozilla-plugin-vlc
you will need to install videoLan player 9.9 i have not tested with the new version of 1.0.0 so remember if you have new version it might not work with the javascript files

> 3. restart Firefox


little more tips ! for you
1. when you install vlc you also need the vlc Mozilla plug-in
2. you also need all the Totem gstreamer codec etc installed
3. mplayer just needs to be installed with plug-in like the rest


more Tips, you can use ctrl { not sure it might be alt plus > right key}
 + > key to move forward in video using vlc, while in totem doesn't seem to work. in all players, you can double click the video to go full screen, you can pause video by pressing your space bar. :D

**[COLOR="Magenta"]sorry you will also need to install VLC-mozilia-plugin and totem with all the gstreamer audio video codec packs[/COLOR]**

---

### Post by mysoogal on 2009-09-15
make sure you install 

videolan, with mozillia vlc web plugin or update your totem player.:KS

down with adobe flash !!! burn adobe books

---

### Post by PenguinLuva on 2009-09-17
It seems a bunch of people are getting the following error message when they browse to a video on Youtube with Youtotem installed:

"YouTotem: Unable to find video source".

Do you have any advice? Do you know how to solve this problem?

---

### Post by som24 on 2009-09-18
[COLOR="DarkGreen"]what'll happen in those videos for which mp4 is not available?[/COLOR]

---

### Post by Artemis3 on 2009-09-20
IMO i think it would be much simpler to download the videos with something like Download Helper then watch with your preferred player.

BTW: Stuff like Bleach is easily available via torrent from Dattebayo fansubs, so you might start avoiding youtube when you can :)

---

### Post by darthmob on 2009-09-20
If you have no problem with the flash tools I would recommend the [YousableTubeFix greasemonkey script]("http://userscripts.org/scripts/show/13333").

- automatically selects best quality (mpeg4 or flv)
- prevents autoplay
- download video button (flv and mpeg4 as well)
- select which parts of youtube are shown

---

### Post by mysoogal on 2009-09-28
Sorry guys i feel so damm stupid i left out Videolan which you will need as the greecemonkey script mainly wants to use vlc to stream. and not totem first.

you will need to install Videolan player and its web plugin

follow this page 

[http://www.videolan.org/doc/vlc-user-guide/en/ch07.html](http://www.videolan.org/doc/vlc-user-guide/en/ch07.html)

of you can just type sudo apt-get install mozilla-plugin-vlc

reboot your brower and turn on the monkey script, go youtube should be working fine :P

---

### Post by whaskes on 2009-11-26
hi all!

i installed it the greasemonkey and the script, but doesn't work it on the youtube.
script: [http://userscripts.org/scripts/show/25481](http://userscripts.org/scripts/show/25481)
included page: [http://*youtube.*/*](http://*youtube.*/*)

**error message: YouTotem: Unable to find video source**

firefox version: 3.5.5
ubuntu dist: 9.10
kernel: Linux whaskes-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
totem version: 2.28.2
vlc version: 1.0.2
gstreamer0.10-ffmpeg 

totem and totem-mozilla it is installed, vlc, vlc-mozilla-plugin it is installed.

i tested this page and every ok, played all file. 
[http://vlc.revolunet.com/git/example.html](http://vlc.revolunet.com/git/example.html)

+ youtube: Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player]("http://www.adobe.com/go/getflashplayer/").


                 
 any idea?

---

### Post by TheTank on 2009-11-27
I have the same problem as whaskes.
Though I have jaunty.

---

### Post by Paul D on 2009-12-23
Totem seems to have a problem though...

See; [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/496616/+activity](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/496616/+activity)

I have the same problem on my Karmic 9.10 install. At random points in playing video,
I get the same error message, "pa_stream_writable_size() failed: Connection terminated". I can drag the play position slider back to just before the place the event happened, and it plays fine. There is also a problem I notice when playing audio, if I move the position slider during playback, the visualization going on in the player stops. The music seems to play OK though. I can live better with that problem then the first one though.

I have Totem Movie Player 2.28.2, using GStreamer 0.10.25, as installed with 9.10.

Anyone else notice this?

---

### Post by astkboy2008 on 2009-12-24
is it can work with mp4 and 3gp

---

### Post by Kangarooo on 2011-12-02
Doesnt work for me.
Ubuntu 10.04.3 LTS
By default latest VLC for now is very old and YT network stream it doesnt opens so
Installed latest VLC  using in [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)
```
% sudo add-apt-repository ppa:lucid-bleed/ppa
% sudo apt-get update
% sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc

```
then greasemonkey and [http://userscripts.org/scripts/show/50771](http://userscripts.org/scripts/show/50771)
But doesnt work..
In script settings witch i can access from below YT video screen In Settings button ive choose VLC.
What else? Ive tryd all options. Doesnt work.

---

