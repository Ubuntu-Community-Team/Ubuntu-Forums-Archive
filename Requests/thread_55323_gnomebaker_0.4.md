---
title: "gnomebaker 0.4"
date: 2005-08-08
forum: Requests
---

### Post by abandoned_hussam on 2005-08-08
Can we backport gnomebaker 0.4? It's already in breezy.
Thanks.

---

### Post by brian g on 2005-08-15
[QUOTE=hussam]Can we backport gnomebaker 0.4? It's already in breezy.
Thanks.[/QUOTE]
any word on this?

---

### Post by infinito on 2005-08-16
[QUOTE=brian g]any word on this?[/QUOTE]
 I've backported this myself, and altought it compiles, gnomebaker keeps segfaulting everytime i try to burn a cd. Don't know if it's library related (maybe gstreamer?) or is about gnomebaker itself.

Anyway, i don't think it would be stable enough for backports. But that's just my opinion...

---

### Post by pulp on 2005-08-16
Hopefully these issues were solved in the 0.4.1 release, which appeared recently

---

### Post by cutOff on 2005-08-16
I've just compiled and packaged the latest version 0.4.1. Seems to work fine and smoothly. Now I only need to host it.

Note 1: Some menu items are in spanish (my locale language). How do I fix this?
Note 2: I followed [this guide](http://women.alioth.debian.org/wiki/index.php/English/PackagingTutorial)  to package it.

Thanks

---

### Post by infinito on 2005-08-16
[QUOTE=cutOff]I've just compiled and packaged the latest version 0.4.1. Seems to work fine and smoothly. Now I only need to host it.

Note 1: Some menu items are in spanish (my locale language). How do I fix this?
Note 2: I followed [this guide](http://women.alioth.debian.org/wiki/index.php/English/PackagingTutorial)  to package it.

Thanks[/QUOTE]
 I've compiled 0.4.1 as well and the issues seem to be solved. But for example, audio cd recording it's sooo slow. Don't know who's to blame (my computer or gnombaker).

About Note 1: Some items are on spanish and others not 'cause the translation seems not to be finished (altought Rosseta template seems to be done...)

---

### Post by cutOff on 2005-08-16
[QUOTE=infinito]I've compiled 0.4.1 as well and the issues seem to be solved. But for example, audio cd recording it's sooo slow. Don't know who's to blame (my computer or gnombaker).

About Note 1: Some items are on spanish and others not 'cause the translation seems not to be finished (altought Rosseta template seems to be done...)[/QUOTE]
Sorry, I've not tried this feature. I'll come back soon.

---

### Post by cutOff on 2005-08-16
well, i've experienced any problems recording CDs (MP3 to CD). Nothing happens. Does anyone else have this problem?

---

### Post by abandoned_hussam on 2005-08-16
[QUOTE=infinito]I've compiled 0.4.1 as well and the issues seem to be solved. But for example, audio cd recording it's sooo slow. Don't know who's to blame (my computer or gnombaker).

About Note 1: Some items are on spanish and others not 'cause the translation seems not to be finished (altought Rosseta template seems to be done...)[/QUOTE]
 Same here, I made a gnomebaker .deb myself using instructions I found on the net ( NOT using checkinstall) and it's running perfectly.`

---

### Post by aledin on 2005-08-18
[QUOTE=infinito]I've compiled 0.4.1 as well and the issues seem to be solved. But for example, audio cd recording it's sooo slow. Don't know who's to blame (my computer or gnombaker). [/QUOTE]

If you mean audio grabbing, the reason for the slowness is that cdda2wav is called with the paranoia library option.
To disable the paranoia option one have to change to sources: edit the file execfunctions.c and comment the line
exec_cmd_add_arg(e, "%s", "-paranoia");
as this
/*      exec_cmd_add_arg(e, "%s", "-paranoia"); */
Recompile and audio cd recording will be faster.

Hope I helped.

---

### Post by infinito on 2005-08-19
[QUOTE=aledin]If you mean audio grabbing, the reason for the slowness is that cdda2wav is called with the paranoia library option.
To disable the paranoia option one have to change to sources: edit the file execfunctions.c and comment the line
exec_cmd_add_arg(e, "%s", "-paranoia");
as this
/*      exec_cmd_add_arg(e, "%s", "-paranoia"); */
Recompile and audio cd recording will be faster.

Hope I helped.[/QUOTE]
 No, is not audio ripping. I was burning some mp3 to audio cd.
Th econversion from mp3 to wav was as fast as usual. The wavs burning to cd was the slow thing.

---

### Post by rwabel on 2005-08-19
so will we have soon a bp of gnomebaker 0.41? Would be great

---

### Post by GizmoQ2k on 2005-08-24
Please port it =)

---

### Post by Nano on 2005-08-24
[QUOTE=cutOff]well, i've experienced any problems recording CDs (MP3 to CD). Nothing happens. Does anyone else have this problem?[/QUOTE]
 You need gstreamer08-lame for that.

---

### Post by UbuWu on 2005-08-29
[QUOTE=Nano]You need gstreamer08-lame for that.[/QUOTE]

I think you mean gstreamer0.8-mad? Lame is for encoding, mad for decoding mp3's.

---

### Post by acascianelli on 2005-08-29
Gnomebaker 0.4.2 is out, any more news on getting this in backports?

---

