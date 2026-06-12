---
title: "updating issue E: The package mcp-account-manager-uoa needs to be reinstalled, but I"
date: 2016-04-09
forum: Ubuntu/Debian BASED
---

### Post by grufolo on 2016-04-09
Dear all
first things first, apologies if what i am posting has a trivial solution. I have tried to find out a way out but i haven't succeeded.

I have a laptop (Acer aspire V3-571G) with a biolinux distro based on Ubuntu 14.04.
I haven't accessed my linux partition for a good while, and today i tried to log in and give it an update for those files requiring a new version.

I had first a problem with repositories, as some that i used to have did not work anymore. Finally, when those which did not work anymore were fixed, i was left with this error:

(both after sudo apt-get update and/or sudo apt-get dist-upgrade)
E: The package mcp-account-manager-uoa needs to be reinstalled, but I can't find an archive for it.

I can't seem to find a way around this issue. Is it a big problem?
Can i just forget about it? Is it stopping my computer from fully updating?

I found this page but i'm not entirely sure about how to decypher it
[http://packages.ubuntu.com/trusty/gnome/mcp-account-manager-uoa](http://packages.ubuntu.com/trusty/gnome/mcp-account-manager-uoa)

Thanks in advance for any help
Andrea

---

### Post by Bashing-om on 2016-04-09
grufolo; Hummm .. 

Curious, as the package is in ubuntu's repository :
> 
sysop@1404mini:~$ apt list mcp-account-manager-uoa
Listing... Done
mcp-account-manager-uoa/trusty-updates 3.8.6-0ubuntu9.2 amd64
sysop@1404mini:~$ 


Let' see what your system has installed and what it might be looking for;
Post back - Between Code Tags -  the output of terminal command:
```

apt-cache policy mcp-account-manager-uoa

```

see where we go from there.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by grufolo on 2016-04-09
Thanks a lot for the reply. I though it was weird too, 
[URL="http://www.dailywritingtips.com/forum/misc.php?do=bbcode#code"]```
[/URL]
kimboz@kimboz-Latitude-E4200[kimboz] apt-cache policy mcp-account-manager-uoa
mcp-account-manager-uoa:
  Installed: 3.8.6-0ubuntu9.1
  Candidate: 3.8.6-0ubuntu9.2
  Version table:
     3.8.6-0ubuntu9.2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
 *** 3.8.6-0ubuntu9.1 0
        100 /var/lib/dpkg/status
     3.8.6-0ubuntu9 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
[URL="http://www.dailywritingtips.com/forum/misc.php?do=bbcode#code"]
```[/URL]

Update: Synaptic package manager says the package was broken. I used Synaptic to completely remove it and i got the following error:
E: mcp-account-manager-uoa: package is in a very bad inconsistent state; you should  reinstall it before attempting a removal

---

### Post by Bashing-om on 2016-04-09
grufolo; Humm ...

It is installed ( older version); let's take the package manager's advise:
```

sudo apt install --reinstall mcp-account-manager-uoa

```

[INDENT][INDENT]what now
[/INDENT][/INDENT]

---

### Post by grufolo on 2016-04-09
there it is
```

kimboz@kimboz-Latitude-E4200[kimboz] sudo apt install --reinstall mcp-account-manager-uoa                                                    [11:13PM]
[sudo] password for kimboz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 mcp-account-manager-uoa : Depends: empathy (= 3.8.6-0ubuntu9.2) but 3.8.6-0ubuntu9.1 is to be installed
                           Recommends: ubuntu-control-center-signon but it is not installable
                           Recommends: account-plugin-aim but it is not going to be installed
                           Recommends: account-plugin-jabber but it is not going to be installed
                           Recommends: account-plugin-yahoo but it is not going to be installed
                           Recommends: account-plugin-salut but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

Bashing, i was wondering if all this mess is caused by the newer version of 3.8.6-0ubuntu9.x .... would that be possible?

Thanks a lot for helping me with this, anyway
Andrea

---

### Post by Bashing-om on 2016-04-09
grufolo; Well ..

The question now becomes what is holding empathy to that lower version ??
```

apt-cache policy empathy

```


[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by grufolo on 2016-04-09
Uhm, i guess you may know what this is

```

kimboz@kimboz-Latitude-E4200[kimboz] apt-cache policy empathy                                                                                [11:40PM]
empathy:
  Installed: 3.8.6-0ubuntu9.1
  Candidate: 3.8.6-0ubuntu9.2
  Version table:
     3.8.6-0ubuntu9.2 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 3.8.6-0ubuntu9.1 0
        100 /var/lib/dpkg/status
     3.8.6-0ubuntu9 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

---

### Post by v3.xx on 2016-04-09
Hey Bashing, how ya doing :D

Me wonders if a ppa is messing with this.

```
inxi -r
```

---

### Post by grufolo on 2016-04-09
Hi V3, thanks to you too
inxi is not recognised

```

zsh: correct 'inxi' to 'init' [nyae]? 


```

---

### Post by v3.xx on 2016-04-09
Ok, just do it longhand

```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

---

### Post by grufolo on 2016-04-09
Hey V3 thanks for your input
inxi is not recognised.

sh: correct 'inxi' to 'init' [nyae]?

---

### Post by v3.xx on 2016-04-09
No, inxi is correct.  Just use the command in post #12.  It outputs the same information.

---

### Post by grufolo on 2016-04-10
Sorry, i did not know inxi.
Here is the output:

```

kimboz@kimboz-Latitude-E4200[kimboz] cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list                                          [12:19AM]
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Alpha amd64 (20140323)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://archive.ubuntu.com/ubuntu/ trusty universe
deb http://archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list.d/bio-linux-legacy.list   /etc/apt/sources.list.d/marutter-c2d4u-trusty.list
/etc/apt/sources.list.d/cran-latest-r.list      /etc/apt/sources.list.d/mozillateam-firefox-next-trusty.list
/etc/apt/sources.list.d/google-chrome.list      /etc/apt/sources.list.d/nebc-bio-linux-trusty.list
/etc/apt/sources.list.d/google-talkplugin.list  /etc/apt/sources.list.d/x2go-stable-trusty.list


```

---

### Post by Bashing-om on 2016-04-10
grufolo; Morning;

So far so good, however.
Let us follow through with v3.xx's thought:
```

tail -v -n +1 /etc/apt/sources.list.d/*

```
and verify these sources seeing where this leads us to.
Be advised that the tool 'inxi' is not installed by default - in this instance, no big deal as we get the info via other means . 

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by grufolo on 2016-04-10
Guys, you're great, but we have a few time zones issues :D

Here's what the command returns:
```

kimboz@kimboz-Latitude-E4200[kimboz] tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/bio-linux-legacy.list <==
# Bio-Linux legacy packages (manually built, there is no deb-src)
# But there is an alternative mirror you can use.
# deb http://distro.ibiblio.org/bio-linux/packages/ unstable bio-linux
deb http://nebc.nerc.ac.uk/bio-linux/ unstable bio-linux

==> /etc/apt/sources.list.d/bio-linux-legacy.list.save <==
# Bio-Linux legacy packages (manually built, there is no deb-src)
# But there is an alternative mirror you can use.
# deb http://distro.ibiblio.org/bio-linux/packages/ unstable bio-linux
deb http://nebc.nerc.ac.uk/bio-linux/ unstable bio-linux

==> /etc/apt/sources.list.d/bl8.installed.save <==
Thu Oct 30 16:35:25 CET 2014

==> /etc/apt/sources.list.d/cran-latest-r.list <==
#Latest R-cran packages
# deb http://www.freestatistics.org/cran//bin/linux/ubuntu trusty/
# deb-src http://www.freestatistics.org/cran//bin/linux/ubuntu trusty/

==> /etc/apt/sources.list.d/cran-latest-r.list.save <==
#Latest R-cran packages
# deb http://www.freestatistics.org/cran//bin/linux/ubuntu trusty/
# deb-src http://www.freestatistics.org/cran//bin/linux/ubuntu trusty/

==> /etc/apt/sources.list.d/cran-precise.list.save <==
deb http://www.stats.bris.ac.uk/R/bin/linux/ubuntu precise/
deb-src http://www.stats.bris.ac.uk/R/bin/linux/ubuntu precise/

==> /etc/apt/sources.list.d/freenx-team-ppa-precise.list.save <==
deb http://ppa.launchpad.net/freenx-team/ppa/ubuntu precise main
deb-src http://ppa.launchpad.net/freenx-team/ppa/ubuntu precise main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-talkplugin.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/talkplugin/deb/ stable main

==> /etc/apt/sources.list.d/google-talkplugin.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/talkplugin/deb/ stable main

==> /etc/apt/sources.list.d/marutter-c2d4u-trusty.list <==
deb http://ppa.launchpad.net/marutter/c2d4u/ubuntu trusty main
# deb-src http://ppa.launchpad.net/marutter/c2d4u/ubuntu trusty main

==> /etc/apt/sources.list.d/marutter-c2d4u-trusty.list.save <==
deb http://ppa.launchpad.net/marutter/c2d4u/ubuntu trusty main
# deb-src http://ppa.launchpad.net/marutter/c2d4u/ubuntu trusty main

==> /etc/apt/sources.list.d/mozillateam-firefox-next-trusty.list <==
deb http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu trusty main

==> /etc/apt/sources.list.d/nebc-bio-linux-precise.list.save <==
# Packages from PPA
deb http://ppa.launchpad.net/nebc/bio-linux/ubuntu precise main
deb-src http://ppa.launchpad.net/nebc/bio-linux/ubuntu precise main

# Packages from Bio-Linux main repo.  Note that adding this repo
# without the above PPA will result in some missing dependencies, so
# don't do that!
deb http://nebc.nerc.ac.uk/bio-linux/ unstable bio-linux

# Don't try to add a matching deb-src line to the above.  There is no
# source repo.  If we have source, it's in the PPA.

==> /etc/apt/sources.list.d/nebc-bio-linux-trusty.list <==
deb http://ppa.launchpad.net/nebc/bio-linux/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nebc/bio-linux/ubuntu trusty main

==> /etc/apt/sources.list.d/nebc-bio-linux-trusty.list.save <==
deb http://ppa.launchpad.net/nebc/bio-linux/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nebc/bio-linux/ubuntu trusty main

==> /etc/apt/sources.list.d/x2go-stable-trusty.list <==
deb http://ppa.launchpad.net/x2go/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/x2go/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/x2go-stable-trusty.list.save <==
deb http://ppa.launchpad.net/x2go/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/x2go/stable/ubuntu trusty main

```

It all looks legit to me but what do i know :D

---

### Post by Bashing-om on 2016-04-10
grufolo; Hummm ...

What is " bio-linux/ " ? I do have some issues with it .

Looking at the source, I see no activity in more than a year... (???)

and there is this:
> 
# Packages from Bio-Linux main repo.  Note that adding this repo
# without the above PPA will result in some missing dependencies, so
# don't do that!
deb [http://nebc.nerc.ac.uk/bio-linux/](http://nebc.nerc.ac.uk/bio-linux/) unstable bio-linux

What is supposed to be " the above PPA " ??
Note that this is a duplicate source ! No want to do that in any case !
see the 1st entry in the directory:
> 
# Bio-Linux legacy packages (manually built, there is no deb-src)
# But there is an alternative mirror you can use.
# deb [http://distro.ibiblio.org/bio-linux/packages/](http://distro.ibiblio.org/bio-linux/packages/) unstable bio-linux
deb [http://nebc.nerc.ac.uk/bio-linux/](http://nebc.nerc.ac.uk/bio-linux/) unstable bio-linux


Unknown at this time how this may relate to the empathy install that is holding ' mcp-account-manager-uoa ' back; but, certainly needs to be addressed .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by grufolo on 2016-04-10
Sorry, Biolinux is a distribution of linux for bioinformaticians and in general for biologists, including some preinstalled software, which is good if you have a few troubles installing programs that are compliacated because they have several dependencies.

It's widely known in this field but not much outside the bio-world.
I could remove the 

```

# Packages from Bio-Linux main repo.  Note that adding this repo
# without the above PPA will result in some missing dependencies, so
# don't do that!
deb [http://nebc.nerc.ac.uk/bio-linux/](http://nebc.nerc.ac.uk/bio-linux/) unstable bio-linux

```
by adding a #, should I try this and re-update?

---

### Post by Bashing-om on 2016-04-10
grufolo; Hey ///

Yes, I vote yes on removing the duplicate source fetch.
Then yeah. let's see what happens with:
```

sudo apt update
sudo apt full-upgrade
sudo apt-get -f install

```

[INDENT]package manager
[INDENT][INDENT][INDENT]make it's self happy
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by howefield on 2016-04-11
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by grufolo on 2016-04-11
Hey y'all guys you have been great, indeed that solved it and magically when i removed that entry, the mcp-account-manager-uoa got updated properly.

Thanks a lot, i would have never guessed it by myself.
I have noticed the thread was moved away but i am not sure as to why, but it's all good.
My heartfelt thanks
Andrea

---

### Post by Bashing-om on 2016-04-11
grufolo; Great !

Never know for sure 'til we try .

As all is now good:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

