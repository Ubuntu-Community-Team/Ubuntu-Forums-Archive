---
title: "movie player and smplayer not working"
date: 2012-02-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rbrick49 on 2012-02-11
movieplayer just crashes when I launch it and smplayer just wont work it loads but wont load video and also vlc is the same,movieplayer and vlc crash the computer and send it back to login screen

---

### Post by redcylon on 2012-02-11
> **rbrick49 said:**
> movieplayer just crashes when I launch it and smplayer just wont work it loads but wont load video and also vlc is the same,movieplayer and vlc crash the computer and send it back to login screen

Do you use proprietary graphic driver? If you do revert/unistall it.

---

### Post by effenberg0x0 on 2012-02-11
> **redcylon said:**
> Do you use proprietary graphic driver? If you do revert/unistall it.

Why? smplayer, vlc and other players work perfectly for me, also including working vdpau on proprietary NVidia drivers 295.17. 

EDIT: In fact, I have 3 instances of xbmc running 1080p video with NVidia 295.17 (2 instances) and 290.10 (one instance) right now. Just tested my desktop with 3.2.0-15 and 295.17 and it worked too.

The problem of the original post is that he hasn't mentioned VGA brand, what driver he's using, what kernel, 32 or 64, if it worked before update, if hes fully updated, how did he install the drivers, nothing. So it's impossible to use that info to help him.

---

### Post by rbrick49 on 2012-02-11
well thanks for the replies first reply from redcylon its an amd system 64 bit with a 6950 radeon amd card I did not install propietry driver as for effenberg0x0 reply 64 bit system all amd and as I said 6950 amd graphics card cayman is its name
thanks folks for the help

---

### Post by rbrick49 on 2012-02-11
> **redcylon said:**
> Do you use proprietary graphic driver? If you do revert/unistall it.yes you were right I did some checking fglrx was installed sort of it said something about updates so I purged and reinstalled mesa all good now
thank you

---

### Post by andrek on 2012-02-13
Um, yeah, is there any bug report on this? Removing fglrx and going back to opensource drivers isn't a way to fix it (especially for laptop users who need proper power management which opensource driver does not have).

Trying to watch any movie in vlc or totem causes xserver to crash and reload...

---

