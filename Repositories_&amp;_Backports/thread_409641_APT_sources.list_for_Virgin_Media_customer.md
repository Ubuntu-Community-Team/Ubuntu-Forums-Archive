---
title: "APT sources.list for Virgin Media customer"
date: 2007-04-14
forum: Repositories &amp; Backports
---

### Post by nicholas on 2007-04-14
I have a 10Mb line from Virgin Media (Soon to be 20Mb yay!) and have just discovered they have an Ubuntu mirror.

I changed my /etc/apt/sources.list to point at said mirror and am getting solid 1.17MB/s downloads. :-D

The mirror URL is [ftp://ubuntu.virginmedia.com/mirrors/ubuntu/archive/](ftp://ubuntu.virginmedia.com/mirrors/ubuntu/archive/)

Just replace the address for each deb or deb-src line in your sources.list and sudo apt-get update for it to take effect.

Below is my sources.list if anyone finds it useful. I am using Feisty but the mirror has previous versions of Ubuntu on there too.

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb ftp://ubuntu.virginmedia.com/mirrors/ubuntu/archive/ feisty main restricted
deb-src ftp://ubuntu.virginmedia.com/mirrors/ubuntu/archive/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb ftp://ubuntu.virginmedia.com/mirrors/ubuntu/archive/ feisty-updates main restricted
deb-src ftp://ubuntu.virginmedia.com/mirrors/ubuntu/archive/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb ftp://ubuntu.virginmedia.com/mirrors/ubuntu/archive/ feisty universe
deb-src ftp://ubuntu.virginmedia.com/mirrors/ubuntu/archive/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb ftp://ubuntu.virginmedia.com/mirrors/ubuntu/archive/ feisty multiverse
deb-src ftp://ubuntu.virginmedia.com/mirrors/ubuntu/archive/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb ftp://ubuntu.virginmedia.com/mirrors/ubuntu/archive/ feisty-backports main restricted universe multiverse
# deb-src ftp://ubuntu.virginmedia.com/mirrors/ubuntu/archive/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

---

### Post by RyconPayne on 2007-04-19
Thank you very, very much.  Still timing out on security.ubuntu.com, but at least now everything else seems to work great.  Excellent.

---

### Post by willskills on 2007-04-19
Great, thanks very much nicholas :)

---

### Post by mkor on 2007-05-09
> **RyconPayne said:**
> Thank you very, very much.  Still timing out on security.ubuntu.com, but at least now everything else seems to work great.  Excellent.
"Still timing out"? Does it mean that there are problems when using the ubuntu repositories via Virgin Media? I'm thinking of getting broadband from them... Could you write if you have any problems with the connection?

---

### Post by redwaldmcmanus on 2008-01-03
awesome
i'm soon to be on Virgin Media, and i'm sure this'll be useful

---

### Post by caramelsoul on 2008-05-26
I am on Virgin Media and have been for a couple of years. I upgraded my broadband to the 10mbs as i use usenet (newshosting) and download quite a bit. The downloads were great during the day but they throttle it right down between 1600 and midnight. During the day i was getting the full 10mbs downloads but at night it came right down to 2mbs. I didnt feel this was satisfactory for the extra i was paying. So i got rid of the XL 10mbs package. Bit of a rip off if you ask me.

---

### Post by jmar71n on 2008-06-09
I've been using the virgin media repository for about 6 months now and have noticed that the repository is sometimes out of date, you can check this at launchpad.

[https://launchpad.net/ubuntu/+archivemirrors]("https://launchpad.net/ubuntu/+archivemirrors")

I have seen it at 3 weeks behind, but I don't think this matters too much because I am still getting the security updates direct from ubuntu.com as Nicholas suggests in his sources.list.

---

