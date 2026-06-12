---
title: "Apt unable to satisfy some basic dependencies"
date: 2006-08-10
forum: Repositories &amp; Backports
---

### Post by montarotech on 2006-08-10
Hi,

apt is returning some unusual errors which I am not sure how to remedy:

this might be quite long
and sorry i didnt have the time to search for a fix on the forum, so if one has already been posted feel free just to point me in the direction of that thread.

```
montaro@volcano:~/Downloads/lazarus$ sudo apt-get install libgtk2.0-dev Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev but it is not going to be installed
E: Broken packages
```
ok so ill install those packages seperately?

```
montaro@volcano:~/Downloads/lazarus$ sudo apt-get install libgtk2.0-dev libcairo2-dev libxcursor-dev libxfixes-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.0.4-0ubuntu1) but 1.2.0-0ubuntu1quinn2 is to be installed
  libxfixes-dev: Depends: libxfixes3 (= 1:3.0.1.2-0ubuntu3) but 1:4.0-0ubuntu1 is to be installed
E: Broken packages
```
ok so ill try to satisfy those manually with:

# sudo apt-get install libgtk2.0-dev libcairo2-dev libxcursor-dev libxfixes-dev libcairo2 libxfixes3

but this returns the same values as errors as above, except stating that libcairo2 and libxfixes3 is already installed.

i've done an apt-get update, and an apt-get dist-upgrade. im all up-to-date according to that.

any ideas?
ill also provide some details of my sources.list

```
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main
deb http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper restricted
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe
deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main
deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted
deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe
deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main
deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe
deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

thanks in advance.

regards,

montaro.

---

### Post by montarotech on 2006-08-11
anyone have any ideas??

---

### Post by az on 2006-08-11
Do you have mixed repositories (two different ubuntu versions or debian and Ubuntu epos at the same time?)  If so, that's your problem.

---

### Post by shunthemask on 2006-08-26
montarotech, did you find a resolution to this problem?  I am getting the exact same problem.  I don't think that I have different versions of the repos.

```
$ sudo apt-get install libgtk2.0-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
E: Broken packages

```

sources.list:
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 

##COMPIZ
deb http://xgl.compiz.info/ dapper main 
deb-src http://xgl.compiz.info/ dapper main 
deb http://ubuntu.compiz.net/ dapper main 
deb-src http://ubuntu.compiz.net/ dapper main 

## UBUNTU SECURITY UPDATES
deb http://us.archive.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse

## dapper-commercial by Canonical
deb http://archive.canonical.com/ubuntu/ dapper-commercial main 
deb-src http://archive.canonical.com/ubuntu/ dapper-commercial main

## PLF REPOSITORY
deb http://packages.freecontrib.org/plf/ dapper free non-free 
deb-src http://packages.freecontrib.org/plf/ dapper free non-free 

## WINE
deb http://wine.budgetdedicated.com/apt/ dapper main 
deb-src http://wine.budgetdedicated.com/apt/ dapper main 



deb http://www.getautomatix.com/apt dapper main

```

thanks

---

### Post by noxel on 2006-08-26
I have the same problem.

> The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
E: Broken packages

Anyone have a solution?

---

### Post by noxel on 2006-08-27
bump.

---

### Post by rupy on 2006-08-27
I had this on my other pc, and I eventually just gave up and fixed it by removing libcairo2 along with half of kde. Now I have it on this pc and I am seriously contemplating doing the same if I can't find a solution.

---

### Post by rupy on 2006-08-27
I figured it out.

I think the compiz repo was supplying a version of libcairo2 without supplying libcairo2-dev. The libcairo2-dev package supplied by the Ubuntu repo's was older. To fix all I did was:

1) Run synaptic package manager
2) search for libcairo2
3) select libcairo2 and go to package > force version, select the older version that matches libcairo2-dev
4) hit apply

You now should be able to install whatever you need that has (non/reverse) depends on libcairo2 :)

---

### Post by noxel on 2006-08-27
Alright, however i can't install libcairo2-dev because i'm getting this error:

> libcairo2-dev:
 Depends: libfontconfig1-dev but it is not going to be installed
 Depends: libfreetype6-dev but it is not going to be installed

if i try to get libfontconfig1-dev i get this error:
> libfontconfig1-dev:
 Depends: libfreetype6-dev but it is not going to be installed

if i try getting libfreetype6-dev i get:
> libfreetype6-dev:
  Depends: libfreetype6 (=2.1.10-1ubuntu2.2) but 2.2.1-0ubuntu1 is to be installed

libfreetype6 version is 2.2.1-0ubuntu1, libfreetype6-dev latest version is 2.1.10-1ubuntu2.2

If i try to force version on libfreetype6 then it will try to remove alot of programs..

Anyway to get around this?

---

### Post by noxel on 2006-08-27
^^ bump. Does anyone know a solution for this? Thanks.

---

### Post by shunthemask on 2006-08-27
Hey noxel, 

do you have compiz installed?  I think that this is the root cause of my problem because I installed it because it looks pretty and such, but I don't use it because it only works ok for me.  I am in the process of removing compiz and trying to straighten everything out.  Soon as that happens, I shall post her up here.

---

### Post by shunthemask on 2006-08-27
noxel, check it out:

Hey rupy, thanks for the help, this worked great for me.  I just had to use this same process for libfontconfig1-dev and libfreetype6-dev, respectively setting them back to dapper and dapper-security.  I then did my 
```
sudo apt-get install libgtk2.0-dev python-gtk2-dev
```
and she ran without a hitch.

I also got rid of compiz in synaptic and took the repos out of my sources.list so hopefully i won't run into this problem again.

> **rupy said:**
> I figured it out.

I think the compiz repo was supplying a version of libcairo2 without supplying libcairo2-dev. The libcairo2-dev package supplied by the Ubuntu repo's was older. To fix all I did was:

1) Run synaptic package manager
2) search for libcairo2
3) select libcairo2 and go to package > force version, select the older version that matches libcairo2-dev
4) hit apply

You now should be able to install whatever you need that has (non/reverse) depends on libcairo2 :)

> **noxel said:**
> Alright, however i can't install libcairo2-dev because i'm getting this error:



if i try to get libfontconfig1-dev i get this error:


if i try getting libfreetype6-dev i get:


libfreetype6 version is 2.2.1-0ubuntu1, libfreetype6-dev latest version is 2.1.10-1ubuntu2.2

If i try to force version on libfreetype6 then it will try to remove alot of programs..

Anyway to get around this?

---

### Post by rupy on 2006-08-27
what version of libcairo2 do you have installed noxel? Did you try forcing it to a lower version, I think it was 1.0.4-0ubuntu1?

---

### Post by shunthemask on 2006-08-27
> **noxel said:**
> libfreetype6 version is 2.2.1-0ubuntu1, libfreetype6-dev latest version is 2.1.10-1ubuntu2.2

If i try to force version on libfreetype6 then it will try to remove alot of programs.

just out of curiousity, which packages does synaptic say it's going to remove?

---

### Post by noxel on 2006-08-27
It tries to remove a bunch of things:

ubuntu-desktop
update-manager
gnome-terminal
synaptic
anjuta
update-notifier
gnome-app-install

and a few others.

And yes, i am running Compiz.

@shaunthemask -- can you explain your solution a little more clearly? I'm not  really sure what you did to fix it. Did you force the version and have to remove a bunch of things?

---

### Post by shunthemask on 2006-08-27
> **noxel said:**
> 
@shaunthemask -- can you explain your solution a little more clearly? I'm not  really sure what you did to fix it. Did you force the version and have to remove a bunch of things?
noxel, first thing's first, do you wish to continue using compiz?  Because if you do, then what I did really won't help you and I don't think that I can be of much help other than pointing you to the compiz forums:
[http://www.compiz.net/](http://www.compiz.net/)

Past that, i didn't realize that I was getting myself into the middle of a bunch of version inconsistencies - synaptic wasn't so verbose with me.  A little back story here: I'm sort of new to linux and I haven't used anything unix like in at least 5 years and I have this tendency to try everything whenever I get a new app or os and I end up breaking and fixing and breaking and fixing.  Not too bad a way to learn, but it takes a bit of time.  Anyhow, this is what I did --

> **rupy said:**
> I figured it out.

I think the compiz repo was supplying a version of libcairo2 without supplying libcairo2-dev. The libcairo2-dev package supplied by the Ubuntu repo's was older. To fix all I did was:

1) Run synaptic package manager
2) search for libcairo2
3) select libcairo2 and go to package > force version, select the older version that matches libcairo2-dev
4) hit apply

You now should be able to install whatever you need that has (non/reverse) depends on libcairo2 :)
I followed rupy's instructions here, and then I forced the versions of libfontconfig1-dev and libfreetype6-dev (i set libcairo2 to dapper, libfontconfig1-dev to dapper and libfreetype6-dev to dapper-security).

Then, I went into synaptic and selected compiz. compiz-gnome, compiz-plugins and libcm7 and marked them for removal and applied the changes. I wish that synaptic had told me that all of those things had to removed with it, would have saved me some trouble and research.

Then, I commented out the compiz repos in my /etc/apt/sources.list:
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted multiverse universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse 
#deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
#deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 

##COMPIZ
#deb http://xgl.compiz.info/ dapper main 
#deb-src http://xgl.compiz.info/ dapper main 
#deb http://ubuntu.compiz.net/ dapper main 
#deb-src http://ubuntu.compiz.net/ dapper main 

## UBUNTU SECURITY UPDATES
deb http://us.archive.ubuntu.com/ubuntu/ dapper-security main restricted universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-security main restricted universe

## dapper-commercial by Canonical
deb http://archive.canonical.com/ubuntu/ dapper-commercial main 
#deb-src http://archive.canonical.com/ubuntu/ dapper-commercial main

## PLF REPOSITORY
deb http://packages.freecontrib.org/plf/ dapper free non-free 
#deb-src http://packages.freecontrib.org/plf/ dapper free non-free 

## WINE
deb http://wine.budgetdedicated.com/apt/ dapper main 
#deb-src http://wine.budgetdedicated.com/apt/ dapper main 

deb http://www.getautomatix.com/apt dapper main

```

To get the terminal and synaptic working again:
```
sudo apt-get install gnome-terminal-data/dapper-updates gnome-terminal/dapper-updates libvte4/dapper-updates libvte-common/dapper-updates synaptic/dapper
```

Since I've seen your post, I went and looked in synaptic to see if I had those packages installed which you said were to be removed, and they weren't there, but now that synaptic is back up and running, I am not all that worried that I'll have unmet dependencies since I have a nice friendly ui to play around with.

My problem is that I don't remember exactly how I installed compiz, or more appropiately, I installed it half way and then found a better way to do it.    Thus, I am not so sure how to backtrack the steps and further, I am not sure what was overwritten with new versions.

Personally, if i fubar things a little, I don't mind because I am just messing around with the distribution and trying to get everything solid before I wipe the system and do a complete reinstall with a source compile and compile all of the applications that I use often.  Right now I am just in the learning phase.

Hope that this ramble has helped.;)

---

### Post by shunthemask on 2006-08-30
noxel, you have any luck?

---

### Post by shunthemask on 2006-09-02
Even better, here is a collection of all of the libraries that compiz updates, and if you have a version mismatch with the -dev libraries, you can download them here:
[http://xgl.compiz.info/]("http://xgl.compiz.info/")

---

### Post by stoanhart on 2006-10-09
> **noxel said:**
> ^^ bump. Does anyone know a solution for this? Thanks.

Woohoo! I've had this problem for a long time. I tried a million different things, and I finally found a (very simple) solution. 

[http://www.hermies.net/downloads/libfreetype6-dev_2.2.1-0.1ubuntu1_i386.deb](http://www.hermies.net/downloads/libfreetype6-dev_2.2.1-0.1ubuntu1_i386.deb)

That's the dev package you need to go with libfreetype6_2.2.1-0. 

I still have no idea what repository this fscking package came from, but at least someone has hosted the right dev package. This solved all my problems!

Enjoy :D

---

### Post by rupy on 2006-10-09
Yeah pretty annoying... Suppose thats the price for living on the (bleeding) edge :D

---

