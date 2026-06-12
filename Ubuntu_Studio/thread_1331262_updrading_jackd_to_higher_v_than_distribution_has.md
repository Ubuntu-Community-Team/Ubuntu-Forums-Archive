---
title: "updrading jackd to higher v than distribution has"
date: 2009-11-19
forum: Ubuntu Studio
---

### Post by gorgon on 2009-11-19
hi all,

so, im still trying to fix [this issue]("http://ubuntuforums.org/showthread.php?t=1330324") and thought I would try to upgrade jackd.But after [this]("http://ubuntuforums.org/showthread.php?t=1330757") I learned that it can be messy to experiment with that without prior knowledge.

So, I wonder, is there a 'safe' way to upgrade jackd to 0.118 or even 0.117 without breaking anything?

the latest distribution packaged version is 0.116.

thanks!
g

---

### Post by trulan on 2009-11-19
Good question.

 I found a ppa that had jack 1.97 (or Jackdmp) and was able to upgrade to that.  However, the higher number doesn't mean newer, just a different variety.  I got decreased stability and was able to go back to the distribution version.  My attempts to build Jack have so far been fruitless (OK, it builds, but then nothing works.)  I haven't found a ppa with 0.118, but that would be the way to go.

---

### Post by gorgon on 2009-11-19
yes, jackd 1.97 is also known as Jack2, while jackd 0.116 etc is just Jack.. 

they work differently but they use the same binary name. all slightly confusing. and their [webpage]("http://jackaudio.org/") does not really tell the difference either.

---

### Post by bluesscream on 2009-11-21
[https://launchpad.net/~frasten/+archive/ppa](https://launchpad.net/~frasten/+archive/ppa)
if you want to give it a try;)

---

### Post by thorgal on 2009-11-21
jack1 (latest is 0.118) : former jack (server, library, etc)
jack2 (latest is 1.9.4) : rewrite of jack1 in C++, but exposing the same C API for backward compatibility.

jack2 does certain things better and will bring (hopefully) some innovations that jack1 cannot.


jack1 and jack2 _installations_ are NOT compatible. As a matter of fact, any multiple installations of jack (1 or 2) is doomed to screw up.

make sure you remove jack before installing a home-compiled one. To do so, you have to install first a fake jack package to respect the dependencies. Removing jack via apt could remove a whole bunch of other apps.

You can get a tip from this debian howto:
[http://www.wickle.com/wiki/index.php/Install_a_dummy_package_to_satisfy_dependencies_on_debian](http://www.wickle.com/wiki/index.php/Install_a_dummy_package_to_satisfy_dependencies_on_debian)

so what you would do is:
-1 build a fake/dummy jack package
-2 install it over your existing install 
-3 compile the jack svn code
-4 install over your dummy package

---

### Post by trulan on 2009-11-21
> **bluesscream said:**
> [https://launchpad.net/~frasten/+archive/ppa]("https://launchpad.net/%7Efrasten/+archive/ppa")
if you want to give it a try;)

Yeah that's the one I've been testing.  It's working pretty well for me now that I've added ohci1394 to rtirq's non-threaded list.  Before that there were xruns galore with my firepod on Jack2.  They are much smaller glitches than I got with Jack1 - you could barely hear them - but there were a lot more of them.  I have been having some pretty serious troubles with the distro version of Jack.  As long as I just used qjackctl and Ardour everything was fine.  But Patchage wouldn't start - said 'error opening bus'.  And I couldn't even open a terminal once jack and ardour were up and running, it would crash and take down Ardour, the gnome panel, and who knows what else.  On Jack2, even with ohci1394 running non-threaded, I still see more xruns than I did on Jack1.  I have to run my latencies a little higher.  But at least I can use Jack as it was meant to be used.  Here's a screenshot, just for fun (check out the new version of Patchage!)

---

