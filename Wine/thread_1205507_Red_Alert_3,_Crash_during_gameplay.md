---
title: "Red Alert 3, Crash during gameplay"
date: 2009-07-06
forum: Wine
---

### Post by Joe_ on 2009-07-06
I'm currently experiencing a problem with playing Red Alert 3. It installs perfectly, runs fine, and then unexpectedly crashes in the middle of missions. I don't *think* it's crashed except during gameplay, and it crashes at indeterminate and unexpected times after a mission/tutorial begins. I've only tested single player.

I'm running Ubuntu 9.04 and Wine 1.1.24.

The main error I'm getting in terminal is:
E: shm.c: mmap() failed: [COLOR=red]Cannot allocate memory[/COLOR]
E: shm.c: mmap() failed: [COLOR=red]Cannot allocate memory[/COLOR]
E: memblock.c: [COLOR=red]Assertion 'b' failed at pulsecore/memblock.c:438, function pa_memblock_acquire(). Aborting.[/COLOR]

After some searching, I took this to be a problem with Pulse Audio. I don't know how to get pasuspender to work and going to System->Preferences->Sound and setting everything to ALSA instead of Pulse Audio didn't fix the problem (exact same error message). Is it not a problem with pulse audio or am I disabling it incorrectly?

---

### Post by khelben1979 on 2009-07-06
Are you using the -opengl parameter?

---

### Post by Joe_ on 2009-07-06
No, I'm not familiar.

---

### Post by khelben1979 on 2009-07-06
Many games runs a lot slower if you don't use the -opengl parameter and some games won't work correctly.

```
wine -opengl [game name]
``` (something like that. I'm not sure if you need more parameters)

---

### Post by Joe_ on 2009-07-06
I got it to work by following this guide to disable pulseaudio.

[http://www.donationcoder.com/Forums/bb/index.php?topic=18769.0](http://www.donationcoder.com/Forums/bb/index.php?topic=18769.0)


It can only go a single mission at a time before crashing (it'll yell "stub" and crash before starting a second mission), but that's okay. At least it's working.

---

