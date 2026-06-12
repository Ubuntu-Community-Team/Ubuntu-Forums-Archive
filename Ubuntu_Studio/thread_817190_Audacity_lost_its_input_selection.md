---
title: "Audacity lost its input selection"
date: 2008-06-03
forum: Ubuntu Studio
---

### Post by ajgreeny on 2008-06-03
I've searched the forums but not found any real answer so here goes.
In Gutsy I had audacity working perfectly with all the inputs (Mic, Mix, Line in, etc etc)working fine. Since doing a clean install of Hardy I only have microphone input and nothing else, not even a drop down box showing.

I've tried all the different sound drivers, both system wide and in Audacity preferences, ie Pulse, ALSA,  OSS and nothing makes a scrap of difference.  Is this a kernel problem with the drivers?  I've even tried the earlier version of Audacity from Gutsy, but that was exactly the same.

---

### Post by caljohnsmith on 2008-06-03
> **ajgreeny said:**
> I've searched the forums but not found any real answer so here goes.
In Gutsy I had audacity working perfectly with all the inputs (Mic, Mix, Line in, etc etc)working fine. Since doing a clean install of Hardy I only have microphone input and nothing else, not even a drop down box showing.

I've tried all the different sound drivers, both system wide and in Audacity preferences, ie Pulse, ALSA,  OSS and nothing makes a scrap of difference.  Is this a kernel problem with the drivers?  I've even tried the earlier version of Audacity from Gutsy, but that was exactly the same.

Just wanted to mention I was having problems with Audacity crashing and other strange behavior in Hardy, so I went with the stable 1.2.7 release instead of the 1.3.x release in the repos. I have not had any trouble since. If you want to give it a try, just go to packages.ubuntu.com and search for Audacity.

---

### Post by Hal58 on 2008-09-03
> **caljohnsmith said:**
> Just wanted to mention I was having problems with Audacity crashing and other strange behavior in Hardy, so I went with the stable 1.2.7 release instead of the 1.3.x release in the repos. I have not had any trouble since. If you want to give it a try, just go to packages.ubuntu.com and search for Audacity.

Could you please provide a little more description of just what steps are needed to do this?  I tried to force load of 1.2.6 from earlier Feisty and a stable Debian and only succeeded in corrupting my apt database.

In searching bug reports, there is one which duplicates the problems I am experiencing on about seven systems (all different H/W and Hardy OS).  I added more info, but apparently no one has reviewed that bug which seems to relate to WxWidgets problems with Hardy.  If the Hardy version of Audacity (1.3.4Beta) is loaded and a WAV file loaded, the following will show the problem:
  - Cut a few tenths of a second from the beginning
  - Move to the end and cut a second or so.

Very quickly CPU usage will go to 100% allocated about 33/66 percent to Audacity and X, although nothing in the Audacity window changes.  You can still move the cursor, but Audacity is frozen.  It can be killed by bringing up a terminal and "killall audacity", and the CPU load will return to normal.  I have had an Athlon64 sitting there for 20 minutes just getting hotter and hotter...

I have tried many config settings, pulse/alsa changes, different files, and cpus including Athlon64, Via C7, Mobile Celerons and Intel Atoms with the same results.  Since I spend many hours a day processing old vinyl music, this is forcing me to keep a couple of old systems with Dapper (6.06).

---

