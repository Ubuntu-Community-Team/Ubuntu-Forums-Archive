---
title: "[SOLVED] Installing ardour 2.5 in Studio"
date: 2008-07-28
forum: Ubuntu Studio
---

### Post by Dark Horse on 2008-07-28
I was trying to install ardour 2.5 from source and I am getting the following error:

Checking for C header file fftw3.h... yes
Checking for C header file aubio/aubio.h... yes
FREESOUND support is not enabled.  Build with 'scons FREESOUND=1' to enable.
LV2 support is not enabled.  Build with 'scons LV2=1' to enable.
This system has no functional C++ compiler. You cannot build Ardour from source without one.

According to synaptic I have G++ installed along with a couple of other compilers.  How do I fix this??
Mark. :confused:

---

### Post by Stochastic on 2008-07-29
try ```
sudo apt-get install build-essential
``` if you continue to get the error I'd post your issue to the [Ardour Forums]("http://ardour.org/forums") as there will be many more people there who know ardour's code.

---

### Post by thorgal on 2008-07-29
and after Stochastic's command line, type this :

```

sudo apt-get build-dep ardour

```

or ardour2 (don't remember the official name of the package).
This command will install all dev packages required to build ardour. Note that if the repository only knows ardour 2.4 or even older, you may face compilation errors as ardour2.5 requires a new lib (libaubio). If so, yo uwill need to install it from your package manager (the lib and the dev package).

---

### Post by Dark Horse on 2008-07-29
Thanks for the replies I found the answer sort of I went to synaptic and searched for a c++ compiler and installed g++ and any thing that said dev or build after it. I must have found the right one after that I still had to install some other dependencies but I did get it to compile on this box Ardour 2.5 is up and working And so far it is the best Ardour yet now If I could eliminate the random freezes (They do seem to be happening less often though). Now to install Ardour 2.5 on the Box in the shack.
     Mark  :popcorn::lolflag:

---

### Post by angelsguitar on 2008-07-29
Also, may I suggest to take a look at this post for useful info on how to build Ardour (with vst support and other extra options):

[http://ubuntuforums.org/showthread.php?t=801718]("http://ubuntuforums.org/showthread.php?t=801718")

---

