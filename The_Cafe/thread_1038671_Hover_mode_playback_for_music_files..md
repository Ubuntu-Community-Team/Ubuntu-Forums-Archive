---
title: "Hover mode playback for music files."
date: 2009-01-13
forum: The Cafe
---

### Post by ww711 on 2009-01-13
I accidentally found this feature.... with GNOME+Nautilus+Rhythmbox.

If you hover your cursor over a audio file, a musical note icon appears, when you move the cursor over that icon, it plays back the audio file. No need to load a music playback application.

I think it's quite a smart function and wanted to share.

---

### Post by hansdown on 2009-01-13
Hi ww711.

My friends love that feature.

---

### Post by chris4585 on 2009-01-13
you don't need Rhythmbox, it uses gstreamer I believe

---

### Post by zmjjmz on 2009-01-13
> **chris4585 said:**
> you don't need Rhythmbox, it uses gstreamer I believe

mpg123

---

### Post by mc4100 on 2009-01-13
> **zmjjmz said:**
> mpg123

Nope; it's gstreamer.
I **know** that it (Nautilus) had previously used mpg123 (or 321? who knows), but I just tried removing them now, and it still works ... therefore, gstreamer.

Edit: .ogg works too, but vorbis tools isn't installed either, meh, I'm pretty sure it's switched to gstreamer ::goes to find bug report/blog entry::

Edit, again;
> Sebastien Bacher  wrote on 2008-02-04:
That is fixed in hardy now which use gstreamer. 
(This was an older bug report, #167946)
... but [this one]("http://bugzilla.gnome.org/show_bug.cgi?id=486827") explains it.

---

### Post by BGFG on 2009-01-13
i too, discovered that by accident. Nice way to quick preview a song without going through the whole software launch...:)

---

### Post by zmjjmz on 2009-01-13
> **mc4100 said:**
> Nope; it's gstreamer.
I **know** that it (Nautilus) had previously used mpg123 (or 321? who knows), but I just tried removing them now, and it still works ... therefore, gstreamer.

Edit: .ogg works too, but vorbis tools isn't installed either, meh, I'm pretty sure it's switched to gstreamer ::goes to find bug report/blog entry::

Edit, again;

(This was an older bug report, #167946)
... but [this one]("http://bugzilla.gnome.org/show_bug.cgi?id=486827") explains it.

Oh, ok. I heard it used mpg123 last time it was discussed.

---

### Post by ww711 on 2009-01-14
Has anyone discovered new/existing features/functionality like or similar to this in gnome?

---

### Post by DocForbin on 2009-03-15
Anyone know how to disable this feature (outside of uninstalling gstreamer)?

---

### Post by Sealbhach on 2009-03-15
> **DocForbin said:**
> Anyone know how to disable this feature (outside of uninstalling gstreamer)?

It used to be that you disable the preview feature in Nautilus Preferences. See if that works.


.

---

### Post by DocForbin on 2009-03-15
> **Sealbhach said:**
> It used to be that you disable the preview feature in Nautilus Preferences. See if that works.
.
Cool, found it, that worked. Thanks.

---

