---
title: "Playing almost any flash video in any video player"
date: 2012-10-30
forum: The Cafe
---

### Post by pqwoerituytrueiwoq on 2012-10-30
setup script is attached (run the script named install or install it manually)
For it works on youtube after you change the playback quality first
most other players will just work (eg jwplayer)
you can add a launcher to your panel, docky, or whatever you call the right bar in unity


to make (s)mplayer disable the screensaver during playback do this
```
smplaymkdir ~/ .mplayer/
echo 'heartbeat-cmd="xscreensaver-command -deactivate"' | tee -a ~/.mplayer/config
```to use it pause the flash video in your browser then run the script, and enjoy getting full hardware acceleration (must be enabled in you players configuration) for you video
```
Usage:
    flash-video [player] [player options] [flash id] [file]
    Examples: (empty quotes = auto)
        flash-video vlc
        flash-video '' '' 2702
        flash-video totem '' '' 17
        flash-video smplayer '-fullscreen -close-at-end' 7458 25
```for the source code just open the file in a text editor (this applies to all files (the installer, the main file, and the launcher))

If you don't specify a player it will give you a list to choose from, if there are multiple flash processes it will ask which ditto for videos

limitations

[LIST]
[*]some sites like hulu and cbs do not work,  well it can play there ads but that is it
[*]this does not work with google chrome as it uses pepper flash
[*]once in a while a video will not work in a certain player so just try another (may need a missing codec)
[*]if the flash player stops downloading the video midway (trying to save bandwidth waiting on you to up pause it in flash), this does not work very well (looking at you dailymotion)
[LIST]
[*]a workaround is to mute flash in your sound settings and let it play while you watch it in your video player, this can still preform better than full screen flash depending on your gpu/cpu
[/LIST]
 
[/LIST]
on most flash players seeking to a section of the video will make it unfindable be the script

---

### Post by monkeybrain2012 on 2012-10-30
Do you need to have flash installed or does it replace flash? There are some greasemonkey scripts that allow you to play flash videos without flash (e.g ViewTube and Linterna Magica (on some sites it may need flash)) I think ViewTube also has an option to open video in external player. Viewtube and LM also work on Chrome (but kind of iffy because gecko-mediaplayer doesn't work very well in Chrome and Totem doesn't always work and LM seems to have some bugs that would freeze Chrome in Ubuntu)

---

### Post by pqwoerituytrueiwoq on 2012-10-30
adobe flash is needed
this works regardless of the url the video is on
the script finds the video flash (is) download(ing/ed) and opens if in any video player you choose
from what i have seen html5 does not use vdpau on my nvidia card but smplayer does, so i pause the vid in flash and run the script to open it in smplayer

---

### Post by monkeybrain2012 on 2012-10-30
> **pqwoerituytrueiwoq said:**
> adobe flash is needed
this works regardless of the url the video is on
the script finds the video flash (is) download(ing/ed) and opens if in any video player you choose
from what i have seen html5 does not use vdpau on my nvidia card but smplayer does, so i pause the vid in flash and run the script to open it in smplayer

Does it work for live streaming? How about embedded videos say in Facebook or Newspaper sites?

Edited: so it uses flash in an essential way, I am asking because Linterna Magica "needs" flash for some sites (like Youtube) but not necessarily adobe flash, can be any flash plugin (like gnash) which may not even work, it needs the plugin just to detect flash objects.

---

### Post by pqwoerituytrueiwoq on 2012-10-30
i do know facebook videos work same for myspace
it does not matter what websuite is playing the video for example you know how flash video replacer would work on youtube but not on a blog with a yuotube video, it is uneffected by that, this is because it does not really on a browser to get the video it relives on flash directly
for the most part if the stream source uses drm it most likely will not work on it
it will play streams just fine as long as it plays slower than it comes in (playing at 100KB/s does not work very well with a 10KB/s stream)
the player will either crash or exit if it would have to buffer (unless your video player have a option to avoid that you can pass to it via a command)

---

### Post by pqwoerituytrueiwoq on 2012-10-30
it is not a replacement for flash in any way, it finds the video flash is playing on the ram and opens in in a player of your choice

---

