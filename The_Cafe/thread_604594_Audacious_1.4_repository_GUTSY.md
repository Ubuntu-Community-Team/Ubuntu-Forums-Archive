---
title: "Audacious 1.4 repository GUTSY"
date: 2007-11-06
forum: The Cafe
---

### Post by Kosimo on 2007-11-06
Did you guys give it a try to the latest audacious 1.4?

We have already official repositories for Gutsy:

Just add this one: ```
deb [http://backports.dereferenced.org/](http://backports.dereferenced.org/) gutsy universe

```

If you already have some previuos version, you should uninstall it first.

New skins included:

[IMG]http://kosimo.googlepages.com/audacious1.4.png[/IMG]


Finally, I'm having something really similar to what I had in windows. My lovely Winamp. Similar appearance & similar functionalities. 

Enjoy

---

### Post by Major_Kong on 2007-11-19
Works great so far.

---

### Post by kodak on 2007-11-19
Does Audacious work in Gnome?

Forget that question


i just seen your side panel/

btw Audacious is a very slick modern player, and uses mush less resource than XmmS

---

### Post by Onyros on 2007-11-19
> **kodak said:**
> Does Audacious work in Gnome?

Forget that question


i just seen your side panel/

btw Audacious is a very slick modern player, and** uses mush less resource than XmmS**Not so, not so... ;)

XMMS uses less than half of the resources Audacious uses.

---

### Post by ariel on 2007-11-21
1.4.2 has been released upstream

---

### Post by DrMega on 2007-11-21
How do I add the repository? I saw the line to add but not sure where to put it.

---

### Post by smartboyathome on 2007-11-21
Open up software sources (in System > Administration), and create a new entry in the Third Party Repositories tab. Put the line in the dialog box that pops up asking you the address of the repo.

---

### Post by Incense on 2007-11-21
> **Onyros said:**
> Not so, not so... ;)

XMMS uses less than half of the resources Audacious uses.

It is still much less then Amarok or Banshee. Audacious is a great music player! I'm running 1.4 on openSUSE right now in fact!

---

### Post by DrMega on 2007-11-21
> **smartboyathome said:**
> Open up software sources (in System > Administration), and create a new entry in the Third Party Repositories tab. Put the line in the dialog box that pops up asking you the address of the repo.

Thanks. Got it running now. It is a nice audio player.

---

### Post by mthei on 2007-11-21
> **Onyros said:**
> Not so, not so... ;)

XMMS uses less than half of the resources Audacious uses.


While you're correct, is XMMS still better? I know it's no longer actively developed, but does that mean there may be some security flaws in it that are not being corrected?

Both are probably the best sounding players for Linux, as well as MPD, of course, but what makes me chose Audacious over the other two mentioned is the fact that Audacious uses Gnome's file browser for opening windows, and will not send files that start with A or B, for example, to the bottom of the list because they may not be capitalised.

---

### Post by Incense on 2007-11-21
> **mthei said:**
> While you're correct, is XMMS still better? I know it's no longer actively developed, but does that mean there may be some security flaws in it that are not being corrected?

Both are probably the best sounding players for Linux, as well as MPD, of course, but what makes me chose Audacious over the other two mentioned is the fact that Audacious uses Gnome's file browser for opening windows, and will not send files that start with A or B, for example, to the bottom of the list because they may not be capitalised.

Actually the XMMS guys just released 1.2.11 on the 16th of this month. 1211 days since the last release. Guess XMMS isn't quite dead yet.

---

### Post by Onyros on 2007-11-22
Naa, I wasn't stating XMMS was better in any way other than memory usage ;)

Even so, I still use it, instead of Audacious. GTK1 doesn't bother me that much, same goes for a few playlist quirks; I just don't use Audacious because I prefer XMMS' equalizer implementation, that's just it.

And don't get me started on the whole equalizer usage stuff, or I'll have to redirect you to Rhythmbox's developers discussion regarding just that. :P

Only app I miss from Windows, runs on Wine but stutters with CPU usage... foobar2000. Unfortunately, there's no Linux port on the horizon, but that was THE audio player.

Regarding the new XMMS release: did those guys get bitter or what? Guess that being dropped from Gentoo and even being considered for the same in Debian (of all distros!), makes people that way, huh?

---

### Post by mthei on 2007-11-22
> **Incense said:**
> Actually the XMMS guys just released 1.2.11 on the 16th of this month. 1211 days since the last release. Guess XMMS isn't quite dead yet.

How unexpected. I'll be sure to give it a try.

---

### Post by nenolod on 2007-11-23
XMMS 1.2.11 will never enter Ubuntu because it's imported from Debian and the Debian maintainer has filed a remove request, not an Orphan request.

He has a goal of removing GTK1 from Debian entirely, of which XMMS packages are a sizeable chunk.

As for my backport, 1.4.2 is building (built on amd64). I've been busy with other things, including rescuing various packages which have both xmms and audacious flavors from being killed along with XMMS.

---

### Post by nenolod on 2007-11-23
Audacious 1.4.2 built on all architectures supported by backports.dereferenced.org.

Additionally, I have built an updated audacious-crossfade package too.

---

### Post by limaunion on 2007-11-25
Thanks for this backport!

---

### Post by MeduZa on 2007-12-24
I love audaciuos, XMMS crash a lot on my pc, I don't know why, Audacious is perfect, I control it whit the logitech's keyboad multimedia keys, interact whit pidgin and with lcd4linux, and the system tray feature is greath! the sound is cristal quality, I upgrade to 1.4.x few minutes ago :guitar:

---

### Post by Kosimo on 2007-12-24
I love my audacious with Winamp skin ;)

[IMG]http://kosimo.googlepages.com/audacious1.4winampskin.png[/IMG]

---

### Post by meho_r on 2007-12-26
Audacious 1.4.4. is out. Update?

---

### Post by whitethorn on 2008-01-01
Hi, I removed the old version of audacious 1.3.3 I think and added the repository, I removed the old version before I installed the new version but now I get some really wierd mistakes.  Seems a bunch of the plugins don't load.  I was hoping to get the global shortcuts working...

neway here's the code I get when I start audacious in the terminal

Failed to load plugin (/usr/lib/audacious/Input/libmplayer.so): /usr/lib/audacious/Input/libmplayer.so: undefined symbol: ctrlsocket_get_session_id
Failed to load plugin (/usr/lib/audacious/Input/libcube.so): /usr/lib/audacious/Input/libcube.so: undefined symbol: xmms_usleep
Failed to load plugin (/usr/lib/audacious/General/libnotify.so): /usr/lib/audacious/General/libnotify.so: undefined symbol: ip_data
Failed to load plugin (/usr/lib/audacious/Visualization/libiris.so): /usr/lib/audacious/Visualization/libiris.so: undefined symbol: xmms_usleep
amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded

I still kinda new to ubuntu, so some help would be great

---

### Post by mmxbass on 2008-01-14
Yea  we could really use the 1.4.3 plugins and 1.4.4 audacious.

---

### Post by mustang on 2008-01-15
It didn't render my winamp 2.1 skin too well (a black bar through the bitrate and sampling frequency).

Oh well, back to 1.3.2. Thanks anyways though :)

---

### Post by chocolatetoothpaste on 2008-01-15
> **mustang said:**
> It didn't render my winamp 2.1 skin too well (a black bar through the bitrate and sampling frequency).

Oh well, back to 1.3.2. Thanks anyways though :)
I have a similar problem.  When I click on winamp skins to load them, the skin never changes and some random black strips show up over the previous skin.  I'm running openbox 3.4

---

### Post by SoulSmasher on 2008-02-01
worked just fine, thanks :)

---

### Post by SoulSmasher on 2008-02-29
by the way, will this source be updated for 1.4.6 ?? it's still 1.4.3 inside

---

### Post by andrew.46 on 2008-03-04
Hi,

 Actually I am still on the older version,

> **Kosimo said:**
> Did you guys give it a try to the latest audacious 1.4?

 But where can I get a copy of your amazing wallpaper?

               Andrew

---

### Post by andrewabc on 2008-03-05
> **andrew.46 said:**
> Hi,
Actually I am still on the older version,

 But where can I get a copy of your amazing wallpaper?

Andrew

The mountain wallpaper can be found at
[http://interfacelift.com/](http://interfacelift.com/)
along with lots of other good wallpapers.

---

### Post by bsmith1051 on 2008-03-14
How about a 1.5.0 release?  It just came out yesterday,
[http://audacious-media-player.org/](http://audacious-media-player.org/)

---

