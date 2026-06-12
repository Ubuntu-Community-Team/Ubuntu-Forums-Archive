---
title: "QJackCtl, need help setting up patches"
date: 2013-08-30
forum: Ubuntu Studio
---

### Post by louh2 on 2013-08-30
I was trying to set up patching using Mudita24 but after some attempts I'm finding out that it can't be used for my card, a M-Audio Delta 2496.  So I am trying to setup patches between software and hardware using QJackCtl.  Has anybody had any success doing this?  I am using Hydrogen, MuSe, Audacity to start.  I have seen the general guidelines of setting up patches but it doesn't really help me understand it enough to set my own connections up.  Basically what I want to achieve is the ability to connect external midi devices to internal software and to be able to monitor tracks while recording.  So far I can't get full duplex audio although I am able to accomplish the midi connectivity somewhat.  I'm hoping QJackCtl will be the answer here.  I am not too overly concerned with latency as I am not playing external devices like keyboards yet but it would be nice to get it as low as I can without distortion.  Thanks ahead of time for any direction here.

---

### Post by jejeman on 2013-08-30
Don't know what you mean by "patches", but if you have listed everything you need in Qjackctl connections, just start connecting.

---

### Post by louh2 on 2013-09-01
I did this but found that the original problem I was having, [http://ubuntuforums.org/showthread.php?t=2170868](http://ubuntuforums.org/showthread.php?t=2170868), still existed.  No full duplex which makes recording nearly impossible.  However I found out what the actual problems was and it had little to do with Jack.  I was trying to route all signals through one of two connections which couldn't work with my current setup.  I needed to select the digital mixer as the port and then use software driven mixers/control panels to control inputs and outputs.  Now it's working well and Jack is setup pretty good too.  I am able to listen to drum patterns in Hydrogen while recording a bass line in Ardour.  This problem has been solved.

---

