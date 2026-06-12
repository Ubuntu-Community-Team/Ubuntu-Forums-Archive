---
title: "In Lucid VLC plugin crashes Firefox"
date: 2010-06-01
forum: Ubuntuzilla
---

### Post by kansasnoob on 2010-06-01
I've not had time to really explore this totally and may not be able to for a while, but I've discovered that "mozilla-plugin-vlc" causes Firefox to crash in Lucid.

And it doesn't matter if it's the Ubuntu version of Firefox or pure Firefox via Ubuntuzilla or even if you do the tar.bz2.

It's fine in Karmic. Substituting mozilla-mplayer works fine.

I have not tried downgrading the VLC packages, nor have I tried even looking for a VLC PPA.

Just thought I'd give you that "heads up"! Oh, and I only run i386 :)

Maybe in a few weeks I'll have time to explore this more closely.

---

### Post by nanotube on 2010-06-02
hey kansasnoob!

thanks for the note. if anyone else comes by with the same, i'll know to tell them it's not ubuntuzilla's fault :)

---

### Post by umuller on 2010-09-01
I seem to have the same issue:
[LIST]
[*]Firefox crashes (or sometimes freezes) whenever navigating back to (or reloading) a page that contains a VLC plugin
[*]The VLC plugin must have played some content on the first page visit for the crash to happen on the second visit to the same page
[*]I'm using UDP multicast displayed by the VLC plugin
[*]VLC V 1.06, Firefox 3.68, Ubuntu 10.04 Workstation 64-bit
[*]Crash: SIGSEGV
[/LIST]

---

