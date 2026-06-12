---
title: "apt-get 404 error"
date: 2011-11-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by CaptainMark on 2011-11-22
I get this error from apt-get update```
Err http://ppa.launchpad.net precise/main amd64 Packages 
404 Not Found
```Is this normal, the setup is upgraded from 11.10 so if its a repo that doesnt exist or apply any more i wont worry

---

### Post by benjabean1 on 2011-11-22
I believe this needs to be:
```
deb http://ppa.launchpad.net precise main
```

---

### Post by paul_in_london on 2011-11-22
> **CaptainMark said:**
> I get this error from apt-get update```
Err http://ppa.launchpad.net precise/main amd64 Packages 
404 Not Found
```Is this normal, the setup is upgraded from 11.10 so if its a repo that doesnt exist or apply any more i wont worry

ppa.launchpad.net is the "top-level" ppa directory. If you go to that URL you'll see a list of ppa sub-directories.

Your ppa sources list entries should be of the form (taking the precise branch of the ricotz testing ppa as an example):

```
ppa.launchpad.net/ricotz/testing/ubuntu precise main
```

EDIT: NB - some of your ppas may not have precise branches yet.

---

### Post by CaptainMark on 2011-11-22
this isnt one ive added though i installed a vanilla 11.10 and used sed to change all entries of oneiric to precise in /etc/apt/sources.list
thats why i was confused

EDIT: i have a chromium ppa that is added by my post_install script, thats failing but i expect it to for now,

---

### Post by paul_in_london on 2011-11-22
> **CaptainMark said:**
> this isnt one ive added though i installed a vanilla 11.10 and used sed to change all entries of oneiric to precise in /etc/apt/sources.list
thats why i was confused

EDIT: i have a chromium ppa that is added by my post_install script, thats failing but i expect it to for now,

I think maybe your sed command went a bit wrong.

This is my /etc/apt/sources.list:

```
deb http://archive.ubuntu.com/ubuntu precise main restricted

deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb http://archive.ubuntu.com/ubuntu precise-security main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu precise restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
**[COLOR="Red"]deb http://extras.ubuntu.com/ubuntu oneiric main[/COLOR]**
[B][COLOR="Red"]deb-src http://extras.ubuntu.com/ubuntu oneiric main
[/COLOR][/B]deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe
deb http://ppa.launchpad.net/vincent-c/nevernote/ubuntu oneiric main
deb-src http://ppa.launchpad.net/vincent-c/nevernote/ubuntu oneiric main
```

Note the highlighted lines - extras.ubuntu.com/ubuntu/dists/precise/ doesn't exist yet so you have to be careful with global substitutions.

EDIT: did you add the chromium ppa manually? In my case:

```
cat /etc/apt/sources.list.d/chromium-daily-ppa-oneiric.list
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu oneiric main
```

(no precise branch for that ppa yet).

---

### Post by paul_in_london on 2011-11-22
Funnily enough a chromium update just came through for me:

```
paul@precise-64:~$ sudo aptitude safe-upgrade
Resolving dependencies...                
The following packages will be upgraded:
  chromium-browser chromium-codecs-ffmpeg 
The following packages are RECOMMENDED but will NOT be installed:
  chromium-browser-l10n 
2 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 20.0 MB of archives. After unpacking 41.0 kB will be freed.
Do you want to continue? [Y/n/?] Y
Get: 1 http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ oneiric/main chromium-codecs-ffmpeg amd64 17.0.947.0~svn20111122r111102-0ubuntu1~ucd1 [392 kB]
Get: 2 http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/ oneiric/main chromium-browser amd64 17.0.947.0~svn20111122r111102-0ubuntu1~ucd1 [19.7 MB]
Fetched 20.0 MB in 13s (1,488 kB/s)                                                                                                                                                                                                           
(Reading database ... 212447 files and directories currently installed.)
Preparing to replace chromium-codecs-ffmpeg 17.0.946.0~svn20111121r110888-0ubuntu1~ucd1 (using .../chromium-codecs-ffmpeg_17.0.947.0~svn20111122r111102-0ubuntu1~ucd1_amd64.deb) ...
Unpacking replacement chromium-codecs-ffmpeg ...
Preparing to replace chromium-browser 17.0.946.0~svn20111121r110888-0ubuntu1~ucd1 (using .../chromium-browser_17.0.947.0~svn20111122r111102-0ubuntu1~ucd1_amd64.deb) ...
Unpacking replacement chromium-browser ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Setting up chromium-codecs-ffmpeg (17.0.947.0~svn20111122r111102-0ubuntu1~ucd1) ...
Setting up chromium-browser (17.0.947.0~svn20111122r111102-0ubuntu1~ucd1) ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

                                         
Current status: 1 update [-2].
paul@precise-64:~$
``` :lolflag:

---

### Post by CaptainMark on 2011-11-24
yes i added the chromium ppa manually in oneiric and updated it with a sed command i took from this forum section? uurm pass, ill just make a new sources.list

---

