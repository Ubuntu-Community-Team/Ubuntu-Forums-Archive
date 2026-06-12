---
title: "usb support wine | crossover | virtual box exe files"
date: 2012-01-20
forum: The Cafe
---

### Post by Claus7 on 2012-01-20
Hello,

lately, I was wondering what I was missing in the linux world, and I could not find much that I was having a great need.

Yet, even though this issue might be endless, I found out that there are some occasions, in which someone would like to run an exe file, which would entail connection with a hardware device.

My main question would be (yet every other answer on the issue is welcome): at which stage is (especially) wine on this issue, which might help a lot of people and their devices?

Every answer is appreciated,
Thank you,
Regards!

---

### Post by gleedadswell on 2012-01-26
I'm dealing with this same issue right now.  In particular, I need to run a program (Data Studio - it's for physics teaching) which is only available for Windows and which needs to talk to data logging sensors via usb.  

See here:

[http://wiki.winehq.org/USB]("http://wiki.winehq.org/USB")

for a rundown on the current status of usb support in wine.

I'm in the middle of trying it out.  I just got the wine source, applied the patches and did the compile (my first time compiling a package from source - I'm such a n00b!).  So far so good.  I'll install the .exe and try connecting to devices tomorrow.  I'll post back here with my experiences.

---

### Post by Claus7 on 2012-01-27
Hello,

thank you very much for your answer. A difficult task to build your own program from source for the first time. I'm very curious to see your result. I hope you the best!

Good luck,
Regards!

---

### Post by gleedadswell on 2012-01-27
Still working on it.  

The compile went fine, except that it can't seem to find libusb.h, so while I had a working wine at the end of the compile I don't think it would have been able to access the usb ports.  So I'm going to figure out where it is looking for libusb.h and make sure there is either a copy of it there or a symbolic link.

Also it took me quite a while to figure out the Windows registry and how to get the drivers and other things that I need out of it to import into wine's registry.  Wow!  The Windows registry is one of the worst pieces of CRAP I've ever seen!  Impossible to navigate, the interface (REGEDIT) sucks and it contains absolutely no documentation to tell you what is what.

---

### Post by gleedadswell on 2012-01-27
Ah ha!  Reading the code in the patch it *looks* like it needs to find a file called libusb.h OR a file called usb.h.  On an Ubuntu install it looks like what we have is a usb.h.  So I think that's working the way it should.

-------------EDIT LATER--------------

Nope!  I was totally wrong.  libusb.h and usb.h are distinct files and you need both for the ./configure to work.  Installing libusb-1.0-0-dev fixed that problem.

---

### Post by Claus7 on 2012-01-27
Hello,

&#967;&#945;&#961;&#940;&#962; &#963;&#964;&#959; &#954;&#959;&#965;&#961;&#940;&#947;&#953;&#959; &#963;&#959;&#965;!...= well done to your efforts and persistence! These were the first words that came to mind.
I admit that you fight the problem with a plan. I would not like to discourage you, yet I do not think that you have an easy task in front of you. I hope that you will be able to find a solution to your problem soon. At the first time I took a look on it I realised that it is supposed to be a very difficult task.

Nonetheless, good luck with your efforts.
May be, if you are seeking more support, you can create a new thread outside community cafe area. 

Kind regards!

---

