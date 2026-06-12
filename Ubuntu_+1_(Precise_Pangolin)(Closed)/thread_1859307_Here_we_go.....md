---
title: "Here we go...."
date: 2011-10-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ArtLaForge on 2011-10-13
Just did a dist-upgrade, well were still 99.9% Oneiric but my sys monitor says Precise.:popcorn:

---

### Post by ventrical on 2011-10-13
Ya don't say :)

---

### Post by cariboo on 2011-10-13
There won't be a lot happening, until after UDS-P in early November.

---

### Post by ventrical on 2011-10-13
Thanks Caribou. I guess we will have to settle for coughing up a few fur balls until we can get our hands on a Pangolin :)

---

### Post by ranch hand on 2011-10-13
> **ventrical said:**
> Ya don't say :)
I like the wallpaper you have there.

---

### Post by ubupirate on 2011-10-13
> **ventrical said:**
> Ya don't say :)

Nice photoshop. :p

---

### Post by IWantFroyo on 2011-10-13
> **ubupirate said:**
> Nice photoshop. :p

+1. [s]System monitor doesn't bother putting the name of the animal in there, doesn't capitalize the first word, and puts it in parenthesis.[/s]

Edit- Nvm. You covered that. Still, a nice _GIMP._

---

### Post by ventrical on 2011-10-14
> **ranch hand said:**
> I like the wallpaper you have there.


Thanks ranchhand (and all). It's just a theme provided by Oneiric and a few adjustments to compiz. The devs for compiz and unity really burned the midnight oil on this distro (IMO).

One of my friends often comments that I always have a new computer:)

With wallch (wallpaperchanger set to very 10 seconds) one can get an appearance of some real time 3D :) Especially with family pics .. etc... I work with some seniors that like to have pics of their grandkids and family moving along the screen - so I am hoping to set up a few PCs for that after PP is release in April.

---

### Post by MacUntu on 2011-10-14
Uhm, that's not photoshopped.

---

### Post by collisionystm on 2011-10-14
here is the official release schedule for Ubuntu 12.04 LTS:

December 1st, 2011 - Alpha 1 release
February 2nd, 2012 - Alpha 2 release
March 1st, 2012 - Beta 1 release
March 22nd, 2012 - Beta 2 release
April 19th, 2012 - Release Candidate release
April 26th, 2012 - Final release of Ubuntu 12.04

---

### Post by PayPaul on 2011-10-14
Somebody is being real cute here with the un-precise pangolin? Messing with the heads of both noobs and nerds alike could get you into big tribble...

:lolflag:

---

### Post by MacUntu on 2011-10-14
How about you check it for yourself?

[https://launchpad.net/ubuntu/precise/+source/base-files/6.4ubuntu6](https://launchpad.net/ubuntu/precise/+source/base-files/6.4ubuntu6)

[IMG]http://img.xrmb2.net/images/812454.png[/IMG]

---

### Post by PayPaul on 2011-10-14
Hold on! Now be clear as to what this is. There is not even an alpha release of the Precise Pangolin yet. It's a splash screen.

---

### Post by MacUntu on 2011-10-14
Well, nobody said that's the final release of Ubuntu 12.04? :)

Right now Precise = Oneiric + [https://lists.ubuntu.com/archives/precise-changes/2011-October/thread.html](https://lists.ubuntu.com/archives/precise-changes/2011-October/thread.html)

Soon the Debian testing auto-import will start (unstable for non-LTS releases) - that's when things slowly should start getting interesting (hopefully).

---

### Post by PayPaul on 2011-10-14
> **MacUntu said:**
> Well, nobody said that's the final release of Ubuntu 12.04? :)

Right now Precise = Oneiric + [https://lists.ubuntu.com/archives/precise-changes/2011-October/thread.html](https://lists.ubuntu.com/archives/precise-changes/2011-October/thread.html)

Soon the Debian unstable auto-import will start - that's when things slowly should start getting interesting (hopefully).

Are these alphas or "pre-alphas". That sounds dangerous. I'm sure the people installing those put them on isolated drives or some such.

---

### Post by matt_symes on 2011-10-14
> **PayPaul said:**
> Are these alphas or "pre-alphas". That sounds dangerous. I'm sure the people installing those put them on isolated drives or some such.

```
matthew@matthew-Aspire-7540:~$sudo  bash -c "sed -i 's/oneiric/precise/g' /etc/apt/sources.list"
<snip>
matthew@matthew-Aspire-7540:~$sudo apt-get update
<snip>
matthew@matthew-Aspire-7540:~$sudo apt-get upgrade
<snip>
matthew@matthew-Aspire-7540:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu precise (development branch)"
matthew@matthew-Aspire-7540:~$ 

```Not my main install though. Just in a test partition.

---

### Post by jppr on 2011-10-14
> **PayPaul said:**
> Are these alphas or "pre-alphas". That sounds dangerous. I'm sure the people installing those put them on isolated drives or some such.

Yep, this is pre-alpha and this is a FUN and very interesting, not dangerous :popcorn:

---

### Post by cpatrick08 on 2011-10-14
> **MacUntu said:**
> Well, nobody said that's the final release of Ubuntu 12.04? :)

Right now Precise = Oneiric + [https://lists.ubuntu.com/archives/precise-changes/2011-October/thread.html](https://lists.ubuntu.com/archives/precise-changes/2011-October/thread.html)

Soon the Debian unstable auto-import will start - that's when things slowly should start getting interesting (hopefully).
since this is a lts release they get the packages from debian testing instead of debian unstable

---

### Post by MacUntu on 2011-10-14
ARGL, right. Good catch, thanks for correcting me! :-)

---

### Post by ranch hand on 2011-10-14
> **PayPaul said:**
> Are these alphas or "pre-alphas". That sounds dangerous. I'm sure the people installing those put them on isolated drives or some such.
There is very little that is different in 12.04-testing right now from 11.10.  There will continue to be little difference for quite a while yet.

Things actually become more unstable around alpha2 usually.

If you are careful it is actually possible to use the dev release as your main OS.  This is not recommended and you better expect some problems, perhaps large ones, along the way.

This is a fast dev cycle and for it to work requires that folks actually use the OS to find what is not working.

This is not something like MS puts out, which even in its released form will eat some folks drives.  This is Linux and it will generally do nothing worse than eat your data.  That is what backups are for.

I will admit that I use an external drive and turn off my internals, particularly during any installs.  I really do not want accidents with the installer mistaking partitions to be formatted due to an error on my part or because of a bug.

Most problems that cause damage are picnic related (Problem In Chair Not In Computer),  I am pretty good at that.

---

