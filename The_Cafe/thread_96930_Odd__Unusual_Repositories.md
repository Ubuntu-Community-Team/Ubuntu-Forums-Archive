---
title: "Odd / Unusual Repositories"
date: 2005-11-29
forum: The Cafe
---

### Post by gingermark on 2005-11-29
So, I surfed onto a [webpage](http://www.usinglinux.org/multimedia/) that listed some multimedia Linux software, and came accross a plugin to display the song xmms is playing in gaim. Gimmicky, I know, but I went looking for it (it's not in the official repos) and came accross the [Atlanta Linux Enthusiasts](http://www.ale.org/new/index.php). Their ftp site seems to have a fair few Ubuntu packages, including what I was after.

I also used to use a repository that someone put up for audioscrobbler plugins when using hoary. In breezy they became offical packages, so I no longer needed it, but it got me wondering what additional repositories people use?

Maybe you have one for a single program, or have found a goldmine out there of useful programs?

I'd be interested to hear what "extra" repositories people are using. Obviously there are the PLF ones, but with the popularity of Ubuntu there must be others all over the world.

I could have posted this in the repository forum, but that's just for offical ones, and I just fancied a chat about it anyways :) 

Cheers,
gingermark.

P.S. My sources.list, if you care:
```
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 
deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted 
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted 
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe 
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe 

deb http://security.ubuntu.com/ubuntu breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted 

deb http://security.ubuntu.com/ubuntu breezy-security universe 
deb-src http://security.ubuntu.com/ubuntu breezy-security universe 

deb http://archive.ubuntu.com/ubuntu breezy multiverse 
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse 

## mirror provided thanks to OVH http://ovh.com (Pengiun Liberation Front)
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free 
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free 

## Ubuntu Backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse 

## KDE 3.5
deb http://kubuntu.org/packages/kde35 breezy main 
```
Feel free to recommend additions to me (especially for repositories with cool multimedia stuff!)

---

### Post by Limulus on 2005-12-06
First some comments about your repositories:

* Unless you plan on using the CD to install packages (e.g. if don't have a good net connection), you don't need the "deb cdrom" entry (its also easy to add back using Synaptic; go Edit -> Add CD-ROM...).

* Unless you use the source code to compile for yourself, you don't need any of the "deb-src" ones; stripping those out will also significantly reduce the time to download package information.

* I notice you're using a mix of official Ubuntu repositories; these can be significantly consolidated.  After stripping out the deb-src entries, go from seven lines:

deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted 
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

to just four:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-security main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-backports main universe multiverse restricted

"archive" can be changed to any of the ones you had iiRC (e.g. "gb.archive", "us.archive" or "security" without it making much of a difference, except perhaps in load times).

* More PLF mirrors here: [http://plf.zarb.org/mirrors.php](http://plf.zarb.org/mirrors.php)

* There are more Ubuntu Extras repositories, though they seem to be updating their website at the moment; I've been using deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) breezy-extras main universe multiverse restricted


Now then, as far as other repositories go, how about:

# Boinc! (Debian)
deb [http://pkg-boinc.alioth.debian.org/](http://pkg-boinc.alioth.debian.org/) ./

# Wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

# Upower
deb [http://repo.nanofreesoft.org](http://repo.nanofreesoft.org) breezy main

# Marillat (Debian audio-visual stuff)
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) etch main

# Rarewares (Debian audio-visual stuff)
deb [http://www.rarewares.org/debian/packages/unstable](http://www.rarewares.org/debian/packages/unstable) ./

---

### Post by Limulus on 2005-12-06
[QUOTE=Limulus]There are more Ubuntu Extras repositories, though they seem to be updating their website at the moment[/QUOTE]
I just [found out]("http://ubuntuforums.org/showthread.php?p=550722") from jdong, the guy who runs the backports, that UE has basically been scrapped, with a lot of its functionality being taken over by the PLF.  I have thus removed UE from my sources.list

---

### Post by ChrisC on 2005-12-11
[QUOTE=Limulus]
# Boinc! (Debian)
deb [http://pkg-boinc.alioth.debian.org/](http://pkg-boinc.alioth.debian.org/) ./
[/QUOTE]

Has anyone been able to get BOINC to install via apt-get/synaptic in Breezy?  I've been beating my head against this for a week and it has brought my Windows -> Ubuntu transition to a full stop.

I've searched the forums, done the deeds.  I don't want to hear if you've HEARD of something that "should" work, I want to hear if you actually have an apt-get-installed BOINC working on your Breezy system ...

Getting frustrated ....

---

### Post by Limulus on 2005-12-11
[QUOTE=ChrisC]Has anyone been able to get BOINC to install via apt-get/synaptic in Breezy?  I've been beating my head against this for a week and it has brought my Windows -> Ubuntu transition to a full stop. I've searched the forums, done the deeds.  I don't want to hear if you've HEARD of something that "should" work, I want to hear if you actually have an apt-get-installed BOINC working on your Breezy system ... Getting frustrated ....[/QUOTE]
Whoops, sorry, looks like they've changed the layout of their repository.  I had Boinc running on my laptop a while ago until I realized how warm it was making it at which point I uninstalled it ^_-

I can confirm that adding the following two lines to your sources.list will work in Breezy:

> deb [http://pkg-boinc.alioth.debian.org/debian/](http://pkg-boinc.alioth.debian.org/debian/) unstable non-free
deb [http://pkg-boinc.alioth.debian.org/debian/](http://pkg-boinc.alioth.debian.org/debian/) stable main
Then press reload in Synaptic.  Get boinc-client (5.2.5-1sarge2) as well as one or both of boinc-manager (4.72-2) and kboincspy.  The latter two are GUIs for Boinc; if you don't want boinc-manager, omit the *unstable* entry.

Right now I'm getting some sort of time-out message about the SETI servers; this should go away in not too long.

**Update**: As per [http://setiweb.ssl.berkeley.edu/index.php](http://setiweb.ssl.berkeley.edu/index.php)

"December 12, 2005 We have turned off work distribution to allow result uploads to catch up."  I guess that's why I haven't been able to connect :)

---

### Post by ChrisC on 2005-12-12
Limulus wins the pennant!  Limulus wins the pennant!  Limulus wins the pennant!

Works great for me.  I'm going to go post this in another thread or two, lots of other people having been beating their heads against this, and giving up and going with the BOINC installer script.  All hail our apt gods.

---

### Post by Limulus on 2005-12-13
Glad to hear that it works; about an hour ago the server let me download some info and its now crunching the numbers (and my CPU temp went from ~45 C to just over 60 C... so I clicked the SETI@home line in the Projects tab of boinc-manager and pressed the "No new work" button ^_-)

---

### Post by mrfrost on 2005-12-13
Hi! I'm the Debian maintainer of BOINC and have built now BOINC packages for Ubuntu "Breezy Badger". Add these lines to your sources.list
```
deb     http://pkg-boinc.alioth.debian.org/ubuntu breezy universe
deb-src http://pkg-boinc.alioth.debian.org/ubuntu breezy universe
```
and run *apt-get install boinc-client boinc-manager* to install the BOINC core client and the BOINC Manager.
Feedback about the packages are very welcomed. And I hope this helps to avoid frustration! :)

Happy crunching!
 - Frank

---

### Post by Limulus on 2005-12-13
mrfrost: boinc-manager updates no problem (thank you for helping make Ubuntu better!) but boinc-client does not; as per Synaptic:

```
boinc-client:
  Depends: lsb-base (>=3.0-6) but 3.0-1ubuntu8 is to be installed
```

lsb-base 3.0-1ubuntu8 is [the default Breezy version](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=lsb-base&searchon=names&subword=1&version=all&release=all), BTW

---

### Post by mrfrost on 2005-12-13
Thanks for the report. I've uploaded new packages which fixes this bug.

---

### Post by Limulus on 2005-12-13
[QUOTE=mrfrost]Thanks for the report. I've uploaded new packages which fixes this bug.[/QUOTE]
Wonderful!  Thanks so much :)

BTW, are there also AMD64 and PPC versions in the works (as I note for some of the Debian versions), or just i386 for the time being?

Regardless, I will be recommending this to be added to ubuntu_demon's source list: [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by mrfrost on 2005-12-13
[QUOTE=Limulus]BTW, are there also AMD64 and PPC versions in the works (as I note for some of the Debian versions), or just i386 for the time being[/QUOTE]

I can only provide packages for i386, since I've no access to other architectures. If someone builds the Ubuntu packages for non i386 arches I'll happily upload them to the pkg-boinc repository.

---

### Post by ChrisC on 2005-12-13
Thanks Frank for your efforts!

Assuming I've already installed the stable/unstable packages that Limulus pointed out yesterday, and would now like to change over to the "breezy" packages instead, will uninstalling and reinstalling boinc-client and boinc-manager wipe out my settings and accumulated work?

My current installation seems to be running OK, although the climateprediction work set terminated overnight with a signal 11.  Don't know yet if that's repeatable behavior, waiting for CP.net to let download another result.  But generally I'd rather be on the breezy packages ...

---

### Post by Limulus on 2005-12-14
[QUOTE=ChrisC]Thanks Frank for your efforts!

Assuming I've already installed the stable/unstable packages that Limulus pointed out yesterday, and would now like to change over to the "breezy" packages instead, will uninstalling and reinstalling boinc-client and boinc-manager wipe out my settings and accumulated work?

My current installation seems to be running OK, although the climateprediction work set terminated overnight with a signal 11.  Don't know yet if that's repeatable behavior, waiting for CP.net to let download another result.  But generally I'd rather be on the breezy packages ...[/QUOTE]

What I did so as to avoid interruptions was go into Boinc Manager, click the Projects tab, highlight the running project (e.g. SETI@home; if you have more than one, you'll need to repeat this for all of them), and on the left hand side, you'll see a Tasks section, with the button No new work; click that and when its done with the current unit it will upload it and not get any new units.

When all the results have been uploaded (edit: even if it says "Ready to report" in the Status column of the Work tab, if you see something like "Wed 14 Dec 2005 12:48:41 AM CST|SETI@home|Finished upload of 30se04aa.8299.11457.573572.87_5_0" in the Messages tab, then its finished), change the repository in your sources.list file to the new breezy one and upgrade (e.g. with Synaptic).

Once the new version is installed, go back and reverse the process by pressing the Allow new work button (repeat as needed).

---

### Post by Limulus on 2005-12-14
[QUOTE=mrfrost]I can only provide packages for i386, since I've no access to other architectures. If someone builds the Ubuntu packages for non i386 arches I'll happily upload them to the pkg-boinc repository.[/QUOTE]
I will ask around and see if perhaps someone from my local LUG can help out on that front :)

---

### Post by mrfrost on 2005-12-14
[QUOTE=ChrisC]Assuming I've already installed the stable/unstable packages that Limulus pointed out yesterday, and would now like to change over to the "breezy" packages instead, will uninstalling and reinstalling boinc-client and boinc-manager wipe out my settings and accumulated work?[/QUOTE]

You should not remove the old boinc-client package! "apt-get remove --purge boinc-client" or marking for complete removal in Synaptic will wipe out your settings and accumulated work, because it removes the BOINC working dir /var/lib/boinc-client. So don't do it.

Just change your sources.list and upgrade the packages.

---

