---
title: "ardour"
date: 2009-10-10
forum: Ubuntu Studio
---

### Post by oslt on 2009-10-10
Dear users,

after my last windows installation broke down because of a virus I decided to install ubuntu studio, because I used magix musicmaker an several software like audacitiy on my windows xp platform.

Installing was easy but then I had lots of difficulties to make my webcam run and to install the right Alsa drivers for my onboard soundcard: AC'97 Sound Controller

Then deinstalled ardour and reinstalled and finally got it working, But after some hours, ardour refused to open saved projects because of a wrong sample rate and then told me my harddisk is too slow to have just a little record of my own voice. On Windows xp my hard disk wasn't too slow!

Is there anybody so kind to help a beginner out of the mess of audio configuration and audio servers under ubuntu 8.04, especially with ardour? Please.

Bernd

---

### Post by trulan on 2009-10-10
Are you on a laptop?  Ardour tells me that my laptop hard drive is too slow if I am running on battery power.  When I plug in the charger it works fine.

The easiest way to set the sample rate is by using Jack Control.  You need to have Jack running at the sample rate the project was recorded with, or it won't work.

---

