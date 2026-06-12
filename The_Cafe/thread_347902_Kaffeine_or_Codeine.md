---
title: "Kaffeine or Codeine?"
date: 2007-01-28
forum: The Cafe
---

### Post by RAV TUX on 2007-01-28
simple question: which do you use to watch DVD  Movies,

Kaffeine or Codeine?

---

### Post by maniacmusician on 2007-01-28
Codeine?

---

### Post by RAV TUX on 2007-01-28
> **maniacmusician said:**
> Codeine?
[http://www.methylblue.com/codeine/](http://www.methylblue.com/codeine/)
> A simple video-player for KDE with a focus on ergonomics and usability.
 If you like polish and attention to detail, this Video-player is for you. It lacks features, but makes up for it in spades.
 [IMG]http://www.methylblue.com/codeine/20060511.png[/IMG] The backend is xine, so it plays almost all video formats that exist, and DVDs too.
 The current version is 1.0.1.

   **Downloads**

 [Codeine 1.0.1 Source Distribution]("http://kde-apps.org/content/download.php?content=17161")
  **FAQ**

 How can I keep up to date with releases?Subscribe to the Codeine development feed, by copying the URL for this page to your RSS reader.How do I install it?You have to compile from source, so: [quote]_~_$ tar xjf codeine-1.0.1.tar.bz2
_~_$ cd codeine-1.0.1 
_codeine-1.0.1_$ ./configure && make && su -c "make install"[/quote][http://kde-apps.org/content/show.php?content=17161](http://kde-apps.org/content/show.php?content=17161)
> 
**Description:**
Codeine is a video player with a different development philosophy.

When I started to develop Codeine I asked a friend to try to use it to "play a video file". The first thing she did was click the "Play" button. But nothing happened because the play button was disabled; I said "You have to load the video first, then you can play it". She replied, "oh, but I wanted to play something, so I clicked the big play button."

Since then if nothing is loaded the Play button opens a generic "What do you want to play?" dialog. This is how I develop Codeine, it should work exactly like you expect, if it doesn't I need to fix it, so tell me what confuses you!

Features: 
() Plays DVDs, VCDs, all video formats *
() Bundled with a simple web-page KPart 
() Starts quickly
() Simple, uncluttered interface
() "Session based" ** 
() Intelligent behaviour ***  

* Yes, even WMV! But this depends on your distro coming with a properly configured xine-lib. Eg. SuSE unfortunately won't even play DVDs or MP3s out of the box anymore. You may want to compile your own xine-lib. At a future time I'll make a script to make this easy.

** Codeine remembers settings specific to each video, not specific to the application. Eg. the playback position, the preferred window size, the video settings (eg contrast, brightness), the subtitle, audio channel and aspect ratio choices, etc, etc. 

*** For example, the screensaver is deactivated when playing videos, but not when paused or when you change desktop. Seeking when paused remains paused.

I promise that Codeine will remain a simple video player. My development priorities are: usability, interface-responsiveness, interface-feedback, error handling and aesthetics. Not features. This is why the ChangeLog looks a little empty; I don't tend to document "polish". 

Requires: 
{} xine-lib 1.0.0 
{} KDElibs 3.3 
{} X11R6, a computer, some video files to play.

Other Features: 
{} You can record http streams with the hidden record action 
{} You can use drag and drop to play files. Try dragging shoutcast stream playlists, they will play too.

The wallpaper featured in the screenshots is available from [http://www.methylblue.com/images/Marine.jpg](http://www.methylblue.com/images/Marine.jpg)


**Changelog:**
Thanks to all the patches I received since 1.0. Hopefully I'll release 1.0.2 within a month.

1.0.1
   Mute button for KPart
   Play DVD entry for KDE 3.5 + media:/ when DVD inserted
DVD-Menu-Toggle is no longer a KToggleAction because I can't detect when DVD menus change, but it still acts as a toggle button
   Made record work for systems other than mine! (hard-coded path)
   Made record shortcut CTRL-R so it doesn't conflict with the DVD-Root-Menu toggle
   videoWindow doesn't judder when toolbar appears in fullscreen anymore
   dvd-toolbar is gone, instead root menu button appears when dvd is playing
   toolbar in fullscreen mode shows on mouse move
   toolbar in fullscreen mode respects user-positioning
   media kioslave support
   double-clicking the video toggles fullscreen
   don't show part in K-Menu
   a volume toolbar button, - available from the configure-toolbar dialog, it's not very good yet


**Licence: **[GPL]("http://www.fsf.org/licenses/gpl.html")

---

### Post by FyreBrand on 2007-01-28
I use Kaffeine.  It's been working pretty good.  What would Codeine do that Kaffeiene doesn't or why would it be good to install it?

---

### Post by RAV TUX on 2007-01-28
Codeine screenshots

---

### Post by maniacmusician on 2007-01-28
Sweet! I will try this out tonight (got a show to watch) and post back then. It looks pretty damn cool.

---

### Post by RAV TUX on 2007-01-28
Kaffeine screenshot

---

### Post by RAV TUX on 2007-01-28
> **FyreBrand said:**
> I use Kaffeine.  It's been working pretty good.  What would Codeine do that Kaffeiene doesn't or why would it be good to install it?I use both Kaffeine and Codeine.....but I have to admit that the Codeine interface is much more user friendly.

I would difinitely say it would be good to install it...I find myself using it more and more then Kaffeine....there are many times that Kaffeine just isn't good enough and you will find Codeine much more useful.

---

### Post by FyreBrand on 2007-01-28
Version 1.0.1-3 is in the universe I'll try it out.

Is that a beryl theme you're using?

---

### Post by RAV TUX on 2007-01-28
> **FyreBrand said:**
> Version 1.0.1-3 is in the universe I'll try it out.

Is that a beryl theme you're using?
actually I just realized I had my Beryl off....

---

### Post by RAV TUX on 2007-01-28
Here is a screenshot of Codeine with Beryl theme "Frames" on...which I usually use.

---

### Post by RAV TUX on 2007-01-28
> **maniacmusician said:**
> Sweet! I will try this out tonight (got a show to watch) and post back then. It looks pretty damn cool.

> **FyreBrand said:**
> Version 1.0.1-3 is in the universe I'll try it out.

Is that a beryl theme you're using?

please post how it goes, I would be interested to hear what you think?

---

### Post by maniacmusician on 2007-01-28
still up at this late hour, RAV? I'm pretty sure we're in the same time zone :)

I did try it. It was pretty cool, except it doesn't support playlists...and I use those extensively. So I guess I'm sticking with Kaffeine

---

### Post by RAV TUX on 2007-01-28
> **maniacmusician said:**
> still up at this late hour, RAV? I'm pretty sure we're in the same time zone :)

I did try it. It was pretty cool, except it doesn't support playlists...and I use those extensively. So I guess I'm sticking with Kaffeine3:58 am here...

it is not as feature rich as Kaffeine,....but some movies like Scanner Darkly has the playlist selection built in...so I guess I didn't miss this?

---

### Post by kuja on 2007-01-28
Depends on my mood. I almost always use Kaffeine. Other times though, I might use Mplayer(any frontend), Okle, or perhaps VLC.

On the other hand ... Thanks to mass amounts of hard drive space, I've been ripping to Matroska(xvid4/aac/chapters/subs) and using that lately too, and playing with VLC (seems to have the best matroska support).

---

### Post by mips on 2007-01-28
I have a mounted dvd iso image file on my HD.

With Kaffeine I just point it to the /mnt/iso/ and it happily plays it it with everything working.

I cannot do this with Codeine, it wants more than a folder, it wants you to specify a file and if i do my menus don't work and it only plays the one file.
How do I get this to work in Codeine ???

I use both players but find Kaffeine to have more features and features are never a bad thing in my book.

---

### Post by maniacmusician on 2007-01-28
> **RAV TUX said:**
> 3:58 am here...

it is not as feature rich as Kaffeine,....but some movies like Scanner Darkly has the playlist selection built in...so I guess I didn't miss this?
I usually watch downloaded stuff, not DVDs, so I need the playlist.

edit: the downside to not having a playlist, in my case, is essentially that I can't select more than 1 file to play at once. It can get bothersome to select a new video after each one I watch.

Also, where the hell is the volume bar on this thing? I have my speakers turned on loud while I adjust the volume of applications individually depending on the setting and my mood. When I turned this thing on, it WAS SO LOUD.

---

### Post by shining on 2007-01-28
I use mplayer movie -sub subfile

---

### Post by Bloodfen Razormaw on 2007-01-28
Kaffeine is by miles the best video player that exists, on any platform.    The best feature is that Kaffeine has done away with the archaic Open File dialog system and integrates the browsing into the program.  Far more user friendly and productive than the way just about every other program on Earth works, by forcing you to constantly handle new dialogs that popup.  Not to mention that it has features far beyond just playing DVDs, such as DVB support.  Codeine is just too basic.  It's like a version of Totem that isn't horribly slow.

---

### Post by %hMa@?b&lt;C on 2007-01-28
kaffeine, never even heard of codeine until this thread

---

### Post by RAV TUX on 2007-01-28
what version Kaffeine &/or Codeine do you use?

I use Kaffeine 0.8.3

and I just emerged(installed): net-www/kaffeine-mozilla-plugin

I use Codeine 1.0.1.3

---

### Post by seijuro on 2007-01-28
Kaffeine, was installed by default does everything I need it to no need for me to try anything else.

---

### Post by FyreBrand on 2007-01-28
I tested out codeine and it's a pretty nice little player.  I can't think of a reason why I would choose it over kaffeine at the moment but I did find it stable and easy to use.  I might try having this the default media player on the work systems since they mostly just play single files.  It's something to experiment with at least.

I'm still pretty entrenched in kaffeine and I love the mozilla plugin even better than vlc's.

---

