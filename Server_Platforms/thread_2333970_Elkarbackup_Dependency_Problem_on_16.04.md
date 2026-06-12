---
title: "Elkarbackup Dependency Problem on 16.04"
date: 2016-08-15
forum: Server Platforms
---

### Post by Kirk Schnable on 2016-08-15
Hi All,

I am trying to install Elkarbackup, following their official instructions found here:  [https://github.com/elkarbackup/elkarbackup/wiki/Installation#ubuntu-1604-lts](https://github.com/elkarbackup/elkarbackup/wiki/Installation#ubuntu-1604-lts)

Unfortunately it has a few problematic dependencies: php5, php5-cli, php5-mysql.  These packages aren't available in Ubuntu 16.04.  (Not sure why their installation instructions specifically say this version is fine...)

I tried a third party repository for installing PHP 5.6, but the packages there were named differently, like php5.6-cli, so they didn't satisfy the dependency for the package.

```
# apt-get install elkarbackup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 elkarbackup : Depends: php5 but it is not installable
               Depends: php5-cli but it is not installable
               Depends: php5-mysql but it is not installable
               Depends: libssh2-php but it is not installable
E: Unable to correct problems, you have held broken packages.
```


Is there any way I can work around this besides using an older version of Ubuntu?  Seems to me if I install php5.6 manually from a third party repository, I should be able to "ignore" this dependency and the software should still work.

---

### Post by Graham_Willis on 2016-08-17
[quote="Kirk Schnable"]Is there any way I can work around this besides using an older version of Ubuntu?[/quote]

You aren't using an older version of Ubuntu, you're using an older version of PHP.
Installing software from third-party repositories is a very good way to render your system unusable (especially when you're mixing it with another version of the same software). However, it doesn't have to be the case. In order to prevent a potential disaster just install this software to dedicated folders, so it'd throw all the files, including these which normally goes into /etc, /lib and similar directories, to a subdirectory of a directory dedicated for your application. I don't know if it's possible to do it using packages, but it's certainly possible compiling from source code. It might require a little effort, but it's worth it (in this case), you just have to look for options like **prefix** and **php-library-dir**, set all of that properly, then compile and install (but double check that doing **configure **you indeed set everything so it wouldn't trash your system).

Welcome old good days of compiling software by hand.

---

