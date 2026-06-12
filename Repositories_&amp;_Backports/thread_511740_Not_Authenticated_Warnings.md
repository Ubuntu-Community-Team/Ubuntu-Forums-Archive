---
title: "Not Authenticated Warnings"
date: 2007-07-28
forum: Repositories &amp; Backports
---

### Post by theoutdoors on 2007-07-28
Hi,

I've suddenly started getting 'You are about to install software that can't be authenticated' warnings when updating or installing packages via synaptic. I've searched the forums a little and there seem to be several threads, but as far as I could see no clear answers as to why this would suddenly be happening.

I am using Ubuntu feisty. My sources.list is as follows:

[I]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports restricted main multiverse universe
# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main[/I]

So far the packages with the warnings are:

From the latest updates:

bind9-host
dnsutils
lftp
libbind9-0
libdns22
libisc11
libisccc0
libisccfg1
liblwres9

And from what I was just installing:

amarok
amarok-xine

As far as I can tell these are, at least in the majority if not all, officially supported packages... so I'm confused. Anyone able to tell me why I'm suddenly getting these warnings. Is there anything I should do about it? Or do I just ignore the warnings??

Thanks!

---

### Post by Ryzol on 2007-07-28
I have also been having this problem off and on for a couple of weeks, and it is rather frustrating. It even tells me that packages as basic as apt-doc can't be authenticated and could compromise my system.

---

### Post by theoutdoors on 2007-07-29
I googled some more and I found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/33696]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/33696")

[http://ubuntuforums.org/showthread.php?t=139191]("http://ubuntuforums.org/showthread.php?t=139191")

It sounds like it's a long running problem.

I changed to use the main repositories instead of the gb mirrors, as suggested, and the warnings went away, so I'm happy for now.

---

### Post by slash28 on 2007-08-05
I do not have any of the gb repositories enabled, yet I have been getting the authentication warnings for about a week now.  I am simply trying to install Thunderbird from the "Ubuntu Supported Apps" category of the Add/Remove applet, so this shouldn't be an issue.

Below is my sources.list file:

```
$ egrep -v "^$|^#" /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

---

### Post by slash28 on 2007-08-05
Update:

I tried using Synaptic instead of Add/Remove, but I still got the same authentication error when I marked Thunderbird for installation.  I cancelled the installation, then clicked the Reload button, and I was then able to mark Thunderbird for installation without any errors.  Success!

Instead of installing, I closed Synaptic and switched back to Add/Remove just to see if the reload of Synaptic fixed it in both places.  Success again!

I don't know what the precise difference is between Add/Remove and Synaptic, but they apparently use the same repository cache file(s).  I guess the moral of the story is that Synaptic should be the first place to turn to when the basic UI of the Add/Remove applet has trouble.

---

### Post by feydrutha on 2007-10-10
I have had this same problem on and off for a while.

I just now was getting the not authenticated warning when trying to install automake.

I do not had the gb repository, but a repository here in italy. I just now switched to another repository (still in italy) from the synaptic GUI and managed to install automake with no warnings.

So yes, this is a repository dependant problem and yes, migrating to another repository is at least a temporary fix.

---

### Post by q.dinar on 2008-08-02
hello.
i have had this warning. after i clicked "reload" it have disappeared.

---

### Post by ms_whosit on 2008-09-23
ditto--I was getting warnings with apt-get, then tried it in Synaptic and got the same warnings, closed Synaptic, opened it and hit reload and it worked without warnings. thanks!

---

