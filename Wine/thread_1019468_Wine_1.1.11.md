---
title: "Wine 1.1.11"
date: 2008-12-23
forum: Wine
---

### Post by poisonkiller on 2008-12-23
On WineHQ homepage, it says, that Wine 1.1.11 was released on 20th December, however it's not showing in repositories (latest is 1.1.10). Does is always take 3 days to make Ubuntu's packages or is there something wrong with my Ubuntu installation?

---

### Post by namdung on 2008-12-23
Ubuntu repositories are updated only once the software has been thoroughly tested by the Ubuntu team. So patience my dear.

---

### Post by poisonkiller on 2008-12-23
Ubuntu team tests packages which aren't even in the original repositories? Wow...

---

### Post by kostkon on 2008-12-23
> **poisonkiller said:**
> On WineHQ homepage, it says, that Wine 1.1.11 was released on 20th December, however it's not showing in repositories (latest is 1.1.10). Does is always take 3 days to make Ubuntu's packages or is there something wrong with my Ubuntu installation?
Usually the package is ready on the next day of a new release. But I believe, this time the packager may be busy with the Christmas and New Year festivities. Just be patient...

> **poisonkiller said:**
> Ubuntu team tests packages which aren't even in the original repositories? Wow...
This was unnecessary... Oh well...

---

### Post by albinootje on 2008-12-23
> **poisonkiller said:**
> On WineHQ homepage, it says, that Wine 1.1.11 was released on 20th December, however it's not showing in repositories (latest is 1.1.10). Does is always take 3 days to make Ubuntu's packages or is there something wrong with my Ubuntu installation?

If you want more bleeding edge software available every day (and keep the broken pieces ;-) switch to Debian Unstable or ArchLinux, hehe :)

---

### Post by skirkpatrick on 2008-12-23
If you want the latest Wine packages, use the Wine repository.

---

### Post by poisonkiller on 2008-12-23
I am using Wine repository (that's how I got Wine 1.1.10). Wine 1.1.11 should already be there, but Update Manager/Synaptic can't find it.

---

### Post by Caseyjp on 2008-12-23
Ditto here.  Normally the new package is in repos the next day or sooner.  I test with the latest 'stable' revs and this caught me off guard as the normal 'clockwork' release of wine following the announcement ....didn't this time.

---

### Post by SBFC on 2008-12-23
It's maintained by one guy. If it's not out right away it's because he hasn't gotten around to it for whatever reason.

You always have the option of compiling from source.

---

### Post by ajackson on 2008-12-23
> **poisonkiller said:**
> I am using Wine repository (that's how I got Wine 1.1.10). Wine 1.1.11 should already be there, but Update Manager/Synaptic can't find it.
The Ubuntu builds are looked after by one person, he normally has them out quick but it is Christmas time so maybe he's busy. He doesn't get paid for building the debs so stop moaning if the release is delayed every once in a while.

As the old saying goes, if you can do better...

---

### Post by gspat on 2008-12-23
Is there a way to see what the latest version in the repository is using apt-get or aptitude? Not install, just view...

I have no problem waiting for (a)ny release, I just want to see.

---

### Post by albinootje on 2008-12-23
> **gspat said:**
> Is there a way to see what the latest version in the repository is using apt-get or aptitude? Not install, just view...

I have no problem waiting for (a)ny release, I just want to see.
```

apt-cache show wine

```
should show the version numbers.

---

### Post by poisonkiller on 2008-12-23
> **ajackson said:**
> The Ubuntu builds are looked after by one person, he normally has them out quick but it is Christmas time so maybe he's busy. He doesn't get paid for building the debs so stop moaning if the release is delayed every once in a while.

As the old saying goes, if you can do better...
I wasn't moaning... I just wondered, if there might be something wrong with my repositories, since the release was quite a while ago. Usually I start looking for the problem in my own computer, but since I didn't find anything, I just wanted to check here.

---

### Post by pootan on 2008-12-23
nevermind

---

### Post by binbash on 2008-12-23
the wine repo is still 1.1.10

---

### Post by lady_jade on 2008-12-23
> **binbash said:**
> the wine repo is still 1.1.10

yeah was trying to get it to be downloaded but I noticed that. I never knew it was maintained by one man. I guess we should expect the new release after the holidays.... We should be reasonable when thinking of others...

---

### Post by binbash on 2008-12-24
> **lady_jade said:**
> yeah was trying to get it to be downloaded but I noticed that. I never knew it was maintained by one man. I guess we should expect the new release after the holidays.... We should be reasonable when thinking of others...

I totally agree with you

---

### Post by Gorbayov on 2008-12-27
download the ubuntu package from here:
[https://launchpad.net/~ubuntu-wine/+archive](https://launchpad.net/~ubuntu-wine/+archive)

---

### Post by emshains on 2008-12-27
> **Gorbayov said:**
> download the ubuntu package from here:
[https://launchpad.net/~ubuntu-wine/+archive](https://launchpad.net/~ubuntu-wine/+archive)

+1


If you want the bleeeeeeeeeeeeding edge build of wine, compile it yourself. 

Its as easy as untar/cd/./configure/make/sudomakeinstall

---

### Post by binbash on 2008-12-28
> **Gorbayov said:**
> download the ubuntu package from here:
[https://launchpad.net/~ubuntu-wine/+archive](https://launchpad.net/~ubuntu-wine/+archive)

thanks for the repository

---

### Post by poisonkiller on 2008-12-28
Please delete this post...

---

### Post by mahuyar on 2008-12-28
> **Gorbayov said:**
> download the ubuntu package from here:
[https://launchpad.net/~ubuntu-wine/+archive](https://launchpad.net/~ubuntu-wine/+archive)

By looking at the date, the guy, Scott Richie, was right on time.  Wine Ubuntu package was ready the very next day.  It was just not pushed onto the wine.budgetdedicated.com repos yet.

Kudos to Scott.  Thanks a ton, man...  :KS:KS:KS

---

