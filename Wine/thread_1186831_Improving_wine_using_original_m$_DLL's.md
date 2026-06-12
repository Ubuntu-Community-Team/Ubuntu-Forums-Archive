---
title: "Improving wine using original m$ DLL's"
date: 2009-06-13
forum: Wine
---

### Post by Jorge M 93 on 2009-06-13
Hi guys; I just use wine for a few apps, but I was wondering if I could use some files (mostly DLL's) from my (almost forgotten) Vista partition to make wine work better. Is it possible? Is it risky to do it?

Thanks.:p

Jorge.

---

### Post by Nexusx6 on 2009-06-13
Its possible to do DLL overrides, but not advised.

Wine's current implementations of MS's DLL's are far better suited for doing the job of acting as a translation layer than MS's are. You could theoretically override all of Wine's DLL's with native ones, but it would only cause trouble and error.

Generally, the only time you should do a DLL override is when you have to as specified in a HowTo or, or a bug trace complains the a certain DLL is missing.

---

### Post by Jorge M 93 on 2009-06-13
o ... I see. Thanks!

So there is no way to improve wine using files from the win() partition?

(I'm not despret for running windows apps, I am just *wondering* ;))

---

### Post by cogadh on 2009-06-13
Like Nexusx6 said, you can add DLLs (or other files) from Windows, but you should only do that when an application has been complaining that a particular DLL/file is missing a function or is missing completely. Just adding DLLs/files when they aren't required is far more likely to break Wine than actually improve anything. Really the only DLLs that you *might* be able to get away with doing that to are the d3dx9_##.dll files (some games need them), but even those are starting to get functional Wine versions now, so in most cases doing that won't really help either.

---

### Post by Jorge M 93 on 2009-06-16
o OK Thanx.

---

### Post by nolliecrooked on 2009-06-16
Ive always installed the DirectX9.0c redistributable. Ive also added several other .DLLs, and never had a single screw up.

---

### Post by NightMKoder on 2009-06-16
> **nolliecrooked said:**
> Ive always installed the DirectX9.0c redistributable. Ive also added several other .DLLs, and never had a single screw up.

Lucky you. Wine has its own directx layer so by installing 9.0c you risked screwing a lot of things up. You can't run microsoft's directx for the simple reason that it uses the windows hardware stack that wine does not even try to emulate.

Some dlls are mostly ok to override (like riched20), while others will just crash wine (like user32,gdi)

Also note, a lot of people (including myself) refuse support to people who downloaded/installed programs that did not need to be there. So by using large parts of windows in wine, you're practically forfeiting support from the community.

---

### Post by Jorge M 93 on 2009-06-18
Don't worry for the support, as I said before I just use wine for e-Sword, Flash 8 and 3DFA, apps that work perfectly. When I asked if it was possible to improve wine with some files of my Vista partition I was just *wondering*.

Thank you again.


I think there is nothing interesting else to say in this post, could I mark it as solved or closed?, you have already answered my question.

---

### Post by del_diablo on 2009-06-20
> **Jorge M 93 said:**
> So there is no way to improve wine using files from the win() partition?

Ripping over all the fonts?

---

### Post by zevans on 2009-06-20
Hm. Lots of the Direct3D stuff now works in WINE directly without the MS DLLs, I agree. However, DirectMusic still seems to be a pain without it and often prevents apps from working that otherwise would. 

I can't really find a consistent story on the advice with this... there's very very little about DirectSound at all on WINE Wiki. Any pointers people?

---

### Post by cogadh on 2009-06-21
Actually, DirectSound in the current Wine is considered to be about 85% complete with 5 currently outstanding bugs/to-do items. Maarten Lankhorst's work over the last few years on getting Wine's ALSA support improved has gone a long way to getting it that far, but it does still have a ways to go. As for attempting to improve it, you can try replacing Wine's dsound.dll with a native copy, but I have not heard of that being too successful. Beside's, most of Wine's sound problems on Ubuntu have little to do with Wine's DSound implementation, but rather have much more to do with Ubuntu's use of PulseAudio for the main sound server, which Wine does not support.

---

### Post by NightMKoder on 2009-06-21
Not exactly that pulseaudio isn't supported by wine, but rather, pulseaudio has a pretty high attitude about supporting alsa. According to pulseaudio devs, wine uses "unsafe" areas of alsa, and they refuse to support these (correctly). 

So instead of having real backwards-compatibility with alsa - they only choose to be partially backwards compatible, and say that wine is the problem.

---

### Post by cogadh on 2009-06-21
Gotta love it when OSS devs start doing things like that, i.e. each says it's the other guy's fault.

---

### Post by zevans on 2009-06-22
> **cogadh said:**
> Actually, DirectSound in the current Wine is considered to be about 85% complete with 5 currently outstanding bugs/to-do items. 

So it's "mostly working" and then....

> you can try replacing Wine's dsound.dll with a native copy, but I have not heard of that being too successful. 

... "it doesn't work."

:-)

> Beside's, most of Wine's sound problems on Ubuntu have little to do with Wine's DSound implementation, but rather have much more to do with Ubuntu's use of PulseAudio for the main sound server, which Wine does not support.

I know about that, but some WINE apps are fine for me so there's obviously no fundamental WINE/audio issue. Unless you're saying that DirectMusic is trying to do something in ALSA that PulseAudio is then putting a stop to?

I am indeed going to try overriding dsound.dll and related things, but that's my point: there doesn't seem to be any "offical" advice about it on the Apps DB or the Wiki, and most of the Googling I've done gives me contradictory results.

---

### Post by zevans on 2009-06-22
> **cogadh said:**
> Gotta love it when OSS devs start doing things like that, i.e. each says it's the other guy's fault.

In fairness this happens a LOT in paid-for projects - human nature. The problem with OSS is that there's nowhere to escalate to to get a decision... although I suppose that's what distros do.

Anyway. my WINE appears to be working with Pulseaudio, so maybe that's old news - it's just PES5 and PES6 that seem to have this issue.

---

### Post by NightMKoder on 2009-06-22
Different apps exercise different parts of wine's audio driver. Simple apps - that play sound occasionally, don't use the advanced features that directsound does (ability to map memory into the sound card). That is the part that is "unsafe" and crashes pulseaudio.

---

### Post by cogadh on 2009-06-24
> **zevans said:**
> In fairness this happens a LOT in paid-for projects - human nature. The problem with OSS is that there's nowhere to escalate to to get a decision... although I suppose that's what distros do.

Well, my point was that with OSS stuff, you usually have much more open communication than in the closed source model, where blaming it on the other guy is really the norm. With OSS, I would expect them to actually talk to each other and work out a solution, rather than just (very publicly) say "it's their fault", whether that is actually correct or not.

> **zevans said:**
> 
[QUOTE=cogadh;7494719]Actually, DirectSound in the current Wine is considered to be about 85% complete with 5 currently outstanding bugs/to-do items
So it's "mostly working" and then....

> **cogadh said:**
>  you can try replacing Wine's dsound.dll with a native copy, but I have not heard of that being too successful.

... "it doesn't work."

:-)

I know about that, but some WINE apps are fine for me so there's obviously no fundamental WINE/audio issue. Unless you're saying that DirectMusic is trying to do something in ALSA that PulseAudio is then putting a stop to?

I am indeed going to try overriding dsound.dll and related things, but that's my point: there doesn't seem to be any "offical" advice about it on the Apps DB or the Wiki, and most of the Googling I've done gives me contradictory results.[/QUOTE]
Correct. Wine's built-in DSound mostly works, but from what I've seen, Microsoft's DSound does not (when used with Wine). 

As NightMKoder so succinctly explained, Wine and Pulse can get along fine, right up until DSound tries to do something through Wine that ALSA would normally have no problem with, but Pulse does. That's why the first thing I do with  new Ubuntu install is completely disable everything Pulse and go back to good old ALSA.

---

### Post by zevans on 2009-06-26
> **cogadh said:**
> 
Correct. Wine's built-in DSound mostly works, but from what I've seen, Microsoft's DSound does not (when used with Wine). 

As NightMKoder so succinctly explained, Wine and Pulse can get along fine, right up until DSound tries to do something through Wine that ALSA would normally have no problem with, but Pulse does. That's why the first thing I do with  new Ubuntu install is completely disable everything Pulse and go back to good old ALSA.

Thanks, that's clear now. I should probably go over to WineWiki and try and write a summary of that...

---

