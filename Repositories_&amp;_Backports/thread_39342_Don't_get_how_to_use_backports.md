---
title: "Don't get how to use backports"
date: 2005-06-04
forum: Repositories &amp; Backports
---

### Post by Gorf on 2005-06-04
I am following this link:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

For how to add backports to my Synaptic.  Currently my sources.list look like this:

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


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

When I click "Reload" in Synaptic it fails on about a dozen repositories.  What am I doing wrong here?  I want to update a few applications (ie: Gaim 1.3.0) from backports, but even after reloading and seeing that the backports repository reloaded, I still only see 1.1.0 in the search.  I have never gotten backports to work.  Can someone hold my hand on this, cause I am not getting it...

---

### Post by crane on 2005-06-04
Have you closed and reopened synaptic? What about apt, do you get the same errors?

---

### Post by Gorf on 2005-06-04
I think I found something that I did.  I closed synaptic reopened it, and now I don't get the errors.  But I still don't see anything different.  How do I select Gaim that is in the backports?

---

### Post by crane on 2005-06-04
I don't really know for sure. I jsut use apt-get update and apt-get upgrade once a week and all is up to date. (gaim 1.3.0)

 Dtry doing a search for gaim and see what comes up.

---

### Post by crane on 2005-06-04
Just did search in synaptic
It showed up as> 
[color=blue]gaim  .....   1:1.3.0-1~5.04ubp multi protocall instant messeging client[/color]

---

### Post by jdong on 2005-06-04
Yep, you have Backports then :)

All backports packages end with "~#.##ubpN", where #.## is the Ubuntu release (5.04 = Hoary) and N is the Backports revision.

---

### Post by Gorf on 2005-06-04
Here ya go.  This is a screenshot of my Synaptic session.  Freshly opened and reloaded:

[http://www.whootis.com/pics/synaptic.gif](http://www.whootis.com/pics/synaptic.gif)

I'm not seeing anything.  And thats with this as my sources.list:


deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


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
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted



sooooo...?

---

### Post by crane on 2005-06-04
Here is mine I'm using a different mirror on the backports.

#deb cdrom:[Ubuntu 4.10 _hoary Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb [http://mirror.my-space.ath.cx/](http://mirror.my-space.ath.cx/) unstable/ 
deb [http://soulmachine.net/debian](http://soulmachine.net/debian) unstable/
#deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports main universe multiverse restricted
deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-extras main universe multiverse restricted

#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted
#[http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/)

---

### Post by Gorf on 2005-06-05
No change.


So not to be offensive or anything, but does anyone in the Ubuntu forums actually offer any advice on actually trying stuff to fix things?  I am really happy that your sources.list works for you, but posting your configuration information does little to nothing in helping understand why it ->**doesn't** <- work for me.  This is my second thread on this subject, and so far all I have got is a bunch of people posting links I have read a dozen times, and showing me thier sources.list.  Is there anyone useful that can actually offer trouble shooting techniques and tips to try and resolve this?

While I truly like this distribution, the support I have managed to get out of it is nearing that of Microsoft tech support...

---

### Post by crash369 on 2005-06-05
[QUOTE=Gorf]While I truly like this distribution, the support I have managed to get out of it is nearing that of Microsoft tech support...[/QUOTE]
well then i guess you are lucky that your system is much more stable than an MS one  :wink: 

as far as an answer to yourquestion,  you said yourself that when you reload your sources in synaptic, it fails on a dozen repositories.  well, if it fails on the backports reps, then obviously you cannot get updated packages (such as gaim v 1.3).

perhaps you can try to use a different mirror.

---

### Post by ltmon on 2005-06-05
You might see more information on the problem if you run

sudo apt-get update

rather than update from within synaptic.

When I did this I found that the repository I was looking at was giving me an "Access Denied" error (not sure why), but I then just changed to another mirror and it was fine.

---

### Post by Gorf on 2005-06-05
[QUOTE=Gorf]I think I found something that I did.  I closed synaptic reopened it, and now I don't get the errors.  But I still don't see anything different.  How do I select Gaim that is in the backports?[/QUOTE]

That implies that the errors are no longer occuring.

---

### Post by Gorf on 2005-06-05
[QUOTE=ltmon]You might see more information on the problem if you run

sudo apt-get update

rather than update from within synaptic.

When I did this I found that the repository I was looking at was giving me an "Access Denied" error (not sure why), but I then just changed to another mirror and it was fine.[/QUOTE]

Alright that sounds like an idea.  Here is the output of that.  I don't really see any problems though...


Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/universe PackagesGet:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release [16.8kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/restricted Packages
Get:7 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages [33B]
Get:8 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages [859B]
Get:9 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages [33B]
Get:10 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages [33B]
Get:11 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/main Packages [33B]
Get:12 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/universe Packages [33B]
Get:13 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/multiverse Packages [33B]
Get:14 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/restricted Packages [33B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Get:15 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages [33B]
Get:16 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages [33B]
Get:17 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages [33B]
Get:18 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages [33B]
Get:19 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/main Packages [33B]
Get:20 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/universe Packages [33B]
Get:21 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/multiverse Packages [33B]
Get:22 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/restricted Packages [33B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Fetched 35.4kB in 1s (23.8kB/s)
Reading package lists... Done

Then just for giggles (and I have uninstalled gaim at this point), I try to reinstall it.  I used the -s switch so that I didn't actually install anything, just report what I would get:


gsweet@whappy:~$ sudo apt-get install -s gaim
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gaim-data
Suggested packages:
  libzephyr3
The following NEW packages will be installed:
  gaim gaim-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Inst gaim-data (1:1.1.4-1ubuntu4.1 Ubuntu:5.04/hoary-security)
Inst gaim (1:1.1.4-1ubuntu4.1 Ubuntu:5.04/hoary-security)
Conf gaim-data (1:1.1.4-1ubuntu4.1 Ubuntu:5.04/hoary-security)
Conf gaim (1:1.1.4-1ubuntu4.1 Ubuntu:5.04/hoary-security)

---

### Post by jdong on 2005-06-05
If you got GAIM 1.3, that means Backports is working...

The error shows up the first time after launching Synaptic, because the package lists aren't there to begin with. After a reload via Synaptic, it'll work.

---

### Post by crash369 on 2005-06-05
Gorf

in synaptic, search for GAIM. highlight the package, then try Package > Force Version...

see if the 1.3 is in the list.

EDIT:  you know what, just doing that, I realized that not all the backport mirrors are synched =/.  for eaxmple, the planetmirror GAIM package is v1.2

---

### Post by Gorf on 2005-06-05
The only two options it shows are 

1:1.1.4-1ubuntu4.1(hoary-security)
1:1.1.4-1ubuntu4 (hoary)

---

### Post by crash369 on 2005-06-05
ok, this is the last thing that i can even imagine to suggest. try removing the trailing / from the backports link.  so change

```
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```to
```
deb http://ubuntu-backports.mirrormax.net hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net hoary-extras main universe multiverse restricted
```

---

### Post by Gorf on 2005-06-06
Here is the *only* entries in my sources.list:

deb [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras main universe multiverse restricted

that's it.  When I reload it I get this:

gsweet@whappy:~$ sudo apt-get update
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Reading package lists... Done


And still the only version that shows up is 1:1.1.4

All I can say is this apt-get crap sucks.  I guess it's back to slackware for me...

---

### Post by Mez on 2005-06-06
Hi gorf... I remember having this problem myself.

It occurs oif you pin the hoary packages I believe.

do you have anything in /etc/apt/preferences

---

### Post by jdong on 2005-06-06
[QUOTE=Gorf]Here is the *only* entries in my sources.list:

deb [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras main universe multiverse restricted

that's it.  When I reload it I get this:

gsweet@whappy:~$ sudo apt-get update
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Reading package lists... Done


And still the only version that shows up is 1:1.1.4

All I can say is this apt-get crap sucks.  I guess it's back to slackware for me...[/QUOTE]

Everything sucks when it isn't configured properly.

You _MUST_ have the original Hoary sources. Cut and paste the UbuntuGuide sources.list, and make sure you aren't pinning (/etc/apt/preferences)

---

### Post by Gorf on 2005-06-06
I have no idea what pinning is.  But the /etc/apt/preferences file is non-existent.  I copied and pasted the UbuntuGuide sources.list so mine now looks like this:

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


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
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted





I had to comment out the cd-rom section cause I keep getting errors on it for some reason.  Afterwards I did:

gsweet@whappy:/etc/apt$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Fetched 4B in 1s (2B/s)
Reading package lists... Done



Then I did:

gsweet@whappy:/etc/apt$ sudo apt-get install -s gaim
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gaim-data
Suggested packages:
  libzephyr3
The following NEW packages will be installed:
  gaim gaim-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Inst gaim-data (1:1.1.4-1ubuntu4.1 Ubuntu:5.04/hoary-security)
Inst gaim (1:1.1.4-1ubuntu4.1 Ubuntu:5.04/hoary-security)
Conf gaim-data (1:1.1.4-1ubuntu4.1 Ubuntu:5.04/hoary-security)
Conf gaim (1:1.1.4-1ubuntu4.1 Ubuntu:5.04/hoary-security)




Mind you I did the "-s" so it wouldn't install anything, just show the version that it intends to install.




Just for grins here is my /etc/apt directory:

gsweet@whappy:/etc/apt$ ls -lR /etc/apt
/etc/apt:
total 28
drwxr-xr-x  2 root root 4096 2005-06-03 22:15 apt.conf.d
-rw-------  1 root root    0 2005-06-03 21:33 secring.gpg
-rw-r--r--  1 root root 1670 2005-06-06 17:53 sources.list
-rw-r--r--  1 root root 1669 2005-06-06 17:53 sources.list~
-rw-r--r--  1 root root 1851 2005-06-04 23:41 sources.list.save
-rw-------  1 root root 1200 2005-06-03 22:26 trustdb.gpg
-rw-r--r--  1 root root 2381 2005-06-03 21:33 trusted.gpg
-rw-r--r--  1 root root 1724 2005-06-03 21:32 trusted.gpg~

/etc/apt/apt.conf.d:
total 20
-rw-r--r--  1 root root  51 2005-03-18 02:49 05aptitude
-rw-r--r--  1 root root 129 2005-06-04 23:41 10periodic
-rw-r--r--  1 root root  85 2005-06-04 23:41 20archive
-rw-r--r--  1 root root 182 2005-03-01 14:08 70debconf
-rw-r--r--  1 root root  70 2005-01-25 05:05 99update-notifier

---

### Post by jdong on 2005-06-07
Do an **apt-get dist-upgrade -s**. Run two dist-upgrades. Sometimes, dependencies can only be resolved in two passes.

---

### Post by stubby on 2005-06-07
I get the same errors as well.

A whole bunch of ign's... I noticed in synaptic that when i did a reload there would be some that would say "hit", but then fail when getting the release.pgp ...

---

### Post by Gorf on 2005-06-07
Two passes:

gsweet@whappy:/etc/apt$ sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gsweet@whappy:/etc/apt$ sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by maspro on 2005-06-07
Well if your sources.list is correct and you have restarted Synaptic and then pushed the reload button in Synaptic and it still doesn't work, then do it the Windows way....... RE-INSTALL Ubuntu. If it works for everyone else and you are the exception, then clearly something is broken on your system or you are doing something wrong. 

This is my sources.list and all is working perfectly for me. 

## UBUNTU CDROM
#deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## UBUNTU MAIN
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## UBUNTU UNIVERSE
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe

## UBUNTU SECURITY
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## UBUNTU MULTIVERSE
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## BACKPORTS
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## MARILLAT
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

---

### Post by maspro on 2005-06-07
[QUOTE=Gorf]No change.


So not to be offensive or anything, but does anyone in the Ubuntu forums actually offer any advice on actually trying stuff to fix things?  I am really happy that your sources.list works for you, but posting your configuration information does little to nothing in helping understand why it ->**doesn't** <- work for me.  This is my second thread on this subject, and so far all I have got is a bunch of people posting links I have read a dozen times, and showing me thier sources.list.  Is there anyone useful that can actually offer trouble shooting techniques and tips to try and resolve this?

While I truly like this distribution, the support I have managed to get out of it is nearing that of Microsoft tech support...[/QUOTE]
I read the whole thread and the people here have given very usefull advice and if all works well on your system then you should have no problems. But if all advice given here is not working for you then something else on your system or network doesn't work right and needs to be fixed first. Did you previously mess around in you Ubuntu installation that might have caused things to break?

---

### Post by Gorf on 2005-06-07
This installation was approximately 30 minutes old when this whole fiasco began.  And the installation before it had the same problem, as did the one before it with Warty.

But perhaps the 4th or 5th time is the charm eh?  I will re-install tonight.  The first thing I will do is **only** modify the sources.list and see how that goes.  I will do it exactly as is described earlier in this thread.  See you in an hour.

---

### Post by Gorf on 2005-06-07
looks like that took a lot less time. 

Anyway, My original sources.list:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


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



My altered sources.list:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release amd64 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

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
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted




My apt-get update:

gsweet@whappy:~$ sudo apt-get update
Password:
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release [26.2kB]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Get:7 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages [33B]
Get:8 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages [8 59B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Get:9 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages [33B]
Get:10 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages  [33B]
Get:11 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages [33B]
Get:12 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages [33B ]
Get:13 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages [3 3B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Get:14 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages [3 3B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages [16.8kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages [75.9kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources [3668B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages [2072kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources [48.4kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources [857kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Fetched 3119kB in 8s (389kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems






and my attempt to install gaim:

gsweet@whappy:~$ sudo apt-get install -s gaim
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gaim-data
Suggested packages:
  libzephyr3
The following packages will be upgraded:
  gaim gaim-data
2 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
Inst gaim [1:1.1.4-1ubuntu4] (1:1.1.4-1ubuntu4.1 Ubuntu:5.04/hoary-security) []
Inst gaim-data [1:1.1.4-1ubuntu4] (1:1.1.4-1ubuntu4.1 Ubuntu:5.04/hoary-security)
Conf gaim-data (1:1.1.4-1ubuntu4.1 Ubuntu:5.04/hoary-security)
Conf gaim (1:1.1.4-1ubuntu4.1 Ubuntu:5.04/hoary-security)




No 1.3.0.  That is with a bone stock nothing altered, fresh off the CD install.

---

### Post by maspro on 2005-06-08
Could it be that something is conflicting in your sources.list regarding pinning different sources? 

What happens when you remove all of your sources except for the backports? 

So make sure the ONLY stuff you have in your sources.list is the following:

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by maspro on 2005-06-08
[QUOTE=Gorf]This installation was approximately 30 minutes old when this whole fiasco began.  And the installation before it had the same problem, as did the one before it with Warty.

But perhaps the 4th or 5th time is the charm eh?  I will re-install tonight.  The first thing I will do is **only** modify the sources.list and see how that goes.  I will do it exactly as is described earlier in this thread.  See you in an hour.[/QUOTE]
Btw did you notice that you have duplicate entries in your sources.list, remove them first. Better yet use the below sources.list and then following these instructions:

**Do the following in this exact order:**

- Close Synaptic. 
- Change your sources.list, save and close file. 
- Open Synaptic.
- Press the "Reload" button.
- Don't search yet.
- Press the "Mark All Upgrades" button.
- Press the "Apply" button.
- Maybe try to restart your system first. 
- Then search for GAIM.

## UBUNTU CDROM
#deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## UBUNTU MAIN
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## UBUNTU UNIVERSE
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

## UBUNTU SECURITY
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## UBUNTU MULTIVERSE
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## BACKPORTS
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

## MARILLAT
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

---

### Post by Gorf on 2005-06-08
[QUOTE=maspro]Could it be that something is conflicting in your sources.list regarding pinning different sources? 

What happens when you remove all of your sources except for the backports? 

So make sure the ONLY stuff you have in your sources.list is the following:

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted[/QUOTE]

Previously in this thread I had attempted that.  I was told that that won't work.  And it had no effect anyway.

As for the conflict.... That previous post was done on a system that was less then 10 minutes old.  There is physically no way to create a conflict unless one comes pre-bundled in the installation.  At this point that is what I am thinking... there must be something wrong with the amd64 install.  Perhaps this afternoon I will reinstall and try it with x86.  

And the dupicate entries apparently appear in the UbuntuGuide.  I replaced the section of sources.list indicated in the guide and resulted in that error.  Perhaps that should be updated as well.

---

### Post by maspro on 2005-06-08
Well I checked the Ubuntu Guide and I don't see any duplicate entries there, are you sure you have copy/paste it right?

Use the sources.list I posted in my previous post, they work for sure!

Also maybe it's indeed wise to use a x86 version of Ubuntu instead of an AMD64 version. And as far as I know there are no major advantages  using a 64-bit version of Ubuntu at this point in time!

---

### Post by maspro on 2005-06-08
I manually browsed the backports repository with firefox and it seems that GAIM 1.3 isn't available for AMD64 and it's only available for x86 systems.

That's one problem about 64-bit systems, linux for AMD64 doesn't nearly have the same amount of software available, x86 has much more working software for it!

---

### Post by jdong on 2005-06-08
oh, you're using AMD64? I didn't realize that.

I have an AMD64 also, but I run 32-bit Ubuntu. I've found that a lot of useful stuff (flashplayer, w32codecs, etc) are not in 64-bit Linux. I've also failed to notice ANY performance difference between 32-bit and 64-bit mode on my desktop.

---

### Post by maspro on 2005-06-08
Well problem solved I would say, install Ubuntu 32-bit for x86 and all should be working perfectly, including GAIM! 

I'm also using Ubuntu 32-bit on a 64-bit laptop and I see no reason to install Ubuntu 64-bit until it's more mature and has more software available for it.

---

### Post by skoal on 2005-06-08
I browsed the online backport repo [http://public.planetmirror.com/pub/ubuntu-backports/dists/hoary-backports-staging/main/binary-i386/](http://public.planetmirror.com/pub/ubuntu-backports/dists/hoary-backports-staging/main/binary-i386/)

and found gaim-1.3 there as well.

Why, however, doesn't this package show up in synaptic (even with a force version attempt)?  Is it because it's in "staging"?

I just downloaded it anyways and used "dpkg -i" on it.

\\//_

---

### Post by maspro on 2005-06-08
[QUOTE=skoal]I browsed the online backport repo [http://public.planetmirror.com/pub/ubuntu-backports/dists/hoary-backports-staging/main/binary-i386/](http://public.planetmirror.com/pub/ubuntu-backports/dists/hoary-backports-staging/main/binary-i386/)

and found gaim-1.3 there as well.

Why, however, doesn't this package show up in synaptic (even with a force version attempt)?  Is it because it's in "staging"?

I just downloaded it anyways and used "dpkg -i" on it.

\\//_[/QUOTE]
If you use a x86 system and not a AMD64 then GAIM 1.3 should show up in Synaptic, but if you don't use a x86 system then GAIM 1.3 is a no no and won't show up.

---

### Post by skoal on 2005-06-08
hmmm...

I'm a str8 up Intel man, dyed-in-the-wool-4-life.  I never could get gaim-1.3 to show up for me in synaptic (after following this entire thread and others).  Oh well, I just dpkg'd the data file first then gaim itself and all's good in da hood.

\\//_

---

### Post by jdong on 2005-06-08
Strange. PlanetMirror doesn't seem to be in sync with the master repository.

Switch to a different mirror. Our official mirror is MirrorMax. Please see ubuntuguide.org/#extrarepositories

---

### Post by picturesqueweb on 2005-06-11
Great list maspro. I like the way the listing is organized. I edited my sources.list to match (with a few minor edits) and it works great. Thank you for posting this list. I too was receiving errors and this thread solved the issues for me.

---

