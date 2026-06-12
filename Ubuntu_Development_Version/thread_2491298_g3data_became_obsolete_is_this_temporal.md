---
title: "g3data became obsolete: is this temporal?"
date: 2023-10-03
forum: Ubuntu Development Version
---

### Post by Claus7 on 2023-10-03
Hello,

today I checked g3data under synaptic and found out that it appeared under obsolete packages. I checked its development and saw (if not mistaken) that it stopped ~ 5 years ago, without this affecting its availability all these years. Does this mean that we are not expecting g3data in future versions of ubuntu?

Regards!

---

### Post by IanW on 2023-10-04
From the github page, it looks like it's been abandoned.
[https://github.com/pn2200/g3data](https://github.com/pn2200/g3data)

---

### Post by Claus7 on 2023-10-04
Hello,

> **IanW said:**
> From the github page, it looks like it's been abandoned.
[https://github.com/pn2200/g3data](https://github.com/pn2200/g3data)

it's a pity. A very nice and useful application. If I recall correctly, a long time ago, ubuntu forum members proposed it to me and I never looked back. 

Regards!

---

### Post by ian-weisser on 2023-10-04
See [https://tracker.debian.org/pkg/g3data](https://tracker.debian.org/pkg/g3data)
and [https://ftp-master.debian.org/removals.txt](https://ftp-master.debian.org/removals.txt)

Package was removed from Debian on 26-09-2023 due to dead upstream. Therefore it won't sync to future releases of Ubuntu.

Of course, any community member willing to do the work can fork it, resurrect it, and resubmit it to Debian (and thence to Ubuntu).

---

### Post by Claus7 on 2023-10-08
Hello,

thank you for your responses. In the meantime I was trying to check some alternatives and I came across Engauge Digitizer. I installed it via synaptic and I'm using it with the following steps:
1) File->Import (advanced) and opening an image of choice.
2) I'm accepting the options from the coordinate system that pops up.
3) Next, when a guide appears, I just press cancel, because I want the original image to remain intact and not converted in black and white.
4) Pressing the axis point tool on top, and going back to image, I can click where I want in order to submit the first coordinates: e.g. 0,0.
5) I'm going on the right for submitting a second point, so as to define axis x.
6) I'm going now on top of the first point to submit the third point and define axis y.
7) Now wherever I'm pointing the mouse, I will see on the bottom of the screen the coordinates of my mouse based on the actions of the previous steps.
8) Clicking point match tool on top, I can click on any point on graph/image and I can see both its coordinates and a + that is printed on the image.
9) During the whole process I can minimize/maximize the image using the mouse wheel (sth that was not available with g3data).
10) Exporting image with added points can be done by using the screenshot tool.

Regards!

PS1: The only drawback compared to g3data that I have noticed is that it is taking some time in order to pinpoint the points on graph.

@ian-weisser: Not a bad idea for undertaking such a task. If in the future I have the time I might look at it. I'm completely noob on that process and some rough thoughts: this program lasted >5 years since it was started to become obsolete. So it might not be so difficult. On the other hand it should get converted to gtk4, which is latin/greek/chinese to me (depending on where you are coming from).

---

### Post by Claus7 on 2024-01-05
Hello,

testing noble I can see that g3data belongs to the obsolete packages, yet it is still there! Using it today it worked as it used to and even better I should say. I hope that it will remain available, even if it appears as obsolete, since mantic days.

Regards!

---

### Post by Claus7 on 2024-07-10
Hello,

in a fresh ubuntu noble installation though, the package is not available under synaptic package manager. I was able to find it and install it from here:
[https://launchpad.net/ubuntu/jammy/amd64/g3data/1:1.5.3-3build1](https://launchpad.net/ubuntu/jammy/amd64/g3data/1:1.5.3-3build1)

Regards!

---

