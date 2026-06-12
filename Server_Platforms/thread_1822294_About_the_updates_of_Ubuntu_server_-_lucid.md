---
title: "About the updates of Ubuntu server - lucid"
date: 2011-08-10
forum: Server Platforms
---

### Post by lohpenwei on 2011-08-10
Hi all,

I would like to seek you guys help as I am too new to ubuntu server. Currently I am using lucid 10.04 LTS as my server os.
However, When the time I apt-get update I will have the following error.

QUOTE
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  mutiverse/binary-amd64/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://ppa.launchpad.net/freeswitch-driver...d64/Packages.gz](http://ppa.launchpad.net/freeswitch-driver...d64/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/freeswitch-driver...d64/Packages.gz](http://ppa.launchpad.net/freeswitch-driver...d64/Packages.gz)  404  Not Found


Any idea could advice me how to solve it?

Thousand Thanks...

---

### Post by stlsaint on 2011-08-11
The first one i am unsure about but the last two are ppa's that you have added so you can troubleshoot them from launchpad.

---

### Post by lohpenwei on 2011-08-11
ya, the link that fetching is wrong, how can i change the http link to the correct one??


[http://ppa.launchpad.net/freeswitch-driver/](http://ppa.launchpad.net/freeswitch-driver/) (WRONG)
[http://ppa.launchpad.net/freeswitch-drivers/](http://ppa.launchpad.net/freeswitch-drivers/) (Correct)

[http://ppa.launchpad.net/freeswitch-drivers/freeswitch-nightly-drivers/ubuntu/dists/lucid/main/binary-amd64/(Correct](http://ppa.launchpad.net/freeswitch-drivers/freeswitch-nightly-drivers/ubuntu/dists/lucid/main/binary-amd64/(Correct))
[http://ppa.launchpad.net/freeswitch-drivers/freeswitch-nightly-/ubuntu/dists/lucid/main/binary-amd64/](http://ppa.launchpad.net/freeswitch-drivers/freeswitch-nightly-/ubuntu/dists/lucid/main/binary-amd64/) (WRONG)

Please advise me.
Thanks..

---

### Post by disconap on 2011-08-12
You will need to manually edit your sources.list file.  Here's a good link to get you started:

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

Once you've opened the file in a text editor, scroll down to the incorrect repositories and correct them (I had to do this with 10.4.1 as well).

It suggests nano for a text editor, and if you already use nano then cool.  I tend to prefer vi, but it's really a matter of personal preference (as I run a lot of macs as well, and I tend to use vi in the OSX terminal as well)...

---

### Post by lohpenwei on 2011-08-13
I see, I use nano for most cases, because I dont really know much about ubuntu, I am too new. So, I just stick with whatever I know. >.<

but which sources.list that I need to modify? is it in the /etc/apt/sources.list ?

Sorry if I have asked stupid question here.

I tried to nano /etc/apt/sources.list
However, inside the list I did not see the repositories which are wrong.

> 
 nano /etc/apt/sources.list
  GNU nano 2.2.2                                              File: /etc/apt/sources.list

#
# deb cdrom:[Ubuntu-Server 10.04.2 LTS _Lucid Lynx_ - Release amd64 (20110211.1)]/ lucid main restricted

# deb cdrom:[Ubuntu-Server 10.04.2 LTS _Lucid Lynx_ - Release amd64 (20110211.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid mutiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse




---

