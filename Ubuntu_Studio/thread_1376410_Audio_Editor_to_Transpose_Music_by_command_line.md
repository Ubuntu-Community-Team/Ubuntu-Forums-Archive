---
title: "Audio Editor to Transpose Music by command line"
date: 2010-01-09
forum: Ubuntu Studio
---

### Post by Johann-1.0 on 2010-01-09
Hello friends. I want to know what audio editor allows me to change the pitch (in an easy way) of an audio file but via the command line. I have to do the same changes changes to a lot of files.
The main problem is...Audacity works good for me for one file at a time...I want to do it with lots of files. Audacity deals with pitch in an easy way for me: transpose from do to re, for example, so I could forget about frequencies numbers. I like the same thing, but at command line. May you help me with this?
The audio editing software should also allow me to mix and merge two or more audio files in an only audio file and let me listen to both at a time.
Thanks in advance.

---

### Post by Johann-1.0 on 2010-01-09
If that audio software has the option not only to change the pitch in a "musical way" but change the "tempo"(speed) of the file, it would be excellent for me. Thanks

---

### Post by AutoStatic on 2010-01-09
Hello Johann-1.0, maybe the package **rubberband-cli** provides what you need.

---

### Post by Johann-1.0 on 2010-01-09
> **AutoStatic said:**
> Hello Johann-1.0, maybe the package **rubberband-cli** provides what you need.
Thank you...but when I look for it via "sudo apt-get install rubberband-cli" it says package not found.

---

### Post by Darce on 2010-01-09
You can install it via the Synaptic Package Manager. Version 1.2 is in there.

---

### Post by AutoStatic on 2010-01-09
> **Johann-1.0 said:**
> Thank you...but when I look for it via "sudo apt-get install rubberband-cli" it says package not found.Which version of Ubuntu do you use?

---

### Post by Johann-1.0 on 2010-01-09
I'm using Ubuntu 8.04 LTS. I tried using Synaptic and didn't work.

---

### Post by AutoStatic on 2010-01-09
It's not included in 8.04 as far as I know.
You could install it from a PPA, this one has rubberband-cli for Hardy: [https://launchpad.net/~danmbox/+archive/ppa](https://launchpad.net/~danmbox/+archive/ppa)
Use it at your own risk though and maybe there's a better way to do it with software that is already available for Hardy, like **sox**.

---

### Post by Johann-1.0 on 2010-01-09
Thank you for your help. I've looking for software but couldn't find an easy one to work...if you suggest me one, I will appreciate it a lot. I was looking and find LADSPA plugins...but I need a higher level of knowledge, so I can't use it right now. Audacity doesn't work at command line, at least for the tasks I want. It works the best for one file at a time...but I need to use it for many files.

---

