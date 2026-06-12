---
title: "Adding Backports to Sources.list - Linux Newbie Pls Help"
date: 2005-08-05
forum: Ubuntu Backports
---

### Post by suma on 2005-08-05
Hey there...

I have (very) recently moved from windows to ubuntu linux. One of the first things I noticed about ubuntu was that it does not have out-of-the-box support for the mp3 codec. I was able to set up mp3 support for players with little trouble, however I have run into a little difficulty when trying enable mp3-ripping support.

I read elsewhere on the forums that support for mp3-ripping was enabled by a file called gstreamer0.8-lame, and that this file could be obtained from the backports repository.

When reading the repository faq on this site, I found the data to add to sources.list in order to set up apt-get to work with the backports: 

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

I added these lines to my sources.list file, but when I fired up Synaptic it caused many errors... Any help solving these issues would be greatly appreciated.

Cheers.
Suma



Synaptic output: 

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)






I don't know if it will help at all, but here is the rest of my sources.list file:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by heimo on 2005-08-05
With a quick look at the errors, I'd guess that you just need to refresh the package database. I think there's a button for that in synaptic, but I guess it should have done that automaticly too ( I don't use it )

You can type this on command line to do the same thing:
 ```
sudo apt-get update

```

---

### Post by suma on 2005-08-05
Cool. It worked. Thanks for the help.

---

### Post by andhraandroid on 2005-10-16
Hi,
    I had the same problem with the backports in hoary I have since updated to Breezy and the problem followed me. I get the following error.
 W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

this is after running apt-get update in root. I read on some site that for breezy you have to change the hoary to breezy in backport repositories, but that produced the same error. Could someone please help me. 
This is my  repositories file :-
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Backports
 deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
 deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


Thanks

---

### Post by Jonathan2007 on 2005-10-16
Well first off there are no backport servers for Breezy as it is very up to date seeing as how it just came out a couple of days ago.

Second if you are still using Hoary and are going to stay on it, you should read [this]("http://ubuntuforums.org/showthread.php?t=69681") thread about the mirrormax servers being shutdown and read [this]("http://ubuntuforums.org/showthread.php?t=52168") thread about new official repositories for Hoary.

---

### Post by dcstar on 2005-10-19
[QUOTE=Jonathan2007]Well first off there are no backport servers for Breezy as it is very up to date seeing as how it just came out a couple of days ago.

Second if you are still using Hoary and are going to stay on it, you should read [this]("http://ubuntuforums.org/showthread.php?t=69681") thread about the mirrormax servers being shutdown and read [this]("http://ubuntuforums.org/showthread.php?t=52168") thread about new official repositories for Hoary.[/QUOTE]

Yep, in other words ignore the **still incorrect** instructions for using Backports in the Hoary Ubuntuguide, and use the correct ones that for a "newbie", are still hard to find!

---

### Post by jdong on 2005-10-19
[QUOTE=dcstar]Yep, in other words ignore the **still incorrect** instructions for using Backports in the Hoary Ubuntuguide, and use the correct ones that for a "newbie", are still hard to find![/QUOTE]

Attempt to contact the maintainer of the guide has already been attempted by multiple users here...

---

### Post by heimo on 2005-10-19
[quote=jdong]Attempt to contact the maintainer of the guide has already been attempted by multiple users here...[/quote] Ubuntuguide.org? Here's discussion about it:
[http://ubuntuforums.org/showthread.php?t=77704]("http://ubuntuforums.org/showthread.php?t=77704")

Here's aysiu's instructions how to add extra repositories:
[http://www.psychocats.net/sources.html]("http://www.psychocats.net/sources.html")

---

### Post by jdong on 2005-10-19
[QUOTE=heimo]Ubuntuguide.org? Here's discussion about it:
[http://ubuntuforums.org/showthread.php?t=77704]("http://ubuntuforums.org/showthread.php?t=77704")

Here's aysiu's instructions how to add extra repositories:
[http://www.psychocats.net/sources.html]("http://www.psychocats.net/sources.html")[/QUOTE]
aha, I wasn't aware of that...

---

