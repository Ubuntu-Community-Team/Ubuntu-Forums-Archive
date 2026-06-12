---
title: "Winamp &quot;send to&quot; menu is missing"
date: 2011-03-14
forum: Wine
---

### Post by El Potro on 2011-03-14
Hello folks!

This is a problem that breakes my head in two. 

I installed Winamp v 5.6 on Ubuntu 10.04, Wine v 1.2.2, and although it works ok, the submenu "send-to" doesn't appear. So I can't make file type conversions with Winamp.

I have read here [http://bugs.winehq.org/show_bug.cgi?id=18926](http://bugs.winehq.org/show_bug.cgi?id=18926) that the problem lies in the file comctl32.dll, so I tried copying it from a Windows XP installation, with no luck (Winamp works but not good, and there isn't any send-to menu).

It got only worst when I tried with "winetricks comctl32" because then Wine completely crashed no matter what program I'm trying to open, and I had to delete the .wine folder, and create a new one. Strange, but that is what happens.

Anybody knows anything about this? Any possible solution?

Thank you very much

---

### Post by El Potro on 2011-03-16
bump, please!

---

### Post by Tweak42 on 2011-03-16
> **El Potro said:**
> bump, please!

What feature that you need in Winamp that you can't get from a native linux player?

---

### Post by El Potro on 2011-03-16
Hi, thanks for trying to help

The function is exactly the only one which isn't working. The format converter. I need to convert mp3 or wma files to aac plus v2 with sbr (spectral band replication) which allows me to reduce the file size considerably much (keeping the same audio quality with bitrates as low as 48 kbps). This is something I need to do in a daily basis, and it bothers me so m

uch having to change to windows.

Winamp does this work flawlessly, and even copies the ID3 tags from the original file. So this is the reason.

The strange thing is that winamp works fine under wine, but the option "send to format converter" does not exist. Is completely gone. Why? Is my question.

If this was a compatibility problem, shouldn't at least the send to option show up and just not work?

Thanks!

---

