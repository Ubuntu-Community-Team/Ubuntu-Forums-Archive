---
title: "Decent software mixer with multiple volume sliders?"
date: 2009-11-01
forum: The Cafe
---

### Post by Johnsie on 2009-11-01
Just had a look in sound preferences. I'm looking do some recording/listening. I would like a software mixer with lots of sliders, kind of like  the one in Windows XP where they are all on the same window.

Is there any way to get something like this with Ubuntu?

---

### Post by Metallion on 2009-11-01
That would be Volume Applet. Just right click on your panel and choose "add to panel". It should be in the list.

---

### Post by Johnsie on 2009-11-01
nope it's not there.

---

### Post by FuturePilot on 2009-11-01
They changed the sound preferences in Karmic. The familiar gnome mixer applet is gone. You might be interested in gnome-alsamixer

---

### Post by Johnsie on 2009-11-01
Yeah, so I see... I take it they aren't aiming karmic and sound professionals?

---

### Post by Skripka on 2009-11-01
> **Johnsie said:**
> Yeah, so I see... I take it they aren't aiming karmic and sound professionals?

Nope.  No linux really is.  There are virtually no professional quality apps written for linux....and those few that are-are shot down by the state of development of the necessary backends.

---

### Post by Johnsie on 2009-11-01
I did find one app that looked promising... Linux music studio or something like that. Never really used it much though.

I've just installed gnome-alsamixer. It didn't fit on my screen and there's no way to make the window any smaller. hat is the type of thing I'm looking for, but maybe with a little more quality assurance put into the UI ;-)

---

### Post by SunnyRabbiera on 2009-11-01
Gnome-alsamixer will give you a multichannel mixer, its just not there in karmic as Karmic uses Pulse by default.

---

### Post by Johnsie on 2009-11-01
Yeah, gnome-alsamixer doesn't fit on my screen. It's too wide and cant be resized any further. I might have to recompile it with a new layout.

I don't understand why the default mixer on Karmic is so bad.

---

### Post by unamanic on 2009-11-01
I use kmix:

```

sudo aptitude install kmix

```

Sure it's a KDE app, but it has a polished feel and it has multi channel mixing and capture source selection so I can switch between the mic jack and the digital mics built into my laptop.

---

### Post by SunnyRabbiera on 2009-11-01
> **Johnsie said:**
> Yeah, gnome-alsamixer doesn't fit on my screen. It's too wide and cant be resized any further. I might have to recompile it with a new layout.

I don't understand why the default mixer on Karmic is so bad.

Like I said its made mainly for pulseaudio.
Pulseaudio is still new tech so not all of its capacity has truly been explored, in the near future we might see a full fledged mixer for pulse.
Give it time, or use KDE that doesn't automatically use pulse.

---

### Post by Johnsie on 2009-11-01
I'm checking out kmix. I don't think having a 'work in progress' application in a release version of an operating system is a good idea. It's not very polished and makes the quality assurance of Ubuntu look bad. I have alot of friends who do recording and I simply couldn't recommend Ubuntu to them in its current state.

Edit: Just tried kmix. It lookslike the best of a bad bunch

---

### Post by Skripka on 2009-11-01
> **Johnsie said:**
>  I have alot of friends who do recording and I simply couldn't recommend Ubuntu to them in its current state.

Anything beyond the most basic single mic recording, under linux, basically requires JACK...and getting JACK to work right for the application at hand is only slightly less enjoyable that a root-canal.

Virtually every audio professional I know uses OSX and ProTools.  Easy handling of multiple inputs/outputs, and no need to recompile a real time kernel etc.  No linux is really suited to professional audio demands, out of the box.

KMix is good for handling multipke devices, but does not allow for software equalizing.  It only lets you control the gain on the device, not frequency bands.

---

### Post by Johnsie on 2009-11-01
Same here. I don't see Ubuntu becoming capable of professional sound engineering any time soon.

---

### Post by Skripka on 2009-11-01
> **Johnsie said:**
> Same here. I don't see Ubuntu becoming capable of professional sound engineering any time soon.

I'm speaking of linux en general, not just Ubuntu.

---

### Post by SunnyRabbiera on 2009-11-01
> **Johnsie said:**
> I'm checking out kmix. I don't think having a 'work in progress' application in a release version of an operating system is a good idea. It's not very polished and makes the quality assurance of Ubuntu look bad. I have alot of friends who do recording and I simply couldn't recommend Ubuntu to them in its current state.

Well Karmic is meant to be in a "experimental state" most of its features are the stepping stones to 10.04.
You got to realize that most of the tech you see in Ubuntu Karmic is a work in progress, sure it might not look "professional" right now but there is a lot of new projects coming to Ubuntu in the near future.
Gnome 3 is a big one right now, we are hoping to see a lot of decent tools and loads of functionality when it comes out.
For now Ubuntu might not be for you, try openSUSE or something Ubuntu is not the only fish in the sea.
You cant criticize the entirety of linux based on Ubuntu, Ubuntu does its own thing to simplify the user experience and bring the user some good tools to start off with.
Progress will be made.

> **Skripka said:**
> I'm speaking of linux en general, not just Ubuntu.

well someones been drinking the linsux cool aid.

---

### Post by Metallion on 2009-11-01
> **FuturePilot said:**
> They changed the sound preferences in Karmic. The familiar gnome mixer applet is gone. You might be interested in gnome-alsamixer

I see. Isn't it possible to install the old one still? I'm still on Jaunty here but what does "sudo apt-get install gnome-volume-control-pulse" do?

---

### Post by Skripka on 2009-11-01
> **SunnyRabbiera said:**
> 



well someones been drinking the linsux cool aid.

Nope.  It just is.  JACK is a PITA, that in addition to the Pulse or ALSA backend(s) is a big reason why no linux is at all suited to pro audio needs.  If you want to record anything with more than the most simple of setups-you're in for a MASSIVE headache.  Ardour is a GREAT tool, and a professional quality mixing station software by itself, that is incredibley capable...but it is all the depends--- things like JACK, and Pulse, as well as needing to compile a real-time kernel etc that make make it a PITA to get to doing anything with.

We haven't even started talking about hardware support problems yet.  Most folks in pro audio use XLR cabled mics with input/output digitizers that connect via USB, for on the go recording...You can basically FORGET about any kind of linux support for those incredibley handy, and rather expensive devices.

Go over to the Ardour forums to see and hear lots of amateur and pro audiophiles p*ssed about their expensive bricks they own, at least when trying to run them under linux.

---

### Post by wysiwyg31 on 2009-11-02
> **Skripka said:**
> You can basically FORGET about any kind of linux support for those incredibley handy, and rather expensive devices.


This is not a linux issue but a manufacturer issue.
Serious ones provides open source drivers and/or documentation. Nearly serious provide good drivers, narrow minded ones just dont care.
It's a pity if no supplier provide linux support for their XLR/USB devices. All I would do is to send email to those suppliers asking to be as professional as they may claim to be.:D


Anyway, this new windows instead of the mixer is a little bit annoying:
- no way to change system/disable system sounds 
- when I increase volume on totem, it increase system sound ( and make me jump to the ceiling at the next message sound on pidgin or whatever..)
- no more mute when double clic on the applet icon...
:(

---

### Post by Xbehave on 2009-11-02
> **Skripka said:**
> things like JACK, and Pulse, as well as needing to compile a real-time kernel etc that make make it a PITA to get to doing anything with.
While jack may still be a PITA to setup (i didn't find it that hard, but then again i didn't do anything serious with it), the ubuntu desktop kernels have enough in the way of realtime to run jack now (there is still work for linux to be a fully realtime kernel, but your default kernel is getting fairly close)

Getting more realtime is *just* a case of recompiling with a different config, however if you want a full realtime kernel you need to patch the mainline/get a separate tree altogether.

---

