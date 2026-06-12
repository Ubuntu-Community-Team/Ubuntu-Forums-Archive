---
title: "Ubuntu 12.04 LTS dependency problem for unity,no desktop environment"
date: 2012-03-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by AzharHafiz.com on 2012-03-13
Hi,

Yes i understand 12.04 LTS hasn't been released yet

did an update yesterday (to the latest release) and received this error

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity : Depends: libbamf3-0 (>= 0.2.108) but it is not going to be installed
         Depends: libgl1-mesa-glx but it is not going to be installed or
                  libgl1
         Depends: libglew1.6 (>= 1.6.0) but it is not going to be installed
         Depends: libgnome-desktop-3-2 (>= 3.2.0) but it is not going to be installed
         Depends: libgtk-3-0 (>= 3.1.6) but it is not going to be installed
         Depends: libindicator3-7 but it is not going to be installed
         Depends: libnux-2.0-0 but it is not going to be installed
         Depends: libunity-core-5.0-5 (= 5.6.0-0ubuntu1) but it is not going to be installed
         Depends: libunity-misc4 (>= 4.0.4) but it is not going to be installed
         Depends: libxfixes3 (>= 1:5.0-4ubuntu1) but it is not going to be installed
         Depends: compiz but it is not going to be installed
         Depends: libnux-abiversion-20120309.01
         Depends: compiz-plugins-main-default but it is not going to be installed
         Depends: nux-tools but it is not going to be installed
         Depends: unity-asset-pool (>= 0.8.18) but it is not going to be installed
         Recommends: indicator-appmenu but it is not going to be installed
         Recommends: indicator-application but it is not going to be installed
         Recommends: indicator-sound but it is not going to be installed
         Recommends: indicator-datetime but it is not going to be installed
         Recommends: indicator-messages but it is not going to be installed
         Recommends: indicator-printers but it is not going to be installed
         Recommends: indicator-power but it is not going to be installed
         Recommends: indicator-session but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

any thoughts to fix it or should I get back to 11.10?

---

### Post by ventrical on 2012-03-13
Try:

**sudo dpkg -i --configure -a**
and/or

sudo apt-get -f install

also

[COLOR=Blue]12.[/COLOR]Will install any packages necessary to fix  the broken package if they  are  available . If some necessary packages  are not available you can  use this to remove the broken one .     Code:

     sudo apt-get -f remove

---

### Post by grahammechanical on 2012-03-13
This is what concerns me:

> did an update yesterday (to the latest release)

Did you update an 11.10 install to 12.04? I hope it was not your only install of Ubuntu.

I am right now using a 12.04 that started out as 11.10 back in November but it is on another partition to my 11.10 Ubuntu.

What is happening is this: 11.10 is slowly being brought up to 12.04 standard. Libraries/packages are being upgraded over time. Old, obsolete to 12.04 libraries are still in place and needed to be upgraded but the newer libraries are not yet ready. So, other related/dependent libraries are held back.

Does that sound like a good explanation? It may even be correct for all I know but it is how I understand what is happening. It satisfies my inquiring mind.

I have noticed that by doing daily updates these issues get resolved in time.

So long as you are not using the Ubuntu development branch as your only Ubuntu installation.

Remember, 12.04 is not a new creation. It is built on 11.10. And 12.10 will start out as 12.04 and slowly be changed into 12.10. 

Somebody has to try out the next release before it is released otherwise issues will not be put right before it is released.

So, I say stick with it. See if you can set 12.04 up the way you want it to be. Then when 12.04 is finally released and you install it you will know how to get it working the way you like.

You will also gain knowledge that you can use to advise all those upgrading to 12.04 at the end of April.

And also think about sharing in testing the development branch of Ubuntu. You are welcome to join in. Sometime in May Ubuntu+1 will be for those trying out and testing 12.10.

Regards.

---

### Post by phlegm on 2012-03-13
Also having this issue. Running a fresh install of 12.04 from a few days ago.
Today this happens
apt-get update
apt-get dist-upgrade

It proceeds to uninstall ubuntu-desktop and unity

Can't install unity now.
apt-get install unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 unity : Depends: libbamf3-0 (>= 0.2.108) but it is not going to be installed
         Depends: libgnome-desktop-3-2 (>= 3.2.0) but it is not going to be installed
         Depends: libgtk-3-0 (>= 3.1.6) but it is not going to be installed
         Depends: libindicator3-7 but it is not going to be installed
         Depends: libunity-core-5.0-5 (= 5.6.0-0ubuntu1) but it is not going to be installed
         Depends: libunity-misc4 (>= 4.0.4) but it is not going to be installed
         Depends: libxfixes3 (>= 1:5.0-4ubuntu1) but it is not going to be installed
         Depends: compiz but it is not going to be installed
         Depends: compiz-plugins-main-default but it is not going to be installed
         Depends: nux-tools but it is not going to be installed
         Depends: unity-asset-pool (>= 0.8.18) but it is not going to be installed
         Recommends: indicator-appmenu but it is not going to be installed
         Recommends: indicator-application but it is not going to be installed
         Recommends: indicator-sound but it is not going to be installed
         Recommends: indicator-datetime but it is not going to be installed
         Recommends: indicator-messages but it is not going to be installed
         Recommends: indicator-printers but it is not going to be installed
         Recommends: indicator-power but it is not going to be installed
         Recommends: indicator-session but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by castrojo on 2012-03-13
You're not supposed to dist-upgrade when it tells you that, just a normal apt-get upgrade. See the sticky about partial upgrades.

---

### Post by phlegm on 2012-03-13
What's the problem with dist-upgrade?
I've been doing them for years and years without issue.
Hrmmm this explains why the package was removed. Now how to get it back installed.

dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages.

---

### Post by phlegm on 2012-03-13
Problem resolved itself as I was typing the last message. 

apt-get update
then
apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libical0 libunity-core-5.0-5 unity-common unity-services
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 608 kB of archives.

Now Unity installed again fine. I guess the devs were just rolling out new packages and didn't have all the required ones out yet.

Original poster. Please try updating again.

---

### Post by screaminj3sus on 2012-03-13
Its common during the beta testing stage for updates not to be released synchronously, so if you run a dist upgrade it might start removing important stuff, because not every needed update it in the repos yet.

If I were to run dist upgrade right now on my 12.04 install the same thing would happen:

```
The following packages will be REMOVED:
  libgstfarsight0.10-0 libtelepathy-farsight0 python-farsight python-papyon
  telepathy-butterfly ubuntu-desktop unity
The following NEW packages will be installed:
  cryptsetup-bin libcryptsetup4 libfarstream-0.1-0 libidl-common
  libtelepathy-farstream1
The following packages will be upgraded:
  empathy empathy-common libidl0 libpurple0 libxfixes3 nautilus-sendto-empathy
  udisks
7 upgraded, 5 newly installed, 7 to remove and 0 not upgraded.
Need to get 4,867 kB of archives.
After this operation, 5,842 kB disk space will be freed.
Do you want to continue [Y/n]? 

```

Sometimes a dist-upgrade/partial upgrade is necessary during the testing (for example is a package was removed/replaced in the repos) but you should always check the terminal output so you can see what packages it wants to remove.

---

### Post by castrojo on 2012-03-13
On a development release things are uploaded all the time and sometimes your mirror is out of sync or not all packages are built yet, so since some of the packages were built but not unity, it decided that you're not supposed to have it. 

The man page is correct assuming the archive isn't changing all the time, but in +1 it's always changing, so in most cases a normal upgrade will do, and if things are held back you just wait until the packages are built and/or your mirror catches up.

---

### Post by zika on 2012-03-13
> **phlegm said:**
> What's the problem with dist-upgrade?
I've been doing them for years and years without issue.
Hrmmm this explains why the package was removed. Now how to get it back installed.

dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. So, dist-upgrade
           command may remove some packages.Dist-upgrade has only one problem: it needs some TLC...

---

### Post by anti_microsoft on 2012-03-13
I had the same prob;lem yesterday. I changed repositories to one closer and it didn't work. Here is what I replied to help someone else:

I had the same problem, didn't work.

What I had to do was CTRL+ALT+F2. Sudo su and cd /etc/apt. The problem was I upgraded my sources to a mirror closer to me. So it was not using official Ubuntu mirrors.

There should be a sources.list.save file there with the original sources setup you started with. 

```
mv sources.list sources.list.2
mv sources.list.save sources.list
```

Then do apt-get clean, apt-get update, apt-get install ubuntu-desktop unity and it should work.

Hope this helps.

---

### Post by jbicha on 2012-03-13
By the way, you can save yourself a decent amount of the dist-upgrade problem if you just run the 32-bit version of Ubuntu. The fancy term is "archive skew" where the 32-bit build completes before or after the 64-bit one.

It won't completely fix the problem as some times two or more separate source packages need to upgraded together.

---

### Post by AzharHafiz.com on 2012-03-13
I've successfully install unity back from synaptic

will changing the updates to LTS instead of new release version help?

It's the only OS on my laptop and loving it

---

### Post by wojox on 2012-03-13
If you dist-upgrade you pull in partial upgrade.
```
[COLOR="Red"]wojox@wojox-desktop:~$ sudo apt-get upgrade[/COLOR]
[sudo] password for wojox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  empathy empathy-common gir1.2-rb-3.0 libidl0 libpurple0 librhythmbox-core5 light-themes nautilus-sendto-empathy rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone ubuntu-desktop
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.


[COLOR="Red"]wojox@wojox-desktop:~$ sudo apt-get dist-upgrade[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libgstfarsight0.10-0 libtelepathy-farsight0 python-farsight python-papyon telepathy-butterfly
The following NEW packages will be installed:
  gtk2-engines-pixbuf libfarstream-0.1-0 libidl-common libqt4-sql-sqlite libtelepathy-farstream1 rhythmbox-mozilla rhythmbox-plugin-zeitgeist
The following packages will be upgraded:
  empathy empathy-common gir1.2-rb-3.0 libidl0 libpurple0 librhythmbox-core5 light-themes nautilus-sendto-empathy rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins rhythmbox-ubuntuone ubuntu-desktop
13 upgraded, 7 newly installed, 5 to remove and 0 not upgraded.
Need to get 5,974 kB of archives.
After this operation, 223 kB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

### Post by alphacrucis2 on 2012-03-13
I guess people don't read the stickies.

---

### Post by AzharHafiz.com on 2012-03-14
i guess let it set to new releases is better till official release

---

### Post by ptn107 on 2012-03-14
FYI the dist-upgrade leaves unity-2d intact.  You can just switch over to it until the repos are synced and then you can do another update/upgrade.

---

### Post by AzharHafiz.com on 2012-03-14
> **ptn107 said:**
> FYI the dist-upgrade leaves unity-2d intact.  You can just switch over to it until the repos are synced and then you can do another update/upgrade.

can't find the way to edit it to solved

---

### Post by cariboo on 2012-03-14
@AzharHafiz.com, go to thread tools at the top of the page, and select Mark this thread as solved.

---

