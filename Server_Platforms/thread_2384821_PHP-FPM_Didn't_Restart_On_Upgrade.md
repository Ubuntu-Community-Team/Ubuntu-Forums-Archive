---
title: "PHP-FPM Didn't Restart On Upgrade"
date: 2018-02-12
forum: Server Platforms
---

### Post by espigle on 2018-02-12
We have a couple web servers (still in development / testing) which we are rolling out on Ubuntu 16.04 and both use PHP-FPM (version 7.0) for handling PHP. They've been running for many months with no real issues. I also recently starting using an on premise Canonical Landscape server to manage patching for our small handful of Ubuntu servers on premise. I'm just using the free tier that's good for 10 servers or less.

We had an update go out on Saturday morning around 2:00am and I had it set to update all packages on the servers. PHP-FPM was one of the packages that got updated during this maintenance window by Landscape. Unfortunately, we found out later that the PHP-FPM daemon didn't restart after upgrade on these two web servers. We have a 3rd server that also runs the same PHP-FPM version (and Ubuntu version) and it restarted fine during the upgrade window after the PHP-FPM software finished upgrading. Here is what a log entry looks like from /var/log/php7.0-fpm.log of the server where it upgraded and started back up fine:

```
[10-Feb-2018 02:04:38] NOTICE: Terminating ...
[10-Feb-2018 02:04:38] NOTICE: exiting, bye-bye!
[10-Feb-2018 02:04:49] NOTICE: configuration file /etc/php/7.0/fpm/php-fpm.conf test is successful

[10-Feb-2018 02:04:49] NOTICE: fpm is running, pid 22076
[10-Feb-2018 02:04:49] NOTICE: ready to handle connections
[10-Feb-2018 02:04:49] NOTICE: systemd monitor interval set to 10000ms
```

For the server that upgraded but didn't restart, it just ends with this:

```
[10-Feb-2018 02:04:44] NOTICE: Terminating ...
[10-Feb-2018 02:04:44] NOTICE: exiting, bye-bye!
```

I manually restarted the daemon when I later found out PHP-FPM wasn't running, and it started up just fine. It appears it upgraded OK and just didn't start back up. My question is: where can I find out why it may not have been restarted after upgrade? The php7.0-fpm.log file isn't showing any errors. I reviewed the dpkg.log file as well and it shows where several PHP-FPM modules were upgraded at this time, no indications of errors. Where else might I go / look to investigate why the PHP-FPM daemon didn't restart after upgrade?

---

### Post by espigle on 2018-02-12
Found more details from the Landscape web GUI. Appears there is a EULA that needs accepting for upgrade and it's failing, so it brings the whole thing down it appears. Need to figure out if there is a way to accept this if one appears on upgrade.

```
[COLOR=#333333]Preparing to unpack .../msodbcsql_17.0.1.1-1_amd64.deb ...[/COLOR]ERROR: The EULA was not accepted. Installation aborted.
dpkg: error processing archive /var/cache/apt/archives/msodbcsql_17.0.1.1-1_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1


Errors were encountered while processing:
 /var/cache/apt/archives/msodbcsql_17.0.1.1-1_amd64.deb
E:Sub-process /usr/bin/dpkg returned an error code (1)
```

---

