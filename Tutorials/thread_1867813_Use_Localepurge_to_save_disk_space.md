---
title: "Use Localepurge to save disk space"
date: 2011-10-23
forum: Tutorials
---

### Post by JRV on 2011-10-23
Localepurge is a utility that removes unneeded language files.  This can save a lot of disk space if you have a small drive on an older system. 

Install localepurge with the command:
```

sudo apt-get install localepurge

```

Or you can install it through Software Center.

During the installation process a window opens ask you to check the languages you want to keep.  Make sure you check everything you will need.

Example:

The only language I need is US English.
I check en and everything that starts with en_US.

The languages that are checked are stored in a file called /etc/locale.nopurge.

This is my /etc/locale.nopurge file, all the options are set to the defaults:
```

####################################################
# This is the configuration file for localepurge(8).
####################################################

####################################################
# Uncommenting this string enables removal of localized 
# man pages based on the configuration information for
# locale files defined below:

MANDELETE

####################################################
# Uncommenting this string causes localepurge to simply delete
# locales which have newly appeared on the system without
# bothering you about it:

DONTBOTHERNEWLOCALE

####################################################
# Uncommenting this string enables display of freed disk
# space if localepurge has purged any superfluous data:

SHOWFREEDSPACE

#####################################################
# Commenting out this string enables faster but less
# accurate calculation of freed disk space:

#QUICKNDIRTYCALC

#####################################################
# Commenting out this string disables verbose output:

#VERBOSE

#####################################################
# Following locales won't be deleted from this system
# after package installations done with apt-get(8):

en
en_US
en_US.ISO-8859-15
en_US.UTF-8

```

Run localepurge with the command:
```

sudo localepurge

```

This is the output from running localepurge on a fresh install of Ubuntu Oneiric 11.10:
```

localepurge: Disk space freed in /usr/share/locale: 20624 KiB
localepurge: Disk space freed in /usr/share/man: 4004 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 33076 KiB
localepurge: Disk space freed in /usr/share/omf: 644 KiB

Total disk space freed by localepurge: 58348 KiB

```


Once localepurge is installed it will run automatically every time you install a package or do an update.

The one drawback to localpurge is that it is slow, and sometimes after an install or update it will run multiple times.

I have tested it and found no problems on every version of Ubuntu going back to 9.04. (Jaunty)

---

