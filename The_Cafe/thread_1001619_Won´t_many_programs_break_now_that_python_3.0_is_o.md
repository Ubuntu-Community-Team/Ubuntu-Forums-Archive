---
title: "Won´t many programs break now that python 3.0 is out??"
date: 2008-12-04
forum: The Cafe
---

### Post by eragon100 on 2008-12-04
Since Python is such a popular language for open-source projects, I wonder a bit about the breakage between python 2.x and python 3.0

Can ubuntu ship with multiple versions of python at the same time?

If it can not, this will mean we will have to choose which programs we want to break. If we ship with 3.0, a lot of popular apps, such as the battle for wesnoth for example, will certainly break. However, if we ship 2.x with Jaunty, everything will keep working for now, but any new programs won´t work.

In short, is there a way to have 2 python installs, one 2.6 and one 3.0, on the same system and automatically link a given program to the version that that program needs to run? If not, which version should we ship??

I really would *not* accept it if the battle for wesnoth wouldn´t on Jaunty because of this, nor if I would have to compile python 3.0 from source. (compiling python is easy, however tons of programs break).

---

### Post by crypto178 on 2008-12-04
AFAIK this is not a problem, there can be multiple versions of python on a same system.

---

### Post by gabril on 2008-12-04
Yeah got to love python! Dont worry, transmission will go smooth! As long as you use apt... there will be no dependency problems EVER!

---

### Post by SeanHodges on 2008-12-04
> **gabril said:**
> Yeah got to love python! Dont worry, transmission will go smooth! As long as you use apt... there will be no dependency problems EVER!

I love the optimism, but can't say I share your confidence here... Apt isn't the magic pixie dust that makes dependency problems go away, it just makes them consistent :)

eragon100, download a copy of Jaunty beta and help test Battle of Wesnoth... Testers are the cornerstone for making sure this sort of thing doesn't happen.

As far as running 2 versions of Python concurrently: I can't see why 2 versions can't be made available in the repositories, if there was a good reason to do so, but providing them both on the disc would be tricky at best - anything new that goes on the live CD must replace something else of lesser value to everyone.

---

### Post by .Maleficus. on 2008-12-04
The Python devs also have a little utility called 2to3, which will take 2.x released programs and convert them to be 3.0 compatible.  I haven't tried it and don't know how much it will help, but the syntax changes aren't too huge IIRC so the places that 2to3 doesn't (or can't) change shouldn't be too hard to port.

Info: [http://docs.python.org/library/2to3.html](http://docs.python.org/library/2to3.html)

---

### Post by eragon100 on 2008-12-04
> **SeanHodges said:**
> I love the optimism, but can't say I share your confidence here... Apt isn't the magic pixie dust that makes dependency problems go away, it just makes them consistent :)

eragon100, download a copy of Jaunty beta and help test Battle of Wesnoth... Testers are the cornerstone for making sure this sort of thing doesn't happen.

As far as running 2 versions of Python concurrently: I can't see why 2 versions can't be made available in the repositories, if there was a good reason to do so, but providing them both on the disc would be tricky at best - anything new that goes on the live CD must replace something else of lesser value to everyone.

Testing is impossible right now, since jaunty alpha 1 doesn't ship with python 3.0

---

### Post by jdong on 2008-12-04
We will ship both python2.5 and python 3 for some time, probably well into jaunty+1 days. They install in independent locations and the default system Python will likely remain a 2.5 variant.

---

### Post by wmcbrine on 2008-12-04
> **jdong said:**
> the default system Python will likely remain a 2.5 variant.Not 2.6?

---

### Post by ssam on 2008-12-04
ubuntu has had multiple python version concurrently in the past (i think you can probably still install 2.4).

if you check now i think you will see that /usr/bin/python is a symlink to /usr/bin/python2.5. I expect there will be a /usr/bin/python30 if you install python3. I'd expect a smooth slow transition.

it will be a while before all the libraries are ported, eg pygtk.

---

### Post by wmcbrine on 2008-12-04
I have 2.4.5, 2.5.2, and 3.0rc1+ installed, all from the repos. "python" starts 2.5.2; "python2.4" or "python3" (or "python3.0") work for the others.

Unfortunately 2.6 didn't make it into the Intrepid repos. I sure hope it is/will be in Jaunty. 2.6 is vital to the transition effort.

Python 3.0rc1+ is in Universe, and is missing some things. I couldn't get either Tkinter or pygtk for it, for example.

---

### Post by conundrumx on 2008-12-04
I had Python 2.3, 2.4 and 2.5 installed at one point, without messing up any programs.  In short, don't worry, everything will work out!

Of course, knowing how to change which version of python a script calls might be helpful.  I can't count how many times I had to do ```
sudo nano -w `which startup-manager`
```

---

### Post by eragon100 on 2008-12-04
Good to hear! :)

However, I would like to see 2.6 be default in jaunty as well, as opposed to 3.0. It is ineed pretty vital for making the needed changes :wink:

---

### Post by jpeddicord on 2008-12-04
> **eragon100 said:**
> Testing is impossible right now, since jaunty alpha 1 doesn't ship with python 3.0

Jaunty has 3.0 in the python3.0 package. I use it right now for testing.

My guess is that 2.5 will be the default, 2.6 and 3.0 will be installed. It will be a while for people to port to 2.6, let alone 3.

---

### Post by eragon100 on 2008-12-04
> **jacobmp92 said:**
> Jaunty has 3.0 in the python3.0 package. I use it right now for testing.

My guess is that 2.5 will be the default, 2.6 and 3.0 will be installed. It will be a while for people to port to 2.6, let alone 3.

testing that sounds like a good idea, thanx :wink:

---

### Post by wmcbrine on 2008-12-04
> **jacobmp92 said:**
> It will be a while for people to port to 2.6, let alone 3.Using 2.6 shouldn't require porting. Only 3.0 is backwards-incompatible.

---

### Post by jdong on 2008-12-04
> **wmcbrine said:**
> Using 2.6 shouldn't require porting. Only 3.0 is backwards-incompatible.

Famous last words :)

---

### Post by jpeddicord on 2008-12-04
> **jdong said:**
> Famous last words :)

```
$ python2.6
>>> import python2.5
  File "<stdin>", line 1
Exception: your computer has exploded
```

---

