---
title: "Video out on Koala Mini Performance improperly bordered"
date: 2007-04-02
forum: System76 Support
---

### Post by Skye on 2007-04-02
Hey folks!

I have a question involving the video out on the koala mini performance computer.  I work for a TV studio, and we bought three of these PCs to use as a bulletin board system (open office impress + full screen = instant bulletin board.)

Everything works well, except for one problem- the TV out displays exactly what it should, but there is a black border around the edge of the display.  This wouldn't be a big deal normally, but we need the display to be full screen, because we broadcast directly what comes from the computer's TV out port.

We have tried messing with the modelines, but nothing really seems to effect the border. The PC's use the intel i945 graphics chipset, which use the intel i810 X driver. Has anyone else encountered this, have a solution, or have some other information? Our xorg.conf is attached.

If anyone could help, that would be awesome.  Thanks!

---

### Post by AusIV4 on 2007-04-03
If I had to guess, I'd say your resolution needs to be adjusted. Changing the modelines in the xorg.conf should enable different resolutions, but it doesn't change your system to them. You'll need to do this in the screen resolution settings in Ubuntu (I use Kubuntu, so I don't know exactly how this is done in Ubuntu).

If it doesn't give you many options, install 915resolution (sudo aptitude install 915resolution), answer its questions, and you should have quite a few more options when it starts up. If this doesn't work, hopefully someone from System76 will have a better answer.

---

