---
title: "Firefox update"
date: 2005-05-01
forum: Repositories &amp; Backports
---

### Post by samppi on 2005-05-01
I currently have Firefox 1.0.2 (which came with Ubuntu Hoary). However, a new version (1.0.3) *is* available from mozilla.org. However, Synaptic says it's up-to-date, and no higher version is available. (I've reloaded package information.) Does this mean that something is broken? Can I install Firefox 1.0.3 without screwing up Synaptic?

---

### Post by XDevHald on 2005-05-01
[QUOTE=samppi]I currently have Firefox 1.0.2 (which came with Ubuntu Hoary). However, a new version (1.0.3) *is* available from mozilla.org. However, Synaptic says it's up-to-date, and no higher version is available. (I've reloaded package information.) Does this mean that something is broken? Can I install Firefox 1.0.3 without screwing up Synaptic?[/QUOTE]


Deffinently not a problem, you can grab it either from the mozilla.org mirror, or you can get it from our backports, [http://backports.ubuntuforums.org]("http://backports.ubuntuforums.org")

Be sure to get the right sources deb, such as Hoary or Warty :)

To get the deb ftp:// in your update manager, you'll need to **sudo gedit /etc/apt/sources.list **and add the deb ftp link to the bottom of the sources.list page :)

Just a nother quick note while I am editing this post, be sure to change the deb link where it says **hoary **to **warty **on both links if you're running warty.

---

### Post by arnieboy on 2005-05-01
[QUOTE=samppi]I currently have Firefox 1.0.2 (which came with Ubuntu Hoary). However, a new version (1.0.3) *is* available from mozilla.org. However, Synaptic says it's up-to-date, and no higher version is available. (I've reloaded package information.) Does this mean that something is broken? Can I install Firefox 1.0.3 without screwing up Synaptic?[/QUOTE]
 go to terminal and type the following:
sudo gedit /etc/apt/sources.list

when the file in question opens up, delete everything thats there in it and paste the following:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


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
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
## deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

DONT COPY FROM THIS LINE ONWARDS

After that save and close the file and type the following two lines in terminal one after the other (pressing enter after each)

sudo gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907

sudo gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907

Thats it u are done. now u will see all updates including firefox showing when u do a
sudo apt-get update

Please add to my reputation after u are done.

Thanks

---

### Post by XDevHald on 2005-05-01
In order for this key to actually work, you'll need to add it.

gpg --armor --export 1F41B907 | sudo apt-key add -

Hit enter and it will Say **OK **when completed, then do the **sudo apt-get update**

---

### Post by arnieboy on 2005-05-01
[QUOTE=BB]In order for this key to actually work, you'll need to add it.

gpg --armor --export 1F41B907 | sudo apt-key add -

Hit enter and it will Say **OK **when completed, then do the **sudo apt-get update**[/QUOTE]
 BB,
    yes, I had intended to add the line which u mentioned but mistakenly typed the import line twice. Thanks for the correction.
-arnieboy

---

### Post by momo66 on 2005-05-01
[QUOTE=samppi]I currently have Firefox 1.0.2 (which came with Ubuntu Hoary). However, a new version (1.0.3) *is* available from mozilla.org. However, Synaptic says it's up-to-date, and no higher version is available. (I've reloaded package information.) Does this mean that something is broken? Can I install Firefox 1.0.3 without screwing up Synaptic?[/QUOTE]
 I just updated mine through Synaptic to 1.03.  try it again

---

