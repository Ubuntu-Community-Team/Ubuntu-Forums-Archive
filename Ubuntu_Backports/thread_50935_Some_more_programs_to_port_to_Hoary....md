---
title: "Some more programs to port to Hoary..."
date: 2005-07-21
forum: Ubuntu Backports
---

### Post by vvlist on 2005-07-21
I realize that some of these might be difficult due to their dependancies, but I thought I should list them just in case:
GAIM 1.4.0
GQView 2.1.0 or higher
gDesklets 0.35.2 or higher
NVU 1.0
a recent kismet
WiFi Radar 1.9.4
MPlayer
Drivel 2.0 or higher
a Ceemedia that works
Latest Evince
Latest Goumet Recipe Manager
a recent Leafpad
Newest Evolution
Inkscape 0.41
future: sonance!
Excuse me if any of these are available, or near available, I just believe these are great programs. Thanks for your time.

---

### Post by jasmuz on 2005-07-21
Most of the program listed by you are already available in the Ubuntu Backports servers.

---

### Post by vvlist on 2005-07-22
Hello again. I don't know what's wrong then. When I use synaptic, (I did apt-get upgrade, and apt-get update too) it says these versions are available:
gaim: backports-1.3.1 (current-1.40)
gqview: backports-1.4.5 (current-2.0.1)
gDesklets: backports-0.34.3 (current-0.35.2)
NVU: backports-1.0pre (current-1.0)
kismet: backports-2004.04.R1 (current-2005.06.R1)
WiFi Radar: backports- non-existant (current-1.9.4)
Drivel: backports-1.2.3 (current-2.0.2)
Evince: backports-0.1.9 (current-0.3.2)
Goumet Recipe Manager: backports- non-existant (current-0.8.5.4)
Leafpad: backports-0.8.1 (current 0.8.2)
Inkscape: backports-0.40 (current-0.41)

Are these numbers correct, or am I using the wrong repository?
This is my sources.list:
 deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


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
deb-src [http://security.ubuntu.om/ubuntu](http://security.ubuntu.om/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Backports

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-backports main universe multiverse restricted
deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-extras main universe multiverse restricted

Is my sources.list be wrong? Or am I expecting more than I should from backports? Thanks for your trouble.

---

### Post by GTvulse on 2005-07-22
Most of those programs are in the staging repositories. That is, they are not deemed proper for wide distribution because they have not been tested well enough. But being in the staging repos, most people don't know how to get at them and test them. A classic catch-22 if you tell me. Anyway, these are the repositories you need to add to apt/K/Synaptic:

```

## Staging Backports

deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

# Only use one mirror, don't waste resources others may need.
#deb http://acm.cs.umn.edu/ubp/ hoary-backports-staging main universe multiverse restricted
#deb http://acm.cs.umn.edu/ubp/ hoary-extras-staging main universe multiverse restricted

```

Big warning, if you have trouble, your computer bursts in flames, you lose your hair overnight, whatever. Don't complain: **file a bug report instead**.

---

### Post by Kyral on 2005-07-22
Eh, don't worry. I'm using Backports-Staging and everything is a-ok

---

### Post by vvlist on 2005-07-22
Thanks a lot, I'll change my sources.list immediately! :smile:

---

### Post by vvlist on 2005-07-22
Wow! This is great, thanks a bunch you guys!

---

### Post by GTvulse on 2005-07-22
[QUOTE=Kyral]Eh, don't worry. I'm using Backports-Staging and everything is a-ok[/QUOTE]

Nah! That was a standard disclaimer. Better than a MS EULA. ;-)

---

### Post by Malakin on 2005-07-26
I'm not seeing gqview 2.1x anywhere, am I missing something or it not available in a binary for Hoary anywhere yet?

2.1 has some fast thumbnail code that I can't really live without.

---

### Post by jdong on 2005-07-26
Let's take a look, one-by-one:
[QUOTE=vvlist]I realize that some of these might be difficult due to their dependancies, but I thought I should list them just in case:
GAIM 1.4.0
[/quote]
jdong@delta:~$ apt-cache show gaim
Package: gaim
Version: 1:1.4.0-1ubuntu1~5.04ubp1

Already there and in stable

> 
GQView 2.1.0 or higher

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=gqview](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=gqview)
2.0.0 is latest Breezy version

> 
gDesklets 0.35.2 or higher

Backporting gdesklets... I've done that twice, and both turned out to be trashy builds. I've given up on it.

> 
NVU 1.0

[http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=0&exact=1&arch=any&releases=all&case=insensitive&keywords=nvu&searchon=names](http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=0&exact=1&arch=any&releases=all&case=insensitive&keywords=nvu&searchon=names)

0.99+1.0pre-1 is still the latest in Breezy
> 
a recent kismet

[http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=0&exact=1&arch=any&releases=all&case=insensitive&keywords=kismet&searchon=names](http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=0&exact=1&arch=any&releases=all&case=insensitive&keywords=kismet&searchon=names)
Is the listed Breezy version OK?

> 
WiFi Radar 1.9.4

What's the Ubuntu package name?

> 
MPlayer

A pain to compile with deps

> 
Drivel 2.0 or higher

root@delta:~# apt-cache show drivel | grep ubp
Version: 2.0.1-1~5.04ubp1
Filename: dists/hoary-backports/universe/binary-i386/drivel_2.0.1-1~5.04ubp1_i386.deb

Already in Backports

> 
a Ceemedia that works

Umm... Ubuntu package name?

> 
Latest Evince

Doesn't compile on Hoary without bringing in a ton of libraries.

> 
Latest Goumet Recipe Manager

Ubuntu package name
> 
a recent Leafpad

0.8.1-1 in Backports

> 
Newest Evolution

Dependencies and bug testing

> 
Inkscape 0.41

[http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=0&exact=1&arch=any&releases=all&case=insensitive&keywords=inkscape&searchon=names](http://packages.ubuntu.com/cgi-bin//search_packages.pl?version=all&subword=0&exact=1&arch=any&releases=all&case=insensitive&keywords=inkscape&searchon=names)

**ACCEPTED** 0.41

Nice shotgun approach :) You hit 1 :)

---

### Post by jdong on 2005-07-26
Err, Inkscape needs a newer libgc from Breezy, so it's not backportable either.

---

### Post by vvlist on 2005-07-27
Thank you very much jdong, I got it all figured out. I mangled my sources.list, so nothing was showing up, my fault. Thanks though, I have everything plus I found a better program than ceemedia called Griffith, well at least I think it is.

---

### Post by Cybolic on 2005-07-31
CeeMedia has an Ubuntu/Debian package available for [download at SourceForge](http://sourceforge.net/project/showfiles.php?group_id=130791).
I use this myself on my Ubuntu system, so there shouldn't be any problem in getting it to work.

If you have any problems with CeeMedia or you really find Griffith to be better, I'd like to know about it so I can fix it.

Also, how does one get a package committed to Ubuntu?


Cheers,
Christian Storgaard

---

### Post by AgenT on 2005-07-31
If you want the newest Inkscape it is easy to get without it ever being available in a repository. First, uninstall your current version. Then go to the download page of Inkscape (this should be on sourceforge) and download the STATIC rpm file. Then type this in console:
 ```
alien your_rpmfile.rpm
``` 
This will create a deb file from the rpm. This deb file *does* work (tested by a few) and it needs *zero* dependencies because it is static (however, this makes it large and redundant). Now all you need to do is install the deb file using your console:
 ```
sudo dpkg -i your_new_debfile.deb
```

---

### Post by graabein on 2005-08-02
Gourmet Recipe Manager looks tasty! I could not find it in the repos but homepage and debs are [here](http://grecipe-manager.sourceforge.net/).

---

### Post by sabot4ge on 2005-08-02
put one more program in the list,
[COLOR=Red]gnomebaker 0.4[/COLOR]
breezy version is 0.3

check the changelog, it worthy the update.

---

### Post by Chandon on 2005-08-07
The version of kismet in warty is older than dirt. As far as I can tell, there's no version in breezy (or I'd just do that).

---

### Post by aledie on 2005-08-08
[QUOTE=Chandon]The version of kismet in warty is older than dirt. As far as I can tell, there's no version in breezy (or I'd just do that).[/QUOTE]
"in warty"?

---

### Post by vvlist on 2005-08-10
Has anyone got Wifi Radar to work? I've been trying but have had no luck.  :?

EDIT: Nevermind. After reading the exhausting README, I got it all figured out. :-|

---

