---
title: "Where to find gstreamer-faad?"
date: 2005-07-05
forum: Repositories &amp; Backports
---

### Post by aCiD2 on 2005-07-05
Hi,

I understand that this is covered on ubuntuguide.org - but for some strange reason I cant access that site. I've searched around but I can't find any apt repositories that contain gstreamer-faad. Could anyone please explain what I need to add to my sources.list to get gstreamer-faad?

Thanks!
aCiD2.

---

### Post by codejunkie on 2005-07-05
your /etc/apt/sources.list file should look something like this plus you'll have the entry for your cdrom at the top you should leave it alone and you can just replace the rest with this hope it helps.
and to answer your questions i think it's in the universe repo not sure though but this should fix it anyway.
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

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

---

### Post by aCiD2 on 2005-07-05
I cleared the contents of my sources.list (except the cd entry) and pasted what you said in. I then ran "sudo apt-get update" and then "sudo apt-get install gstreamer-faad" seems it cant find it :(

```
acid2@iridescent:~$ sudo apt-get install gstreamer-faad
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer-faad
```

Any ideas?

---

### Post by aCiD2 on 2005-07-05
Whoops, gstreamer0.8-faad :P There we go! Thank you!

---

