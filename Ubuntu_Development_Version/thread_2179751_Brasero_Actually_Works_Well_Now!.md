---
title: "Brasero Actually Works Well Now!"
date: 2013-10-09
forum: Ubuntu Development Version
---

### Post by craig10x on 2013-10-09
At least the version that is offered in ubuntu 13.10 anyway...I think i read there is a new maintainer on it now (after the original maintainer had neglected it for quite some time) and i recently decided to give it another try...

There is one VERY IMPORTANT "tip" you need to know...As set up by default, when burning a disc, Brasero will perform what it calls a CHECKSUM both before and after the disc is burned...i think it is supposed to be checking for errors or something...If you use it as is, Brasero is slow as molasses and can take about 22 minutes to burn a 4 gb dvd....

However, if you go to "edit" "plug ins" and uncheck the two CHECKSUM plug ins (the before and after) then the same disc will burn in 9 minutes or so!  (same as k3b would take)...

I made data discs, iso images, and even ripped (copy to copy) an encrypted dvd just like k3b does and in the same amount of time!  (you have to have libdvdcss2 on your system for that to work of course)...

So without Checksums, it seems to be working great and have not got a single "coaster" yet :D

Finally i can use the default gnome burner instead of having to install the kde one... ;)

---

