---
title: "Some error while updating"
date: 2015-01-24
forum: Security
---

### Post by darko6 on 2015-01-24
I have an error, dont know how to fix it.

---

### Post by mörgæs on 2015-01-24
Try to close all other windows and run it again.

---

### Post by oldos2er on 2015-01-24
You can fix the NO_PUBKEY error with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A902DDA375E52366
```

---

### Post by darko6 on 2015-01-24
tnx guys, but i have another old error pop up again.[ATTACH=CONFIG]259468[/ATTACH]

---

### Post by Bashing-om on 2015-01-24
darko6; Hello;

> **darko6 said:**
> tnx guys, but i have another old error pop up again.[ATTACH=CONFIG]259468[/ATTACH]

Likely an unsupported application in trusty.
Post -Between code tags - :
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
so we can find/copy/paste the URL and verify that suspicion.

[INDENT][INDENT]3rd party software
[INDENT][INDENT][INDENT]not 'buntu's fault
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mörgæs on 2015-01-24
Yes, as mentioned above we prefer that you copy the output as text and post it in CODE tags. Images take up space and their contents is not searchable.

---

### Post by darko6 on 2015-01-25
```
darko@darko:~$ cat -n /etc/apt/sources.list     1	# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ trusty main restricted
     2	deb-src http://archive.ubuntu.com/ubuntu trusty main restricted #Added by software-properties
     3	
     4	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     5	# newer versions of the distribution.
     6	deb http://rs.archive.ubuntu.com/ubuntu/ trusty main restricted
     7	deb-src http://rs.archive.ubuntu.com/ubuntu/ trusty universe main restricted multiverse #Added by software-properties
     8	
     9	## Major bug fix updates produced after the final release of the
    10	## distribution.
    11	deb http://rs.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12	deb-src http://rs.archive.ubuntu.com/ubuntu/ trusty-updates universe main restricted multiverse #Added by software-properties
    13	
    14	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    15	## team. Also, please note that software in universe WILL NOT receive any
    16	## review or updates from the Ubuntu security team.
    17	deb http://rs.archive.ubuntu.com/ubuntu/ trusty universe
    18	deb http://rs.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19	
    20	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21	## team, and may not be under a free licence. Please satisfy yourself as to 
    22	## your rights to use the software. Also, please note that software in 
    23	## multiverse WILL NOT receive any review or updates from the Ubuntu
    24	## security team.
    25	deb http://rs.archive.ubuntu.com/ubuntu/ trusty multiverse
    26	deb http://rs.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    27	
    28	## N.B. software from this repository may not have been tested as
    29	## extensively as that contained in the main release, although it includes
    30	## newer versions of some applications which may provide useful features.
    31	## Also, please note that software in backports WILL NOT receive any review
    32	## or updates from the Ubuntu security team.
    33	deb http://rs.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    34	deb-src http://rs.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse #Added by software-properties
    35	
    36	deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    37	deb-src http://security.ubuntu.com/ubuntu trusty-security universe main restricted multiverse #Added by software-properties
    38	deb http://security.ubuntu.com/ubuntu trusty-security universe
    39	deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    40	
    41	## Uncomment the following two lines to add software from Canonical's
    42	## 'partner' repository.
    43	## This software is not part of Ubuntu, but is offered by Canonical and the
    44	## respective vendors as a service to Ubuntu users.
    45	deb http://archive.canonical.com/ubuntu trusty partner
    46	deb-src http://archive.canonical.com/ubuntu trusty partner
    47	
    48	## This software is not part of Ubuntu, but is offered by third-party
    49	## developers who want to ship their latest software.
    50	deb http://extras.ubuntu.com/ubuntu trusty main
    51	deb-src http://extras.ubuntu.com/ubuntu trusty main
    52	# deb http://repo.mate-desktop.org/archive/1.8/ubuntu trusty main
    53	# deb-src http://repo.mate-desktop.org/archive/1.8/ubuntu trusty main
    54	# deb-src http://repo.mate-desktop.org/archive/1.8/ubuntu trusty main
darko@darko:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/alexmurray-indicator-sensors-trusty.list <==
deb http://ppa.launchpad.net/alexmurray/indicator-sensors/ubuntu trusty main
# deb-src http://ppa.launchpad.net/alexmurray/indicator-sensors/ubuntu trusty main


==> /etc/apt/sources.list.d/alexmurray-indicator-sensors-trusty.list.save <==
deb http://ppa.launchpad.net/alexmurray/indicator-sensors/ubuntu trusty main
# deb-src http://ppa.launchpad.net/alexmurray/indicator-sensors/ubuntu trusty main


==> /etc/apt/sources.list.d/appgrid-stable-trusty.list <==
deb http://ppa.launchpad.net/appgrid/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/appgrid-stable-trusty.list.save <==
deb http://ppa.launchpad.net/appgrid/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/atareao-atareao-trusty.list <==
deb http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main


==> /etc/apt/sources.list.d/atareao-atareao-trusty.list.save <==
deb http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main


==> /etc/apt/sources.list.d/atareao-sunflower-trusty.list <==
deb http://ppa.launchpad.net/atareao/sunflower/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/sunflower/ubuntu trusty main


==> /etc/apt/sources.list.d/atareao-sunflower-trusty.list.save <==
deb http://ppa.launchpad.net/atareao/sunflower/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/sunflower/ubuntu trusty main


==> /etc/apt/sources.list.d/claudiocn-slm-trusty.list <==
# deb http://ppa.launchpad.net/claudiocn/slm/ubuntu trusty main
# deb-src http://ppa.launchpad.net/claudiocn/slm/ubuntu trusty main


==> /etc/apt/sources.list.d/claudiocn-slm-trusty.list.save <==
# deb http://ppa.launchpad.net/claudiocn/slm/ubuntu trusty main
# deb-src http://ppa.launchpad.net/claudiocn/slm/ubuntu trusty main


==> /etc/apt/sources.list.d/costales-folder-color-trusty.list <==
deb http://ppa.launchpad.net/costales/folder-color/ubuntu trusty main
# deb-src http://ppa.launchpad.net/costales/folder-color/ubuntu trusty main


==> /etc/apt/sources.list.d/costales-folder-color-trusty.list.save <==
deb http://ppa.launchpad.net/costales/folder-color/ubuntu trusty main
# deb-src http://ppa.launchpad.net/costales/folder-color/ubuntu trusty main


==> /etc/apt/sources.list.d/ehoover-compholio-trusty.list <==
deb http://ppa.launchpad.net/ehoover/compholio/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu trusty main


==> /etc/apt/sources.list.d/ehoover-compholio-trusty.list.save <==
deb http://ppa.launchpad.net/ehoover/compholio/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu trusty main


==> /etc/apt/sources.list.d/fyrmir-compiz-plugins-trusty.list <==
# deb http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu trusty main
# deb-src http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu trusty main


==> /etc/apt/sources.list.d/fyrmir-compiz-plugins-trusty.list.save <==
# deb http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu trusty main
# deb-src http://ppa.launchpad.net/fyrmir/compiz-plugins/ubuntu trusty main


==> /etc/apt/sources.list.d/fyrmir-livewallpaper-daily-trusty.list <==
deb http://ppa.launchpad.net/fyrmir/livewallpaper-daily/ubuntu trusty main
# deb-src http://ppa.launchpad.net/fyrmir/livewallpaper-daily/ubuntu trusty main


==> /etc/apt/sources.list.d/fyrmir-livewallpaper-daily-trusty.list.save <==
deb http://ppa.launchpad.net/fyrmir/livewallpaper-daily/ubuntu trusty main
# deb-src http://ppa.launchpad.net/fyrmir/livewallpaper-daily/ubuntu trusty main


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/google-earth.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/earth/deb/ stable main


==> /etc/apt/sources.list.d/google-earth.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/earth/deb/ stable main


==> /etc/apt/sources.list.d/google-webdesigner.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/webdesigner/deb/ stable main


==> /etc/apt/sources.list.d/google-webdesigner.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/webdesigner/deb/ stable main


==> /etc/apt/sources.list.d/ingalex-super-boot-manager-trusty.list <==
deb http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu raring main
# deb-src http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu raring main


==> /etc/apt/sources.list.d/ingalex-super-boot-manager-trusty.list.save <==
deb http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu raring main
# deb-src http://ppa.launchpad.net/ingalex/super-boot-manager/ubuntu raring main


==> /etc/apt/sources.list.d/intellinuxgraphics.list <==
deb https://download.01.org/gfx/ubuntu/14.04/main trusty main #Intel Graphics drivers


==> /etc/apt/sources.list.d/intellinuxgraphics.list.save <==
deb https://download.01.org/gfx/ubuntu/14.04/main trusty main #Intel Graphics drivers


==> /etc/apt/sources.list.d/kubuntu-ppa-backports-trusty.list <==
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main


==> /etc/apt/sources.list.d/kubuntu-ppa-backports-trusty.list.save <==
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main


==> /etc/apt/sources.list.d/lookit-daily-trusty.list <==
deb http://ppa.launchpad.net/lookit/daily/ubuntu trusty main
# deb-src http://ppa.launchpad.net/lookit/daily/ubuntu trusty main


==> /etc/apt/sources.list.d/lookit-daily-trusty.list.save <==
deb http://ppa.launchpad.net/lookit/daily/ubuntu trusty main
# deb-src http://ppa.launchpad.net/lookit/daily/ubuntu trusty main


==> /etc/apt/sources.list.d/maarten-baert-simplescreenrecorder-trusty.list <==
deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu trusty main
# deb-src http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu trusty main


==> /etc/apt/sources.list.d/maarten-baert-simplescreenrecorder-trusty.list.save <==
deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu trusty main
# deb-src http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu trusty main


==> /etc/apt/sources.list.d/mc3man-trusty-media-trusty.list <==
deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main


==> /etc/apt/sources.list.d/mc3man-trusty-media-trusty.list.save <==
deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main


==> /etc/apt/sources.list.d/mefrio-g-plymouthmanager-trusty.list <==
# deb http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu trusty main


==> /etc/apt/sources.list.d/mefrio-g-plymouthmanager-trusty.list.save <==
# deb http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu trusty main


==> /etc/apt/sources.list.d/moka-stable-trusty.list <==
deb http://ppa.launchpad.net/moka/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/moka/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/moka-stable-trusty.list.save <==
deb http://ppa.launchpad.net/moka/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/moka/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/mozillateam-firefox-next-trusty.list <==
deb http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu trusty main


==> /etc/apt/sources.list.d/mozillateam-firefox-next-trusty.list.save <==
deb http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu trusty main


==> /etc/apt/sources.list.d/mqchael-pipelight-trusty.list <==
deb http://ppa.launchpad.net/mqchael/pipelight/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu trusty main


==> /etc/apt/sources.list.d/mqchael-pipelight-trusty.list.save <==
deb http://ppa.launchpad.net/mqchael/pipelight/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu trusty main


==> /etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main


==> /etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list.save <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main


==> /etc/apt/sources.list.d/nitrux-nitrux-artwork-trusty.list <==
# deb http://ppa.launchpad.net/nitrux/nitrux-artwork/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nitrux/nitrux-artwork/ubuntu trusty main


==> /etc/apt/sources.list.d/nitrux-nitrux-artwork-trusty.list.save <==
# deb http://ppa.launchpad.net/nitrux/nitrux-artwork/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nitrux/nitrux-artwork/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-apps-trusty.list <==
deb http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-apps-trusty.list.save <==
deb http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-icons2-trusty.list <==
deb http://ppa.launchpad.net/noobslab/icons2/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons2/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-icons2-trusty.list.save <==
deb http://ppa.launchpad.net/noobslab/icons2/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons2/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-icons-trusty.list <==
deb http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-icons-trusty.list.save <==
deb http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-themes-trusty.list <==
deb http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-themes-trusty.list.save <==
deb http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main


==> /etc/apt/sources.list.d/numix-ppa-trusty.list <==
deb http://ppa.launchpad.net/numix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/numix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/numix/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/numix-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/numix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/numix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/numix/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/opera.list <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)


# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.


# deb http://deb.opera.com/opera-beta/ stable non-free #Opera Browser (beta releases)


==> /etc/apt/sources.list.d/opera.list.save <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades


deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)


# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.


# deb http://deb.opera.com/opera-beta/ stable non-free #Opera Browser (beta releases)


==> /etc/apt/sources.list.d/peterlevi-ppa-trusty.list <==
deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/peterlevi/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/peterlevi-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/peterlevi/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_bit-ticker_ubuntu.list <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/bit-ticker/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_bit-ticker_ubuntu.list.save <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/bit-ticker/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_marblearena2_ubuntu.list <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/marblearena2/ubuntu trusty main #credentials stored in /etc/apt/auth.conf


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_marblearena2_ubuntu.list.save <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/marblearena2/ubuntu trusty main #credentials stored in /etc/apt/auth.conf


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf


==> /etc/apt/sources.list.d/ravefinity-project-ppa-trusty.list <==
deb http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/ravefinity-project-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/screenlets-dev-ppa-trusty.list <==
# deb http://ppa.launchpad.net/screenlets-dev/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/screenlets-dev/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/screenlets-dev-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/screenlets-dev/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/screenlets-dev/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/skunk-pepper-flash-trusty.list <==
deb http://ppa.launchpad.net/skunk/pepper-flash/ubuntu trusty main
# deb-src http://ppa.launchpad.net/skunk/pepper-flash/ubuntu trusty main
# deb-src http://ppa.launchpad.net/skunk/pepper-flash/ubuntu trusty main


==> /etc/apt/sources.list.d/skunk-pepper-flash-trusty.list.save <==
deb http://ppa.launchpad.net/skunk/pepper-flash/ubuntu trusty main
# deb-src http://ppa.launchpad.net/skunk/pepper-flash/ubuntu trusty main
# deb-src http://ppa.launchpad.net/skunk/pepper-flash/ubuntu trusty main


==> /etc/apt/sources.list.d/spideroak.com.sources.list <==
deb http://apt.spideroak.com/ubuntu-spideroak-hardy/ release restricted




==> /etc/apt/sources.list.d/spideroak.com.sources.list.save <==
deb http://apt.spideroak.com/ubuntu-spideroak-hardy/ release restricted




==> /etc/apt/sources.list.d/steam.list <==
# deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
# deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam


==> /etc/apt/sources.list.d/steam.list.save <==
# deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
# deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam


==> /etc/apt/sources.list.d/thebernmeister-ppa-trusty.list <==
deb http://ppa.launchpad.net/thebernmeister/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/thebernmeister/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/thebernmeister-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/thebernmeister/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/thebernmeister/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/thefanclub-ubuntu-after-install-trusty.list <==
deb http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu trusty main
# deb-src http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu trusty main


==> /etc/apt/sources.list.d/thefanclub-ubuntu-after-install-trusty.list.save <==
deb http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu trusty main
# deb-src http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntuhandbook1-corebird-trusty.list <==
deb http://ppa.launchpad.net/ubuntuhandbook1/corebird/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntuhandbook1/corebird/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntuhandbook1-corebird-trusty.list.save <==
deb http://ppa.launchpad.net/ubuntuhandbook1/corebird/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntuhandbook1/corebird/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-java-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.save <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-tor-browser-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-tor-browser-trusty.list.save <==
deb http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu trusty main
darko@darko:~$ 



```

---

### Post by cariboo on 2015-01-25
The server is working from here, this is a direct link to the drivers:

[https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/](https://download.01.org/gfx/ubuntu/14.04/main/pool/main/i/)

---

