---
title: "inkscape 0.46-devel"
date: 2009-03-13
forum: Ubuntu Studio
---

### Post by djallalnamri on 2009-03-13
*hello
*i have installed inkscape 0.46-devel on ubuntu 8.04 recently it works well except that when i use the pencil tool,inkscape "says" in french:inkscape had undergone internal error and is going to shut down now
*any idea
*thanks in advance

---

### Post by Ascenti0n on 2009-03-13
It is a development version, not a stable one, bugs are par for the course.

I think Inkscape have had the 0.46 in development for almost a year. Their site suggests development has slowed down dramatically or even halted. The head dev is looking for donations to continue the project.

My suggestion is to remove 0.46, install 0.45 or install the KDE's app.

---

### Post by Roanoke on 2009-03-13
Do 
```

sudo apt-get install inkscape

```
in a terminal for the latest stable.
It would be a shame if inkscape development halted, as it's the de facto vector editor of linux. Where did you see that it's development stopped?

---

### Post by Ascenti0n on 2009-03-13
I went on their site today as it happens. The project dev is organising a developers graphics meeting, so the project is not completely dead.

In fact they have just released the 0.46, which as I said was in devel for almost a year.

I like inkscape and I hope it gets more support and momentum.

---

### Post by Ascenti0n on 2009-03-13
just remembered, to the OP - I think the Ubuntu repos have 0.45, you might want to download the 0.46 full public release direct from the inkscape website.

---

### Post by kayosiii on 2009-03-13
0.47 is the current dev version. [http://wiki.inkscape.org/wiki/index.php/ReleaseNotes047](http://wiki.inkscape.org/wiki/index.php/ReleaseNotes047) will give you some idea of what is comming in the next version.

---

### Post by Guruji on 2009-03-14
@AscentiOne
Inkscape is not dead.. and has not halted at all, huge improvements have been done, don't think that because 0.47 has not been released yet that the development is slow or halted, have a look at [http://inkscape.svn.sourceforge.net/viewvc/](http://inkscape.svn.sourceforge.net/viewvc/) you'll see that improvements and bug fixes are made every day.

to install the development version aka 0.46+devel (that will be 0.47), you can download nightly builds from:
[https://launchpad.net/~inkscape-nightly/+archive/ppa](https://launchpad.net/~inkscape-nightly/+archive/ppa)

you can also compile yourself the last bleeding edge, it's quite easy, it's just a matter of copy pasting in the terminal from the instructions you get here (Compiling unstable developement version):
[http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu](http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu)

if you have questions regarding the use of inkscape check here:
[https://answers.launchpad.net/inkscape](https://answers.launchpad.net/inkscape)

to report bugs here:
[https://bugs.launchpad.net/inkscape](https://bugs.launchpad.net/inkscape)

---

### Post by djallalnamri on 2009-03-14
*hello
*the solution was given to me by someone at linux graphics users group:
 if someone ever has the same problem solution is to go inside inkscape folder after having made hidden folders "visible" and add this "~" at the end of "preferences.xml" to rename it this way "preferences.xml~" and the problem is solved
*thanks again

---

