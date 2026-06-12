---
title: "Missing library for alsa application"
date: 2011-06-02
forum: Ubuntu Dev Link Forum
---

### Post by fbr-dk on 2011-06-02
Hi,

Newbie trying to compile alsa app in Ubuntu 10.10, like

gcc -o AudioGenerator AudioGenerator.c -lasound

but get

/usr/bin/ld: cannot find -lasound
collect2: ld returned 1 exit status

can anyone tell me which library to use?

Small part of source shown below:

#include <stdio.h>
#include <stdlib.h>
//#include <alsa/asoundlib.h>
#include <sound/asound.h>
#include <math.h>

main(void)
...

thank you
fbr

---

### Post by pbrane on 2011-06-03
install libasound2 and libasound2-dev. that should do it.

---

### Post by fbr-dk on 2011-06-05
Thank you pbrane - I can compile now.

fbr-dk

---

