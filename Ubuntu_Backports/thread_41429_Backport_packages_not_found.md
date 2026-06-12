---
title: "Backport packages not found??"
date: 2005-06-13
forum: Ubuntu Backports
---

### Post by jsee06home on 2005-06-13
Hello and thank you for reading this. I am about the newest newbie of all when it comes to Ubuntu/Linux so please bear with me. 
I am trying to get my laptop set up to work well with Ubuntu because I really enjoy working with it so far. 

The issue I am having, is I have searched for hours trying to figure out how to install a few things. I just read up on how to update apt-get ([http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)) to work with backports by editing the /etc/apt/sources.list file, but when I go to update the apt-get list (sudo apt-get update), it never finds any new packages. so if i type in a terminal window apt-get install smeg, it replies back with E: Couldnt find package smeg. Or another example that I am worried about mostly, is installing the firefox 1.0.4.. so I can update my extensions to get flash player to work.. I get the same error as well when trying to install.

As far as hardware goes, I am using an HP ZV5000 series (5430us) laptop with Hoary installed, and this is the Amd64 installed version of Ubuntu. 

Please when replying speak like I am in 2nd grade literally with command line input, as I am a pretty good avid user with the Windows world, but I am trying to lean into Linux. Any help is REALLY appreciated! Thank you! ](*,)

---

### Post by CAE on 2005-06-13
Could you post the contents of the sources.list?

---

### Post by JeffcS on 2005-06-16
I get a similar error messege

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplayer-mozilla

here is my sources list:

 b cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by dlpfmVfH on 2005-06-16
it doesn't matter, I started the same way as you did...
didn't know anything...

for the extra repositories...type the following in console (terminal) 
sudo gedit /etc/apt/sources.list or
sudo kate /etc/apt/sources.list (if you're using kubuntu)

then copy the lines you want...:
 [HTML]
## UBUNTU MAIN
deb http://nl.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu hoary main restricted

deb http://nl.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu hoary-updates main restricted

## UBUNTU UNIVERSE
deb http://nl.archive.ubuntu.com/ubuntu hoary universe
deb-src http://nl.archive.ubuntu.com/ubuntu hoary universe

## UBUNTU SECURITY
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security universe multiverse

## UBUNTU MULTIVERSE
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## UBUNTU BACKPORTS MIRRORS
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports-staging main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-extras-staging main universe multiverse restricted

or

deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

## ENLIGHTENMENT
deb http://ubuntu.nooms.de/ hoary/
 
## XFCE4
deb http://www.os-works.com/debian testing main
deb-src http://www.os-works.com/debian testing main
[/HTML] 

as you can see...I'm from the netherlands..that's the nl part the ubuntu lines..
you can change that with the ones from your sources.list...

If you have more questions..just ask..!

:)

smeg is a totally different project, not in the repositories...

You have to download the deb file yourself...

then go to console / terminal:

sudo dpkg -i (the file you downloaded).deb 

press enter...and if al goes well.. it says installed...

as for the other files...I find synaptic...very usefull
searching packages..and a little documentation with it...

O:)

---

### Post by jdong on 2005-06-16
FYI, Smeg is in Backports repos because it entered Breezy.


Can you please switch to the caliu or mirrormax mirrors? Planetmirror's known to be out of sync. We've contacted them, and they should be back on the ball soon.

---

### Post by sakke on 2005-06-23
I am having the same problem. I am also quite new to Ubuntu (and Linux at general).

I tried to install Flash player plugin for Firefox. I have read [Ubuntuguide](http://www.ubuntuguide.org/#flash-mozilla) and added extra repositories.

The backports part of my sources.list is currently
> 
## Backports
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted 
 

I have tried other mirrors also, but it didn't help.

The first time I sudoed "apt-get update" I had error
> W: Duplicate sources.list entry [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-backports/main Packa ges (/var/lib/apt/lists/ftp2.caliu.info_backports_dists_hoary-backports_main_bin ary-i386_Packages)

but when I run apt-get update the second time, everything went fine.

Now I finally try sudo apt-get install flashplayer-mozilla (like Ubuntuguide says) but it doesn't work. I am using Finnish language, but in English it says something like "the package flashplayer-mozilla was not found"

I have tried it quite many times with different mirrors. I must be doing something wrong, but I can't find out what.

(edit: "apt get" -> "apt-get")

---

### Post by jdong on 2005-06-23
[QUOTE=sakke]
Now I finally try sudo apt-get install flashplayer-mozilla (like Ubuntuguide says) but it doesn't work. I am using Finnish language, but in English it says something like "the package flashplayer-mozilla was not found"[/QUOTE]

Flashplayer is a part of the official Ubuntu repositories,in Universe.

Go back to the guide, and copy-paste their Extra Repositories sources.list file; it has everything you need.

---

### Post by sakke on 2005-06-24
Thanks for helping, now I found it and learnt also something new.

---

