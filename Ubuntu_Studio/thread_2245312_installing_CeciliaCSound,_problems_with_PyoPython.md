---
title: "installing Cecilia/CSound, problems with Pyo/Python"
date: 2014-09-22
forum: Ubuntu Studio
---

### Post by Zestie Bumwhig on 2014-09-22
I already posted this in "Multimedia"; I thought I should give it a shot over here, too, even though I'm not actually running Ubuntu Studio (my computer's too old!)

I'm trying to install Cecilia, a frontend for CSound. I've used it  before; it's a hoot. Now, I know there's a Cecilia in Synaptic, but it  doesn't work on either of my computers. It's years out of date.

I'm running Lubuntu 12.04.04 LXLE, because I have a 10-yr-old 32bit  laptop. I have downloaded Cecilia5, but I need Python and Pyo for it to  run, apparently. I am WAAAY out of my depth at this point.

I have followed directions for installing pulseaudio (and I'm pretty  sure I got it right), and Python, and wxpython... I'm following these  directions:

[https://code.google.com/p/pyo/wiki/Installation](https://code.google.com/p/pyo/wiki/Installation)

But my current stumbling block is 
sudo python setup.py install

It goes a long ways, and then says
src/engine/pyomodule.c:24:21: fatal error: sndfile.h: No such file or directory
compilation terminated.
error: command 'gcc' failed with exit status 1

Anyone know what to do here? I used the SVN to get the exact pyo the  site was talking about (pyo-read-only). I'm just really flying blind  here... hoping that, if I follow these instructions to the letter, I'll  be rewarded with awesome noises.

Similarly, if anyone out there has already installed Cecilia5, I'd love  to hear your stories. I'm not even sure how to start it, once it gets  loaded. I've used it - that's not what I mean - I just don't know how to  launch a Python(?) script(?).

Thanks!

---

### Post by Zestie Bumwhig on 2014-09-22
You know Temujin? Temujin, over in Multimedia? You know that cat, right?

Well, Big T solved this for me. Apparently, I still needed 
libsndfile1-dev

available via Synaptic or apt-get install. That wasn't the only one; after that, I also needed portaudio-midi and liblo-dev.

But I got them, and it works!

Thanks, T.

---

