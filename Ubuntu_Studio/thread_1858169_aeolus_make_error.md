---
title: "aeolus make error"
date: 2011-10-11
forum: Ubuntu Studio
---

### Post by marcia on 2011-10-11
Dear All,

The ubuntu aeolus would always crash on me immediately after starting it. I decided to find the source and compile. I thought I satisfied all dependencies however I have this error after I run make. This is aeolus 0.8.4 from the aeolus home page.

make
g++  -O3 -Wall -MMD -MP -DVERSION=\"0.8.4\" -DLIBDIR=\"/usr/local/lib64\" -march=native  -c -o audio.o audio.cc
audio.cc: In member function ‘void Audio::init_alsa(const char*, int, int, int)’:
audio.cc:115: error: no matching function for call to ‘Alsa_driver::Alsa_driver(const char*&, int, int, int&, int&, int&)’
/usr/include/clalsadrv.h:36: note: candidates are: Alsa_driver::Alsa_driver(const char*, unsigned int, snd_pcm_uframes_t, unsigned int, bool, bool, bool)
/usr/include/clalsadrv.h:33: note:                 Alsa_driver::Alsa_driver(const Alsa_driver&)
make: *** [audio.o] Error 1

Does anyone understand this error?

Any help will be greatly appreciated.

Thanks.

Marcia

---

### Post by marcia on 2011-10-11
I got it installed. I did need a dependency which was the clalsadrv source library. Now I have a new problem for which I will begin a new thread.

Thanks.

Marcia

---

