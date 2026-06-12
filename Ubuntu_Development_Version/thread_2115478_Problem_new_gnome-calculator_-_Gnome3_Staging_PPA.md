---
title: "Problem: new gnome-calculator - Gnome3 Staging PPA"
date: 2013-02-13
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-02-13
There is a new gnome-calculator (3.7.5) in the Gnome3 Staging PPA.
Also there is a new transitional gcalctool (3.7.5) package to ease the transition from gcalctool to gnome-calculator.

However, upgrading gcalctool from the recent version (6.6.2) to the new 3.7.5 version is not succesfull.
This is because this upgrade also installs gnome-calculator and there is an error overwriting one same package.

Transition is perhaps possible manually by simply first removing the recent gcalctool (6.6.2) and then installing the gnome-calculator (3.7.5).

Gnome-calculator (3.7.5) breaks and replaces gcalctool (<< 3.7.0)
Gcalctool (3.7.5) depends on gnome-calculator.

---

### Post by zika on 2013-02-13
> **Harry33 said:**
> There is a new gnome-calculator (3.7.5) in the Gnome3 Staging PPA.
Also there is a new transitional gcalctool (3.7.5) package to ease the transition from gcalctool to gnome-calculator.

However, upgrading gcalctool from the recent version (6.6.2) to the new 3.7.5 version is not succesfull.
This is because this upgrade also installs gnome-calculator and there is an error overwriting one same package.

Transition is perhaps possible manually by simply first removing the recent gcalctool (6.6.2) and then installing the gnome-calculator (3.7.5).

Gnome-calculator (3.7.5) breaks and replaces gcalctool (<< 3.7.0)
Gcalctool (3.7.5) depends on gnome-calculator.No need to purge gcalctool, simple```
sudo apt-get install -f
```does the trick... At least here on my machine...

---

### Post by VinDSL on 2013-02-13
> **Harry33 said:**
> Transition is perhaps possible manually by simply first removing the recent gcalctool (6.6.2) and then installing the gnome-calculator (3.7.5).

Gnome-calculator (3.7.5) breaks and replaces gcalctool (<< 3.7.0)
Gcalctool (3.7.5) depends on gnome-calculator.
I get these type of (dependency) errors in Synaptic, from time-to-time.

And, 99% of the time, clicking "Apply" a second time fixes it.  ;)

```
vindsl@Zuul:~$ apt-cache policy gnome-calculator
gnome-calculator:
  Installed: 1:3.7.5-0ubuntu1~raring1
  Candidate: 1:3.7.5-0ubuntu1~raring1
  Version table:
 *** 1:3.7.5-0ubuntu1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status


vindsl@Zuul:~$ apt-cache policy gcalctool
gcalctool:
  Installed: 1:3.7.5-0ubuntu1~raring1
  Candidate: 1:3.7.5-0ubuntu1~raring1
  Version table:
 *** 1:3.7.5-0ubuntu1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     6.6.2-0ubuntu1 0
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/main i386 Packages
     6.6.0-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main i386 Packages
```

It's as if the upgrades are installed out-of-order.

In this case, everything was upgraded on the first try, except gcalctool.  Then, clicking "Apply" a second time did the trick.

---

### Post by Harry33 on 2013-02-13
> **VinDSL said:**
> I get these type of (dependency) errors in Synaptic, from time-to-time.

And, 99% of the time, clicking "Apply" a second time fixes it.  ;)

```
vindsl@Zuul:~$ apt-cache policy gnome-calculator
gnome-calculator:
  Installed: 1:3.7.5-0ubuntu1~raring1
  Candidate: 1:3.7.5-0ubuntu1~raring1
  Version table:
 *** 1:3.7.5-0ubuntu1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status


vindsl@Zuul:~$ apt-cache policy gcalctool
gcalctool:
  Installed: 1:3.7.5-0ubuntu1~raring1
  Candidate: 1:3.7.5-0ubuntu1~raring1
  Version table:
 *** 1:3.7.5-0ubuntu1~raring1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/ raring/main i386 Packages
        100 /var/lib/dpkg/status
     6.6.2-0ubuntu1 0
        500 http://samaritan.ucmerced.edu/ubuntu/ raring/main i386 Packages
     6.6.0-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main i386 Packages
```It's as if the upgrades are installed out-of-order.

In this case, everything was upgraded on the first try, except gcalctool.  Then, clicking "Apply" a second time did the trick.

Fine, but did you then remove gcalctool (3.7.5) as it is only a transitional package helping the installation of gnome-calculator?

---

### Post by zika on 2013-02-13
At the same time there was gnomine (transitional package) and gnome-mines (new package) Did You remove gnomine? ... ;)
They are transitional only in in Gnome3 PPA, not in raring universe... Removing them might jeopardize possible ppa-purge, is not that true?

---

### Post by Harry33 on 2013-02-13
> **zika said:**
> At the same time there was gnomine (transitional package) and gnome-mines (new package) Did You remove gnomine? ... ;)
They are transitional only in in Gnome3 PPA, not in raring universe... Removing them might jeopardize possible ppa-purge, is not that true?

In case of gcalctool and gnome-calculator, the fact is that gcalctool is now the old name of the application. The new name for the same application is now gnome-calculator.

You can very easily find this out by first purging gcalctool and after that installing gnome-calculator.

The job that a transitional package here does is that you can install a new package by only upgrading the old package. After that the transitional package has nothing to do in your system any more and it can be removed.

---

### Post by zika on 2013-02-13
> **Harry33 said:**
> In case of gcalctool and gnome-calculator, the fact is that gcalctool is now the old name of the application. The new name for the same application is now gnome-calculator.

You can very easily find this out by first purging gcalctool and after that installing gnome-calculator.

The job that a transitional package here does is that you can install a new package by only upgrading the old package. After that the transitional package has nothing to do in your system any more and it can be removed.
All that You wrote is OK. But, only caveat that I have is that these packages are yet not available in Raring and they are from a PPA that is a step ahead of RR... So, I was only cautious... Nothing more or less...
As far as I remember (I've just checked /var/apt/history.log) these were available only as dist-upgrade... I still fear that by removing them ppa-purge of PPA would be a bit harder than without...Bitten by the snake so I fear of lizard...
I've tried to purge them at my place, but... If I try to purge gcalctool Synaptic wants to take ubuntu-desktop and gnome-calculator with it... That's my machine...
```
:~$ sudo apt-get purge gcalctool 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-calculator gstreamer1.0-alsa gstreamer1.0-plugins-base-apps
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gcalctool* ubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 125 kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
```If I do not ask for removal of gcalctool autoremove doesn't offer any package to be removed...

---

### Post by jbicha on 2013-02-13
I don't recommend removing the transitional packages in the GNOME3 Staging PPA as the metapackages (like ubuntu-desktop in the previous comment) have not been updated for the new names and won't until the new packages are in the regular Ubuntu repositories. The transitional packages are empty packages and do not hurt anything but do ensure that dependencies work.

---

### Post by Harry33 on 2013-02-14
> **jbicha said:**
> I don't recommend removing the transitional packages in the GNOME3 Staging PPA as the metapackages (like ubuntu-desktop in the previous comment) have not been updated for the new names and won't until the new packages are in the regular Ubuntu repositories. The transitional packages are empty packages and do not hurt anything but do ensure that dependencies work.

Right, of course that is true regarding the meta packages.
Me, I retain more freedom for myself by removing the meta packages from my setup.
That, in turn, allows me to remove the packages and applications I do not use or need.

---

