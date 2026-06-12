---
title: "gimp multi core"
date: 2009-02-05
forum: Ubuntu Studio
---

### Post by anv on 2009-02-05
I have 4 core processor, while working with Gimp I noticed from task manager that it uses just 25% max from total capacity, though even in preferences there is option to use 4 processors. anyone knows solution to adjust the setting to use all cores?!?

---

### Post by anv on 2009-02-09
hmm it does that same with Blender too 25 - 26 % from processor capacity

according Htop while rendering with Blender (4 threads are enabled):

core 1  0-3%
core 2  0%
core 3  0-5%
core 4  100%

---

### Post by bongobong on 2009-07-26
**Bug 589752 – (Better) Multicore Support for Effects and Scripts**


[http://bugzilla.gnome.org](http://bugzilla.gnome.org)

---

### Post by Labello on 2009-07-26
> **anv said:**
> hmm it does that same with Blender too 25 - 26 % from processor capacity

according Htop while rendering with Blender (4 threads are enabled):

core 1  0-3%
core 2  0%
core 3  0-5%
core 4  100%

There is a setting where you can enable more core in the blender rendersettings. i am pretty shure about that.

---

