---
title: "amaroK 1.3.7 - Error"
date: 2006-01-05
forum: Ubuntu Backports
---

### Post by PereUbu on 2006-01-05
This message is popping up when I try to start amaroK 1.3.7:

> Error amaroK
amaroK could not find any sound-engine plugins. amaroK is now updating the KDE configuration database. Please wait a couple of minutes, then restart amaroK.
If this does not help, it is likely that amaroK is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.

All needed sound-engine plugins are installed, and amaroK worked like a charm before upgrading to 1.3.7. Any ideas how to solve this?


Best regards 
PereUbu

---

### Post by PereUbu on 2006-01-05
Hello again

I gave up :(  
Downgraded to amarok 1.3.1 again, which work fine.

Something must be wrong with the backport, though.

Hope you find out!

PS! I used this backport: deb [http://kubuntu.org/packages/amarok-1.3.7](http://kubuntu.org/packages/amarok-1.3.7) breezy main

---

### Post by noigeaR on 2006-01-07
amarok 1.3.7 from kubuntu.org works fine here.
there's now also an official backport of amarok 1.3.7 in the breezy-backports repository. maybe this works better for you than the one from kubuntu?

---

### Post by PereUbu on 2006-01-07
I am afraid the backports are two of a kind. I get the same error message when installing amarok 1.3.7 in the breezy-backports repository. (I did an apt-get clean, before apt-get install and watched it download from the breezy-backports repository)

Thanx for your help, anyway ;) 

PereUbu

[IMG]http://static.flickr.com/43/83543325_b8dc610f3d.jpg[/IMG]

---

### Post by tongue on 2006-01-09
I get exactly the same error.. 

So if anyone has any idéa how to fix this, please respond

---

### Post by noigeaR on 2006-01-09
what's your kde version? i've upgraded to kde 3.5 (from kubuntu repository) and amarok 1.3.7 works here, so maybe the backports have a problem with kde 3.4.3?

---

### Post by tongue on 2006-01-09
Im not using KDE, im a gnome user. :)

---

### Post by Velvet Elvis on 2006-01-09
Add these two lines to your /etc/apt/sources.list

```
deb http://kubuntu.org/packages/kde35 breezy main
deb http://kubuntu.org/packages/amarok-1.3.7 breezy main

```

sudo apt-get update
sudo apt-get dist-upgrade

and you should be in business.

All the kde libraries and core aps will be upgraded to the 3.5 versions as well.  Depending on what you have installed, it might be a lot of packages, but it's well worth it, IMHO.

---

### Post by noigeaR on 2006-01-09
according to this page [http://packages.ubuntu.com/breezy-backports/kde/amarok](http://packages.ubuntu.com/breezy-backports/kde/amarok)
amarok 1.3.7 from breezy-backports shouldn't acutally depend on kdelibs 3.5 but still on the 3.4.3 from the main breezy repo. so installing the 3.5 kdelibs and all their dependencies is overkill and shouldn't be necessary at all...
maybe there's a dependency bug in the backports package. i'll send jdong a pm about that.

---

### Post by jdong on 2006-01-09
Make sure that either amarok-gstreamer or amarok-xine is installed.

---

### Post by tjabri on 2006-01-09
I just did an apt-get clean and apt-get install amarok amarok-gstreamer and I have the same problem...

---

### Post by PereUbu on 2006-01-15
> Add these two lines to your /etc/apt/sources.list

Code:

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main deb [http://kubuntu.org/packages/amarok-1.3.7](http://kubuntu.org/packages/amarok-1.3.7) breezy main


sudo apt-get update
sudo apt-get dist-upgrade

and you should be in business.

All the kde libraries and core aps will be upgraded to the 3.5 versions as well. Depending on what you have installed, it might be a lot of packages, but it's well worth it, IMHO.

Thank U Velvet Elvis!

Upgrading kde packages to 3.5 did the trick. Amarok 1.3.7 works fine now.

Greetings from 
Pere Ubu

---

### Post by DDM on 2006-01-15
Upgrade to 3.5 worked for me too. Thanks, I came close to wiping my / out of frustration.

---

### Post by TradeMark on 2006-05-05
Yeah that worked awesomely for me too. Unfortunately I think I broke something else in my floundering about trying to fix it :'( ahhh well.

---

