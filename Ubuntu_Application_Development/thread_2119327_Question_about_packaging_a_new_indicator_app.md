---
title: "Question about packaging a new indicator app"
date: 2013-02-23
forum: Ubuntu Application Development
---

### Post by yktoo on 2013-02-23
Hi all,


Newbie here.

I've created a new Ubuntu indicator application (sound switcher), and want to make a package/PPA available for it.

Now I'm a bit lost. I've read [**Packaging New Software**]("http://developer.ubuntu.com/packaging/html/packaging-new-software.html"), but that starts right with a proper source tarball--which I don't have yet.

My app is a Python program, and it requires an extra library (PulseAudio bindings). Could you point me out a good description of how I can best package:
[LIST=1]
[*]The Python application file
[*]Application icon
[*]Required lib_pulseaudio file
[/LIST]

Thx. Dmitry

---

### Post by Frogs Hair on 2013-02-25
If want to compress the contents of a folder right click and select compress and there is a package type menu which appears in the dialog box. I'm not sure if that is what you are looking for though.

---

### Post by yktoo on 2013-02-28
Thank you Frogs Hair, but what I meant was actually making a .deb package from a Python app. The same thing that is asked [here]("http://stackoverflow.com/questions/2927615/easy-straightforward-way-to-package-a-python-program-for-debian") (but unfortunately still not comprehensively replied).

---

