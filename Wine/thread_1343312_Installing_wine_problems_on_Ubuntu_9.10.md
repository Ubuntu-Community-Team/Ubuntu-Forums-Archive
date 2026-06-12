---
title: "Installing wine problems on Ubuntu 9.10"
date: 2009-12-01
forum: Wine
---

### Post by Allyanora on 2009-12-01
I have just upgraded to Ubuntu 9.10 and never installed wine before. I tried several other sites but nothing to resolve my problem. I downloaded the archive file and wrote in the terminal window   sudo apt-get install wine

the problem is that it says like this:

> allyanora@allyanora-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages


i followed the instructions on this site too:   [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)  but in the end, when i go to Applications->Add/Remove and search for Wine to install it, it says again: fix broken packages then try to install it again.

is there something I'm missing? I am new and I have no idea what's going on. Is the package from the official site broken? from where can I get a good package for Ubuntu 9.10?

---

### Post by jessiebrownjr on 2009-12-01
I had some freakshow errors happen with Transmission... I used an upgrade from the website that wasn't really recommended... and during a system upgrade, it removed it.. I went back to package manager to install it, but it said I was missing a dependancy.. I found out which one it was because it said that much.. I couldn't find it in the repo's but I googled it, and installed it manually, and then it fixed it..

If it lists a dependancy, try to find it that way
if you can't get any help
can always reinstall or try winehq.org

---

### Post by Allyanora on 2009-12-02
Hmm.. I didn't encounter that kind of problem... I don't know what's wrong. It just says the package is broken, nothing else, just when it wants to install... this is weird.


edit:

still didn't manage to install wine in any possible method. it just says cannot install wine 1.2, fix broken packages. (i tried installing from terminal too)

How can I install an older version of wine on Ubuntu 9.10 ?

---

### Post by agilius on 2009-12-02
I think the full line to install wine was:

[I]```
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list](http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/winehq.list
```

[/I]But I might be wrong. Why not try the other method where you first add the wine wineHQ APT Repository to your software list? It's on the wine [homesite here]("http://www.winehq.org/download/deb"). 

Good luck.

---

### Post by Allyanora on 2009-12-02
> **agilius said:**
> I think the full line to install wine was:

*```
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list](http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/winehq.list
```*But I might be wrong. Why not try the other method where you first add the wine wineHQ APT Repository to your software list? It's on the wine [homesite here]("http://www.winehq.org/download/deb"). 

Good luck.


that full line you gave was for jaunty, for ubuntu 9.04 not for ubuntu 9.10. it says right there what line is for what version.

I tried that method, doesn't work. same result.

---

### Post by 8Kuula on 2009-12-02
Maybe these help?

[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/447197](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/447197)
and
[http://ubuntuforums.org/showpost.php?p=8406437&postcount=5](http://ubuntuforums.org/showpost.php?p=8406437&postcount=5)

---

### Post by Allyanora on 2009-12-03
> **8Kuula said:**
> Maybe these help?

[https://bugs.launchpad.net/ubuntu/+source/wine/+bug/447197](https://bugs.launchpad.net/ubuntu/+source/wine/+bug/447197)
and
[http://ubuntuforums.org/showpost.php?p=8406437&postcount=5](http://ubuntuforums.org/showpost.php?p=8406437&postcount=5)


thank you, I will try these out too.

I also managed to install wine 1.1.33 using the steps on this thread:  [http://ubuntuforums.org/showthread.php?t=1341617](http://ubuntuforums.org/showthread.php?t=1341617)  

It takes a  little while but it was installed for sure. 

I guess the version 1.2 has some bugs: I will try out to install this version too (again, because my problem was that it says that the package is broken, to see if the bugs were fixed (it is an unstable version right now, that's what I've heard. the most new and stable version is 1.1.33 so far. (correct me if I'm wrong)

thanx to all :D really helped me a lot

---

### Post by 8Kuula on 2009-12-03
Stable: Wine 1.0.1
Development: Wine 1.1.33

Currently.

But that 1.0.1 version is realy old version.
Would suggest to use some development version since those has alot improvements, and regressions too :D

Little more info about Wine versions if want to read: [http://wiki.winehq.org/WineReleaseCriteria](http://wiki.winehq.org/WineReleaseCriteria)

So in nutshell, when you install wine1.2 package you actualy install latest development version until Wine 1.2 comes out, that would become new stable release then.

---

### Post by can8dnSix on 2009-12-03
"A .deb package can also be downloaded from [HTML]http://wine.budgetdedicated.com[/HTML]/  please keep in mind that Ubuntu versions older than Hardy are no longer being updated."

Download the version for 9.04 and install it manually (double click on it and click "install" when asked). I just did this and everything works fine; the link below is the source. Thanks :L

source:
[HTML]http://www.wine-reviews.net/wine-reviews/microsoft/office-2007-in-ubuntu-910-with-wine-1132.html[/HTML]

---

### Post by vikjon0 on 2010-01-03
> The following packages have unmet dependencies:
wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages 

Yes, I also get this in a clean 9.10 installation.
(after adding the beta PPA from wine web site)

I could install it after selecting wine1.2 instead of wine in synaptic. Dont have the exact name, get it from synaptic or I can find it for you later.

the installation seem to work but I am not really happy with the result. The gnome panels are not re-drawned correctly with wine started. This was more or less the same in 1.0.1. Perhaps wine is not stable in 9.10?

---

### Post by Allyanora on 2010-01-03
I have no idea, but that didn't look good to me.

it is true that 9.10 is new and it might have issues. I'm not an expert in this, I am in the stage of learning so from what I see, I think it has some problems.

but maybe later they will be resolved. For now, I use what i have ^_^

---

### Post by 8Kuula on 2010-01-03
```
sudo apt-get remove wine
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.2
```

*cross fingers*

---

### Post by Allyanora on 2010-01-04
uh, and does it work? :-s

---

### Post by 8Kuula on 2010-01-04
For me, it does. But there are many computers with many diffirent configurations. :roll:

---

### Post by hitman_dreams on 2010-01-04
it seems as though you need to use:
   sudo apt-get install wine1.2
The directions say to use:
   sudo apt-get install wine

if you don't add the 1.2 to it, it won't install...at least that's what happened to me.

---

### Post by Allyanora on 2010-01-09
Ok, here is the solution: if you upgrade from 9.04 to 9.10 you won't be able to install wine 1.2, just maybe other older versions.

I have freshly installed 9.10 and i could install wine just fine.

---

### Post by zeroandone on 2010-01-09
If you followed the instruction on Wine website: [www.winehq.org/download](www.winehq.org/download) for adding software source in Ubuntu 9.10, then you need to remember to install wine1.2, not wine. In Synaptic, wine is marked as a dummy package and it is why you got the damaged package error.

---

### Post by weichimaster on 2010-01-10
> **8Kuula said:**
> ```
sudo apt-get remove wine
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.2
```*cross fingers*

Awesome, that fixed it for me.

---

### Post by GhostyGu on 2010-03-20
> **8Kuula said:**
> ```
sudo apt-get remove wine
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.2
```*cross fingers*

I'm a total newby (2 weeks since installing Ubuntu 9.10, Linux virgin) and this solved my problem! Thank-you :thumbs-up:

---

### Post by mine070 on 2010-03-21
I just went into the Software center to download wine and it worked perfectly.

---

### Post by kerrykk on 2010-04-13
I can’t install WINE either.  I downloaded it on a flash drive and when I click on it in Ubuntu 9.10 it says error dependency is not satisfiable. Libaudio2.

---

### Post by Chii1337 on 2010-04-29
okay well, i tried every method on this forum to install wine and i get the terminal output

```
Resolving wine.budgetdedicated.com... 81.171.111.247
Connecting to wine.budgetdedicated.com|81.171.111.247|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-04-29 19:56:55 ERROR 404: Not Found.

```

or when i try to just download a .deb package i get back 
```
Error: Dependency is not satisfiable: libopenal1
```

anybody got any ideas?? 
anything helps!

---

