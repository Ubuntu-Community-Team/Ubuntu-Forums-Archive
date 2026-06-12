---
title: "Gui on"
date: 2009-11-03
forum: Server Platforms
---

### Post by mudcow007 on 2009-11-03
hello all

im trying (in vain) to install a gui onto my brand spanking new install of 9.10

i have ran

```
sudo apt-get update
```

then

```
sudo get-apt install ubuntu-desktop
```

after about 2 hours of downloading it goes back to the command line prompt with the messages

```
Failed to fetch http://gb.archive.ubuntu.com/pool/main/x/xserver-org-video-v41/xserver-xorg-video-vmware_10.16.7-1_amd64.deb The HTTP server sent an invalid reply header [IP: 194.169.254.10 80]
```

there are quite a few of these and at the very bottom it states

```
Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

the machine is currently online and downloading updates, so its not an internet connectivity issue (i dont think)

any ideas!!?

thanks

---

### Post by mudcow007 on 2009-11-03
do you think it could be pointing at old repositories?

the error message i posted above, i cant find the software its looking for in 

[http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-v4l/](http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-v4l/)

?!?

---

### Post by mudcow007 on 2009-11-04
anyone!?

---

### Post by MrQuan on 2009-11-04
Well I'm a beginner, but sometimes when apt-get fails for whatever reason, aptitude works:...

```
sudo aptitude install ubuntu-desktop
```

---

### Post by mudcow007 on 2009-11-04
i think i have possibly sorted it my self

i think it was a firewall issue on my gateway

thanks for all the "help"

---

### Post by mudcow007 on 2009-11-04
nope sorry guys still not working it failed again with the messages 
Failed to fetch [http://gb.archive.ubuntu.com/pool/main/x/xserver-org-video-v41/xserver-xorg-video-vmware_10.16.7-1_amd64.deb](http://gb.archive.ubuntu.com/pool/main/x/xserver-org-video-v41/xserver-xorg-video-vmware_10.16.7-1_amd64.deb) The HTTP server sent an invalid reply header [IP: 194.169.254.10 80]

again

---

### Post by everdred on 2009-11-04
Though I'm not sure if this will help, it might help to paste the contents of your /etc/apt/sources.list to make sure they're pointing to the right place.

---

### Post by MrQuan on 2009-11-04
> **mudcow007 said:**
> thanks for all the "help"
Well, you've got three seperate threads about this issue with some "help" suggestions you haven't responded to yet.

---

### Post by wojox on 2009-11-04
You need to change servers.

---

### Post by wojox on 2009-11-04
You need to change servers. That link is broken. Try pointing to a different server.

---

### Post by mudcow007 on 2009-11-04
hi guys thanks for all the posts, i have been playing around with kubuntu. which installed fine?

i would prefer gnome though.

i will post up my sources file in a sec. thanks!
```

# 
# deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release amd64 (20091027.2)]/ karmic main restricted

#deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release amd64 (20091027.2)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse

```

---

### Post by mudcow007 on 2009-11-05
By the power of grayskull i have the power.....

Its working!!

it was the sources, i changed them from 

```
http://gb.archive.ubuntu.com
```

```
ftp://archive.ubuntu.com
```

now its all good....

---

