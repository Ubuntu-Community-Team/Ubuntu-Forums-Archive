---
title: "LMMS bad then no sound."
date: 2009-11-08
forum: Ubuntu Studio
---

### Post by Madspyman on 2009-11-08
Using the latest Ubuntu 9.10 (clean install). When I import or preview ogg or wav files they sound choppy and then eventually make no sound at all, nor does anything else that should. I have to restart the computer to get it working again but as soon as I import samples it screws up again. This never happened in Jaunty, lmms worked great in Jaunty (I even tried the version from the jaunty repo, still no dice.) 

Hope someone can help cause I like Karmic and don't want to have to downgrade over one program.

---

### Post by Madspyman on 2009-11-09
Ok I've been reading some more posts on the forums and it's obvious the Karmic still isn't ready for primetime. Upgrading to it from Jaunty breaks things, and many programs in the repo's won't function correctly even after a clean install. 

I have karmic on both my desktop and laptop and both are suffering from the same ailments, and my laptop won't come out of suspend mode without a restart.

Nobody seems to have any answers either because Karmic is still so new. 

These are some of the most embarrasing OS issues, if programs in the repositories don't work with karmic they shouldn't be in the repo's at all.

---

### Post by lightrush on 2009-11-10
If you want a stable OS you should use Hardy 8.04. It is an LTS version and it is based off Debian Stable. None of the releases other than LTS are really stable OSes in the sense of rigorously tested.

As for LMMS I have problems too but of a different kind.

---

### Post by Madspyman on 2009-11-11
Yeah I totally overreacted, I had to change my settings in Lmms from alsa to pulse, problem solved.

---

### Post by FreezWay on 2009-11-11
im using alsa and i get no sound, none....

---

### Post by Gannin on 2009-11-26
I'm having this issue as well, and I have to agree.  There are many things I like about Karmic, but it's by far the buggiest version of Ubuntu I've ever used.  I know they're trying to do some big things here, like transition the entire sound system over to Pulse and integrate it better into Gnome, but as it stands, at least from my point of view, Karmic is like the Vista of Ubuntu.

---

### Post by AutoStatic on 2009-11-27
> **FreezWay said:**
> im using alsa and i get no sound, none....That's because PulseAudio has your Alsa backend locked. You can either select PulseAudio as your audio device in LMMS or kill PulseAudio beforehand (**kill -9 pulseaudio**). You do need an extra file in ~/.pulse/client.conf then with the line *autospawn = no* otherwise PulseAudio will immediately respawn after you've killed it.

---

### Post by AutoStatic on 2009-11-27
> **Gannin said:**
> I'm having this issue as well, and I have to agree.  There are many things I like about Karmic, but it's by far the buggiest version of Ubuntu I've ever used.  I know they're trying to do some big things here, like transition the entire sound system over to Pulse and integrate it better into Gnome, but as it stands, at least from my point of view, Karmic is like the Vista of Ubuntu.What's so buggy about it then? And it's mostly the Gnome devs who are migrating the sound stack from ESD to PulseAudio AFAIK, not Ubuntu. Personally I think Karmic is a nice release: it starts up way faster, the RT kernel is pretty solid and most of the software is up to date again.

---

### Post by sgx on 2009-11-27
For one thing, the hardware probe says nvidia 6100 gfx are 800x600
maximum, a dealbreaker. I could probably dump in an xorg.conf from
a distro that gets it right, but last time I did that, gfx were 1280x1028, but the mouse was frozen, and I was going to be happier doing other things. ;) It looks like beta-testing of Karmic is going well, so maybe in February 2010, I may get up early, start the office coffeemaker, and build a working xorg.conf, or die trying :D

---

### Post by AutoStatic on 2009-11-27
> **sgx said:**
> For one thing, the hardware probe says nvidia 6100 gfx are 800x600
maximum, a dealbreaker. I could probably dump in an xorg.conf from
a distro that gets it right, but last time I did that, gfx were 1280x1028, but the mouse was frozen, and I was going to be happier doing other things. ;) It looks like beta-testing of Karmic is going well, so maybe in February 2010, I may get up early, start the office coffeemaker, and build a working xorg.conf, or die trying :DMaybe the nVidia driver is buggy?

---

### Post by mango42 on 2009-11-27
> **Gannin said:**
> Karmic is like the Vista of Ubuntu.

Oh please! That's tantamount to blasphemy!! =D>

Give it time or stay well behind the wave - these truly vocational coders are working flat out as it is. My policy (for a quieter life) is to keep one version behind current.

---

### Post by Gannin on 2009-11-27
> **mango42 said:**
> My policy (for a quieter life) is to keep one version behind current.

Who said anything about bringing logic into the discussion?  :P

---

### Post by keyshawn on 2009-12-16
thanks madspy, :guitar:

I switched mine to Pulse and it now worked. 

However, I would prefer to use Alsa since pulse has bad latency. 

My ~./pulse directory does not contain a .conf file.  my .pulse directory contains:

```

af081ec4b17b963d998bc67749a5d7a1-card-database.tdb
af081ec4b17b963d998bc67749a5d7a1-default-sink
af081ec4b17b963d998bc67749a5d7a1:default-sink
af081ec4b17b963d998bc67749a5d7a1-default-source
af081ec4b17b963d998bc67749a5d7a1:default-source
af081ec4b17b963d998bc67749a5d7a1:device-volumes.i486-pc-linux-gnu.gdbm
af081ec4b17b963d998bc67749a5d7a1-device-volumes.tdb
af081ec4b17b963d998bc67749a5d7a1-runtime
af081ec4b17b963d998bc67749a5d7a1:runtime
af081ec4b17b963d998bc67749a5d7a1:stream-volumes.i486-pc-linux-gnu.gdbm
af081ec4b17b963d998bc67749a5d7a1-stream-volumes.tdb
default-sink
default-source
volume-restore.table

```

do i have to create a file named .conf ?

---

### Post by RaumTrug on 2009-12-16
yep, clean alsa is much better for music production progs. I did it this way:

just do (alt-f2 or console) "gedit ~/.pulse/client.conf", add "autospawn = no" and save!

then make quicklaunchers somewhere in your panel, one executing "pulseaudio -k" (killing pulse the gentle way) and one "pulseaudio -D" (reactivates pulse).

in karmic, you'll notice if pulse is running or not with the volume control taskbar icon: if pulse is not running, it will disappear (so get some alsa mixer ready to be able to control levels).

[edit] sorry for stating gksudo before the gedit phrase...I removed it now. that'd probably make such a file for the "root" user, without it should work ;)

---

