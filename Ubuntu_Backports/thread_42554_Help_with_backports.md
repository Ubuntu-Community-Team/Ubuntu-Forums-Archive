---
title: "Help with backports"
date: 2005-06-18
forum: Ubuntu Backports
---

### Post by speedsix on 2005-06-18
Hi,

I have added the extra repositories as per the Ubuntu Guide but when I search for speciic packages liste in the guide via Synaptic, nothing turns up.

For example Azureus and the Java 1.5 sdk?

What am I doing wrong?

64bit Hoary btw


many thanks

---

### Post by AndyAWS on 2005-06-18
Did you 'Reload Package Information' under the 'edit' menu?

---

### Post by fluideye on 2005-06-18
# sudo apt-get update

What do you have in /etc/apt/sources.list ?

---

### Post by speedsix on 2005-06-18
Hi my sources.lst file is as follows


```
deb-src http://gb.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://gb.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu hoary main restricted

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

Thanks

---

### Post by speedsix on 2005-06-18
Sorry, when I say 'nothing' turns up I mean not the specific backport packages like the jsdk, the regular stuff from the main ubuntu servers is there.

---

### Post by fluideye on 2005-06-18
Are you getting any "failed to fetch errors" when you sudo apt-get update?

If you are on a fresh install you may want to try this script, it worked well for me

[http://ubuntuforums.org/showthread.php?t=22646&highlight=automatic+script](http://ubuntuforums.org/showthread.php?t=22646&highlight=automatic+script)

---

### Post by Majlo on 2005-06-18
[QUOTE=speedsix]Hi,

I have added the extra repositories as per the Ubuntu Guide but when I search for speciic packages liste in the guide via Synaptic, nothing turns up.

For example Azureus and the Java 1.5 sdk?

What am I doing wrong?

64bit Hoary btw


many thanks[/QUOTE]

Azureus , j2re is not in Backport repo for architecture amd64 

See
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-amd64/](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-amd64/)

But for i386 is it
[http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/)

---

### Post by fluideye on 2005-06-18
oops, overlooked amd64, thanks Majlo

---

