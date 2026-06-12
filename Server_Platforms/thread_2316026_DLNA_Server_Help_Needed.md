---
title: "DLNA Server Help Needed"
date: 2016-03-04
forum: Server Platforms
---

### Post by DGINSD on 2016-03-04
I just installed Lubuntu desktop 14.04.4 LTS on an old Dell Latitude X300 laptop to use as a DLNA server for my video collection. I'll be using my LG BP730 blu-ray players Smart Share function (LG's DLNA implementation) to play what the server is putting out. So far I've installed and tried Mediatomb and Plex both worked for my needs but both have issues that need to be solved. 

Mediatomb stays up and running but pause FF and rewind don't work, and no matter the video my player can't use chapter markers, Subtitles are always shown on playback and have to be manually turned off through the player rather than defaulting to off. 

Plex, pause FF and rewind work just fine chapter markers are not recognized and therefore don't work. Subtitles are the same as mediatomb the first stream is played rather than defaulting to off. The biggest problem is if I stop playback the player loses connection and says there is a network error, if i go back out to the home menus, the server is still there and I can access it and select another video, no problem (Mediatomb stays connected without a problem). Another issue with Plex is I have some videos that are 2 part, Plex will only show me one of these which only allows me to watch half the video, I can't figure out how to tell the server its a 2 part video, rather than 2 versions of the same video.

I've tried quite a few different formats for my videos, all made with handbrake. I settled on a MKV container with MP4 video at typically ntsc film 23.?? fps, audio is AC3 passthrough 5.1, Subtitles are VOBSUB all English tracks. I settled on this format because it seemed to work the best playing on my blu-ray player from a USB stick.

This is my first time doing anything with server software aside from SSH, so any help anyone can give me would be greatly appreciated.

---

### Post by TheFu on 2016-03-06
I played with mediatomb 5+ yrs ago. I wasn't able to get it working in a way that I needed. 1-2 yrs ago, I switched to using PlexMS with different DLNA clients.  Seems that most of the issues you are having are due to a poor DLNA client implementation.  I can assure you that Plex has settings to control everything you've listed able, provided the client supports those settings too.  The main client we use is a raspberry Pi v2 running OSMC (a version of kodi) and all the normal controls are working.  Can pick from multiple audio tracks, multiple subtitles, etc.  mp4 is just a container, like mkv.  I suspect you really use h.264 for the video encoding - AC3 is a pure copy of the input audio to the output audio - which has to be decoded by the player. Not all players handle AC3, but it soundn't like yours does.

For multi-part videos, file names have to be for plex to merge them together.  -cd1.mkv -cd2.mkv will work. So will -p1.mkv, -p2.mkv - this only works for movies, not TV shows.  Plex wants 3 different video sections.
* movies
* tv shows
* videos - which aren't either TV/Movies.

I've never used the plex clients.  My clients are running Kodi with the PlexBMC addon.  There's also the direct web interface into Plex - this is where server settings are made.  The only issue I have with plex and DLNA is that it doesn't support EDL files to automatically skip commercials.  XBMC/Kodi has that support (for a very long time), but Plex doesn't provide those files to the clients.

There are lots of how-to guides for setting up media under Plex. In general, the XBMC guides apply - so ... [http://blog.jdpfu.com/2011/02/21/xbmc-tips](http://blog.jdpfu.com/2011/02/21/xbmc-tips) has a layout that is still working under Plex.

Plex also supports Roku and Chromecast and assorted android clients like bubbleUpNp.  Since every client has a little different capabilities, I've had to put a beefier Plex server in to perform transcoding for the chromecast. It is really picky about media - only wants h.264/aac files. Nothing else.  No AC3 audio.

---

### Post by SeijiSensei on 2016-03-06
I use minidlna.  As TheFu says, it depends a lot on the player you are using.  My LG TV won't play a number of the MKV files in my collection and replies with an "unsupported file type" error.  The same shows play just fine with BubbleUPnP+MXPlayer on my Android phone or VLC on a remote client.  So I'm wondering if your LG player may be the guilty party here.  If you have an Android phone, download those two apps and see if they work correctly, or install VLC on a computer and try using that.  If they work properly, but the LG device does not, I think that's your answer.

---

### Post by DGINSD on 2016-03-08
I forgot to mention I'm running the media server on an old laptop, mostly this is an experiment to gain some experience with a mediated and see what works for an eventual permanent desktop install with adequate specs to run as a htpc and media server. The laptop is a Dell X300 with a Pentium M processor single core at 1.4mhz, integrated Intel graphics i915, 1.1G RAM, and a 160G hard drive, and a 2TB USB hard drive. Playing videos from this is of very poor quality,  jerky video, so on the fly transcoding just adding happening. I actually tried using Kodi first, a dedicated 32bit beta build first, and then as a desktop environment on top of Lubuntu 14.04.4, and finally as an application on the same OS, all failed I'm assuming for graphics reasons or other system specs related issues. (Getting the base OS installed was difficult enough).

I've pretty much settled on Plex Media server its a lot heavier than MediaTomb but seems to have fewer issues. So my main concern is the disconnecting after playback which want an issue with mediatomb so I'm guessing I need a custom profile written for my player. In the owners manual for my LG BP730 it says almost all formats are supported through dlna I'll attach a PDF of the owners manual. It wants you to install Nero Mediahome 4 which only supports Windows and Mac. I've read that through writing a custom device profile you can get the server to present itself as a better supported device or software suite. Knowing this and knowing how to this are two very different things. Any good links on how to write and use a custom Plex profile?


I actually tried using h264 encoding but had problems getting subtitles to work so mp4 seemed the most trouble free.

---

### Post by slickymaster on 2016-03-08
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by TheFu on 2016-03-08
> **DGINSD said:**
>  Any good links on how to write and use a custom Plex profile?


I actually tried using h264 encoding but had problems getting subtitles to work so mp4 seemed the most trouble free.

Not all i915 GPUs are the same.

I had a few Pentium M system here back in 2006.  They are not upto the task of transcoding anything - nothing - nada.  They can be used for pure 100base-tx file servers, however.  There is good news.  If you need transcoding, and it seems you do, a $60 Intel Pentium G3258 will do it easily. A year ago, you could get a MB+CPU combo at MicroCenter for $99, drop in a 2G DDR3 stick and be happy.  I have have one (replaced an AMD E-350 APU).  The G3258 is an amazing desktop CPU - transcodes 2 Hidef streams concurrently.  That removes the need to have pretty much any client-side issues with codecs.  If you transcode to h.264/AAC, then **any** modern player will play it.  I seriously doubt you'll need to create a new profile for the device. You'll copy one that is close, look at the debug messages and tweak the recognition settings ... that's if you have multiple playback devices. If you only have 1, then you can replace the "generic" to transcode everything as needed.

The g3258 is a "best bang for the buck" CPU, IMHO, but you might want to optimize more on price or power use or silence or something else.  The stock fan with the G3258 isn't silent, but it isn't THAT loud either. I would never put it in the same room as my home theatre, however.  A 100% silent Raspberry Pi v2 makes a fine player, if it comes to that.

**ANY** APU today will have enough GPU to playback either h.264 or mpeg2 video at 1080p today. It is only the older media which might not be supported by GPU playback or one of the newest Google video codecs (VP8/VP9) that NOBODY supports in hardware yet which will cause issues.  For any std-def videos, even a 5 yr old Atom should have enough CPU to handle 600p or less resolutions in software.

My G3258 is a NAS, Plex Server, lite-Kodi box and Calibre server - it runs a few other things too and never slows down.  Use NFS for the NAS-side - never CIFS - too many reasons to list. Many people use CIFS for media and are completely happy - I need to say that too.  Kodi supports NFS natively - inside the GUI, so just the server-side export need be setup. I barely use it to watch videos directly - it is mainly a network server for Kodi (w/ PlexBMC addon), BubbleUpNP, chromecast, and roku clients.

My XBMC/Kodi directory layout was accepted by PlexMS as the TV, Movie, Video, Music, Photos layout too. Before I had multiple clients, XBMC was fine. Once I got a chromecast - transcoding became mandatory, so Plex was really the easiest of the solutions available.  I'm not happy that plex is closed-source or that they have only paid clients (which I've never used).  They walk a different line around software than I would, but that is their decision and I respect it.  To be very clear - you do not need a Plex online account or plex client to use this software. It works really, really, really well without that privacy sucking stuff, but there are some things that do not work.

Hopefully that covers enough of the questions.

---

### Post by SeijiSensei on 2016-03-08
I've ascertained that my LG TV can play some Matroska files but not all.  I think it might happen when the audio track is encoded as FLAC.  It has no problems with AAC-encoded material.  It also doesn't always handle ASS subtitles correctly which seems especially weird.  Sometimes they are not interpreted and the TV displays the commands as well as the unformatted subtitle texts.  

I have this same TV connected directly to the computer where the video library is stored, so I don't need to use DLNA at all.  But I was curious to see which files it cannot play that mpv or mplayer have no problem with.

I'm also wondering whether it can handle H.264 with 10-bit color.  I have a couple of those files around, too.

If you're having performance problems transcoding on-the-fly you might consider encoding with XviD+MP3 in the AVI container.  XviD is less computationally demanding than H.264, but with some decline in quality.  If that's available to you, with your transcoder, I'd give it a try and see whether you are satisfied with the results.  Pretty much any device from the past decade should be able to play those, since XviD is the open implementation of the DivX specification.  I downloaded this [test file](http://download.wavetlan.com/SVV/Media/HTTP/AVI/SUPER/SUPER_test5_XviD_16bit_320x240_AR1to1_15fps_KF1to1_64kbps_MPEG2_5_Mono_11025Hz_32kbps.AVI), and the TV played it.  It has MP3 audio.

---

### Post by TheFu on 2016-03-08
Doubtful that any commercial player can handle FLAC or any of the 20 other audio formats that aren't 
a) AAC
b) MP3
c) MP2-audio

A view might support ogg, but they won't support anything newer.  It is just the nature of commercial software - they want to support content produced by commercial companies - so those are the choices today.  In the future, I bet h.265 and VP8 will be supported in hardware by drivers - but only if someone huge with lots of market strength standardizes.

I've written off everything with DRM - never plan to own any bluray stuff. NEVER.

---

### Post by DGINSD on 2016-03-11
> **SeijiSensei said:**
> I've ascertained that my LG TV can play some Matroska files but not all.  I think it might happen when the audio track is encoded as FLAC.  It has no problems with AAC-encoded material.  It also doesn't always handle ASS subtitles correctly which seems especially weird.  Sometimes they are not interpreted and the TV displays the commands as well as the unformatted subtitle texts.  

I have this same TV connected directly to the computer where the video library is stored, so I don't need to use DLNA at all.  But I was curious to see which files it cannot play that mpv or mplayer have no problem with.

I'm also wondering whether it can handle H.264 with 10-bit color.  I have a couple of those files around, too.

If you're having performance problems transcoding on-the-fly you might consider encoding with XviD+MP3 in the AVI container.  XviD is less computationally demanding than H.264, but with some decline in quality.  If that's available to you, with your transcoder, I'd give it a try and see whether you are satisfied with the results.  Pretty much any device from the past decade should be able to play those, since XviD is the open implementation of the DivX specification.  I downloaded this [test file]("http://download.wavetlan.com/SVV/Media/HTTP/AVI/SUPER/SUPER_test5_XviD_16bit_320x240_AR1to1_15fps_KF1to1_64kbps_MPEG2_5_Mono_11025Hz_32kbps.AVI"), and the TV played it.  It has MP3 audio.
 That's what i find so odd about my player is it seems to play all my mkv files formatted as said in my original post, Dolby digital and all. The only problem is the player losing connection with the server, if you stop playback. It can even move on to the next video when it finishes with the first selected without losing connection, but if you stop playback i get a network error and have to navigate to the home menu then back to the server to play another selection.

---

### Post by DGINSD on 2016-03-14
Since both Plex and media tomb both have their issues with the player in using, I thought as a last ditch effort I'd give minidlna a try, I was discouraged before by its supposed lack of features, turns out that's the answer.  Minidlna works flawlessly, stays connected as good or better than mediatomb, and playback features work as good as Plex.

I'd still like to fix Plex's dropping connection issue, because of the more advanced database features, but till I can get that worked out minidlna is a great stop gap. Thank you to SeijiSensei for the tip.

---

