---
title: "Guitar Rig 3 doesn't start"
date: 2009-04-20
forum: Wine
---

### Post by aenima1891 on 2009-04-20
if i try to run Guitar Rig 3 from terminal, I obtain this output:
```
fixme:win:RegisterDeviceNotificationA (hwnd=0x1002c, filter=0x32fcc8,flags=0x00000000),
        returns a fake device notification handle!
fixme:win:RegisterDeviceNotificationA (hwnd=0x1002c, filter=0x32fcd0,flags=0x00000000),
        returns a fake device notification handle!

```
I'm using Kubuntu Jaunty 9.04 with wine 1.1.19. My default sound card is M-Audio Fast Track USB
How can i solve this problem? please help me...i'm relatively new in linux:KS

---

### Post by aenima1891 on 2009-05-03
now i'm using Ubuntu Jaunty, but i have the same problem
```
fixme:win:RegisterDeviceNotificationA (hwnd=0x1002c, filter=0x32fcc8,flags=0x00000000),
	returns a fake device notification handle!
fixme:win:RegisterDeviceNotificationA (hwnd=0x1002c, filter=0x32fcd0,flags=0x00000000),
	returns a fake device notification handle!


```

please help me

---

### Post by Nareto on 2009-06-20
I have the same problem. Prior of installing wineasio it was working, though it would take some minutes to pop up. Unfortunately i never did start it from terminal so i don't know if i was getting this error even before wineasio.
Searching for solution

---

### Post by ldk_linux on 2009-07-16
I have been having the problem for ages (Guitar Rig 2 and Guitar Rig 3). The funny thing is that this only happens on some machines, and with certain kernels.

I have come to the conclusion that this issue is a deadlock bug inside Guitar Rig, that for some reason never happens under Windows, but sometimes happens under Linux. Whatever the reason is the consequence is that there is no wat to reliably run GR on Linux :-(

If you are looking for some nice effects to use under Linux, I recommend two possible solutions:

1) Use IK Multimedia Amplitube, which is decent and seems to work well under Linux (especially with recent versions of Wine)

2) Use the Simulanalog VST suite ([www.simulanalog.org](www.simulanalog.org)). It is a free suite of VST that faithfully reproduce a bunch of effects and amps of the past - some of them are so-so, but others (like the JCM and the TubeScreamer) kick ***. They are Windows VSTs, so you need a VST-aware host for Linux (like Ardour or Reaper).

---

### Post by Nareto on 2009-07-17
regarding my above post on wineasio, that's not true: Guitar Rig 3 will start, fact is sometimes it will take 50 minutes from when i launch it to when it pops up. And nothing relevant in terminal. Yep, totally unreliable.

> **ldk_linux said:**
> 
If you are looking for some nice effects to use under Linux, I recommend two possible solutions:

1) Use IK Multimedia Amplitube, which is decent and seems to work well under Linux (especially with recent versions of Wine)

2) Use the Simulanalog VST suite ([www.simulanalog.org](www.simulanalog.org)). It is a free suite of VST that faithfully reproduce a bunch of effects and amps of the past - some of them are so-so, but others (like the JCM and the TubeScreamer) kick ***. They are Windows VSTs, so you need a VST-aware host for Linux (like Ardour or Reaper).

Or better still [rakarrack]("http://rakarrack.sourceforge.net/") which has *very* interesting sounds and best of all is open source and runs natively on linux. There's also guitarix which seems more specifically oriented on distorted guitar (haven't tried it as much though). Or you could simply use jack-rack which is fully midi controllable (btw guitarix effects are avaiable in jack-rack too)

---

### Post by ldk_linux on 2009-07-17
Nareto,

I would love to use OpenSource software to process my guitar sound... but I tried a lot of apps including RackArrak and the CAPS LADSPA plugins and I was never satisfied with the results. This is the only reason I am recommending commercial software.

However, I didn't know about Guitarix. Looks pretty cool, I will give it a try :-)

---

### Post by athalyba on 2009-09-13
Just for the record: when trying to run GR3 from the terminal, the following message comes:

fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 15/02/2009, dlt (d/m/y): 18/10/2009
fixme:win:RegisterDeviceNotificationA (hwnd=0x10028, filter=0x32fcc8,flags=0x00000000),
    returns a fake device notification handle!
fixme:win:RegisterDeviceNotificationA (hwnd=0x10028, filter=0x32fcd0,flags=0x00000000),
    returns a fake device notification handle!

If after 50 minutes it works, I'll back with the news :-)

---

