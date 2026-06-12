---
title: "Unable to apt-get,"
date: 2012-02-13
forum: Server Platforms
---

### Post by Symphona on 2012-02-13
Hello All,

I seem to be having problems installing/updating with apt-get, as well as authenticating any packages I try to install. I have checked the DNS settings, which seem to work.

I'm still running 9.10 (Karmic), as its a home server which I don't really keep tended, however this is now causing a few problems.

Example output when installing. Following the given advice leads to more 404 errors
```
symphona@Asgard:/$ sudo apt-get install nmap
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  liblua5.1-0
The following NEW packages will be installed
  liblua5.1-0 nmap
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,681kB of archives.
After this operation, 6,570kB of additional disk space will be used.
Do you want to continue [Y/n]? y

WARNING: The following packages cannot be authenticated!
  liblua5.1-0 nmap
Install these packages without verification [y/N]? y

Err http://gb.archive.ubuntu.com karmic/main liblua5.1-0 5.1.4-3
  404  Not Found
Err http://gb.archive.ubuntu.com karmic/main nmap 5.00-2
  404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/lua5.1/liblua5.1-0_5.1.4-3_i386.deb  404  Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/n/nmap/nmap_5.00-2_i386.deb  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```I'm guessing I should change the respositories? Not sure honestly, help is much appreciated!

---

### Post by snowpine on 2012-02-13
Edit your /etc/apt/sources.list and change all the URLs from:

```
http://gb.archive.ubuntu.com/
```

to:

```
http://old-releases.ubuntu.com/
```

and be sure to:

```
sudo apt-get update
```

This will allow you to install **old and unsupported** applications from the Karmic repos. Karmic will never get any more bug fixes or security patches; it is "end of life" and provided on an as-is basis. 10.04 is the oldest version currently supported (and 12.04 is right around the corner).

---

### Post by Symphona on 2012-02-13
I guess the correct question then is: will changing the repositories allow me to update to the supported versions? As much as I don't need to be at the cutting edge, being close enough that things still work will be lovely!

Thanks for the help.

---

### Post by ruffEdgz on 2012-02-13
The problem you are getting is probably because Ubuntu 9.10 isn't supported any more as shown here: [http://en.wikipedia.org/wiki/Ubuntu_(operating_system)#Releases](http://en.wikipedia.org/wiki/Ubuntu_(operating_system)#Releases)

It would be wise to move it to 10.04 since that is the current LTS (Long Term Service) version but that will be updated to 12.04 in about 2 months or so (should be coming out in April).

I did find a link for a ppa that might have packages for 9.10 but I don't recommend using it since you should be on a supported and up-to-date server version: [http://ppa.launchpad.net/fta/ppa/ubuntu](http://ppa.launchpad.net/fta/ppa/ubuntu)

I verified that the URL does work and still has Karmic package. Read the below for an example of how you can update this in the /etc/apt/source.list file:
```

deb http://ppa.launchpad.net/fta/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/fta/ppa/ubuntu karmic main
deb http://archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb http://ppa.launchpad.net/tormodvolden/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/tormodvolden/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/pythoneers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/pythoneers/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main

```

---

### Post by ruffEdgz on 2012-02-13
> **Symphona said:**
> I guess the correct question then is: will changing the repositories allow me to update to the supported versions? As much as I don't need to be at the cutting edge, being close enough that things still work will be lovely!

Thanks for the help.

Its an older doc but it should be able to help you with that question about upgrading from Karmic to Lucid:

[https://help.ubuntu.com/community/LucidUpgrades#Upgrade_from_9.10_to_10.04_LTS](https://help.ubuntu.com/community/LucidUpgrades#Upgrade_from_9.10_to_10.04_LTS)

---

### Post by snowpine on 2012-02-13
> **Symphona said:**
> I guess the correct question then is: will changing the repositories allow me to update to the supported versions? As much as I don't need to be at the cutting edge, being close enough that things still work will be lovely!

Thanks for the help.

If you go 1 step to 10.04 Lucid, you will have a nice, stable server through April 2015.

There are two ways to do this: fresh reinstall (my recommendation) or "end of life" upgrade.

---

### Post by Symphona on 2012-02-13
That update to 10.04 worked perfectly, I'll settle with this version until I have the time to set up a fresh install, thank you for the help!

---

