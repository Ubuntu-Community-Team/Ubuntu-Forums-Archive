---
title: "Ubuntu TuneUp"
date: 2009-07-15
forum: Tips &amp; Tutorials Team
---

### Post by Frantique on 2009-07-15
Hello all!
I just released  a small post install script for Ubuntu systems.
Here is the description:

**Ubuntu TuneUp** - v. 0.0.1
Coded by: *Frantique* (undernetangel@gmail.com)
*A small Bash script to make quick tuneup on a freshly installed Ubuntu system.*
---
**Usage:** sudo tuneup.sh OPTION
**Options:**
**-c **: By default sets concurrency to shell.
**-s** : Set swappiness to lower value. (Use it just if you have more than 1Gb of RAM)
**-g** : Install some extra packages like Flash plugin, extra fonts, Java, tweak-ubuntu, etc.
**-f** : Tune up Flash video playback. (Just if GPU can be used.)
**-a** : Execute all above.
**-h** : This help screen.
**-v** : Display version.

**How to install:**
1. Download from [http://artinvoice.hu/tuneup.tar.gz](http://artinvoice.hu/tuneup.tar.gz)
2. Unpack with: tar xvzf tuneup.tar.gz 
3. Start a Terminal and go to tuneup/ directory
4. Run the command: sudo ./tuneup.sh -a

Enjoy!

---

### Post by frodon on 2009-07-16
Do we still approve post install scripts ?

---

