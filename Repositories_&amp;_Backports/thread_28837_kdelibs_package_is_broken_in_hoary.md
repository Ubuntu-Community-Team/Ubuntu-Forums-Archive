---
title: "kdelibs package is broken in hoary"
date: 2005-04-21
forum: Repositories &amp; Backports
---

### Post by Biffy on 2005-04-21
Hi, just did a dist-upgrade in hoary, and it seems that the package kdelibs is broken. Unmet dependencies, it says. The problem is that now, i cant do dist-upgrade again. Seems like i need to fix that package first, and i have no idea how to.

You guys got it too?

---

### Post by rwabel on 2005-04-22
[QUOTE=Biffy]Hi, just did a dist-upgrade in hoary, and it seems that the package kdelibs is broken. Unmet dependencies, it says. The problem is that now, i cant do dist-upgrade again. Seems like i need to fix that package first, and i have no idea how to.

You guys got it too?[/QUOTE]

same for me here, I just downgraded to the normal hoary version. Sooner or later that package will be fixed.

---

### Post by Biffy on 2005-04-22
Yes, but you cant upgrade your system when you have a broken package. I cant do that here.

But i tried running apt-get dist-upgrade -f

There is one upgrade, but when trying to install it says that dpkg returned an error message.

---

### Post by gaboo on 2005-04-22
Same problem here.
It's sad that apt-get cannot handle this.

We cannot install/remove anything because of this package  :-?

How can I downgrade kdelibs ?

---

### Post by mendicant on 2005-04-22
You could just hold the package:

aptitude hold kdelibs-data

You just have to remember to unhold it (by installing it, for instance) when it gets fixed.

---

### Post by Biffy on 2005-04-22
How to hold a package in synaptic? And, are you sure that it is kdelibs-data that should be put on hold? kdelibs is the package that is broken.

I just tried upgrading kdelibs-data again but got the same error message.

---

### Post by mendicant on 2005-04-22
[QUOTE=Biffy]And, are you sure that it is kdelibs-data that should be put on hold? kdelibs is the package that is broken.
[/QUOTE]

Then I guess we're getting different errors.  I get:
```

Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf

```

which I could fix manually, but it's not a big deal.  You could also just change the version.  In aptitude, you just hit enter when you have the package selected and select the version at the bottom of the page.  In synaptic, you can choose Package->Force Version.

I don't know how to hold packages in synaptic--I don't use it.

---

### Post by Biffy on 2005-04-22
```
Preconfiguring packages ...
(Läser databasen ... 144089 filer och kataloger installerade.)
Förbereder att ersätta kdelibs-data 4:3.4.0-0ubuntu3 (med .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Packar upp ersättande kdelibs-data ...
dpkg: fel vid hantering av /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 försöker skriva över "/usr/share/icons/default.kde" som också finns i paketet knetworkconf
Fel uppstod vid hantering:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thats my error message, looks like the same error you get. I got Swedish language. :)

So, kdelibs needs kdelibs-data3.1 to work, but the installed version is 3.0 . If i choose to force version, i can choose between 3.0 or 3.1 . If i choose 3.1 , i get the same error message.

Will Ubuntu-team fix this?

---

### Post by gaboo on 2005-04-22
I can't understand how apt-get works. I'm new to using it.

I know kdelibs package is currently broken. Well, I just have to wait untill it's fixed.

I can understand that packages depending on it cannot be installed.
But why  a packages which have nothing to do with kdelibs can't be installed ? It's very frustrating : because of this bug, I can't remove or add any other packages, I keep having the same error.

Or I am just too newbie ?
I tried to hold the packages. Same error.

---

### Post by mendicant on 2005-04-22
Right.  The intention of my advice to force version was to force it to 3.0.  Clearly, the security update isn't quite ready (particularly since it isn't listed as a security update yet).  If you do force the version, you would have to do so for kdelibs and kdelibs-data, I assume.

For aptitude, just run aptitude, search for kdelibs-data (/kdelibs-data<enter>), put it on hold (=), go to the next broken package (b), which will be kdelibs, press enter, go to the end of the page and select (+) the 4:3.4.0-0ubuntu3 package.  This will downgrade kdelibs after you install it (g).  Then, search for kdelibs, and put it on hold (=).  Now you can install anything else you want.

Under synaptic, I imagine you just force the version to the ubuntu3 for kdelibs-data and kdelibs packages and install them, and you'll be done.

---

### Post by mendicant on 2005-04-22
[QUOTE=gaboo]I can't understand how apt-get works. I'm new to using it.
[/QUOTE]

You should probably use aptitude instead:

[http://lists.debian.org/debian-user/2004/04/msg11344.html](http://lists.debian.org/debian-user/2004/04/msg11344.html)

[QUOTE=gaboo]
But why  a packages which have nothing to do with kdelibs can't be installed ? It's very frustrating : because of this bug, I can't remove or add any other packages, I keep having the same error.
[/QUOTE]

I can't remove things without fixing the problem, but I can install other packages.  I just tried to upgrade kdelibs, kdelibs-data and install mgetty (which was previously not installed).  mgetty installed just fine.  There could be other ordering constraints depending on the package (maybe something else in the kde section would not install, for instance), but you can install some stuff.

I think it won't remove things because of this ordering issue.  It prefers to upgrade the kdelibs stuff, before removing things, and stops at the first error.

However, following the directions I gave in my previous post for aptitude works.  It's what I just did, and I can remove and install anything else I want.

---

### Post by gaboo on 2005-04-22
Thank you medicant. I've learnt something today :)

So it works, I can install packages now. But aptitude removed 20+ packages including some core kde packages. My k-menu disapeared and several other programs were removed. Dunno why it did that :S
I think if I reboot, kde won't start lol

I'm going to try to install them again :) Sure I'm not far from breaking my first ubuntu ! :p

edit: I notices that the first package to be removed was kde-devel. I tried a "apt-get install kde-devel" and everything's back ! Whooo. Ok now my system is fixed, all I have to do I wainting for broken packages updates. Thanks again medicant.

---

### Post by mendicant on 2005-04-22
Whoa!  It's a bit surprising that it removed stuff--did it warn you at least?  aptitude will warn me of what it's about to do, and if I see anything getting removed without my explicit say so, I stop it immediately, and correct whatever is going on that makes it think it should remove those packages.

My sincerest apologies if my advice screwed up KDE for you.  You should at least make sure that kubuntu-desktop is installed correctly.

---

### Post by gaboo on 2005-04-22
[QUOTE=mendicant]
My sincerest apologies if my advice screwed up KDE for you.  You should at least make sure that kubuntu-desktop is installed correctly.[/QUOTE]

No pb, kubuntu desktop hasn't been removed. And everything's now installed. 
aptitude didn't warn me, when I hit 'g' ... badaboom ;)

Surprisingly, It has also removed mozilla-forefox and installed mozilla-browser instead.
I think I made something wrong while in aptitude :)
But it(s ok now.

---

### Post by mendicant on 2005-04-22
Ah.  I see. In the curses interface, you may have to use pagedown to see everything that it plans to do.  Interesting.  Maybe they should put the packages to be removed at the very top, as a bigger warning.

---

### Post by Biffy on 2005-04-22
I just really want to know if the Ubuntu-team is working on this, because i can wait. Dont know why, but it does not feel good to force packages and stuff.

---

### Post by Biffy on 2005-04-22
Problem solved. This is how to fix it:

if knetworkconf is the package interfering, just remove it. Then upgrade kdelibs-data , it should be upgraded to 3.1 .

Done! No more broken packages.  :)

---

### Post by mendicant on 2005-04-22
Well, in 'forcing' the package, you're just going back to a working version.  Removing knetworkconf means you've gotten rid of some functionality.  Reverting to an older version of the package means you've lost no functionality.

---

### Post by Biffy on 2005-04-23
But i can just reinstall knetworkconf. Its as simple as that.

---

### Post by mendicant on 2005-04-23
Except that you'll now get the error trying to install knetworkconf, because presumably, there is  still a file in conflict with kdelibs-data.

---

### Post by rwabel on 2005-04-23
I don't care about the new version of kdelibs. that's why I just forced apt (you can do that simple in synaptic) to use the version from hoary instead of the version from hoary security stuff.

---

### Post by Biffy on 2005-04-23
[QUOTE=mendicant]Except that you'll now get the error trying to install knetworkconf, because presumably, there is  still a file in conflict with kdelibs-data.[/QUOTE]

You are probably right. But, knetworkconf isnt a program i need anyway.

---

### Post by rolo on 2005-04-25
I had the same problem mentioned in this thread and my solution was to use synaptic: 1) remove kdelibs-data (it will also remove kubuntu-desktop), 2) install kdelibs-data (security version) and kubuntu-desktop. Knetworkconf is not a problem because the updated version is installed as part of kdelibs-data.

Hope it may help.

---

### Post by rosslaird on 2005-04-25
If I use synaptic as indicated above, it wants to remove every single kde app.

I'm hoping this gets fixed soon, as none of the suggested fixes seem to quite work as indicated on my system.

I suppose I could take this opportunity to learn more about the aptitude system, but for once I don't want to. I have to do my taxes this week instead...

---

### Post by Tm_T on 2005-04-26
Seems like there's script that fixes this annoying problem, it may not work for everyone, but worked to me just fine.

[http://moba.linuxfaqs.de/kdelibs-debug.sh](http://moba.linuxfaqs.de/kdelibs-debug.sh)

And props goes to KaiL, he  wrote it.

---

### Post by rosslaird on 2005-04-26
Yup, the script works.
In case you're interested, here's the script itself:


#!/bin/bash
# Kai F. Lahmann <kl@3dots.de>
# this repair every known damage made by the kdelibs update in hoary-security.
# the script needs to be run as root - so 'sudo sh kdelibs-debug.sh'

#kdelibs-data
dpkg -i --force-overwrite /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubunt$
# /etc/kderc get's deleted, so we restore it
echo "[Directories]" > /etc/kderc
echo "userProfileMapFile=/etc/kde-user-profile" >> /etc/kderc
echo >> /etc/kderc
echo "[Directories-default]" >> /etc/kderc
echo "prefixes=/usr/share/kubuntu-default-settings/kde-profile/default/" >> /et$
# kcontrol repair
apt-get install --reinstall kcontrol

---

### Post by paul cooke on 2005-04-27
[QUOTE=rosslaird]Yup, the script works.
In case you're interested, here's the script itself:


#!/bin/bash
# Kai F. Lahmann <kl@3dots.de>
# this repair every known damage made by the kdelibs update in hoary-security.
# the script needs to be run as root - so 'sudo sh kdelibs-debug.sh'

#kdelibs-data
dpkg -i --force-overwrite /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubunt$
# /etc/kderc get's deleted, so we restore it
echo "[Directories]" > /etc/kderc
echo "userProfileMapFile=/etc/kde-user-profile" >> /etc/kderc
echo >> /etc/kderc
echo "[Directories-default]" >> /etc/kderc
echo "prefixes=/usr/share/kubuntu-default-settings/kde-profile/default/" >> /et$
# kcontrol repair
apt-get install --reinstall kcontrol[/QUOTE]


the script is NOT the solution... the solution is in removing the update from the security update repository until it is actually ready to release... currently in this borked form, it is causing no end of problems... my synaptic keeps on insisting in upgrading kdelibs even though everytime it does, it then reports it to be be broken and I have to force it back to v3... and then it tries it on again the next time I want to install a package...

Currently, I've disabled the security updates repository and am waiting for the update to be announced the correct way, rather than have it slipped in to the repository with no announcement when it patently isn't ready...

---

### Post by rwabel on 2005-04-27
[QUOTE=paul cooke]the script is NOT the solution... the solution is in removing the update from the security update repository until it is actually ready to release... currently in this borked form, it is causing no end of problems... my synaptic keeps on insisting in upgrading kdelibs even though everytime it does, it then reports it to be be broken and I have to force it back to v3... and then it tries it on again the next time I want to install a package...

Currently, I've disabled the security updates repository and am waiting for the update to be announced the correct way, rather than have it slipped in to the repository with no announcement when it patently isn't ready...[/QUOTE]

just force the ubuntu version to update and then lock it. this prevents your system to get upgraded by the newer version from the ubuntu secutiry repository.

---

### Post by mendicant on 2005-04-27
[QUOTE=paul cooke]the script is NOT the solution...[/QUOTE]

Agreed.  Anything that borks /etc/kderc (or anything else you have installed) should not be installed.

---

### Post by Tm_T on 2005-04-28
And still, that script is mentioned in #Kubuntu @ freenode as a solution. :)
As long as people who I trust advise me to do so, I do so. ;)

---

### Post by Azrayal on 2005-04-30
I've been using ubuntu now for a few weeks and I've encountered the same issue. That script worked a charm. 

Thanks.  :)

---

### Post by Tm_T on 2005-05-04
Ok now I have to say, be careful with that script, I noticed that some KDE configurations doesn't work correctly anymore (or at all). I don't know if it's just me or if that "new" kdelibs-data is broken. we'll see how it goes...

---

### Post by mendicant on 2005-05-04
I do wish they'd get rid of those packages from security.  The only kdelibs* security update they've announced works fine (kdelibs4, kdelibs-bin, from [http://ubuntuforums.org/showthread.php?t=31425)](http://ubuntuforums.org/showthread.php?t=31425)), so I'm puzzled as to why those other packages are there.

---

### Post by rwabel on 2005-05-04
thanks for the link. I tried to install these 3 packages, but it didn't help. Did it work for you?

---

### Post by mendicant on 2005-05-04
They worked fine for me.  I just used the 'normal' procedure (via aptitude dist-upgrade, for instance), and holding the kdelibs and kdelibs-data packages.

```

% COLUMNS=120 dpkg --list kdelibs4 kdelibs-bin kdelibs4-dev kdelibs kdelibs-data
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  kdelibs4                 3.4.0-0ubuntu3.1         KDE core libraries
ii  kdelibs-bin              3.4.0-0ubuntu3.1         KDE core binaries
No packages found matching kdelibs4-dev.
ii  kdelibs                  3.4.0-0ubuntu3           KDE core libraries metapackage
ii  kdelibs-data             3.4.0-0ubuntu3           KDE core shared data

```

You'll notice that I have kdelibs and kdelibs-data at their original versions (not the available ubuntu3.1), which allows everything to upgrade properly.

---

### Post by rwabel on 2005-05-04
I tried to install the 3 deb files via dpkg but didn't work.
How did you install these 3 deb files, they gave me same conflict.
[QUOTE=mendicant]They worked fine for me. I just used the 'normal' procedure (via aptitude dist-upgrade, for instance), and holding the kdelibs and kdelibs-data packages.

```

% COLUMNS=120 dpkg --list kdelibs4 kdelibs-bin kdelibs4-dev kdelibs kdelibs-data
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                     Version                  Description
+++-========================-========================-================================================================
ii  kdelibs4                 3.4.0-0ubuntu3.1         KDE core libraries
ii  kdelibs-bin              3.4.0-0ubuntu3.1         KDE core binaries
No packages found matching kdelibs4-dev.
ii  kdelibs                  3.4.0-0ubuntu3           KDE core libraries metapackage
ii  kdelibs-data             3.4.0-0ubuntu3           KDE core shared data

```

You'll notice that I have kdelibs and kdelibs-data at their original versions (not the available ubuntu3.1), which allows everything to upgrade properly.[/QUOTE]

---

### Post by mendicant on 2005-05-05
What error are you getting?  If it's related to kdelibs or kdelibs-data, I've posted in this thread about how to hold them using aptitude.

---

### Post by Tm_T on 2005-05-12
[QUOTE=Tm_T]Ok now I have to say, be careful with that script, I noticed that some KDE configurations doesn't work correctly anymore (or at all). I don't know if it's just me or if that "new" kdelibs-data is broken. we'll see how it goes...[/QUOTE]
heh, looks like that was temporary, must be one of those "user errors" then ;)

---

### Post by rwabel on 2005-05-13
Follow that thread for solving the kdelibs problem
[http://ubuntuforums.org/showthread.php?t=28721]("http://ubuntuforums.org/showthread.php?t=28721")

---

