---
title: "DeVeDe cannot complete conversion Jaunty 64-bit"
date: 2009-08-15
forum: Ubuntu Studio
---

### Post by jtslau on 2009-08-15
Right I have a problem using DeVeDe under Jaunty 64-bit.  After selecting multiple videos and starting the conversion process, the conversion would fail after encoding just one video, giving the error message: 

"Conversion failed Maybe you ran out of disk space?"

Interesting of note, this problem only happens in Jaunty 64-bit, as I have installed Jaunty 32-bit and Karmic 64-bit (alpha3) and both do not have the aforementioned problem.

My system specs:
Intel Core i7 920
6GB DDR3 Ram (Thus the reason why running 64-bit is necessary).
500 GB WD Black Drive for system files, formatted as xfs (with a ext2 boot partition).
640GB x 8 WD Black Drives in RAID5 mdadm array mounted as /home, formatted as xfs.
Mplayer Version: 2:1.0~rc2-0ubuntu19+medibuntu1
Mencoder version: 2:1.0~rc2-0ubuntu19+medibuntu1
Other software obtained either through Ubuntu repository or through Medibuntu repository, none other repositories are used.

Does anyone have any ideas how to fix this?  Upgrading mplayer or mencoder to Karmic's version is not an option, as all that does is introduce dependency hell.

Note that I have filed a bug report on launchpad, but figure I try my luck here as well.  You can reproduce this error by installing devede on Jaunty 64-bit and converting more than 2 titles.

My bug report filed here: [https://bugs.launchpad.net/ubuntu/+source/devede/+bug/413460](https://bugs.launchpad.net/ubuntu/+source/devede/+bug/413460)

---

### Post by OisinT on 2009-09-25
I'm having the same problem now too... it's driving me crazy.  No settings changed on my end, it just seemed to stop working after an update.  All help appreciated

---

### Post by frank392 on 2009-10-29
I have the same problem on 9.04 ands 9.10 32 bits

---

### Post by raditzman on 2010-02-22
I'm also having the same problem in KK 64 bits. If I do a preview of the video with subtitles it hangs at 97%, but if I do it without subtitles it shows fine.

Any help is welcome.

---

### Post by jtslau on 2010-03-12
Actually the issue (at least for me) has been fixed as of Karmic 64-bit, and the bug fixers at launchpad have marked the issue as closed.

---

### Post by stonebit on 2010-09-12
I've had the problem as well. I reinstalled after a purge, tried different machines, bla bla bla. After some trial and error, it seems the issue is with certain container formats (avi mostly for me) and the size of the container file (avi over 1 gig). I worked around the issue by swapping  containers on the input file...

Install mkvtoolnix-gui and mkvtoolnix. Run the mkv file creator. Input your file that crashes devede. Make sure the desired video and audio tracks are checked. Look at the output file location. Start the mux (this will take almost no time). Input the new mkv into devede in place of the file that doesn't convert / shoots out the error. Devede should now run through without any issues and make the dvd iso.

---

