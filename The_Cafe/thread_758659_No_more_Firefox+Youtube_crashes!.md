---
title: "No more Firefox+Youtube crashes!"
date: 2008-04-18
forum: The Cafe
---

### Post by pseudo-random on 2008-04-18
Just got this update through with Hardy Heron yesterday:
[IMG]http://wintolin.co.uk/images/flash-plugin.jpg[/IMG]
According to the details it fixes the notorious flash-crash when on youtube etc.
There's plenty threads with different solutions, none of which have ever worked for me so I'm pleased to see the problem-solution process working. So far I've had zero crashes as opposed to a 10% crash frequency when watching Youtube vids. Great work, Keep it up guys.
:)

---

### Post by Wobedraggled on 2008-04-18
I'll have to test it later, with my "special" sites.


Talk about a buzzkill. 


:lolflag:

---

### Post by Seisen on 2008-04-18
Its about time they fixed that problem.

---

### Post by FuturePilot on 2008-04-18
I don't think it was the usual Flash crashing problem. With the introduction of PulseAudio and libflashsupport, there was excessive crashing. This just removed libflashsupport as a dependency of flashplugin-nonfree. So it's no different than the way it was setup in previous versions of Ubuntu. Some have already said it still freezes when leaving a page with Flash in it.

```
flashplugin-nonfree (9.0.124.0ubuntu2) hardy; urgency=low

  * fix "frequent crashes with flash on youtube"; we fix this by
    demoting libflashsupport from depends: to suggests: (LP: #192888)
    This has positive as well as negative consequences:
     (+) increased stability for firefox and nspluginwrapper
     (-) pulseaudio users reported that this breaks sound if flash
         while other applications are running that use the sound
         device for output.
    Users that installed libflashsupport during hardy cycle should
    uninstall it to increase stability.
    - update debian/control

 -- Alexander Sack < [email]asac@ubuntu.com[/email]>   Wed, 16 Apr 2008 00:39:41 +0200
```

---

### Post by -grubby on 2008-04-18
YAY!! I just checked my updates. It's updating as we speak. I've been waiting a long time for this to be fixed

---

### Post by tigerplug on 2008-04-18
> **pseudo-random said:**
> Just got this update through with Hardy Heron yesterday:
[IMG]http://wintolin.co.uk/images/flash-plugin.jpg[/IMG]
According to the details it fixes the notorious flash-crash when on youtube etc.
There's plenty threads with different solutions, none of which have ever worked for me so I'm pleased to see the problem-solution process working. So far I've had zero crashes as opposed to a 10% crash frequency when watching Youtube vids. Great work, Keep it up guys.
:)


Excellent!:guitar:

---

### Post by derekr44 on 2008-04-18
I'm glad.  This was very annoying.

---

### Post by amazingtaters on 2008-04-18
seems since today's updates I can't play .wmv's anymore. Stupid mplayer plugins.

---

### Post by ZarathustraDK on 2008-04-18
YES!

This has to be most annoying problem ever on my comp.

Hasn't crashed yet.

*crosses fingers*

---

### Post by imopen on 2008-04-18
my firefox 3b5 still crush :mad:

---

### Post by Blue Heron on 2008-04-18
ff is also to blame

---

### Post by FuturePilot on 2008-04-18
> **Blue Heron said:**
> ff is also to blame

It's not. This is a Flash problem. It will crash any browser, not just Firefox.

---

### Post by Blue Heron on 2008-04-18
> **FuturePilot said:**
> It's not. This is a Flash problem. It will crash any browser, not just Firefox.

nope, good software can handle crashes:
instead of crashing itself FF must say: **Plugin crashed, restarting plugin**

---

### Post by ZarathustraDK on 2008-04-19
Hmm I did get ff to crash by voraciously opening and closing tabs from youtube. Didn't 'feel' like the 50/50 risk-crash I experienced before though. Usually I get to see a flicker of the video (or at least the controls of the player) before it crashes; didn't get that far this time.

Still it's an isolated incidence for my part.

---

### Post by imopen on 2008-04-19
After had blamed FF and Hardy Heron for a weekend, it was crashing every two/three web sites with Flash in the page :mad:, I found the solution for me... I hope it'll work for you, too.

1) install latest "flashplugin-nonfree" package

2) Then UNINSTALL "libflashsupport" package

3) select Alsa as default sound server, for any application. System->Preferences->Sound, select ALSA on Sounds Event, Music and Movies, Audio Conferencing.


My sistem now works like a charm :guitar:


I think that PulseAudio is an immature technology and enabling it by default in Hardy Heron is a suicide choice. :rolleyes:


I come back to me lovely FF that now has no problem with flash (thanks Alsa) :)

---

### Post by bash on 2008-04-19
The funny thing is: FF never crashed for me until yesterdays update. Now it crashes constantly. :/

---

### Post by Pathfinder_ on 2008-04-19
> **bash said:**
> The funny thing is: FF never crashed for me until yesterdays update. Now it crashes constantly. :/

Crashes about 80% of the time when I'm browsing youtube. Unacceptable for being this close to final release.

---

### Post by boteeka on 2008-04-20
I uninstalled flashplugin-nonfree and libflashsupport, reinstalled flashplugin-nonfree and now flash plays nicely with ff.

But I still have problems. After playing some youtube video in ff, there is no way to get sound from any other application until I quit ff first. I _hate_ this situation.

---

