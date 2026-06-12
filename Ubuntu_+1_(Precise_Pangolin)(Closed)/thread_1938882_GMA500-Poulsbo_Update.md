---
title: "GMA500-Poulsbo Update"
date: 2012-03-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fjgaude on 2012-03-10
Hey, fellows (you know who you are) does any of this link apply to what is to be released with 12.04?

[http://www.phoronix.com/scan.php?page=news_item&px=MTA2ODQ](http://www.phoronix.com/scan.php?page=news_item&px=MTA2ODQ)

---

### Post by lucazade on 2012-03-10
Hi fjgaude!
unfortunately at the moment these patches are just for kernel 3.4... we have to wait!

btw there is aleady some ongoing work in precise to have a out-of-the-box experience with psb_gfx.
There are a couple of bug reports marked as work in progress.

---

### Post by fjgaude on 2012-03-10
Well, sooner or later I'll give 12.04 a try with psb_gfx. Right now the EMGD 1.8 is working okay w/ 11.10.

I'll give kernel 3.4 a try as soon as it is out. Will 12.04 ever get it?

Thanks for the reply!

---

### Post by PilotPaul on 2012-03-11
Any work on psb_gfx is good news (I am using it in Precise beta on my 751h at the moment), but ultimately the lack of hardware acceleration to me means there is still no real future for this chip  ... EMGD 1.8 works OK for me on Natty (my main production partition), but having spent the last 3 years with this lovely little netbook I am likely to replace it this summer (considering an Aspire S3 Ultrabook).

Still its been a hell of a ride! :-)

---

### Post by tista on 2012-03-11
Yeah guys! let's ride the crazy wave!! :)

[IMG]http://i42.tinypic.com/5cy79l.jpg[/IMG]

---

### Post by KarmicKarmicChameleon on 2012-04-06
> **PilotPaul said:**
> Any work on psb_gfx is good news (I am using it in Precise beta on my 751h at the moment), but ultimately the lack of hardware acceleration to me means there is still no real future for this chip  ... EMGD 1.8 works OK for me on Natty (my main production partition), but having spent the last 3 years with this lovely little netbook I am likely to replace it this summer (considering an Aspire S3 Ultrabook).

Still its been a hell of a ride! :-)

It has been a great ride! I'm likely to keep my Dell Mini 10 for several more years though due to it's small formfactor and ability to slip it in and out of my jacket for on the fly environment testing. Hopefully we'll get the bugs out and fully support the gma500 without all of the hoop jumping. 

I just gave Lubuntu a shot and it doesn't boot at all after install. Freezes with the Lubuntu loading screen. :(

---

### Post by fjgaude on 2012-04-26
Wow, I ran the Release i386 ISO of 12.04 on my Dell mini-10n without a hitch! WiFi, sound, screen resolution (1366x768) all working without intervention.

Thank you, Alan Fox, Tista, Luca, and all, for the good work.

Will report if the machine sleeps/resumes after install to a partition.

UPDATE: Installed, went as expected, following the tips from Poulsbo support site.

Ran GTKPERF and received 30.1 seconds, the best ever! Was 300 sec on 11.10 and 70 sec on 10.04. Wow! Thanks to all!

Am updating kernel to 3.2.0-24 pae now.

UPDATE: No go for Resume after Suspend. Everything works as it should.

---

### Post by lucazade on 2012-04-26
;)

---

