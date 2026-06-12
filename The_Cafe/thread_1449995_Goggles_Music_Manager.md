---
title: "Goggles Music Manager"
date: 2010-04-08
forum: The Cafe
---

### Post by Ric_NYC on 2010-04-08
> **Features**

[LIST]
[*]Fast and light weight. Quick startup, no splash screen needed!
[*]Supports Ogg Vorbis , FLAC, MP3 , MP4 , ASF and Musepack music files.
[*]Support for AlbumArt embedded in tag or as separate file on disk.
[*]Tag editing and file renaming capability (batch). One or more tracks may be edited at the same time.
[*]Smart sorting with user configurable leading word filter to prevent sorting on common words like the, a or an.
[*]Support for play lists. Play lists may be played in a certain configurable order, or browsed through like the main music library.
[*]Export music library and play lists to XSPF,PLS,Extended M3U,M3U and CSV.
[*]Clipboard & DND (drag-and-drop) support to arrange playlists and dragging to and from gnome / kde applications.
[*]Uses xine multimedia library for gapless playback and buildin equalizer.
[*]Written using FOX, one of the fastest GUI toolkits available. Support for FOX-1.6.x and the latest development version FOX-1.7.x.
[*]Customizable icons. Either use buildin icons or use an existing gnome/kde icon theme.
[*]Configurable user interface from minimalistic to detailed view. Full screen mode available with FOX-1.7.11.
[*]Clean and fast database backend using SQLite 3.
[*]last.fm audio scrobbler support. (libre.fm supported as well)
[*]Replay Gain support (Ogg Vorbis, FLAC and mp3 with APE tags).
[/LIST]

[http://code.google.com/p/gogglesmm/](http://code.google.com/p/gogglesmm/)

[IMG]http://img580.imageshack.us/img580/6410/mainwindow0914.png[/IMG]



Gallery

[http://picasaweb.google.com/s.jansen/GogglesMusicManager08#](http://picasaweb.google.com/s.jansen/GogglesMusicManager08#)


**Comments**:

> Basically, it's a simple music player that does it's job and works really fast. Other than it's speed, I was also impressed with how little system resources it uses: 8.7 MB of RAM (on my system) and never more than 2% CPU (my music collections is something near 40.000 songs).


**(???)Please note that to install it in Ubuntu, you can't have Nvidia 190 drivers (because libxine1 depends on nvidia185 drivers)(????)**.


> **Great but... not working with x86_64 Karmic. The "wrong architecture" error thing... :( (????)** 


But...


> You can "force architecture" in 64 bit Karmic before installing...

Read this post here:
[http://www.khattam.info/2009/08/20/howto-instal](http://www.khattam.info/2009/08/20/howto-instal)...

Basically it's:

sudo dpkg -i --force-architecture 

... and after that install your package...

[http://www.webupd8.org/2009/11/goggles-music-manager-for-linux.html](http://www.webupd8.org/2009/11/goggles-music-manager-for-linux.html)












Simple and fast.

---

### Post by onaridge on 2011-04-03
I really want to use this so that i can scrobble LastFM which Audacious is refusing to do. I got this error when I tried to install the deb pkg : dependency not satisfiable libjpeg62(>=6b1). I have lucid Lynx, what do I do?

---

### Post by 3rdalbum on 2011-04-03
Just what Linux really needs: another music player! It's good to have a thousand choices.

---

### Post by cokicd on 2011-04-05
Use this ppa to install it. It's always updated to the latest version.

Maverick: **sudo add-apt-repository ppa:ferramroberto/maverickextra**

Lucid:[B] sudo add-apt-repository ppa:ferramroberto/extra 
[/B]
**sudo apt-get update**
**sudo apt-get install gogglesmm               **

---

