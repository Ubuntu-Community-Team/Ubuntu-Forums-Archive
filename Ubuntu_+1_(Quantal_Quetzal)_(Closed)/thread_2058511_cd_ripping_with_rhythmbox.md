---
title: "cd ripping with rhythmbox"
date: 2012-09-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-09-15
just a few small notes on, - 

gnome has switched to presets so that's what RB will be using. The first time edit > preferences > music is opened there will be an erroneous message box as seen in screen 1. It will not go away until a .prs is created in ~/.gstreamer-0.10/presets/

The way to do that is expand the dropdown & pick the 'Custom setting' choice. That will cause the .prs to be created & the message won't appear next time 

In the case of mp3 you may actually need to install some codecs, clicking on the message will do so. Still you again need to choose the Custom settings to get a .prs created, ect.

The Custom setting changes quality, to review any other options you can open the .prs. ( custom is [rhythmbox-custom-settings]
Presets are limited to the avail. gst options, for the most part the defaults are ok. To see - 

gst-inspect vorbisenc
gst-inspect lamemp3enc

The 'ubuntu-default' is a pre-installed preset that was a 12.04 response to gnome lowering their default (Default in settings) to **very** low quality for ogg & mp3

The downside for mp3 is the preset way doesn't allow the use of xingmux headers so track times will likely vary depending on player, have yet found a way around this...

As far as soundjuicer - 
only useful for flac & low rent portable devices. Sj could be made to use custom presets in 12.04, atm in 12.10 that seems problematic so it will use the current Gnome Defaults for mp3 & ogg

As far as mp4
As custom .prs can be user created, probably have an example somewhere, other than testing I use abcde or rubyripper

---

