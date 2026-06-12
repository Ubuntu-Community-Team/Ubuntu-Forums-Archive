---
title: "Banshee, Totem, GStreamer freezes"
date: 2012-02-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jpeddicord on 2012-02-25
[s]Want to crowdsource a bit before I go filing a bug report on this.[/s]
**Bug filed:** [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/941229](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/941229)

Anyone having some freezing issues with Banshee, Totem, or any other media player? I get seemingly random lockups in Banshee when I seek or skip songs too frequently. No problems if I just leave it running on its own, though.

In Totem, I have a similar issue where seeking can cause a lockup. Not sure if the two are related (gstreamer bug) or coincidental. Additionally, I'm only seeing this behavior on MP3s; testing this with Vorbis works out fine.

Quick way to reproduce: Open an MP3 in Totem. Madly click or scrub on the seek bar for a few seconds. See if you can get it to lock up.

In Banshee, if you have a largely MP3 library, you can just open any song, and start mashing the "next" button to observe a freeze.

Going to try to get backtraces from both of these, but I just want to know if anyone else is experiencing these problems first, or if I'm just going insane. :)


EDIT: Beautiful, a deadlock:```
GStreamer-WARNING **: wrong STREAM_LOCK count 0
^C
Program received signal SIGINT, Interrupt.
0x00007ffff623d89c in __lll_lock_wait ()
   from /lib/x86_64-linux-gnu/libpthread.so.0
(gdb) bt
#0  0x00007ffff623d89c in __lll_lock_wait ()
   from /lib/x86_64-linux-gnu/libpthread.so.0
#1  0x00007ffff6239080 in _L_lock_903 ()
   from /lib/x86_64-linux-gnu/libpthread.so.0
#2  0x00007ffff6238f19 in pthread_mutex_lock ()
   from /lib/x86_64-linux-gnu/libpthread.so.0
#3  0x00007ffff6468391 in g_static_rec_mutex_lock ()
   from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#4  0x00007ffff0427240 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgstbase-0.10.so.0
#5  0x00007ffff0424498 in ?? ()
   from /usr/lib/x86_64-linux-gnu/libgstbase-0.10.so.0
#6  0x00007ffff41b69c2 in gst_pad_send_event ()
   from /usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0
#7  0x00007ffff41b6f52 in gst_pad_push_event ()
   from /usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0
#8  0x00007fffc83f4ec6 in ?? ()
   from /usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstflump3dec.so
#9  0x00007ffff41b69c2 in gst_pad_send_event ()
   from /usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0
#10 0x00007ffff41b6f52 in gst_pad_push_event ()
...

```

Well, that at least confirms it's a problem with GStreamer, and likely the MP3 decoding (libgstflump3dec.so).

---

### Post by VinDSL on 2012-02-25
> **jpeddicord said:**
> [s]Want to crowdsource a bit before I go filing a bug report on this.[/s]
**Bug filed:** [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/941229](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/941229)

Anyone having some freezing issues with Banshee, Totem, or any other media player? I get seemingly random lockups in Banshee when I seek or skip songs too frequently. No problems if I just leave it running on its own, though.
I don't use Totem but, yes, the Banshee gui has been freezing randomly since the first day I used it... way back when.  

I always *assumed* Conky was causing the problem, since Conky usually freezes too, when this happens.

Banshee keeps on trucking -- it's just the interface that freezes.  If I'm listening to podcasts, and/or web radio, it'll play for hours, even though the gui is ghosted out and dead as a bag of hammers.

Conky, on the other hand, requires a force-quit.

I've never delved into the exact cause of these freezes.  It's just a minor irritation, to me.  That said, it would be nice if someone found a fix.

---

### Post by jpeddicord on 2012-02-25
> **VinDSL said:**
> I don't use Totem but, yes, the Banshee gui has been freezing randomly since the first day I used it... way back when.  

I always *assumed* Conky was causing the problem, since Conky usually freezes too, when this happens.

Banshee keeps on trucking -- it's just the interface that freezes.  If I'm listening to podcasts, and/or web radio, it'll play for hours, even though the gui is ghosted out and dead as a bag of hammers.

Conky, on the other hand, requires a force-quit.

I've never delved into the exact cause of these freezes.  It's just a minor irritation, to me.  That said, it would be nice if someone found a fix.

The issue I'm seeing would *probably* mean that playback freezes as well, since it deadlocks on seeking and skipping. I suppose it could be possible to deadlock on its own while playing (and maybe keep playing) but I haven't run into any situations to test that.

The freezes I'm seeing happen probably 1 of 10 times I try to do, well.. anything in Banshee. More so if I'm trying to do something quickly.

---

### Post by VinDSL on 2012-02-26
> **jpeddicord said:**
> The freezes I'm seeing happen probably 1 of 10 times I try to do, well.. anything in Banshee. More so if I'm trying to do something quickly.
I managed to stuff up Banshee (not that hard), so I switched to Rhythmbox and immediately got it to freeze too.  LoL!

At that point, I installed Guayadeque, but everything was so janky on my desktop (active/focused windows were underneath inactive/unfocused windows, et cetera) that I had to logout/login to straighten things out.

I've been trying to get Guayadeque to freeze, by quickly going back n' forth on MP3 files, and... so far, so good.

I run Peppermint Two OS on a bootable USB thumb, and Guayadeque is the default music player.  I can't remember it ever freezing up on me.

I've noticed that while I'm seeking back n' forth on an MP3 file, it doesn't jump to the new spot, e.g. start playing the new location, until I release the mouse button.  Maybe this is precluding the freezing, because there's no skipping, during seeks.

Anyway, I'll roll with Guayadeque for a while, and see if I can break it...  ;)

---

### Post by lemmy15 on 2012-02-26
I use Ubuntu 10.10.  Since I had a system update about three weeks ago, I've had problems listening to audio files (mp3).  (totem?).

What happens is that during a particular broadcast, it suddenly cuts out and goes back to the beginning of file, so I have to restart the show.

Here is one link as an example, but this problem has occurred numerous times:

[http://www.netcastdaily.com/broadcast/fsn2012-0225-3.mp3](http://www.netcastdaily.com/broadcast/fsn2012-0225-3.mp3)

I also, since this system update, have had problems with Totem Plugin, 2.32.0, Browser Plugin using GStreamer 0.10.30.  

[http://kingworldnews.com/kingworldnews/Broadcast/Entries/2012/2/25_KWN_Weekly_Metals_Wrap.html](http://kingworldnews.com/kingworldnews/Broadcast/Entries/2012/2/25_KWN_Weekly_Metals_Wrap.html)

I've used Ubuntu for a few years but don't know enough to troubleshoot or articulate well my problems.  Any help would be greatly appreciated!

---

### Post by jpeddicord on 2012-02-26
> **lemmy15 said:**
> I use Ubuntu 10.10.  Since I had a system update about three weeks ago, I've had problems listening to audio files (mp3).  (totem?).

What happens is that during a particular broadcast, it suddenly cuts out and goes back to the beginning of file, so I have to restart the show.

Here is one link as an example, but this problem has occurred numerous times:

[http://www.netcastdaily.com/broadcast/fsn2012-0225-3.mp3](http://www.netcastdaily.com/broadcast/fsn2012-0225-3.mp3)

I also, since this system update, have had problems with Totem Plugin, 2.32.0, Browser Plugin using GStreamer 0.10.30.  

[http://kingworldnews.com/kingworldnews/Broadcast/Entries/2012/2/25_KWN_Weekly_Metals_Wrap.html](http://kingworldnews.com/kingworldnews/Broadcast/Entries/2012/2/25_KWN_Weekly_Metals_Wrap.html)

I've used Ubuntu for a few years but don't know enough to troubleshoot or articulate well my problems.  Any help would be greatly appreciated!That's likely a different issue; the one we're describing is a complete lockup where the applications must be force close'd. You may want to start a new thread to get the help you need with troubleshooting.

Totem (GStreamer?) hasn't really been all that solid for me with network streams, though. Perhaps try the stream in VLC and see if it works there first, to eliminate any network causes.

> **VinDSL said:**
> I've been trying to get Guayadeque to freeze, by quickly going back n' forth on MP3 files, and... so far, so good.

I run Peppermint Two OS on a bootable USB thumb, and Guayadeque is the default music player.  I can't remember it ever freezing up on me.Interesting.. that is a GStreamer player, so by all accounts it *should* be having problems. :P

> I've noticed that while I'm seeking back n' forth on an MP3 file, it doesn't jump to the new spot, e.g. start playing the new location, until I release the mouse button.  Maybe this is precluding the freezing, because there's no skipping, during seeks.Very possible.

> Anyway, I'll roll with Guayadeque for a while, and see if I can break it...  ;)I'm going to give it a stab as well.

---

### Post by jpeddicord on 2012-02-26
I've done it!

```
jacob@termina: ~ $ guayadeque 

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Created the configuration folder
Created the lyrics folder
Created the collections folder
Created the Radios folder
Created the Jamendo folder
Created the Magnatune folder
Created the Podcasts folder
Created the Layouts folder
Created the default configuration file
Created the default equalizers file
Created the default lyrics sources file
09:23:01 AM: Initialized locale ( en_US )
09:23:01 AM: MediaViewer 'My Music' => '4F49F9F5' ==>> 00000000
09:23:01 AM: Created collection folder '/home/jacob/.guayadeque/Collections/4F49F9F5'
09:23:01 AM: Library Db Version 0
09:23:01 AM: Updating database version to 21
09:23:01 AM: SetViewMode -1 => 0
09:23:01 AM: guLibPanel::IniPanelData( 13101 )
09:23:01 AM: guLibPanel::DoTextSearch( '' )
09:23:02 AM: OnCollectionCommand 13100  0 0  1
09:23:02 AM: Updating the podcasts...
09:23:02 AM: Indicators_Sound_Available() => 0
09:23:02 AM: Indicators_Sound_Available() => 0
09:23:03 AM: playlist active 0
09:23:34 AM: AddToPlayList( ..., 1, 0 )
09:23:34 AM: Loading 0 0 => 0 '/home/jacob/Music/Agnelli & Nelson - Holding On To Nothing (Paul van Dyk Edit).mp3'
09:23:34 AM: OnMediaLoaded Cur: 0 1   3121320025
09:23:34 AM: Track starts at 0 with length 636000
09:23:34 AM: Trying to get url: http://lyrics.wikia.com/Agnelli_%26_Nelson:Holding_On_To_Nothing_(Paul_van_Dyk_Edit)
09:23:34 AM: StatusChanged( 0, 0, 0, 0 )
09:23:35 AM: Delete expired Cache elements done

GStreamer-WARNING **: wrong STREAM_LOCK count 0
```I couldn't get it to lock up just by clicking on the slider, but scrolling the mouse wheel over it caused it to happen.

---

### Post by VinDSL on 2012-02-26
> **jpeddicord said:**
> I've done it!

I couldn't get it to lock up just by clicking on the slider, but scrolling the mouse wheel over it caused it to happen.
Bingo! 

I (re)produced the freeze by furiously wheeling over the slider, too... ;)

**Edit**

Here's the dialog in cli...

```
vindsl@Zuul:~$ guayadeque
01:10:03 PM: Deleted stale lock file '/home/vindsl/.guayadeque/.guayadeque-vindsl'.
01:10:03 PM: Initialized locale ( en_US )
01:10:03 PM: MediaViewer 'My Music' => '4F498126' ==>> 00000000
01:10:03 PM: Library Db Version 21
01:10:04 PM: SetViewMode -1 => 0
01:10:04 PM: guLibPanel::IniPanelData( 13101 )
01:10:04 PM: guLibPanel::DoTextSearch( '' )
01:10:04 PM: OnCollectionCommand 13100  0 0  1
01:10:05 PM: Updating the podcasts...
01:10:05 PM: Indicators_Sound_Available() => 0
01:10:05 PM: Indicators_Sound_Available() => 0
01:10:06 PM: playlist active 0
01:10:33 PM: OnMediaLoaded Cur: 0 1   -1152828602
01:10:33 PM: Track starts at 0 with length 6531000
01:10:33 PM: StatusChanged( 0, 0, 0, 0 )
01:10:33 PM: Trying to get url: http://lyrics.wikia.com/Michael_Savage:The_Michael_Savage_Show_02%2F22%2F2012_FULL
01:10:34 PM: Trying to get url: http://www.azlyrics.com/lyrics/michaelsavage/themichaelsavageshow02222012full.html
01:10:35 PM: Trying to get url: http://www.coveralia.com/letras/the-michael-savage-show-02-22-2012-full-michael-savage.php
01:10:37 PM: Trying to get url: http://www.directlyrics.com/michael-savage-the-michael-savage-show-02-22-2012-full-lyrics.html
01:10:37 PM: Trying to get url: http://www.elyrics.net/read/M/michael-savage-lyrics/the-michael-savage-show-02-22-2012-full-lyrics.html
01:10:38 PM: Trying to get url: http://letras.terra.com.br/winamp.php?musica=the%2Bmichael%2Bsavage%2Bshow%2B02_22_2012%2Bfull&artista=michael%2Bsavage
01:10:39 PM: Trying to get url: http://www.loudson.gs/M/michael-savage/the-michael-savage-show-podcast/the-michael-savage-show-02-22-2012-full
01:10:39 PM: Trying to get url: http://www.lyrics.com/lyrics/michael-savage/the-michael-savage-show-02-22-2012-full.html
GStreamer-WARNING **: wrong STREAM_LOCK count 0
01:10:42 PM: Trying to get url: http://www.lyrics007.com/Michael+Savage+Lyrics/The+Michael+Savage+Show+02%2F22%2F2012+FULL+Lyrics.html
01:10:42 PM: Trying to get url: http://www.lyricsbay.com/the_michael_savage_show_02_22_2012_full_lyrics-michael_savage.html
01:10:43 PM: Trying to get url: http://www.lyricsdownload.com/michael-savage-the-michael-savage-show-02-22-2012-full-lyrics.html
01:10:43 PM: Trying to get url: http://www.lyricsmania.com/the_michael_savage_show_02_22_2012_full_lyrics_michael_savage.html
01:10:47 PM: Trying to get url: http://www.lyricsmode.com/lyrics/M/michael_savage/the_michael_savage_show_02_22_2012_full.html
01:10:49 PM: Trying to get url: http://www.lyricsreg.com/lyrics/michael%2Bsavage/the%2Bmichael%2Bsavage%2Bshow%2B02%2B22%2B2012%2Bfull/
01:10:49 PM: Trying to get url: http://www.lyricstime.com/michael-savage-the-michael-savage-show-02-22-2012-full-lyrics.html
01:10:50 PM: Trying to get url: www.lyricsvip.com/Michael-Savage/The-Michael-Savage-Show-02%2F22%2F2012-FULL-Lyrics.html
Killed
vindsl@Zuul:~$

```

Guess I can turn off the lyrics. :D

**Edit 2**

Okay, here's the annotated output with lyrics disabled...

```
vindsl@Zuul:~$ guayadeque
01:42:19 PM: Initialized locale ( en_US )
01:42:19 PM: MediaViewer 'My Music' => '4F498126' ==>> 00000000
01:42:19 PM: Library Db Version 21
01:42:19 PM: SetViewMode -1 => 0
01:42:19 PM: guLibPanel::IniPanelData( 13101 )
01:42:19 PM: guLibPanel::DoTextSearch( '' )
01:42:19 PM: OnCollectionCommand 13100  0 0  1
01:42:20 PM: Updating the podcasts...
01:42:20 PM: Indicators_Sound_Available() => 0
01:42:20 PM: Loading 0 -1 => 0 '/home/vindsl/.guayadeque/Podcasts/The Michael Savage Show Podcast/Savage_02-22-2012_FULL.mp3'
01:42:21 PM: playlist active 0
01:42:29 PM: OnMediaLoaded Cur: 0 1   -1150912284
01:42:29 PM: Track starts at 0 with length 6531000
01:42:29 PM: StatusChanged( 0, 0, 0, 0 )
[COLOR="DarkRed"]**(This is where I scrolled the slider with the mouse wheel)**[/COLOR]
GStreamer-WARNING **: wrong STREAM_LOCK count 0
[COLOR="DarkRed"]**(force-quit due to freeze)**[/COLOR]
Killed
vindsl@Zuul:~$ 

```

---

### Post by mc4man on 2012-02-26
At least here the poor seeking behavior (forced thru wild seeking) seems be be attached to the gstreamer pulseaudio plugin.
With it removed can't cause a lock up (the plugin is not absolutely required

---

### Post by VinDSL on 2012-02-26
I just went over to the gstreamer dev ppa, and upgraded as much as I could.  Gstreamer is intertwined with a lot of things, and replacing one of the core packages would have required removing about half of the operating system.  LoL!

SOURCE: [https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

The first thing I noticed, on restart, was the login sounds were back again -- haven't heard them in a while.

I've been trying to stuff up Banshee, but so far it's working like a champ!

I'll try Rhythmbox next.  I noticed that the gstream plugin was removed from the Rhythmbox package, during the upgrades.

Then, I see if I can break Guayadeque.

**4 Hours Later**

Still getting freezes, all the way around...

---

### Post by VinDSL on 2012-02-26
> **lemmy15 said:**
> What happens is that during a particular broadcast, it suddenly cuts out and goes back to the beginning of file, so I have to restart the show.[...]
I listen mostly to podcasts.

What happens is that during playback, it suddenly cuts out, and skips forward to the next podcast.

So, I have to go back to the original podcast and search for where it cutout.

This, of course, is like playing with nitroglycerin. If you move the slider too quickly, the player blows up in your face (and takes Conky along with it). :p

---

### Post by jpeddicord on 2012-02-26
> **mc4man said:**
> At least here the poor seeking behavior (forced thru wild seeking) seems be be attached to the gstreamer pulseaudio plugin.
With it removed can't cause a lock up (the plugin is not absolutely required

Wasn't able to confirm. Removed libgstpulse temporarily, and I was still able to get a lockup just as easily as when it was on.

---

### Post by mc4man on 2012-02-27
> **jpeddicord said:**
> Wasn't able to confirm. Removed libgstpulse temporarily, and I was still able to get a lockup just as easily as when it was on.
Yep - it appears I wasn't thrashing it hard enough to cause the lock up here.

---

### Post by jpeddicord on 2012-02-27
> **mc4man said:**
> Yep - it appears I wasn't thrashing it hard enough to cause the lock up here.

At least we can get the same results, you had me worried. :P

I'm going to get a more descriptive backtrace when I get home from work today. The [bug status upstream]("https://bugzilla.gnome.org/show_bug.cgi?id=670846") was updated to blocker/critical, so hopefully we'll find and resolve this issue quickly.

---

