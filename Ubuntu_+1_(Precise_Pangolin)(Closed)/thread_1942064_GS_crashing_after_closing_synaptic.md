---
title: "GS crashing after closing synaptic"
date: 2012-03-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Quackers on 2012-03-16
Over the last 3 or 4 days I've seen a number of gnome-shell crashes. These appear to be most often just after closing synaptic.
The desktop can freeze except for the cursor or sometimes it will go to a black screen and then reload ok.
The last time was about an hour ago and the desktop froze up. I waited for about 5 minutes and still couldn't click on anything. So, in preparation for a REISUB I held down Alt Gr and Sys Rq keys and the screen flashed to black and GS reloaded.
Coincidence? Dunno :confused:

Anyone seeing similar occurrences?

---

### Post by keithpeter on 2012-03-17
Hello Quackers

Yup, see [http://ubuntuforums.org/showthread.php?t=1942035](http://ubuntuforums.org/showthread.php?t=1942035)

What video card/drivers are you using? There has been history with nvidia and nvidia provided drivers...

Moderators: merge these threads to see if anyone else has similar issues?

---

### Post by Quackers on 2012-03-17
Nvidia 8600M GT with up to date Nvidia driver.
There were problems, as I remember it, with Nvidia and 12-04 not getting on for a while, but those were solved some time ago.
Also synaptic has had one or two problems, but those too were solved some time ago, as far as I'm aware.

On this system there is also a more disturbing item I just noticed.
With nothing else running but this open firefox tab gnome-shell is using 770M of ram on its own!
On startup GS uses about 116M of ram, at idle. Sadly as the system's up-time accumulates GS's use of ram jumps too.
The system has 20 hours of up-time on the clock and ram use by GS has just gone to 772M. 
I'll have to reboot soon just to calm things down again.

---

### Post by Quackers on 2012-03-17
I've updated to the new kernel and synaptic doesn't seem to crash GS at the moment, but ram usage is still increasing.
6 hours up-time and GS is using 258M at idle( at startup it runs about 114M). I'm not 100% but I think GS may not be releasing ram after using it. Just a hunch from watching my conky output.

---

### Post by keithpeter on 2012-03-17
Hello Quackers and all

Gnome-Shell certainly more stable at present after the kernel upgrade (i386-pae)

top is reporting 
```

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
1690 keith     20   0  668m 146m  50m S    8  3.6   1:44.69 gnome-shell
```

after 45 mins or so. I'll have it running most of tomorrow as I'm writing some stuff. Moving a 'heavy' window (libreoffice, firefox) around really pushes the cpu%

---

### Post by keithpeter on 2012-03-18
Hello All

Still getting the freezes on gnome-shell, its Libreoffice. Scrolling or resizing windows causes a freeze.

Anyone any ideas where to find a log file that might explain what is triggering this?

---

### Post by Quackers on 2012-03-20
Apart from the apparent extreme ram usage for GS (which has slowed somewhat since yesterday's updates), things have been ok for the last 2 days (ie no GS crashes after closing synaptic).

I've just run today's updates and on closing synaptic GS crashed again. The screen freezes, conky display freezes and nothing is clickable. No Alt + F2, no ctrl + Alt + T, nothing. Then after about 20 seconds or so the screen flashes to black and GS returns working normally.

It's a bit of an oddity.

BTW this is a 64 bit standard upgrade from OO with no GS-related repo's enabled.

---

