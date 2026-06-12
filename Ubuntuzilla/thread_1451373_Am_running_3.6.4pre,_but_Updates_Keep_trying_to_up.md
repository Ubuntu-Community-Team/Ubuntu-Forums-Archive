---
title: "Am running 3.6.4pre, but Updates Keep trying to update 3.5"
date: 2010-04-10
forum: Ubuntuzilla
---

### Post by kendoori on 2010-04-10
I have Ubuntuzilla set up and am running 3.6.4pre as a result of this. Update manager keeps trying to push an update to 3.5.x to me, and then goes through the process (ask me to reboot browser), but I remain on 3.6.4 (as preferred).

Is there anyway to make the system start forgetting about updating 3.5?

---

### Post by nanotube on 2010-04-11
ubuntuzilla does not have 3.6.4pre, it only has releases, therefore 3.6.3 is the latest in the ubuntuzilla repositories.

you're probably getting stuff from the daily builds repo instead.

---

### Post by kendoori on 2010-04-11
Ubuntuzilla is in my sources.list, so not sure how I would be getting the daily build. Some update was pushed out yesterday that has actually made FF 3.6.4 nearly unusable. Others have reported that this has to do with the Flash plugin and that if one disables flash, the issue goes away.

My sources.list is below. I don't see any other mozilla reference beisdes ubuntuzilla. How can I get ubuntuzilla to be back in charge?

```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic main restricted
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic-updates main restricted
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic universe
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic universe
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic-updates universe
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic multiverse
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic multiverse
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic-updates multiverse
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic-security main restricted
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic-security main restricted
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic-security universe
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic-security universe
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic-security multiverse
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ karmic-security multiverse
deb http://download.virtualbox.org/virtualbox/debian karmic non-free
deb http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/shutter/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/tp-fan/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/jeffreyratcliffe/ubuntu karmic main
deb-src http://ppa.launchpad.net/jeffreyratcliffe/ubuntu karmic main
deb http://mirror.sifnt.net.au/linux karmic main
deb http://packages.medibuntu.org/ karmic free non-free
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
deb http://ppa.launchpad.net/voronov84/andreyv/ubuntu karmic main

deb http://dl.google.com/linux/deb/ stable non-free main
deb http://ppa.launchpad.net/xsisqox/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/xsisqox/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu karmic main

```

---

### Post by nanotube on 2010-04-11
Hi
no idea... maybe the daily ppa is in your /etc/apt/sources.list.d/?

what command do you use to start firefox? /usr/bin/firefox? or something else?

---

### Post by kendoori on 2010-04-11
Yes, the daily appears to be in /etc/apt/sources.list.d (see below). So even though ubuntuzilla is my sources.list, this entry is over-riding it? If I remove the sources.list.d entry, and do an update, will it revert me to the Ubuntuzilla version?

The command used to launch firefox on my system (e.g. what's in the launcher), is just: firefox

However, this appears to trigger multiple processes (see system monitor below)

[IMG]http://www.tpchealthcare.com/downloads/ff-systemmonitor.png[/IMG] 

```

docky-core-ppa-karmic.list
docky-core-ppa-karmic.list.save
google-chrome.list
google-chrome.list.save
medibuntu.list
medibuntu.list.save
mozillateam-firefox-stable-karmic.list
mozillateam-firefox-stable-karmic.list.save
opera.list
opera.list.save
pidgin-ppa.list
pidgin-ppa.list.save
spideroak.com.sources.list.save
stebalien-simple-service-manager-karmic.list
stebalien-simple-service-manager-karmic.list.save
ubuntu-mozilla-daily-ppa-karmic.list
ubuntu-mozilla-daily-ppa-karmic.list.save
ubuntu-wine-ppa-karmic.list
ubuntu-wine-ppa-karmic.list.save
wine-doors-dev-team-ppa-karmic.list
wine-doors-dev-team-ppa-karmic.list.save
xsisqox-ppa-karmic.list

```

---

### Post by nanotube on 2010-04-12
hi
you can remove the mozilla-daily.list and .list.save from that directory. then ```
sudo apt-get remove firefox-3.6
``` and then finally ```
sudo apt-get install firefox-mozilla-build
```

(don't forget to completely exit firefox before you do that)

now you should be able to start firefox as normal, with the 'firefox' command, and it should be the mozilla release of 3.6.3.

---

