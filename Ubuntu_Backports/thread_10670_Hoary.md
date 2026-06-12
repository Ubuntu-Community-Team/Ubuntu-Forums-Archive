---
title: "Hoary"
date: 2005-01-10
forum: Ubuntu Backports
---

### Post by techn9ne on 2005-01-10
When hoary comes out and there is mixed warty and warty-backport will people still be able to smoothly upgrade to hoary?

---

### Post by jdong on 2005-01-10
I intend on making a simple upgrade script for that purpose. All my package versions either contain "backportedfrom" (old versions) or "4.10ubp" (new versions). Simply use Grep to detect these in version strings of packages, then apt-get install PACKAGE/hoary.

---

### Post by HiddenWolf on 2005-01-16
[QUOTE=jdong]I intend on making a simple upgrade script for that purpose. All my package versions either contain "backportedfrom" (old versions) or "4.10ubp" (new versions). Simply use Grep to detect these in version strings of packages, then apt-get install PACKAGE/hoary.[/QUOTE]
Wouldn't be hard to do even manually.
The problem is, do you force the backports to hoary versionsand then dist-upgrade
or
do you force backports back to warty versions then dist-upgrade

could be a bit of breakage either way.

---

### Post by jdong on 2005-01-16
That's a good question. An interesting one to answer.

---

### Post by joede on 2005-01-17
[QUOTE=HiddenWolf]
The problem is, do you force the backports to hoary versions and then dist-upgrade
or do you force backports back to warty versions then dist-upgrade could be a bit of breakage either way.[/QUOTE]

There is a special way other backport repositories (for Debian Woody) are going.

All backports must use the decremented package release with a unique add on. So a backport of a package foobar_1.0-4_i386.deb from hoary to warthy should be named foobar_1.0-3.ubp_i386.deb! This way, the packages in hoary are always newer than these in the backport repository.

---

### Post by joede on 2005-01-17
Talking about backport repositories, I want to ask for another "feature". With the current structure of the repository, everyone is forced to update all packages available in the repository. Other backport repositories like [www.backports.org](www.backports.org) doesn't use a "monolithic structure".

If every application or groups off applications uses it's own repository, everybody could select the stuff he wants to add. To met the dependencies, you simple have to add the these packages as symlinks. 

To add the package foobar, the source.lists should have the following line.

deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) warty-backports foobar

To add all the packages available, add main / universe instead of the package name.

For an example, just have a look at [http://www.backports.org/debian/](http://www.backports.org/debian/)

---

### Post by HiddenWolf on 2005-01-17
[QUOTE=joede]Talking about backport repositories, I want to ask for another "feature". With the current structure of the repository, everyone is forced to update all packages available in the repository. Other backport repositories like [www.backports.org](www.backports.org) doesn't use a "monolithic structure".

If every application or groups off applications uses it's own repository, everybody could select the stuff he wants to add. To met the dependencies, you simple have to add the these packages as symlinks. 

To add the package foobar, the source.lists should have the following line.

deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) warty-backports foobar

To add all the packages available, add main / universe instead of the package name.

For an example, just have a look at [http://www.backports.org/debian/](http://www.backports.org/debian/)[/QUOTE]
It is possible to 'pin' packages in synaptic, so they won't be upgraded. For now, that should do.

---

### Post by nocturn on 2005-01-17
[QUOTE=joede]Talking about backport repositories, I want to ask for another "feature". With the current structure of the repository, everyone is forced to update all packages available in the repository. Other backport repositories like [www.backports.org](www.backports.org) doesn't use a "monolithic structure".

If every application or groups off applications uses it's own repository, everybody could select the stuff he wants to add. To met the dependencies, you simple have to add the these packages as symlinks. 

To add the package foobar, the source.lists should have the following line.

deb [http://ubuntu-bp.sourceforge.net/ubuntu](http://ubuntu-bp.sourceforge.net/ubuntu) warty-backports foobar

To add all the packages available, add main / universe instead of the package name.

For an example, just have a look at [http://www.backports.org/debian/](http://www.backports.org/debian/)[/QUOTE]

I used this way:

- Add backports to sources
- aptitude update
- aptidude the packages I wanted (FireFox)
- Comment out backports
- aptitude update

That did it.

---

### Post by jdong on 2005-01-17
I think I'll start work on a backports rollback/rollforward script now.

---

### Post by jdong on 2005-01-17
[QUOTE=joede]There is a special way other backport repositories (for Debian Woody) are going.

All backports must use the decremented package release with a unique add on. So a backport of a package foobar_1.0-4_i386.deb from hoary to warthy should be named foobar_1.0-3.ubp_i386.deb! This way, the packages in hoary are always newer than these in the backport repository.[/QUOTE]

That's deceptive, though... You're alluding to a completely different package in the other release!

---

### Post by jdong on 2005-01-17
```

apt-show-versions -b | grep warty-backports | cut -d ' ' -f 1 | awk -F/ '{print $1;}'

```

Shows all installed backports (includes staging). Working on piping that to xargs.

---

### Post by jdong on 2005-01-17
```

apt-show-versions -b | grep warty-backports | cut -d ' ' -f 1 | awk -F/ '{print $1;}' | xargs --replace="{}" echo {}/warty

```

Looks like this will work fine.

Requires apt-show-versions to be installed (from Universe).

---

### Post by jdong on 2005-01-17
```
apt-show-versions -b | grep warty-backports | cut -d ' ' -f 1 | awk -F/ '{print $1;}' |grep -v grepmap | xargs --replace="{}" echo {}/warty | xargs sudo apt-get install -s

```

This version takes into account that grepmap doesn't exist in Warty.

---

### Post by HiddenWolf on 2005-01-17
[QUOTE=jdong]```
apt-show-versions -b | grep warty-backports | cut -d ' ' -f 1 | awk -F/ '{print $1;}' |grep -v grepmap | xargs --replace="{}" echo {}/warty | xargs sudo apt-get install -s

```

This version takes into account that grepmap doesn't exist in Warty.[/QUOTE]
Hm. Walk me through and I'll test it for you. :-)

---

### Post by jdong on 2005-01-17
1. apt-get install apt-show-versions

2. Edit sources.list, remove backports. apt-get update.

3. Run the command I gave you. Make sure it doesn't bomb out. Make sure it doesn't remove important stuff.

4. Run the command, taking off the '-s'. This WILL perform the changes that were simulated in #3.

5. do an apt-get dist-upgrade to get any possible security updates that were rolled back.

6. You are now using official Warty. All traces of backports are uninstalled.

---

### Post by HiddenWolf on 2005-01-17
[QUOTE=jdong]1. apt-get install apt-show-versions

2. Edit sources.list, remove backports. apt-get update.

3. Run the command I gave you. Make sure it doesn't bomb out. Make sure it doesn't remove important stuff.

4. Run the command, taking off the '-s'. This WILL perform the changes that were simulated in #3.

5. do an apt-get dist-upgrade to get any possible security updates that were rolled back.

6. You are now using official Warty. All traces of backports are uninstalled.[/QUOTE]

root@system:~ # apt-show-versions -b | grep warty-backports | cut -d ' ' -f 1 | awk -F/ '{print $1;}' |grep -v grepmap | xargs --replace="{}" echo {}/warty | xargs sudo apt-get install -s
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by HiddenWolf on 2005-01-17
root@system:/home/hidde # apt-show-versions -b | grep warty-backports | cut -d ' ' -f 1 | awk -F/ '{print $1;}' |grep -v grepmap | xargs --replace="{}" echo {}/warty | xargs sudo apt-get install -y
Reading Package Lists... Done
Building Dependency Tree... Done
Selected version 2.0.2-3ubuntu5 (Ubuntu:warty) for libgimp2.0
Selected version 0.8-2ubuntu2 (Ubuntu:warty) for mozilla-thunderbird
Selected version 0.8.5-1ubuntu2 (Ubuntu:warty) for rhythmbox
Selected version 2.0.2-3ubuntu5 (Ubuntu:warty) for gimp-python
Selected version 2.0.8-2ubuntu1 (Ubuntu:warty) for xchat-common
Selected version 1:1.0.0-1ubuntu1 (Ubuntu:warty) for gaim
Selected version 2.0.8-2ubuntu1 (Ubuntu:warty) for xchat
Selected version 4.2.11ubuntu2 (Ubuntu:warty) for debhelper
Selected version 2.0.2-3ubuntu5 (Ubuntu:warty) for gimp
Selected version 0.99+1.0PR.1+revertedto0.9.3-0ubuntu3 (Ubuntu:warty) for mozilla-firefox
Selected version 0.53.4-1ubuntu4 (Ubuntu:warty) for synaptic
Selected version 3:2.4.0-3ubuntu1 (Ubuntu:warty) for gthumb
Selected version 2.0.2-3ubuntu5 (Ubuntu:warty) for gimp-data
Selected version 0.5.3-1 (Ubuntu:warty) for reiser4progs
Selected version 0.0.20040329-11ubuntu10 (Ubuntu:warty) for hotplug
Suggested packages:
  dh-make libzephyr3 gimp-help-en gimp-help libgimp-perl gimp-data-extras latex-xft-fonts mozilla-thunderbird-offline mozilla-thunderbird-typeaheadfind mozilla-thunderbird-inspector
  mozilla-thunderbird-enigmail kernel-patch-2.6-reiser4 libgnome2-perl apt-watch libnet-google-perl
Recommended packages:
  gimp-svg mozilla-firefox-gnome-support xprt-xprintorg
The following packages will be DOWNGRADED:
  debhelper gaim gimp gimp-data gimp-python gthumb hotplug libgimp2.0 mozilla-firefox mozilla-thunderbird reiser4progs rhythmbox synaptic xchat xchat-common
0 upgraded, 0 newly installed, 15 downgraded, 0 to remove and 0 not upgraded.
Need to get 29.7MB/41.1MB of archives.
After unpacking 5379kB of additional disk space will be used.
E: There are problems and -y was used without --force-yes

Now, this puzzles me. The old versions are 5mb bigger than the old ones?
Why the hell is 3/4th of what needs to be downed already on my hdd? Is there some temp folder caching all this?

---

### Post by jdong on 2005-01-17
add --force-yes as it instructs....

---

### Post by HiddenWolf on 2005-01-17
[QUOTE=jdong]add --force-yes as it instructs....[/QUOTE]
 Preparing to replace xchat-common 2.4.1-0.1ubuntu1-warty+backportedfrom-ubuntu-hoary1 (using .../xchat-common_2.0.8-2ubuntu1_all.deb) ...
Unpacking replacement xchat-common ...
Errors were encountered while processing:
 /var/cache/apt/archives/gimp_2.0.2-3ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by jdong on 2005-01-17
What was the error that GIMP gave?

---

### Post by HiddenWolf on 2005-01-17
[QUOTE=jdong]What was the error that GIMP gave?[/QUOTE]
Errors were encountered while processing:
 gimp
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@system:~ # apt-get install gimp
Reading Package Lists... Done
Building Dependency Tree... Done
The following extra packages will be installed:
  gimp-data libgimp2.0
Suggested packages:
  gimp-help-en gimp-help libgimp-perl gimp-data-extras
Recommended packages:
  gimp-svg
The following packages will be upgraded:
  gimp gimp-data libgimp2.0
3 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0B/10.1MB of archives.
After unpacking 3534kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
root@system:~ #

---

### Post by joede on 2005-01-18
[QUOTE=HiddenWolf]It is possible to 'pin' packages in synaptic, so they won't be upgraded. For now, that should do.[/QUOTE]

That's right, but as far as I know, with pinning, you have to pin all unwanted packages. Am I right?

---

### Post by joede on 2005-01-18
[QUOTE=nocturn]I used this way:
- Add backports to sources
- aptitude update
- aptidude the packages I wanted (FireFox)
- Comment out backports
- aptitude update
That did it.[/QUOTE]

That one possible way. But going this way, you have to add and remove the "backport line" every time you want to update / install something.

---

### Post by joede on 2005-01-18
[QUOTE=jdong]That's deceptive, though... You're alluding to a completely different package in the other release![/QUOTE]

That's not my though. It's the more or less official way. It is used by many debian developers, who makes backports (mainly to Debian Woody) available. I know at least 3 repositories doing it this way.

Why do you think it's problem? Only the debian package release is decremented. Due to the postfix added to the package release, this release should become "higher" than the release without a postfix.

So the package release "3.ubp" is less than the current "4" but more than previous "3". That's what I've been told.

---

