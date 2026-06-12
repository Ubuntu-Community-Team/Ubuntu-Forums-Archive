---
title: "Qt4 vs. Qt5 : Which applications are still based on Qt4?"
date: 2015-05-03
forum: Ubuntu, Linux and OS Chat
---

### Post by syntaxerror74 on 2015-05-03
This was just plain coincidence. I wanted to check Qt5 version and just because of being a lazy typist myself, I *dpkg -l* 'ed for \*qt\* instead of \*qt5\*.
So I got aware that apart from (obvious) Qt5, even Qt4 was still installed in parallel for some reason.

So does anyone of you guys know which applications still need Qt4? I'm planning to get rid of the v4 release ASAP, because I think it's never a good idea to keep two versions in parallel unless there is an absolute requirement to do so.
The following command already gave some more insight:
[SIZE=2]*(Note for new users: No worries. This command is perfectly safe; it isn't going to wreak **any** havoc on your system, trust me.)*[/SIZE]
```
$ apt-get --simulate remove ^libqt4-\* | tee qt4needed.log
```

AFAICS, from my stuff (that I installed via pre-built packages) only **multimedia**-related applications like amarok, [SIZE=3]**kmix**[/SIZE] [1], ksnapshot, picard, smplayer as well as Ark (archiver, I almost never use this); all the rest do seem to be already migrated to Qt5 here on Vivid (final). However, I might still be wrong at that.

For instance, I'm still wondering why *libtesseract3* and *tesseract-ocr* showed up in my log file as well, as these should be entirely Qt-independent (they're non-GUI applications, to begin with).

[1] Today I've managed to build kmix for KF5/Qt5, with one "downer": to have access to modules like kcm_phonon.so, you might require KDE plasma-desktop installation, which takes no less than half a gigabyte of installation files. You have been warned.

---

### Post by monkeybrain20122 on 2015-05-04
vlc?

---

### Post by syntaxerror74 on 2015-05-05
Yes that can be! Good point. As I don't use VLC player myself, there is no wonder it was not listed.

---

