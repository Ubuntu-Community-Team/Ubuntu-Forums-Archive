---
title: "Post a clean sources.list file"
date: 2005-08-06
forum: Repositories &amp; Backports
---

### Post by chapterthree on 2005-08-06
Hello All,

I'm thinking that my sources.list file may not be using the correct horay repositories, and was wondering if somebody could post a clean or current version of their sources.list file.

I have included mine below, maybe somebody can tell me if I need to make any modifications.

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

#deb ftp://ftp.nerim.net/debian-marillat stable main
#deb ftp://ftp.nerim.net/debian-marillat unstable main
#deb ftp://ftp.nerim.net/debian-marillat testing main

#deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
#deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by varunus on 2005-08-06
Yours looks OK to me.  Don't use Marillat unless you absolutely have to though...Instead of using Marillat, use Hoary-extras (almost the same packages, but designed for hoary so no breakage) as you seem to be doing.

I think you can also add a hoary-security line for multiverse.

---

### Post by Ubunted on 2005-08-06
```
## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

deb [http://ftp2.caliu.info/backports](http://ftp2.caliu.info/backports) hoary-backports main universe multiverse restricted
deb [http://ftp2.caliu.info/backports](http://ftp2.caliu.info/backports) hoary-extras main universe multiverse restricted
```

This is mine. I keep the unofficial backport repos in there "just in case". I'll probably remove them once the official backports project gets fully up to speed.

---

### Post by TravisNewman on 2005-08-07
main, restricted, universe, and multiverse can all go on the same line, just so you know.

---

### Post by pranith on 2005-08-07
I am also using the same sources.list file.......but i am not able to update nethin   :mad: 

 :sad:   :cry:  errors like these are appearing in Synaptic:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libltdl3_1.5.6-5_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libtool/libltdl3_1.5.6-5_i386.deb)
  Temporary failure resolving 'us.archive.ubuntu.com'

for every package.... :cry:

---

### Post by Ubunted on 2005-08-07
[QUOTE=panickedthumb]main, restricted, universe, and multiverse can all go on the same line, just so you know.[/QUOTE]
 I know, just haven't bothered doing that yet. Why does it come that way anyway?

---

