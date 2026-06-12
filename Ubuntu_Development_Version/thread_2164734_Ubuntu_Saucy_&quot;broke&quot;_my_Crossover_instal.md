---
title: "Ubuntu Saucy &quot;broke&quot; my Crossover installation"
date: 2013-08-01
forum: Ubuntu Development Version
---

### Post by rrohde on 2013-08-01
A couple of days ago I noticed that apt-get dist-upgrade removed my ia32-crossover installation. 

I haven't been able to reinstall Crossover ever since, and this is the one and only application I really *need* for work, as I am forced to use MS Office to create content. 

When attempting to install Crossover from the CLI, I get the following:

dpkg -i ia32-crossover_12.2.2-1_amd64.deb 
Selecting previously unselected package ia32-crossover.
(Reading database ... 326525 files and directories currently installed.)
Unpacking ia32-crossover (from ia32-crossover_12.2.2-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of ia32-crossover:
 ia32-crossover depends on libc6-i386; however:
  Package libc6-i386 is not installed.
 ia32-crossover depends on ia32-libs; however:
  Package ia32-libs is not installed.
 ia32-crossover depends on lib32gcc1; however:
  Package lib32gcc1 is not installed.
 ia32-crossover depends on lib32nss-mdns; however:
  Package lib32nss-mdns is not installed.
 ia32-crossover depends on lib32z1; however:
  Package lib32z1 is not installed.
 ia32-crossover depends on lib32asound2; however:
  Package lib32asound2 is not installed.

dpkg: error processing ia32-crossover (--install):
 dependency problems - leaving unconfigured
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Errors were encountered while processing:
 ia32-crossover


When attempting install via Software Center, I get the following (see screenshots):
[http://screencloud.net//img/screenshots/5856cf84438af4e929126e6bb8556847.png](http://screencloud.net//img/screenshots/5856cf84438af4e929126e6bb8556847.png)

Please advise. Needless to say, besides all the other issues (mouse not working, ACPI calls to function keys not working, etc), this is almost the final nail in the Ubuntu coffin for me :(

---

### Post by cariboo on 2013-08-01
If you are having so many problems, why in the world are you using a development version.

Even though Saucy is relatively stable, we still do advise that you keep a previous version around, just in case problems like this turn up.

---

### Post by howefield on 2013-08-01
ia32-libs is gone, kaput, no more.

I'm not sure but you might need to wait for the next release of Crossover with revised dependencies (or use 12.04.2 eg). I'll be looking for a solution at the weekend when time is less pressing.

Teamviewer also borked on me but was able to fix that one.

---

### Post by rrohde on 2013-08-01
> **cariboo907 said:**
> If you are having so many problems, why in the world are you using a development version.

Even though Saucy is relatively stable, we still do advise that you keep a previous version around, just in case problems like this turn up.

Well, if it wasn't for folks saying that with the automated test cases each and every development version should be stable and usable, I probably wouldn't do this. 

The issues that I noted regarding mouse and ACPI calls are regressions. The complete loss of ia32-libs is a genuine new issue...

---

### Post by rrohde on 2013-08-01
> **howefield said:**
> ia32-libs is gone, kaput, no more.

I'm not sure but you might need to wait for the next release of Crossover with revised dependencies (or use 12.04.2 eg). I'll be looking for a solution at the weekend when time is less pressing.

Teamviewer also borked on me but was able to fix that one.

Thanks for the heads-up.

---

### Post by mc4man on 2013-08-01
I'd expect that by release Crossover will  release a new deb that's more in line with how things are done now (and recently.

The ia32-libs doesn't really matter, just a metapackage & for the most part all that crossover needs is available. 
Atm it's still using *-i386 as deps instead of *:i386,  but most are still there in *-i386. 
Ex. - 
libc6-i386 is installable, installs to /lib32 & /usr/lib32
libc6:i386 is also available, installs to /lib/i386-linux-gnu & /usr/lib/i386-linux-gnu (the current preferred way

The only package missing that it needs is lib32asound2, that's no longer in 13.10, it's now libasound2/libasound2:i386 only

So other than that,  the current ia32-crossover_12.2.2-1_amd64.deb could be installed in 13.10 with no alsa support if one did a little work on the .deb & in synaptic. 
(or possibly link the various libasound2 .so's..
Though I'd say waiting for it to upgrade or going back to an earlier Ubuntu would be better choice. (or maybe use an i386 install if inclined.

screen shows it installed on a amd64 13.10 I just put up to test something, seems to work ok in a very limited trial, (installed & ran winrar),  not really advised.

---

### Post by grahammechanical on 2013-08-02
> [COLOR=#000000]Well, if it wasn't for folks saying that with the automated test cases each and every development version should be stable and usable, I probably wouldn't do this. [/COLOR]

Ah!, but saucy is still working is it not? So, saucy is stable and apt-get dist-upgrade did what it is supposed to do.

> [COLOR=#333333][FONT=Ubuntu]It tells APT to use "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less important ones if necessary.[/FONT][/COLOR]

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

The upgrade did not break saucy. It broke an application that depended on libraries that were no longer part of saucy. As you have noticed the Software Centre will not install it for us because of the need to keep the development branch stable.

If you are looking for nails, this one is as good as the others. Get the hammer out.

Regards.

---

### Post by jfernyhough on 2013-08-02
> **rrohde said:**
> A couple of days ago I noticed that apt-get dist-upgrade removed my ia32-crossover installation. 

I haven't been able to reinstall Crossover ever since, and this is the one and only application I really *need* for work, as I am forced to use MS Office to create content. 
You could always install Windows in a virtual machine while waiting for Crossover to support Saucy (and Jessie).

---

### Post by rrnbtter on 2013-08-02
Greetings,
rrohde, I don't know what posts you have been reading but you probably shouldn't be using a dev version unless you can sustain a complete OS crash. There are over 10,000 softwares available for linux and I can't tell you how many still don't work in Raring much less Saucy. The switch from trayicons to indicators bleeped quite a few. My favorite Kompozer was missing from the repos for a few versions though it was hackable. It is up to the software devs to keep up with the OS and many don't try until the final release. Ubuntu uses the LTS to keep compatibility for business users and others that are easily scared. The VM suggestion is a good idea. For myself, I keep a copy of Windows 7 on an alternate HD to update my TomTom and do my Taxes once a year. Be careful! Just saying!

P.S. Oh! and don't forget to backup!

---

### Post by JMB74 on 2013-08-03
Do either of the workarounds here help: [https://www.codeweavers.com/support/forums/general/?t=26;msg=146859](https://www.codeweavers.com/support/forums/general/?t=26;msg=146859)

---

### Post by bmbaker on 2013-08-05
just tested using [http://media.codeweavers.com/pub/crossover/cxlinux/demo/install-crossover-12.2.1.bin](http://media.codeweavers.com/pub/crossover/cxlinux/demo/install-crossover-12.2.1.bin)
to reinstall crossover it works with sketchup and had no issues installing. hope this helps.

---

### Post by ianmillington on 2013-09-13
> **howefield said:**
> ia32-libs is gone, kaput, no more.


Teamviewer also borked on me but was able to fix that one.

Hi - I installed the kubuntu 13.10 issue last night and ran into this issue. Teamviewer was uninstalled in the process and won't reinstall due to lib32asound2 no longer being available. I note you had the same issue so wonder whether you can let me know how you were able to fix it please? 

Much obliged

Ian

---

### Post by JMB74 on 2013-09-13
Are you using the new version 12.5 of crossover? That seems to survive an upgrade to 13.10 for me anyway.

---

### Post by ianmillington on 2013-09-13
No I'm not using Crossover at all. I have vanilla wine as there is 1 windows program on my computer (an educational one that my wife uses at the school where she works) and that has survived the upgrade.

What I'm talking about is Teamviewer - it's a remote desktop application. It ships as a .deb file, but underneath it is a windows application packaged with it's own version of Wine: A bit like Picassa used to be when Google offered a Linux version. I imagine that the version of wine being shipped within the package will be pretty old and thus requires lib32asound2. If  this change is being implemented across the Linux ecosystem I do hope someone's talking to the Teamviewer developers!

---

### Post by ianmillington on 2013-09-13
Okay, the answer was on the Teamviewer install page - it seems they know about it.

The solution is to install the teamviewer.deb file, as opposed to the 64bit one. Problem solved!

---

### Post by JMB74 on 2013-09-13
> **ianmillington said:**
> What I'm talking about is Teamviewer 

Sorry. Missed that.

Glad you got it sorted anyway. :)

---

### Post by ianmillington on 2013-09-13
Not a problem - thanks for showing an interest.

As an aside, I have had pretty much the same experience with Google Earth today. The 64 bit deb file would not install due to missing ialibs32. Solved by installing the 32 bit package. Wonder how many more external programs will be affected by this.

---

### Post by ZoiaGuyver on 2013-09-13
As was said ia32-libs is gone, its not a "new issue" as no other distro has them anyways. Most the stuff now use a "multiarch" package meaning it can support both 32 and 64bits. What you have with Crossover is partly you jumping into a still in development release, the other problem is Crossover itself not using Multiarch and requiring the 32 bit only libraries, you "could" manually install them if it was really necessary but it's not advisable in any way.

---

### Post by HDave on 2013-10-18
> **ianmillington said:**
> Okay, the answer was on the Teamviewer install page - it seems they know about it.

The solution is to install the teamviewer.deb file, as opposed to the 64bit one. Problem solved!

Thanks a lot for this -- was struggling with the missing library and this did the trick for Teamviewer.

---

