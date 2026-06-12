---
title: "playing Xvid ?"
date: 2006-09-14
forum: Sun Sparc Users
---

### Post by kmantronix on 2006-09-14
Does anyone know if packages are available for playing xvid on ubuntu sparc ?

Thanks,

---

### Post by kazuya on 2006-09-14
That is a good question. The architectures are different. Can you play regular avi, mpeg4, or even wmv files right now? I would have suggested automatix, as it helps install all the media codecs you could possible ever use. 

One suggestion would be for you to install vlc after enabling multiverse repo from synaptic, reloading, and installing vlc. when you install vlc it tends to enable playback of all file formats.. Not too sure.

The package name may be wxvlc. Try it or go the automatix way, through this link:

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

Automatix helps you install flash, and many more media related stuff with ease. You occassionally have to enter in your password when prompted to continue the process..

Hope that helps.

---

### Post by kmantronix on 2006-09-14
I would prefer the vlc solution, but looks like there is no vlc package even with  multiverse set 

$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc


below my sources.list contents :

deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by kmantronix on 2006-09-14
forget my last reply... 

I forgot to do the :

$sudo apt-get update 

after modifying /etc/apt/sources.list

---

### Post by kmantronix on 2006-09-15
I did install vlc yesterday, but there is no plugin built in it to play xvid.
I alos tried to download automatix but there is no packages available for ubuntu sparc.

So no progress for now ... 

Any other idea ? :confused:

---

### Post by kmantronix on 2006-09-20
finally solved by installing mplayer ! :p 
xvid OK !
.mov OK !

---

