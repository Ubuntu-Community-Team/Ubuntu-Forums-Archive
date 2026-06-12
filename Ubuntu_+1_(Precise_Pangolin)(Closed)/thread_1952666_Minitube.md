---
title: "Minitube"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by northwestern on 2012-04-04
Has anybody managed to get the video working in minitube 1.7.1 yet ?

I have two problems-
1/ Video does not run but sound is OK.
2/ The selected tune changes to the next one before it has finished.

appreciate any help.

Regards
Northwestern

---

### Post by mc4man on 2012-04-04
There are 2 things wrong atm - 
First there is a possible crash when switching videos
[https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/921287](https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/921287)

Then there is the inability of gstreamer thru the gstreamer phonon backend to properly decode most Baseline@L2.1, Baseline@L1.1  files which are quite common on youtube - (_this bug needs confirming.._
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014)

A solution to the decoding issue is to use the vlc phonon backend which is quite possible though you have to  either re-build minitube or unpack the minitube .deb, edit the control file & repackage (I do the former), then install the vlc backend & remove the gstreamer backend

Bug on that, no decent response 
[https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586](https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586)

So here, using the vlc backend there are no decoding issue & it rarely crashes, (the gstreamer backend is very prone to crashes

---

