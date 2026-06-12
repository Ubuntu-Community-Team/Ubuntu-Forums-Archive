---
title: "Installing Java 1.5.0-10..I only see 1.5.0-06-1"
date: 2007-01-13
forum: Repositories &amp; Backports
---

### Post by Jonathan987 on 2007-01-13
Hey guys, I'm not very good with linux so bare with me.....I'm trying to update sun's java (JRE) 1.5.0-06-1 to 1.5.0-10

I don't see an update available in add/remove programs or the advanced view -- synaptic.

I'm using dapper LTS...


thanks!


Jonathan

---

### Post by Jonathan987 on 2007-01-16
does anyone have some info that could help me!??!

Thanks! :)

---

### Post by mlind on 2007-01-23
You can check out the version from [http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=sourcenames&version=all&exact=1&keywords=sun-java5](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=sourcenames&version=all&exact=1&keywords=sun-java5)
or by typing
```

apt-cache madison sun-java5-jre

```

for Ubuntu Dapper (6.06 LTS) there's only **1.5.0-06-1** version available. You can request a update on Ubuntu's [Malone bugtracer]("https://bugs.launchpad.net/ubuntu/+source/sun-java5/+bugs"). 
Updates for stable releases like Dapper, are released seldom and usually only if there's security related issue or major bugs fixed.

I can help you to build the package from Feisty's (current Ubuntu development version) source for yourself though if you wish.

---

### Post by blair nilsson on 2007-01-23
At the very least I'd be interested, any chance of posting a guide to the forum?

---

### Post by mlind on 2007-01-24
Here's a short HOWTO **without** using pbuilder/sbuild. Preferred way is to use pbuilder/sbuild  or other similar tool though, but you'll find instructions for these by searching the forums or Ubuntu wiki.


[LIST]
[*]add Feisty **multiverse** source repository in **/etc/apt/sources.list**
```

deb-src http://archive.ubuntu.com/ubuntu feisty **multiverse**

```
[*]create temporary working directory and get the source
```

mkdir /tmp/sun-java5
cd /tmp/sun-java5
sudo aptitude update
apt-get source sun-java5
cd sun-java5-1.5.0-10

```
[*]install build-dependencies (listed in debian/control). Some of the packages are not required for all architectures, so don't worry if you get warnings.
```

sudo aptitude install debhelper po-debconf defoma unzip bzip2 patch libasound2 unixodbc libx11-6 libxext6 libxi6 libxp6 libxt6 libxtst6 lib32asound2 ia32-libs

```
[*]build
```

sudo aptitude install fakeroot dpkg-dev
dpkg-buildpackage -rfakeroot -us -uc

```
[/LIST]

If you use this method, keep track of the installed build depends and then remove those after the binary is built.

---

### Post by Jonathan987 on 2007-01-27
Hey, thanks for your little tutorial.....

when I type in the second of the two build commands I get the following error:

dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is


what does this mean?

also what do you mean by: "keep track of the installed build depends and then remove those after the binary is built."

Sorry I know these questions are very novice....

thanks!

Jonathan

---

### Post by mlind on 2007-01-27
> **Jonathan987 said:**
> Hey, thanks for your little tutorial.....

when I type in the second of the two build commands I get the following error:

dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is


You have to be in the source directory tree when you type the dpkg-buildpackage command. Did you remember to **cd sun-java5-1.5.0-10** ?


> **Jonathan987 said:**
> 
also what do you mean by: "keep track of the installed build depends and then remove those after the binary is built."

Sorry I know these questions are very novice....

thanks!

Jonathan

It's not essential, but you probably don't want all the build dependencies (packages you installed using aptitude) laying around after you've done with building the package. I usually use sbuild/pbuilder for building all Ubuntu/Debian packages, these take care of dependecy resolution (automatically installs all build dependencies) and do their job in a temporary chroot (packages are installed in a sandbox and sandbox is removed afterwards).

---

