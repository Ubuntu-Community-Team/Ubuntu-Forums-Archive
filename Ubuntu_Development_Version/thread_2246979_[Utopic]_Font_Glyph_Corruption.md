---
title: "[Utopic] Font Glyph Corruption"
date: 2014-10-04
forum: Ubuntu Development Version
---

### Post by g4oblivionyt on 2014-10-04
Hello, I recently installed Ubuntu Gnome 14.10 (daily 2014-10-03) and have been experiencing what seems to be glyph corruption.
I figured it was a bug in mesa and that it would be fixed once I switched to Oibaf's PPA and Linux 3.17rc7 but I'm still experiencing the issue  after updating.

[IMG]http://i2.minus.com/i1Knr5WPpN7Sg.png[/IMG], [IMG]http://i.minus.com/iMQbwML49kCjr.png[/IMG]

Does anyone have any idea what could be causing this outside of mesa and the kernel?

System:
Ubuntu 14.10 (daily 2014-10-03 w/ updates)
Driver: radeonsi
GPU: AMD Radeon HD 7770

Notes:
Issue is present in the LiveCD
I did not have this issue running Linux 3.17rc6 with ~10 day old mesa 10.4 snapshot in 14.04
The corruption isn't always a solid color

---

### Post by tista on 2014-10-05
Hi g4oblivionyt,

Well... I'm not sure, Was it related to this bug?:
[https://bugzilla.kernel.org/show_bug.cgi?id=68571]("https://bugzilla.kernel.org/show_bug.cgi?id=68571")

They said some remained bugs (glitches?) are appeared onto non-GL applications, if so, you'd better to check and append **drm-fix** branch kernel ppa instead of linus's mainline.

Best Regards,
Tista

---

