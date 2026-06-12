---
title: "Audio-recorder for Precise now available"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by moma on 2012-04-04
Hello,
I have upgraded audio-recorder to version 0.8 and it should work fine in pure GTK3 distros such as Ubuntu 12.04 and Fedora 16+.

[[img]http://bildr.no/thumb/1148651.jpeg[/img]](http://bildr.no/view/1148651)

Get ready-made packages for Precise from:
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

Source code:
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

Test and love it + happy holidays.

BTW: **Please help to update the translations on **
[https://translations.launchpad.net/audio-recorder/trunk](https://translations.launchpad.net/audio-recorder/trunk)

---

### Post by hughr2005 on 2012-04-04
That looks great, thanks moma :)

I'll start testing now :D

---

### Post by ubuntu27 on 2012-04-05
All right. I helped translating a little bit.


Thanks for the app! :popcorn:

---

### Post by mc4man on 2012-04-06
moma - 
looking really good, nice progression (gtk3) from previous
Don't think I quite get 'atomatically controlled by ..' feature but otherwise works well

---

### Post by moma on 2012-04-16
@mc4man: Good observation.
The dbus-interface to Rhythmbox is broken in this version. But I have a dev-version here that uses the latest MediaPlayer2 (MPRIS) standard and it should work with all MPRIS-compatible mediaplayers (Rhythmbox, Banshee, Amarok, and even Spotify, etc.). The recording can be controlled by these players.

Read also:
[https://bugs.launchpad.net/audio-recorder/+bug/973809](https://bugs.launchpad.net/audio-recorder/+bug/973809) 
+
[http://specifications.freedesktop.org/mpris-spec/latest/](http://specifications.freedesktop.org/mpris-spec/latest/)

---

### Post by mc4man on 2012-04-16
> **moma said:**
> @mc4man:  But I have a dev-version here that uses 
For a moment I thought "here" was going to a link, guess it means you have it "there"

If it's gets uploaded at some point will give a try out

---

### Post by Baldrick_NZ on 2012-04-16
Great job, Momo!

Just one thing though, how can I change the quality of the recording? Sometimes I might want an ogg vorbis file at 320kbps, and other times 64kbps will do?

Cheers.

---

### Post by mc4man on 2012-04-17
> **Baldrick_NZ said:**
> Great job, Momo!

Just one thing though, how can I change the quality of the recording? Sometimes I might want an ogg vorbis file at 320kbps, and other times 64kbps will do?

Cheers.
Moma would know better but I'll take a guess - 
There isn't from what I see a config for the recorder but I think A-r is using the gst profiles that are still stored/set in gconf, so for ogg - 
/system/gstreamer/0.10/audio/profiles/cdlossy/pipeline
So you'd open that key & raise or lower the blue
 quality=0.[COLOR="Blue"]5[/COLOR]

As usual one should be careful when editing gst profiles - good to copy out how written & save somewhere

There aren't atm or the foreseeable future any profile settings for gst audio in gnome3 > gsettings so it's gconf or inside an app itself like banshee does
(RB is currently limited to the gst defaults when ripping cd's

---

### Post by Baldrick_NZ on 2012-04-18
> **mc4man said:**
> Moma would know better but I'll take a guess - 
There isn't from what I see a config for the recorder but I think A-r is using the gst profiles that are still stored/set in gconf, so for ogg - 
/system/gstreamer/0.10/audio/profiles/cdlossy/pipeline


Thanks again for your help mac4man.

Any chance you could give me the full link to the gconf file? I can't see this in my file hierarchy, doesn't even come up as a search.

Cheers.

---

### Post by mc4man on 2012-04-18
see screen for in gconf-editor
(we could work out a command line edit, I'll edit into this post in a bit
Haven't used ogg too much, assume lower is lower br, higher is higher br?

If using gconf-editor either max or widen the window so the whole key is visible when editing

attached is text file with 3 ex, for command line if you'd like that route, 3 examples are - 
1st one is default, 2nd sets to a quality of 3, 3rd to a quality of 8
Each command is 1 long line - you must get it all

---

### Post by Baldrick_NZ on 2012-04-18
Great stuff! Worked a treat, Thanks!

---

### Post by moma on 2012-04-21
Hello,
To mc4man and Baldrick_NZ:
As you say, the program gets the Gstreamer-pipelines from the GConf-registry. Take a look at the src/media-profiles.c module.

Install and start gconf-editor and browse to: 
system -> gstreamer -> 0.10 -> audio -> profiles.
----

[B]New updated package for Ubuntu 12.10 (precise).
[/B]I just uploaded version 0.9 for compilation on the Launchpad.net. The recorder now implements the new MPRIS2-standard. It can be controlled by all MPRIS2-compatible players such as; Rhythmbox, Banshee, Amarok.

Please see: [https://bugs.launchpad.net/audio-recorder/+bug/973809](https://bugs.launchpad.net/audio-recorder/+bug/973809)

I have only crafted packages for Ubuntu 12.04 but it should also run on Ubuntu 11.10 (if you compile it from source ;-).  

Would you please test the version 0.9 on Ubuntu 12.04.
Use your favourite player and make a recording of a radio-channel, etc. Test even Skype if you use it.

Please check the output file.
 
Check also if the icons for audio sources and players are OK. (see the listbox in the GUI). 

Package for audio-recorder 0.9 (for Precice!) should be ready now.
Ref: [https://launchpad.net/~osmoma/+archive/audio-recorder/+packages](https://launchpad.net/~osmoma/+archive/audio-recorder/+packages)

---

### Post by mc4man on 2012-04-21
0.9 is working good
As far as mpris2 - 
by default RB & banshee (if installed) will show (always

To add additional mpris2 players I've found  - 
First start the player, then start AR (if Ar is autostarting in indicators close it out

Then that player will be added & avail. from list but this isn't persistent, only shows as described - player, then AR

Screen show an add. 3 added, noting obviously all 3 are running

A few really minor - don't exactly matter?
The Ar window is set to be always on top  & set to show on all WS's

Edit: as far as the 3 add. I have installed Ar works thru mpris2 with totem-3.2/3.4 & audacious, vlc only manually (atm using repo 2.0.1, will put in 2.1-git shortly

---

### Post by moma on 2012-04-22
Hello,
You are right. Only RhythmBox and Banshee (if installed) are added programmatically to the listbox. These are the most often used players on Ubuntu/Fedora.

Have you used the small "reload" button beside the listbox (the small blue knob in your picture). Clicking it should re-load the player list, so there is no need to restart the recorder.

Of course, it may happen AR fails to start the player automatically when selected. This should be easy to fix because AR already knows both the xxx.desktop file and the name of player's MPRIS2-interface, such as "org.mpris.MediaPlayer2.banshee". It should be easy to start this service/program from AR. The current start_app() function needs re-thinking.
Ref: src/dbus-mpris2.c (func mpris2_start_app(...)).

I thought that the "StartServiceByName" call could do this. 
Tested it with:
```
$ dbus-send --session --dest="org.freedesktop.DBus" \
              "/org/freedesktop/DBus" \
              "org.freedesktop.DBus.StartServiceByName" \
              "string:org.mpris.MediaPlayer2.rhythmbox" \
              "int32:0"
```
But it does nothing. This needs googling!

A suggestion for improvement.
The list could remember the detected MPRIS2-players. Of course it should check at start if these programs (executables) still exist in the system. And it should automatically restart the lastly selected player. Now it simply forgets the players that are shut off.

And thanks for your through test. Lovely to see that both Totem and VLC are MPRIS2-compatible.

---

### Post by mc4man on 2012-04-22
I added audacious, (3.2.1) to the manual list (dbus-player.c), works well, audacious use's a mpris2 plugin which should be default enabled in 12.04

Assume totem-3.2/4 would as well (not available in default 12.04

vlc is an 'odd' case, as mentioned before even if set in the sources list won't work to control AR though will with the traditional manual method.

What's a bit different about vlc in general is that it will not be seen in the sound indicator, (usually),  until a new vlcrc is created after the orig. new install. All other players show after first use. Whether that 'fact' indicates some diff in vlc's implementation that is relevant to not working in Ar mpris2 wise don't know

---

### Post by moma on 2012-04-23
Mc4man,
You may attach your batch (the code fragment) for Audacious in this thread.
Ok, I understand more about the VLC issue. I will now install VLC on my Ubuntu 12.10 (from the repo) and gonna debug it here.

I think the app-list needs some refinement. At least it should remember the lastly selected player (besides the fixed entries; Rhythmbox, Banshee and your Audacious). 

Your help has been valuable.

// Moma Antero

---

### Post by mc4man on 2012-04-23
Moma - I just tucked on to the end of that section as in debdiff (removed changelog

As far as remembering - currently when using autostart it does 'remember' last set source - if that was a player then the player is also started on login. Some may like that, others won't.
Wouldn't be the worst thing if upon exiting reverted to a default audio source (Built-in Audio ... here) though I'm ok with current behavior

---

