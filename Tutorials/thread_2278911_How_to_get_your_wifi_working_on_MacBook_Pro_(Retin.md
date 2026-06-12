---
title: "How to get your wifi working on MacBook Pro (Retina, 13-inch, Mid 2014)"
date: 2015-05-19
forum: Tutorials
---

### Post by Jamie_Batchelor on 2015-05-19
Hello there,

I am here today to give you a tutorial on how to get your wifi working on MacBook Pro (Retina, 13-inch, Mid 2014), with Ubuntu 14.04 LTS.

Firstly you must go to your terminal application within Ubuntu, once you have done that, you then copy below and paste it into the terminal.
lspci -nn

then you press enter and look for the broadcom wireless name, once you have got it, copy below and paste into the terminal.


sudo apt-get install bcmwl-kernel-source

press enter, if it asks you for a media disc labelled, just press C and enter, it should then start to download what is needed.

next, you must copy and paste this below into terminal.

modprobe wl

Now press enter and you should be done!.

If you don't have it show up, just try restart your pc.

Thanks for reading and enjoy.

---

