---
title: "Using Mencoder to convert a xvid to a dvd 2Pass?"
date: 2009-01-06
forum: Ubuntu Studio
---

### Post by echel0n on 2009-01-06
I'm currently trying to convert a xvid to a dvd mpg compliant file but in high quality and was wondering if someone could throw me some help on this one.

Here's the commands I'm using so far.

```

#Pass 1
mencoder -oac copy -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:480,harddup -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:vstrict=0:aspect=16/9:vpass=1 -ofps 30000/1001 -o /dev/null movie.avi

#Pass 2
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf scale=720:480,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:vstrict=0:acodec=ac3:abitrate=192:aspect=16/9:vpass=2 -ofps 30000/1001 -o movie.mpg movie.avi

```

Also is mencoder better to use for quality then ffmpeg ? I know mencoder is more just a frontend to ffmpeg but still wanted to ask the question.

Thanks.

---

### Post by eshwar_andhavarapu on 2009-11-29
got the same question. . .

---

