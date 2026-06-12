---
title: "Low Tech Dapper Setup Script"
date: 2006-06-13
forum: The Cafe
---

### Post by benbruscella on 2006-06-13
OK, so this is just a place to document my Dapper setup and experiences, so there is no need to read any further!

**Step 1:**
**Enable all Repositories**

*Background:*
The default installation for Ubuntu ships with limited enabled repositories.  this is OK for most things, but most things people want to install needs more repositories enabled. 

*Details:*
Edit sources.list to get apt to see them.  More details can be found here:
[http://ubuntuguide.org/wiki/Dapper#Repositories]("http://ubuntuguide.org/wiki/Dapper#Repositories")

Or, make up your own sources.list here:
[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

Here is my /etc/apt/sources.list in full:

```
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb http://au.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://au.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://au.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```

**Step 1b:**
**Update and Upgrade**

*Background:*
Since the sources.list has changed, we need to update everything:

*Details:*
```
sudo apt-get update
sudo apt-get upgrade dist-upgrade
```

By the way, I have a FAT32 drice for data backup, so here is the line I added to /etc/fstab to make this mount under Ubuntu:

```
/dev/hdb1 /media/data vfat iocharset=utf8,umask=000 0 0
```

Installed AMAROK 1.4 using this:
[http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php)
```

sudo apt-get install amarok amarok-engines

```

**Step 2:**
**Restricted Formats**

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

*Details:*
MP3 support with preview:
```

sudo apt-get install gstreamer0.10-plugins-ugly mpg321 vorbis-tools
sudo apt-get install libxine-extracodecs
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-ugly
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll

```

w32 codecs:
```

wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
sudo dpkg -i w32codecs_20060611-0.0_i386.deb

```

Alternative Players:
```

sudo apt-get install totem-xine gxine

```

Playing Streaming Video from the Internet:
```

sudo apt-get install totem-xine-firefox-plugin

```

DVD playback:
```

sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

```

AAC decoding:
```

gstreamer0.10-plugins-bad-multiverse

```

Flash and JAVA:
```

sudo apt-get install flashplugin-nonfree
sudo update-flashplugin
sudo apt-get install gsfonts gsfonts-x11
sudo apt-get install sun-java5-bin sun-java5-plugin

```

Acrobat et al:
```

sudo apt-get install acroread
sudo apt-get install mozilla-acroread
sudo apt-get install acroread-plugins

```


**Step 3:**
**Applications**

```

sudo apt-get install d4x gftp cowbell easytag audacity k3b  build-essential eclipse
sudo apt-get install rar
sudo ln -fs /usr/bin/rar /usr/bin/unrar

```

---

