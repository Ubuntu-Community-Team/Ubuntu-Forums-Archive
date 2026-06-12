---
title: "Gwenview slow in Artful"
date: 2017-10-08
forum: Ubuntu Development Version
---

### Post by adlerhn on 2017-10-08
Since I upgraded to Artful, Gwenview is very slow. It takes many seconds every time I open an image or delete one. It used to work flawlessly in Zesty.

Any idea of what could it be or how could I debug the issue? I've searched bug reports but haven't found anything. Thanks.

---

### Post by Chanath on 2017-10-08
> **adlerhn said:**
> Since I upgraded to Artful, Gwenview is very slow. It takes many seconds every time I open an image or delete one. It used to work flawlessly in Zesty.

Any idea of what could it be or how could I debug the issue? I've searched bug reports but haven't found anything. Thanks.

I never used Kubuntu 17.04, so can't say how it worked there, but I have Kubuntu 17.10 and Gwenview works very fast. Maybe, you try a fresh install?

---

### Post by ajgreeny on 2017-10-08
Just out of interest, why gwenview which is more of a qt/kde application, if you're running the default Ubuntu system?
I am assuming that you must have installed it, preferring it to eog, the default image viewer.

Do you have a similar problem with eog?

---

### Post by adlerhn on 2017-10-08
Yeah, I like gwenview much more than eog, as gwenview can browse folders and show thumbnails of the images in them.

There is no issue with eog.

---

### Post by adlerhn on 2017-10-19
Ok, I just realised that the slowdown happens only when using Wayland. Under Xorg it works flawlessly.

---

### Post by adlerhn on 2017-10-19
I have submitted a bug report: [https://bugs.launchpad.net/ubuntu/+source/gwenview/+bug/1724984](https://bugs.launchpad.net/ubuntu/+source/gwenview/+bug/1724984)

---

### Post by cariboo on 2017-10-20
Closed, as Artful has been released.

---

