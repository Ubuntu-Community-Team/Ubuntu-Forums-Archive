---
title: "Gimp 2.2.x, Easytag 1.x (gtk 2.x?), Liferea"
date: 2005-01-05
forum: Ubuntu Backports
---

### Post by thepoch on 2005-01-05
Any possibilities on backporting Gimp 2.2.x, Easytag 1.x (compiled for gtk 2.x, with smooth fonts, etc.), and maybe the latest Liferea (liferea-gtkhtml and liferea-mozilla)?

I have no idea how complicated it will all be of course. But it would be highly appreciated! =)

dex

---

### Post by arakno on 2005-01-05
Hi!

Just in case you're in a rush for an EasyTAG package, it's very easy to do one yourself using the latest source package.

I just untarred it and did something like:

cd [your easy tag source code dir. here]
chmod+x debian/rules
fakeroot debian/rules binary

You may also need to edit some files inside debian/ to update the version number but I'm not sure (my current package is using an older version number :P).

By the way, my first contact with EasyTAG was last weekend and it ROCKS!

Now I even consider it better then id3tag-it for Windows, which used to be my favorite mp3 tagger.

---

### Post by jdong on 2005-01-05
Gimp accepted. Evaluating Easytag and others.

---

### Post by jdong on 2005-01-05
Building GIMP right now. NOTE: I was unable to satisfy the requirement of Python-dev 2.4 (Warty has 2.3.4). Forcing an override because: 

[http://www.gentoo.org/cgi-bin/viewcvs.cgi/media-gfx/gimp/gimp-2.2.0.ebuild?rev=HEAD&content-type=text/vnd.viewcvs-markup](http://www.gentoo.org/cgi-bin/viewcvs.cgi/media-gfx/gimp/gimp-2.2.0.ebuild?rev=HEAD&content-type=text/vnd.viewcvs-markup)

Gentoo says we only need 2.2. ./configure doesn't complain, which further supports that we don't really need 2.4.

---

