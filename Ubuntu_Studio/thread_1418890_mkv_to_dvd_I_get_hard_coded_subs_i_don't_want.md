---
title: "mkv to dvd I get hard coded subs i don't want?"
date: 2010-03-01
forum: Ubuntu Studio
---

### Post by Ferrat on 2010-03-01
Well I seem to have to opposite problem from most, I don't want hard coded sub but for some reason mencoder has started hard coding sub stream 2 subtitles to my mpg?

```
mencoder -channels 6 -ovc lavc -oac lavc -of mpeg -mpegopts format=dvd:tsaf -srate 48000 -lavcopts vcodec=mpeg2video:vpass=1:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=4000:keyint=12:trell:mbd=2:precmp=2:subcmp=2:cmp=2:dia=-10:predia=-10:cbp:mv0:vqmin=1:lmin=1:dc=10:vstrict=0:threads=2:aspect=4/3:acodec=ac3:abitrate=448 -ofps 25 -speed 25025/24000  -vf scale=720:576 -o output.mpg source.mkv 

```

This worked yesturday but for some reason it now adds subtitles, I've tried purge mplayer and mencoder and removed the .mplayer (can't find a .mencoder) but I still get them hard coded? :/

---

### Post by Ferrat on 2010-03-01
mplayer has also started using stream 2 subs as default when starting the mkv file? how do I change this? tried removing subtitles auto loading etc but nothing changes

EDIT: found a way around it by adding a -sid that didn't exist but really why did this happen in the first place?? stops me from using devede again :/

---

### Post by cwhisperer on 2010-03-09
> **Ferrat said:**
> Well I seem to have to opposite problem from most, I don't want hard coded sub but for some reason mencoder has started hard coding sub stream 2 subtitles to my mpg?

```
mencoder -channels 6 -ovc lavc -oac lavc -of mpeg -mpegopts format=dvd:tsaf -srate 48000 -lavcopts vcodec=mpeg2video:vpass=1:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=4000:keyint=12:trell:mbd=2:precmp=2:subcmp=2:cmp=2:dia=-10:predia=-10:cbp:mv0:vqmin=1:lmin=1:dc=10:vstrict=0:threads=2:aspect=4/3:acodec=ac3:abitrate=448 -ofps 25 -speed 25025/24000  -vf scale=720:576 -o output.mpg source.mkv 

```

This worked yesturday but for some reason it now adds subtitles, I've tried purge mplayer and mencoder and removed the .mplayer (can't find a .mencoder) but I still get them hard coded? :/

Hi,
I don't know the answer to your question, but I would rather know how to create a dvd from an mkv file? thx for any help ;)

---

