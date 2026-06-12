---
title: "FFmpeg (Slight Return)"
date: 2014-11-22
forum: Ubuntu Development Version
---

### Post by mc4man on 2014-11-22
FFmpeg has been returned though atm only it's binaries will use it.  Generally speaking any source that could benefit from it over libav will need to be specifically built off of. (over time some may start to appear as upgrades to the default package(s)

Also atm it has only native aac encoding, maybe an  'extra' version will appear sometime or nothing a self rebuild or ppa can't resolve.
Should allow the return of mplayer & if any dev pays attention an actual working version of cmus-ffmpeg plugin among other advantages..

---

### Post by andrew.46 on 2014-12-05
> **mc4man said:**
> FFmpeg has been returned [...]

Great news for Ubuntu :)

---

### Post by mc4man on 2014-12-06
Will be interesting over time to see how it develops.
At some point they'll really need to do extra package(s) 
(for other reasons checked out winff & noticed it can't use this ffmpeg for aac audio without altering the preset(s) as it uses libvo-aacenc which can come only come in via extra officially.
Vivid now includes libx265 & it's avail. in the current ffmpeg (2.4.4), currently 35/1.4

mplayer will likely only return if it does so in Debian, haven't seen any movement there
(- I'm pretty sure I saw an offer of help regarding a dynamically linked mplayer/ffmpeg from FFmpeg or Mplayer dev(s), they should take advantage of the generosity

---

### Post by andrew.46 on 2014-12-06
> **mc4man said:**
> mplayer will likely only return if it does so in Debian, haven't seen any movement there


Mind you MPlayer development itself has been more than a little slow these days, I hope it is not sliding into retirement...

---

### Post by mc4man on 2014-12-06
> **andrew.46 said:**
> Mind you MPlayer development itself has been more than a little slow these days, I hope it is not sliding into retirement...
Noticed that myself.. Though I still think it's quite useful & does have a great frontend in smplayer. I'd think many users do prefer gui's over cli so for that alone hope it continues on.
(- I  use mpv more here but for gui still on smplayer/mplayer. The only current frontend for mpv, baka-mplayer, still needs a lot of work though is useable

---

### Post by sudodus on 2014-12-08
> **andrew.46 said:**
> Great news for Ubuntu :)

+1 :-)

---

### Post by mc4man on 2014-12-08
When I filed bug on returning (probably would of without report) put up a demo to illustrate no issues ect.
Rather than get rid of have extended ffmpeg slightly (fuller aac encoding support) & added some examples of sources using.
(- the current mpv in vivid has to me a questionable recommend of youtube-dl package, left in place for the moment
The baka frontend to mpv is 0.2 release (have git master packaged in 14.04, will replace this one  in near future
cmus has full ffmpeg support which libav can't currently provide
[https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1)

---

