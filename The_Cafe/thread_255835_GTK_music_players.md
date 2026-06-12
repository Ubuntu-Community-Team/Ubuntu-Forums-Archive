---
title: "GTK music players"
date: 2006-09-12
forum: The Cafe
---

### Post by majesticturkey on 2006-09-12
This has probably been discussed many times before. Sorry.

What I want to know is, what is everyone's music player of choice for GNOME, and why. It's not a poll because I really want the why.

I'm looking for an AmaroK-like player. Amarok is too slow in GNOME though, and it's not worth moving to KDE just for it (I really don't like KDE, GNOME fits me better). I use Listen right now, but it seems to have some inadequacies and glitches. I know Exaile is out there, too. I'm looking for a player with AS/Last.fm support, lyrics/information fetching, and iPod support. The iPod support is flexible...I don't need it at all, it would just be very nice to have. Also needs to support AAC/m4a - I converted my library back when I used iTunes a very long time ago and just don't want to waste a few days and tons of memory changing it back.

---

### Post by samir85 on 2006-09-12
Did you try the new Listen 0.5 beta ?
I think they made some good progress with it.

---

### Post by majesticturkey on 2006-09-12
You're right, the .5 beta is pretty nice. Problem is, it doesn't seem to read/play AAC. Did they change the engine on me, or something?

---

### Post by samir85 on 2006-09-12
Concerning the AAC playback issue: Since Listen uses Gstreamer, you should be able to play aac files if there is a Gstreamer aac plugin available ...

---

### Post by Ramses de Norre on 2006-09-12
Is there any gtk player that uses the xine engine? I haven't found any yet..
I use amarok now and I think that's the most mature media player atm, but I'd like a gtk one with the same functionality more.

---

### Post by muep on 2006-09-12
Rhythmbox hasn't even been mentioned? I like it a lot. It is GTK, lightweight, library based, well integrated and plays a ton of music formats through GStreamer. It is also the default.

RB was not very good at the time of the Warty Warthog release, but at the moment it is a great music player that I like a lot. Though... if one wanted the album art or lyrics fetching, I think there are some better alternatives for it. For a good all-round music player I haven't found a better one yet.

---

### Post by Bagnaj97 on 2006-09-12
I havent tested it but I've heard good things about Banshee. I use AmaroK and I havent found it slow under gnome.

---

### Post by samir85 on 2006-09-12
Does Rhythmbox in Edgy has built-in ID3Tag-Editing by default?

Actually, I switched from Rhythmbox to Listen because Rhythmbox was lacking this feature :D

---

### Post by Dragonbite on 2006-09-12
I've used [Banshee]("http://banshee-project.org/index.php/Main_Page") and it seemed to work alright for me, though I didn't fool around with AAC/m4a.

---

### Post by TeeAhr1 on 2006-09-12
[gmusicbrowser]("squentin.free.fr/gmusicbrowser/gmusicbrowser.html")
I bang the drum for Quentin all the time on these forums, so instead of going into my usual tirade, here's the feature list from the site:

[QUOTE=Quentin Sculo]main features

    * fast even with 10,000s of songs (developped with over 17000 songs on a duron800)
    * powerful browser which doesn't interfere with the playlist
    * artist/album lock : easily restrict playlist to current artist/album
    * easy access to songs related to the currently playing song
          o songs from the same album
          o album(s) from the same artist(s)
          o songs with same title (other versions, covers, ...)
    * support ogg vorbis, mp3 and flac files (and mpc with gstreamer)
    * fully featured tag editor (support all id3 versions, limited support for APE & lyrics3 tags)
    * simple mass-tagging and mass-renaming
    * support multiple genres for a song
    * support multiple artists for each song by separating them with '&'
    * customizable named 'flags' can be set for each song (ex : bootleg, live, -'s favorites, ...)
    * filter history in the browser window
    * filters with unlimited nesting of conditions
    * customizable weighted random mode (based on rating, last time played, flag, ...)
    * tray icon, with customizable tip window
    * customizable window layouts (layouts documentation)
    * plugin system (experimental), included plugins :
          o nowplaying (to update an external program when the playing song changes)
          o last.fm
          o fetch cover from google image
          o simple lyrics
          o MozEmbed : use the mozilla engine to display wikipedia artist page and search lyrics with google[/QUOTE]

---

### Post by hanzomon4 on 2006-09-12
The issue with listen v.5 beta is a bug. Listen is not the only new great gtk player though, There is Exaile and it's a great player.
 
    With exaile you can play all formats, transfer songs to your ipod, download missing album art with one click, listen to radio, shout cast, and podcast, edit playlist on your ipod(I think), and there's a bunch of other features.

Check it out here [exaile]("http://www.ubuntuforums.org/showthread.php?t=159879&highlight=exaile")

---

### Post by maniacmusician on 2006-09-12
or the official exaile website at [www.exaile.org](www.exaile.org)

---

### Post by pianoboy3333 on 2006-09-12
I say:
wo0t! for quod libet!

[http://www.sacredchao.net/quodlibet/wiki/Download](http://www.sacredchao.net/quodlibet/wiki/Download)

---

### Post by grte on 2006-09-12
If what you're looking for is a gtk amarok, then I second exaile.  Even the interface will be familiar.

---

### Post by teet on 2006-09-12
> **muep said:**
> Rhythmbox hasn't even been mentioned? I like it a lot. It is GTK, lightweight, library based, well integrated and plays a ton of music formats through GStreamer. It is also the default.

RB was not very good at the time of the Warty Warthog release, but at the moment it is a great music player that I like a lot. Though... if one wanted the album art or lyrics fetching, I think there are some better alternatives for it. For a good all-round music player I haven't found a better one yet.

Actually the latest release of RB (version 0.95 I think) has album art support built in (it just downloads the album art automatically based on the ID3 tags) and a lyrics plugin.  There are some deb's somebody built around here that worked just fine for me.

> **samir85 said:**
> Does Rhythmbox in Edgy has built-in ID3Tag-Editing by default?

Actually, I switched from Rhythmbox to Listen because Rhythmbox was lacking this feature :D

The deb's (from somewhere on the forum) I installed Rhythmbox 0.95 had ID3 Tag editing enabled for me (which was a nice surprise).  However, it won't edit the ID3 tags on all my music for some reason. I don't think it has anything to do with permissions because I chmod 777'ed all my music.

-teet

---

### Post by saracen on 2006-09-12
For the best, and I seriously mean THE BEST, id3 tag editing, download easytag.  It's in the repositories.

---

### Post by maniacmusician on 2006-09-12
best in linux maybe. I think it kind of sucks. It crashes a lot for me when I try to download tags for an album.

I really, REALLY miss Tag&Rename from windows. It was sooooooooo easy to tag things.....[sigh].....

---

### Post by TeeAhr1 on 2006-09-15
I'm a big fan of the mass tagging feature in gmusicbrowser.  Highlight all the songs you want to edit, it's in the right-click menu, and there you go.  Very nice interface.  Here's a screenshot...

---

### Post by hanzomon4 on 2006-09-15
Cowbell is nice(the only one I've tried)

---

### Post by maniacmusician on 2006-09-15
> **TeeAhr1 said:**
> I'm a big fan of the mass tagging feature in gmusicbrowser.  Highlight all the songs you want to edit, it's in the right-click menu, and there you go.  Very nice interface.  Here's a screenshot...
that looks slightly similar to Tag&Rename, just not nearly as many features.

What I really need from a tag editor is to be able to download album art and embedd it in the ID3 tag. that makes my life so much easier.

---

### Post by fuscia on 2006-09-15
xmms. the rest is like getting a drink of water out of a fire hose.

---

### Post by maniacmusician on 2006-09-15
> **fuscia said:**
> xmms. the rest is like getting a drink of water out of a fire hose.
maybe for small amounts of tracks, but with a 35GB+ collection of music, it's quite handy to be able to go through your music in an organized way

---

### Post by fuscia on 2006-09-15
> **maniacmusician said:**
> maybe for small amounts of tracks, but with a 35GB+ collection of music, it's quite handy to be able to go through your music in an organized way

to me, that's what a file manager's for. i guess it boils down to the same process with different apps. i just find the combination of thunar and xmms to be slicker than all that other junk.

---

### Post by maniacmusician on 2006-09-15
yeah. i guess it's all down to preference

---

### Post by fuscia on 2006-09-15
> **maniacmusician said:**
> yeah. i guess it's all down to preference

yup, it's like we're all at the same party drinking really different brands of beer.

---

