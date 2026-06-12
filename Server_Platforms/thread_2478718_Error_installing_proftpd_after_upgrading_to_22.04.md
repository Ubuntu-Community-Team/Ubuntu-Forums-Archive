---
title: "Error installing proftpd after upgrading to 22.04"
date: 2022-09-03
forum: Server Platforms
---

### Post by rickey++ on 2022-09-03
Hi everyone,

I upgraded my server from 20.04 to 22.04. On first trial update did not go through as proftpd was not installed during update, so I revert back to 20.04, removed proftpd and then did upgrade to 22.04. It went smoothly.
I then tried to install proftpd and I again got the error.

I saw a similar thread ([https://ubuntuforums.org/showthread.php?t=2478062&p=14108218#post14108218](https://ubuntuforums.org/showthread.php?t=2478062&p=14108218#post14108218)) with a possible solution, however even after unmask I get the same error. I am unsure of what to do next.

If anyone has a suggestion please reply. Thanks in advance.
```
root@server:~# dpkg --configure -a
Setting up proftpd-core (1.3.7c+dfsg-1build1) ...
usermod: no changes
Synchronizing state of proftpd.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable proftpd
Could not execute systemctl:  at /usr/bin/deb-systemd-invoke line 142.
dpkg: error processing package proftpd-core (--configure):
 installed proftpd-core package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of proftpd-mod-crypto:
 proftpd-mod-crypto depends on proftpd-core (= 1.3.7c+dfsg-1build1); however:
  Package proftpd-core is not configured yet.

dpkg: error processing package proftpd-mod-crypto (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of proftpd-mod-wrap:
 proftpd-mod-wrap depends on proftpd-core (= 1.3.7c+dfsg-1build1); however:
  Package proftpd-core is not configured yet.

dpkg: error processing package proftpd-mod-wrap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of proftpd-basic:
 proftpd-basic depends on proftpd-core; however:
  Package proftpd-core is not configured yet.
 proftpd-basic depends on proftpd-mod-wrap; however:
  Package proftpd-mod-wrap is not configured yet.
 proftpd-basic depends on proftpd-mod-crypto; however:
  Package proftpd-mod-crypto is not configured yet.

dpkg: error processing package proftpd-basic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 proftpd-core
 proftpd-mod-crypto
 proftpd-mod-wrap
 proftpd-basic

```

---

### Post by LHammonds on 2022-09-03
I'm not familiar with proftpd so take what I say about it with a grain of salt and back everything up of value.

I never do in-place upgrades because the risk factor is too high.  The OS is tested to do the upgrade but not the scenario of every package that's available....and it would be exceptionally rare for anyone running a server without additional packages.  Therefore I have always considered doing an in-place upgrade too risky to my services going dark.  However, in a virtual environment, I have the luxury of running two servers at the same time (old vs new) but that may not be the case with home users with only one machine running a bare-metal install.  In a bare-metal install scenario, there will be much more downtime, especially if there are issues with applications / data / configuration (regardless if doing in-place upgrade or fresh re-install).

If you can, I would backup the data, re-format and install a fresh 22.04.  Then install the software, configure it and restore the data.

But if that is not possible, then I'd suppose the next step would be to clean the proftpd software.  Most everything in what you posted is just a cascade of dependency problems (one thing needs the other thing installed before the next can be installed).  The crux of the cascade dependency seems to be proftpd-core.

On my 20.04.5 LTS server, I did not find a proftpd-core package.  There is proftpd-basic 1.3.6c-2

On my 22.04.1 LTS server, I found proftpd-basic 1.3.7c+dfsg-1build1 but it depends on proftpd-core, proftpd-mod-wrap, proftpd-mod-crypto (which we saw in the cascade effect of errors)

I would not be surprised if there were changes in the configuration files (or other required libraries) of the old to new version so step #1 would be to remove all traces of the old package if possible.

You can try the below commands but I don't know how effective they will be at cleaning an installation from a different OS version since the current OS only knows about the new packages.

```
sudo apt remove proftpd-mod-crypto
sudo apt remove proftpd-mod-wrap
sudo apt remove proftpd-core
sudo apt remove proftpd-basic
sudo apt autoremove
sudo apt purge proftpd-mod-crypto
sudo apt purge proftpd-mod-wrap
sudo apt purge proftpd-core
sudo apt purge proftpd-basic
```

The next step I would do would be to manually find leftover remnants such as configuration files that are not part of the new install.

I am not familiar with that package so have a look around for files that were left behind and move or delete them.

The next step would be to try and install the application.  If everything was purged, it should install just fine...but there are a LOT of dependencies and differences of the old version on 20.04 and new version on 22.04 which might make this extremely difficult to clear.

```
sudo apt install proftpd-basic
```

LHammonds

---

