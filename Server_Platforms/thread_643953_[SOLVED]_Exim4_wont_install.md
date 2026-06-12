---
title: "[SOLVED] Exim4 wont install"
date: 2007-12-18
forum: Server Platforms
---

### Post by CheShA on 2007-12-18
Problem - I was having problems with Exim so i decided to reinstall it.  Having apt-get removed it I went to apt-get install and I get this (important part is in highlighted in red):


```
root@ubiquitus:/var/lib/dpkg# apt-get install exim4
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  exim4-base exim4-config exim4-daemon-light libdb4.3
Suggested packages:
  mail-reader eximon4 exim4-doc-html exim4-doc-info libmail-spf-query-perl
Recommended packages:
  mailx
The following NEW packages will be installed
  exim4 exim4-base exim4-config exim4-daemon-light libdb4.3
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2098kB of archives.
After unpacking 4575kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package libdb4.3.
(Reading database ... 39352 files and directories currently installed.)
Unpacking libdb4.3 (from .../libdb4.3_4.3.29-8ubuntu2_amd64.deb) ...
Selecting previously deselected package exim4-config.
Unpacking exim4-config (from .../exim4-config_4.67-5build1_all.deb) ...
Selecting previously deselected package exim4-base.
Unpacking exim4-base (from .../exim4-base_4.67-5build1_amd64.deb) ...
Selecting previously deselected package exim4-daemon-light.
Unpacking exim4-daemon-light (from .../exim4-daemon-light_4.67-5build1_amd64.deb) ...
Selecting previously deselected package exim4.
Unpacking exim4 (from .../exim4_4.67-5build1_all.deb) ...
Setting up libdb4.3 (4.3.29-8ubuntu2) ...
[COLOR="Red"]Setting up exim4-config (4.67-5build1) ...
dpkg-statoverride: cannot open statoverride: No such file or directory
dpkg: error processing exim4-config (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of exim4-base:[/COLOR]
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:
  Package exim4-config is not configured yet.
  Package exim4-config-2 is not installed.
  Package exim4-config which provides exim4-config-2 is not configured yet.
dpkg: error processing exim4-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4-daemon-light:
 exim4-daemon-light depends on exim4-base (>= 4.67); however:
  Package exim4-base is not configured yet.
dpkg: error processing exim4-daemon-light (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of exim4:
 exim4 depends on exim4-base (>= 4.67); however:
  Package exim4-base is not configured yet.
 exim4 depends on exim4-daemon-light | exim4-daemon-heavy | exim4-daemon-custom; however:
  Package exim4-daemon-light is not configured yet.
  Package exim4-daemon-heavy is not installed.
  Package exim4-daemon-custom is not installed.
dpkg: error processing exim4 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exim4-config
 exim4-base
 exim4-daemon-light
 exim4
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Does anyone have any idea what the problem might be?

i also did this for good measure:
```
root@ubiquitus:/var/lib/dpkg# locate dpkg-statoverride
/usr/sbin/dpkg-statoverride
/usr/share/man/de/man8/dpkg-statoverride.8.gz
/usr/share/man/fr/man8/dpkg-statoverride.8.gz
/usr/share/man/man8/dpkg-statoverride.8.gz
/usr/share/man/pl/man8/dpkg-statoverride.8.gz

```

and this:
```
root@ubiquitus:/var/lib/dpkg# dpkg-statoverride
dpkg-statoverride: no mode specified

Usage: dpkg-statoverride [<option> ...] <command>
...etc 

```

This made no difference:
```
root@ubiquitus:/var/lib/dpkg# cp statoverride-old statoverride

```

The server is a fresh install of Gutsy with only a few packages on.

---

### Post by CheShA on 2007-12-18
I do apologie for reaching out to the forums so easily.... I have resolved this  only minutes after posting.  

I edited /var/lib/dpkg/status, searched for exim4 and deleted a big paragraph about exim4, then i deleted a line or two out of /var/lib/dpkg/statoverride which was relating to exim4.  

then I (probably unneccessarily)  did:
```
apt-get clean && apt get autoclean && apt-get update 
```

and everything was able to install fine again.

---

