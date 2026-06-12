---
title: "Repository or?"
date: 2005-05-10
forum: Repositories &amp; Backports
---

### Post by NoTiG on 2005-05-10
Do i have a problem with my REpositories ??? I have been following various howtos.. and often i CANNOT apt-get packages. FOr instance........ I have a broadcom wifi card so i needed ndiswrapper.. Following a howto i tryied

sudo apt-get install ndiswrapper-utils 
"couldn't find package"

I tried following the gdesklets howto...

sudo apt-get install gdesklets
"couldnt find package"

ALso another one was sudo apt-get install build-essentials 

 couldnt find.. and also
couldnt find tuxracer !!!! . I uncommented the lines in my /etc/apt/sources.list file... like the howto said . I can post my sources.list file. but my question is...... why are so many files not found?????????// is it because they have not made them yet for the 64 bit distribution????/

---

### Post by nemin on 2005-05-10
[QUOTE=NoTiG]Do i have a problem with my REpositories ??? I have been following various howtos.. and often i CANNOT apt-get packages.[/QUOTE]
When your sources.list looks like [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories), you should be able to get most ubuntu packages. Another tip, use ```
sudo apt-cache search <keyword>
```  to find the *exact* package name you have to use with apt-get.

---

### Post by NoTiG on 2005-05-10
TY nemin. I apparently was mistyping build-essentials. its build-essential. 

And even though i uncommented some lines from my sources.list... a couple lines were missing... i don't see why they made it different than on that how too. so i found tuxracer. However ndiswrapper....... is still missing in action..

---

### Post by az on 2005-05-10
ndiswrapper-utils

---

### Post by NoTiG on 2005-05-10
ndiswrapper-utils isnt in any of the repositories for 64 bit ............ unless my repositories are messed up which is what i was wondering in the first place. 

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted
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

---

