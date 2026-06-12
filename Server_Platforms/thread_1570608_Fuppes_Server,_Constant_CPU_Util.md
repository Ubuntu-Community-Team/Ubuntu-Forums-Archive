---
title: "Fuppes Server, Constant CPU Util?"
date: 2010-09-08
forum: Server Platforms
---

### Post by mattlach on 2010-09-08
All,

I recently installed fuppes using the instructions posted here:
[http://ubuntuforums.org/showthread.php?t=1310511](http://ubuntuforums.org/showthread.php?t=1310511)

further following the instructions here to add to init.d:
[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d)

I now have fuppes running, and it seems to function (I have streamed several test videos and some music on our PS, but I still need to figure out dependancies and the ugly XML config file to enable transcoding.

Two issues I have noted:
1.) On my dual core Athlon X2 1.5ghz fuppes constantly uses anywhere from 7 to 10% CPU, even after DB building is complete, wheter I am trying to stream anything or not.   Is this normal?  Should I file a bug report?

2.) Unlike most other people, I can't seem to get the web management interface to work.  The port I set in the config file is open, but all it does is display a blank white webpage.  Is this another bug I should file, or a config issue?

I appreciate any feedback.

Thanks,
Matt

---

### Post by dfroe on 2011-01-24
> On my dual core Athlon X2 1.5ghz fuppes constantly uses anywhere from 7  to 10% CPU, even after DB building is complete, wheter I am trying to  stream anything or not.I also noticed the same behaviour here on Ubuntu 10.04 LTS with fuppes 0.680.
After fuppesd runs for one hour it has already consumed 25 minutes of cpu time.
I do not know, but I guess this looks like a general bug in fuppes.

---

