---
title: "cinelerra instrallation"
date: 2010-03-28
forum: Ubuntu Studio
---

### Post by Lord M on 2010-03-28
Hello,
I would need some info on how to get installed cinelerra on Ubuntu Studio 9.10 (latest version).

I had some bad results with opensuse and now I switched to Ubuntu and I found quite good distro, I just miss some software (I will post in a new thread the other I need fast).

My pc is a 64 bit, if this matters and I added the repository

[http://giss.tv/~vale/debian64]("http://giss.tv/%7Evale/debian64") ./

but it says I still miss some piece of dependencies, mainly lib and encoders... and the "software won't be installed". Is this a karmic problem?

Any idea or some repository that is known to work on this distro to have the compisiting software?

Thanks for any clue.

---

### Post by d_in_Conduct on 2010-03-29
Take a look at:

[http://cvs.cinelerra.org](http://cvs.cinelerra.org)

---

### Post by Lord M on 2010-03-29
Thank you!
I hope this will solve also the dependencies problems. I got before a cinelerra fully installed but without the codec it was not working, opening or import any movie file.

The packages here are for 9.04 and I have the 9.10. I will try later and post my results.

---

### Post by Lord M on 2010-03-29
Ok I tried the package: first news is I got cinelerra but at start I have this error

MWindow::int_shm:/proc/sys/kernel/shmmax is 0x2000000
it should be at least 0x7ffffff for cinelerra

plus I can't import any movie file, I can't see anything. I also installed all the extra libs that are listed in the software requirements on the website. 

This but I can't find all in the repository


[LIST]
[*] a52dec
[*] dv
[*] faac
[*] ffmpeg
[*] fftw
[*] lame
[*] libavc1394
[*] libfaad2
[*] libraw1394
[*] mjpegtools
[*] OpenEXR
[*] theora
[*] x264
[/LIST]


Ideas? 

A good alternative could be another software to compose videos with similar features.

---

