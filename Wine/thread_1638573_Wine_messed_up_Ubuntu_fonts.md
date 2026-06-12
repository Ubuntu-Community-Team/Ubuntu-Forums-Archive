---
title: "Wine messed up Ubuntu fonts"
date: 2010-12-05
forum: Wine
---

### Post by init1 on 2010-12-05
After installing Wine today, I noticed that the text in Firefox looked...different. The font doesn't look bad, but it's different, and it's bothering me. I've attached 2 screen shots of the same web page: The first was loaded before installing Wine, and the second was loaded after installing Wine. Is there any way to restore the fonts to the way they were?

---

### Post by RoflHaxBbq on 2010-12-06
Wine is a user level application, so I doubt that it can permanently mess up your fonts.

Try opening Firefox and pressing Tools>Options>Content, And then look for "Font And Colors". In Windows mine is set to Times New Roman, size 16.
Check Yours.

Also try resetting Firefox settings to default, or maybe even reinstalling Firefox altogether. But don't do that until you get some more feedback, as I'm still a bit nooby with Linux.

And I presume this problem only happens in Firefox and not everywhere in your GNOME GUI, in which case you have a big problem.

---

### Post by init1 on 2010-12-06
> **RoflHaxBbq said:**
> Wine is a user level application, so I doubt that it can permanently mess up your fonts.

Try opening Firefox and pressing Tools>Options>Content, And then look for "Font And Colors". In Windows mine is set to Times New Roman, size 16.
Check Yours.

Also try resetting Firefox settings to default, or maybe even reinstalling Firefox altogether. But don't do that until you get some more feedback, as I'm still a bit nooby with Linux.

And I presume this problem only happens in Firefox and not everywhere in your GNOME GUI, in which case you have a big problem.
I know Wine couldn't have changed my fonts or my settings, but the installation of Wine through apt could have. During the installation, apt installed several Windows fonts. Perhaps the font I'm used to in Ubuntu got replaced by a Windows font or perhaps a font settings was changed.
Also, my font in Firefox is serif size 16, which I think is the default in Ubuntu.

---

### Post by yarozar on 2011-02-28
I have the vere same problem in Chromium browser. Browser's setting were not changed. It looks like Wine installation overwrites some of Ubuntu's fonts with its own version.

---

### Post by neur0 on 2012-03-07
Same problem here on a Fedora installation.

EDIT: Solved with moving/deleting/replacing/renaming the "wine-tahoma-fonts"

---

