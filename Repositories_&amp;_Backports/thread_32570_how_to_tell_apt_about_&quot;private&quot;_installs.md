---
title: "how to tell apt about &quot;private&quot; installs"
date: 2005-05-08
forum: Repositories &amp; Backports
---

### Post by gratefulfrog on 2005-05-08
(previously posted by at thread 163326, wrong forum.. sorry)

I am doing a lot of compiling and installing software that is not available at the Ubuntu repositories, or if it is available, the version offered is defective or out of date.

Can anyone tell me how to inform apt of these installations so that it doesn't overwrite my versions with packages that it installs as dependencies?

An example of this is **ffmpeg**. The Ubuntu version is out of date and defective on my AMD64 platform. I unistalled the Ubuntu package, then downloaded the current cvs snapshot, built and installed it for my platform. It works perfectly! But, now, apt (synaptic) won't let me install software that depends on ffmpeg! so I am stuck!

 :???:

---

### Post by dewey on 2005-05-08
Try packaging it into a .deb file, 
```
$sudo alien -d <packagenamehere>.tar.gz
```
and installing it using
```
$sudo dpkg -i <packagenamehere>.deb
```
That should allow dpkg and apt to realize it's installed.

---

### Post by crane on 2005-05-08
[QUOTE=dewey]
That should allow dpkg and apt to realize it's installed.[/QUOTE]

I installed wine and wine tools from a .deb file. Now every time I update I get a message stating that those to packages can't be updated.

---

### Post by jodef on 2005-05-08
[QUOTE=crane]I installed wine and wine tools from a .deb file. Now every time I update I get a message stating that those to packages can't be updated.[/QUOTE]That seems to be an unfortunate side effect of going that route I installed Mplayer using a deb package and get the same message from synaptic.

---

