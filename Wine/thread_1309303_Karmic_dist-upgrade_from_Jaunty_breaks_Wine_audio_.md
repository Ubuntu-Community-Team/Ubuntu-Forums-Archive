---
title: "Karmic dist-upgrade from Jaunty breaks Wine audio for Bioshock?"
date: 2009-11-01
forum: Wine
---

### Post by aoanla on 2009-11-01
Hi all,

So, I dist-upgraded from Jaunty to Karmic yesterday, and things seemed fine. In particular, nothing bad seemed to have happened to audio (testing in various applications, including Flash in Opera, audio works for all of them).

Until, that is, I got around to trying to play Bioshock in Steam in Wine.
Despite winecfg being happy to play test sounds, launching Bioshock now results in the terminal being spammed with 
```

 AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busy

```
and the game never completing launching (it hangs before going fullscreen - with just the Bioshock logo strip displayed).
Bioshock worked perfectly happily in Jaunty in Wine (1.1.32)

Fiddling with Pulseaudio options doesn't seem to do anything (I've tried changing the audio device, and enabling simultaneous audio) and trying wine with padsp (after winecfg with padsp) causes a crash with a pulseaudio assertion failure on bioshock launch.
Reinstalling Wine from the wine1.2 development branch target in Karmic also doesn't fix anything.

Needless to say, this is decidedly suboptimal. 
Does anyone have any ideas (other than the Wine guys actually biting the bullet and writing a PulseAudio driver...)?

edited to add:

Hmm, Team Fortress 2 also doesn't work properly - whilst the audio plays on the Valve video before it starts up properly, it then seems to hang at the menu screen ( "loading..." in the bottom right corner, no sound) and trying to Alt-Tab out apparently results in an X crash, since the screen blanks and I end up back at the GDM login screen.
Of course, that might be a 1.1.31 problem, since I'm currently using the wine1.2 karmic package and I hadn't tried TF2 in 1.1.31 before...

edited again to add:

winecfg to OSS driver stops the spamming of the error about /dev/dsp being busy... but Bioshock still hangs at the same point (just with no output to the terminal now).

edited finally to add:
Ctrl-Cing out of Wine during the hang gives a:

m files\steam\steamapps\common\bioshock\Builds\Release\bioshock.exe: /build/buildd/openal-soft-1.8.466/OpenAL32/Include/alMain.h:73: DeleteCriticalSection: Assertion `ret == 0' failed.

before exit. 
I tried fiddling with OpenAL settings, but I'm not sure how to fix this (trying driver=pulse in /etc/openal/alsoft.conf doesn't fix it).


final final edit:
Using the Karmic Wine ppa, same problem exists for Bioshock.
Audiosurf works, however, launched from Steam, so this isn't a general problem with all wine games.

---

### Post by aoanla on 2009-11-01
Right. This appears to be an instance of bug 20177, to do with OpenAL problems in Wine/OpenAL Soft.

Following the advice in the thread (setting OpenAL to native with
```

export WINEDLLOVERRIDES="openal32=n"

```

allows me to launch Bioshock successfully (with winecfg set to ALSA mode).

---

