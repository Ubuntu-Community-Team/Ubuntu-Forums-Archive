---
title: "popup when you press the printscreen button"
date: 2014-03-11
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2014-03-11
One recent change to Trusty that I am very, very grateful for is the popup when you press the printscreen button. It asks if you want to save the screenie.

Before I would accidentally hit that button several times a day because it is very close to the backspace button on my keyboard.
I would wind up with a bunch of unwanted screenies in my downloads folder that I would then have to cull.

Pretty sure I am not the only one that likes this change. :P

---

### Post by zika on 2014-03-11
> **Cavsfan said:**
> One recent change to Trusty that I am very, very grateful for is the popup when you press the printscreen button. It asks if you want to save the screenie.

Before I would accidentally hit that button several times a day because it is very close to the backspace button on my keyboard.
I would wind up with a bunch of unwanted screenies in my downloads folder that I would then have to cull.

Pretty sure I am not the only one that likes this change. :PIs that new? I've had it for quite some time but I do not know if that is from some ppa or mainline...

---

### Post by Cavsfan on 2014-03-11
> **Cavsfan said:**
> One recent change to Trusty that I am very, very grateful for is the popup when you press the printscreen button. It asks if you want to save the screenie.

Before I would accidentally hit that button several times a day because it is very close to the backspace button on my keyboard.
I would wind up with a bunch of unwanted screenies in my downloads folder that I would then have to cull.

Pretty sure I am not the only one that likes this change. :P

> **zika said:**
> Is that new? I've had it for quite some time but I do not know if that is from some ppa or mainline...

I just got it in an update within the last few days or it could have came on the ISO I recently installed. My previous install was January 9th I believe.
But yes I just noticed it on my system in the past few days.

---

### Post by zika on 2014-03-11
> **Cavsfan said:**
> I just got it in an update within the last few days or it could have came on the ISO I recently installed. My previous install was January 9th I believe.
But yes I just noticed it on my system in the past few days.I meant further in last year...

---

### Post by Cavsfan on 2014-03-12
> **zika said:**
> I meant further in last year...

Definitely not here. I have had to clean up the screenshots taken when accidentally touching the key beside backspace forever it seems.
I would bump that key and hear a sound like a flashbulb going off knowing I had another one in my downloads folder. There was never before a popup asking if I wanted to save it.
I like it is happening now though for sure.

---

### Post by zika on 2014-03-12
Two scenarios comes to my mind:
1. I'm remembering wrongly (would not be the first time to happen)...
2. There is a switch that either me (turned it on) or You (turned it off) hit at random and now it is back to (possibly new) default with upgrade... ;) I'll investigate that scenario once i get some spare time for that... ;)
I'm sorry for all this off-topic provoked by me ;)
Update&#8321;:```
$ gnome-screenshot --interactive
```is the answer... I might have used this all the time, I'll investigate further...

---

### Post by mc4man on 2014-03-12
Last I checked which was some time ago Gnome didn't offer interactive on PrtSc, so maybe the 'new' behavior' in flashback is from the recent switch in gnome-panel as mentioned in other thread - 
> gnome-panel (1:3.8.0-1ubuntu9) trusty; urgency=low

  * Revert changes to 41_classic_layout.patch introduced in -1ubuntu4,
    this causes two keyboard indicators to be visible.
  * Identify as Unity, again (LP: #1224217).
  * Use unity-settings-daemon instead of gnome-settings-daemon.
  * Add gnome-flashback-services.desktop to autostart indicators.
  * Bump Standards-Version to 3.9.5, no changes needed.

 -- Dmitry Shachnev <mitya57@ubuntu.com>  Sat, 01 Mar 2014 14:39:38 +0400

---

### Post by Cavsfan on 2014-03-12
> **zika said:**
> Two scenarios comes to my mind:
1. I'm remembering wrongly (would not be the first time to happen)...
2. There is a switch that either me (turned it on) or You (turned it off) hit at random and now it is back to (possibly new) default with upgrade... ;) I'll investigate that scenario once i get some spare time for that... ;)
I'm sorry for all this off-topic provoked by me ;)
Update&#8321;:```
$ gnome-screenshot --interactive
```is the answer... I might have used this all the time, I'll investigate further...

I know I didn't do anything to change the behavior.

> **mc4man said:**
> Last I checked which was some time ago Gnome didn't offer interactive on PrtSc, so maybe the 'new' behavior' in flashback is from the recent switch in gnome-panel as mentioned in other thread -

```
[COLOR=#000000]*gnome-panel (1:3.8.0-1ubuntu9) trusty; urgency=low*[/COLOR]

[COLOR=#000000]** Revert changes to 41_classic_layout.patch introduced in -1ubuntu4,*[/COLOR]
[COLOR=#000000]*this causes two keyboard indicators to be visible.*[/COLOR]
[COLOR=#000000]** Identify as Unity, again (LP: #1224217).*[/COLOR]
[COLOR=#000000]** Use unity-settings-daemon instead of gnome-settings-daemon.*[/COLOR]
[COLOR=#000000]** Add gnome-flashback-services.desktop to autostart indicators.*[/COLOR]
[COLOR=#000000]** Bump Standards-Version to 3.9.5, no changes needed.*[/COLOR]

[COLOR=#000000]*-- Dmitry Shachnev <mitya57@ubuntu.com> Sat, 01 Mar 2014 14:39:38 +0400*[/COLOR]
```


Now that makes sense as it seems that is about when it occurred.

---

