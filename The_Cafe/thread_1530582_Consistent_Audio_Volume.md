---
title: "Consistent Audio Volume"
date: 2010-07-13
forum: The Cafe
---

### Post by Shibblet on 2010-07-13
I have a lot of FLAC files on my computer.  All from CD's that I have converted.

Here's my goofy little problem.  The volume from file to file is inconsistent.  The volume is consistent with the tracks on the CD.  But when you set Audacious to shuffle, I am constantly turning up the volume, and then turning it down again.

Is there anything out there that can keep the volume level consistent between files?

---

### Post by Npl on 2010-07-13
its called "replaygain". No idea if Audacious supports it.

---

### Post by Redo on 2010-07-13
Replaygain is exactly what you want. It reads the average volume of each track, then adds a tag to tell the player how much to boost or reduce the volume of the song to reach 89db average. This means it's a nondestructive process, only adding a tag to the metadata (can do both on a track per track basis and album per album basis)

I use foobar2000 through WINE. You can add your entire library to the playlist, then highlight all tracks and have it analyze each track and apply replaygain info to the music. Then foobar lets you playback with the replaygain applied on an album per album basis, or on a track per track basis (which is the one you'd want).

I'm not sure about the native linux players, while there are some fairly decent ones, none of them ever came close to satisfying my desires for a real foobar2000 clone. Luckily it runs just fine in WINE (visualizations are a bit choppy, otherwise no issues)

---

