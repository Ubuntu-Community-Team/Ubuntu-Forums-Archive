---
title: "Is there any loop station software?"
date: 2009-09-24
forum: Ubuntu Studio
---

### Post by mikio on 2009-09-24
hi,

I am looking for a software loop station. Something that works like a Roland RC-2 (that is the only one I tried).

I did search the internet but could not find anything. Maybe there is a plug-in for Ardour - I did not find one thought. I think that it might be known under an other name? 

Thanks for any hints!

---

### Post by madeinfamous on 2009-09-24
allo mikio,

you could try this one : SooperLooper

"SooperLooper is a looping sampler very much like the Gibson/Oberheim Echoplex Digital Pro (EDP). Features include Recording, Overdubbing, Multiply, Insert, Replace, Reverse, Mute and many more"

it's in the add/remove

[http://www.essej.net/sooperlooper/](http://www.essej.net/sooperlooper/)

i hope this is what your were searching

have a nice day :)

---

### Post by raboofje on 2009-09-24
Never tried it myself, but i think I've heard FreeWheeling mentioned in this context.

---

### Post by mikio on 2009-09-24
Thanks a lot! 

Both of them are what I was looking for - brilliant! 

Check out the demo videos on:
[http://freewheeling.sourceforge.net/](http://freewheeling.sourceforge.net/) 

For SooperLooper I found this great example video on youtube you might want to check out:
[http://www.youtube.com/watch?v=Y7V-E5tT5zc](http://www.youtube.com/watch?v=Y7V-E5tT5zc)
(there are probably more to find..)

I'll watch the demos and see which one I like more, and give that one a try first..

Thanks again!

---

### Post by trmbtwo on 2010-04-20
You may want to check out Infinite Dub,
[www.infinitedub.com](www.infinitedub.com)

---

### Post by babarosa on 2010-04-24
... and there is "Kluppe" too [http://kluppe.klingt.org/](http://kluppe.klingt.org/) Compiling it is quite easy.

Regards,
Michael

---

### Post by mango42 on 2010-07-25
> **babarosa said:**
> ... and there is "Kluppe" too [http://kluppe.klingt.org/](http://kluppe.klingt.org/) Compiling it is quite easy.

Regards,
Michael

Hi, Apologies for reviving an old thread but based on your recommendation, I had a go at compiling **kluppe_0.6.14-1+b1_i386** on Karmic - gave up at the **libsndfile** requirement. Why isn't this library in Synaptic? **libsndfile1** is...

And sadly the only PPA I've discovered so far throws out an 'unsatisfiable dependency' error - **libfontconfig1** needs to be >2.8.0

It's most likely 'user error' as the synaptic version 0.6.12? installs without problems. I'll get there but any pointers would be most welcome :popcorn:

---

### Post by Pablo_F on 2010-07-25
Hi mango42 . Normally, to compile you need the development versions of the libs, not only the libs themselves. In this case, kluppe depends on libsndfile1, so you need to install libsndfile1-dev. 

Anyway, if you do a :

sudo apt-get build-dep kluppe

you will install all (or almost all, but most probably, all) the dependencies required to compile kluppe.

Cheers! Pablo

---

### Post by mango42 on 2010-07-26
> **Pablo_F said:**
> sudo apt-get build-dep kluppe

Gracias, **Pablo_F** - build-dep is a new one for me!

That's the beauty of Linux - you learn something new every day ... whether you want to or not ;)

On another subject entirely, have you ever got Arpage to work and if so how?

---
danny-mango-bass-aKwardz-g
[http://soundcloud.com/bass-akwardz/](http://soundcloud.com/bass-akwardz/)

---

### Post by AutoStatic on 2010-07-26
Arpage needs an external clock source. I always have Qtractor rolling in the background, but apparently you can also use gtklick: [http://www.linuxjournal.com/content/linux-arpeggiators-part-2](http://www.linuxjournal.com/content/linux-arpeggiators-part-2)

---

