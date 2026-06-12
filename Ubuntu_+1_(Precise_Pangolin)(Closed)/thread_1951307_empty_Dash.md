---
title: "empty Dash"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by whinis on 2012-04-02
After upgrading to 12.04 my ubuntu install has become unusable since the dash is empty. no matter what tab I search or what I search, all return no results. attached is a screenshot of what should be a valid search.

---

### Post by cariboo on 2012-04-02
DO you get anything when you click any of the other lenses (the small icons at the bottom of the dash)?

---

### Post by whinis on 2012-04-02
The only lens that shows anything is the video lens and only 3 online videos.

---

### Post by philinux on 2012-04-02
> **whinis said:**
> The only lens that shows anything is the video lens and only 3 online videos.

I would open a terminal ctrl alt t and use :

unity --reset

---

### Post by whinis on 2012-04-02
I have tried unity reset as at first the system would freeze after login and tty6 said something about the usb 3.0 driver( name fails me) however for whatever reason unity --reset fixed that. I also tried untiy --replace for when it failed as well as apt-get reinstall (unity stuff). The problem presist in the 3 kernels I run (11.10 kernel, 12.04 kernel, and a custom kernel 3.0.0) although I have not tried unity 2d.

---

### Post by jbicha on 2012-04-02
Do you have [zeitgeist]("http://pad.lv/964146") installed? It's of course installed by default, but you might have done an incorrect dist-upgrade to remove it.

---

### Post by whinis on 2012-04-02
> **jbicha said:**
> Do you have [zeitgeist]("http://pad.lv/964146") installed? It's of course installed by default, but you might have done an incorrect dist-upgrade to remove it.
It was installed however doing the first thing in the bug report 

```
mv ~/.local/share/zeitgeist ~/.local/share/zeitgeist.bak
 kill -s TERM `pidof /usr/lib/unity-lens-applications/unity-applications-daemon`

```fixed my issue, apparently its a corrupted database.

if it will not harm anything maybe in the update process it could delete the current database to prevent problems.

---

