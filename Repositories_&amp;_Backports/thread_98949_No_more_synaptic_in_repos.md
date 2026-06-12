---
title: "No more synaptic in repos?"
date: 2005-12-04
forum: Repositories &amp; Backports
---

### Post by Heretic09 on 2005-12-04
When I try to apt-get synaptic I get an error:

Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate

I'm on kubuntu but I prefer synaptic over adept.

I have the following sources:
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas all
deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas all

deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://eyagi.bpa.nu/~jamie/ubuntu](http://eyagi.bpa.nu/~jamie/ubuntu) breezy main restricted universe multiverse
deb-src [http://eyagi.bpa.nu/~jamie/ubuntu](http://eyagi.bpa.nu/~jamie/ubuntu) breezy main restricted universe multiverse

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

While on the subject of repos, anyone know another source for freenx other than seveas? When I try to apt-get it I get the following error:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freenx: Depends: expect but it is not installable
E: Broken packages

---

### Post by GreyFox503 on 2005-12-04
I'm using Synaptic with Gnome, and it shows that the "synaptic" package is still there when I search for it.  I'm not sure what your error means, though.

---

### Post by Heretic09 on 2005-12-04
Well if you're using ubuntu then it comes preinstalled and so will show up fine on the list. But if you're using kubuntu it will not get it from the repos. Only reason I can think of is that the package is no longer in the repository becuase it doesn't complain of a dependency issue just that it can't find the package itself..

---

### Post by GreyFox503 on 2005-12-04
I just noticed at the bottom of the error it says:

The following packages have unmet dependencies:
  freenx: Depends: expect but it is not installable
E: Broken packages


Maybe you need to fix this dependency before installing synaptic. It doesn't like something about freenx.  I've never used that so I don't know much about it.  I don't know how KDE does this because I've never used it's package manager, but try poking around in its menus to find something about resolving or fixing broken packages.

---

### Post by teaker1s on 2005-12-04
you should be able to get it locally off cd

---

### Post by Heretic09 on 2005-12-04
The error message when trying to install synaptic is:

E: Package synaptic has no installation candidate

the errror message "E: Broken packages" is from when I try to install freenx (another problem)

I may be able to get it off the cd (dunno since its a kubuntu cd), I just find it curious that its no longer available on the repos.

---

### Post by noigeaR on 2005-12-09
I'm using Kubuntu and I have Synaptic in my repositories. I've installed Synaptic through adept, but if this doesn't work for you, try installing it from the terminal with```
sudo apt-get update
sudo apt-get install synaptic
```

---

### Post by noigeaR on 2005-12-09
Something different I've just noticed. Why haven't you got main and restricted sections from the official archive.ubuntu.com in your sources.list?

This is missing:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted

and I guess that's where your synaptic is...

---

