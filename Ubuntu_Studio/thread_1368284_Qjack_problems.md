---
title: "Qjack problems"
date: 2009-12-30
forum: Ubuntu Studio
---

### Post by nick_geetar on 2009-12-30
Message on my Qjack says some weird stuff that doesn't look normal.This is my message that I get when I press start on Jack. It connects and I'm able to run some apps but it just don't look right.
 p, li { white-space: pre-wrap; }  [COLOR=#999999]12:52:53.364 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:52:53.366 Statistics reset.[/COLOR]
 [COLOR=#66CC99]12:52:53.388 ALSA connection graph change.[/COLOR]
 [COLOR=#CCCC99]12:52:53.624 ALSA connection change.[/COLOR]
 [COLOR=#999999]12:52:57.536 Startup script...[/COLOR]
 [COLOR=#990099]12:52:57.538 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]12:52:57.942 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]12:52:57.942 JACK is starting...[/COLOR]
 [COLOR=#990099]12:52:57.943 /usr/bin/jackd -R -dalsa -r44100 -p512 -n2 -D -Chw:0,0 -Phw:0,0 -zs[/COLOR]
 [COLOR=#999999]12:52:57.948 JACK was started with PID=3206.[/COLOR]
 no message buffer overruns
 jackd 0.116.1
 Copyright 2001-2005 Paul Davis and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK compiled with System V SHM support.
 cannot lock down memory for jackd (Cannot allocate memory)
 loading driver ..
 Enhanced3DNow! detected
 SSE2 detected
 apparent rate = 44100
 creating alsa driver ... hw:0,0|hw:0,0|512|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 configuring for 44100Hz, period = 512 frames (11.6 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback
 JACK: unable to mlock() port buffers: Cannot allocate memory
 JACK: unable to mlock() port buffers: Cannot allocate memory
 [COLOR=#999933]12:53:00.065 Server configuration saved to "/home/nick/.jackdrc".[/COLOR]
 [COLOR=#999999]12:53:00.067 Statistics reset.[/COLOR]
 [COLOR=#999999]12:53:00.071 Client activated.[/COLOR]
 [COLOR=#9999CC]12:53:00.074 JACK connection change.[/COLOR]
 [COLOR=#CC9966]12:53:00.082 JACK connection graph change.[/COLOR]
 Enhanced3DNow! detected
 SSE2 detected
 cannot lock down memory for RT thread (Cannot allocate memory)

---

### Post by AutoStatic on 2009-12-30
```
cannot lock down memory for RT thread (Cannot allocate memory)
```

Hello Nick, which Ubuntu version? You're probably missing a line like the following in */etc/security/limits.conf*:
```
@audio - memlock unlimited  # maximum locked-in-memory address space (KB)
```
And could you post the contents of your */home/nick/.jackdrc* file?

---

### Post by nick_geetar on 2009-12-31
I'm running karmic studio. I am missing the text in my config file. Should I add it? I couldn't find the jackdrc file though.

---

### Post by cchhrriiss121212 on 2009-12-31
Studio has a GUI for this now. Go to Ubuntu Studio controls under System>Administration. Check the box that says enable memlock and set a percentage of memory you would like to allocate, I set mine at 90%. A nice value of about -15 is recommended as well.

To view that jackdrc file you need to have jack open and select view hidden files.

---

### Post by nick_geetar on 2010-01-02
Hey thanks for the help. My jack is runnin fine now.

---

### Post by Thrashard on 2011-03-07
I have some problems too.
I am using Ubuntu 10.04 LTS

.jackdrc
> /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2




limits.conf:
> #@audio          -       rtprio          90
#@audio          -       nice            -10
#@audio          -       memlock         unlimited

---

### Post by cchhrriiss121212 on 2011-03-07
Just remove the comment symbols, a # means the system will ignore whatever is on that line.

---

### Post by Thrashard on 2011-03-12
One more problem. If i insert guitar's jack in the laptop's mic hole, it works on integrated speaker but if i insert both the jack of my creative speakers there's no sound. WTF? :D

---

### Post by cchhrriiss121212 on 2011-03-12
Try starting a new thread in the hardware section, as this is not a jack issue. Remember to post what devices you are using.

---

