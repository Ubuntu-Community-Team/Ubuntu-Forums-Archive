---
title: "Why does The GIMP poop little empty files all over the place?"
date: 2008-12-18
forum: Ubuntu Studio
---

### Post by Krovas on 2008-12-18
...and how can I make it stop? Anywhere I open an image, The GIMP dumps three 0-byte files named "Colors-", "Light" and ".gimp-2.3scripts". It's cluttering things up and is just generally annoying. Can anybody help here?

---

### Post by Stochastic on 2008-12-18
I've never experienced the issue you describe, can you give more details of your software setup, like what version of Ubuntu you're running, what version of gimp you have installed (if the 2.3 in the one filename is any indication, then I'd say that's your problem).  Could you post the output of ```
apt-cache policy gimp
```

---

### Post by Krovas on 2008-12-18
```
krovas@thievesguild:~$ apt-cache policy gimp
gimp:
  Installed: 2.4.5-1ubuntu2
  Candidate: 2.4.5-1ubuntu2
  Version table:
 *** 2.4.5-1ubuntu2 0
        500 http://us.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status

```


This has been an issue ever since I've started using Hardy.

---

### Post by Stochastic on 2008-12-18
Try installing the backport version for hardy.
-go into System -> Administration -> Software Sources
-click on the Updates tab, and check the box for hardy-backports
-click close
It should refresh your repository tree as you close it, but you can do it manually if you need.  Then you can either just install the newer GIMP then change your settings back, or install all the backports and leave that setting enabled.

---

### Post by Lison_wang on 2008-12-19
portable crusher plant comes in all shapes and sizes and can be made up of many different kinds of equipment. When it comes to portable and moblie crushing plant, Recycling attachments, aggregate plant and industry grinding mill plant, count on SBM as your single source supplier for equipment.[http://www.portablecrushers.com/http://www.crusher-in-china.com/portable-mobile-crushing-plant/portable_crushing_plant.html](http://www.portablecrushers.com/http://www.crusher-in-china.com/portable-mobile-crushing-plant/portable_crushing_plant.html)

---

