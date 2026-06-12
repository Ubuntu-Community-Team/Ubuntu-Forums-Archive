---
title: "Editing X264"
date: 2008-09-23
forum: Ubuntu Studio
---

### Post by ginbuntu on 2008-09-23
Hi, what application can I use to edit a .mp4 file encoded with X264+AAC?

I want to split the video in parts. 


thanks in advance

---

### Post by paulmerchant on 2008-09-23
Try Avidemux if you need a GUI.

---

### Post by FakeOutdoorsman on 2008-09-24
[HowTo split/concatenate MP4 files with MP4Box]("http://forum.doom9.org/showthread.php?t=93240")

Lets you do this without the need to re-encode.  MP4Box is part of the **gpac** package in the repository.

---

### Post by paulmerchant on 2008-09-24
> **FakeOutdoorsman said:**
> [HowTo split/concatenate MP4 files with MP4Box]("http://forum.doom9.org/showthread.php?t=93240")

Lets you do this without the need to re-encode.  MP4Box is part of the **gpac** package in the repository.

I just checked out gpac. Wow, there's a lot more than last time I looked at the project. The MP4Box solution would technically be much better. With Avidemux, you would be re-encoding (going down a digital generation).

---

### Post by eye208 on 2008-09-25
> **paulmerchant said:**
> With Avidemux, you would be re-encoding (going down a digital generation).
No.

In smart copy mode, Avidemux will only reencode those frames which lost their reference frames (I-frames) due to a cut. If you cut at I-frame positions only, no reencoding will be done.

See [here](http://www.avidemux.org/admWiki/index.php?title=Cutting#Intra_Frames_and_SmartCopy) for more info.

---

### Post by paulmerchant on 2008-09-25
> **eye208 said:**
> No.

In smart copy mode, Avidemux will only reencode those frames which lost their reference frames (I-frames) due to a cut. If you cut at I-frame positions only, no reencoding will be done.

See [here](http://www.avidemux.org/admWiki/index.php?title=Cutting#Intra_Frames_and_SmartCopy) for more info.

Thanks. That's good to know.

---

