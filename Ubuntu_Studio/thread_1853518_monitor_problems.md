---
title: "monitor problems"
date: 2011-10-02
forum: Ubuntu Studio
---

### Post by Brian shep on 2011-10-02
hello all i have a problem with a sony multiscan E400 crt monitor there doesnt seem to be drivers for this monitor i am running studio 11.04 what can i do are there generic drivers that will let me adjust the screen resolution and refresh rate.........

---

### Post by oldsoundguy on 2011-10-02
Have you tried going into system> preferences> monitor .. and seeing if you can make adjustments there?

It is the video card or chip and drivers for same that determine what can and can not be done with a display. And the support for some older and built in chips just do not work at 100% (plus, CRT monitors are also now considered legacy hardware.)

---

### Post by Brian shep on 2011-10-02
actually yes. oldsoundguy  i tried but it wont let me adjust the resolution which is 1024 by 768 or the refresh rate  so i have horrible flickering and greenish color my computer is an oldie but goodie dell optiplex 160l with onboard video no video card! surely i can do something!~

---

### Post by oldsoundguy on 2011-10-02
> **Brian shep said:**
> actually yes. oldsoundguy  i tried but it wont let me adjust the resolution which is 1024 by 768 or the refresh rate  so i have horrible flickering and greenish color my computer is an oldie but goodie dell optiplex 160l with onboard video no video card! surely i can do something!~

Unless you are into exploration, testing, and the usual "let's see what this does" .. the time spent trying to bring legacy hardware up to anything that resembles speed and smoothness, is really wasted time for most.

Having said that .. I have one box that I have dubbed "my crash test dummy"  and that is what it is!  NOTHING critical on it so that I can experiment without any fear .. the "so what" attitude .. if it crashes, just try something different.

You might try putting Linux Mint (it utilizes Ubuntu's version of Linux) and see if you can get the thing to function.  I have found that Mint works on Legacy stuff, albeit sometimes slow and sometimes with a lot less bells and whistles, but it DOES work.

---

### Post by jejeman on 2011-10-02
Give us an output from
```
lspci -knn|grep VGA -A 4
```
is this specs. for this monitor
> Horizontal Scan Range - 30 - 96kHz
Vertical Scan Range - 48 - 120Hz
Maximum Resolution - 1800 x 1440 @ 60Hz
Recommended Resolution 1280 X 1024 @ 85Hz 

---

### Post by Brian shep on 2011-10-02
thanks for the response you guys sorry for the absence today! well i ran dpkg reconfigure xserver xorg and seemed to improve things a bit ...corrected the resolution but shows refresh rate of 0 and wont let me adjust it under preferences, and as far as testing goes its not a problem. thats what i do with this optiplex.............its a tank! ive installed many different distros on this little tank and usually without problems but normally i use an lg led display monitor but i decided to upgrade to this LEGACY monitor which is quite a nice thing for 8 dollars by the way!!! i would be happy to try anything you guys recomend to get this thing working right .im pretty sure there is a solution to my resolution.. thanks again for the help!@

---

### Post by Brian shep on 2011-10-02
hello jeje man that seems to be right as far as the monitor specs go ....its a 19 inch sony i would think that my onbord graphics support this monitor at least at the 1280 resolution ..i would appreciate any advice you could give me.

---

### Post by jejeman on 2011-10-03
First, give us the output from the command above.

---

### Post by sgx on 2011-10-03
> **Brian shep said:**
> actually yes. oldsoundguy  i tried but it wont let me adjust the resolution which is 1024 by 768 or the refresh rate  so i have horrible flickering and greenish color my computer is an oldie but goodie dell optiplex 160l with onboard video no video card! surely i can do something!~
Get an used nvidia pci video card cheap, from a gamer, recycler, or a new one at bestbuy is only $50.

Try macpup, and pclinuxos, the debian hardware detection is different
than what pclinuxos uses, and a different kernel. Before getting
an nvidia video card, my main computers motherboard chip/monitor would not function with debian distros. Sometimes hardware and software must be matched.
Cheers

---

