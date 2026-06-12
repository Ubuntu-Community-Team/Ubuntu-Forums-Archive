---
title: "Can't add extra repositories (Solved)"
date: 2005-10-23
forum: Repositories &amp; Backports
---

### Post by public_void on 2005-10-23
Hey

I'm a n00b, so be kind.
I can't seem to add extra repositories. I tried to manually do it as suggested [here]("http://www.ubuntuguide.org/"). I start by editting sources.list in gedit. I used the one in the link, but I changed it after (as you can see below). That goes fine so then I go to update. This is the problem, each of the connections times out, reading some of the other threads i'm probably not the only one with this kinda problem. I am behind a proxy on a uni network, I know this could be a problem.

My Soucres.list

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

---

### Post by aysiu on 2005-10-23
You can browse the internet and get email in Ubuntu but the repositories time out? That's odd. Your sources.list doesn't look odd in any way (except you can comment out--put a # sign in front of--the CD source in the beginning).

---

### Post by public_void on 2005-10-23
Heres my Terminal window so you see what I mean. I've tried to ping the servers (82.211.81.138 and 82.211.81.182), but that failed (although they may not except ping request). I really think it the proxy I'm behind, but I'm not sure how.

Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.182), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.182), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (82.211.81.182), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (82.211.81.182), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Reading package lists... Done

---

### Post by spaznrq on 2005-10-23
I've upgraded to Breezy 5.10 final release and just can't find the solution to these repository problems...

First of all, I'm a Linux noob.  I tried out the 5.10 pre-release preview and things went alright.  Ran into some repository problems but I found a good source.list to copy and paste to make things work.  I've been doing a lot of reading about this around here, but I'm still not understanding what the problem is about not being able to connect and backport problems blab blah.. Now, I'm just tired of searching through these forums everyday and filtering through all these searches to find a helpful response for 5.10.  It's frustrating for us noobs.

Can someone kindly paste their most current, working sources.list for me?

---

### Post by public_void on 2005-10-26
I've done it at last. I found an old thread [here](http://ubuntuforums.org/showthread.php?t=63496&highlight=apt.conf+http+proxy) that told me to create /etc/apt/apt.conf and to put this in

ACQUIRE {
http::proxy "http://user:password@proxy:portnum/"
}

I've updated my repositories now.

---

### Post by ecobuntu on 2005-10-27
[QUOTE=spaznrq]I've upgraded to Breezy 5.10 final release and just can't find the solution to these repository problems...

First of all, I'm a Linux noob.  I tried out the 5.10 pre-release preview and things went alright.  Ran into some repository problems but I found a good source.list to copy and paste to make things work.  I've been doing a lot of reading about this around here, but I'm still not understanding what the problem is about not being able to connect and backport problems blab blah.. Now, I'm just tired of searching through these forums everyday and filtering through all these searches to find a helpful response for 5.10.  It's frustrating for us noobs.

Can someone kindly paste their most current, working sources.list for me?[/QUOTE]

Here's mine

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

------
It works about 9/10 times...if it doesn't work wait a few minutes and retry updating it.

---

### Post by spaznrq on 2005-10-28
Thanks ecobuntu!

I actually realized I needed to do a "sudo apt-get update" after I edit the sources.list file.  I've been doing that before, but somehow I didn't realize I forgot this last step this time.  So now, I've learned this lesson the hard way for all of you hehe. Thanks.

---

