---
title: "libcairo1_0.3.0-1_i386.deb"
date: 2005-06-11
forum: Ubuntu Backports
---

### Post by compmodder26 on 2005-06-11
This package has to be installed for a successfull upgrade of firefox.  Unfortunately it won't install due to a MD5 checksum mismatch.  So now I can't upgrade firefox.  Anybody else getting this problem?

---

### Post by nevets on 2005-06-11
[QUOTE=compmodder26]This package has to be installed for a successfull upgrade of firefox.  Unfortunately it won't install due to a MD5 checksum mismatch.  So now I can't upgrade firefox.  Anybody else getting this problem?[/QUOTE]

Yes, I found this problem this morning when I tried to upgrade to 1.04. Now I do not have new or old version of Firefox. I hope someone here knows the fix.

---

### Post by kerinin on 2005-06-11
i'm so glad i'm not the only one having this problem - it started for me last night before anyone had posted.

i'm still trying to figure it out - no luck so far.  the really annoying thing is that this all started because i wanted to install an extension for firefox, but when you go to the extensions page in mozilla.org they won't let you see any until you've updated to the latest firefox.  there's apparently some bug about how the ubuntu package version number isn't correct.  

elsewhere i've seen people suggest waiting a while and then doing an apt-get update when they got MD5Sum mismatches on other packages.  it seems to happen when the maintainer is changing the file in the repository and the changes have updated yet.  of course, this has been going on for at least 12 hours now.

---

### Post by kerinin on 2005-06-11
oh, one other thing that might help someone who knows more about this than myself:

the version needed for firefox is 0.3.0-1, but the current [debian package](http://packages.debian.org/testing/libs/libcairo1)  version number is 0.4.0-1

---

### Post by jdong on 2005-06-11
```


jdong@ubp-fortress:~$ apt-cache show libcairo1
Package: libcairo1
Priority: optional
Section: libs
Installed-Size: 268
Maintainer: Dave Beckett <dajobe@debian.org>
Architecture: i386
Source: libcairo
Version: 0.3.0-1
Replaces: libcairo0
Depends: libc6 (>= 2.3.2.ds1-4), libfontconfig1 (>= 2.2.1), libfreetype6 (>= 2.1.5-1), libpixman1 (>= 0.1.3), libpng12-0 (>= 1.2.8rel), libx11-6 | xlibs (>> 4.1.0), libxrender1, zlib1g (>= 1:1.2.1)
**Filename: pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb**
Size: 121090
MD5sum: 14d3ce46a1fc2d96e60af38c3ff3e19c
Description: Multi-platform 2D graphics library
 Provides anti-aliased vector-based rendering for X. Paths consist
 of line segments and cubic splines and can be rendered at any width
 with various join and cap styles. All colors may be specified with
 optional translucence (opacity/alpha) and combined using the extended
 Porter/Duff compositing algebra as found in the X Render Extension.
 .
 Cairo exports a stateful rendering API similar in spirit to the path
 construction, text, and painting operators of PostScript, (with the
 significant addition of translucence in the imaging model). When
 complete, the API is intended to support the complete imaging model of
 PDF 1.4.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

This is an official Ubuntu package, so I have no clue why the checksum isn't matching. It's not my problem though; it's Ubuntu's.

---

### Post by Xian on 2005-06-11
[QUOTE=jdong]This is an official Ubuntu package, so I have no clue why the checksum isn't matching. It's not my problem though; it's Ubuntu's.[/QUOTE]
It's probably on the us.archive mirror which has been squirrelly this weekend.
Best to switch to the archive.ubuntu.com server till a better sync.

---

### Post by kerinin on 2005-06-11
that fixed it for me, thanks!

>sudo gedit /etc/apt/sources.list
>remove 'us.' from all repositories
>sudo apt-get clean
>sudo apt-get update
>sudo apt-get install libcairo1

---

### Post by Rob2687 on 2005-06-12
Same problem with the ca.archive :/

---

### Post by Seth on 2005-06-12
[QUOTE=Rob2687]Same problem with the ca.archive :/[/QUOTE]
 ca and us archives are the same machine.

---

### Post by barryww on 2005-07-10
[QUOTE=kerinin]that fixed it for me, thanks!

>sudo gedit /etc/apt/sources.list
>remove 'us.' from all repositories
>sudo apt-get clean
>sudo apt-get update
>sudo apt-get install libcairo1[/QUOTE]
 And me as well.  Solved the libcairo error.

---

