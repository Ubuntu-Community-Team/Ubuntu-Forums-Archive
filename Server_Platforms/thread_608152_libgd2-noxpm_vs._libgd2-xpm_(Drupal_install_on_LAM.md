---
title: "libgd2-noxpm vs. libgd2-xpm (Drupal install on LAMP)"
date: 2007-11-09
forum: Server Platforms
---

### Post by mahalie on 2007-11-09
I'm fairly new to LAMP administration and linux in general. I have a LAMP already up and running on which I've installed MediaWiki, Plone and Wordpress for testing. I wanted to install Drupal too and was following the instructions in the [Community Ubuntu Documentation]("https://help.ubuntu.com/community/Drupal").

Even though I already have the LAMP running I ran apt-get (after update and upgrade) and based on php5-gd installed two packages that created dependency problems. I googled these packages but could not figure out what they are. Have I screwed something up? Should I remove those just installed and reinstall libgd2-noxpm? Here's what I did:

```

sudo apt-get install php5-gd
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libgd2-xpm
Suggested packages:
  libgd-tools
The following packages will be REMOVED:
  libgd2-noxpm
The following NEW packages will be installed:
  libgd2-xpm php5-gd
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
Need to get 227kB of archives.
After unpacking 156kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com dapper-updates/main libgd2-xpm 2.0.33-2ubuntu5.2 [194kB]
Get:2 http://us.archive.ubuntu.com dapper-updates/main php5-gd 5.1.2-1ubuntu3.9 [32.8kB]
Fetched 227kB in 6s (35.3kB/s)
Preconfiguring packages ...
dpkg: libgd2-noxpm: dependency problems, but removing anyway as you request:
 python2.4-gd depends on libgd2-noxpm (>= 2.0.33) | libgd2-xpm (>= 2.0.33); however:
  Package libgd2-noxpm is to be removed.
  Package libgd2-xpm is not installed.
(Reading database ... 101089 files and directories currently installed.)
Removing libgd2-noxpm ...
Selecting previously deselected package libgd2-xpm.
(Reading database ... 101081 files and directories currently installed.)
Unpacking libgd2-xpm (from .../libgd2-xpm_2.0.33-2ubuntu5.2_i386.deb) ...
Selecting previously deselected package php5-gd.
Unpacking php5-gd (from .../php5-gd_5.1.2-1ubuntu3.9_i386.deb) ...
Setting up libgd2-xpm (2.0.33-2ubuntu5.2) ...
Setting up php5-gd (5.1.2-1ubuntu3.9) ...

```

---

