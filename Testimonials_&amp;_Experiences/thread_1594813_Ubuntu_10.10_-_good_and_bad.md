---
title: "Ubuntu 10.10 - good and bad"
date: 2010-10-12
forum: Testimonials &amp; Experiences
---

### Post by julianb on 2010-10-12
I have Ubuntu 10.10 installed on my eeePC 1201hab. There are things that I like, and things that I don't.

It doesn't work out of the box with the intel "poulsbo" graphics hardware. Following the instructions [here]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") to install poulsbo drivers made the machine's resolution work correctly, but made the machine fail to play any videos except in flash player. 

Flashplayer and java have worked great, no fuss - same with nearly everything else about the OS. There are some significant improvements over previous versions of Ubuntu. But...

Suspend doesn't work. Shutdown doesn't always work right either - both of these problems, though, came up after I installed the drivers for the poulsbo graphics hardware.

Another issue is, the built in chat client isn't working with facebook or gmail chat. the "broadcast accounts" feature seems to have a problem with identica but works with other services.

The webcam that came with the machine still doesn't work. And neither does Skype (it's unable to pick up sound from the microphone, even though the included Sound Recorder app works correctly).

---

### Post by 3Miro on 2010-10-12
I guess you have seen this thread, people are suggesting to try another distro. I will be interested to know if indeed another distro will work "out of the box". If so, then this is bad for both Intel and Canonical (I mean worse than just not working).

[http://ubuntuforums.org/showthread.php?t=1453445](http://ubuntuforums.org/showthread.php?t=1453445)

As for Skype, it can be very picky sometimes. Have you tried changing the sound device in the Skype settings and definitely don't let Skype adjust your mic volume. Between selecting input/output devices from the mixer applet and alsamixer in the terminal as well as fiddling with the Skype settings, I have always managed to get it to work (on hardware different form yours of course).

Lets hope they come up with a patch for the graphics driver soon.

---

### Post by ubunterooster on 2010-10-13
iNtel seems to be a large problem in GPU problems this release

---

